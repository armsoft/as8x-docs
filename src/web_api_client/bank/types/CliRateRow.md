---
layout: page
title: "CliRateRow դաս" 
---

Հաճախորդի Դիլինգային փոխարժեքի առաջարկման եղանակ (CLIRATES) աղյուսակի տողի տվյալները։ Նախատեսված է հաճախորդի ստեղծման/խմբագրման և տվյալների ստացման համար։

```c#
public class CliRateRow
{
    /// <summary> Արժ.դբ. </summary>
    public string CurDb { get; set; }

    /// <summary> Արժ.կր. </summary>
    public string CurCr { get; set; }

    /// <summary> Կանխիկ/ Անկանխիկ </summary>
    public string CashOrNo { get; set; }

    /// <summary> Ընդ. վճ. համակարգ </summary>
    public string PaySysIn { get; set; }

    /// <summary> Փոխարժեքի տեսակ </summary>
    public string RateType { get; set; }

    /// <summary> Փոխարժեքի շեղում (%) </summary>
    public decimal RateDev { get; set; }

    /// <summary> Փոխ.շեղում (ֆիքս.գում.) </summary>
    public decimal RateDevFix { get; set; }
}
```
