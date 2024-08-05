---
layout: page
title: "AS-8X համակարգի պրոյեկտների նկարագրություն"
tags: [structure]
---

## Բովանդակություն

* [Ներածություն](#ներածություն)
* ՀԾ-Բանկի 8X սերվիսի պրոյեկտներ
  * [ArmSoft.AS8X.BankService](#armsoftas8xbankservice)
  * [ArmSoft.AS8X.Bank](#armsoftas8xbank)
  * [ArmSoft.AS8X.BankOLAP](#armsoftas8xbankolap)
  * [ArmSoft.AS8X.Bank.Samples](#ArmSoftas8xbanksamples)
* 8X հարթակի միջուկային պրոյեկտներ
  * [ArmSoft.AS8X.Service](#armsoft.as8x.service)
  * [ArmSoft.AS8X.Core](#armsoft.as8x.core)
  * [ArmSoft.AS8X.Common](#armsoft.as8x.common)
  * [ArmSoft.AS8X.Models](#armsoft.as8x.models)
* 8X հարթակի REST API տիպիզացված գրադարան
  * [ArmSoft.AS8X.Client](#armsoft.as8x.client)
* 8X հարթակի կոնֆիգուրացիոն սերվիս
  * [ArmSoft.AS8X.Configuration.Service](#armsoft.as8x.configuration.service)


## Ներածություն
Ստորև ներկայացված են ՀԾ-Բանկի 8X սերվիսի բաղադրիչ պրոյեկտները։

## ՀԾ-Բանկի 8X սերվիսի պրոյեկտներ
### ArmSoft.AS8X.BankService
Պրոյեկտը մուտքային կետն է 8X սերվիսի միացման համար։ Այն ASP.NET-ով պրոյեկտ է։  
Այն կարելի է ինչպես միացնել Debugging ռեժիմում այնպես էլ կառուցել և տեղադրել IIS-ում։

Պրոյեկտը պարունակում է ՀԾ-Բանկին յուրահատուկ REST API-ների նկարագրությունները Controller-ներով իրականացված։  

### ArmSoft.AS8X.Bank
Պրոյեկտը պարունակում է ՀԾ-Բանկին յուրահատուկ նկարագրությունները (փաստաթղթթերի, տվյալների աղբյուրներ...) և սերվիսները։ 

### ArmSoft.AS8X.BankOLAP
Պրոյեկտը պարունակում է OLAP հաշվետվությունների, OLAP բանաձևերին վերաբերող տրամաբանություններ։ 

### ArmSoft.AS8X.Bank.Samples
Պրոյեկտը պարունակում է ընդլայնումների օրինակներ՝  
- Փաստաթղթերի իրադարձություների ընլայնում,
- Տվյալների աղբյուրի ընդլայնում,
- Տպելու ձևերի ընդլայնում,
- Նոր Տվյալների աղբյուր,
- Նոր փաստաթուղթ,
- Վարկային հայտերի ցուցանիշ և պայման։

## 8X հարթակի միջուկային պրոյեկտներ
### ArmSoft.AS8X.Service
Պրոյեկտը պարունակում է 8X հարթակի միջուկային/գլխավոր REST API-ների նկարագրությունները Controller-ներով իրականացված։  

### ArmSoft.AS8X.Core
Պրոյեկտը պարունակում է 8X հարթակի 
- ընդհանուր տրամաբանությունները (նույնականացում, սեսիաների կառավարում, sql միացումների ղեկավարում, սխալների մշակում, մոնիտորինգ, դիագնոստիկա, ֆայլային համակարկ, էլ.փոստ ...),
- համակարգային նկարագրությունների (Document, DataSource, DPR ...) բազային դասերը,
- նկարագրությունների ընդլայնման ինտերֆեյսները (DocumentExtender, DataSource Extender ...), 
- հիմնական սերվիսները(IDBService, IDocumentService, IParametersService ...) և դրանց կարգավորող տրամաբանությունը,
- միջուկային փաստաթղթերի և տվյալների աղբյուրների իրականացումները։

### ArmSoft.AS8X.Common
Պրոյեկտը պարունակում է 8X հարթակի 
- միջուկային հաստատուններ,
- համակարգային տիպերը(BooleanFieldType, NumPairFieldType ...),
- միջուկային տրամաբանություն չիրականացնող դասեր (RESTException, ատտրիբուտներ, NoParam, NoColumns, NoResult ...)
- .as ֆայլերի վերծանման դասերը (Parser) և ստացված նկարագրությունները,
- C#-ի ներդրված տիպերի extension մեթոդներ պարունակող դասերը(DateExtensions, StringExtensions ...)։

### ArmSoft.AS8X.Models
Պրոյեկտը պարունակում է 8X հարթակի REST API-ին փոխանցվող և դրանից վերադարձվող դասերը։

## 8X հարթակի REST API տիպիզացված գրադարան
### ArmSoft.AS8X.Client
Պրոյեկտը պարունակում է 8X հարթակի REST API-ին դիմող դասերը։

## 8X հարթակի կոնֆիգուրացիոն սերվիս
### ArmSoft.AS8X.Configuration.Service
Պրոյեկտը առաձին սերվիս է, որի միջոցով հնարավոր է ստանալ տարբեր տվյալներ տեղադրված 8X սերվիսների վերաբերյալ։ Այն ASP.NET-ով պրոյեկտ է։  
