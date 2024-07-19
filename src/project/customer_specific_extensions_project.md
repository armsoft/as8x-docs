---
layout: page
title: "Կազմակերպության սեփական ընդլայնումները պարունակող պրոյեկտի ստեղծում"
---

Ընդլայնումներ մշակելը հեշտացնելու համար C#-ի ֆայլերը կարելի է հավաքել մեկ պրոյեկտի մեջ։ Պրոյեկտը պետք է ունենա հետևյալ կառուցվածքը
* Ստեղծել Class Library տիպի պրոյեկտ։ Ստեղծման եղանակին ծանոթանալու համար [տե'ս](https://learn.microsoft.com/en-us/dotnet/core/tutorials/library-with-visual-studio?pivots=dotnet-8-0#create-a-class-library-project):
* Պրոյեկտում հարկավոր է անջատել հետևյալ հատկությունները
  * Implicit global usings
    (.csproj ֆայլում  `<ImplicitUsings>disable</ImplicitUsings>`)
  * Nullable
    (.csproj ֆայլում  `<Nullable>disable</Nullable>`)
* Պրոյեկտին ավելացնել աշխատանքի համար անհրաժեշտ dll-ները։


## Պարտադիր dll-ներ

* ArmSoft.AS8X.Common.dll
* ArmSoft.AS8X.Core.dll
* Armsoft.PrintTemplates2.dll

## Ստորև dll-ները պարդիր չեն, բայց հիմնականում օգտագործվում են

* Armsoft.PrintTemplates2.dll
* Ardalis.SmartEnum.dll
* Microsoft.Data.SqlClient.dll

## Յուրահատուկ ՀԾ-Բանկի ընդլայնումների համար

* ArmSoft.AS8X.Bank.dll

## Յուրահատուկ ՀԾ-Ձեռնարկության ընդլայնումների համար

* ArmSoft.AS8X.Enterprise.dll

## Յուրահատուկ ՀԾ-Աշխատավարձի ընդլայնումների համար

* ArmSoft.AS8X.Wages.dll

## csproj-ի օրինակ

``` xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>net8.0</TargetFramework>
    <ImplicitUsings>disable</ImplicitUsings>
    <Nullable>disable</Nullable>
  </PropertyGroup>

  <ItemGroup>
    <Reference Include="ArmSoft.AS8X.Bank">
      <HintPath>..\ServiceLocation\ArmSoft.AS8X.Bank.dll</HintPath>
    </Reference>
    <Reference Include="ArmSoft.AS8X.Common">
      <HintPath>..\ServiceLocation\ArmSoft.AS8X.Common.dll</HintPath>
    </Reference>
    <Reference Include="ArmSoft.AS8X.Core">
      <HintPath>..\ServiceLocation\ArmSoft.AS8X.Core.dll</HintPath>
    </Reference>
    <Reference Include="Armsoft.PrintTemplates2">
      <HintPath>..\ServiceLocation\Armsoft.PrintTemplates2.dll</HintPath>
    </Reference>
    <Reference Include="System.Data.SqlClient">
      <HintPath>..\ServiceLocation\Microsoft.Data.SqlClient.dll</HintPath>
    </Reference>
    <Reference Include="System.Data.SqlClient">
      <HintPath>..\ServiceLocation\Ardalis.SmartEnum.dll</HintPath>
    </Reference>
  </ItemGroup>

</Project>
```
