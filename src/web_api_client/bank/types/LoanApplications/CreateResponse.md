---
layout: page
title: CreateResponse դաս
---

Այս դասը պարունակում է վարկային հայտի ստեղծման պատասխանի տվյալները։

Վերադարձվում է [LoanApplicationsRoutes](../../routes/LoanApplicationsRoutes.md).[Create](../../routes/LoanApplicationsRoutes.md#create) մեթոդի կողմից։

```csharp
public class CreateResponse
{
    /// <summary>Ստեղծված հայտի կոդ</summary> 
    public string AppCode { get; set; }
}
```
