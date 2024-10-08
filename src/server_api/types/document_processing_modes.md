---
layout: page
title: "Փաստաթղթի ռեժիմներ"
tags: [PROCESSINGMODE]
---

## Բովանդակություն

* [Փաստաթղթի ռեժիմներ](#փաստաթղթի-ռեժիմներ)
  * [Կատարման ռեժիմներ](#կատարման-ռեժիմներ)
	  * [Նկարագրություն](#նկարագրություն) 
	  * [Արժեքների բազմություն](#արժեքների-բազմություն)
	  * [Փոփոխման եղանակ](#փոփոխման-եղանակ) 	  
  * [UI-ում ստեղծման և խմբագրման ռեժիմներ](#ui-ում-ստեղծման-և-խմբագրման-ռեժիմներ)
      * [Նկարագրություն](#նկարագրություն-1) 
	  * [Արժեքների բազմություն](#արժեքների-բազմություն-1)
	  * [Փոփոխման եղանակ](#փոփոխման-եղանակ-1) 
  * [Տպելու ձևանմուշների կատարման ռեժիմներ](#տպելու-ձևանմուշների-կատարման-ռեժիմներ)
      * [Նկարագրություն](#նկարագրություն-2) 
	  * [Արժեքների բազմություն](#արժեքների-բազմություն-2)
	  * [Փոփոխման եղանակ](#փոփոխման-եղանակ-2) 

## Կատարման ռեժիմներ

### Նկարագրություն

Փաստաթղթի հիմնական գործողություններն են Create, Store, Load, Delete:
Փաստաթղթի կատարման ռեժիմները որոշում են վերոնշյալ գործողությունների սերվերային տրամաբանության կատարման սերվիսը՝ 4X թե 8X service:

### Արժեքների բազմություն

- 0 – 4X-ից փաստաթղթի գործողությունները (Store, Load, Create, Delete) կատարվում են առանց սերվիսի, իսկ սերվիսում Store, Delete արգելված են: Առաջարկվում է ներկայիս 0 արժեքի դեպքում կիրառել սա
    
- 4 - 4X-ից փաստաթղթի գործողությունները (Store, Load, Create, Delete) կատարվում են առանց սերվիսի, իսկ սերվիսում Store, Delete թույլատրված են:
    
- 8 - 4X-ից փաստաթղթի գործողությունները (Load, Create) կատարվում են առանց սերվիսի, (Store, Delete), եթե տրանզակցիայի տակ չի սերվիսով, եթե տրանզակցիայի տակ է առանց սերվիսի, իսկ սերվիսում Store, Delete թույլատրված են:
    
- 12 – 4X-ից փաստաթղթի գործողությունները (Load, Create) կատարվում են առանց սերվիսի (Store, Delete) կատարվում են սերվիսով, իսկ սերվիսում Store, Delete թույլատրված են: Պետք է առաջացվի սխալ, եթե 4x-ում Store, Delete կկանչվի, երբ տրանզակցիա կա:
    
- 16 – 4X-ից փաստաթղթի գործողությունները (Store, Load, Create, Delete) կատարվում են սերվիսով, իսկ սերվիսում Store, Delete թույլատրված են: Պետք է առաջացվի սխալ, եթե 4x-ում Store, Delete կկանչվի, երբ տրանզակցիա կա:

`Constants.def` ֆայլում սահմանած են այս արժեքներին համապատասխան հաստատուններ, որոնք կարելի է օգտագործել փաստաթղթի նկարագրության PROCESSINGMODE հատկությանը վերագրելիս։

* DocProcessingMode0 = 0
* DocProcessingMode1 = 4
* DocProcessingMode2 = 8 
* DocProcessingMode3 = 12
* DocProcessingMode4 = 16

### Փոփոխման եղանակ

Փաստաթղթի կատարման ռեժիմը կարելի է փոխել 2 եղանակով՝
- “Համակարգային նկարագրություններ” դիտելու ձևի “Փոխել կատարման ռեժիմը” կոնտեքստային ֆունկցիայով բացվող ֆիլտրման պատուհանի “Փաստաթղթի կատարման ռեժիմ” հայտանիշով:   
- Փաստաթղթի նկարագրության ֆայլում PROCESSINGMODE հատկությունում գումարելով անհրաժեշտ արժեքը և նկարագրությունը ներմուծելով տվյալների բազա։

## UI-ում ստեղծման և խմբագրման ռեժիմներ

### Նկարագրություն

Նախատեսված է փաստաթղթի ստեղծման և խմբագրման պատուհանները բացելու թույլտվությունը 4x և 8x UI-ներում կարգավորելու համար։

### Արժեքների բազմություն

- 0 - Փաստաթղթի ստեղծման և խմբագրման պատուհանը թույլատրված է բացել և 4x և 8x UI-ներում։    
- 32 - Փաստաթղթի ստեղծման և խմբագրման պատուհանը թույլատրված է բացել միայն 4x UI-ում։
- 64 - Փաստաթղթի ստեղծման և խմբագրման պատուհանը թույլատրված է բացել միայն 8x UI-ում։

`Constants.def` ֆայլում սահմանած են այս արժեքներին համապատասխան հաստատուններ, որոնք կարելի է օգտագործել փաստաթղթի նկարագրության PROCESSINGMODE հատկությանը վերագրելիս։

* DocCreateAndEditEnabledIn4xAnd8x = 0
* DocCreateAndEditEnabledIn4x = 32
* DocCreateAndEditEnabledIn8x = 64

### Փոփոխման եղանակ

Փաստաթղթի Ստեղծման և խմբագրման ռեժիմը UI-ում կարելի է փոխել 2 եղանակով՝
- “Համակարգային նկարագրություններ” դիտելու ձևի “Փոխել կատարման ռեժիմը” կոնտեքստային ֆունկցիայով բացվող ֆիլտրման պատուհանի “Փաստաթղթի ստեղծման և խմբագրման ռեժիմ UI-ում” հայտանիշով:   
- Փաստաթղթի նկարագրության ֆայլում PROCESSINGMODE հատկությունում գումարելով անհրաժեշտ արժեքը և նկարագրությունը ներմուծելով տվյալների բազա։

## Տպելու ձևանմուշների կատարման ռեժիմներ

### Նկարագրություն

Տպելու ձևանմուշի ստեղծման գործընթացը բաղկացած է 2 հիմնական փուլերից՝
-   Բանաձևերի և տվյալների հաշվարկ,
-   Ֆայլի ստեղծում և լրացում։

### Արժեքների բազմություն

- 0 - Բանաձևերի, տվյալների հաշվարկը և ֆայլի ստեղծումն ու լրացումը կատարվում են 4x-ում։
    
- 1 - Բանաձևերի, տվյալների հաշվարկը հաշվարկը կատարվում է 8x սերվիսում, իսկ ֆայլի ստեղծումն ու լրացումը 4x-ում։
    
- 2 - Բանաձևերի, տվյալների հաշվարկը, ֆայլի ստեղծումն ու լրացումը կատարվում են 8x սերվիսում։
    
- 3 - Այս ռեժիմը անհրաժեշտ է օգտագործել այն դեպքում, երբ տվյալների բազայում տպելու ձևանմուշների կատարման ռեժիմը անհրաժեշտ է թողնել նույնը և փոխել միայն փաստաթղթի կատարման ռեժիմը։ Այն նախատեսված է միայն ծրագրային օգտագործման համար և հասանելի չէ օգտոգործողներին։

`Constants.def` ֆայլում սահմանած են այս արժեքներին համապատասխան հաստատուններ, որոնք կարելի է օգտագործել փաստաթղթի նկարագրության PROCESSINGMODE հատկությանը վերագրելիս։

* TSWithoutService = 0
* TSInServiceWithCalculatedData = 1
* TSAllInService = 2
* TSProcessingModeChangeNotRequired = 3

### Փոփոխման եղանակ

Փաստաթղթի տպելու ձևանմուշի կատարման ռեժիմը կարելի է փոխել 2 եղանակով՝
- “Համակարգային նկարագրություններ” դիտելու ձևի “Փոխել կատարման ռեժիմը” կոնտեքստային ֆունկցիայով բացվող ֆիլտրման պատուհանի “Տպվող տեսքերի լրացման ռեժիմ” հայտանիշով:   
- Փաստաթղթի նկարագրության ֆայլում PROCESSINGMODE հատկությունում գումարելով անհրաժեշտ արժեքը և նկարագրությունը ներմուծելով տվյալների բազա։
