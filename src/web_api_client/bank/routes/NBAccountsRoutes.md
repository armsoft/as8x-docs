---
layout: page
title: "NBAccountsRoutes դաս" 
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

`NBAccountsRoutes` դասը պարունակում է մեթոդներ ետհաշվեկշռային հաշիվների հետ աշխատանքը ապահովելու համար։  
Այն հասանելի է [`BankApiClient`](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### CreateNBInputOrder

```c#
public async Task<CreateNBOrderResponse> CreateNBInputOrder(CreateNBOrderRequest request)
```

Ստեղծում է Ե/Հ մուտքի օրդեր ստանալով անհրաժեշտ պարամտերերը։
Վերադարձնում է կարգավիճակ, որը ցույց է տալիս գործողությունը բարեհաջող է անցել, թե՝ ոչ։

**Պարամետրեր**

* `request` -  [CreateNBOrderRequest](../types/CreateNBOrderRequest.md)  
   Ստեղծվող Ե/Հ մուտքի օրդերի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/NBAccountsRoutes.md#օրինակ-3)։

### CreateNBOutputOrder

```c#
public async Task<CreateNBOrderResponse> CreateNBOutputOrder(CreateNBOrderRequest request)
```

Ստեղծում է Ե/Հ ելքի օրդեր ստանալով անհրաժեշտ պարամտերերը։
Վերադարձնում է կարգավիճակ, որը ցույց է տալիս գործողությունը բարեհաջող է անցել, թե՝ ոչ։

**Պարամետրեր**

* `request` -  [CreateNBOrderRequest](../types/CreateNBOrderRequest.md)  
   Ստեղծվող Ե/Հ ելքի օրդերի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/NBAccountsRoutes.md#օրինակ-4)։
