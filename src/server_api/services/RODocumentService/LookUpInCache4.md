---
title: RODocumentService.LookUpInCache(int, DocumentLoadSession, Ref<bool>, bool) մեթոդ
---

```c#
public Task<T> LookUpInCache<T>(int isn, 
                                DocumentLoadSession documentLoadSession,
                                Ref<bool> isRefreshed = null, 
                                bool lookInArc = true) where T : RODocument, new()
                                        
```

Փնտրում է փաստաթուղթը քեշում ըստ փաստաթղթի ներքին նույնականացման համարի և վերադարձնում։ 
Քեշում բացակայության դեպքում բեռնում է փաստաթուղթը տվյալների պահոցից, ավելացնում քեշում և վերադարձնում։ 

**Պարամետրեր**

* `T` - Վերադարձնում է փաստաթղթի նկարագրված դաս 8X-ում, [RODocument](../../types/RODocument.md) դասի ժառանգ։
* `isn` - Փնտրվող փաստաթղթի ներքին նույնականացման համարը։
* `documentLoadSession` - Փաստաթղթի բեռնման սեսսիա։ Եթե փաստաթուղթը պարունակվում է բեռնման սեսսիայի քեշում, ապա վերադարձնում է այն, հակառակ դեպքում բեռնում է տվյալների պահոցից, ավելացնում բեռնման սեսսիայի քեշում և վերադարձնում։
* `isRefreshed` - Ցույց է տալիս, արդյոք մեթոդի կանչի արդյունքում փաստաթուղթը բեռնվել է տվյալների պահոցից և թարմացվել քեշում, թե ոչ։
* `lookInArc` - Արխիվացված փաստաթղթի բեռնման հայտանիշ։ **true** արժեքի դեպքում փաստաթուղթը հիմնական պահոցում չգտնելու դեպքում փորձում է բեռնել նաև արխիվային տվյալների պահոցից, եթե այնտեղ նույնպես փաստաթութը առկա չէ, առաջանում է սխալ։
