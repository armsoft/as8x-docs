---
layout: page
title: "Address դաս" 
---

Հասցեի տվյալներ։ Այս դասը նախատեսված է հաճախորդի ստեղծման/խմբագրման համար։

```c#
public class Address
{
    /// <summary> Երկիր </summary>
    public string Country { get; set; }

    /// <summary> Մարզ </summary>
    public string Community { get; set; }

    /// <summary> Ինդեք </summary>
    public string Index { get; set; }

    /// <summary> Քաղաք </summary>
    public string City { get; set; }

    /// <summary> Քաղաք անգլերեն </summary>
    public string CityEng { get; set; }

    /// <summary> Փողոց </summary>
    public string Street { get; set; }

    /// <summary> Փողոց անգլերեն </summary>
    public string StreetEng { get; set; }

    /// <summary> Տուն/Շենք </summary>
    public string BuildNum { get; set; }

    /// <summary> Տուն/Շենք անգլերեն </summary>
    public string BuildNumEng { get; set; }

    /// <summary> Բնակարան </summary>
    public string Apartment { get; set; }

    /// <summary> Բնակարան անգլերեն </summary>
    public string ApartmentEng { get; set; }
}
```
