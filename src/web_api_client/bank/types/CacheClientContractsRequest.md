---
layout: page
title: "CacheClientContractsRequest դաս" 
---

Այս դասը նախատեսված է hաճախորդի պայմանագրերի քեշավորման համար։

Օգտագործվում է [AgrProfilesRoutes](../routes/AgrProfilesRoutes.md).[CacheClientContracts](../routes/AgrProfilesRoutes.md#cacheclientcontracts) մեթոդում։

```c#
public class CacheClientContractsRequest
{
/// <summary>Հաճախորդի կոդ</summary>
public string CliCode { get; set; }

/// <summary>Քեշավորման ամսաթիվ</summary>
public DateTime Date { get; set; }

/// <summary>Ենթահամակարգերի ցուցակ</summary>
public List<string> Subsystems { get; set; }
}
```
