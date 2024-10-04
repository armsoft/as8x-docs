---
layout: page
title: "Նոր երկար աշխատող պրոցեսի (DPR) նկարագրման ձեռնարկ"
tags: [DPR]
sublinks:
- { title: "Օժանդակ դասերի սահմանում", ref: օժանդակ-դասերի-սահմանում }
- { title: "Հիմնական դասի սահմանում", ref: հիմնական-դասի-սահմանում }
- { title: "Կոնստրուկտորի ձևավորում", ref: կոնստրուկտորի-ձևավորում }
- { title: "Execute", ref: execute }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [.cs ընդլայնմամբ ֆայլի սահմանում](#cs-ընդլայնմամբ-ֆայլի-սահմանում)
  - [Օժանդակ դասերի սահմանում](#օժանդակ-դասերի-սահմանում)
  - [Հիմնական դասի սահմանում](#հիմնական-դասի-սահմանում)
  - [Կոնստրուկտորի ձևավորում](#կոնստրուկտորի-ձևավորում)
  - [Execute](#execute)

## Ներածություն

Սերվիսային երկար տևող հարցումներ կատարելու և կատարման ընթացքին հետևելու համար նկարագրվում է երկար աշխատող պրոցես (DPR - Data Processing Request): 
Տե՛ս [Ասինխրոն մշակում կիրառությունների սերվերի վրա](../../architecture/appserver_async.md)։

8X-ում DPR նկարագրության համար հարկավոր է նկարագրել սերվերում աշխատող տրամաբանությունը C# դասում (`.cs` ֆայլում)։  
Հարկավոր է սահմնել մուտքային և ելթային պարամետրերի դասեր (կարող ենք օգտագործվել գոյություն ունեցողները)։

Կազմակերպության սեփական DPR-ների ստեղծման համար [տե՛ս](../../extensions/definitions/dpr_new_guide.md):

## .cs ընդլայնմամբ ֆայլի սահմանում

Ամբողջական կոդը դիտելու համար [տե՛ս](../examples/dpr/code.cs):

### Օժանդակ դասերի սահմանում

- Ստեղծել DPR-ի կատարման համար անհրաժեշտ պարամետրերը նկարագրող դաս։
  ```c#
  public class DeleteDocsByIsnRequest
  {
      public List<int> DocumentIsns { get; set; }
  }
  ```

- Ստեղծել DPR-ի կատարման արդյունքում ստացվող տվյալները նկարագրող դասը։
  ```c#
  public class DeleteDocsByIsnResponse
  {
      public StorageInfo StorageInfo { get; set; }
  }
  ```

### Հիմնական դասի սահմանում

- Հայտատարել դաս, որը ունի `DPR` ատրիբուտը և ժառանգում է `DataProcessingRequest<R, P>` դասը՝ որպես `R` փոխանցելով DPR-ի կատարման արդյունքում ստացվող տվյալները նկարագրող դասը, իսկ որպես `P`՝ պարամետրերը նկարագրող դասը։ 
  Պարամետրերի բացակայության դեպքում անհրաժեշտ է փոխանցել `NoParam` դասը, իսկ արդյունքի բացակայության դեպքում՝ `NoResult` դասը։
  ```c#
  [DPR(DPRType = DPRType.Report, ArmenianCaption = "Փաստաթղթերի հեռացում", EnglishCaption = "Deletion of documents")]
  public class DeleteDocsByIsnDPR : DataProcessingRequest<DeleteDocsByIsnResponse, DeleteDocsByIsnRequest>
  ```
  `DPR` ատրիբուտում հարկավոր է նշել խումբը, հայերեն անվանումը յունիկոդ կոդավորմամբ և անգլերեն անվանումը։

### Կոնստրուկտորի ձևավորում

- Ձևավորել կոնստրուկտորը, որտեղ անհրաժեշտ է [ինյեկցիա](../../project/injection.md) անել աշխատանքի համար անհրաժեշտ service-ները։
  ```c#
  private readonly IDocumentService documentService;
  private readonly IStorageService storageService;
  
  public DeleteDocsByIsnDPR(IDocumentService documentService, IStorageService storageService)
  {
      this.documentService = documentService;
      this.storageService = storageService;
  }
  ```

### Execute 

DPR-ի կատարման տրամաբանությունը մշակելու համար անհրաժեշտ է մշակել [Execute](dpr.md#execute) մեթոդը, որին փոխանցվում է պարամետրերը նկարագրող դասը և վերադարձնում է կատարման արդյունքում ստացվող տվյալները նկարագրող դասը։

Օրինակում նկարագրված DPR-ը հեռացնում է կատարման պարամետրում տրված ISN-ներով փաստաթղթերը համակարգից [IDocumentService](../services/IDocumentService.md).[Delete](../services/IDocumentService.md#delete) մեթոդի միջոցով, ստեղծում է [TextReport](TextReport.md)՝ կատարման ընթացքում առաջացած սխալները տեքստային հաշվետվությունում գրանցելու, որպես ֆայլ պահելու և վերադարձնելու համար։

```c#
public override async Task<DeleteDocsByIsnResponse> Execute(DeleteDocsByIsnRequest request, CancellationToken stoppingToken)
{
    // սխալների հավաքագրման համար տեքստային հաշվետվության ստեղծում
    using var report = new TextReport.TextReport(this.storageService)
    {
        ArmenianCaption = "Կատարման ընթացքում առաջացած սխալներ".ToArmenianANSI(),
        EnglishCaption = "Errors which occured during execution"
    };

    // 80 լայնությամբ ֆրագմենտի ավելացում հաշվետվությունում
    const int fragmentLength = 80;
    report.AddFragment(fragmentLength);

    // հաշվետվությունում գլխագիր տողի ավելացում թավ տառաոճով
    var formattedText = ApplyStyle("Փաստաթղթերի հեռացման սխալներ", TextReportStyle.Bold);
    report.AddHeader(formattedText);

    // DPR-ի կատարման պրոգրեսի պատուհանում "Հարցման կատարում" անունով փուլի ավելացում
    this.Progress.Add("Հարցման կատարում");
    var isns = request.DocumentIsns;

    this.Progress.CurrentPhase.Total = isns.Count; // պրոգրեսի ընթացիկ փուլում մշակվող տվյալների քանակը տալով
                                                   // պրոգրեսի պատուհանում հնարավոր է ցույց տալ մշակման ենթակա տվյալներից քանիսն են մշակվել

    this.Progress.CurrentPhase.Row = 0; // ընթացիկ պահին մշակվել է 0 փաստաթուղթ

    foreach (int isn in isns)
    {
        if (stoppingToken.IsCancellationRequested)
        {
            break; // եթե DPR-ի կատարման պրոգրեսի պատուհանից սեղմվել է «Ընդհատել» կոճակը, ապա ընդհատվում է կատարումը
        }
        this.Progress.CurrentPhase.Row++; // ամեն փաստաթղթի մշակման հետ պատուհանում փոխվում է մշակված փաստաթղթերի քանակը, օրինակ 7/11
        try
        {
            //հերթական փաստաթղթի ամբողջական հեռացում
            await this.documentService.Delete(isn, true, "Փաստաթղթի հեռացում".ToArmenianANSI());
        }
        catch (Exception ex)
        {
            // առաջացած սխալի հաղորդագրությունների ավելացում որպես տող տեքստային հաշվետվությունում
            foreach (string line in ex.Message.Split(['\n']))
            {
                report.AddRow(line, isn);
            }
            report.AddRow(string.Empty);
        }
    }

    // բոլոր փաստաթղթերի մշակումից հետո հաշվետվությունը պահվում է որպես ֆայլ SaveToStorageAndClose մեթոդի միջոցով,
    // որը վերադարձնում է StorageInfo, որը պարունակում է ֆայլի և ֆայլը պարունակող թղթապանակի անունները
    return new DeleteDocsByIsnResponse { StorageInfo = await report.SaveToStorageAndClose() };
}
```
