---
title: Controleer of een klant in aanmerking komt voor een upgrade naar een Azure-plan
description: U kunt de ProductUpgradeRequest-resource gebruiken om een ProductUpgradesEligibility-resource te retourneren om te bepalen of een klant in aanmerking komt voor een upgrade van een Microsoft Azure-abonnement (MS-AZR-0145P) naar een Azure-plan.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: a72a9f2f3909ac4b3b74754b58a8d8d4745fbb2cadd101ad18cf487b1b02267a
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996017"
---
# <a name="check-a-customers-eligibility-for-upgrading-to-an-azure-plan"></a>Controleer of een klant in aanmerking komt voor een upgrade naar een Azure-plan

U kunt de [**ProductUpgradeRequest-resource**](product-upgrade-resources.md#productupgraderequest) gebruiken om te controleren of een klant in aanmerking komt voor een upgrade naar een Azure-plan vanuit een Microsoft Azure-abonnement (MS-AZR-0145P) Deze methode retourneert een [**ProductUpgradesEligibility-resource**](product-upgrade-resources.md#productupgradeseligibility) met de geschiktheid voor productupgradeseligibility van de klant.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met app- en gebruikersreferenties. Volg het [model voor beveiligde apps](enable-secure-app-model.md) bij het gebruik van App+User-verificatie met Partner Center API's.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- De productfamilie.

## <a name="c"></a>C\#

Ga als volgende te werk om te controleren of een klant in aanmerking komt voor een upgrade naar een Azure-plan:

1. Maak een **ProductUpgradesRequest-object** en geef de klant-id en 'Azure' op als de productfamilie.

2. Gebruik de **verzameling IAggregatePartner.ProductUpgrades.**
3. Roep de **CheckEligibility-methode** aan en geef het **productUpgradesRequest-object** door, dat een **ProductUpgradesEligibility-object** retourneert.

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

ProductUpgradesEligibility productUpgradeEligibility = partnerOperations.ProductUpgrades.CheckEligibility(productUpgradeRequest);

if (productUpgradeEligibility.IsEligibile)
{
    ....
}

```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/eligibility HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

De aanvraag body moet een [**ProductUpgradeRequest-resource**](product-upgrade-resources.md#productupgraderequest) bevatten.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades/eligibility HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c245d5f2-1de3-4ae0-9e42-95e38e3cb8ff
MS-CorrelationId: e3f26e6a-044f-4371-ad52-0d91ce4200be
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 340
Expect: 100-continue
Connection: Keep-Alive
{
        "customerId": "4c721420-72ad-4708-a0a7-371a2f7b0969",
        "productFamily": "azure"
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een [**ProductUpgradesEligibility-resource**](product-upgrade-resources.md#productupgradeseligibility) in de body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 Ok
Content-Length: 150
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 04 Oct 2019 20:35:35 GMT

{
    "customerId": "c1958bc7-3284-4952-a257-de594ee64743",
    "isEligible": true,
    "productFamily": "azure"
}
```
