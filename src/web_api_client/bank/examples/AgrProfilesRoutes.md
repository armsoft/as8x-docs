---
layout: page
title: "Օրինակ AgrProfilesRoutes" 
sublinks:
- { title: "Օրինակ CacheClientContracts", ref: օրինակ-1 }
---

## Բովանդակություն
- [CacheClientContracts-ի օգտագործման օրինակ](#օրինակ-1)

## Օրինակ 1
Հաճախորդի պայմանագրերի քեշավորման օրինակ։

```c#
private static async Task CacheClientContracts(BankApiClient apiClient)
{
    try
    {
        // Կատարում է հաճախորդի պայմանագրերի քեշավորում՝ նշելով անհրաժեշտ տվյալները
        await apiClient.AgrProfiles.CacheClientContracts(new()
        {
            CliCode = "00000001", // Հաճախորդի կոդ
            Date = DateTime.Today, // Քեշավորման ամսաթիվ
            Subsystems = ["C1", "C3"] // Ենթահամակարգերի ցուցակ
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
