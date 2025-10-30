---
layout: page
title: "NBAccountsRoutes դաս" 
sublinks:
- { title: "CreateNBAccount", ref: createnbaccount }
- { title: "GetNBAccountRemainder", ref: getnbaccountremainder }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [CreateNBAccount](#createnbaccount)
  - [GetNBAccountRemainder](#getnbaccountremainder)

## Ներածություն

`NBAccountsRoutes` դասը պարունակում է մեթոդներ ետհաշվեկշռային հաշիվների հետ աշխատանքը ապահովելու համար։  
Այն հասանելի է [`BankApiClient`](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### CreateNBAccount

```c#
public Task<CreateNBAccountResponse> CreateNBAccount(CreateNBAccountRequest request)
```

Ստեղծում է հաճախորդի ետհաշվեկշռային հաշիվ ստանալով Հ/Պ ետհաշվեկշռային հաշվի կոդը, հաճախորդին, արժույթը և հաշվի տիպը։
Վերադարձնում ստեղծված հաշվի համարը։

**Պարամետրեր**

* `request` - Ավելացվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/NBAccountsRoutes.md#օրինակ-1)։

### GetNBAccountRemainder

```c#
public Task<GetNBAccountRemainderResponse> GetNBAccountRemainder(GetNBAccountRemainderRequest request)
```

Վերադարձնում է հաճախորդի ետհաշվեկշռային հաշվի մնացորդը հաշվի արժույթով ստանալով հաշվեհամարը և հարկ եղած դեպքում մնացորդի ամսաթիվը։

**Պարամետրեր**

* `request` - Ետհաշվեկշռային հաշվի տվյալները։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/NBAccountsRoutes.md#օրինակ-2)։
