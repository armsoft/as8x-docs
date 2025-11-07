---
layout: page
title: "CreateNBOrderRequest դաս" 
---

Այս դասը նախատեսված է Ե/Հ մուտքի օրդեր, Ե/Հ ելքի օրդեր փաստաթղթերի ստեղծման համար։

Օգտագործվում է [NBAccountsRoutes](../routes/NBAccountsRoutes.md).[CreateNBInputOrder](../routes/NBAccountsRoutes.md#createnbinputorder) ,
   [NBAccountsRoutes](../routes/NBAccountsRoutes.md).[CreateNBOutputOrder](../routes/NBAccountsRoutes.md#createnboutputorder) մեթոդներում։

```c#
public class CreateNBOrderRequest
{
    /// <summary> Փաստաթղթի N </summary>
    public string DocNumber { get; set; }

    /// <summary> Ամսաթիվ </summary>
    public DateTime? Date { get; set; }

    /// <summary> Ետհաշվեկշռային հաշվի Հ/Պ յոթանիշ կոդ </summary>
    public string BalAcc { get; set; }

    /// <summary> Հ/Պ ետհաշվեկշռային հաշիվ </summary>
    public string NBAcc { get; set; }

    /// <summary> Արժույթ </summary>
    public string Cur { get; set; }

    /// <summary> Քանակ </summary>
    public decimal Count { get; set; } = 0;

    /// <summary> Գումար </summary>
    public decimal Amount { get; set; }

    /// <summary> Արժեքները մուտք անող / ստացող </summary>
    public string PayerReceiverName { get; set; }

    /// <summary> Անձը հաստատող փաստ </summary>
    public string PassNum { get; set; }

    /// <summary> Հիմք </summary>
    public string Base { get; set; }

    /// <summary> Նպատակ </summary>
    public string Aim { get; set; }

    /// <summary> Գրասենյակ </summary>
    public string Branch { get; set; }

    /// <summary> Բաժին </summary>
    public string Depart { get; set; }
}
```
