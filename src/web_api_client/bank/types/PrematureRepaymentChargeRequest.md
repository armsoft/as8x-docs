---
layout: page
title: "CacheClientContractsRequest դաս"
---

Այս դասը նախատեսված է վաղաժամկետ մարումից տույժի հաշվարկման համար։

Օգտագործվում է [PrematureChargesRoutes](../routes/PrematureChargesRoutes.md).[PrematureRepaymentCharge](../routes/PrematureChargesRoutes.md#prematurecharges) մեթոդում։

```c#
public class PrematureRepaymentChargeRequest
{
    /// <summary>Պայմանագրի ISN</summary>
    public int AgrISN { get; set; }

    /// <summary>Մարման ամսաթիվ</summary>
    public DateTime PaymentDate { get; set; }

    /// <summary>Մարվող մայր գումար</summary>
    public decimal RepaidPrincipal { get; set; }
}

```
