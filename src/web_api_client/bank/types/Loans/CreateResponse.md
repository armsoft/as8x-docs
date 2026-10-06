---
layout: page
title: CreateResponse դաս
---

Այս դասը պարունակում է վարկային պայմանագրի ստեղծման պատասխանի տվյալները։

Վերադարձվում է [LoansRoutes](../../routes/LoansRoutes.md).[Create](../../routes/LoansRoutes.md#create) մեթոդի կողմից։

```c#
public class CreateResponse
{
    /// <summary> Պայմանագրի կոդ </summary>
    public string Code { get; set; }

    /// <summary> Պայմանագրի ISN </summary>
    public int ISN { get; set; }

    /// <summary> Պայմանագիրը վերջնական վիճակում է, թե ոչ </summary>
    public bool IsFinalState { get; set; }
}
```
