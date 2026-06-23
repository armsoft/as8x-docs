---
layout: page
title: Օրինակ CreditOffersRoutes
sublinks:
- { title: "Օրինակ Create", ref: օրինակ-1 }
---

## Բովանդակություն

- [Create-ի օգտագործման օրինակ](#օրինակ-1)

## Օրինակ 1

Վարկային առաջարկի ստեղծման օրինակ։

```csharp
public static async Task CreateCreditOffer(BankApiClient apiClient)
{
    try
    {
        var res = await apiClient.CreditOffers.Create(new()
        {
            Date = new DateTime(2025, 1, 1),           // Ամսաթիվ
            CliCode = "00000001",                       // Հաճախորդի կոդ
            Name = "Վարկային առաջարկ",                 // Անվանում
            NameEng = "Credit Offer",                   // Անգլերեն անվանում
            AppType = "01",                             // Հայտատեսակ
            Shablon = "001",                            // Ձևանմուշի N
            Amount = 500000,                            // Սահմանաչափ
            InterestRate = new InterestRate
            {
                Rate = 12.5m,                           // Տոկոսադրույք
                Divisor = Divisor.Yearly_365            // Բաժանարար
            },
            Duration = new Periodicity
            {
                Month = 12,                             // Ամիս
                Day = 0                                 // Օր
            },
            EndDate = new DateTime(2026, 1, 1),         // Առաջարկի վերջնաժամկետ
            AccountNumber = "1111110110070200"          // Հաշվարկային հաշիվ
        });

        Console.WriteLine(res.Code); // Ստեղծված վարկային առաջարկի կոդ
    }
    catch (ApiException ex)
    {
        Console.WriteLine(ex.Code);
        Console.WriteLine(ex.Message);
        Console.WriteLine(ex.StatusCode);
    }
}
```
