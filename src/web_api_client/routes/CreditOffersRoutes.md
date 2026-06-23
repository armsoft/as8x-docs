---
layout: page
title: "CreditOffersRoutes դաս"
sublinks:
- { title: "Create", ref: create }
---

## Բովանդակություն

- [Create](#create)

## Create

```csharp
public async Task<CreateResponse> Create(CreateRequest request)
```

Ստեղծում է վարկային առաջարկ։

**Պարամետրեր**

| Անուն | Տեսակ | Նկարագրություն |
|-------|-------|----------------|
| request | [CreateRequest](../types/CreditOfferCreateRequest.md) | Վարկային առաջարկի ստեղծման հարցման տվյալներ |

**Վերադարձվող արժեք**

[CreateResponse](../types/CreditOfferCreateResponse.md) — Ստեղծված վարկային առաջարկի տվյալներ։

**Օրինակ**

Տե՛ս [CreditOffersRoutes-ի օրինակ](../examples/CreditOffersRoutes.md)։
