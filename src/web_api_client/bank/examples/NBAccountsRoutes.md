---
layout: page
title: "Օրինակ NBAccountsRoutes" 
sublinks:
- { title: "Օրինակ CreateNBAccount", ref: օրինակ-1 }
- { title: "Օրինակ GetNBAccountRemainder", ref: օրինակ-2 }
---

## Բովանդակություն
- [CreateNBAccount-ի օգտագործման օրինակ](#օրինակ-1)
- [GetNBAccountRemainder-ի օգտագործման օրինակ](#օրինակ-2)

## Օրինակ 1
Նոր ետհաշվեկշռային հաշվի ստեղծման օրինակ։

```c#
public static async Task CreateNBAccount(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է հաճախորդի ետհաշվեկշռային հաշիվ՝ նշելով Հ/Պ ետհաշվեկշռային հաշիվը, հաճախորդին, արժույթը և հաշվի տիպը
        var res = await apiClient.NBAccounts.CreateGeneralAccForCli(new()
        {
            BalAcc = "8000000",
            CliCode = "00000001",
            Cur = "000",
            AccType = "22"
        });

        Console.WriteLine(res.AccCode);         //Վերադարձվում է ձևավորված հաշվի համարը
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
public static async Task GetNBAccountRemainder(BankApiClient apiClient)
{
    try
    {
        // Ստանում է ետհաշվեկշռային հաշվի մնացորդը, արժույթը և մնացորդի ամսաթիվը՝ նշելով հաշվեհամարը
        var res = await apiClient.NBAccounts.GetNBAccountRemainder(new()
        {
            AccountCode = "8000000/0000101"
        });

        Console.WriteLine(res.Remainder);         //Վերադարձվում է մնացորդը
        Console.WriteLine(res.Currency);         //Վերադարձվում է հաշվի արժույթը
        Console.WriteLine(res.Date);         //Վերադարձվում է մնացորդի ամսաթիվը
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
