---
layout: page
title: "appsettings.json: Կարգավորման ֆայլ"
tags: [Settings, appsettings]
sublinks:
- { title: "additionalSettings", ref: additionalsettings }
- { title: "Autentication", ref: autentication }
- { title: "db", ref: db }
- { title: "Extensions", ref: extensions }
- { title: "Hangfire", ref: hangfire }
- { title: "JwtConfig", ref: jwtconfig }
- { title: "OTLP", ref: otlp }
- { title: "redisCachingSettings", ref: rediscachingsettings }
- { title: "redisCachedItems", ref: rediscacheditems }
- { title: "Serilog", ref: serilog }
- { title: "MinimumLevel-ի կարգավորում", ref: minimumlevel-ի-կարգավորում }
- { title: "Լոգի գրանցում ֆայլում", ref: լոգի-գրանցում-ֆայլում }
- { title: "Լոգի գրանցում Seq սերվերում", ref: լոգի-գրանցում-seq-սերվերում }
- { title: "Լոգի ֆիլտրում", ref: լոգի-ֆիլտրում }
- { title: "Մի քանի լոգերի կիրառում", ref: մի-քանի-լոգերի-կիրառում }
- { title: "Storage", ref: storage }
---

## Բովանդակություն

- [Բովանդակություն](#բովանդակություն)
- [Ներածություն](#ներածություն)
- [additionalSettings](#additionalsettings)
- [Autentication](#autentication)
- [db](#db)
- [Extensions](#extensions)
- [Hangfire](#hangfire)
- [JwtConfig](#jwtconfig)
- [OTLP](#otlp)
- [redisCachingSettings](#rediscachingsettings)
  - [redisCachedItems](#rediscacheditems)
- [Serilog](#serilog)
  - [MinimumLevel-ի կարգավորում](#minimumlevel-ի-կարգավորում)
  - [Լոգի գրանցում ֆայլում](#լոգի-գրանցում-ֆայլում)
  - [Լոգի գրանցում Seq սերվերում](#լոգի-գրանցում-seq-սերվերում)
  - [Լոգի ֆիլտրում](#լոգի-ֆիլտրում)
  - [Մի քանի լոգերի կիրառում](#մի-քանի-լոգերի-կիրառում)
- [Storage](#storage)

## Ներածություն

[appsettings.json](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration)-ը նախատեսված է 8X սերվիսի աշխատանքի կարգավորման պարամետրերը սահմանելու համար, ինչպիսիք են տվյալների բազայի Sql Connection-ը, լոգավորման կարգավորումները:
Այստեղ ավելացվում են կարգավորումներ, որոնք պարունակում են գաղտնիք (password) կամ որոնք էականորեն փոխում են 8X սերվիսի պահվածքը։ 
Նման պարամետրորը նպատակահարմար չէ պահել 4X հարթակի համակարգային պարամետրերի մեջ։

Տե՛ս նաև
- [All About AppSettings In ASP.NET Core](https://www.c-sharpcorner.com/article/all-about-appsettings-in-asp-net-core/)
- [Configuration in .NET](https://learn.microsoft.com/en-us/dotnet/core/extensions/configuration)
- [Configuration in ASP.NET Core](https://learn.microsoft.com/en-us/aspnet/core/fundamentals/configuration/)
- [ՀԾ-Ձեռնարկություն, ՀԾ-Աշխատավարձ և ՀԾ-Բանկ համակարգերի գրանցման մեխանիզմի ինտեգրացումը Azure AD-ի հետ](https://support.armsoft.am/ViewKnowlageBaseArticle.aspx?KnowlageBaseArticleId=0bac001e-11d6-ee11-8f70-00155d643014)
- [ՀԾ-Ձեռնարկություն, ՀԾ-Աշխատավարձ և ՀԾ-Բանկ համակարգերի գրանցման մեխանիզմի ինտեգրացումը Windows ADFS-ի հետ](https://support.armsoft.am/ViewKnowlageBaseArticle.aspx?KnowlageBaseArticleId=92e2c510-43eb-ee11-8f70-00155d643014)
- [Սխալների լոգավորման կազմակերպում](https://support.armsoft.am/ViewKnowlageBaseArticle.aspx?KnowlageBaseArticleId=78fe933a-07c5-eb11-8f3e-00155d644419)
  - [Serilog.Settings.Configuration](https://github.com/serilog/serilog-settings-configuration)
  - [Serilog Expressions](https://github.com/serilog/serilog-expressions)

## additionalSettings

Նախկինում 8X սերվիս լոգին լինելու համար անհրաժեշտ էր միայն մուտքանուն և գաղտնաբառ, որի արդյունքում ստացվում էր JWT token, որի միջոցով օգտագործողը նույնականացվում էր և կարող էր կատարել կամայական API կանչեր։

Այժմ մտցվել է API Client-ի գաղափար, որը նախատեսված է 8X սերվիս մուտք գործող կլիենտ ծրագրի սահմանման համար։  
Այն անհրաժեշտ է ստեղծել 4X կամ 8X համակարգի UI-ից "**API Client-ներ**" դիտելու ձևից "**Ավելացնել**" կոնտեքստային ֆունկցիայով՝ նշելով կլիենտի վավերականացման եղանակը (սերտիֆիկատով կամ բանալիով) և նկարագրելով Json ֆորմատի **Manifest** ֆայլ, որը սահմանում է կլիենտ ծրագրի իրավասությունները և սահմանափակումները (որ օգտագործողները կարող են մուտք գործել համակարգ, որ տվյալների աղբյուրներին, փաստաթղթերին, DPR-ներին կարող են դիմել ու որ API կանչերը կատարել)։

![api_client_add](../images/api_client_add.png)

Այս հայտանիշը ավելացվել է հին լոգինի մեխանիզմը անջատելու համար։

```json
"additionalSettings": {
    "disableOldLogins": false
}
```

**Պարամետրեր**
* `disableOldLogins` - Լոգինի հին մեխանիզմի անջատման հայտանիշ։

## Autentication

Azure AD-ով կամ Windows ADFS-ով նույնականացման կարգավորումներ։  
Մանրամասների համար տե՛ս 
- [ՀԾ-Ձեռնարկություն, ՀԾ-Աշխատավարձ և ՀԾ-Բանկ համակարգերի գրանցման մեխանիզմի ինտեգրացումը Azure AD-ի հետ](https://support.armsoft.am/ViewKnowlageBaseArticle.aspx?KnowlageBaseArticleId=0bac001e-11d6-ee11-8f70-00155d643014)
- [ՀԾ-Ձեռնարկություն, ՀԾ-Աշխատավարձ և ՀԾ-Բանկ համակարգերի գրանցման մեխանիզմի ինտեգրացումը Windows ADFS-ի հետ](https://support.armsoft.am/ViewKnowlageBaseArticle.aspx?KnowlageBaseArticleId=92e2c510-43eb-ee11-8f70-00155d643014)։

Այս կարգավորումները հարկավոր է լինեն նույնը 8X սերվիսի և կոնֆիգուրացիոն սերվիսի համար։

```json
"Autentication": {
    "Alternative": "AD",
    "AD": {
        "Authority": "https://login.microsoftonline.com/yourdomain.am",
        "ClientId": "158u5wn2-2n95-14nm-22b2-9694efe14vae",
        "RedirectUri": "https://yourdomain.am/b2bAdminTool",
        "TokenMapping": "oid",
        "ResourceID": "https://yourdomain.am/Cloud"
    },
    "ADFS": {
        "Authority": "https://federationservername.yourdomain.am/adfs",
        "ClientId": "v04c6fd-4220-14e6-n315-f147ac852c18",
        "RedirectUri": "https://localhost:44322",
        "TokenMapping": "sid"
    }
}
```

**Պարամետրեր**
* `Alternative` - Սահմանում է օգտագործողի նույնականացման եղանակը՝ `AD` կամ `ADFS`։
* `AD` - Կարգավորում է Azure Active Directory-ով նույնականացման կարգավորումները։
  * `Authority` - Oգտագործողի նույնականացման համար անհրաժեշտ URL-ը։
  * `ClientId` - Ծրագրի Client ID-ն, որը գրանցված է Azure AD-ում:
  * `RedirectUri` - Նույնականացումից հետո վերահղման համար URL-ը:
  * `TokenMapping` - Նույնականացման համար անհրաժեշտ տոկենի տեսակը` OID:
  * `ResourceID` - Ծրագրի կողմից մուտքագրվող ռեսուրսի URL-ը:
* `ADFS` - Կարգավորում է Active Directory Federation Services (ADFS)-ով նույնականացման կարգավորումները։
  * `Authority` - Oգտագործողի նույնականացման համար անհրաժեշտ URL-ը։
  * `ClientId` - Ծրագրի Client ID-ն, որը գրանցված է ADFS-ում:
  * `RedirectUri` - Նույնականացումից հետո վերահղման համար URL-ը:
  * `TokenMapping` - Նույնականացման համար անհրաժեշտ տոկենի տեսակը` [SID](https://www.techtarget.com/searchsecurity/definition/security-identifier):

## db

Այս բաժինը նախատեսված է տվյալների բազայի կարգավորումները տալու համար։

```json
"db": {
    "server": "TEST-SERVER",
    "database": "test_db",
    "login": "test-user",
    "password": "test-password",
    "readOnly" : "1",
    "maxPoolSize" : 100,
    "customerId": "100000",
    "encrypt": false
}
```

**Պարամետրեր**
* `server` - Սերվերի անուն։
* `database` - Սերվերում գտնվող տվյալների բազայի անուն։
* `login` - Տվյալների բազայի սերվերին մուտք գործելու համար օգտագործվող մուտքանունը։
* `password` - Տվյալների բազայի սերվերին մուտք գործելու համար օգտագործվող գաղտնաբառը։
* `readOnly` - Նշում է, թե արդյոք տվյալների բազային միացումը միայն կարդալու իրավասությամբ, է թե ոչ։ Ընդունում է "0" կամ "1" արժեք։ Լռությամբ արժեքը "0" է։
* `maxPoolSize` - Տվյալների բազային [միացումների Pool](https://www.linkedin.com/pulse/how-sql-connection-pool-works-prashant-pathak/)-ում միացումների առավելագույն քանակը։ Լռությամբ արժեքը 100 է։
* `customerId` - Պատվիրատուի նույնակացման համար։ Օգտագորվում է ՀԾ-Ձեռնարկության և ՀԾ-Աշխատավարձի 8X սերվիսների կողմից։
* `encrypt` - Նշում է, թե արդյոք տվյալների բազային միացումը ծածկագրվի, թե ոչ։ Լռությամբ արժեքը false է։

## Extensions

Այս բաժինը նախատեսված է կազմակերպության սեփական նկարագրությունները և ընդլայնումները պարունակող պրոյեկտ(ներ)ի սահմանման համար։
Ընդլայնող պրոյեկտ(ներ)ը անհրաժեշտ է նախապես ստեղծել, կարգավորել (ստեղծման, կարգավորման եղանակին ծանոթանալու համար [տե՛ս](customer_specific_extensions_project.md)) և build անել, որի արդյունքում ձևավորվում են dll-ներ։

```json
"Extensions": [
    {
        "Id": "ACS",
        "Name": "Organisation Specific Definitions project",
        "Location": "Organisation-DLLs",
        "MainAssembly": "Organisation.Specific.Definitions.dll",
        "SystemType": "Bank",
        "Assemblies": [
                "Security.Authentication.dll",
                "Seq.Api.dll"
            ]
        }
    ],
```

**Պարամետրեր**
* `Id` - **Ոչ պարտադիր**: Պրոյեկտի id-ն։
* `Name` - **Պարտադիր**: Պրոյեկտի անունը, որը օգտագործվում է ընդլայնող dll-(ներ)ի բեռնման ընթացքում առաջացած սխալների լոգավորման համար։
* `Location` - **Պարտադիր**: Ընդլայնող dll-ները պետք է տեղակայված լինեն սերվիսի Publish-ի թղթապանակում և այս դաշտում անհրաժեշտ է նշել այդ dll-ների հարաբերական ճանապարհը Publish-ի թղթապանակի նկատմամբ, որպեսզի դրանք հասանելի լինեն Production-ում։
Օր․՝ եթե ընդլայնող dll-ները պատճենվել են Publish-ի թղթապանակի "Organisation-DLLs" ենթաթղթապանակում, ապա Location-ի արժեքը պետք է լինի "Organisation-DLLs"։
**Յուրաքանչյուր նոր տարբերակի տեղադրման ժամանակ՝ ընդլայնող dll-ում փոփոխությունների դեպքում, պրոյեկտը անհրաժեշտ է կրկին build անել և տեղադրել Publish-ի թղթապանակում։**
* `MainAssembly` - **Պարտադիր**։ Հիմնական ընդլայնող dll-ի անունը, որը պետք է տեղակայված լինի **Location**-ում նշված հասցեում։ Օրինակ՝ **"Organisation.Specific.Definitions.dll"**։
* `SystemType` - **Պարտադիր**։ Այն ծրագրի անունը, որում ավելացվելու է ընդլայնող dll-(ներ)ը։ Կարող է ընդունել հետևյալ արժեքները՝
  * `Wages` - ՀԾ ՄՌԿ
  * `Enterprise` - ՀԾ Ձեռնարկություն
  * `Bank` - ՀԾ Բանկ
* `Assemblies` - **Ոչ պարտադիր**: dll-ների անունների զանգված, որոնք անհրաժեշտ են **MainAssembly**-ում նշված assembly-ին աշխատանքի համար։ dll-ները պետք է տեղակայված լինեն **Location**-ում նշված հասցեում։ 

## Hangfire

[Hangfire](https://www.bytehide.com/blog/hangfire-dotnet)-ը գրադարան է, որը նախատեսված է background job-երի հերթի դրման և կատարման մեխանիզմը ապահովելու համար։

```json
"IsHangfireServer": false

"Hangfire": {
    "server": "TEST-SERVER",
    "database": "test_db",
    "login": "test-user",
    "password": "test-password",
    "workerCount": 10,
    "expirationInDays": 1
}
```

**Պարամետրեր**
* `IsHangfireServer` - Hangfire Server-ի միացման հայտանիշ։
* `server` - Սերվերի անունը, որտեղ գտնվում է Hangfire-ի տվյալների բազան:
* `database` - Տվյալների բազայի անունը, որը օգտագործում է Hangfire-ը:
* `login` -  Տվյալների բազայի սերվերին մուտք գործելու համար օգտագործվող մուտքանունը։
* `password` - Տվյալների բազայի սերվերին մուտք գործելու համար օգտագործվող գաղտնաբառը։
* `workerCount` - Ֆոնային աշխատող պրոցեսների քանակը, որոնք Hangfire-ը պետք է օգտագործի առաջադրանքները մշակելու համար։
* `expirationInDays` - Նշում է օրերի քանակը, որից հետո մշակված առաջադրանքները կհամարվեն ժամկետանց և կջնջվեն տվյալների բազայից։

## JwtConfig

8X սերվիսում ծրագրային նույնականացվելուց սերվիսը տրամադրվում է JWT Token, որը օգտագործվում է API կանչերի ժամանակ նույնականությունը ստուգելու համար: 
Այս բաժնում սահմանված են JWT Token-ի կարգավորումները։

```json
"JwtConfig": {
    "secret": "7V{)Grmn0/12cx^TY<gnl.568",
    "issuer": "test_db",
    "expirationInMinutes": 1440,
    "refreshExpirationInMinutes": 43200
}
```

**Պարամետրեր**
* `secret` - JWT Token-ի վավերականացման ու ստորագրման համար նախատեսված բանալի։
* `issuer` - Token-ը թողարկող տվյալների բազայի անունը։
* `expirationInMinutes` - JWT Token-ի վավերականության տևողությունը րոպեներով։
* `refreshExpirationInMinutes` - Թարմացման Token-ի վավերականության տևողությունը րոպեներով:

## OTLP

Այս բաժինը նախատեսված է trace-ների և մետրիկաների կարգավորումների սահմանման համար։ 

```json
"OTLP": {
    "Metrics": {
        "EnableDefaultInstrumantations": false,
        "PeriodicExporting": {
            "ExportIntervalMilliseconds": 10000
            },
        "CachedItemsCountEnabled": false
        },
      "Tracing": {
          "EnableDefaultInstrumantations": false,
          "SqlClientInstrumentation": {
              "Enabled": false,
              "AddSqlParameters": false
            }
        }
    }
```

**Պարամետրեր**
* `Metrics` - Այս բաժինը նախատեսված է մետրիկաների կարգավորման համար։
  * `EnableDefaultInstrumantations` - Ծրագրի աշխատանքի ընթացքում եկած Api հարցումների մասին մետրիկաների հավաքագրման հայտանիշ։ Լռությամբ արժեքը `false` է։
  * `PeriodicExporting` - Այս բաժինը նախատեսված է պարբերական մետրիկաների կարգավորման համար։
    * `ExportIntervalMilliseconds` - Պարբերական մետրիկաների արտահանման ինտերվալը միլիվայրկյաններով։
  * `CachedItemsCountEnabled` - Lite և RO Document-ների օբյեկտների քանակի գրանցման հայտանիշ։ Լռությամբ արժեքը `false` է։

* `Tracing` - Այս բաժինը նախատեսված է trace-ների կարգավորման համար։
  * `EnableDefaultInstrumantations` - Ծրագրի աշխատանքի ընթացքում եկած Api հարցումների մասին trace-ների հավաքագրման հայտանիշ։ Լռությամբ արժեքը `false` է։
  * `SqlClientInstrumentation` - Այս բաժինը նախատեսված է Sql հարցումների համար trace-երի կարգավորման համար։
    * `Enabled` - Ծրագրի աշխատանքի ընթացքում կատարված Sql հարցումների համար trace-երի հավաքագրման հայտանիշ։ Լռությամբ արժեքը `false` է։
    * `AddSqlParameters` - Sql հարցման պարամետրերի մասին ինֆորմացիան trace-երում ներառման հայտանիշ։ Լռությամբ արժեքը `false` է։

## redisCachingSettings

Redis-ը նախատեսված է տվյալների քեշավորման և արագ բեռնման համար։ 
Այս բաժնում սահմանված են Redis-ի կարգավորումները։

```json
"redisCachingSettings": {
    "enabled": false,
    "connectionString": "dockerub1:6379,password=mypassword"
}
```

**Պարամետրեր**
* `enabled` - Redis-ով տվյալների քեշավորման միացման հայտանիշ։
* `connectionString` - Redis սերվերին միացման Connection string-ը։
  Տե՛ս [Redis Connection Strings](https://docs.servicestack.net/redis/client-managers)։

### redisCachedItems

Այս բաժինը նախատեսված է կարգավորելու Redis սերվերում պահվող առանձին տվյալներ և պահպանման տևողությունը։ 
Այն ընդլայնվում է և առաձին պրոյեկտներում կարող է ավելի շատ լինել։  
Օրինակ ՀԾ-Բանկի սերվիսը տալիս է OLAP կարգավորումների քեշավորման պարամետրերը։

8X հարթակում նվազագույնը առկա են հետևյալ կարգավորումները փաստաթղթի մետատվյալները, պարամետրերը և մոնիտորինգի համար անհրաժեշտ տվյալները քեշավորելու համար։
```json
"redisCachedItems": {
    "documentMetadata": {
        "enabled": true,
        "lifetime": "1.00:00:00"
    },
    "monitoring": {
        "enabled": true,
        "lifetime": "0.00:01:00"
    },
    "parameters": {
        "enabled": true,
        "lifetime": "1.00:00:00"
    }
}
```

Յուրաքանչյուր բաժին պարունակում է երկու պարամետր՝
* `enabled` - Թույլատրված է քեշավորումը Redis-ում, թե ոչ։
* `lifetime` - Քեշի պահպանման տևողությունը Redis-ում։ Լռությամբ արժեքը 1 օրն է։



## Serilog

8X սերվիսում լոգերի հավաքագրման համար օգտագործվում է [Serilog](https://serilog.net/) գրադարանը։ 
appsettings.json-ում կարգավորումների ձևը որոշվում է Serilog գրադարանի կողմից։

Լոգավորումը հնարավոր է կարգավորել այնպես, որ լոգը գրանցվի Console-ում, ֆայլում կամ [Seq սերվերում](https://datalust.co/seq)։ 
Հնարավոր է կարգավորել, որ միաժամանակ մի քանի աղբյուրում կատարվի լոգի գրանցում։
Այդ թվում կիրառելով որոշակի ֆիլտր։

Տե՛ս նաև 
- [Serilog.Settings.Configuration](https://github.com/serilog/serilog-settings-configuration)
- [Սխալների լոգավորման կազմակերպում](https://support.armsoft.am/ViewKnowlageBaseArticle.aspx?KnowlageBaseArticleId=78fe933a-07c5-eb11-8f3e-00155d644419)։

### MinimumLevel-ի կարգավորում

Այստեղ կարգավորվում է լոգի պահպանման մակարդակը (Information, Warning, Error, Debug, Trace)։

Օրինակ՝
```json
"Serilog": {
    "MinimumLevel": {
        "Default": "Information",
        "Override": {
            "Microsoft": "Warning",
            "System": "Warning",
            "Microsoft.AspNetCore": "Warning",
            "Serilog.AspNetCore": "Warning"
        }
    }
}
```
**Պարամետրեր**

* `MinimumLevel:Default` - Կարգավորովում է լոգի պահպանման մակարդակը (Information, Warning, Error, Debug, Trace) ընդհանուր դեպքում։
* `MinimumLevel:Override` - Կարգավորովում է լոգի պահպանման մակարդակը առանձին աղբյուրների համար։

### Լոգի գրանցում ֆայլում

Ֆայլում գրանցումը ապահովելու համար անհրաժեշտ է `Serilog` բաժնի `WriteTo` ենթաբաժնում ավելացնել դրան հատուկ պարամետրերը։
 
```json
"Serilog": {
    "WriteTo": [
        {
            "Name": "File",
            "Args": {
                "path": "./logs/log.json",
                "rollingInterval": "Day",
                "formatter": "Serilog.Formatting.Compact.CompactJsonFormatter, Serilog.Formatting.Compact"
            }
        }
    ]
}
```

**Պարամետրեր**
* `Name` - Գրելով `File` նշում են, որ լոգավորումը կատարվում է ֆայլում։
* `Args` - Գրանցման ֆայլի կարգավորումները։
  * `path` - Ֆայլի հարաբերական ճանապարհը appsettings.json ֆայլի նկատմամբ։
  * `rollingInterval` - Լոգերի գրանցման համար անհրաժեշտ նոր ֆայլի ստեղծման հաճախականությունը։
    Այս օրինակում նշված է Day, որ նշանակում է, որ ամեն օրվա լոգերի համար ստեղծվում է նոր ֆայլ։
  * `formatter` - Լոգերի գրանցման ֆորմատը(JSON, XAML, ...):
    Օրինակում նշված արժեքը առավել հարմար է լոգերի հետ հետագա աշխատանքի համար։

### Լոգի գրանցում Seq սերվերում

Seq սերվերում գրանցումը ապահովելու համար անհրաժեշտ է `Serilog` բաժնի `WriteTo` ենթաբաժնում ավելացնել դրան հատուկ պարամետրերը։

```json
"Serilog": {
    "WriteTo": [
        {
            "Name": "Seq",
            "Args": {
                "serverUrl": "http://95.140.203.18:8443",
                "bufferBaseFilename": "./logs/buffer"
            }
        }
    ]
}
```

**Պարամետրեր**
* `Name` - Գրելով `Seq` նշում են, որ լոգավորումը կատարվում է Seq սերվերում։
* `Args` - Գրանցման Seq-ի կարգավորումները։
  * `serverUrl` - Seq-ի սերվերի հասցեն։
  * `bufferBaseFilename` - Սերվերի անհասանելի լինելու դեպքում լոգերի գրանցման համար անհրաժեշտ ֆայլի հարաբերական ճանապարհը appsettings.json ֆայլի նկատմամբ։
    Սերվերը հասանելի դառնալուն պես ֆայլում գրանցված լոգերը գրանցվում են Seq-ում։

### Լոգի ֆիլտրում

Լոգը կարելի գրանցել կիրառելով որոշ ֆիլտրեր։
Ստորև օրինակում ֆիլտրվում է ըստ լոգի ConnectedService դաշտի 'ArCaP2P' արժեքի և լոգավորումը պահպանում է ArCaP2P_XXXXXXXX.json անունով ֆայլում (XXXXXXXX-ի փոխարեն գրված ամսաթիվ):

```json
"Serilog": {
  "WriteTo": [
    {
      "Name": "Logger",
      "Args": {
        "configureLogger": {
          "Filter": [
            {
              "Name": "ByIncludingOnly",
              "Args": {
                "expression": "@p['ConnectedService'] = 'ArCaP2P'"
              }
            }
          ],
          "WriteTo": [
            {
              "Name": "File",
              "Args": {
                "path": "./logs/ArCaP2P_.json",
                "formatter": "Serilog.Formatting.Compact.CompactJsonFormatter, Serilog.Formatting.Compact",
                "rollingInterval": "Day",
                "rollOnFileSizeLimit": true,
                "fileSizeLimitBytes": "1000000"
              }
            }
          ]
        }
      }
    }
  ]
}
```

Վերև լոգի կարգավորման մեջ կարևոր են 
* `"Name": "Logger"` - Նշում է որ բարդ լոգ է։
* `"Filter"` - Կարգավորում է ֆիլտրը։ Տե՛ս նաև [Serilog Expressions](https://github.com/serilog/serilog-expressions)։


### Մի քանի լոգերի կիրառում

Ստորև օրինակում կարգավորված են վերևի երեք լոգերը միարժամանակ։

```json
"Serilog": {
  "MinimumLevel": {
    "Default": "Information",
    "Override": {
      "Microsoft": "Warning",
      "System": "Warning",
      "Microsoft.AspNetCore": "Warning",
      "Serilog.AspNetCore": "Warning"
    }
  },
  "WriteTo": [
    {
      "Name": "File",
      "Args": {
        "path": "./logs/log.json",
        "rollingInterval": "Day",
        "formatter": "Serilog.Formatting.Compact.CompactJsonFormatter, Serilog.Formatting.Compact"
      }
    },
    {
      "Name": "Seq",
      "Args": {
        "serverUrl": "http://95.140.203.18:8443",
        "bufferBaseFilename": "./logs/buffer"
      }
    },
    {
      "Name": "Logger",
      "Args": {
        "configureLogger": {
          "Filter": [
            {
              "Name": "ByIncludingOnly",
              "Args": {
                "expression": "@p['ConnectedService'] = 'ArCaP2P'"
              }
            }
          ],
          "WriteTo": [
            {
              "Name": "File",
              "Args": {
                "path": "./logs/ArCaP2P_.json",
                "formatter": "Serilog.Formatting.Compact.CompactJsonFormatter, Serilog.Formatting.Compact",
                "rollingInterval": "Day",
                "rollOnFileSizeLimit": true,
                "fileSizeLimitBytes": "1000000"
              }
            }
          ]
        }
      }
    }
  ]
}
```

## Storage

Սահմանում է ծրագրի աշխատանքի ընթացքում ստեղծվող ֆայլերի (Text reports, տպելու ձևանմուշներից առաջացած ֆայլեր, կամ այլ ֆայլեր) լոկալ պահպանման կարգավորումները։

```json
 "Storage": {
     "BaseUri": "http://localhost:1026/",
     "Directory": "C:\\Storage\\Files\\",
     "Permanent": {
         "Directory": "C:\\Storage\\PermanentFiles\\"
     }
 }
```

**Պարամետրեր**
* `BaseUri` - Սերվիսի հասցեն, որն օգտագործվում է ֆայլերի ծրագրային բեռնման կամ վերբեռնման դեպքում URL-ների ձևավորման համար։
* `Directory` - Ստեղծվող ժամանակավոր ֆայլերի պահպանման հիմնական թղթապանակի ճանապարհը։
* `Permanent` - Այս ենթաբաժինը նախատեսված է ստեղծվող մշտական ֆայլերի կարգավորման համար։
  * `Directory` - Ստեղծվող մշտական ֆայլերի պահպանման հիմնական թղթապանակի ճանապարհը։ 
