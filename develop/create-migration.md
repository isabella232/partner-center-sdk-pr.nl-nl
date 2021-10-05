---
title: Een nieuwe commerce-migratie maken
description: Een nieuwe commercemigratie maken
ms.date: 10/04/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 659cc036b37ce85283581d2f3e28493814dad5f7
ms.sourcegitcommit: 856b0baa4824960e13ee9672817a2d2e713fdf43
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/05/2021
ms.locfileid: "129528708"
---
#  <a name="create-a-new-commerce-migration"></a>Een nieuwe commerce-migratie maken

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Een migratie maken van een abonnement naar New Commerce Experience

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een huidige abonnements-id

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
|**VERZENDEN** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/migrations/newcommerce HTTP/1.1           |

### <a name="uri-parameter"></a>URI-parameter

Deze tabel bevat de vereiste queryparameters voor het maken van een nieuwe commercemigratie.

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

Als dit lukt, retourneert deze methode een verzameling [abonnementsresources](subscription-resources.md) in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-examples"></a>Antwoordvoorbeelden

```http
{
    "id": "d3a0ef43-a208-4c32-8b10-f15e99d4e782",
    "currentSubscriptionId": "9beb6319-6889-4d28-a155-68ca9c783842",
    "status": "Processing",
    "customerTenantId": "a836f6d8-1b17-44af-aaf1-1e5511c5d4e1",
    "partnerTenantId": "7828d7ba-f17b-45c3-a1ce-8b6c3e3a26c0",
    "catalogItemId": "CFQ7TTC0LF8S:0002:CFQ7TTC0KSVV",
    "subscriptionEndDate": "2022-09-06T00:00:00Z",
    "quantity": 1,
    "termDuration": "P1Y",
    "billingCycle": "Monthly"
}
```
