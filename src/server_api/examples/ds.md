---
layout: page
title: "Տվյալների աղբյուրի օգտագործման օրինակներ" 
---

# Տվյալների աղբյուրի կատարման ձեռնարկ AS-8X համակարգում

## Ներածություն

AS-8X համակարգում տվյալների աղբյուրի կատարման երկու հիմնական մեթոդ կա՝ **չտիպիզացված** և **տիպիզացված**: Այս երկու մեթոդները տարբերվում են իրենց իրականացման, օգտագործման և վերադարձվող արդյունքի առումով:

## Հիմնական տարբերությունները

1. **Պարամետրերի փոխանցում**
   * Չտիպիզացված՝ օգտագործում է Dictionary<string, object>՝ պարամետրերի արժեքների պահման համար
   * Տիպիզացված՝ օգտագործում է պարամետրերը նկարագրող դասը
2. **Կատարման մեթոդ**
   * Չտիպիզացված՝ DataSourceService դասի ExecuteDataSource մեթոդը
   * Տիպիզացված՝ տվյալների աղբյուրը նկարագրող դասի Execute մեթոդը
3. **Վերադարձվող արդյունք**
   * Չտիպիզացված՝ List&lt;T&gt;՝ որպես T վերադարձնելով տվյալների աղբյուրի սյուները նկարագրող դասը
   * Տիպիզացված՝ DataSourceResult&lt;R&gt;` որպես R վերադարձնելով տվյալների աղբյուրի սյուները նկարագրող դասը
4. **Տիպի անվտանգություն**
   * Չտիպիզացված՝ ցածր, հնարավոր են runtime սխալներ
   * Տիպիզացված՝ բարձր, compile-time ստուգումներ են իրականացվում
5. **Լրացուցիչ մետատվյալներ**
   * Չտիպիզացված՝ չի տրամադրում
   * Տիպիզացված՝ տրամադրում է (տվյալների աղբյուրի [սխեմա](../definitions/schema.md), կատարման ընթացքում առաջացած սխալների մասին ինֆորմացիա և այլն)

Օրինակներում օգտագործված տվյալների աղբյուրի նկարագրող դասին ծանոթանալու համար [տես](ds/sql_based_code.cs)։

## 1. Չտիպիզացված կատարում

### Քայլեր՝

1. Ստեղծել Dictionary<string, object> տիպի օբյեկտ՝ փոխանցելով կատարման համար անհրաժեշտ պարամետրերը՝ որպես key գրելով պարամետրի անունը, իսկ որպես value` արժեքը:
2. Կանչել DataSourceService դասի ExecuteDataSource մեթոդը՝ փոխանցելով տվյալների աղբյուրի ներքին անվանումը և պարամետրերի ցանկը:

### Օրինակ՝

```csharp

// 1. Ստեղծել Dictionary և լրացնել պարամետրերը
var dsParams = new Dictionary<string, object>()
{
    {"TreeId", "PARGROUP" },
    {"NodeType", "Install" }
};

// 2. Կատարել տվյալների աղբյուրը
var dsResult = await this.dsService.ExecuteDataSource<TreeNode.DataRow>("TreeNode", dsParams);

// ցիկլով անցնել տողերի վրայով և տպել արժեքները
foreach(TreeNode.DataRow row in dsResult)
{
    Debug.WriteLine("Code - " + row.Code);
    Debug.WriteLine("Name - " + row.Name);
    Debug.WriteLine(string.Empty);
}

```
### Արդյունք՝
Վերադարձնում է List&lt;T&gt; տիպի օբյեկտ, որտեղ T-ն տվյալների աղբյուրի տողերը նկարագրող դասն է: Այս օրինակում T-ն հանդիսանում է TreeNode.DataRow-ն։

## 2. Տիպիզացված  կատարում

### Քայլեր՝

1. Ստանալ տվյալների աղբյուրի նկարագրող դասը DataSourceService դասի GetDataSource մեթոդով:
2. Ստեղծել տվյալների աղբյուրի պարամետրերը նկարագրող դասի օբյեկտ՝ փոխանցելով կատարման համար անհրաժեշտ պարամետրերը։
3. Կանչել տվյալների աղբյուրի դասի Execute մեթոդը՝ փոխանցելով պարամետրերը նկարագրող դասը:

### Օրինակ՝

```csharp

// 1. Ստանալ տվյալների աղբյուրը 
var dsTreeNode = this.dsService.GetDataSource<TreeNode>(); 

// 2. Ստեղծել և լրացնել պարամետրերի նկարագրող դասի օբյեկտը 
var dsParams = new TreeNode.Param { 
    TreeId = "PARGROUP", 
    NodeType = "Install"
}; 

// 3. Կատարել տվյալների աղբյուրը 
var dsResult = await dsTreeNode.Execute(dsParams);

// ցիկլով անցնել տողերի վրայով և տպել արժեքները
foreach(TreeNode.DataRow row in dsResult.Rows)
{
  Debug.WriteLine("Code - " + row.Code);
  Debug.WriteLine("Name - " + row.Name);
  Debug.WriteLine(string.Empty);
}

```
### Արդյունք՝
Վերադարձնում է DataSourceResult&lt;T&gt; տիպի օբյեկտ` որպես T վերադարձնելով տվյալների աղբյուրի տողերը նկարագրող դասը, որը պարունակում է տվյալների աղբյուրի տողերը և հավելյալ տեղեկատվություն տվյալների աղբյուրի մասին։
