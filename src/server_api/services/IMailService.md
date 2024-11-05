---
layout: page
title: "IMailService սերվիս" 
tags: email
sublinks:
- { title: "DBMailService, MailKitMailService", ref: ներածություն }
- { title: "SendMail", ref: sendmail }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Մեթոդներ](#մեթոդներ)
  - [SendMail](#sendmail)
- [Օրինակ](#օրինակ)


## Ներածություն

IMailService ինտերֆեյսը նախատեսված է էլեկտրոնային հաղորդագրություններ ուղարկելու համար։

Առկա է ինտերֆեյսի երկու իրականացում՝ `DBMailService` և `MailKitMailService`, ինյեկցիա հարկավոր է կատարել դրանցից որևէ մեկը։

- `DBMailService` - Էլ. նակաների ուղարկումը կատարվում է SQL սերվերի sp_send_dbmail պրոցեդուրայով։
- `MailKitMailService` - Էլ. նակաների ուղարկումը կատարվում է 8X սերվիսիս։

Տե՛ս [օրինակը](../examples/ITemplateSubstitutionService.md#օրինակ-1)։

## Մեթոդներ

### SendMail

```c#
public Task SendMail(MailArgs args)
```

Ուղարկում է էլեկտրոնային նամակ (email) ըստ `args` տվյալների։

**Պարամետրեր**

* `args` - [Էլ. նամակի տվյալներ](../types/MailArgs.md)։

