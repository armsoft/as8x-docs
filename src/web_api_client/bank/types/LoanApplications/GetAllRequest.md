---
layout: page
title: GetAllRequest դաս
---

Այս դասը նախատեսված է վարկային հայտերի տվյալները ստանալու համար։

Օգտագործվում է [LoanApplicationsRoutes](../../routes/LoanApplicationsRoutes.md).[GetAll](../../routes/LoanApplicationsRoutes.md#getall) մեթոդում։

```csharp
public class GetAllRequest
{
    /// <summary> Ամսաթիվ </summary>
    public DateTime Date { get; set; }

    /// <summary> Հաճախորդի կոդ </summary>
    public string CliCode { get; set; }

    /// <summary> Հայտի համար </summary>
    public string AppCode { get; set; }
}
```
