---
title: Een abonnement valideren voor migratie
description: Valideren of een abonnement in aanmerking komt voor migratie.
ms.date: 10/04/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c8d2ae596901a45a794230c79cfb54815963e300
ms.sourcegitcommit: 856b0baa4824960e13ee9672817a2d2e713fdf43
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/05/2021
ms.locfileid: "129528704"
---
# <a name="validate-a-subscription-for-migration"></a>Een abonnement valideren voor migratie

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Een abonnement valideren voor migratie naar New Commerce Experience

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een huidige abonnements-id

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
|**VERZENDEN** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/migrations/newcommerce/validate HTTP/1.1  |

### <a name="uri-parameter"></a>URI-parameter

Deze tabel bevat de vereiste queryparameters voor het valideren van een abonnement voor migratie.

| Naam               | Type   | Vereist | Beschrijving                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| customer-tenant-id | tekenreeks | Yes      | Een tekenreeks in GUID-indeling die de klant identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST Partner Center headers [voor meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de [abonnementseigenschappen](subscription-resources.md) in de aanvraag body beschreven.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| currentSubscriptionId | tekenreeks           | Yes             | Een abonnements-id die aangeeft voor welk abonnement validatie voor migratie is vereist.            |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
"currentSubscriptionId" : "9beb6319-6889-4d28-a155-68ca9c783842"
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een 'isEligible'-booleaanse naam in de antwoord-body, waarmee wordt aangegeven of het huidige abonnement in aanmerking komt voor migratie naar nieuwe commerce.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-examples"></a>Antwoordvoorbeelden

```http
1. 
    {
        "currentSubscriptionId": "9beb6319-6889-4d28-a155-68ca9c783842",
        "isEligible": false,
        "errors": [
            {
                "code": 5,
                "description": "Subscription cannot be migrated to New Commerce because the equivalent offer is not yet available in New Commerce",
            }
        ]
    }

2. 
    {
        "currentSubscriptionId": "9beb6319-6889-4d28-a155-68ca9c783842",
        "isEligible": true,
    "catalogItemId": "CFQ7TTC0LF8S:0002:CFQ7TTC0KSVV",
    }
```
