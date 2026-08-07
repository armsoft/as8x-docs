---
layout: page
title: SignRequest դաս
---

Այս դասը նախատեսված է վարկային հայտը ստորագրության փուլում հաստատելու/մերժելու համար։

Օգտագործվում է [LoanApplicationsRoutes](../../routes/LoanApplicationsRoutes.md).[Sign](../../routes/LoanApplicationsRoutes.md#sign) մեթոդում։

```csharp
public class SignRequest
{
    /// <summary>Հայտի համար</summary>
    public string AppCode { get; set; }

    /// <summary>Պատասխան</summary>
    public Answer Answer { get; set; }
}
```

* [Answer](../../types/Answer.md) enum-ի նկարագիր