---
title: "Օրինակ IUIRequestExecutionProgress" 
sublinks:
- { title: "Օրինակ MessageBox, Document", ref: օրինակ-1 }
- { title: "Օրինակ փաստաթղթում AddCustomUIRequest-ով տվյալների փոխանցում", ref: օրինակ-2 }
- { title: "Օրինակ փաստաթղթում AddCustomUIRequest-ով տվյալների ստացում", ref: օրինակ-3 }
---

## Բովանդակություն
- [Փաստաթղթի ջնջման ժամանակ լրացուցիչ դիալոգի ցուցադրման օրինակ](#օրինակ-1)
- [Փաստաթղթի գրանցման ընթացքում պարտքերի տեղեկանք ցույց տալու օրինակ։](#օրինակ-2)
- [Փաստաթղթի գրանցման ընթացքում մի քանի դաշտով դիալոգ ցույց տալու օրինակ](#օրինակ-3)

## Օրինակ 1

Փաստաթղթի ջնջման ժամանակ լրացուցիչ դիալոգի ցուցադրման օրինակ։

Այս օրինակում փաստաթղթի հեռացման [Delete](../definitions/document.md#delete) իրադարձության մշակիչում [MessageBox](../types/IUIRequestExecutionProgress.md#messagebox) մեթոդի միջոցով ցույց է տալիս հաղորդագրության պատուհան կլիենտի ինտերֆեյսում։

```c#
public override async Task Delete(DeleteEventArgs args)
{
  // բեռնում է փաստաթղթի զավակ փաստաթղթերը
  var children = await this.DocumentService.GetDocumentChildren(this.ISN);

  if (children.Count > 0)
  {
    // MessageBox մեթոդի կանչի արդյունքում կլիենտում բացվում է հաղոորդագրւթյան պատուհան
    // "Հեռացնել պայմանագրի հաշիվները" տեքստով և "Այո" կոճակ սեղմման դեպքում հեռացվում է փաստաթղթի
    // զավակ փաստաթղթերը։
    var delAcc = (await this.Progress.MessageBox("Հեռացնել պայմանագրի հաշիվները".ToArmenianANSI(),
      MessageBoxButtons.YesNo, MessageBoxIconType.Question)).UIRequestResult == MessageBoxRequestResult.Yes;
    
    foreach (var (childISN, _) in children)
    {
      await this.DocumentService.CutParentLink(childISN, this.ISN);
      if (delAcc)
      {
        await this.DocumentService.Delete(childISN, false, "");
      }
    }
  }
}
```

## Օրինակ 2

Փաստաթղթի գրանցման ընթացքում պարտքերի տեղեկանք ցույց տալու օրինակ։

Այս օրինակում փաստաթղթի գրանցման ընթացքում ստուգվում է արդյոք առկա են պարտքեր, ձևավորվում է [տեղեկատուի տեսքով հաշվետվություն](../types/TextReport.md), որը պահպանվում է սերվերի ֆայլային պահոցում, ապա պահված հաշվետվության բեռնման տվյալները ուղարկվում են 4X կլիենտին [AddCustomUIRequest](../types/IUIRequestExecutionProgress.md#addcustomuirequest) մեթոդի միջոցով։

```c#
private const int ShowOverdueDebtsId = 1;

public override async Task Action(ActionEventArgs args)
{
    //...
    if (await this.HasOverdueDebts())
    {
        using TextReport debtsReport = await this.GetOverdueDebtsReport();
        var storageInfo = await infoReport.SaveToStorageAndClose();
        var result = await this.Progress.AddCustomUIRequest<NoResult, StorageInfo>(storageInfo, ShowOverdueDebtsId);

        // տեղեկանքը 4X-ում ցույց տալուց հետո դադարեցվում է փաստաթղթի գրանցումը
        throw new InvisibleException();
    }
    //...
}
```

4X-ում փաստաթղթի [FillUIRequestConfig](https://armsoft.github.io/as4x-docs/HTM/ProgrGuide/ScriptProcs/FillUIRequestConfig.html) իրադարձության մեջ, կարգավորած է, թե ֆունկցիան պետք է մշակի սերվերից ստացած հարցումը։ 

```vb
Public Sub FillUIRequestConfig(ByVal args As EventArgsUIRequestConfig)
	Dim config As New CustomUIRequestConfig
	config.Module = "MyModule" 'մշակող մոդուլի անունը
	config.AddSub 1, "ShowOverdueDebts" '1 id-ով հարցումը մշակող ֆունկցիան
	config.AddSub 2, "ShowMakeAccTrans" '2 id-ով հարցումը մշակող ֆունկցիան

	args.Configuration = config
End Sub
```

`ShowOverdueDebts` ֆունկցիան ստանում է `EventArgsUIRequest` օբյեկտ, որը պարունակում է սերվիսից եկող պարամետրերը Dictionary-ի մեջ։ Այստեղ 
* Ստեղծվում է `StorageInfo` տիպի օբյեկտ, որին փոխանցվում է սերվիսից եկած `StorageInfo`-ի ֆայլի և թղթապանակի անունները:
* Բեռնվում է սերվիսում պահված տեղեկանքը `LoadFromStorageInService` մեթոդի միջոցով, ապա այն ցուցադրվում է էկրանին։

```vb
'MODULE { NAME = MyModule;
Public Sub ShowOverdueDebts(ByVal args As EventArgsUIRequest)
	Dim report As AsRepViewer
	Dim oStorageInfo As StorageInfo

    ' args պարամետրի Request հատկությունը Dictionary տիպի է, որը պարունակում է սերվիսից եկած տվյալները
	oStorageInfo.BlobName = args.Request("BlobName")
	oStorageInfo.Container = args.Request("Container")
	Set report = CreateRepViewer()
	report.LoadFromStorageInService(oStorageInfo)
    report.Show
End Sub
```


## Օրինակ 3

Փաստաթղթի գրանցման ընթացքում մի քանի դաշտով դիալոգ ցույց տալու օրինակ։

Այս օրինակում Փաստաթղթի գրանցման ընթացքում ցույց է տրվում է դիալոգ 4X կլինետում, [AddCustomUIRequest](../types/IUIRequestExecutionProgress.md#addcustomuirequest) մեթոդով հարցման հետևանքով։ Ապա լրացված արժեքները վերադարձվում է 8X սերվիսին։

```c#
private const int ShowMakeAccTransId = 2;

public override async Task Action(ActionEventArgs args)
{
    //...
    var result = await this.Progress.AddCustomUIRequest<MakeAccTransResponse, NoParam>(new NoParam(), ShowMakeAccTransId);

    if (dlgReq.UIRequestResultState == UIRequestResultState.Timeout 
        || dlgReq.Result.Canceled)
    {
        //եթե ժամանակը լրացել է կամ դիալոգը դադարեցվել է, ապա ընդհատել փաստաթղթի գրանցումը
        throw new InvisibleException();
    }
    
    if (dlgReq.Result.DoTrans)
    {
        DateTime transDate = dlgReq.Result.TransDate.Value;
        //.. մշակել նշված ամսաթվով թղթակցությունները
    }
    //...
}
```

Վերադարձվող տվյալների համար հարկավոր է սահմանված է դաս։

```c#
public class MakeAccTransResponse
{
    public bool DoTrans { get; set; }
    public DateTime? TransDate { get; set; }
    public bool Canceled { get; set; }
}
```

4X-ում փաստաթղթի [FillUIRequestConfig](https://armsoft.github.io/as4x-docs/HTM/ProgrGuide/ScriptProcs/FillUIRequestConfig.html) իրադարձության մեջ, կարգավորած է, թե ֆունկցիան պետք է մշակի սերվերից ստացած հարցումը։ 

```vb
Public Sub FillUIRequestConfig(ByVal args As EventArgsUIRequestConfig)
	Dim config As New CustomUIRequestConfig
	config.Module = "MyModule" 'մշակող մոդուլի անունը
	config.AddSub 1, "ShowOverdueDebts" '1 id-ով հարցումը մշակող ֆունկցիան
	config.AddSub 2, "ShowMakeAccTrans" '2 id-ով հարցումը մշակող ֆունկցիան

	args.Configuration = config
End Sub
```

`ShowMakeAccTrans` ֆունկցիայում ցույց է տրվում դիալոգ և լրացված տվյալները վերադարձվում է 8X սերվիսին։
Եթե դիալոգը դադարեցվել է, ապա դա նույնպես վերադարձվում է 8X սերվիսին։

```vb
'MODULE { NAME = MyModule;
Public Sub ShowMakeAccTrans(ByVal args As EventArgsUIRequest)
Dim dlg As AsDialog
	Set dlg = CreateDialog("EditAccDoc")
	With dlg
        .Caption = #ChangeAccs
        .ECaption = #e_ChangeAccs
        Call .AddControl("ISDOTRANS", "Կատարել ձևակերպումներ", "Boolean", , , "Make Transactions")
		Call .AddControl("DODATE", "Ամսաթիվ", "Date", , Param("WkDate"), "Date")
	End With
	dlg.Show args.SecondsToShow - 10
	If dlg.Cancel Then
		args.Response.Add "Canceled", True
	Else
		args.Response.Add "TransDate", dlg("DODATE")
		args.Response.Add "DoTrans", dlg("ISDOTRANS")
	End If
End Sub
```
