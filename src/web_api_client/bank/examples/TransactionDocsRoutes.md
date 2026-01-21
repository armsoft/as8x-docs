---
layout: page
title: "Օրինակ TransactionDocsRoutes" 
sublinks:
- { title: "Օրինակ CreateMemOrder", ref: օրինակ-1 }
- { title: "Օրինակ CreateCurrencyExchange", ref: օրինակ-2 }
---

## Բովանդակություն
- [CreateMemOrder-ի օգտագործման օրինակ](#օրինակ-1)
- [CreateCurrencyExchange-ի օգտագործման օրինակ](#օրինակ-2)

## Օրինակ 1
Հիշարար օրդերի ստեղծման օրինակ։

```c#
  public static async Task CreateMemOrder(BankApiClient apiClient)
  {
      try
      {
          var res = await apiClient.TransactionDocs.CreateMemOrder(new()
          {
              Date = new DateTime(2025, 1, 1), // Ամսաթիվ
              AccDb = "10110070200", // Հաշիվ դեբետ
              AccCr = "10099440301", // Հաշիվ կրեդիտ
              Currency = "000", // Արժույթ
              Amount = 100, // Գումար
              Aim = "Aim", // Նպատակ
              OuterID = "12345678", // Արտաքին N
              CheckBlackList = true // Կատարել սև ցուցակի ստուգում
          });

          Console.WriteLine(res.ISN);         //Վերադարձնում է ստեղծված հիշարար օրդերի Isn-ը
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
Արտարժույթի փոխանակման ստեղծման օրինակ։

```c#
  public static async Task CreateCurrencyExchange(BankApiClient apiClient)
  {
      try
      {
          var res = await apiClient.TransactionDocs.CreateCurrencyExchange(new()
          {
              Date = new DateTime(2025, 1, 1), // Ամսաթիվ
              AccDb = "10110070200", // Հաշիվ դեբետ
              AccCr = "10099440301", // Հաշիվ կրեդիտ
              CurrencyDb = "000", // Դեբետ հաշվի արժույթ
              CurrencyCr = "001", // Կրեդիտ հաշվի արժույթ
              AmountDb = 100, // Գումար դեբետ (դեբետ կամ կրեդիտ գումարներից առնվազն մեկը պետք է լրացնել)
              Aim = "Aim", // Նպատակ
              OuterID = "12345678", // Արտաքին N
              CheckBlackList = true // Կատարել սև ցուցակի ստուգում
          });

          Console.WriteLine(res.ISN);         //Վերադարձնում է ստեղծված արտարժույթի փոխանակման Isn-ը
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
