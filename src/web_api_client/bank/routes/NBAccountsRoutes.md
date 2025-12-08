---
layout: page
title: "NBAccountsRoutes դաս" 
sublinks:
- { title: "Create", ref: create }
- { title: "GetRemainder", ref: getremainder }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [Create](#create)
  - [GetRemainder](#getremainder)

## Ներածություն

`NBAccountsRoutes` դասը պարունակում է մեթոդներ ետհաշվեկշռային հաշիվների հետ աշխատանքը ապահովելու համար։  
Այն հասանելի է [`BankApiClient`](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### Create

```c#
public Task<CreateNBAccountResponse> Create(CreateNBAccountRequest request)
```

Ստեղծում է հաճախորդի ետհաշվեկշռային հաշիվ ստանալով Հ/Պ ետհաշվեկշռային հաշվի կոդը, հաճախորդին, արժույթը և հաշվի տիպը։
Վերադարձնում ստեղծված հաշվի համարը։

**Պարամետրեր**

* `request` - Ավելացվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/NBAccountsRoutes.md#օրինակ-1)։

### GetRemainder

```c#
public Task<GetNBAccountRemainderResponse> GetRemainder(GetNBAccountRemainderRequest request)
```

Վերադարձնում է հաճախորդի ետհաշվեկշռային հաշվի մնացորդը հաշվի արժույթով, հաշվի արժույթը և մնացորդի ամսաթիվը ստանալով հաշվեհամարը և հարկ եղած դեպքում մնացորդի ամսաթիվը։

**Պարամետրեր**

* `request` - Ետհաշվեկշռային հաշվի տվյալները։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/NBAccountsRoutes.md#օրինակ-2)։
