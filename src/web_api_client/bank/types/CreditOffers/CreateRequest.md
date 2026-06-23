---
layout: page
title: CreditOffer.CreateRequest դաս
---

Այս դասը նախատեսված է վարկային առաջարկի ստեղծման համար։

Օգտագործվում է [CreditOffersRoutes](.../routes/CreditOffersRoutes.md).[Create](.../routes/CreditOffersRoutes.md#create) մեթոդում։

```csharp
public class CreateRequest
{
    /// <summary> Ամսաթիվ </summary>
    public DateTime Date { get; set; }

    /// <summary> Հաճախորդի կոդ </summary>
    public string CliCode { get; set; }

    /// <summary> Անվանում </summary>
    public string Name { get; set; }

    /// <summary> Անգլերեն անվանում </summary>
    public string NameEng { get; set; }

    /// <summary> Հայտատեսակ </summary>
    public string AppType { get; set; }

    /// <summary> Ձևանմուշի N </summary>
    public string Shablon { get; set; }

    /// <summary> Սահմանաչափ </summary>
    public decimal Amount { get; set; }

    /// <summary> Տոկոսադրույք </summary>
    public InterestRate InterestRate { get; set; }

    /// <summary> Տևողություն </summary>
    public Periodicity Duration { get; set; }

    /// <summary> Առաջարկի վերջնաժամկետ </summary>
    public DateTime EndDate { get; set; }

    /// <summary> Հաշվարկային հաշիվ </summary>
    public string AccountNumber { get; set; }
}
```
