---
layout: page
title: PaymentDocsRoutes դաս
sublinks:
  - title: CreateCrPayOrd
    ref: createcrpayord
---

# Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [CreateCrPayOrd](#createcrpayord)

# Ներածություն

`PaymentDocsRoutes` դասը պարունակում է վճարային փաստաթղթերի ստեղծմանը վերաբերող REST API կանչեր։

Այն հասանելի է `BankApiClient` դասի միջից։

# Մեթոդներ

## CreateCrPayOrd

```csharp
public Task<OuterPaymentOrderResponse> CreateCrPayOrd(OuterPaymentOrderRequest request)
```

Ստեղծում է վճարման հանձնարարագիր փաստաթուղթ ստանալով անհրաժեշտ տվյալները։

Վերադարձնում է ստեղծված վճարման հանձնարարագրի Isn-ը։

### Պարամետրեր

#### request - [OuterPaymentOrderRequest](outerpaymentorderrequest)

Ստեղծվող վճարման հանձնարարագրի տվյալներ։

Տե՛ս [Օրինակ](#օրինակ)

```csharp
var request = new OuterPaymentOrderRequest
{
    // Լրացնել անհրաժեշտ դաշտերը
};

var response = await bankApiClient.PaymentDocs.CreateCrPayOrd(request);
```