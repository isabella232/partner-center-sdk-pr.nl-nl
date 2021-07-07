---
title: De status van de productupgrade voor een klant op te halen
description: U kunt de productUpgradeRequest-resource gebruiken om de status van een productupgrade voor een klant naar een nieuwe productfamilie te bepalen, zoals van een Microsoft Azure-abonnement (MS-AZR-0145P) naar een Azure-abonnement.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 03d925dd0fae987226ad1f8e71fad380ba144b83
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445558"
---
# <a name="get-the-product-upgrade-status-for-a-customer"></a>De status van de productupgrade voor een klant op te halen

U kunt de [**resource ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) gebruiken om de status van een upgrade naar een nieuwe productfamilie op te halen. Deze resource is van toepassing wanneer u een klant upgradet van een Microsoft Azure-abonnement (MS-AZR-0145P) naar een Azure-abonnement. Een geslaagde aanvraag retourneert [**de resource ProductUpgradesEligibility.**](product-upgrade-resources.md#productupgradeseligibility)

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met app- en gebruikersreferenties. Volg het [model voor beveiligde apps bij](enable-secure-app-model.md) het gebruik van App+User-verificatie met Partner Center API's.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- De productfamilie.

- De upgrade-id van een upgradeaanvraag.

## <a name="c"></a>C\#

Ga als volgende te werk om te controleren of een klant in aanmerking komt voor een upgrade naar een Azure-plan:

1. Maak een **ProductUpgradesRequest-object** en geef de klant-id en 'Azure' op als de productfamilie.

2. Gebruik de **verzameling IAggregatePartner.ProductUpgrades.**

3. Roep de **ById-methode** aan en geef **de upgrade-id door.**

4. Roep de **methode CheckStatus** aan en geef het **productUpgradesRequest-object** door. Dit retourneert een **ProductUpgradeStatus-object.**

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

ProductUpgradesStatus productUpgradeStatus = partnerOperations.ProductUpgrades.ById(selectedUpgradeId).CheckStatus(productUpgradeRequest);

if (productUpgradeEligibility.IsEligibile)
{
    ....
}

```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI |
|----------|-----------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/{upgrade-id}/status HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de klant op te geven voor wie u de status van een productupgrade krijgt.

| Naam               | Type | Vereist | Beschrijving                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| **upgrade-id** | GUID | Ja | De waarde is een upgrade-id met GUID-indeling. U kunt deze id gebruiken om een bij te houden upgrade op te geven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

De aanvraag body moet een [**ProductUpgradeRequest-resource**](product-upgrade-resources.md#productupgraderequest) bevatten.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades/42d075a4-bfe7-43e7-af6d-7c68a57edcb4/status  HTTP/1.1
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
 {
    "customerId": "4c721420-72ad-4708-a0a7-371a2f7b0969",
    "productFamily": "azure"
  }
  "Attributes": {
  "ObjectType": "ProductUpgradeRequest"
  }
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
    "id": "42d075a4-bfe7-43e7-af6d-7c68a57edcb4",
    "status": "Completed",
    "productFamily": "Azure",
    "lineItems": [
        {
            "sourceProduct": {
                "id": "b1beb621-3cad-4d7a-b360-62db33ce028e",
                "name": "AzureSubscription"
            },
            "targetProduct": {
                "id": "d231908e-31c1-de0e-027b-bc5ce11f09d9",
                "name": "Microsoft Azure plan"
            },
            "upgradedDate": "2019-08-29T23:47:28.8524555Z",
            "status": "Completed"
        }
    ]
}

```
