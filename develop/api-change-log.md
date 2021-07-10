---
title: REST API-wijzigingenlogboek voor Partnercentrum
description: Deze pagina bevat wijzigingen in de Partner Center REST API's
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.topic: reference
ms.date: 12/15/2020
ms.openlocfilehash: d4f7f034a36a26b6219086ca952b189f7a313ef7
ms.sourcegitcommit: 51237e7e98d71a7e0590b4d6a4034b6409542126
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2021
ms.locfileid: "113571992"
---
# <a name="december-2020-changes-to-partner-center-rest-apis"></a>Wijzigingen van december 2020 in Partner Center REST API's

Kijk hier voor wijzigingen in Partner Center REST API's.

## <a name="enhancements-to-education-pricing-eligibility-apis"></a>Verbeteringen in de education pricing Eligibility API's



### <a name="what-has-changed"></a>Wat is er veranderd?

Momenteel heeft de Partner Center-API de kwalificaties GET en PUT om te controleren of Education-klanten in aanmerking komen. Er worden geen wijzigingen aangebracht in de GET Kwalificatie-API. We hebben echter een retourcase toegevoegd aan de PUT Kwalificatie-API.

- GET: verandert niet.
- PUT: retourcase wordt toegevoegd.

Deze API's worden eind februari 2021 uit gebruik genomen om te worden vervangen door nieuwe API's, zoals hieronder wordt beschreven.

### <a name="scenarios-impacted"></a>Scenario's die worden beïnvloed:

Klant in aanmerking komen voor onderwijsprijzen voor bepaalde SKU's

### <a name="detail-descriptions"></a>Beschrijvingen van details

Er worden twee nieuwe API's voor GET- en POST-kwalificaties geïntroduceerd. De nieuwe API's gebruiken **Kwalificaties,** niet **Kwalificatie.** De API's zijn beschikbaar voor testen in FY21 Q2.

#### <a name="get-qualifications"></a>GET Kwalificaties

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

#### <a name="response-fields"></a>Antwoordvelden: 

- Waarden voor VettingStatus: Approved, Denied, InReview, enzovoort.

- VettingReason-waarden:
   - Geen Education-klant
   - Geen Education-klant meer
   - Geen education-klant - na beoordeling
   - Beperkte toegang tot onderwijsklant
   - Geen academische domein
   - Geen in aanmerking komende bibliotheek
   - Geen in aanmerking komende Moet
 
#### <a name="post-qualifications"></a>POST-kwalificaties

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
