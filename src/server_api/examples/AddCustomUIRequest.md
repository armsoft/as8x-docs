---
title: "Փաստաթղթում Custom UI Request-ի ավելացման օրինակ" 
---

Այս օրինակում [բեռնվում](../services/IDocumentService.md#load) են ընթացիկ փաստաթղթի [ծնող փաստաթղթերը](../services/IDocumentService.md#getdocumentparents), ծնող փաստաթղթերի մասին ինֆորմացիան ավելացվում է [տեքստային հաշվետվությունում](../types/TextReport.md), որը պահվում է ընթացիկ սեսսիայի [կոնտեյներում](../services/IStorageService.md#container)՝ [SaveToStorageAndClose](../types/TextReport.md#savetostorageandclose) մեթոդի միջոցով: Պահված հաշվետվությունը պարունակող թղթապանակի, ֆայլի անունները ուղարկվում են կլիենտական հատված [AddCustomUIRequest](../types/UIRequestExecutionProgress/AddCustomUIRequest.md) մեթոդի միջոցով՝ փոխանցելով `StoragInfo` տիպի օբյեկտ։

```c#
public override async Task<TemplateSubstitution> TemplateSubstitution(Dictionary<string, bool> mode,
                                                                   Dictionary<string, object> parameters = null)
{
    var parents = await this.documentService.GetDocumentParents(this.ISN);
    var infoReport = new TextReport(this.storageService)
    {
        ArmenianCaption = "Փաստաթղթի ծնող փաստաթղթերի նկարագրություն".ToArmenianANSI(),
        EnglishCaption = "Description of the document's parent documents"
    };
    foreach (var parent in parents)
    {
        var parentDocument = await this.documentService.Load(parent.isn);
        infoReport.AddRow($"Ծնող փաստաթղթի տեսակ {this.Description.DocType}".ToArmenianANSI());
        infoReport.AddRow($"Ծնող փաստաթղթի հայերեն անվանում {this.Description.ArmenianCaption}".ToArmenianANSI());
        infoReport.AddRow($"Ծնող փաստաթղթի անգլերեն անվանում {this.Description.EnglishCaption}".ToArmenianANSI());
        infoReport.AddRow($"Ծնող փաստաթղթի ստեղծման ամսաթիվ {this.CreationDate}".ToArmenianANSI());
        infoReport.Break();
    }
    var storageInfo = await infoReport.SaveToStorageAndClose();
    var result = await this.Progress.AddCustomUIRequest<NoResult, StorageInfo>(storageInfo, 1);
}
```

4x-ում անհրաժեշտ է մշակել [FillUIRequestConfig](https://armsoft.github.io/as4x-docs/HTM/ProgrGuide/ScriptProcs/FillUIRequestConfig.html) իրադարձությունը, որում պետք է սահմանել Custom UI Request-ի մշակման կոնֆիգուրացիան։ 

```vb
Public Sub FillUIRequestConfig(ByVal oEventArgsUIRequestConfig As EventArgsUIRequestConfig)

	Dim oCustomUIRequestInfo As CustomUIRequestConfig
	Set oCustomUIRequestInfo = New CustomUIRequestConfig
	oCustomUIRequestInfo.Module = "Module" 'Custom UI Request-ը մշակող մոդուլի անունը
	oCustomUIRequestInfo.AddSub 1, "UIRequestHandler" 'Custom UI Request-ը մշակող պրոցեդուրայի անունը

	oEventArgsUIRequestConfig.Configuration = oCustomUIRequestInfo
End Sub
```

Custom UI Request-ը մշակող UIRequestHandler պրոցեդուրան ստանում է `EventArgsUIRequest` օբյեկտ, որը պարունակում է սերվիսից եկող պարամետրերը Dictionary ձևաչափով։

* UIRequestHandler-ում ստեղծվում է `StorageInfo` տիպի օբյեկտ, որին փոխանցվում է սերվիսից եկած `StorageInfo`-ի ֆայլի և թղթապանակի անունները:
* Ստեղծվում է դատարկ տեքստային հաշվետվություն [CreateRepViewer](https://armsoft.github.io/as4x-docs/HTM/ProgrGuide/Functions/Functions/CreateRepViewer.html) մեթոդի միջոցով։
* Բեռնվում է սերվիսում հավաքված տեքստային հաշվետվությունը `LoadFromStorageInService` մեթոդի միջոցով։
* Եթե բեռնված հաշվետվությունը դատարկ չի, ապա այն ցուցադրվում է [Show](https://armsoft.github.io/as4x-docs/HTM/ProgrGuide/Functions/AsRepViewer/Show.html) մեթոդի միջոցով։

```vb
Public Sub UIRequestHandler(ByVal args As EventArgsUIRequest)

	Dim Report As AsRepViewer
	Dim oStorageInfo As StorageInfo

    ' args պարամետրի REQUEST հատկությունը Dictionary տիպի է, որը պարունակում է սերվիսից եկած տվյալները
	oStorageInfo.BlobName = args.REQUEST("BlobName")
	oStorageInfo.Container = args.REQUEST("Container")
	Set Report = CreateRepViewer()
	Report.LoadFromStorageInService(oStorageInfo)

	If Not Report Is Nothing AndAlso Report.RowCount > 0 Then
		Report.Show
	End If
End Sub
```
