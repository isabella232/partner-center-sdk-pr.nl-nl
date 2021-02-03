---
title: Controleren of de klant in aanmerking komt voor een upgrade naar een Azure-abonnement
description: U kunt de ProductUpgradeRequest-Resource gebruiken om een ProductUpgradesEligibility-resource te retour neren om te bepalen of een klant in aanmerking komt voor een upgrade van een Microsoft Azure (MS-AZR-0145P) naar een Azure-abonnement.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 568ed3f4cff7d9cd520e608d43cb89bb78e00ccc
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767169"
---
# <a name="check-a-customers-eligibility-for-upgrading-to-an-azure-plan"></a>Controleren of de klant in aanmerking komt voor een upgrade naar een Azure-abonnement

**Van toepassing op:**

- Partnercentrum

U kunt de [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) -Resource gebruiken om te controleren of een klant in aanmerking komt voor een upgrade naar een Azure-abonnement van een Microsoft Azure (MS-AZR-0145P). deze methode retourneert een [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) -resource met de product upgrade van de klant.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met app + gebruikers referenties. Volg het [model voor beveiligde apps](enable-secure-app-model.md) wanneer u app + gebruikers authenticatie met partner Center api's gebruikt.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- De product familie.

## <a name="c"></a>C\#

Controleren of een klant in aanmerking komt voor een upgrade naar een Azure-abonnement:

1. Maak een **ProductUpgradesRequest** -object en geef de klant-id en ' Azure ' op als de product familie.

2. Gebruik de verzameling **IAggregatePartner. ProductUpgrades** .
3. Roep de methode **CheckEligibility** aan en geef het object **ProductUpgradesRequest** door, waardoor een **ProductUpgradesEligibility** -object wordt geretourneerd.

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

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/productUpgrades/Eligibility http/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

De aanvraag tekst moet een [**ProductUpgradeRequest**](product-upgrade-resources.md#productupgraderequest) -resource bevatten.

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

Als dit lukt, retourneert deze methode een [**ProductUpgradesEligibility**](product-upgrade-resources.md#productupgradeseligibility) -resource in de hoofd tekst.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

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
