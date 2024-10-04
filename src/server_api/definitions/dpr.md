---
layout: page
title: "DPR Երկար աշխատող պրոցեսի նկարագրություն" 
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [DataProcessingRequest դաս](#dataprocessingrequest-դաս)
- [Հատկություններ](#հատկություններ)
  - [ArmenianCaption](#armeniancaption)
  - [EnglishCaption](#englishcaption)
  - [IsParametersSupported](#isparameterssupported)
  - [Name](#name)
  - [Progress](#progress)
  - [DPRType](#dprtype)
  - [IsCancellationSupported](#iscancellationsupported)
- [Մեթոդներ](#մեթոդներ)
  - [AfterDeserializeParameter](#afterdeserializeparameter)
  - [Execute](#execute)

## Ներածություն

Սերվիսային երկար տևող հարցումներ կատարելու և կատարման ընթացքին հետևելու համար նկարագրվում է երկար աշխատող պրոցես (DPR - Data Processing Request): 
Տե՛ս [Ասինխրոն մշակում կիրառությունների սերվերի վրա](../../architecture/appserver_async.md)։

8X-ում DPR նկարագրության համար հարկավոր է նկարագրել սերվերում աշխատող տրամաբանությունը C# դասում (`.cs` ֆայլում)։  
Հարկավոր է սահմնել մուտքային և ելթային պարամետրերի դասեր (կարող ենք օգտագործվել գոյություն ունեցողները)։

Կազմակերպության սեփական DPR-ների ստեղծման համար [տե՛ս](../../extensions/definitions/dpr_new_guide.md):

## DataProcessingRequest դաս

DPR-ի համար անհրաժեշտ է սահմանել դաս, որը ժառանգում է `DataProcessingRequest<R, P>` դասը՝ որպես R փոխանցելով DPR-ի կատարման արդյունքում ստացվող տվյալները նկարագրող դասը, իսկ որպես P՝ պարամետրերը նկարագրող դասը և ունի DPR-ի տեսակը, հայերեն, անգլերեն անվանումները պարունակող `DPR` ատրիբուտը։

**Օրինակ**

```c#
[DPR(DPRType = Common.DPRType.Other, ArmenianCaption = "Փաստաթղթի դաշտերի խմբագրում", EnglishCaption = "Document's fields' edition")]
public class EditDocumentsFields : DataProcessingRequest<EditFieldsResponse, EditFieldsRequest>
```

## Հատկություններ

### ArmenianCaption

```c#
public string ArmenianCaption { get; }
```

Վերադարձնում է հայերեն անվանումը ANSI կոդավորմամբ:

### EnglishCaption

```c#
public string EnglishCaption { get; }
```

Վերադարձնում է անգլերեն անվանումը:

<!-- ### IsParametersSupported

```c#
public bool IsParametersSupported { get; }
```

Ցույց է տալիս DPR-ի ունի պարամետրեր թե ոչ: -->

### Name

```c#
public string Name { get; }
```

Վերադարձնում է ներքին անունը: 
Այն նկարագրվող դասի անունն է, եթե տրված չէ DPR ատրիբուտի մեջ։

### Progress

```c#
public DataSourceExecutionProgress Progress { get; }
```

Վերադարձնում է DPR-ի կատարման պրոգրեսը:

Այս օբյեկտի միջոցով հնարավոր է կառավարել աշխատանքի փուլերը, UI-ում ցույց տալ այդ փուլերը և UI-ում ցույց տալ հաղորդագրության պատուհան (MessageBox):
Տե՛ս [օրինակ](../examples/dpr/code.cs)։


### DPRType

```c#
public DPRType DPRType { get; private set; }
```

Վերադարձնում է տեսակը, որը լրացված է նկարագրվող դասի վրա DPR ատրիբուտի մեջ։

### IsCancellationSupported

```c#
public virtual bool IsCancellationSupported { get { return true; } }
```

Այս մշակվող հատկության միջոցով հնարավոր է թույլատրել կամ արգելել UI-ից պրոցեսի դադարեցման (cancellation) հնարավորությունը։

## Մեթոդներ

### AfterDeserializeParameter

```c#
protected virtual Task AfterDeserializeParameter(P parameter, JsonElement jsonElement)
```

Մեթոդը կանչվում է միջուկի կողմից DPR-ը հերթագրման դնելուց առաջ։
Այն հարկավոր է մշակվել, եթե հարկավոր է փոխանցված պարամետրերի ստուգումներ կատարել, կամ մուտքային պարամետրերի ձևափոխել։
Մեթոդի կանչից առաջ `parameter`-ը արդեն իսկ ձևավորված է ըստ ցանցով փոխանցված JSON-ի։

**Պարամետրեր**

- `parameter` - Մուտքային պարամետրերի նկարագրված դասի օբյեկտ։ 
- `jsonElement` - Փոխանցված JSON օբյեկտի մեջ։

### Execute

```c#
public abstract Task<R> Execute(P p, CancellationToken stoppingToken)
```

Մեթոդը կանչվում է միջուկի կողմից, այստեղ հարկավոր է մշակել սերվերում աշխատող տրամաբանությունը։

**Պարամետրեր**

- `R` - Կատարման արդյունքում վերադարձվող տվյալները նկարագրող դաս:
- `p` - Մուտքային պարամետրերի նկարագրված դասի օբյեկտ։
- `stoppingToken` - Դադարեցման տոկենը։