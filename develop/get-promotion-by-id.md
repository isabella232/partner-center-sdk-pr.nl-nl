---
title: Krijgt één promotie
description: Krijgt één promotie voor een bepaalde promotie-id en een bepaald land.
ms.date: 09/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 9ed9171cd7bbe8a6d5202deb7cc6111bb76ec923
ms.sourcegitcommit: 7be22de808a10fa2d05577d6497086c8ca3f678a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/24/2021
ms.locfileid: "128715984"
---
# <a name="get-promotion-by-id"></a>Promotie op id krijgen

**Van toepassing op**

- Partnercentrum

**Juiste rollen**

- Globale beheerder
- Beheeragent

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de Microsoft 365 en Dynamics 365 New Commerce Experience Technical Preview.

Partners kunnen één promotie krijgen voor een bepaalde promotie-id en een bepaald land. Deze methode retourneert de promotiegegevens, waarbij de begin- en einddatum van de promotie worden genegeerd. Deze methode wordt voornamelijk gebruikt voor afstemmingsdoeleinden om promotiegegevens op te halen, zelfs nadat de promotie is verlopen.



## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Promotie-id is een reeks tekenreeksen met scheidingstekens die een specifieke promotie vertegenwoordigen.

- Land vertegenwoordigt het land van de klant waar promoties voor beschikbaar zijn. Land wordt vertegenwoordigd door een landcode van twee tekens.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **TOEVOEGEN**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/productpromotions/{promotion-id}?country={country-code HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameters om beschikbare promoties te retourneren.

| Naam                    | Type     | Vereist | Beschrijving                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **promotion-id**  | **tekenreeks** | J        | Een tekenreeks die de promotie definieren die moet worden opgehaald.           |
| **Land** | **tekenreeks** | J        | Een landcode van twee letters die bepaalt voor welke klant landpromoties beschikbaar zijn. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/productpromotions/CFQ7TTC0HD33:0003:CFQ7TTC0K59M?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode één promotie.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en meer foutopsporingsinformatie. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 24 Sep 2021 20:42:26 GMT

 
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
        }
```
