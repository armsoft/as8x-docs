---
title: IDocumentService.GetDocumentState(int) մեթոդ
---

```c#
public Task<int> GetDocumentState(int isn)
```

Վերադարձնում է փաստաթղթի վիճակը։
Եթե փաստաթուղթը առկա չի, կամ ոչ վերջնական ջնջված է, ապա ֆունկցիան վերադարձնում է `-1` արժեք։

**Պարամետրեր**

* `isn` - Փաստաթղթի ներքին նույնականացման համար։
