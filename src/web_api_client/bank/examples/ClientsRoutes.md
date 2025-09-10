---
layout: page
title: "Օրինակ ClientsRoutes" 
sublinks:
- { title: "Օրինակ CreateClientFromEkeng", ref: օրինակ-1 }
- { title: "Օրինակ CreatePhysicalClientByFullData", ref: օրինակ-2 }
- { title: "Օրինակ CreateJuridicalClientByFullData", ref: օրինակ-3 }
- { title: "Օրինակ UpdatePhysicalClientData", ref: օրինակ-4 }
- { title: "Օրինակ UpdateJuridicalClientData", ref: օրինակ-5 }
---

## Բովանդակություն
- [CreateClientFromEkeng-ի օգտագործման օրինակ](#օրինակ-1)
- [CreatePhysicalClientByFullData-ի օգտագործման օրինակ](#օրինակ-2)
- [CreateJuridicalClientByFullData-ի օգտագործման օրինակ](#օրինակ-3)
- [UpdatePhysicalClientData-ի օգտագործման օրինակ](#օրինակ-4)
- [UpdateJuridicalClientData-ի օգտագործման օրինակ](#օրինակ-5)

## Օրինակ 1

Նոր ֆիզ. անձ հաճախորդի ստեղծման օրինակ ԷԿԵՆԳ համակարգից ստանալով անձի տվյալները։

```c#
public static async Task CreateClientFromEkeng(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է ֆիզիկական անձ տիպի հաճախորդ՝ նշելով անձը հաստատող փաստաթղթի համարներից մեկը և ռեզիդենտությունը
        var res = await apiClient.Clients.CreateClientFromEkeng(new()
        {
            PersonSSN = "1234567891",     //Սոց.քարտի համարը
            //PassCode = "AH1234567891",  //Անձնագրի համար
            //TaxNumber = "1234567891",   //Անհատ ձեռնարկատիրոջ ՀՎՀՀ
            Resident = true,            //Հաճախորդի ռեզիդենտություն (ՊԱՐՏԱԴԻՐ Է)

            EMail = "test@mail.am",     //էլ.փոստ
            Mobile = "374 91111111",    //Բջջ.հեռախոսահամար
        });

        Console.WriteLine(res.IsNewCreated);
        Console.WriteLine(res.Client);          //Վերադարձնում է ստեղծված հաճախորդի համարը
    }
    catch (ApiException ex)
    {
        // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
        Console.WriteLine(ex.Code); // սխալի կոդ
        Console.WriteLine(ex.Message); // սխալի հաղորդագրություն
        Console.WriteLine(ex.StatusCode); // սխալի վիճակի կոդ
    }
}
```

## Օրինակ 2

Նոր ֆիզ. անձ հաճախորդի ստեղծման օրինակ։

```c#
private static async Task CreateClient(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է ֆիզիկական անձ տիպի հաճախորդ՝ նշելով անհրաժեշտ տվյալները
        var res = await apiClient.Clients.CreatePhysicalClientByFullData(new()
        {
            // հաճախորդի անձնագրի տվյալներ
            Passport = new()
            {
                PassCode = "AH1234567891", // կոդ
                PassType = "01", //տեսակ
                PassBy = "001", // ում կողմից է տրված
                DatePass = new DateTime(2020, 11, 15), // տրման ամսաթիվ
                DateExpire = new DateTime(2030, 11, 15), // վավեր է մինչև
            },

            FirstName = "Պողոս".ToArmenianANSI(), // հաճախորդի անուն
            LastName = "Պողոսյան".ToArmenianANSI(), // հաճախորդի ազգանուն
            Resident = true, // հաճախորդի ռեզիդենտության հայտանիշ
            ResidenceCountry = "AM", // հաճախորդի ռեզիդենտության երկրի կոդ
            RelatedWithBank = false, // հաճախորդը ունի բանկի հետ կապվածություն թե ոչ
            IsBankEmployee = false, // հաճախորդը հանդիսանում է բանկի աշխատակից թե ոչ
            CitizenshipCountry = "AM", // հաճախորդի քաղաքացիության երկրի կոդ
            StmtType = ArmSoft.AS8X.Public.BankModels.Clients.StatementDeliverModes.Bank, // քաղվածքի ստացման եղանակ
            OtherFieldValues = new() { { "UDRWCOUNT", "555" } },
            SSNNumber = "1234567891", // սոց. քարտի համար
            SSNDate = new DateTime(2020, 11, 15), // սոց. քարտ-ի տրման ամսաթիվ
            SSNType = "2", // սոց. քարտի տիպ
        });

        
        Console.WriteLine(res.Client);  // տպում է ստեղծված հաճախորդի կոդը
        Console.WriteLine(res.IsFinalState);  //ստեղծված հաճախորդը վերջնական վիճակում է
    }
    catch (ApiException ex)
    {
        // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
        Console.WriteLine(ex.Code); // սխալի կոդ
        Console.WriteLine(ex.Message); // սխալի հաղորդագրություն
        Console.WriteLine(ex.StatusCode); // սխալի վիճակի կոդ
    } 
}
```

## Օրինակ 3

Նոր իրավ. հաճախորդի ստեղծման օրինակ։

```c#
private static async Task CreateClient(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է ֆիզիկական անձ տիպի հաճախորդ՝ նշելով անհրաժեշտ տվյալները
        var res = await apiClient.Clients.CreateJuridicalClientByFullData(new()
        {
            Name = "Կազմակերպություն".ToArmenianANSI(), // հաճախորդի անվանում
            NameEng = "Organization".ToArmenianANSI(), // հաճախորդի անգլերեն անվանում
            TaxCode = "11223344", // հաճախորդի ՀՎՀՀ
            RegNum = "1111111111", // գրանցման համար
            RegDate = new DateTime(2020, 11, 15), // տրված
            RegType = "1", // տիպ
            RegistrationCertNumber = "1111111111", // հաճախորդի պետ. գրանցման վկայականի համար
            Volort = "12", // հաճախորդի գործունեության ոլորտ
            StateStatus = "2", // հաճախորդի պետական կարգավիճակ
            ClientSize = "0", // հաճախորդի չափ
            Resident = true, // հաճախորդի ռեզիդենտության հայտանիշ
            ResidenceCountry = "AM", // հաճախորդի ռեզիդենտության երկրի կոդ
            StmtType = ArmSoft.AS8X.Public.BankModels.Clients.StatementDeliverModes.Bank, // քաղվածքի ստացման եղանակ
            Branch = "00", // հաճախորդի գրասենյակ
            Department = "1", // հաճախորդի բաժին
            AccessType = "21", // հաճախորդի հաս. տիպ
            ClientNote2 = "2", // նշում 2
            ClientNote3 = "01", // նշում 3
            OtherFieldValues = new() { { "UDRWCOUNT", "555" } }

            // հաճախորդի գրանցման հասցե
            address = new()
            {
                Country = "AM", // երկիր
                Community = "010010635", // բնակավայր
                City = "Երևան".ToArmenianANSI(), // քաղաք
                CityEng = "Yerevan", // քաղաք անգլերեն
                Street = "Չարենց".ToArmenianANSI(), // փողոց
                StreetEng = "Charents" // փողոց անգլերեն
            }
        });

        
        Console.WriteLine(res.Client);  // տպում է ստեղծված հաճախորդի կոդը
        Console.WriteLine(res.IsFinalState);  // ստեղծված հաճախորդը վերջնական վիճակում է
    }
    catch (ApiException ex)
    {
        // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
        Console.WriteLine(ex.Code); // սխալի կոդ
        Console.WriteLine(ex.Message); // սխալի հաղորդագրություն
        Console.WriteLine(ex.StatusCode); // սխալի վիճակի կոդ
    } 
}
```
## Օրինակ 4

Ֆիզ. անձ հաճախորդի խմբագրման օրինակ։

```c#
private static async Task UpdateClient(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է ֆիզիկական անձ տիպի հաճախորդ՝ նշելով անհրաժեշտ տվյալները
        var res = await apiClient.Clients.UpdatePhysicalClientData(new()
        {
            ClientCode = "00000001", // խմբագրվող հաճախորդի կոդ
            NewMobile = "37477111111", // նոր հեռախոսահամար
            NewEmail = "client@gmail.com", // նոր էլ. հասցե
            NewStmtType = ArmSoft.AS8X.Public.BankModels.Clients.StatementDeliverModes.Bank, // նոր քաղվածքի ստացման եղանակ,
            FillCurrentAddressAsReg = true, // true - Փաստացի հասցեն լրացվում է Գրանցման հասցեյի նման
            UpdateFromEkeng = true // հաճախորդի վրա դրվում է "Տվյալների թարմացում ԷԿԵՆԳ-ից" նշիչը
            OtherFieldValues = new() { { "UDRWCOUNT", "555" } },
            // հաճախորդի անձնագրի տվյալներ
            Passport = new()
            {
                PassCode = "AH1234567891", // կոդ
                PassType = "01", //տեսակ
                PassBy = "001", // ում կողմից է տրված
                DatePass = new DateTime(2020, 11, 15), // տրման ամսաթիվ
                DateExpire = new DateTime(2030, 11, 15), // վավեր է մինչև
            }
        });

        
        Console.WriteLine(res.Client);  // տպում է ստեղծված հաճախորդի կոդը
        Console.WriteLine(res.IsFinalState);  //ստեղծված հաճախորդը վերջնական վիճակում է
    }
    catch (ApiException ex)
    {
        // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
        Console.WriteLine(ex.Code); // սխալի կոդ
        Console.WriteLine(ex.Message); // սխալի հաղորդագրություն
        Console.WriteLine(ex.StatusCode); // սխալի վիճակի կոդ
    } 
}
```
## Օրինակ 5

Իրավաբանական հաճախորդի խմբագրման օրինակ։

```c#
private static async Task UpdateClient(BankApiClient apiClient)
{
    try
    {
        // ստեղծում է ֆիզիկական անձ տիպի հաճախորդ՝ նշելով անհրաժեշտ տվյալները
        var res = await apiClient.Clients.UpdateJuridicalClientData(new()
        {
            ClientCode = "00000001", // խմբագրվող հաճախորդի կոդ
            NewMobile = "37477111111", // նոր հեռախոսահամար
            NewEmail = "client@gmail.com", // նոր էլ. հասցե
            NewStmtType = ArmSoft.AS8X.Public.BankModels.Clients.StatementDeliverModes.Bank, // նոր քաղվածքի ստացման եղանակ,
            FillCurrentAddressAsReg = true, // true - Փաստացի հասցեն լրացվում է Գրանցման հասցեյի նման
            OtherFieldValues = new() { { "UDRWCOUNT", "555" } },

            // հաճախորդի փաստացի հասցե
            // դաշտը չփոխանցելու դեպքում պարունակությունը չի փոփոխվի, դատարկ փոխանցելու դեպքում կդատարկվի
            NewCurrentAddress = new()
            {
                Country = "AM", // երկիր
                Community = "010010635", // բնակավայր
                City = "Երևան".ToArmenianANSI(), // քաղաք
                CityEng = "Yerevan", // քաղաք անգլերեն
                Street = "Չարենց".ToArmenianANSI(), // փողոց
                StreetEng = "Charents" // փողոց անգլերեն
            }
        });

        Console.WriteLine(res.Client);  // տպում է ստեղծված հաճախորդի կոդը
        Console.WriteLine(res.IsFinalState);  //ստեղծված հաճախորդը վերջնական վիճակում է
    }
    catch (ApiException ex)
    {
        // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
        Console.WriteLine(ex.Code); // սխալի կոդ
        Console.WriteLine(ex.Message); // սխալի հաղորդագրություն
        Console.WriteLine(ex.StatusCode); // սխալի վիճակի կոդ
    } 
}
```
