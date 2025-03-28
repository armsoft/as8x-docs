---
layout: page
title: "AppLogService սերվիս" 
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [Write](#write)
  - [Write](#write-1)

## Ներածություն

AppLogService դասը նախատեսված է հատուկ իրադարձությունների (տարբերակի փոփոխություն, Debug-ի գործարկում) մանրամասների տվյալների պահոցում գրանցվելու ֆունկցիոնալությունը ապահովելու համար։

## Մեթոդներ

### Write

```c#
public Task Write(AppLogInfo appLogInfo)
```

Գրանցում է հատուկ իրադարձության (տարբերակի փոփոխություն, Debug-ի գործարկում...) մանրամասները տվյալների պահոցում։

**Պարամետրեր**

* `appLogInfo` - [Հատուկ իրադարձության մանրամասները նկարագրող դասի օբյեկտ](../types/AppLogInfo.md):

### Write

```c#
public Task Write(string moduleCode, string operationCode, string comment, int objectISN, int baseISN)
```

Գրանցում է հատուկ իրադարձության (տարբերակի փոփոխություն, Debug-ի գործարկում...) մանրամասները տվյալների պահոցում։

**Պարամետրեր**

* `moduleCode` - Իրադարձության մոդուլի կոդ։
* `operationCode` - Իրադարձության գործողության կոդ։
* `comment` - Իրադարձությունը նկարագրող մեկնաբանություն։
* `objectISN` - Իրադարձությունը իրականացրած երկրորդային փաստաթղթի ներքին նույնականացման համար (isn)։
* `baseISN` - Իրադարձությունը իրականացրած հիմքային փաստաթղթի ներքին նույնականացման համար (isn)։
