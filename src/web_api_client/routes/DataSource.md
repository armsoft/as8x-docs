---
layout: page
title: "DataSource" 
tags : DS
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Հատկություններ](#հատկություններ)
  - [Client](#client)
  - [Definition](#definition)
  - [FetchSize](#fetchsize)
  - [FirstFetchSize](#firstfetchsize)
  - [ShowProgress](#showprogress)
  - [EncodeResultUnicode](#encoderesultunicode)
- [Մեթոդներ](#մեթոդներ)
  - [ExecuteAsync](#executeasync)
  - [LoadDefinitionAsync](#loaddefinitionasync)
  - [LongExecuteAsync](#longexecuteasync)

## Ներածություն

DataSource դասը նախատեսված է Client ծրագրից Web API-ների միջոցով տվյալների աղբյուրը կատարելու և կատարման արդյունքը վերադարձնելու ֆունկցիոնալությունը ապահովելու համար։

## Հատկություններ

### Client

```c#
public ApiClient Client { get; set; }
```

Վերադարձնում կամ նշանակում է `ApiClient` դասի օբյեկտ, որը նախատեսված է տվյալների աղբյուրի կատարման ընթացքում կլիենտից դեպի սերվեր անհրաժեշտ հարցումներ կատարելու համար։

### Definition

```c#
public DataSourceDefinition Definition { get; set; }
```

Վերադարձնում կամ նշանակում է տվյալների աղբյուրի նկարագրությունը, որը պարունակում է տվյալների աղբյուրի, սյուների և պարամետրերի հատկությունները։

Տվյալների աղբյուրի նկարագրությունը կարելի է ստանալ `DefinitionsCache` դասի `GetDataSourceDefinition` մեթոդի միջոցով։

### FetchSize

```c#
public int FetchSize { get; set; }
```

Տվյալների աղբյուրի կատարման արդյունքում վերադարձվող տողերը սերվիսից կլիենտ բեռնվում են բլոկ առ բլոկ։

Այս հատկությունը վերադարձնում կամ նշանակում է բեռնման յուրաքանչյուր բլոկի տողերի քանակը՝ բացառությամբ առաջինի։

### FirstFetchSize

```c#
public int FirstFetchSize { get; set; }
```

Տվյալների աղբյուրի կատարման արդյունքում վերադարձվող տողերը սերվիսից կլիենտ բեռնվում են բլոկ առ բլոկ։

Այս հատկությունը վերադարձնում կամ նշանակում է բեռնման առաջին բլոկի տողերի քանակը։

### ShowProgress

```c#
public bool ShowProgress { get; set; }
```

Վերադարձնում կամ նշանակում է տվյալների աղբյուրը կատարման և բեռնման գործընթացի պրոգրեսի պատուհանով ցուցադրման հայտանիշը։

### EncodeResultUnicode

```c#
public bool EncodeResultUnicode { get; set; }
```

Վերադարձնում կամ նշանակում է, արդյոք տվյալների աբյուրի տողերի կոդավորումը `Unicode` է, թե ոչ։ 

## Մեթոդներ

### ExecuteAsync

```c#
public Task<DataSourceResult<R>> ExecuteAsync(P param, HashSet<string> columns = default, string isn = null,
                                              CancellationToken cancellationToken = default, TimeSpan? timeout = null)
```

Կատարում է տվյալների աղբյուրը, վերադարձնում ստացված տողերի ցուցակը և կատարման ընթացքում առաջացած սխալների մանրամասն տեղեկությունը։

Այս մեթոդը անհրաժեշտ է օգտագործել այնպիսի տվյալների աղբյուրների կատարման համար, որոնց կատարման ժամանակը չի գերազանցում 180 վայրկյանը։

**Պարամետրեր**

* `param` - Տվյալների աղբյուրի պարամետրերը նկարագրող դասի օբյեկտ՝ `ParameterCollection` դասի ժառանգ։
* `columns` - Տվյալների աղբյուրի վերադարձվող սյուների անունների ցուցակ։
* `isn` - Sql-based տվյալների աղբյուրում տող ավելացնելու, ջնջելու կամ թարմացնելու դեպքում տվյալների աղբյուրի կատարվելիս փոփոխված տողի isn-ը։
* `cancellationToken` - Ընդհատման օբյեկտ:
* `timeout` - Տվյալների աղբյուրի կատարման հարցման առավելագույն ժամանակը։ Արժեք չփոխանցելու դեպքում հարցման կատարման առավելագույն ժամանակ համարվելու է 180 վրկ (3 ր)։

### LoadDefinitionAsync

```c#
public async Task LoadDefinitionAsync(string name, CancellationToken cancellationToken = default)
```

Բեռնում է տվյալների աղբյուրի նկարագրությունը և վերագրում [Definition](#definition) հատկությանը։

**Պարամետրեր**

* `param` - Տվյալների աղբյուրի ներքին անունը։
* `cancellationToken` - Ընդհատման օբյեկտ:

### LongExecuteAsync

```c#
public Task<DataSourceResult<R>> LongExecuteAsync(P param, HashSet<string> columns = default, 
                                                  string isn = null, bool handleEvents = false,
                                                  CancellationToken cancellationToken = default, TimeSpan? timeout = null)
```

Կատարում է տվյալների աղբյուրը, վերադարձնում ստացված տողերի ցուցակը և կատարման ընթացքում առաջացած սխալների մանրամասն տեղեկությունը։

Այս մեթոդը անհրաժեշտ է օգտագործել այնպիսի տվյալների աղբյուրների կատարման համար, որոնց կատարման ժամանակը գերազանցում է 180 վայրկյանը կամ անհայտ է։

Մեթոդը հերթի է դնում տվյալների աղբյուրի կատարումը, հարցնում է կատարման ընթացքի մասին ինֆորմացիա, քանի դեռ կատարումը չի ավարտվել և վերջում վերադարձնում է կատարման արդյունքը։

Տե՛ս նաև [Ասինխրոն մշակում կիրառությունների սերվերի վրա](../../architecture/appserver_async.md):

**Պարամետրեր**

* `R` - Տվյալների աղբյուրի տողը նկարագրող դասի օբյեկտ՝ `ExtendableRow` դասի ժառանգ։
* `param` - Տվյալների աղբյուրի պարամետրերը նկարագրող դասի օբյեկտ՝ `ParameterCollection` դասի ժառանգ։
* `columns` - Տվյալների աղբյուրի վերադարձվող սյուների անունների ցուցակ։
* `isn` - Sql-based տվյալների աղբյուրում տող ավելացնելու, ջնջելու կամ թարմացնելու դեպքում տվյալների աղբյուրի կատարվելիս փոփոխված տողի isn-ը։
* `cancellationToken` - Ընդհատման օբյեկտ:
* `timeout` - Տվյալների աղբյուրի կատարման արդյունքի ստացման հարցման առավելագույն ժամանակը։ Արժեք չփոխանցելու դեպքում հարցման կատարման առավելագույն ժամանակ համարվելու է 180 վրկ (3 ր)։


**Օրինակ**

Ներկայացված է օգտագործողի նույնականացման ու տվյալների աղբյուրի կանչի օրինակ կլիենտից։

Օրինակում ներկայացված տվյալների աղբյուրի սերվիսային նկարագրությանը ծանոթանալու համար [տե՛ս](../../server_api/examples/ds/sql_based_code.cs):

```c#
using var httpClient = new HttpClient();
var loginService = new LoginService();

// նույնականացնում է 51 id-ով և բանալիով նույնականացվող կլիենտ ծրագրի ANNA մուտքանունով օգտագործողին 
loginService.Authenticate("https://localhost:5001", httpClient, null, 51, "ErUrTE92n05jT8aD3NqZsyS6m4PjTqHQ7v", "ANNA");

// ստեղծում է DataSource դասի օբյեկտ, Client հատկությանը փոխանցելով ApiClient դասի օբյեկտ:
// Client հատկության արժեքավորումը պարտադիր է, քանի որ այն նախատեսված է տվյալների աղբյուրի կատարման համար 
// անհրաժեշտ http հարցումներ կլիենտից սերվիս ուղարկելու համար
var ds = new DataSource()
{
    Client = new ApiClient(loginService, httpClient, null)
};

//բեռնում է տվյալների աղբյուրի նկարագրությունը՝ ըստ ներքին անվան
await ds.LoadDefinitionAsync("TreeNode");

// պարամետրերի նկարագրման համար անհրաժեշտ է ստեղծել ParameterCollection դասի օբյեկտ՝
// Definition հատկությանը պարտադիր փոխանցելով տվյալների աղբյուրի Definition-ի Parameters հատկությունը
var parameters = new ParameterCollection() { Definition = ds.Definition.Parameters };

// parameters օբյեկտի indexer-ի միջոցով անհրաժեշտ է նշել պարամետրերի արժեքները ՝ 
// նշելով պարամետրի անունը և փոխանցելով անհրաժեշտ արժեքը։
// Փոխանցվող արժեքը object տիպի է
parameters["TreeId"] = "Banks";
parameters["NodeType"] = "1";

// տվյալների աղբյուրը կատարելու համար անհրաժեշտ է կանչել Execute մեթոդը՝ փոխանցելով պարամետրերը
ds.Execute(parameters);
```