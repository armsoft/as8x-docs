---
layout: page
title: GetAllResponse դաս
---

Այս դասը պարունակում է վարկային հայտի ստեղծման պատասխանի տվյալները։

Վերադարձվում է [LoanApplicationsRoutes](../../routes/LoanApplicationsRoutes.md).[GetAll](../../routes/LoanApplicationsRoutes.md#getall) մեթոդի կողմից։

```csharp
public class GetAllResponse
{
    /// <summary>Հայտեր</summary>
    public List<AppForm> AppForms { get; set; }
}
```

* [AppForm](../../types/LoanApplications/AppForm.md) դասի նկարագիր
