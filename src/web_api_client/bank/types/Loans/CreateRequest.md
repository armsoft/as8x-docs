---
layout: page
title: "CreateRequest դաս" 
---

Այս դասը նախատեսված է գրաֆիկով վարկային պայմանագրի (C1Univer) ստեղծման համար։

Օգտագործվում է [LoansRoutes](../../routes/LoansRoutes.md).[Create](../../routes/LoansRoutes.md#create) մեթոդում։

Պարտադիր լրացման դաշտերն են՝ `OuterCode`, `Date`, `DateGive`, `CliCode`, `Amount`, `Shablon`։  

```c#
public class CreateRequest
{
    /// <summary> Արտաքին N </summary>
    public string OuterCode { get; set; }

    /// <summary> Ծնող փաստաթղթի արտաքին N (լրացվում է, եթե ստեղծվում է որպես ծնող պայմանագրի զավակ) </summary>
    public string OuterParent { get; set; }

    /// <summary> Կնքման ամսաթիվ </summary>
    public DateTime Date { get; set; }

    /// <summary> Հատկացման ամսաթիվ </summary>
    public DateTime DateGive { get; set; }

    /// <summary> Մարման ամսաթիվ </summary>
    public DateTime? DateAgr { get; set; }

    /// <summary> Հաճախորդի կոդ </summary>
    public string CliCode { get; set; }

    /// <summary> Անվանում (եթե null փոխանցեն, կգրվի հաճախորդի անվանումը) </summary>
    public string Name { get; set; }

    /// <summary> Պայմանագրի գումար </summary>
    public decimal Amount { get; set; }

    /// <summary> Տոկոսադրույք </summary>
    public InterestRate InterestRate { get; set; }

    /// <summary> Մեկնաբանություն </summary>
    public string Comment { get; set; }

    /// <summary> Հաշվարկման հաշիվ </summary>
    public string AccAcc { get; set; }

    /// <summary> Տոկոսների վճարման հաշիվ </summary>
    public string AccAccPR { get; set; }

    /// <summary> Մարման օրեր </summary>
    public string RepayDay { get; set; }

    /// <summary> Մարումների սկիզբ </summary>
    public DateTime? AgrMarBeg { get; set; }

    /// <summary> Մարումների վերջ </summary>
    public DateTime? AgrMarFin { get; set; }

    /// <summary> Մարումների սկիզբ (տոկոս) </summary>
    public DateTime? AgrMarBegPer { get; set; }

    /// <summary> Մարումների վերջ (տոկոս) </summary>
    public DateTime? AgrMarFinPer { get; set; }

    /// <summary> Ժամկետանց գումարի տույժ </summary>
    public InterestRate PcPenAgr { get; set; }

    /// <summary> Ժամկետանց տոկոսի տույժ </summary>
    public InterestRate PcPenPer { get; set; }

    /// <summary> Վարկային գծի գործելու ժամկետ </summary>
    public DateTime? DateLngEnd { get; set; }

    /// <summary> Ձևանմուշ </summary>
    public string Shablon { get; set; }

    /// <summary> Չօգտագործված մասի տոկոսադրույք </summary>
    public InterestRate PcNoChoose { get; set; }

    /// <summary> Սուբսիդավորման տոկոսադրույք </summary>
    public InterestRate PcGrant { get; set; }

    /// <summary> Սուբսիդավորման հաշիվ </summary>
    public string AccGrt { get; set; }

    /// <summary> Սուբսիդավորման ավարտի ամսաթիվ </summary>
    public DateTime? GrantEndDate { get; set; }

    /// <summary> Տոկոսների հաշվարկների սկիզբ </summary>
    public DateTime? PerCalcStart { get; set; }

    /// <summary> Վարձավճարի հաշվարկների սկիզբ </summary>
    public DateTime? GnzCalcStart { get; set; }

    /// <summary> Ժամկետանց գումարի տոկոսադրույք (վնաս) </summary>
    public InterestRate PcLoss { get; set; }

    /// <summary> Հաշվարկել ԲՏՀԴ տոկոսագումարը </summary>
    public bool? CalcFinPer { get; set; }

    /// <summary> Ճյուղայնություն </summary>
    public string Sector { get; set; }

    /// <summary> Օգտագործման ոլորտ (նոր ՎՌ) </summary>
    public string UsageField { get; set; }

    /// <summary> Նպատակ </summary>
    public string Aim { get; set; }

    /// <summary> Միջազգային կազմակերպություն </summary>
    public string InterOrg { get; set; }

    /// <summary> Ծրագիր </summary>
    public string Schedule { get; set; }

    /// <summary> Երաշխավորություն </summary>
    public string Guarantee { get; set; }

    /// <summary> Երկիր </summary>
    public string Country { get; set; }

    /// <summary> Մարզ </summary>
    public string District { get; set; }

    /// <summary> Մարզ (նոր ՎՌ) </summary>
    public string Region { get; set; }

    /// <summary> Նշում </summary>
    public string Note { get; set; }

    /// <summary> Նշում 2 </summary>
    public string Note2 { get; set; }

    /// <summary> Նշում 3 </summary>
    public string Note3 { get; set; }

    /// <summary> Գրասենյակ </summary>
    public string AcsBranch { get; set; }

    /// <summary> Բաժին </summary>
    public string AcsDepart { get; set; }

    /// <summary> Հասանելիության տիպ </summary>
    public string AcsType { get; set; }

    /// <summary> Կշռել դրամային ռիսկով </summary>
    public bool? WeightByAMDRisk { get; set; }

    /// <summary> Պայմ. թղթային N </summary>
    public string PaperCode { get; set; }

    /// <summary> Կապակցված պայմանագրի N </summary>
    public string LinkedAgrN { get; set; }

    /// <summary> Գործարքի ժամ </summary>
    public TimeSpan? TimeOp { get; set; }

    /// <summary> Վերանայման ամսաթիվ </summary>
    public DateTime? RevisionDate { get; set; }

    /// <summary> Սուբյեկտիվ դասակարգված </summary>
    public bool? SubjRisk { get; set; }

    /// <summary> ՊԵԿ ուղարկվող </summary>
    public bool? SRCSend { get; set; }

    /// <summary> Մասնաբաժիններով տրամադրվող (Ն51, Ն52) </summary>
    public bool? Phased { get; set; }

    /// <summary> Սուբսիդավորման ծրագիր(եր) ACRA </summary>
    public string SubsidyProgACRA { get; set; }

    /// <summary> Չդասակարգվող </summary>
    public bool? NotClass { get; set; }

    /// <summary> Ապահովված է այլ ապահովվածությամբ </summary>
    public bool? OtherCollateral { get; set; }

    /// <summary> Ժամկետանց օրերի հաշվարկն ըստ աշխատանքային օրերի </summary>
    public bool? DoOvrdInWorkDays { get; set; }

    /// <summary> Համավարկառուներ </summary>
    public List<CodebtorRow> Codebtors { get; set; }

    /// <summary> Նշումներ </summary>
    public List<NoteRow> Notes { get; set; }

    /// <summary> Այլ մարումների գրաֆիկի տողեր </summary>
    public List<OtherScheduleRow> OtherScheduleRows { get; set; }

    /// <summary> Այլ ռեկվիզիտներ/ընդլայնված ռեկվիզիտներ (UDR) </summary>
    public Dictionary<string, string> OtherFieldValues { get; set; }
}
```

* [InterestRate](../../types/InterestRate.md) դասի նկարագիր
* [CodebtorRow](../../types/CodebtorRow.md) դասի նկարագիր
* [NoteRow](../../types/NoteRow.md) դասի նկարագիր
* [OtherScheduleRow](../../types/OtherScheduleRow.md) դասի նկարագիր
