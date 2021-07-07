---
title: Een entiteit voor productupgrade maken voor een klant
description: U kunt de resource ProductUpgradeRequest gebruiken om een entiteit voor productupgrade te maken om een klant te upgraden naar een bepaalde productfamilie.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4e346b7f5294a8847047c85115d8c80f34eaca84
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973398"
---
# <a name="create-a-product-upgrade-entity-for-a-customer"></a>Een entiteit voor productupgrade maken voor een klant

U kunt een entiteit voor productupgrade maken om een klant te upgraden naar een bepaalde productfamilie (bijvoorbeeld een Azure-plan) met behulp van de **productUpgradeRequest-resource.**

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met app- en gebruikersreferenties. Volg het [model voor beveiligde apps bij](enable-secure-app-model.md) het gebruik van App+User-verificatie met Partner Center API's.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- De productfamilie waarvoor u de klant wilt upgraden.

## <a name="c"></a>C\#

Een klant upgraden naar een Azure-abonnement:

1. Maak een **ProductUpgradesRequest-object** en geef de klant-id en 'Azure' op als de productfamilie.

2. Gebruik de **verzameling IAggregatePartner.ProductUpgrades.**

3. Roep de **methode Create** aan en geef het **productUpgradesRequest-object** door, waarmee een locatieheaderreeks **wordt** retourneert.

4. Extraheren van **de upgrade-id** uit de locatieheaderreeks die kan worden gebruikt om de [upgradestatus op te vragen.](get-product-upgrade-status.md)

```csharp
// IAggregatePartner partnerOperations;

string selectedCustomerId = "58e2af4f-0ad3-4688-8744-be2357cd939a";

string selectedProductFamily = "Azure";

var productUpgradeRequest = new ProductUpgradesRequest
{
    CustomerId = selectedCustomerId,
    ProductFamily = selectedProductFamily
};

var productUpgradeLocationHeader = partnerOperations.ProductUpgrades.Create(productUpgradeRequest);

var upgradeId = Regex.Split(productUpgradeLocationHeader, "/")[1];

```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/productupgrades HTTP/1.1 |

#### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

#### <a name="request-body"></a>Aanvraagbody

De aanvraag body moet een [ProductUpgradeRequest-resource](product-upgrade-resources.md#productupgraderequest) bevatten.

#### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/productupgrades HTTP/1.1
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
  "productFamily": "Azure"
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat het antwoord een **Location-header** met een URI die kan worden gebruikt om de status van de productupgrade op te halen. Sla deze URI op voor gebruik met andere gerelateerde REST API's.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: productUpgrades/42d075a4-bfe7-43e7-af6d-7c68a57edcb4
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 28 Sep 2019 20:35:35 GMT
```
