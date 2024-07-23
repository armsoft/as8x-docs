---
layout: page
title: "Տվյալների աղբյուրի պարամետրերի ընդլայնման ձեռնարկ" 
---

## Բովանդակություն
* [Ներածություն](#ներածություն)
* [.cs ֆայլի ստեղծում](#cs-ֆայլի-ստեղծում)
* [Ներմուծում և օգտագործում](#ներմուծում-և-օգտագործում)

## Ներածություն

Գոյություն ունեցող դիտելու ձևերում լրացուցիչ սյուներ, պարամետրեր ավելացնելու, տողերի պարունակությունը փոփոխելու համար նկարագրվում է տվյալների աղբյուրի ընդլայնում։

Ստորև ձեռնարկում նկարագրած է տվյալների աղբյուրում նոր պարամետրերր ավելացնելու քայլերը։  
Դիտելու ձև ընդլայնելու և նոր սյուներ ավելացնելու հիմնական ձեռնարկը համար տե՛ս [Տվյալների աղբյուրի ընդլայնում 8X-ում](ds_extender_guide.md)։  
Ընդլայնումը դիտելու ձևում օգտագործումը համար [տե՛ս](view_guide.md):

Օրինակը ամբողջությամբ հասանելի է [այստեղ](ds_extender_param_full_example.md)։

## .cs ֆայլի ստեղծում

Տվյալների աղբյուրի պարամետրերը նկարագրող դասը սահմանվում է ընդլայնվող սյունյակների նման։ 
Տե'ս նաև [Տվյալների աղբյուրի ընդլայնում 8X-ում](ds_extender_guide.md)։

.cs ֆայլում հարկավոր է ստեղծել class, որը ժառանգում է `Extender<R, P>` դասը՝ որպես `R` փոխանցելով տվյալների աղբյուրի սյուները նկարագրող դասը, իսկ որպես `P`՝ պարամետրերը նկարագրող դասը։ 
Եթե տվյալների աղբյուրը չի պարունակում սյուներ, ապա որպես `R` անհրաժեշտ է փոխանցել `NoColumns` դասը։ 
Հարկավոր է նաև ավելացնել `[DataSourceExtender]` ատրիբուտը։ Օրինակ՝

``` cs
[DataSourceExtender]
public class AllOperExtended : Extender<NoColumns, AllOperExtended.Params>
```

Բերվող օրինակում, որպես նոր պարամետր հայտարարված է հաճախորդի կոդը։

Ավելացվող պարամետրը հարկավոր է սահմանել երկու տեղ
1. Նոր class, որը պարունակում է ընդլայնվող պարամետրերը որպես հատկություններ  (Օրինակում `Params`)

``` cs
public class Params
{
    public string CliCode { get; set; }
}
```

2. Ընդլայնող դասի կոնստրուկտորի մեջ՝ [AddParam](ds_extender.md#addparam) ֆունկցիայի միջոցով։

``` cs
private readonly IDBService dbService;

public AllOperExtended(IDBService dbService)
{
    this.dbService = dbService;
    AddParam(nameof(Params.CliCode), "Հաճախորդի կոդ".ToArmenianANSI(), FieldTypeProvider.GetStringFieldType(8));           
}
```

[AddParam](ds_extender.md#addparam) ֆունկցիային հարկավոր է փոխանցել հետևյալ արժեքները՝
- Պարամետրի ներքին անուն՝ կոդ (նույնանուն հատկության պետք է լինի ստեղծված `Params` դասի մեջ),
- Անվանումը հայրեն ANSI կոդավորմամբ (կարելի է գրել Unicode և օգտագործել ToArmenianANSI() ֆունկցիան),
- Պարամետրի տիպը։

Կոնստրուկտորի մեջ ստանում է նաև տվյալների պահոցի հետ աշխատելու `IDBService` սերվիսը [ինյեկցիայի](/src/project/injection.md) միջոցով։

### BeforeProcess ֆունկցիա

Պարամետրին դիմելու համար [BeforeProcess](ds_extender.md#beforeprocess) ֆունկցիայում 
- ստանում է տվյալների աղբյուրին փոխանցված պարամետրերը `extenderParameters` փոփոխականի մեջ,
- ստուգվում է հաճախորդ պարամետրի փոխանցված (լրացված) լինելը,
- կատարվում է SQL հարցում, որի արդյունքում վերադարձվում են տվյալ հաճախորդի բոլոր հաշիվները

``` cs
private HashSet<string> accounts;

public override async Task BeforeProcess(IList<IExtendableRow> rows, IDataSourceArgs args)
{
    var extenderParameters = (Params)args.ExtenderParameters;
    if (string.IsNullOrWhiteSpace(extenderParameters.CliCode))
    {
        return;
    }
    string sqlQuery = "SELECT fCODE from ACCOUNTS with (nolock) where fCLICODE = @CliCode";
    this.accounts = (await this.dbService.Connection.QueryAsync<string>(sqlQuery,
          new { CliCode = extenderParameters.CliCode })).ToHashSet();
}
```

### ProccessRow ֆունկցիա

Եթե ընդլայնված պարամետրով փոխանցված հաճախորդի կոդ, ապա [ProccessRow](ds_extender.md#proccessrow) ֆունկցիայում ստուգվում է, որ տվյալների աղբյուրի յուրաքանչյուր տողում գրված հաշիվը (դեբետում կամ կրեդիտում) լինի [BeforeProcess](ds_extender.md#beforeprocess)-ում ստացած հաշիվների ցանկում։
Եվ առկայության դեպքում [ProccessRow](ds_extender.md#proccessrow) ֆունկցիան վերադարձնում է `true`, որպեսզի տողը ընդգրկվի վերջնական ցանկում։ Ցանկում չլինելու դեպքում վերադարձնում է `false` տողը վերջնական ցանկից հանելու համար։

``` cs
public override Task<bool> ProccessRow(IExtendableRow row, IDataSourceArgs args)
{
    var extenderParameters = (Params)args.ExtenderParameters;
    if (string.IsNullOrWhiteSpace(extenderParameters.CliCode))
    {
        return Task.FromResult(true);
    }
    var dsRow = (AllOperations.DataRow)row;
    bool result = this.accounts.Contains(dsRow.ACCDB) || this.accounts.Contains(dsRow.ACCCR);

    return Task.FromResult(result);
}
```

## Ներմուծում և օգտագործում

.as և .cs ֆայլերը պատրաստ լինելուն պես անհրաժեշտ է **SYSCON**-ով համապատասխան .as ֆայլը ներմուծել համակարգ, ինչի արդյունքում .cs ֆայլը նույնպես կներմուծվի։ 

ֆայլերը ներմուծելուց հետո հարկավոր այն [կարգավորել դիտելու ձևում](view_guide.md)։
