---
layout: page
title: "TransactionDocsRoutes դաս" 
sublinks:
- { title: "CreateMemOrder", ref: creatememorder }
- { title: "CreateCurrencyExchange", ref: createcurrencyexchange }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [CreateMemOrder](#creatememorder)
  - [CreateCurrencyExchange](#createcurrencyexchange)

## Ներածություն

`TransactionDocsRoutes` դասը պարունակում է մեթոդներ գործողությունների փաստաթղթերի հետ աշխատանքը ապահովելու համար։  
Այն հասանելի է [`BankApiClient`](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### CreateMemOrder

```c#
public Task<CreateMemOrderResponse> CreateMemOrder(CreateMemOrderRequest request)
```

Ստեղծում է հիշարար օրդեր փաստաթուղթ ստանալով անհրաժեշտ տվյալները։
Վերադարձնում է ստեղծված հիշարար օրդերի Isn-ը։

**Պարամետրեր**

* `request` -  [CreateMemOrderRequest](../types/CreateMemOrderRequest.md)  
    Ստեղծվող հիշարար օրդերի տվյալներ։
  
**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/TransactionDocsRoutes.md#օրինակ-1)։

### CreateCurrencyExchange

```c#
public Task<CreateCurrencyExchangeResponse> CreateCurrencyExchange(CreateCurrencyExchangeRequest request)
```

Ստեղծում է արտարժույթի փոխանակման փաստաթուղթ ստանալով անհրաժեշտ տվյալները։
Վերադարձնում է ստեղծված արտարժույթի փոխանակման Isn-ը։

**Պարամետրեր**

* `request` -  [CreateCurrencyExchangeRequest](../types/CreateCurrencyExchangeRequest.md)  
    Ստեղծվող արտարժույթի փոխանակման տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/TransactionDocsRoutes.md#օրինակ-2)։
