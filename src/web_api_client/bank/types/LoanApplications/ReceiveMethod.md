---
layout: page
title: "ReceiveMethod enum" 
---

Գումարի ստացման եղանակ։ Enum-ը նախատեսված է հայտի ստեղծման համար։

```c#
/// <summary> Գումարի ստացման եղանակ </summary>
public enum ReceiveMethod
{
    /// <summary> Առձեռն ստանալ մասնաճյուղում  </summary>    
    Cash = 1,

    /// <summary> Ստանալ քարտով </summary>    
    WithCard = 2,

    /// <summary> Ստանալ հաշվով  </summary>    
    WithAccount = 3
}
```
