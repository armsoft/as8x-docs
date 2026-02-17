---
layout: page
title: "GetJuridicalClientDataResponse դաս" 
---

Այս դասը վերադարձվում է իրավաբանական հաճախորդի տվյալների ստացման ժամանակ։

Օգտագործվում է [ClientsRoutes](../routes/ClientsRoutes.md).[GetJuridicalClientData](../routes/ClientsRoutes.md#getjuridicalclientdata) մեթոդում։

```c#
public class GetJuridicalClientDataResponse
{
    /// <summary>Հաճախորդի կոդ</summary>
    public string ClientCode { get; set; }

    /// <summary>Հաճախորդի Արտաքին N </summary>
    public string OuterID { get; set; }

    /// <summary>ՀՎՀՀ</summary>
    public string TaxCode { get; set; }

    /// <summary>Ռեզիդենտություն</summary>
    public bool Resident { get; set; }

    /// <summary>Բանկի հետ կապակցվածություն</summary>
    public bool RelatedWithBank { get; set; }

    /// <summary>Անվանում</summary>
    public string Name { get; set; }

    /// <summary>Անգլերեն անվանում</summary>
    public string NameEng { get; set; }
}
```
