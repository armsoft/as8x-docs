---
layout: page
title: Օրինակ PaymentDocsRoutes
sublinks:
    - { title: "Օրինակ CreateMemOrder", ref: օրինակ-1 }
---

# Բովանդակություն

- CreateCreditPaymentOrder-ի օգտագործման օրինակ

# Օրինակ

Վճարման հանձնարարագիր փաստաթղթի ստեղծման օրինակ։

```csharp
public static async Task CreateCreditPaymentOrder(BankApiClient apiClient)
{
    try
    {
        var res = await apiClient.PaymentDocs.CreateCreditPaymentOrder(new()
        {
            AcsBranch = "001", // Գրասենյակ
            AcsDepart = "01", // Բաժին
            Date = new DateTime(2025, 1, 1), // Ամսաթիվ
            DocNumber = "000001", // Փաստաթղթի N
            ClientCode = "00000001", // Հաճախորդի կոդ
            Residence = "1", // Ռեզիդենտություն
            AccountDebit = "1111110110070200", // Հաշիվ դեբետ
            AccountCredit = "1111110099440301", // Հաշիվ կրեդիտ
            Payer = "ÐáíÑ³ÝÝ»ë ÐáíÑ³ÝÝÇëÛ³Ý", // Վճարող
            PayerEng = "Hovhannes Hovhannisyan", // Վճարող անգլերեն
            Receiver = "öáË³ÝóáõÙ", // Ստացող
            ReceiverEng = "ABC LLC", // Ստացող անգլերեն
            Summa = 100, // Գումար
            Aim = "Payment for services", // Նպատակ
            OuterID = "12345678", // Արտաքին N
            CheckBlackList = true, // Սև ցուցակի ստուգում
            CheckDebtsByAmountBlock = true, // Արգելադրված պարտքերի ստուգում
            UseOverlimit = false, // Գերածախսի օգտագործում
            CheckPastDueDebts = true, // Պարտքերի ստուգում
            PastDueDebtsSoftCheck = true // Soft check
        });

        Console.WriteLine(res.ISN); // Ստեղծված փաստաթղթի ISN-ը
    }
    catch (ApiException ex)
    {
        Console.WriteLine(ex.Code);
        Console.WriteLine(ex.Message);
        Console.WriteLine(ex.StatusCode);
    }
}
```
