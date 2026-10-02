---
layout: page
title: "AppForm դաս" 
---

Վարկային հայտ

```c#
/// <summary> Հայտի տվյալներ </summary>
public class AppForm
{
    /// <summary>Հայտի վիճակ</summary>
    public string State { get; set; }

    /// <summary>Հայտի համար</summary>
    public string Code { get; set; }

    /// <summary>Հայտի ամսաթիվ</summary>
    public DateTime Date { get; set; }

    /// <summary>Հաճախորդի կոդ</summary>
    public string CliCode { get; set; }

    /// <summary>Հայտատեսակ</summary>
    public string AppType { get; set; }

    /// <summary>Պայմանագրի տեսակ</summary>
    public string AgrKind { get; set; }

    /// <summary>Արժույթ</summary>
    public string Cur { get; set; }

    /// <summary>Համակարգ</summary>
    public string SystemType { get; set; }

    /// <summary>Ձևանմուշի համար</summary>
    public string Shablon { get; set; }
    
    /// <summary>Գումարի ստորին սահման</summary>
    public decimal MinSum { get; set; }
    
    /// <summary>Գումարի վերին սահման</summary>
    public decimal MaxSum { get; set; }
    
    /// <summary>Ամսական առավելագույն գումար</summary>
    public decimal MonthMaxSum { get; set; }
    
    /// <summary>Նվազագույն տևողություն</summary>
    public Periodicity MinDuration { get; set; }
    
    /// <summary>Առավելագույն տևողություն</summary>
    public Periodicity MaxDuration { get; set; }
    
    /// <summary>Մարման օրվա վերին սահման</summary>
    public short MaxFixedDay { get; set; }
    
    /// <summary>Տոկոսադրույք</summary>
    public InterestRate InterestRate { get; set; }
    
    /// <summary>Չօգտագործված մասի տոկոսադրույք</summary>
    public InterestRate UnusedPartsInterestRate { get; set; }
    
    /// <summary>Գումար</summary>
    public decimal Amount { get; set; }
    
    /// <summary>Մարման ընդհանուր գումար</summary>
    public decimal TotalPayAmount { get; set; }
    
    /// <summary>Փաստացի տոկոսադրույք</summary>
    public decimal ActualRate { get; set; }
    
    /// <summary>Տևողություն</summary>
    public Periodicity Duration { get; set; }
    
    /// <summary>Մարման օր</summary>
    public short FixedDay { get; set; }
    
    /// <summary>Գումարի ստացման եղանակ</summary>
    public string ReceiveMethod { get; set; }
    
    /// <summary>Հաշվարկային հաշիվ</summary>
    public string AccountNumber { get; set; }
    
    /// <summary>Շահառուի անվանում</summary>
    public string RespName { get; set; }
    
    /// <summary>Քարտի համար</summary>
    public string CardNumber { get; set; }
    
    /// <summary>Քարտի անվանում</summary>
    public string CardName { get; set; }
    
    /// <summary>Պայմանագրի ISN</summary>
    public int AgrIsn { get; set; }
    
    /// <summary>Անցում</summary>
    public string Transition { get; set; }
    
    /// <summary>Անցման անվանում</summary>
    public string TransitionName { get; set; }
    
    /// <summary>Պատասխանի տեսակ</summary>
    public string ResponseType { get; set; }
    
    /// <summary>Հայտի վիճակի տեսակ</summary>
    public string StateType { get; set; }
    
    /// <summary>Պայմանագիրը հաստատված է</summary>
    public bool AgrIsConf { get; set; }
    
    /// <summary>Գումարը տրամադրված է</summary>
    public bool SumIsGiven { get; set; }
    
    /// <summary>Գործընկերոջ կոդ</summary>
    public string Partner { get; set; }
    
    /// <summary>ԻԲ օգտագործող</summary>
    public string IBUser { get; set; }
}
```
