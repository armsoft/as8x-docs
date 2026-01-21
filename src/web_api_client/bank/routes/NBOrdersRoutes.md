---
layout: page
title: "NBOrdersRoutes դաս" 
sublinks:
- { title: "CreateNBInputOrder", ref: createnbinputorder }
- { title: "CreateNBOutputOrder", ref: createnboutputorder }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [CreateNBInputOrder](#createnbinputorder)
  - [CreateNBOutputOrder](#createnboutputorder)

## Ներածություն

`NBOrdersRoutes` դասը պարունակում է մեթոդներ ետհաշվեկշռային հաշիվների մուտքի/ելքի օրդերների ստեղծման համար։  
Այն հասանելի է [`BankApiClient`](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### CreateNBInputOrder

```c#
public Task<CreateNBOrderResponse> CreateNBInputOrder(CreateNBOrderRequest request)
```

Ստեղծում է Ե/Հ մուտքի օրդեր ստանալով անհրաժեշտ պարամետրերը։ Վերադարձնում է ստեղծված Ե/Հ մուտքի օրդերի ISN-ը։

**Պարամետրեր**

* `request` -  [CreateNBOrderRequest](../types/CreateNBOrderRequest.md)  
   Ստեղծվող Ե/Հ մուտքի օրդերի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/NBOrdersRoutes.md#օրինակ-1)։

### CreateNBOutputOrder

```c#
public Task<CreateNBOrderResponse> CreateNBOutputOrder(CreateNBOrderRequest request)
```

Ստեղծում է Ե/Հ ելքի օրդեր ստանալով անհրաժեշտ պարամետրերը։ Վերադարձնում է ստեղծված Ե/Հ ելքի օրդերի ISN-ը։

**Պարամետրեր**

* `request` -  [CreateNBOrderRequest](../types/CreateNBOrderRequest.md)  
   Ստեղծվող Ե/Հ ելքի օրդերի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/NBOrdersRoutes.md#օրինակ-2)։
