---
layout: page
title: "UpdatePhysicalClientDataRequest դաս" 
---

Այս դասը նախատեսված է ֆիզիկական անձ հաճախորդի խմբագրման համար։

Օգտագործվում է [ClientsRoutes](../routes/ClientsRoutes.md).[UpdatePhysicalClientData](../routes/ClientsRoutes.md#updatephysicalclientdata) մեթոդում։

```c#
public class UpdatePhysicalClientDataRequest
{
    /// <summary> Տվյալների թարմացում ԷԿԵՆԳ-ից </summary>
    public bool? UpdateFromEkeng { get; set; }

    /// <summary> Անձնագրի տվյալներ </summary>
    public PassData Passport { get; set; } = null;

    /// <summary> Անձնագրի տվյալներ 2 </summary>
    public PassData Passport2 { get; set; } = null;
}
```
* [PassData](../types/PassData.md) դասի նկարագիր
