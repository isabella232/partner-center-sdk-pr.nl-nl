---
title: Een gebruiksoverzicht voor een partner krijgen
description: U kunt de resource PartnerUsageSummary gebruiken om een samenvatting van het gebruik van partners te krijgen van alle klanten die een specifieke Azure-service of -resource hebben aangeschaft tijdens de huidige factureringsperiode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: f003980f1b521ad0ac26dbfd0d4821b9096fdd27
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873901"
---
# <a name="get-a-usage-summary-for-a-partner"></a>Een gebruiksoverzicht voor een partner krijgen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

U kunt de resource **PartnerUsageSummary** gebruiken om een samenvatting van het gebruik van partners te krijgen van alle klanten die een specifieke Azure-service of -resource hebben aangeschaft tijdens de huidige factureringsperiode.

*Het totaal dat door deze API wordt geretourneerd, retourneerd geen verbruik voor klanten die een Azure-plan hebben.* Gepland voor afschaffing in de toekomst.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

## <a name="c"></a>C\#

Ga als volgt te werk om een gebruiksoverzicht te krijgen voor alle klanten die een specifieke Azure-service of -resource hebben aangeschaft tijdens de huidige factureringsperiode:

1. Gebruik uw **IAggregatePartner.**

2. Roep de **eigenschap UsageSummary** aan, gevolgd door de **methoden Get()** of **GetAsync()** :

    ``` csharp
    // IAggregatePartner partnerOperations;

    var usageSummary = partnerOperations.UsageSummary.Get();
    ```

Zie voor een voorbeeld het volgende:

- Voorbeeld: [Consoletest-app](console-test-app.md)
- Project: **PartnerSDK.FeatureSamples**
- Klasse: **GetPartnerUsageSummary.cs**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                         |
|---------|---------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/usagesummary HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een **PartnerUsageSummary-resource** in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor een [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "customersOverBudget": 1,
    "customersTrendingOver": 0,
    "customersWithUsageBasedSubscription": 11,
    "resourceId": "11111111-4574-4539-bc42-0e539b9684c0",
    "id": "11111111-4574-4539-bc42-0e539b9684c0",
    "resourceName": "PLAMUATT2NETNEW",
    "name": "PLAMUATT2NETNEW",
    "billingStartDate": "2019-08-28T00:00:00-07:00",
    "billingEndDate": "2019-09-27T00:00:00-07:00",
    "totalCost": 22.861172,
    "currencyLocale": "fr-FR",
    "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
    "links": {
        "self": {
            "uri": "/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "PartnerUsageSummary"
    }
}
```
