---
layout: page
title: "IUIRequestExecutionProgress ինտերֆեյս" 
tags: Indicate, Progress
sublinks:
- { title: "UIRequestEnabled", ref: uirequestenabled }
- { title: "AddCustomUIRequest", ref: addcustomuirequest }
- { title: "MessageBox", ref: messagebox }
---

## Բովանդակություն

- [Ներածություն](#ներածություն)
- [Հատկություններ](#հատկություններ)
  - [UIRequestEnabled](#uirequestenabled)
- [Մեթոդներ](#մեթոդներ)
  - [AddCustomUIRequest](#addcustomuirequest)
  - [MessageBox](#messagebox)
  - [MessageBox](#messagebox-1)

## Ներածություն

IUIRequestExecutionProgress ինտերֆեյսը նախատեսված է [Փաստաթղթի](../definitions/document.md) և [Տվյալների մշակման հարցման (DPR)](../definitions/dpr.md) կատարման ընթացքում սերվերից կլիենտին [հարցումներ ուղարկելու](#addcustomuirequest), կլիենտում [հաղորդագրության պատուհան ցույց տալու](#messagebox) և պատասխանը ստանալու ֆունկցիոնալությունը ապահովելու համար։

Իրականացնում է [IExecutionProgress](IExecutionProgress.md)

## Հատկություններ

### UIRequestEnabled

```c#
bool UIRequestEnabled { get; }
```

Ստուգում է արդյոք հասանելի է օգտագործողի ինտերֆեյսը և արդյոք թույլատրված է հաղորդագրության պատուհան ցույց տալ, կամ կատարել այլ ինտերֆեյսային գործողություն։  
Միայն `true` արժեքի դեպքում հնարավոր ցույց տալ սերվիսից եկող [հաղորդագրության պատուհան](#messagebox)։

## Մեթոդներ

### AddCustomUIRequest

```c#
Task<CustomUIRequestResult<R>> AddCustomUIRequest<R, S>(S requestSource, 
                                                        int id,
                                                        int millisecondsToShow = 60000,
                                                        Action<S> toUnicode = null,
                                                        bool supportRememberTheAnswer = false);
```

Այս մեթոդը օգտագործվում է [Փաստաթղթի](../definitions/document.md) և [Տվյալների մշակման հարցման (DPR)](../definitions/dpr.md) կատարման ընթացքում 8X սերվիսից կլիենտին կատարվում է հարցում, որի հիման վրա կլիենտում ստեղծվում և ցուցադրվում է պատուհան, ապա մուտքագրված արժեքները վերադարձվում են 8X սերվիսին։  

Տվյալներ կարող եմ չփոխանցվել և չվերադարձվել։ 
Այդ դեպքում օգտագործվում են `NoParam` և `NoResult` տիպերը։

Տե՛ս օգտագործման օրինակներ՝ [տվյալների փոխանցում](../examples/IUIRequestExecutionProgress.md#օրինակ-2), [տվյալների ստացում](../examples/IUIRequestExecutionProgress.md#օրինակ-3)։

**Պարամետրեր**

* `R` - Կլիենտից ստացվող տվյալները նկարագրող դաս։
* `S` - Կլիենտին փոխանցվող տվյալները նկարագրող դաս։
* `requestSource` - Կլիենտին փոխանցվող տվյալները նկարագրող դասի օբյեկտ։
* `id` - Հարցման նույնականացուցիչ։ 
  Այս նույնականացուցիչը մշակվում է նաև կլիենտական կողմում, որպեսզի որոշվի կլիենտում հարցումը մշակող ֆունկցիան:
* `millisecondsToShow` - Կլիենտից պատասխան սպասելու առավելագույն ժամանակը։  
  Կլիենտական ինտերֆեյսում պատուհան ցույց տալուց, պատուհանը հարկավոր է ցույց տալ ավելի պակաս ժամանակ, և սերվերին պատասխան ուղարկել մինչ ժամանակի լրանալը: Օրինակ՝ սերվերը սպասում է 60 վրկ, իսկ պատուհանը ցույց տրվի 50 վրկ։  
  Լռությամբ արժեքը 60 վայրկյան։
* `toUnicode` - Կլիենտին փոխանցվող տվյալները յունիկոդ կոդավորելու ֆունկցիա։
* `supportRememberTheAnswer` - `true` արժեքի դեպքում կլինետին հարցում չի լինի, եթե նույն `id`-ով արդեն հարցում եղել է ընթացիկ պրոցեսի ժամանակ և կլիենտից վերադարձվող պատասխանում նշված է, որ պատասխանը հարկավոր է կիրառել հաջորդ հարցումների փոխարեն, ապա ֆունկցիան կվերադարձնի նախորդ հարցված պատասխանը։  
  Նախատեսված է տվյալների մշակման հարցման ժամանակ (DPR) մի քանի փաստաթուղթ գրանցելուց առաջինի համար կլիենտին հարցում կատարելու և երկխոսության պատուհան ցույց տալու համար, իսկ մյուս փաստաթղթերի դեպքում հարցումներ չկատարելու համար։ Նման դեպքերում ինտերֆեյսում երկխոսության պատուհանի վրա ավելացվում է «Կիրառել պատասխանը հաջորդների համար նույնպես» նշիչ։

### MessageBox

```c#
Task<MessageBoxResult> MessageBox(string prompt, MessageBoxButtons messageBoxButtons = MessageBoxButtons.OK,
                                  MessageBoxIconType messageBoxIcon = MessageBoxIconType.Default,
                                  MessageBoxDefaultButton messageBoxDefaultButton = MessageBoxDefaultButton.DefaultButton1,
                                  string title = "", int millisecondsToShow = 15000, int? id = null)
```

Այս մեթոդը օգտագործվում է [Փաստաթղթի](../definitions/document.md) և [Տվյալների մշակման հարցման (DPR)](../definitions/dpr.md) կատարման ընթացքում 8X սերվիսից 4X կամ 8X կլիենտին հաղորդագրություն ուղարկելու, հաղորդագրության պատասխանը ստանալու և այն սերվիսում մշակելու համար։

Տե՛ս օգտագործման [օրինակը](../examples/IUIRequestExecutionProgress.md#օրինակ-1)։

**Պարամետրեր**

* `prompt` - Հաղորդագրության պատուհանի տեքստը։
* `messageBoxButtons` - [Հաղորդագրության պատուհանում ավելացվող կոճակները](MessageBoxButtons.md): Չլրացնելու դեպքում պատուհանում ավելացվելու է միայն "Լավ" կոճակը։
* `messageBoxIcon` - [Հաղորդագրության պատուհանում ավելացվող պատկերակը](MessageBoxIconType.md)։ Չլրացնելու դեպքում պատուհանում ավելացվելու է "Information Message" պատկերակը։
* `messageBoxDefaultButton` - [Հաղորդագրության պատուհանի լռությամբ կոճակը](MessageBoxDefaultButton.md)։  
  Պատուհանի էկրանին երևալու ժամանակը լրանալուն պես պատուհանը ավտոմատ փակվում է` սեղմելով լռությամբ ընտրված կոճակը։  
  Չլրացնելու դեպքում լռությամբ կոճակ հանդիսանալու է ձախից առաջին կոճակը։
* `title` - Հաղորդագրության պատուհանի գլխագիրը։ 
  Չլրացնելու դեպքում գլխագիր հանդիսանալու է ծրագրի անունը՝ «ՀԾ Բանկ», «ՀԾ Ձեռնարկություն»...
* `millisecondsToShow` - Հաղորդագրության պատուհանի էկրանին երևալու ժամանակը միլիվայրկյաններով: 
  Չլրացնելու դեպքում պատուհանը փակվելու է 15 վրկ հետո՝ սեղմելով լռությամբ ընտրված կոճակը (`messageBoxDefaultButton`)։
* `id` - Հաղորդագրության պատուհանի նույնականացուցիչ:

### MessageBox

```c#
Task<MessageBoxResult> MessageBox(string prompt, MessageBoxButtons messageBoxButtons,
                                  MessageBoxIconType messageBoxIcon, 
                                  MessageBoxDefaultButton messageBoxDefaultButton,
                                  string title, TimeSpan timeSpanToShow, int? id = null)
```

Այս մեթոդը օգտագործվում է [Փաստաթղթի](../definitions/document.md) և [Տվյալների մշակման հարցման (DPR)](../definitions/dpr.md) կատարման ընթացքում 8X սերվիսից 4X կամ 8X կլիենտին հաղորդագրություն ուղարկելու, հաղորդագրության պատասխանը ստանալու և այն սերվիսում մշակելու համար։

**Պարամետրեր**

* `prompt` - Հաղորդագրության պատուհանի տեքստը։
* `messageBoxButtons` - [Հաղորդագրության պատուհանում ավելացվող կոճակները](MessageBoxButtons.md)։
* `messageBoxIcon` - [Հաղորդագրության պատուհանում ավելացվող պատկերակը](MessageBoxIconType.md)։ 
* `messageBoxDefaultButton` - [Հաղորդագրության պատուհանի լռությամբ կոճակը](MessageBoxDefaultButton.md)։  
  Պատուհանի էկրանին երևալու ժամանակը լրանալուն պես պատուհանը ավտոմատ փակվում է` սեղմելով լռությամբ ընտրված կոճակը։
* `title` - Հաղորդագրության պատուհանի գլխագիրը։
* `timeSpanToShow` - Հաղորդագրության պատուհանի էկրանին երևալու ժամանակը:
* `id` - Հաղորդագրության պատուհանի նույնականացուցիչ:

