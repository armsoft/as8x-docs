---
layout: page
title: "AgrProfilesRoutes դաս" 
sublinks:
- { title: "CacheClientContracts", ref: cacheclientcontracts }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [CacheClientContracts](#cacheclientcontracts)

## Ներածություն

`AgrProfilesRoutes` դասը պարունակում է մեթոդներ պայմանագրերի քեշավորման համար։  
Այն հասանելի է [`BankApiClient`](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### CreateNBInputOrder

```c#
public async Task<CreateNBOrderResponse> CreateNBInputOrder(CreateNBOrderRequest request)
```

Ստեղծում է Ե/Հ մուտքի օրդեր ստանալով անհրաժեշտ պարամետրերը։ Վերադարձնում է ստեղծված Ե/Հ մուտքի օրդերի ISN-ը։

**Պարամետրեր**

* `request` -  [CreateNBOrderRequest](../types/CreateNBOrderRequest.md)  
   Ստեղծվող Ե/Հ մուտքի օրդերի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/NBOrdersRoutes.md#օրինակ-1)։
