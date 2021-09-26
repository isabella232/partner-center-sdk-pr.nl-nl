---
title: Haalt een lijst met huidige promoties op voor een segment en markt voor geven
description: Haalt een lijst met huidige promoties op voor een segment en markt voor geven.
ms.date: 09/24/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 0b9cc6ccdebbd641ab8b7dcd6cc5932c191d85ad
ms.sourcegitcommit: 7be22de808a10fa2d05577d6497086c8ca3f678a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/24/2021
ms.locfileid: "128715981"
---
# <a name="get-promotions"></a>Promoties krijgen

**Van toepassing op**

- Partnercentrum

**Juiste rollen**

- Globale beheerder
- Beheeragent

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de Microsoft 365 en Dynamics 365 New Commerce Experience Technical Preview.

Partners kunnen een lijst met actieve nieuwe commerciële promoties voor een bepaalde markt (land) en segment krijgen. Deze methode retourneert beschikbare huidige promoties op basis van de beschikbare begin- en einddatums van de promoties.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Segment vertegenwoordigt het type klant voor welke promoties zijn ingeschakeld. Ondersteunt momenteel alleen commercieel.

- Land vertegenwoordigt het land van de klant waar promoties voor beschikbaar zijn. Land wordt vertegenwoordigd door een landcode van twee tekens.

## <a name="rest-request"></a>REST-aanvraag
[GET] /v1/productpromotions?country={country-code}&segment={segment}

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **TOEVOEGEN**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/productpromotions?country={country-code}&segment={segment} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameters om beschikbare promoties te retourneren.

| Naam                    | Type     | Vereist | Beschrijving                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **Segment**  | **tekenreeks** | J        | Een tekenreeks die bepaalt welke promoties beschikbaar zijn voor een bepaald segment.           |
| **Land** | **tekenreeks** | J        | Een landcode van twee letters die bepaalt voor welke klant landpromoties beschikbaar zijn. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/productpromotions?country=US&segment=commercial HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een lijst met promoties.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en meer foutopsporingsinformatie. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en meer parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT


{
    "totalCount": 2,
    "items": [
        {
            "id": "39NFJQT1PJQB:0001:39NFJQT1Q5KN",
            "name": "Visio Plan 1",
            "description": "Visio Plan 1",
            "startDate": "2021-09-23T00:00:00+00:00",
            "endDate": "2021-10-14T23:59:59+00:00",
            "properties": {
                "isAutoApplicable": true
            },
            "requiredProducts": [
                {
                    "productId": "CFQ7TTC0HD33",
                    "skuId": "0003",
                    "term": {
                        "duration": "P1Y",
                        "billingCycle": "Annual"
                    },
                    "pricingPolicies": [
                        {
                            "policyType": "PercentDiscount",
                            "value": "0.05"
                        }
                    ]
                }
            ]
        },
        {
            "id": "39NFJQT1PJQC:0001:39NFJQT1Q5KM",
            "name": "Vision Plan 1",
            "description": "Vision Plan 1",
            "startDate": "2021-09-23T00:00:00+00:00",
            "endDate": "2021-10-14T23:59:59+00:00",
            "properties": {
                "isAutoApplicable": true
            },
            "requiredProducts": [
                {
                    "productId": "CFQ7TTC0HD33",
                    "skuId": "0003",
                    "term": {
                        "duration": "P1Y",
                        "billingCycle": "Monthly"
                    },
                    "pricingPolicies": [
                        {
                            "policyType": "PercentDiscount",
                            "value": "0.167"
                        }
                    ]
                }
            ]
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
