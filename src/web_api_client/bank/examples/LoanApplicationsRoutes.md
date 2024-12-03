---
layout: page
title: "Օրինակ LoanApplicationsRoutes" 
---

## Բովանդակություն

- [Վարկային հայտի ստեղծման օրինակ](#վարկային-հայտի-ստեղծման-օրինակ)
- [Վարկային հայտի ստորագրման օրինակ](#վարկային-հայտի-ստորագրման-օրինակ)
- [Վարկային հայտի տպելու ձևանմուշների վերադարձման և օգտագործման օրինակ](#վարկային-հայտի-տպելու-ձևանմուշների-վերադարձման-և-օգտագործման-օրինակ)

## Վարկային հայտի ստեղծման օրինակ

```c#
private static async Task CreateLoanApplication(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է վարկային հայտ՝ նշելով անհրաժեշտ տվյալները
        var res = await apiClient.LoanApplications.Create(new()
        {
            CliCode = "00110136", // հաճախորդի կոդ
            AppType = "0008", // հայտատեսակ
            Amount = 1000000, // վարկային հայտի 
            Duration = new Periodicity() { Month = 12 }, // վարկի տևողություն
            RepayDay = 16, // վարկի մարման օր
            ReceiveMethod = ReceiveMethod.WithAccount, // վարկային հայտի հաստատման դեպքում գումարի փոխանցման եղանակ (այս դեպքում հաշվին)
            AccountNumber = "2500011013600100", // վարկային հայտի հաստատման դեպքում գումարի փոխանցման հաշվարկային հաշիվ
            RespName = "Պողոս Պողոսյան".ToArmenianANSI(), // շահառուի անվանում
            Comment = "Մեկնաբանություն ANSI-ով".ToArmenianANSI(), // մեկնաբանություն
            Date = DateTime.Today, // վարկային հայտի ստեղծման ամսաթիվ
        });

        // տպում է ստեղծված վարկային հայտի կոդը
        Console.WriteLine(res.AppCode);
    }
    // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
    catch (ApiException ex)
    {
        Console.WriteLine(ex.Code); // սխալի կոդ
        Console.WriteLine(ex.Message); // սխալի հաղորդագրություն
        Console.WriteLine(ex.StatusCode); // սխալի վիճակի կոդ
    }
}
```

## Վարկային հայտի ստորագրման օրինակ

```c#
private static async Task SignLoanApplication(BankApiClient apiClient)
{
    try
    {
        // ստորագրում է "0011" կոդով վարկային հայտը՝ մերժելով այն
        var res = await apiClient.LoanApplications.Sign(new()
        {
            AppCode = "0011",
            Answer = Answer.Reject
        });
    }
    // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
    catch (ApiException ex)
    {
        Console.WriteLine(ex.Code); // սխալի կոդ
        Console.WriteLine(ex.Message); // սխալի հաղորդագրություն
        Console.WriteLine(ex.StatusCode); // սխալի վիճակի կոդ
    }
}
```

## Վարկային հայտի տպելու ձևանմուշների վերադարձման և օգտագործման օրինակ

```c#
private static async Task GetPrintForms(BankApiClient apiClient)
{
    try
    {
        // վերադարձնում է "0012" կոդով վարկային հայտի "Պայմանագիր", "Արբիտրաժային համաձայնագիր", "Անհատական թերթիկ" տեսակի տպելու ձևանմուշները
        var res = await apiClient.LoanApplications.GetPrintForms(new()
        {
            AppCode = "0012",
            AppPrintForms = [PrintFormType.Arbitrage, PrintFormType.Contract, PrintFormType.IndividualSheet]
        });

        // նշված ճանապարհով թղթապանակի գոյություն չունենալու դեպքում ստեղծում է այն
        if (!Directory.Exists(@"D:\Work\Docs\IDLeasing\0012"))
        {
            Directory.CreateDirectory(@"D:\Work\Docs\IDLeasing\0012");
        }

        // ցիկլով անցնում է վարկային հայտի տպելու ձևանմուշների վրայով
        foreach (var (printType, file) in res.PrintForms)
        {
            Console.WriteLine(printType);

            // նշված ճանապարհով թղթապանակում ստեղծում է ֆայլ և լրացնում վարկային հայտի տպելու ձևանմուշը ֆայլում
            await File.WriteAllBytesAsync(Path.Combine(@"D:\Work\Docs\IDLeasing\0012", file.FileName), file.Data);
        }
    }

    // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
    catch (ApiException ex)
    {
        Console.WriteLine(ex.Code); // սխալի կոդ
        Console.WriteLine(ex.Message); // սխալի հաղորդագրություն
        Console.WriteLine(ex.StatusCode); // սխալի վիճակի կոդ
    }
}
```