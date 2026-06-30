---
layout: page
title: "InterestRate դաս" 
---

Տոկոսադրույք/Բաժանարար։

```c#
public class InterestRate
{
    /// <summary> Տոկոսադրույք </summary>
    public decimal Rate { get; set; }

    /// <summary> Բաժանարար </summary>
    public Divisor Divisor { get; set; }
}

/// <summary> Բաժանարար </summary>
public enum Divisor
{
    /// <summary> Օրական </summary>
    Daily = 1,
    /// <summary> Շաբաթական </summary>
    Weekly = 7,
    /// <summary> Ամսական (28օր) </summary>
    Monthly_28 = 28,
    /// <summary> Ամսական (29օր) </summary>
    Monthly_29 = 29,
    /// <summary> Ամսական (30օր) </summary>
    Monthly_30 = 30,
    /// <summary> Ամսական (31օր) </summary>
    Monthly_31 = 31,
    /// <summary> Տարեկան (360օր)</summary>
    Yearly_360 = 360,
    /// <summary> Տարեկան (365օր)</summary>
    Yearly_365 = 365,
    /// <summary> Տարեկան (366օր)</summary>
    Yearly_366 = 366,
    /// <summary> Տարեկան (365-366օր)</summary>
    Yearly_367 = 367
}
```
