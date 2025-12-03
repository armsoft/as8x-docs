---
layout: page
title: "GetNBAccountRemainderRequest դաս" 
---

Այս դասը նախատեսված է ետհաշվեկշռային հաշվի մնացորդի հարցման համար։

Օգտագործվում է [NBAccountsRoutes](../routes/NBAccountsRoutes.md).[GetRemainder](../routes/NBAccountsRoutes.md#getremainder) մեթոդում։

```c#
public class GetNBAccountRemainderRequest
{
    /// <summary> Հ/Պ ետհաշվեկշռային հաշիվ </summary>
    public string BalAcc { get; set; }

    /// <summary> Ետհաշվեկշռային հաշվի համարը </summary>
    public string AccountCode { get; set; }

    /// <summary> Ամսաթիվ </summary>
    public DateTime? Date { get; set; }
}
```
