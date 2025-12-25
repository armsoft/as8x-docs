---
layout: page
title: "CreateMemOrderRequest դաս" 
---

Այս դասը նախատեսված է հիշարար օրդեր փաստաթղթի ստեղծման համար։

Օգտագործվում է [TransactionDocsRoutes](../routes/TransactionDocsRoutes.md).[CreateMemOrder](../routes/TransactionDocsRoutes.md#creatememorder) մեթոդում։

```c#
public class CreateMemOrderRequest
{
    /// <summary> Փաստաթղթի N </summary>
    public string DocNumber { get; set; }

    /// <summary> Ամսաթիվ </summary>
    public DateTime? Date { get; set; }

    /// <summary> Հաշիվ դեբետ </summary>
    public string AccDb { get; set; }

    /// <summary> Հաշիվ կրեդիտ </summary>
    public string AccCr { get; set; }

    /// <summary> Արժույթ </summary>
    public string Currency { get; set; }

    /// <summary> Գումար </summary>
    public decimal Amount { get; set; }

    /// <summary> Նպատակ </summary>
    public string Aim { get; set; }

    /// <summary> Ընդունող վճարային համակարգ </summary>
    public string PaySystemIn { get; set; }

    /// <summary> Գրասենյակ </summary>
    public string AcsBranch { get; set; } = string.Empty;

    /// <summary> Բաժին </summary>
    public string AcsDepart { get; set; } = string.Empty;

    /// <summary> Ունիկալ համար </summary>
    public string OuterID { get; set; }

    /// <summary> Կատարել սև ցուցակի ստուգում </summary>
    public bool CheckBlackList { get; set; } = true;

    /// <summary> Ստուգել դեբետ հաշվի հաշվետիրոջ գումարների արգելադրումից պարտքի առկայությունը </summary>
    public bool CheckDebtsByAmountBlock { get; set; } = true;

    /// <summary> Կատարել գերածախսի հաշվին </summary>
    public bool UseOverlimit { get; set; } = false;

    /// <summary> Կատարել պարտքերի ստուգում </summary>
    public bool CheckPastDueDebts { get; set; } = true;

    /// <summary> true - արժեքի դեպքում առաջանում է սխալ միայն այն դեպքում, երբ մնացորդը չի բավարարում փոխանցվող գումարին և պարտքին 
    /// Կիրառելի է միայն <see cref="CheckPastDueDebts"/>-ի true արժեքի դեպքում</summary>
    public bool PastDueDebtsSoftCheck { get; set; } = true;
}
```
