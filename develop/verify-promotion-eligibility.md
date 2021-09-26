---
title: Geschiktheid voor een promotie controleren
description: Controleert of een klanttransactie in aanmerking komt voor een bepaalde promotie.
ms.date: 02/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: ad3346ddca0438c0011e2c6fd03c3ec00b1a1fe3
ms.sourcegitcommit: 7be22de808a10fa2d05577d6497086c8ca3f678a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/24/2021
ms.locfileid: "128715982"
---
# <a name="verify-promotion-eligibility"></a>Geschiktheid voor promotie controleren

**Van toepassing op**

- Partnercentrum

**Juiste rollen**

- Globale beheerder
- Beheeragent

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de Microsoft 365 en Dynamics 365 New Commerce Experience Technical Preview.

Parters kunnen controleren of een klanttransactie in aanmerking komt voor een bepaalde promotie. Deze methode retourneert *Waar* als de klanttransactie in aanmerking komt voor een bepaalde promotie. Partners kunnen controleren of ze in aanmerking komen voordat ze een transactie indienen om ervoor te zorgen dat de promotie wordt toegepast.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Geschiktheid omvat de product-SKU-beschikbaarheid die wordt aangeschaft, de promotie-id die wordt geëvalueerd, de hoeveelheid, de duur van de periode en de factureringscyclus van de transactie.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **VERZENDEN**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customerId}/promotionEligibilities HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameters om beschikbare promoties te retourneren.

| Naam                    | Type     | Vereist | Beschrijving                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **Klantid**  | **tekenreeks** | J        | De waarde is een klant-tenant-id in GUID-indeling. Dit is een id waarmee u een klant kunt opgeven.          |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST Partner Center headers [voor meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

De body bevat een verzameling PromotionEligibilitiesRequestItems. In deze tabel worden de eigenschappen voor [een PromotionEligibilitiesRequestItem beschreven.](promotion-resources.md#promotioneligibilitiesrequestitem)

| Eigenschap        | Type             | Vereist        | Beschrijving                                                                                               |
|-----------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| catalogItemId   | tekenreeks           | Ja             | De id van het catalogusitem.                         |
| quantity        | int | Ja        | Het aantal licenties of exemplaren.                 |
| termDuration    | DateTime         | Ja             | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn P1M (één maand), P1Y (één jaar) en P3Y (drie jaar).   |
| billingCycle    | tekenreeks | Ja     | De waarde die het type factureringscyclus aangeeft.   |
| promotionId     | tekenreeks           | Ja             | De id van het promotie-item.                       | 

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/customers/46632f71-f052-4384-8f84-4cdb6c12c2a1/promotionEligibilities HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US

{
    "items": [
        {
            "catalogItemId": "CFQ7TTC0KZ59:0001:CFQ7TTC0KZ59",
            "quantity": 1,
            "termDuration": "P1Y",
            "billingCycle": "Monthly",
            "promotionId": " CFQ7TTC0HL8W:0001:CFQ7TTC0K59M"
        }
    ]
}

```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een verzameling geschiktheidsresultaten.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en meer foutopsporingsinformatie. Gebruik een hulpprogramma voor netwerk traceer om deze code, fouttype en meer parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
    "totalCount": 1,
    "items": [
        {
            "catalogItemId": "CFQ7TTC0KZ59:0001:CFQ7TTC0KZ59",
            "quantity": 1,
            "termDuration": "P1Y",
            "billingCycle": "Monthly",
            "eligibilities": [
                {
                    "promotionId": "CFQ9TTC0HH4R:0001:CFQ8HGC0K77G",
                    "isEligible": false,
                    "errors": [
                        {
                            "type": "SeatCount",
                            "minRequiredSeats": 25,
                            "maxRequiredSeats": 500
                        },
                        {
                            "type": "Term",
                            "eligibleTerms": [
                                {
                                    "duration": "P3Y",
                                    "billingCycle": "Monthly"
                                }
                            ]
                        },
                        {
                            "type": "FirstPurchase"
                        }
                    ]
                }
            ],
            "attributes": {
                "objectType": "PromotionEligibilities"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```

