---
title: IKernelService.GetRem(string, int, DateTime?) մեթոդ
---

```c#
public Task<(decimal CRem, decimal NCRem)> GetRem(string accounting, 
                                                  int isn, 
                                                  DateTime? remDate = null)
```

Վերադարձնում է փաստաթղթի հաշվառման մնացորդը նշված ամսաթվի դրությամբ։

Վերադարձնում է կորտեժ`
* `CRem` - Մնացորդը։
* `NCRem` - Մնացորդի դրամային համարժեքը։ 
  Այս թիվը ձևավորվում է մնացորդի ձևավորման ժամանակ, այլ ոչ թե վերահաշվարկվում մեթոդի կանչի ժամանակ։

**Պարամետրեր**

* `accounting` - Հաշվառման կոդ (ներքին անուն):
* `isn` - Հաշվառվող օբյեկտի ներքին նույնականացման համար։
* `remDate` - Մնացորդը բերելու ամսաթիվը։ 
  Եթե պարամետրը փոխանցված չէ, ապա բերվում է վերջնական մնացորդը։
