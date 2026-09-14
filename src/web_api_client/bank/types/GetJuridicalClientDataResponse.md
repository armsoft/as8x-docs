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

    /// <summary>Հաճախորդը փակ է</summary>
    public bool IsClosed { get; set; }

    /// <summary>Հեռախոսահամար</summary>
    public string Mobile { get; set; } = "";

    /// <summary>Հեռախոսահամարը վավեր է</summary>
    public bool MobileIsValid { get; set; } = false;

    /// <summary>Էլ. հասցե</summary>
    public string EMail { get; set; } = "";

    /// <summary>Էլ. հասցեն վավեր է</summary>
    public bool EMailIsValid { get; set; } = false;

    /// <summary> Քաղվածքի տրամադրման ձև </summary>
    public StatementDeliverModes? AccStmtType { get; set; } = null;

    /// <summary> Քաղվածքի տրամադրման ձև </summary>
    public StatementDeliverModes? CardStmtType { get; set; } = null;

    /// <summary> Քաղվածքի տրամադրման ձև </summary>
    public StatementDeliverModes? AgrStmtType { get; set; } = null;

    /// <summary> Փաստացի հասցե </summary>
    public Address CurrentAddress { get; set; } = null;

    /// <summary> Գրանցման հասցե </summary>
    public Address RegAddress { get; set; } = null;

    /// <summary>
    /// Իրավաբանական կարգավիճակը 
    /// 1 - իրավաբանական անձ
    /// 2 - Ֆիզիկական անձ
    /// 3 - անհատ ձեռներեց
    /// </summary>
    public short Status { get; set; } = 0;

    /// <summary> Այլ ռեկվիզիտներ/ընդլայնված ռեկվիզիտներ (UDR)</summary>
    public Dictionary<string, object> OtherFieldValues { get; set; }

    /// <summary>Անվանում</summary>
    public string Name { get; set; }

    /// <summary>Անգլերեն անվանում</summary>
    public string NameEng { get; set; }

    /// <summary>Գրանցման N</summary>
    public string RegNum { get; set; }

    /// <summary>Տրված</summary>
    public DateTime? RegDate { get; set; }

    /// <summary>Տիպ</summary>
    public string RegType { get; set; }
}
```
