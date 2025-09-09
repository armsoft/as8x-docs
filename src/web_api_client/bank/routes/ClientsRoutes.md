---
layout: page
title: "ClientsRoutes դաս" 
sublinks:
- { title: "CreateClientFromEkeng", ref: createclientfromekeng }
- { title: "CreatePhysicalClientByFullData", ref: createphysicalclientbyfulldata }
- { title: "CreateJuridicalClientByFullData", ref: createjuridicalclientbyfulldata }
- { title: "UpdatePhysicalClientData", ref: updatephysicalclientdata }
- { title: "UpdateJuridicalClientData", ref: updatejuridicalclientdata }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [CreateClientFromEkeng](#createclientfromekeng)
  - [CreatePhysicalClientByFullData](#createphysicalclientbyfulldata)
  - [CreateJuridicalClientByFullData](#createjuridicalclientbyfulldata)    
  - [UpdatePhysicalClientData](#updatephysicalclientdata)
  - [UpdateJuridicalClientData](#updatejuridicalclientdata)

## Ներածություն

ClientsRoutes դասը պարունակում է մեթոդներ հաճախորդների տվյալների հետ աշխատանքը ապահովելու համար։
Այն հասանելի է [BankApiClient](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### CreateClientFromEkeng

```c#
public Task<CreatePhysicalClientByFullDataResponse> CreateClientFromEkeng(
    CreateClientFromEkengRequest request)
```

Ստեղծում է ֆիզ. անձ հաճախորդ ստանալով նույնականացման փաստաթղթի համարը (սոց.քարտ, անձնագիր...), իսկ հիմնական տվյալները ստանալով [ԷԿԵՆԳ](https://www.ekeng.am) համակարգից:
Եթե այդ տվյալներով հաճախորդ առկա է համակարգում, ապա նոր հաճախորդ չի ստեղծվում։
Վերադարձնում հաճախորդի ստեղծված լինելու մասին տվյալներ՝ հաճախորդի կոդ, ստեղված հաճախորդի վիճակը վերջնական է, թե ոչ։

**Պարամետրեր**

* `request` - Ավելացվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-1)։

### CreatePhysicalClientByFullData

```c#
public Task<CreateClientResponse> CreatePhysicalClientByFullData(
    CreatePhysicalClientByFullDataRequest request)
```

Ստեղծում է նոր ֆիզ. անձ հաճախորդ ըստ հաճախորդի հիմնական տվյալների։ 
Վերադարձնում հաճախորդի ստեղծված լինելու մասին տվյալներ՝ հաճախորդի կոդ, ստեղված հաճախորդի վիճակը վերջնական է, թե ոչ։

**Պարամետրեր**

* `request` - Ավելացվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-2)։

### CreateJuridicalClientByFullData

```c#
public Task<CreateClientResponse> CreateJuridicalClientByFullData(
    CreateJuridicalClientByFullDataRequest request)
```

Ստեղծում է նոր իրավ. հաճախորդ ըստ հաճախորդի հիմնական տվյալների։ 
Վերադարձնում հաճախորդի ստեղծված լինելու մասին տվյալներ՝ հաճախորդի կոդ, ստեղված հաճախորդի վիճակը վերջնական է, թե ոչ։

**Պարամետրեր**

* `request` - Ավելացվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-3)։

### UpdatePhysicalClientData

```c#
public async Task UpdatePhysicalClientData(UpdatePhysicalClientDataRequest request)
```

Խմբագրում է ֆիզ. անձ հաճախորդի տվյալները ըստ փոխանցված տվյալների։

**Պարամետրեր**

* `request` - Խմբագրվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-4)։

### UpdateJuridicalClientData

```c#
public async Task UpdateJuridicalClientData(UpdateJuridicalClientDataRequest request)
```

Խմբագրում է իրավ. հաճախորդի տվյալները ըստ փոխանցված տվյալների։

**Պարամետրեր**

* `request` - Խմբագրվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-5)։
