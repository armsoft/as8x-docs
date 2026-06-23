---
layout: page
title: CreditOffersRoutes դաս
sublinks:
- { title: "Create", ref: create }
---


## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [Create](#create)

## Ներածություն

`CreditOffersRoutes` դասը պարունակում է մեթոդներ վարկային առաջարկների հետ աշխատանքը ապահովելու համար։  
Այն հասանելի է [`BankApiClient`](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### Create

```csharp
public Task<CreateResponse> Create(CreateRequest request)
```

Ստեղծում է վարկային առաջարկ ստանալով անհրաժեշտ տվյալները։

Վերադարձնում է ստեղծված վարկային առաջարկի կոդը։

**Պարամետրեր**

* `request` - [CreateRequest](../types/CreditOfferCreateRequest.md)
  
Ստեղծվող վարկային առաջարկի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/CreditOffersRoutes.md#օրինակ-1)։


---
