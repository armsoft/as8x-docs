---
layout: page
title: "CreateJuridicalClientByFullDataRequest դաս" 
---

Այս դասը նախատեսված է իրավաբանական անձ հաճախորդի ստեղծման համար։

Օգտագործվում է [ClientsRoutes](../routes/ClientsRoutes.md).[CreateJuridicalClientByFullData](../routes/ClientsRoutes.md#createjuridicalclientbyfulldata) մեթոդում։

```c#
public class CreateJuridicalClientByFullDataRequest
{
    // Ընդհանուր էջ
    /// <summary>Անվանում</summary>
    public string Name { get; set; }

    /// <summary>Անգլերեն անվանում</summary>
    public string NameEng { get; set; }

    /// <summary>ՀՎՀՀ</summary>
    public string TaxCode { get; set; }

    /// <summary>Գրանցման N</summary>
    public string RegNum { get; set; }

    /// <summary>Տրված</summary>
    public DateTime? RegDate { get; set; }

    /// <summary>Տիպ</summary>
    public string RegType { get; set; }

    /// <summary>Լուծարված</summary>
    public bool InActive { get; set; }

    /// <summary>Գործունեության ոլորտ</summary>
    public string Volort { get; set; }

    /// <summary>Գործունեության ոլորտ(ԿԲ)</summary>
    public string VolortCB { get; set; }

    /// <summary>Պետական կարգավիճակ</summary>
    public string StateStatus { get; set; }

    /// <summary>Հաճախորդի չափ</summary>
    public string ClientSize { get; set; }

    /// <summary>Պետ.գրանցման վկայականի համար</summary>
    public string RegistrationCertNumber { get; set; }

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

    /// <summary>Կազմ-Իրավ կարգավիճակ</summary>
    public string CompanyStatus { get; set; }

    /// <summary>Այլ կազմակերպական-իրավական ձև</summary>
    public string OtherCompanyStatus { get; set; }

    /// <summary>Սեփ. ձև.</summary>
    public string OwnType { get; set; }

    /// <summary>Այլ(վ. ռեգ.)</summary>
    public string OtherReg { get; set; }

    /// <summary>Իրավ. անձի եկամուտներ</summary>
    public decimal Income {  get; set; }

    /// <summary>Օտարերկր. մասնակց.</summary>
    public string ForeignPart { get; set; }

    /// <summary>Օտարերկր. պետ. մարմին</summary>
    public string ForeignRepublicDivision { get; set; }

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

    // Հասցե էջ
    /// <summary>Գրանցման հասցե</summary>
    public Address Address { get; set; }

    /// <summary>Փաստացի հասցե</summary>
    public Address CurrentAddress { get; set; }

    /// <summary>Լրացնել փաստացի հասցեն ըստ գրանցման հասցեի</summary>
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

* [Address](../types/Address.md) դասի նկարագիր
* [StatementDeliverModes](../types/StatementDeliverModes.md) դասի նկարագիր
