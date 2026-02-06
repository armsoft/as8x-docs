---
layout: page
title: "GetClientDataRequest դաս" 
---

Այս դասը նախատեսված է հաճախորդի տվյալների ստացման համար։

Օգտագործվում է [ClientsRoutes](../routes/ClientsRoutes.md).[GetPhysicalClientData](../routes/ClientsRoutes.md#getphysicalclientdata) և [ClientsRoutes](../routes/ClientsRoutes.md).[GetJuridicalClientData](../routes/ClientsRoutes.md#getjuridicalclientdata) մեթոդում։

```c#
public class GetClientDataRequest
{
    /// <summary> Հաճախորդի կոդ</summary>
    public string ClientCode { get; set; }

    /// <summary> Հաճախորդի արտաքին ID </summary>
    public string ClientOuterID { get; set; }
}
