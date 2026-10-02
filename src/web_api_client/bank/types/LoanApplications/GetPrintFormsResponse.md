---
layout: page
title: GetPrintFormsResponse դաս
---

Այս դասը պարունակում է վարկային հայտի տպման ձևերի հարցման պատասխանը։

Վերադարձվում է [LoanApplicationsRoutes](../../routes/LoanApplicationsRoutes.md).[GetPrintForms](../../routes/LoanApplicationsRoutes.md#getprintforms) մեթոդի կողմից։

```csharp
public class GetPrintFormsResponse
{
    /// <summary>Լրացված տպման ձևերի ցուցակ</summary>
    public Dictionary<PrintFormType, PrintFileInfo> PrintForms { get; set; }

    /// <summary> Հայտի լրացված տպման ձևի ֆայլի տվյալներ </summary>
    public class PrintFileInfo
    {
        /// <summary> Ֆայլի անուն </summary>
        public string FileName { get; set; }

        /// <summary> Ֆայլային պահոցի թղթապանակ </summary>
        public string Container { get; set; }

        /// <summary> Ֆայլային պահոցի ֆայլի անուն </summary>
        public string BlobName { get; set; }
    }
}
```

* [PrintFormType](../../types/LoanApplications/PrintFormType.md) enum-ի նկարագիր
