---
layout: page
title: "OtherScheduleRow դաս" 
---

Պայմանագրի այլ մարումների գրաֆիկի տող։

Օգտագործվում է [Loans.CreateRequest](../types/Loans/CreateRequest.md) դասում։

```c#
public class OtherScheduleRow
{
    /// <summary> Ամսաթիվ </summary>
    public DateTime Date { get; set; }

    /// <summary> Գումար </summary>
    public decimal Amount { get; set; }

    /// <summary> Մեկնաբանություն </summary>
    public string Comment { get; set; }
}
```
