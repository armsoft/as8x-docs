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
            Date = new DateTime(2025, 1, 1),                   // Ամսաթիվ
            CliCode = "00000001",                              // Հաճախորդի կոդ
            Name = "Վարկային առաջարկ".ToArmenianANSI(),        // Անվանում
            NameEng = "Credit Offer",                          // Անգլերեն անվանում
            AppType = "",                                      // Հայտատեսակ
            Shablon = "0001",                                  // Ձևանմուշի N
            Amount = 500000,                                   // Սահմանաչափ
            InterestRate = new InterestRate                    // Տոկոսադրույք
            {
                Rate = 12,                           
                Divisor = Divisor.Yearly_365            
            },
            Duration = new Periodicity                         // Տևողություն
            {
                Month = 12,                             
                Day = 0                                 
            },
            EndDate = new DateTime(2026, 1, 1),                // Առաջարկի վերջնաժամկետ
            AccountNumber = "33069150300"                      // Հաշվարկային հաշիվ
        });

        Console.WriteLine(res.Code);                           // Ստեղծված վարկային առաջարկի կոդ
    }
    catch (ApiException ex)
    {
        Console.WriteLine(ex.Code);
        Console.WriteLine(ex.Message);
        Console.WriteLine(ex.StatusCode);
    }
}
```
