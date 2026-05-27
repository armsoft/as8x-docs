---
layout: page
title: PaymentDocsRoutes դաս
sublinks:
  - title: CreateCreditPaymentOrder
    ref: createcreditpaymentorder
---

# Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [CreateCreditPaymentOrder](#createcreditpaymentorder)

# Ներածություն

`PaymentDocsRoutes` դասը պարունակում է վճարային փաստաթղթերի ստեղծմանը վերաբերող REST API կանչեր։

Այն հասանելի է `BankApiClient` դասի միջից։

# Մեթոդներ

## CreateCreditPaymentOrder

```csharp
public Task<CreateCreditPaymentOrderResponse> CreateCreditPaymentOrder(CreateCreditPaymentOrderRequest request)
```

Ստեղծում է վճարման հանձնարարագիր փաստաթուղթ ստանալով անհրաժեշտ տվյալները։

Վերադարձնում է ստեղծված վճարման հանձնարարագրի Isn-ը։

### Պարամետրեր

* `request` - [CreateCreditPaymentOrderRequest](../types/CreateCreditPaymentOrderRequest.md)
  
Ստեղծվող վճարման հանձնարարագրի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/TransactionDocsRoutes.md#օրինակ-1)։
```
