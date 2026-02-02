---
layout: page
title: "PrematureChargesRoutes դաս" 
sublinks:
- { title: "PrematureRepaymentCharge", ref: prematurecharges }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [PrematureRepaymentCharge](#prematurecharges)

## Ներածություն

`PrematureChargesRoutes` դասը պարունակում է մեթոդներ վաղաժամկետ մարումից տույժի հաշվարկման համար։  
Այն հասանելի է [`BankApiClient`](../types/BankApiClient.md) դասից։

## Մեթոդներ

### PrematureRepaymentCharge

```c#
public Task<PrematureRepaymentChargeResponse> PrematureRepaymentCharge(PrematureRepaymentChargeRequest request)
```

Հաշվարկում է վաղաժամկետ մարումից տույժը։

**Պարամետրեր**

* `request` -  [PrematureRepaymentChargeRequest](../types/PrematureRepaymentChargeRequest.md)  
   Վաղաժամկետ մարումից տույժի հարցման տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/PrematureChargesRoutes.md#օրինակ-1)։
