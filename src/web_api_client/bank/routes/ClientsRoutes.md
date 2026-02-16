---
layout: page
title: "ClientsRoutes դաս" 
sublinks:
- { title: "CreateClientFromEkeng", ref: createclientfromekeng }
- { title: "CreateJuridicalClientByFullData", ref: createjuridicalclientbyfulldata }
- { title: "CreatePhysicalClientByFullData", ref: createphysicalclientbyfulldata }
- { title: "GetJuridicalClientData", ref: getjuridicalclientdata }
- { title: "GetPhysicalClientData", ref: getphysicalclientdata }
- { title: "UpdateJuridicalClientData", ref: updatejuridicalclientdata }
- { title: "UpdatePhysicalClientData", ref: updatephysicalclientdata }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [CreateClientFromEkeng](#createclientfromekeng)
  - [CreateJuridicalClientByFullData](#createjuridicalclientbyfulldata)    
  - [CreatePhysicalClientByFullData](#createphysicalclientbyfulldata)
  - [GetJuridicalClientData](#getjuridicalclientdata)
  - [GetPhysicalClientData](#getphysicalclientdata)
  - [UpdateJuridicalClientData](#updatejuridicalclientdata)
  - [UpdatePhysicalClientData](#updatephysicalclientdata)

## Ներածություն

ClientsRoutes դասը պարունակում է մեթոդներ հաճախորդների տվյալների հետ աշխատանքը ապահովելու համար։
Այն հասանելի է [BankApiClient](../types/BankApiClient.md) դասի միջից։

## Մեթոդներ

### CreateClientFromEkeng

```c#
public Task<CreateClientResponse> CreateClientFromEkeng(
    CreateClientFromEkengRequest request)
```

Ստեղծում է ֆիզ. անձ հաճախորդ ստանալով նույնականացման փաստաթղթի համարը (սոց.քարտ, անձնագիր...), իսկ հիմնական տվյալները ստանալով [ԷԿԵՆԳ](https://www.ekeng.am) համակարգից:
Եթե այդ տվյալներով հաճախորդ առկա է համակարգում, ապա նոր հաճախորդ չի ստեղծվում։
Վերադարձնում հաճախորդի ստեղծված լինելու մասին տվյալներ՝ հաճախորդի կոդ, ստեղված հաճախորդի վիճակը վերջնական է, թե ոչ։

**Պարամետրեր**

* `request` - Ավելացվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-1)։

### CreateJuridicalClientByFullData

```c#
public Task<CreateClientResponse> CreateJuridicalClientByFullData(
    CreateJuridicalClientByFullDataRequest request)
```

Ստեղծում է նոր իրավ. հաճախորդ ըստ հաճախորդի հիմնական տվյալների։ 
Վերադարձնում հաճախորդի ստեղծված լինելու մասին տվյալներ՝ հաճախորդի կոդ, ստեղված հաճախորդի վիճակը վերջնական է, թե ոչ։

**Պարամետրեր**

* `request` -  [CreateJuridicalClientByFullDataRequest](../types/CreateJuridicalClientByFullDataRequest.md)  
  Ավելացվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-2)։

### CreatePhysicalClientByFullData

```c#
public Task<CreateClientResponse> CreatePhysicalClientByFullData(
    CreatePhysicalClientByFullDataRequest request)
```

Ստեղծում է նոր ֆիզ. անձ հաճախորդ ըստ հաճախորդի հիմնական տվյալների։ 
Վերադարձնում հաճախորդի ստեղծված լինելու մասին տվյալներ՝ հաճախորդի կոդ, ստեղված հաճախորդի վիճակը վերջնական է, թե ոչ։

**Պարամետրեր**

* `request` -  [CreatePhysicalClientByFullDataRequest](../types/CreatePhysicalClientByFullDataRequest.md)  
  Ավելացվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-3)։

### GetJuridicalClientData

```c#
public Task<GetJuridicalClientDataResponse> GetJuridicalClientData(GetClientDataRequest request)
```

Վերադարձնում է իրավաբանական անձ հաճախորդի տվյալները ըստ հաճախորդի կոդի կամ ըստ հաճախորդի արտաքին կոդի։

**Պարամետրեր**

* `request` -  [GetClientDataRequest](../types/GetClientDataRequest.md)  
   Փնտրվող հաճախորդի տվյալներ։
  
**Վերադարձվող արժեք**

* `response` -  [GetJuridicalClientDataResponse](../types/GetJuridicalClientDataResponse.md)  
   Հաճախորդի վերադարձվող տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-4)։

### GetPhysicalClientData

```c#
public Task<GetPhysicalClientDataResponse> GetPhysicalClientData(GetClientDataRequest request)
```

Վերադարձնում է ֆիզիկական անձ հաճախորդի տվյալները ըստ հաճախորդի կոդի կամ ըստ հաճախորդի արտաքին կոդի։

**Պարամետրեր**

* `request` -  [GetClientDataRequest](../types/GetClientDataRequest.md)  
   Փնտրվող հաճախորդի տվյալներ։

**Վերադարձվող արժեք**

* `response` -  [GetPhysicalClientDataResponse](../types/GetPhysicalClientDataResponse.md)  
   Հաճախորդի վերադարձվող տվյալներ։
  
**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-5)։

### UpdateJuridicalClientData

```c#
public Task<UpdateClientResponse> UpdateJuridicalClientData(UpdateJuridicalClientDataRequest request)
```

Խմբագրում է իրավաբանական անձ հաճախորդի տվյալները ըստ փոխանցված տվյալների։

**Պարամետրեր**

* `request` -  [UpdateJuridicalClientDataRequest](../types/UpdateJuridicalClientDataRequest.md)  
   Խմբագրվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-6)։

### UpdatePhysicalClientData

```c#
public Task<UpdateClientResponse> UpdatePhysicalClientData(UpdatePhysicalClientDataRequest request)
```

Խմբագրում է ֆիզ. անձ հաճախորդի տվյալները ըստ փոխանցված տվյալների։

**Պարամետրեր**

* `request` -  [UpdatePhysicalClientDataRequest](../types/UpdatePhysicalClientDataRequest.md)  
   Խմբագրվող հաճախորդի տվյալներ։

**Օրինակ**

Տե՛ս օգտագործման [օրինակը](../examples/ClientsRoutes.md#օրինակ-7)։

