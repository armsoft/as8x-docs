---
layout: page
title: "Օրինակ NBOrdersRoutes" 
sublinks:
- { title: "Օրինակ CreateNBInputOrder", ref: օրինակ-1 }
- { title: "Օրինակ CreateNBOutputOrder", ref: օրինակ-2 }
---

## Բովանդակություն
- [CreateNBInputOrder-ի օգտագործման օրինակ](#օրինակ-1)
- [CreateNBOutputOrder-ի օգտագործման օրինակ](#օրինակ-2)

## Օրինակ 1
Ե/Հ մուտքի օրդեր ստեղծման օրինակ։

```c#
private static async Task CreateNBInputOrder(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է Ե/Հ մուտքի օրդեր՝ նշելով անհրաժեշտ տվյալները
        var res = await apiClient.NBAccounts.CreateNBInputOrder(new()
        {
            Date = new DateTime(2025,1,1), // Ամսաթիվ
            BalAcc = "8000000", // Ետհաշվեկշռային հաշվի Հ/Պ
            NBAcc = "10120028", // Հ/Պ ետհաշվեկշռային հաշիվ
            Cur = "000", // Արժույթ
            Count = 0, // Քանակ
            Amount = 100, // Գումար
            PayerReceiverName = "Մուտք Անողը".ToArmenianANSI(), // Արժեքները մուտք անող
            Base = "Հիմք".ToArmenianANSI(), // Հիմք
            Aim = "Նպատակ".ToArmenianANSI(), // Նպատակ
            OuterCode = "12345678" // Արտաքին N
        });
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

## Օրինակ 2
Ե/Հ ելքի օրդեր ստեղծման օրինակ։

```c#
private static async Task CreateNBOutputOrder(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է Ե/Հ ելքի օրդեր՝ նշելով անհրաժեշտ տվյալները
        var res = await apiClient.NBAccounts.CreateNBOutputOrder(new()
        {
            Date = new DateTime(2025,1,1), // Ամսաթիվ
            BalAcc = "8000000", // Ետհաշվեկշռային հաշվի Հ/Պ
            NBAcc = "10120028", // Հ/Պ ետհաշվեկշռային հաշիվ
            Cur = "000", // Արժույթ
            Count = 0, // Քանակ
            Amount = 100, // Գումար
            PayerReceiverName = "Մուտք Անողը".ToArmenianANSI(), // Արժեքները ստացող
            Base = "Հիմք".ToArmenianANSI(), // Հիմք
            Aim = "Նպատակ".ToArmenianANSI(), // Նպատակ
            OuterCode = "12345679" // Արտաքին N
        });
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
