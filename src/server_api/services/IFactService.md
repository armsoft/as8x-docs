---
layout: page
title: "IFactService սերվիս" 
tags: AsFact, Hi, Hi2
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [Exists](#exists)
  - [LoadByBase](#loadbybase)
  - [LoadByObject](#loadbyobject)
  - [LoadByTrans](#loadbytrans)
  - [LastDate](#lastdate)
  - [LoadHI2ByBase](#loadhi2bybase)
  - [LoadHI2ByObject](#loadhi2byobject)
  - [LastHI2FactDate](#lasthi2factdate)
  - [SetAccDeb](#setaccdeb)
  - [SetAccCrd](#setacccrd)

## Ներածություն

IFactService դասը նախատեսված է հաշվառման գործառնությունների (Fact) հետ աշխատանքը ապահովելու համար։

## Մեթոդներ

### Exists

```c#
public Task<bool> Exists(int baseIsn = 0, int objectIsn = 0, string accounting = "", string operation = "", bool useArchive = true);
```

Ստուգում է նշված հաշվառող կամ հիմք փաստաթղթով գործառույթների առկայությանը։

Մեթոդի կանչի ժամանակ անհրաժեշտ է արժեք փոխանցել `baseIsn` կամ `objectIsn` պարամետրերից գոնե մեկին։

**Պարամետրեր**

* `baseIsn` - Հիմքային փաստաթղթի ներքին նույնականացման համար։
* `objectIsn` - Հաշվառող փաստաթղթի ներքին նույնականացման համար։
* `accounting` - Հաշվառման կոդը։
* `operation` - Գործողությունների կոդերի ցանկ։ 
  Եթե ցանկը սկսվում է “+” նշանով, ապա հաշվի են առնվում գործողությունների բոլոր կոդերը, որոնք թվարկվում են նրանից հետո։ 
  “-“ նշանի դեպքում անտեսվում են այն գործողությունները, որոնց կոդերը թվարկված են ցանկի մեջ։ 
  Գործողությունների կոդերը թվարկվում են մեկը մյուսի հետևից բացատների միջոցով։ 
  Ցանկը նաև կարող է պարունակել առանց նշանի միակ տարր:
* `useArchive` - Արխիվացված գործառնության որոնման հայտանիշ։ 

### LoadByBase

```c#
public Task<List<Fact>> LoadByBase(int baseIsn, 
                                   string accounting = "", 
                                   string operation = "", 
                                   bool useArchive = true);
```

Վերադարձնում է հիմքային փաստաթղթով ստեղծված գործառույթների ցուցակը։

Նշված պարամետրերով գործառույթների բացակայության դեպքում վերադառնում է դատարկ ցուցակ։ Վերադարձվող ցուցակի յուրաքանչյուր տարր գործառույթ տիպի օբյեկտ է։

**Պարամետրեր**

* `baseIsn` - Հիմքային փաստաթղթի ներքին նույնականացման համար։
* `accounting` - Հաշվառման կոդը։
* `operation` - Գործողությունների կոդերի ցանկ։ 
  Եթե ցանկը սկսվում է “+” նշանով, ապա հաշվի են առնվում գործողությունների բոլոր կոդերը, որոնք թվարկվում են նրանից հետո։ 
  “-“ նշանի դեպքում անտեսվում են այն գործողությունները, որոնց կոդերը թվարկված են ցանկի մեջ։ 
  Գործողությունների կոդերը թվարկվում են մեկը մյուսի հետևից բացատների միջոցով։ 
  Ցանկը նաև կարող է պարունակել առանց նշանի միակ տարր:
* `useArchive` - Արխիվացված գործառնությունների բեռնման հայտանիշ։ 

### LoadByObject

```c#
public Task<List<Fact>> LoadByObject(string accCode, int objectIsn, DateTime beginDate, DateTime endDate, string operation = "");
```

Վերադարձնում է հաշվառվող օբյեկտով ստեղծված գործառույթների ցուցակը տրված ժամանակահատվածում։

Նշված պարամետրերով գործառույթների բացակայության դեպքում վերադառնում է դատարկ ցուցակ։ Վերադարձվող ցուցակի յուրաքանչյուր տարր գործառույթ տիպի օբյեկտ է։

**Պարամետրեր**

* `accCode` - Հաշվառման կոդ:
* `objectIsn` - Հաշվառող փաստաթղթի ներքին նույնականացման համար։
* `beginDate`- Ժամանակաշրջանի սկզբի ամսաթիվ։
* `endDate` - ժամանակաշրջանի վերջին ամսաթիվ։
* `operation` - Գործողությունների կոդերի ցանկ։ 
  Եթե ցանկը սկսվում է “+” նշանով, ապա հաշվի են առնվում գործողությունների բոլոր կոդերը, որոնք թվարկվում են նրանից հետո։ 
  “-“ նշանի դեպքում անտեսվում են այն գործողությունները, որոնց կոդերը թվարկված են ցանկի մեջ։ 
  Գործողությունների կոդերը թվարկվում են մեկը մյուսի հետևից բացատների միջոցով։ 
  Ցանկը նաև կարող է պարունակել առանց նշանի միակ տարր:

### LoadByTrans

```c#
public Task<List<Fact>> LoadByTrans(int baseIsn, int trans, string accounting = "", string operation = "");
```

Վերադարձնում է հիմքային փաստաթղթով և գործարքի համարով ստեղծված գործառույթների ցուցակը։

Նշված պարամետրերով գործառույթների բացակայության դեպքում վերադառնում է դատարկ ցուցակ։ Վերադարձվող ցուցակի յուրաքանչյուր տարր գործառույթ տիպի օբյեկտ է։

**Պարամետրեր**

* `baseIsn` - Հիմքային փաստաթղթի ներքին նույնականացման համար։
* `trans` - Գործողության համար։
* `accounting` - Հաշվառման կոդը։
* `operation` - Գործողությունների կոդերի ցանկ։ 
  Եթե ցանկը սկսվում է “+” նշանով, ապա հաշվի են առնվում գործողությունների բոլոր կոդերը, որոնք թվարկվում են նրանից հետո։ 
  “-“ նշանի դեպքում անտեսվում են այն գործողությունները, որոնց կոդերը թվարկված են ցանկի մեջ։ 
  Գործողությունների կոդերը թվարկվում են մեկը մյուսի հետևից բացատների միջոցով։ 
  Ցանկը նաև կարող է պարունակել առանց նշանի միակ տարր:

### LastDate

```c#
public Task<DateTime?> LastDate(string accountingCode, int isn, DateTime? upToDate, string operation = "");
```

Վերադարձնում է վերջին գործառնության ամսաթիվը նշված հաշվառումից։ 

Եթե գործառնությունը չի գտնվել, ապա վերադառնում է null:

**Պարամետրեր**

* `accountingCode` - Հաշվառման կոդը։
* `isn` - Հաշվառման օբյեկտի ներքին նույնականացման համար, որի համար փնտրում է վերջին գործողության ամսաթիվը։
* `upToDate` - Տրված լինելու դեպքում վերջին գործողության ամսաթիվը փնտրվում է մինչև նշված ամսաթիվը։ 
  Հակառակ դեպքում փնտրում է ամենավերջին գործողության ամսաթիվը։
* `operation` - Տրված լինելու դեպքում փնտրվում է հենց այս գործողության կոդով վերջին ամսաթիվը։ 
  Հակառակ դեպքում բոլոր գործողությունների վերջին ամսաթիվը։

### LoadHI2ByBase

```c#
public Task<List<Fact>> LoadHI2ByBase(int baseIsn, string accounting = "", string operation = "", long glAccISN = -1);
```

Վերադարձնում է հիմքային փաստաթղթով ստեղծված HI2 գործառույթների ցուցակը։

Նշված պարամետրերով գործառույթների բացակայության դեպքում վերադառնում է դատարկ ցուցակ։ Վերադարձվող ցուցակի յուրաքանչյուր տարր գործառույթ տիպի օբյեկտ է։

**Պարամետրեր**

* `baseIsn` - Հիմքային փաստաթղթի ներքին նույնականացման համար։
* `accounting` - Հաշվառման կոդը։
* `operation` - Գործողությունների կոդերի ցանկ։ 
  Եթե ցանկը սկսվում է “+” նշանով, ապա հաշվի են առնվում գործողությունների բոլոր կոդերը, որոնք թվարկվում են նրանից հետո։ 
  “-“ նշանի դեպքում անտեսվում են այն գործողությունները, որոնց կոդերը թվարկված են ցանկի մեջ։ 
  Գործողությունների կոդերը թվարկվում են մեկը մյուսի հետևից բացատների միջոցով։ 
  Ցանկը նաև կարող է պարունակել առանց նշանի միակ տարր:
* `glAccISN` - Կուտակող օբյեկտի ներքին նույնականացման համար։

### LoadHI2ByObject

```c#
public Task<List<Fact>> LoadHI2ByObject(string accounting, 
                                        int objectIsn, 
                                        long glAccISN = -1, 
                                        DateTime? beginDate = null, 
                                        DateTime? endDate = null, 
                                        string operation = "");
```

Վերադարձնում է հաշվառվող օբյեկտով ստեղծված HI2 գործառույթների ցուցակը տրված ժամանակահատվածում։

Նշված պարամետրերով գործառույթների բացակայության դեպքում վերադառնում է դատարկ ցուցակ։ Վերադարձվող ցուցակի յուրաքանչյուր տարր գործառույթ տիպի օբյեկտ է։

**Պարամետրեր**

* `accounting` - Հաշվառման կոդը։
* `objectIsn` - Հաշվառող փաստաթղթի ներքին նույնականացման համար։
* `glAccISN` - Կուտակող օբյեկտի ներքին նույնականացման համար։
* `beginDate`- Ժամանակաշրջանի սկզբի ամսաթիվ։
* `endDate` - ժամանակաշրջանի վերջին ամսաթիվ։
* `operation` - Գործողությունների կոդերի ցանկ։ 
  Եթե ցանկը սկսվում է “+” նշանով, ապա հաշվի են առնվում գործողությունների բոլոր կոդերը, որոնք թվարկվում են նրանից հետո։ 
  “-“ նշանի դեպքում անտեսվում են այն գործողությունները, որոնց կոդերը թվարկված են ցանկի մեջ։ 
  Գործողությունների կոդերը թվարկվում են մեկը մյուսի հետևից բացատների միջոցով։ 
  Ցանկը նաև կարող է պարունակել առանց նշանի միակ տարր:

### LastHI2FactDate

```c#
public Task<DateTime?> LastHI2FactDate(string accountingCode, int isn, int glIsn, DateTime? upToDate, string operation = "");
```

Վերադարձնում է հաշվառվող օբյեկտի համար նշանակված վերջին HI2 գործառույթի ամսաթիվը, որը ստեղծվել է հաշվառման նշված կոդով մինչև նշված ամսաթիվը ներառյալ։

**Պարամետրեր**

* `accountingCode` - Հաշվառման կոդը։
* `isn` - Հաշվառվող օբյեկտի ներքին նույնականացմամ համար։
* `glIsn` - Կուտակող օբյեկտի ներքին նույնականացման համար։
* `upToDate` - Տրված լինելու դեպքում վերջին գործողության ամսաթիվը փնտրվում է մինչև նշված ամսաթիվը։ 
  Հակառակ դեպքում փնտրում է ամենավերջին գործողության ամսաթիվը։
* `operation` - Տրված լինելու դեպքում փնտրվում է հենց այս գործողության կոդով վերջին ամսաթիվը։ 
  Հակառակ դեպքում բոլոր գործողությունների վերջին ամսաթիվը։

### SetAccDeb

```c#
public Task SetAccDeb(Fact fact, string value, bool uncheck = false);
```

Նշանակում է գործառնության դեբետային հաշիվը։

**Պարամետրեր**

* `fact` - Գործառնության օբյեկտ։
* `value` - Վերագրվող արժեք։
* `uncheck` - `false` արժեքի դեպքում ստուգվում է վերագրվող հաշվի առկայությունը [հաշվառում](https://armsoft.github.io/as4x-docs/HTM/ProgrGuide/Defs/Accounting.html) համակարգային նկարագրության AccFolder թղթապանակում, որտեղ նշվում են դեբետի կամ կրեդիտի թղթակցությանը մասնակցող հաշիվները։

### SetAccCrd

```c#
public Task SetAccCrd(Fact fact, string value, bool uncheck = false);
```

Նշանակում է գործառնության կրեդիտային հաշիվը։

**Պարամետրեր**

* `fact` - Գործառնության օբյեկտ։
* `value` - Վերագրվող արժեք։
* `uncheck` - `false` արժեքի դեպքում ստուգվում է վերագրվող հաշվի առկայությունը [հաշվառում](https://armsoft.github.io/as4x-docs/HTM/ProgrGuide/Defs/Accounting.html) համակարգային նկարագրության AccFolder թղթապանակում, որտեղ նշվում են դեբետի կամ կրեդիտի թղթակցությանը մասնակցող հաշիվները։