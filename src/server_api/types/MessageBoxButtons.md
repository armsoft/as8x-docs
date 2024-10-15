---
layout: page
title: "MessageBoxButtons" 
---

Այս enum-ը նախատեսված է հաղորդագրության պատուհանում (MessageBox) ավելացվող կոճակների սահմանման համար։

```c#
public enum MessageBoxButtons
{
    OK = 0,
    OKCancel = 1,
    YesNoCancel = 3,
    YesNo = 4
}
```

**Արժեքների բազմություն**

* `OK` - Ցուցադրվում է **Լավ** կոճակը։
* `OKCancel` - Ցուցադրվում են **Կատարել**, **Դադարեցնել** կոճակները։
* `YesNoCancel` - Ցուցադրվում են **Այո**, **Ոչ**, **Դադարեցնել** կոճակները։
* `YesNo` - Ցուցադրվում են **Այո**, **Ոչ** կոճակները։