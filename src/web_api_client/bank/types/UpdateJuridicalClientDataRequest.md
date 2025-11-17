---
layout: page
title: "UpdateJuridicalClientDataRequest դաս" 
---

Այս դասը նախատեսված է իրավաբանական անձ հաճախորդի խմբագրման համար։

Օգտագործվում է [ClientsRoutes](../routes/ClientsRoutes.md).[UpdateJuridicalClientData](../routes/ClientsRoutes.md#updatejuridicalclientdata) մեթոդում։

```c#
public class UpdateJuridicalClientDataRequest
{
    /// <summary> Խմբագրվող Հաճախորդի կոդ</summary>
    public string ClientCode { get; set; }

    /// <summary> Նոր հեռախոսահամար </summary>
    public string NewMobile { get; set; }

    /// <summary> Նոր էլ. հասցե </summary>
    public string NewEmail { get; set; }

    /// <summary> Նոր քաղվածքի տրամադրման ձև </summary>
    public StatementDeliverModes? NewStmtType { get; set; } = null;

    /// <summary> Նոր փաստացի հասցե </summary>
    public Address NewCurrentAddress { get; set; } = null;

    /// <summary> Նոր գրանցման հասցե </summary>
    public Address NewRegAddress { get; set; } = null;

    /// <summary> true - գրանցման հասցեն լրացվում է որպես փաստացի հասցե </summary>
    public bool FillCurrentAddressAsReg { get; set; } = false;

    /// <summary> Ընդլայնված դաշտերի անունները և արժեքները </summary>
    public Dictionary<string, string> OtherFieldValues { get; set; }
}
```

* [PassData](../types/PassData.md) դասի նկարագիր
* [Address](../types/Address.md) դասի նկարագիր 
* [StatementDeliverModes](../types/StatementDeliverModes.md) enum-ի նկարագիր
