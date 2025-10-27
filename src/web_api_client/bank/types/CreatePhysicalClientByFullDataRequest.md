---
layout: page
title: "CreatePhysicalClientByFullDataRequest դաս" 
---

Այս դասը նախատեսված է ֆիզիկական անձ հաճախորդի ստեղծման համար։

Օգտագործվում է [ClientsRoutes](../routes/ClientsRoutes.md).[CreatePhysicalClientByFullData](../routes/ClientsRoutes.md#createphysicalclientbyfulldata) մեթոդում։

```c#
public class CreatePhysicalClientByFullDataRequest
{
    /// <summary>Սոց քարտ</summary>
    public string SSNNumber { get; set; }

    /// <summary>Տրված</summary>
    public DateTime? SSNDate { get; set; }

    /// <summary>Տիպ</summary>
    public string SSNType { get; set; }

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

    /// <summary>Անձնագրի տվյալներ</summary>
    public PassData Passport { get; set; }

    /// <summary>Անձնագրի տվյալներ 2</summary>
    public PassData Passport2 { get; set; }

    /// <summary>Բանկի աշխատակից</summary>
    public bool IsBankEmployee { get; set; }

    /// <summary>Տվյալների թարմացում Էկենգից</summary>
    public bool UpdateFromEkeng { get; set; }

    /// <summary>Ռեզիդենտություն</summary>
    public bool Resident { get; set; }
    
    /// <summary>Ռեզիդենտության երկիր</summary>
    public string ResidenceCountry { get; set; }
    
    /// <summary>Գրասենյակ</summary>
    public string Branch { get; set; }
    
    /// <summary>Բաժին</summary>
    public string Department { get; set; }
    
    /// <summary>Հաս.տիպ</summary>
    public string AccessType { get; set; }
    
    /// <summary>Բանկի հետ կապակցվածություն</summary>
    public bool RelatedWithBank {  get; set; }

    // Լրացուցիչ էջ
    /// <summary>Զբաղվածություն</summary>
    public string Employment { get; set; }
    /// <summary>Կրթական մակարդակ</summary>
    public string EducationStage { get; set; }

    /// <summary>Ընտանեկան կարգավիճակ</summary>
    public string MaritalStatus { get; set; }

    /// <summary>Ընտանիքի անդամների քանակ</summary>
    public short FamilyMembCount { get; set; }

    /// <summary>Անձնական եկամուտներ</summary>
    public decimal PersonalIncome { get; set; }

    /// <summary>Ընտանեկան եկամուտներ</summary>
    public decimal FamilyIncome { get; set; }

    /// <summary>Սեռ</summary>
    public string Gender { get; set; }

    /// <summary>Քաղաքացիություն</summary>
    public string Citizenship { get; set; }

    /// <summary>Քաղաքացիության երկիր</summary>
    public string CitizenshipCountry { get; set; }

    /// <summary>Քաղաքացիության երկիր 2</summary>
    public string CitizenshipCountry2 { get; set; }

    /// <summary>Ծննդյան ամսաթիվ</summary>
    public DateTime? BirthDate { get; set; }

    /// <summary>Ծննդյան վայր</summary>
    public string BirthPlace { get; set; }

    /// <summary>Նշում</summary>
    public string ClientNote { get; set; }

    /// <summary>Նշում 2</summary>
    public string ClientNote2 { get; set; }

    /// <summary>Նշում3</summary>
    public string ClientNote3 { get; set; }

    /// <summary>Գաղտնաբառ</summary>
    public string Password { get; set; }

    /// <summary>Բջջային</summary>
    public string Mobile { get; set; }

    /// <summary>Էլ. հասցե</summary>
    public string EMail { get; set; }

    /// <summary> Base64 կոդավորմամբ նկար </summary>
    public string Photo_Id { get; set; }

    // Հասցե էջ
    /// <summary>Գրանցման հասցե</summary>
    public Address Address { get; set; }
    
    /// <summary>Փաստացի հասցե</summary>
    public Address CurrentAddress { get; set; }
    
    /// <summary>Լրացնել փաստացի հասցեն ըստ գրանցման հասցեյի</summary>
    public bool FillCurrentAddressAsReg { get; set; }
    
    // Քաղվածքներ/ Ծանուցումներ
    
    /// <summary> Տրամադրման ձև</summary>
    public StatementDeliverModes StmtType { get; set; } = StatementDeliverModes.Bank;
    
    /// <summary> Ծանուցման ձև</summary>
    public string NotifMode { get; set; }
    
    /// <summary> Այլ ռեկվիզիտներ/ընդլայնված ռեկվիզիտներ (UDR)</summary>
    public Dictionary<string, string> OtherFieldValues { get; set; }
}
```

* [PassData](../types/PassData.md) դասի նկարագիր
* [Address](../types/Address.md) դասի նկարագիր
* [StatementDeliverModes](../types/StatementDeliverModes.md) դասի նկարագիր
