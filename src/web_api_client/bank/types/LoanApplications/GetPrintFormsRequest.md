---
layout: page
title: GetPrintFormsRequest դաս
---

Այս դասը նախատեսված է վարկային հայտերի տպման ձևերը ստանալու համար։

Օգտագործվում է [LoanApplicationsRoutes](../../routes/LoanApplicationsRoutes.md).[GetPrintForms](../../routes/LoanApplicationsRoutes.md#getprintforms) մեթոդում։

```csharp
public class GetPrintFormsRequest
{
    /// <summary>Հայտի համար</summary>
    public string AppCode { get; set; }

    /// <summary>Տպվող ձևերի տեսակներ</summary>
    public List<PrintFormType> AppPrintForms { get; set; }
}
```

* [PrintFormType](../../types/LoanApplications/PrintFormType.md) enum-ի նկարագիր