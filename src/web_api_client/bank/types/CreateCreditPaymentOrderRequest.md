---
layout: page
title: CreateCreditPaymentOrderRequest դաս
---

Այս դասը նախատեսված է վճարման հանձնարարագիր փաստաթղթի ստեղծման համար։

Օգտագործվում է `PaymentDocsRoutes.CreateCreditPaymentOrder` մեթոդում։

```csharp
public class CreateCreditPaymentOrderRequest
{
    /// <summary> Գրասենյակ </summary>
    public string AcsBranch { get; set; }

    /// <summary> Բաժին </summary>
    public string AcsDepart { get; set; }

    /// <summary> Ամսաթիվ </summary>
    public DateTime? Date { get; set; }

    /// <summary> Նշում </summary>
    public string PayNote { get; set; }

    /// <summary> Փաստաթղթի N </summary>
    public string DocNumber { get; set; }

    /// <summary> Հաճախորդի կոդ </summary>
    public string ClientCode { get; set; }

    /// <summary> Ռեզիդենտություն </summary>
    public string Residence { get; set; }

    /// <summary> Հաշիվ դեբետ </summary>
    public string AccountDebit { get; set; }

    /// <summary> Վճարող </summary>
    public string Payer { get; set; }

    /// <summary> Վճարող անգլերեն </summary>
    public string PayerEng { get; set; }

    /// <summary> Վճարողի իրավաբանական կարգավիճակ </summary>
    public string PayerLegalState { get; set; }

    /// <summary> Վճարողի ՀՎՀՀ(վճարող) </summary>
    public string PayerTaxCode { get; set; }

    /// <summary> Վճարողի սոցիալական քարդ </summary>
    public string PayerSocialCard { get; set; }

    /// <summary> Հաշիվ կրեդիտ </summary>
    public string AccountCredit { get; set; }

    /// <summary> Ստացող բանկ </summary>
    public string ReceiverBank { get; set; }

    /// <summary> Ստացող </summary>
    public string Receiver { get; set; }

    /// <summary> Ստացող անգլերեն </summary>
    public string ReceiverEng { get; set; }

    /// <summary> Ստացողի իրավաբանական կարգավիճակ </summary>
    public string ReceiverLegalState { get; set; }

    /// <summary> Ստացողի ՀՎՀՀ(վճարող) </summary>
    public string ReceiverTaxCode { get; set; }

    /// <summary> Ստացողի սոցիալական քարդ </summary>
    public string ReceiverSocialCard { get; set; }

    /// <summary> Ստացողի անձը հաստատող փաստաթղթի տիպ </summary>
    public string ReceiverPassType { get; set; }

    /// <summary> Ստացողի անձը հաստատող փաստաթուղթ </summary>
    public string ReceiverPassNum { get; set; }

    /// <summary> Գումար </summary>
    public decimal Summa { get; set; }

    /// <summary> Նպատակ </summary>
    public string Aim { get; set; }

    /// <summary> Մուծող </summary>
    public string CashPayer { get; set; }

    /// <summary> Մուծողի անձը հաստատող փաստաթղթի տիպ </summary>
    public string PayerPassType { get; set; }

    /// <summary> Մուծողի անձը հաստատող փաստաթուղթ </summary>
    public string PayerPassNum { get; set; }

    /// <summary> Մուծողի հասցե </summary>
    public string Address { get; set; }

    /// <summary> Մուծողի էլեկտրոնային հասցե </summary>
    public string EMail { get; set; }

    /// <summary> Հիմք </summary>
    public string Base { get; set; }

    /// <summary> Մուծողի ծննդյան ամսաթիվ </summary>
    public DateTime? DateOfBirth { get; set; }

    /// <summary> Մուծողի ծննդավայր </summary>
    public string BirthPlace { get; set; }

    /// <summary> Պետ. գրանցման վկայականի համար </summary>
    public string RegCert { get; set; }

    /// <summary> Հանձնարարականի կոդ (23E) </summary>
    public string PaymentCode { get; set; }

    /// <summary> Հաշվետվողականության կոդ (77B) </summary>
    public string ReportCode { get; set; }

    /// <summary> Հաշվետվողականություն </summary>
    public string Report { get; set; }

    /// <summary> Հաղորդագրություն 1 կոդ </summary>
    public string MessageCode1 { get; set; }

    /// <summary> Հաղորդագրություն 1 </summary>
    public string Message1 { get; set; }

    /// <summary> Հաղորդագրություն 2 կոդ </summary>
    public string MessageCode2 { get; set; }

    /// <summary> Հաղորդագրություն 2 </summary>
    public string Message2 { get; set; }

    /// <summary> Հաղորդագրություն 3 կոդ </summary>
    public string MessageCode3 { get; set; }

    /// <summary> Հաղորդագրություն 3 </summary>
    public string Message3 { get; set; }

    /// <summary> Հաղորդագրություն 4 կոդ </summary>
    public string MessageCode4 { get; set; }

    /// <summary> Հաղորդագրություն 4 </summary>
    public string Message4 { get; set; }

    /// <summary> Հաղորդագրություն 5 կոդ </summary>
    public string MessageCode5 { get; set; }

    /// <summary> Հաղորդագրություն 5 </summary>
    public string Message5 { get; set; }

    /// <summary> Հաղորդագրություն 6 կոդ </summary>
    public string MessageCode6 { get; set; }

    /// <summary> Հաղորդագրություն 6 </summary>
    public string Message6 { get; set; }

    /// <summary> Պարտապանի ռեզիդենտություն </summary>
    public string DebtorResidence { get; set; }

    /// <summary> Պարտապանի իրավաբանական կարգավիճակ </summary>
    public string DebtorLegalState { get; set; }

    /// <summary> Պարտապանի ՀՎՀՀ </summary>
    public string DebtorTaxCode { get; set; }

    /// <summary> Պարտապանի սոցիալական քարդ </summary>
    public string DebtorSocialCard { get; set; }

    /// <summary> Պարտապանի անվանում </summary>
    public string Debtor { get; set; }

    /// <summary> Պարտապանի անձը հաստատող փաստաթղթի տիպ </summary>
    public string DebtorPassType { get; set; }

    /// <summary> Պարտապանի անձը հաստատող փաստաթուղթ </summary>
    public string DebtorPassNum { get; set; }

    /// <summary> Պարտապանի հասցե </summary>
    public string DebtorAddress { get; set; }

    /// <summary> Պարտապանի լիազորված անձ </summary>
    public string DebtorAuthorizedPerson { get; set; }

    /// <summary> Պարտապանի լրացուցիչ ինֆորմացիա </summary>
    public string DebtorAdditionalInfo { get; set; }

    /// <summary> Պարտապանի Էլ. փողերի հաշիվ </summary>
    public string DebtorElectronicAccount { get; set; }

    /// <summary> Վճարողի լիազորված անձ </summary>
    public string PayerAuthorizedPerson { get; set; }

    /// <summary> Լրացուցիչ ինֆորմացիա </summary>
    public string SenderAdditionalInfo { get; set; }

    /// <summary> Ստացողի հասցե </summary>
    public string RAddress { get; set; }

    /// <summary> Ստացողի լիազորված անձ </summary>
    public string ReceiverAuthorizedPerson { get; set; }

    /// <summary> Լրացուցիչ ինֆորմացիա </summary>
    public string ReceiverAdditionalInfo { get; set; }

    /// <summary> Ունիկալ համար </summary>
    public string OuterID { get; set; }

    /// <summary> Ընդունող վճարային համակարգ </summary>
    public string PaySystemIn { get; set; }

    /// <summary> Կատարել սև ցուցակի ստուգում </summary>
    public bool CheckBlackList { get; set; } = true;

    /// <summary> Ստուգել դեբետ հաշվի հաշվետիրոջ գումարների արգելադրումից պարտքի առկայությունը </summary>
    public bool CheckDebtsByAmountBlock { get; set; } = true;

    /// <summary> Կատարել գերածախսի հաշվին </summary>
    public bool UseOverlimit { get; set; } = false;

    /// <summary> Կատարել պարտքերի ստուգում </summary>
    public bool CheckPastDueDebts { get; set; } = true;

    /// <summary>
    /// true - արժեքի դեպքում առաջանում է սխալ միայն այն դեպքում,
    /// երբ մնացորդը չի բավարարում փոխանցվող գումարին և պարտքին։
    /// Կիրառելի է միայն <see cref="CheckPastDueDebts"/>-ի true արժեքի դեպքում
    /// </summary>
    public bool PastDueDebtsSoftCheck { get; set; } = true;
}
```
