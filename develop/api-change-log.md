---
title: REST API-wijzigingenlogboek voor Partnercentrum
description: Deze pagina bevat wijzigingen in de REST Api's van het Partner Center
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.topic: reference
ms.date: 12/15/2020
ms.openlocfilehash: b2c2cac36a8bd1bec7aa5bf6e5d1aa73b4779535
ms.sourcegitcommit: 717e483a6eec23607b4e31ddfaa3e2691f3043e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104711845"
---
# <a name="december-2020-changes-to-partner-center-rest-apis"></a>Wijzigingen van 2020 december voor het Partner Center REST-Api's

Schakel dit selectie vakje in als u de REST-Api's van het partner centrum wilt wijzigen.

## <a name="enhancements-to-education-pricing-eligibility-apis"></a>Verbeteringen van de geschiktheids-Api's voor onderwijs prijzen



### <a name="what-has-changed"></a>Wat is er gewijzigd?

Op dit moment heeft de partner centrum-API de mogelijkheid om de geschiktheid van het onderwijs klanten te verifiëren. Er worden geen wijzigingen aangebracht in de kwalificatie-API ophalen. We hebben echter een retour Case toegevoegd aan de PUT-kwalificatie-API.

- GET-wordt niet gewijzigd. [Huidige API-artikel](./get-customer-qualification-synchronous.md)
- Er wordt een case met de waarde PUT toegevoegd. [Huidige API-artikel](./update-customer-qualification-synchronous.md)

Deze Api's worden aan het einde van februari 2021 verwijderd en vervangen door nieuwe Api's, zoals hieronder wordt beschreven.

### <a name="scenarios-impacted"></a>Getroffen scenario's:

Klant geschiktheid voor onderwijs prijzen voor Select Sku's

### <a name="detail-descriptions"></a>Gedetailleerde beschrijvingen

Er worden twee nieuwe GET-en POST-kwalificaties-Api's geïntroduceerd. De nieuwe Api's maken gebruik van **kwalificaties**, geen **Kwalificatie**. De Api's zijn beschikbaar voor testen in FY21 Q2.

#### <a name="get-qualifications"></a>Kwalificaties ophalen

```http
GET {customer_id}/qualifications
```

#### <a name="response-example"></a>Voorbeeldantwoord:

```json
{
  "Qualification": "Education",
  "VettingStatus": "Denied",
  "VettingReason": "Not an education customer",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

#### <a name="response-fields"></a>Antwoord velden: 

- VettingStatus waarden: goedgekeurd, geweigerd, inbeoordeling enz.

- VettingReason waarden:
   - Geen onderwijs klant
   - Geen onderwijs gebruiker meer
   - Geen onderwijs klant-na beoordeling
   - Alleen een onderwijs gebruiker
   - Geen academisch domein
   - Geen beschik bare bibliotheek
   - Geen in aanmerking komend Museum
 
#### <a name="post-qualifications"></a>BERICHT kwalificaties

```http
POST {customer_id}/qualifications
    [
            "Qualification": "Education"
    ]
```

#### <a name="response-example"></a>Voorbeeldantwoord:

```JSON
{
  "Qualification": "Education",
  "VettingStatus": "InReview",
  "VettingCreatedDate": "07/09/2020: 00:00:00" //UTC
}
```

## <a name="next-steps"></a>Volgende stappen

[REST API-verwijzing voor Partnercentrum](partner-center-rest-api-reference.md)