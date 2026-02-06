---
layout: page
title: "GetPhysicalClientDataResponse դաս" 
---

Այս դասը վերադարձվում է ֆիզիկական անձ հաճախորդի տվյալների ստացման ժամանակ։

Օգտագործվում է [ClientsRoutes](../routes/ClientsRoutes.md).[GetPhysicalClientData](../routes/ClientsRoutes.md#getphysicalclientdata) մեթոդում։

```c#
public class GetPhysicalClientDataResponse
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

    /// <summary> Անուն </summary>
    public string FirstName { get; set; }

    /// <summary>Ազգանուն</summary>
    public string LastName { get; set; }

    /// <summary>Հայրանուն</summary>
    public string PatrName { get; set; }

    /// <summary>Անուն անգլերեն</summary>
    public string FirstNameEng { get; set; }

    /// <summary>Ազգանուն անգլերեն</summary>
    public string LastNameEng { get; set; }

    /// <summary>Հայրանուն անգլերեն</summary>
    public string PatrNameEng { get; set; }

    /// <summary>Սոց քարտ</summary>
    public string SSNNumber { get; set; }

    /// <summary>Տրված</summary>
    public DateTime? SSNDate { get; set; }

    /// <summary>Տիպ</summary>
    public string SSNType { get; set; }

    /// <summary>Անձնագրի տվյալներ</summary>
    public PassData Passport { get; set; }

    /// <summary>Անձնագրի տվյալներ 2</summary>
    public PassData Passport2 { get; set; }

    /// <summary>Բանկի աշխատակից</summary>
    public bool IsBankEmployee { get; set; }
}
```

* [PassData](../types/PassData.md) դասի նկարագիր
