---
layout: page
title: Օրինակ LoansRoutes
sublinks:
- { title: "Օրինակ Create", ref: օրինակ-1 }
---

## Բովանդակություն

- [Create-ի օգտագործման օրինակ](#օրինակ-1)

## Օրինակ 1


```c#
public static async Task CreateLoan(BankApiClient apiClient)
{
    try
    {
        var res = await apiClient.Loans.Create(new()
        {
            OuterCode = "TEST0001",                                       // արտաքին N
            Date = new DateTime(2026, 9, 29),                             // կնքման ամսաթիվ
            DateGive = new DateTime(2026, 9, 29),                         // հատկացման ամսաթիվ
            DateAgr = new DateTime(2028, 9, 29),                          // մարման ամսաթիվ
            CliCode = "00000001",                                         // հաճախորդի կոդ
            Name = "Հաճախորդ 00000001".ToArmenianANSI(),                  // անվանում (չլրացնելու դեպքում կգրվի հաճախորդի անվանումը)
            Amount = 1000000,                                             // պայմանագրի գումար
            InterestRate = new InterestRate { Rate = 12, Divisor = Divisor.Yearly_365 }, // տոկոսադրույք
            Comment = "Վարկի ստեղծում".ToArmenianANSI(),                  // մեկնաբանություն
            Shablon = "0064",                                             // ձևանմուշ
            Sector = "01.1/3",                                            // ճյուղայնություն
            Schedule = "9",                                               // ծրագիր
            Guarantee = "9",                                              // երաշխավորություն
            PcPenAgr = new InterestRate { Rate = 0.5m, Divisor = Divisor.Daily },      // ժամկետանց գումարի տույժ
            PcPenPer = new InterestRate { Rate = 0.5m, Divisor = Divisor.Daily },      // ժամկետանց տոկոսի տույժ
            PcGrant = new InterestRate { Rate = 0, Divisor = Divisor.Yearly_365 },     // սուբսիդավորման տոկոսադրույք
            PerCalcStart = new DateTime(2026, 10, 29),                    // տոկոսների հաշվարկների սկիզբ
            CalcFinPer = true,                                            // հաշվարկել ԲՏՀԴ տոկոսագումարը
            TimeOp = new TimeSpan(8, 0, 0),                               // գործարքի ժամ
            Codebtors =                                                   // համավարկառուներ
            [
                new() { CliCode = "00000002", Proportion = 50, SRCSend = false }
            ],
            Notes =                                                     // նշումներ
            [
                new() { Code = "1", Value = "Թեստ".ToArmenianANSI() }
            ],
            OtherScheduleRows =                                           // այլ մարումների գրաֆիկի տողեր
            [
                new() { Date = new DateTime(2026, 10, 29), Amount = 10000, Comment = "տող 1".ToArmenianANSI() },
                new() { Date = new DateTime(2026, 11, 29), Amount = 15000, Comment = "տող 2".ToArmenianANSI() },
                new() { Date = new DateTime(2026, 12, 29), Amount = 20000, Comment = "տող 3".ToArmenianANSI() }
            ],
            OtherFieldValues = new()                                      // ընդլայնված ռեկվիզիտներ (UDR)
            {
                ["UDRPERCON"] = "ABC"
            }
        });

        Console.WriteLine(res.Code);          // տպում է ստեղծված պայմանագրի կոդը
        Console.WriteLine(res.ISN);           // պայմանագրի ISN-ը
        Console.WriteLine(res.IsFinalState);  // պայմանագիրը վերջնական վիճակում է, թե ոչ
    }
    catch (ApiException ex)
    {
        // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
        Console.WriteLine(ex.Code); // սխալի կոդ
        Console.WriteLine(ex.Message); // սխալի հաղորդագրություն
        Console.WriteLine(ex.StatusCode); // սխալի վիճակի կոդ
    }
}
```
