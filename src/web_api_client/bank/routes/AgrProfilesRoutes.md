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

`AgrProfilesRoutes` դասը պարունակում է մեթոդներ պայմանագրերը քեշավորման համար։  
Այն հասանելի է [`BankApiClient`](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### CacheClientContracts

```c#
public async Task<CacheClientContractsResponse> CacheClientContracts(CacheClientContractsRequest request)
```

Կատարում է հաճախորդի պայմանագրերի քեշավորում։

**Պարամետրեր**

* `request` -  [CacheClientContractsRequest](../types/CacheClientContractsRequest.md)  
   Հաճախորդի պայմանագրերի քեշավորման հարցման տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/AgrProfilesRoutes.md#օրինակ-1)։
