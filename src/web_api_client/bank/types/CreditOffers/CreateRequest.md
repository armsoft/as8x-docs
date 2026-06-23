---
layout: page
title: "CreditOffer.CreateRequest դաս"
sublinks:
- { title: "Date", ref: date }
- { title: "CliCode", ref: clicode }
- { title: "Name", ref: name }
- { title: "NameEng", ref: nameeng }
- { title: "AppType", ref: apptype }
- { title: "Shablon", ref: shablon }
- { title: "Amount", ref: amount }
- { title: "InterestRate", ref: interestrate }
- { title: "Duration", ref: duration }
- { title: "EndDate", ref: enddate }
- { title: "AccountNumber", ref: accountnumber }
---

## Բովանդակություն

Վարկային առաջարկի ստեղծման հարցման տվյալներ։ Օգտագործվում է [CreditOffersRoutes.Create](../routes/CreditOffersRoutes.md#create) մեթոդում։

## Հատկություններ

### Date

```csharp
public DateTime Date { get; set; }
```

Ամսաթիվ։

---

### CliCode

```csharp
public string CliCode { get; set; }
```

Հաճախորդի կոդ։

---

### Name

```csharp
public string Name { get; set; }
```

Անվանում։

---

### NameEng

```csharp
public string NameEng { get; set; }
```

Անգլերեն անվանում։

---

### AppType

```csharp
public string AppType { get; set; }
```

Հայտատեսակ։

---

### Shablon

```csharp
public string Shablon { get; set; }
```

Ձևանմուշի N։

---

### Amount

```csharp
public decimal Amount { get; set; }
```

Սահմանաչափ։

---

### InterestRate

```csharp
public InterestRate InterestRate { get; set; }
```

Տոկոսադրույք։ Տե՛ս [InterestRate](InterestRate.md) դասը։

---

### Duration

```csharp
public Periodicity Duration { get; set; }
```

Տևողություն։ Տե՛ս [Periodicity](Periodicity.md) դասը։

---

### EndDate

```csharp
public DateTime EndDate { get; set; }
```

Առաջարկի վերջնաժամկետ։

---

### AccountNumber

```csharp
public string AccountNumber { get; set; }
```

Հաշվարկային հաշիվ։
