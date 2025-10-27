---
layout: page
title: "UpdatePhysicalClientDataRequest դաս" 
---

Այս դասը նախատեսված է ֆիզիկական անձ հաճախորդի խմբագրման համար։

Օգտագործվում է [ClientsRoutes](../routes/ClientsRoutes.md).[UpdatePhysicalClientData](../routes/ClientsRoutes.md#updatephysicalclientdata) մեթոդում։

```c#
public class UpdatePhysicalClientDataRequest
{
    /// <summary> Խմբագրվող Հաճախորդի կոդ </summary>
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

    /// <summary> Տվյալների թարմացում ԷԿԵՆԳ-ից </summary>
    public bool? UpdateFromEkeng { get; set; }

    /// <summary> Անձնագրի տվյալներ </summary>
    public PassData Passport { get; set; } = null;

    /// <summary> Անձնագրի տվյալներ 2 </summary>
    public PassData Passport2 { get; set; } = null;

    /// <summary> Ընդլայնված դաշտերի անունները և արժեքները </summary>
    public Dictionary<string, string> OtherFieldValues { get; set; }
}
```

* [PassData](../types/PassData.md) դասի նկարագիր
* [Address](../types/Address.md) դասի նկարագիր 
* [StatementDeliverModes](../types/StatementDeliverModes.md) դասի նկարագիր
