---
layout: page
title: "PassData դաս" 
---

Անձնագրի տվյալների դաս։ Նախատեսված է հաճախորդի ստեղծման/խմբագրման համար։

```c#
public class PassData
{
    /// <summary> Տիպ </summary>
    public string PassType { get; set; }

    /// <summary> Անձ. հաստ. փաստ. կոդ </summary>
    public string PassCode { get; set; }

    /// <summary> Տրված </summary>
    public string PassBy { get; set; }

    /// <summary> Ամսաթիվ </summary>
    public DateTime? DatePass { get; set; }

    /// <summary> Վավեր է մինչև </summary>
    public DateTime? DateExpire { get; set; }

    /// <summary> Ում կողմից է տրված </summary>
    public string ForeignPassBy { get; set; }
}
```
