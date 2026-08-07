---
layout: page
title: "LoanApplicationsRoutes դաս" 
sublinks:
- { title: "Create", ref: create }
- { title: "GetAll", ref: getall }
- { title: "GetPrintForms", ref: getprintforms }
- { title: "Sign", ref: sign }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [Create](#create)
  - [GetAll](#getall)
  - [GetPrintForms](#getprintforms)
  - [Sign](#sign)

## Ներածություն

`LoanApplicationsRoutes` դասը պարունակում է մեթոդներ հաճախորդների տվյալների հետ աշխատանքը ապահովելու համար։
Այն հասանելի է [`BankApiClient`](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### Create

```c#
public Task<CreateResponse> Create(CreateRequest request)
```

Ստեղծում է վարկային հայտ ըստ հաճախորդի հայտի տվյալների։

Վերադարձնում է ստեղծված վարկային առաջարկի կոդը` [CreateResponse](../types/LoanApplications/CreateResponse.md)։

**Պարամետրեր**

* `request` - [CreateRequest](../types/LoanApplications/CreateRequest.md)
* Բացվող վարկային հայտի տվյալները։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/LoanApplicationsRoutes.md#օրինակ-1)։

### GetAll

```c#
public Task<GetAllResponse> GetAll(GetAllRequest request)
```

Վերադարձնում է հաճախորդի բոլոր վարկային հայտերի տվյալները՝ [GetAllResponse](../types/LoanApplications/GetAllResponse.md)։

**Պարամետրեր**

* `request` - [GetAllRequest](../types/LoanApplications/GetAllRequest.md)
* Հաճախորդի և վարկային հայտի տվյալները՝ հաճախորդի կոդ, հայտի համար:

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/LoanApplicationsRoutes.md#օրինակ-4)։

### GetPrintForms

```c#
public Task<LoanApplications.GetPrintFormsResponse> GetPrintForms(GetPrintFormsRequest request)
```

Վերադարձնում է վարկային հայտի լրացված տպելու ձևանմուշների տվյալները և պարունակությունը ցուցակով՝ [GetPrintFormsResponse](../types/LoanApplications/GetPrintFormsResponse.md)։
Հնարավոր է ստանալ «Պայմանագիրը», «Արբիտրաժային համաձայնագիրը» և «Անհատական թերթիկ»։

**Պարամետրեր**

* `request` - [GetPrintFormsRequest](../types/LoanApplications/GetPrintFormsRequest.md)
* Վարկային հայտի կոդը և անհրաժեշտ տպելու ձևանմուշների տեսակների ցուցակը։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/LoanApplicationsRoutes.md#օրինակ-3)։

### Sign

```c#
public Task<SignResponse> Sign(SignRequest request)
```

Հաստատում կամ մերժում է վարկային հայտը, եթե այն գտնվում է համապատասխան վիճակում։

**Պարամետրեր**

* `request` - [SignRequest](../types/LoanApplications/SignRequest.md)
* Վարկային հայտի տվյալները և կատարվող գործողության տեսակը՝ մերժում կամ հաստատում։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/LoanApplicationsRoutes.md#օրինակ-2)։
