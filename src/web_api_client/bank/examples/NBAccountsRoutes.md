---
layout: page
title: "Օրինակ NBAccountsRoutes" 
sublinks:
- { title: "Օրինակ CreateNBAccount", ref: օրինակ-1 }
---

## Բովանդակություն
- [CreateNBAccount-ի օգտագործման օրինակ](#օրինակ-1)

## Օրինակ 1
Նոր ետհաշվեկշռային հաշվի ստեղծման օրինակ։

```c#
public static async Task CreateNBAccount(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է հաճախորդի ետհաշվեկշռային հաշիվ՝ նշելով Հ/Պ ետհաշվեկշռային հաշիվը, հաճախորդին, արժույթը և հաշվի տիպը
        var res = await apiClient.Accounts.CreateGeneralAccForCli(new()
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
