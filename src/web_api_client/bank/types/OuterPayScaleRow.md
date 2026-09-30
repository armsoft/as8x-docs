---
layout: page
title: "OuterPayScaleRow դաս" 
---

Արտաքին փոխանց.գանձ.տեսակ (OPAYCOMT) աղյուսակի տողի տվյալները։ Նախատեսված է հաճախորդի ստեղծման/խմբագրման և տվյալների ստացման համար։

```c#
public class OuterPayScaleRow
{
    /// <summary> Ընդ. վճ. համակարգ </summary>
    public string PaySysIn { get; set; }

    /// <summary> Ուղ. վճ. համակարգ </summary>
    public string PaySysOut { get; set; }

    /// <summary> Երկիր </summary>
    public string Country { get; set; }

    /// <summary> Ծախսերի մանրամասնություն </summary>
    public string ExpType { get; set; }

    /// <summary> Արժ. </summary>
    public string Cur { get; set; }

    /// <summary> Նշում(վճարում) </summary>
    public string PayNote { get; set; }

    /// <summary> Գանձ.տես. </summary>
    public string Tuning { get; set; }
}
```
