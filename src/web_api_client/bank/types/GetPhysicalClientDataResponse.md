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

    /// <summary>Անձը հաստ.փաստ. ստուգում</summary>
    public DateTime? PassCheckDate { get; set; } = null;

    /// <summary>Բանկի աշխատակից</summary>
    public bool IsBankEmployee { get; set; }

    /// <summary> Կոնտակտ. տվյալն. ստուգում</summary>
    public DateTime? ContactCheckDate { get; set; } = null;

    /// <summary>Ծննդյան ամսաթիվ</summary>
    public DateTime? DateOfBirth { get; set; }

    /// <summary>Զբաղվածություն</summary>
    public string Employment { get; set; } = "";

    /// <summary>Կրթական մակարդակ</summary>
    public string EducationStage { get; set; } = "";

    /// <summary>Ընտանեկան կարգավիճակ</summary>
    public string MaritalStatus { get; set; } = "";

    /// <summary>Ընտանիքի անդամների քանակ</summary>
    public int FamilyMembCount { get; set; } = 0;

    /// <summary>Անձնական եկամուտներ</summary>
    public decimal PersonalIncome { get; set; } = 0;

    /// <summary>Ընտանեկան եկամուտներ</summary>
    public decimal FamilyIncome { get; set; } = 0;

    /// <summary> Տվյալների թարմացում ԷԿԵՆԳ-ից </summary>
    public bool UpdateFromEkeng { get; set; }

}
```

* [PassData](../types/PassData.md) դասի նկարագիր
