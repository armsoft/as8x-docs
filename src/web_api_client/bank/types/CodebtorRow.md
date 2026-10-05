---
layout: page
title: "CodebtorRow դաս" 
---

Պայմանագրի համավարկառուի տվյալներ։

Օգտագործվում է [Loans.CreateRequest](../types/Loans/CreateRequest.md) դասում։

```c#
public class CodebtorRow
{
    /// <summary> Հաճախորդի կոդ </summary>
    public string CliCode { get; set; }

    /// <summary> Մասնաբաժին </summary>
    public decimal Proportion { get; set; }

    /// <summary> ՊԵԿ ուղարկվող </summary>
    public bool SRCSend { get; set; }
}
```
