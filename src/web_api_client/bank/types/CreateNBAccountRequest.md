---
layout: page
title: "CreateNBAccountRequest դաս" 
---

Այս դասը նախատեսված է ետհաշվեկշռային հաշվի ստեղծման համար։

Օգտագործվում է [NBAccountsRoutes](../routes/NBAccountsRoutes.md).[Create](../routes/NBAccountsRoutes.md#create) մեթոդում։

```c#
public class CreateNBAccountRequest
{
    /// <summary> Հ/Պ ետհաշվեկշռային հաշիվ </summary>
    public string BalAcc { get; set; }

    /// <summary> Հաշվետեր հաճախորդի կոդ </summary>
    public string CliCode { get; set; }

    /// <summary> ՀԾ-Բանկ համակարգում արժույթի կոդ </summary>
    public string Cur { get; set; }

    /// <summary> Ետհաշվեկշռային հաշվի տիպը </summary>
    public string AccType { get; set; }

    /// <summary> Բացման ամսաթիվ </summary>
    public DateTime? OpenDate { get; set; }

    /// <summary> Քանակային հաշիվ </summary>
    public bool IsCount { get; set; } = false;

    /// <summary> Միավորի գին </summary>
    public decimal ValueOfUnit { get; set; } = 0;

    /// <summary> Հաշվի վերին սահման </summary>
    public decimal UpperLimit { get; set; } = 999_999_999_999.99M;

    /// <summary> Հաշվի ստորին սահման </summary>
    public decimal LowerLimit { get; set; } = 0;

    /// <summary> Նշում </summary>
    public string Note { get; set; } = string.Empty;

    /// <summary> Նշում 2 </summary>
    public string Note2 { get; set; } = string.Empty;

    /// <summary> Նշում 3 </summary>
    public string Note3 { get; set; } = string.Empty;

    /// <summary> Գրասենյակ </summary>
    public string AcsBranch { get; set; } = string.Empty;

    /// <summary> Բաժին </summary>
    public string AcsDepart { get; set; } = string.Empty;

    /// <summary> Հասանելիության տիպ </summary>
    public string AcsType { get; set; } = string.Empty;
}
```
