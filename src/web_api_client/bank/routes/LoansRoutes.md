---
layout: page
title: "LoansRoutes դաս" 
sublinks:
- { title: "Create", ref: create }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [Create](#create)

## Ներածություն

LoansRoutes դասը պարունակում է մեթոդներ վարկային պայմանագրերի հետ աշխատանքը ապահովելու համար։
Այն հասանելի է [BankApiClient](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### Create

```c#
public Task<CreateResponse> Create(CreateRequest request)
```

Ստեղծում է գրաֆիկով վարկային պայմանագիր (C1Univer) ըստ փոխանցված տվյալների։
Եթե լրացված է `OuterParent` դաշտը, ապա պայմանագիրը ստեղծվում է որպես նշված արտաքին N-ով ծնող պայմանագրի զավակ։
Եթե `Name` դաշտը չի լրացվում, ապա որպես պայմանագրի անվանում գրանցվում է հաճախորդի անվանումը։
Վերադարձնում է ստեղծված պայմանագրի մասին տվյալներ՝ պայմանագրի կոդ, ISN, ստեղծված պայմանագրի վիճակը վերջնական է, թե ոչ։

**Պարամետրեր**

* `request` -  [CreateRequest](../types/Loans/CreateRequest.md)  
  Ստեղծվող վարկային պայմանագրի տվյալներ։

**Վերադարձվող արժեք**

* `response` -  [CreateResponse](../types/Loans/CreateResponse.md)  
  Ստեղծված պայմանագրի տվյալներ։

**Սխալներ**

Փոխանցված տվյալների ստուգման ժամանակ սխալի առաջացման դեպքում մեթոդը առաջացնում է `ApiException`, որի `Code` հատկությունը պարունակում է սխալի կոդը։

| Սխալի կոդ | Նկարագրություն |
|-----------|----------------|
| `required_outercode` | Արտաքին N դաշտը պարտադիր է։ |
| `required_date` | Կնքման ամսաթիվը պարտադիր է։ |
| `required_dategive` | Հատկացման ամսաթիվը պարտադիր է։ |
| `required_clicode` | Հաճախորդի կոդը պարտադիր է։ |
| `required_amount` | Պայմանագրի գումարը պարտադիր է։ |
| `required_shablon` | Ձևանմուշը պարտադիր է։ |
| `invalid_divisor_interestrate` | `InterestRate` տոկոսադրույքի բաժանարարի սխալ արժեք։ |
| `invalid_divisor_pcpenagr` | `PcPenAgr` տոկոսադրույքի բաժանարարի սխալ արժեք։ |
| `invalid_divisor_pcpenper` | `PcPenPer` տոկոսադրույքի բաժանարարի սխալ արժեք։ |
| `invalid_divisor_pcnochoose` | `PcNoChoose` տոկոսադրույքի բաժանարարի սխալ արժեք։ |
| `invalid_divisor_pcgrant` | `PcGrant` տոկոսադրույքի բաժանարարի սխալ արժեք։ |
| `invalid_divisor_pcloss` | `PcLoss` տոկոսադրույքի բաժանարարի սխալ արժեք։ |

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/LoansRoutes.md#օրինակ-1)։
