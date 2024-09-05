---
layout: page
title: "LiteDocumentService" 
tags: [LiteDocumentService, Cache, Document]
---

## Բովանդակություն
- [Բովանդակություն](#բովանդակություն)
- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [ClearCache](#clearcache)
  - [Load](#load)
  - [Load](#load-1)
  - [LoadFromFolder](#loadfromfolder)
  - [LoadGrids](#loadgrids)
  - [LoadIntoCache](#loadintocache)
  - [LookUpInCache](#lookupincache)
  - [LookUpInCache](#lookupincache-1)
  - [RemoveFromCache](#removefromcache)
  - [RemoveFromCache](#removefromcache-1)

## Ներածություն

LiteDocumentService դասը նախատեսված է LiteDocument տիպի փաստաթղթերը տվյալների պահոցից բեռնելու, քեշում պահելու և քեշից կարդալու ֆունկցիոնալությունը ապահովելու համար։

## Մեթոդներ

### ClearCache

```c#
public void ClearCache();
```

Հեռացնում է բոլոր փաստաթղթերը քեշից։

### Load

```c#
public Task<LiteDocument> Load(int isn,
                               bool loadGrids = false,
                               bool throwExceptionIfDeleted = true,
                               bool lookInArc = true);
```

Բեռնում է փաստաթուղթը տվյալների պահոցից ըստ փաստաթղթի ներքին նույնականացման համարի։

**Պարամետրեր**

* `isn` - Բեռնվող փաստաթղթի ներքին նույնականացման համարը։
* `loadGrids` - Փաստաթղթի աղյուսակների բեռնման հայտանիշ։ Լռությամբ արժեքը **false** է։
* `throwExceptionIfDeleted` - Պահանջվող փաստաթղթի հեռացված լինելու դեպքում սխալի գեներացման հայտանիշ։ Լռությամբ արժեքը **true** է:
* `lookInArc` - Արխիվացված փաստաթղթի բեռնման հայտանիշ։ **true** արժեքի դեպքում փաստաթուղթը հիմնական պահոցում չգտնելու դեպքում փորձում է բեռնել նաև արխիվային տվյալների պահոցից, եթե այնտեղ նույնպես փաստաթութը առկա չէ, առաջանում է սխալ։ Լռությամբ արժեքը **true** է։

### Load

```c#
public Task<Dictionary<int, LiteDocument>> Load(IEnumerable<int> isnList);
```

Բեռնում է նշված ներքին նույնականացման համարներով փաստաթղթերը հիմնական տվյալների պահոցից՝ առանց աղյուսակների բեռնման և արխիվային տվյալների ստուգման:

**Պարամետրեր**

* `isnList` - Փաստաթղթերի ներքին նույնականացման համարների ցուցակ։

### LoadFromFolder

```c#
public Task<LiteDocument> LoadFromFolder(string folderID, string folderKey, bool loadGrids = false);
```

Բեռնում է փաստաթուղթը տվյալների պահոցից ըստ փաստաթուղթը պարունակող թղթապանակի ներքին անվան և թղթապանակի տարրի կոդի։

**Պարամետրեր**

* `folder` - Փաստաթուղթը պարունակող թղթապանակի ներքին անունը։
* `folderKey` - Թղթապանակի տարրի կոդը։
* `loadGrids` - Փաստաթղթի աղյուսակների բեռնման հայտանիշ։ Լռությամբ արժեքը **false** է։

### LoadGrids

```c#
public Task LoadGrids(LiteDocument document, bool lookInArc = false);
```

Բեռնում է փաստաթղթի աղյուսակները տվյալների պահոցից և ավելացնում նշված փաստաթղթում։

**Պարամետրեր**

* `document` - Փաստաթուղթը նկարագրող դասը։
* `lookInArc` - Արխիվացված փաստաթղթի աղյուսակների բեռնման հայտանիշ։ **true** արժեքի դեպքում փաստաթուղթը հիմնական պահոցում չգտնելու դեպքում փորձում է աղյուսակները բեռնել նաև արխիվային տվյալների պահոցից, եթե այնտեղ նույնպես փաստաթութը առկա չէ, առաջանում է սխալ։ Լռությամբ արժեքը **true** է։

### LoadIntoCache

```c#
public virtual Task<LiteDocument> LoadIntoCache(int isn,
                                                bool throwExceptionIfDeleted = true,
                                                Ref<bool> isRefreshed = null,
                                                bool lookInArc = true)
```

Բեռնում է փաստաթուղթը տվյալների պահոցից ըստ փաստաթղթի ներքին նույնականացման համարի և ավելացնում քեշում։

**Պարամետրեր**

* `isn` - Բեռնվող փաստաթղթի ներքին նույնականացման համարը։
* `throwExceptionIfDeleted` - Պահանջվող փաստաթղթի հեռացված լինելու դեպքում սխալի գեներացման հայտանիշ։ Լռությամբ արժեքը **true** է:
* `isRefreshed` - Ցույց է տալիս, արդյոք մեթոդի կանչի արդյունքում փաստաթուղթը բեռնվել է տվյալների պահոցից և թարմացվել քեշում, թե ոչ։ Լռությամբ արժեքը **null** է:
* `lookInArc` - Արխիվացված փաստաթղթի բեռնման հայտանիշ։ **true** արժեքի դեպքում փաստաթուղթը հիմնական պահոցում չգտնելու դեպքում փորձում է բեռնել նաև արխիվային տվյալների պահոցից, եթե այնտեղ նույնպես փաստաթութը առկա չէ, առաջանում է սխալ։ Լռությամբ արժեքը **true** է։

### LookUpInCache

```c#
public Task<LiteDocument> LookUpInCache(int isn,
                                        TimeSpan checkAfter,
                                        Ref<bool> isRefreshed = null,
                                        bool lookInArc = true)
                                        
```

Փնտրում է փաստաթուղթը քեշում ըստ փաստաթղթի ներքին նույնականացման համարի և վերադարձնում։ Քեշում բացակայության դեպքում բեռնում է փաստաթուղթը տվյալների պահոցից, ավելացնում քեշում և վերադարձնում։ 

**Պարամետրեր**

* `isn` - Փնտրվող փաստաթղթի ներքին նույնականացման համարը։
* `checkAfter` - Եթե քեշում պարունակվող փաստաթղթի թարմության վերջին ստուգումից անցել է ավելի շատ ժամանակ, քան նշված է այս պարամետրում, ապա ստուգվում է փաստաթղթի թարմությունը։ Եթե քեշում պարունակվող փաստաթղթի timestamp-ը չի համընկնում տվյալների պահոցում գրանցված timestamp-ի հետ, ապա փաստաթուղթը բեռնում է տվյալների պահոցից, հակառակ դեպքում վերադարձնում է քեշում առկա փաստաթուղթը։  
* `isRefreshed` - Ցույց է տալիս, արդյոք մեթոդի կանչի արդյունքում փաստաթուղթը բեռնվել է տվյալների պահոցից և թարմացվել քեշում, թե ոչ։ Լռությամբ արժեքը **null** է:
* `lookInArc` - Արխիվացված փաստաթղթի բեռնման հայտանիշ։ **true** արժեքի դեպքում փաստաթուղթը հիմնական պահոցում չգտնելու դեպքում փորձում է բեռնել նաև արխիվային տվյալների պահոցից, եթե այնտեղ նույնպես փաստաթութը առկա չէ, առաջանում է սխալ։ Լռությամբ արժեքը **true** է։

### LookUpInCache

```c#
public Task<LiteDocument> LookUpInCache(string folderID,
                                        string folderKey,
                                        TimeSpan checkAfter,
                                        Ref<bool> isRefreshed = null) 
```

Փնտրում է փաստաթուղթը քեշում ըստ փաստաթուղթը պարունակող թղթապանակի ներքին անվան և թղթապանակի տարրի կոդի և վերադարձնում։ Քեշում բացակայության դեպքում բեռնում է փաստաթուղթը տվյալների պահոցից, ավելացնում քեշում և վերադարձնում։ 

**Պարամետրեր**

* `folderID` - Փաստաթուղթը պարունակող թղթապանակի ներքին անունը։
* `folderKey` - Թղթապանակի տարրի կոդը։
* `checkAfter` - Եթե քեշում պարունակվող փաստաթղթի թարմության վերջին ստուգումից անցել է ավելի շատ ժամանակ, քան նշված է այս պարամետրում, ապա ստուգվում է փաստաթղթի թարմությունը։ Եթե քեշում պարունակվող փաստաթղթի timestamp-ը չի համընկնում տվյալների պահոցում գրանցված timestamp-ի հետ, ապա փաստաթուղթը բեռնում է տվյալների պահոցից, հակառակ դեպքում վերադարձնում է քեշում առկա փաստաթուղթը։ 
* `isRefreshed` - Ցույց է տալիս, արդյոք մեթոդի կանչի արդյունքում փաստաթուղթը բեռնվել է տվյալների պահոցից և թարմացվել քեշում, թե ոչ։ Լռությամբ արժեքը **null** է:

### RemoveFromCache

```c#
public void RemoveFromCache(int isn);
```

Հեռացնում է նշված փաստաթուղթը քեշից։

**Պարամետրեր**

* `isn` - Փաստաթղթի ներքին նույնականացման համարը։

### RemoveFromCache

```c#
public void RemoveFromCache(string docType);
```

Հեռացնում է նշված տեսակի բոլոր փաստաթղթերը քեշից։

**Պարամետրեր**

* `docType` - Փաստաթղթի տեսակը։