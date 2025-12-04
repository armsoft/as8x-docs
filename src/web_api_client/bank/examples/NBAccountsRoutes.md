---
layout: page
title: "Օրինակ NBAccountsRoutes" 
sublinks:
- { title: "Օրինակ Create", ref: օրինակ-1 }
- { title: "Օրինակ GetRemainder", ref: օրինակ-2 }
---

## Բովանդակություն
- [Create-ի օգտագործման օրինակ](#օրինակ-1)
- [GetRemainder-ի օգտագործման օրինակ](#օրինակ-2)

## Օրինակ 1
Նոր ետհաշվեկշռային հաշվի ստեղծման օրինակ։

```c#
public static async Task Create(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է հաճախորդի ետհաշվեկշռային հաշիվ՝ նշելով Հ/Պ ետհաշվեկշռային հաշիվը, հաճախորդին, արժույթը և հաշվի տիպը
        var res = await apiClient.NBAccounts.Create(new()
        {
            BalAcc = "8000000",
            CliCode = "00000001",
            Cur = "000",
            AccType = "22"
        });

        Console.WriteLine(res.BalAcc);         //Վերադարձնում է ձևավորված հաշվի Հ/Պ կոդը
        Console.WriteLine(res.NBAcc);         //Վերադարձնում է ձևավորված հաշվի համարը
    }
    catch (ApiException ex)
    {
        // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
        Console.WriteLine(ex.Code);
        Console.WriteLine(ex.Message);
        Console.WriteLine(ex.StatusCode);
    }
}
```

## Օրինակ 2
Ետհաշվեկշռային հաշվի մնացորդի ստացման օրինակ։

```c#
public static async Task GetRemainder(BankApiClient apiClient)
{
    try
    {
        // Ստանում է ետհաշվեկշռային հաշվի մնացորդը, արժույթը և մնացորդի ամսաթիվը՝ նշելով հաշվեհամարը
        var res = await apiClient.NBAccounts.GetRemainder(new()
        {
            BalAcc = "8000000",
            NBAcc = "0000101"
        });

        Console.WriteLine(res.Remainder);         //Վերադարձնում է մնացորդը
        Console.WriteLine(res.Cur);         //Վերադարձնում է հաշվի արժույթը
        Console.WriteLine(res.Date);         //Վերադարձնում է մնացորդի ամսաթիվը
    }
    catch (ApiException ex)
    {
        // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
        Console.WriteLine(ex.Code);
        Console.WriteLine(ex.Message);
        Console.WriteLine(ex.StatusCode);
    }
}
```
