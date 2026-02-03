---
layout: page
title: "Օրինակ PrematureChargesRoutes" 
sublinks:
- { title: "Օրինակ PrematureRepaymentCharge", ref: օրինակ-1 }
---

## Բովանդակություն
- [PrematureRepaymentCharge-ի օգտագործման օրինակ](#օրինակ-1)

## Օրինակ 1
Վաղաժամկետ մարումից տույժի հաշվարկման օրինակ։

```c#
    private static async Task PrematureRepaymentCharge(BankApiClient apiClient)
    {
        try 
        { 
            var res = await apiClient.PrematureCharges.PrematureRepaymentCharge(new()
                {
                    AgrISN = 12345678, //Պայմանագրի ISN
                    PaymentDate = DateTime.Now, //Մարման ամսաթիվ
                    RepaidPrincipal = 1000000m //Մարվող մայր գումար
            });
            Console.WriteLine(res.Amount); //Վերադարձնում է վաղաժամկետ մարումից տույժը
        }
        catch (ApiException ex)
        {
            // մեթոդի կանչի ընթացքում սխալի առաջացման դեպքում տպում է սխալի մանրամասները
            Console.WriteLine(ex.Code); // սխալի կոդ
            Console.WriteLine(ex.Message); // սխալի հաղորդագրություն
            Console.WriteLine(ex.StatusCode); // սխալի վիճակի կոդ
        }
    }
```
