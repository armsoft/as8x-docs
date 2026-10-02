---
layout: page
title: CreateRequest դաս
---

Այս դասը նախատեսված է վարկային հայտի ստեղծման համար։

Օգտագործվում է [LoanApplicationsRoutes](../../routes/LoanApplicationsRoutes.md).[Create](../../routes/LoanApplicationsRoutes.md#create) մեթոդում։

```csharp
public class CreateRequest
{
    /// <summary>Հայտի ամսաթիվ</summary> 
    public DateTime Date { get; set; }

    /// <summary>Հաճախորդի կոդ</summary> 
    public string CliCode { get; set; }

    /// <summary>Հայտատեսակ</summary> 
    public string AppType { get; set; }

    /// <summary>Մեկնաբանություն</summary>
    public string Comment { get; set; }

    /// <summary>Գումար</summary>
    public decimal Amount { get; set; }

    /// <summary>Տևողություն</summary>
    public Periodicity Duration { get; set; }

    /// <summary>Մարման օր</summary>
    public short RepayDay { get; set; }

    /// <summary>Գումարի ստացման եղանակ</summary>
    public ReceiveMethod ReceiveMethod { get; set; }

    /// <summary>Հաշվարկային հաշիվ</summary>
    public string AccountNumber { get; set; }

    /// <summary>Շահառուի անվանում</summary>
    public string RespName { get; set; }

    /// <summary>Քարտի համար</summary>
    public string CardNumber { get; set; }

    /// <summary>Քարտի անվանում</summary>
    public string CardName { get; set; }
}
```

* [Periodicity](../../types/Periodicity.md) դասի նկարագիր
* [ReceiveMethod](../../types/LoanApplications/ReceiveMethod.md) enum-ի նկարագիր
