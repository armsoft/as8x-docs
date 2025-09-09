---
title: UIRequestExecutionProgress.AddCustomUIRequest<R, S>(S, int, int, Action<S>, bool) մեթոդ
---

```c#
public Task<CustomUIRequestResult<R>> AddCustomUIRequest<R, S>(S requestSource, 
                                                               int id,
                                                               int millisecondsToShow = 60000,
                                                               Action<S> toUnicode = null,
                                                               bool supportRememberTheAnswer = false);
```

Այս մեթոդը օգտագործվում է [DataSource](../../definitions/ds.md)-ի, [DPR](../../definitions/dpr.md)-ի, [Document](../../definitions/document.md)-ի կատարման ընթացքում 8X սերվիսից 4X կամ 8X կլիենտին տվյալներ փոխանցելու նպատակով, որոնց հիման վրա կլիենտում ստեղծվում և ցուցադրվում է պատուհան։ 

Տե՛ս օգտագործման [օրինակը](../../examples/AddCustomUIRequest.md)։

**Պարամետրեր**

* `R` - Կլիենտից ստացվող տվյալները նկարագրող դաս։
* `S` - Կլիենտին փոխանցվող տվյալները նկարագրող դաս։
* `requestSource` - Կլիենտին փոխանցվող տվյալները նկարագրող դասի օբյեկտ։
* `id` - Պատուհանի ներքին նույնականացման համարը (id):
* `millisecondsToShow` - Պատուհանի էկրանին երևալու ժամանակը միլիվայրկյաններով: Լռությամբ արժեքը 60 վայրկյանն է։
* `toUnicode` - Կլիենտին փոխանցվող տվյալները Unicode կոդավորման փոխակերպելու համար նախատեսված Action։
* `supportRememberTheAnswer` - «Կիրառել պատասխանը հաջորդների համար նույնպես» նշիչի ցուցադրման հայտանիշ։ Պարամետրի **true** արժեքի և նշիչի ընտրման դեպքում պատուհանը կփակվի այն կոճակով, որը սեղմվել է առաջին ցուցադրման ժամանակ։