---
title: Een lijst met categorieën van aanbiedingen per markt ophalen
description: Meer informatie over het ophalen van een verzameling die alle aanbiedingscategorieën in een bepaald land/regio en land/regio voor alle Microsoft Clouds bevat.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: e699355f07dda3941eafed32f5f635d94000abd1
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874275"
---
# <a name="get-a-list-of-offer-categories-by-market"></a>Een lijst met categorieën van aanbiedingen per markt ophalen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

In dit artikel wordt beschreven hoe u een verzameling ophaalt die alle aanbiedingscategorieën in een bepaald land/regio en land/regio bevat.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

## <a name="c"></a>C\#

Een lijst met aanbiedingscategorieën in een bepaald land/regio en land/regio op te halen:

1. Gebruik de [**verzameling IAggregatePartner.Operations**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) om de [**methode With() aan te**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner.with) roepen voor een bepaalde context.

2. Inspecteer [**de eigenschap OfferCategories**](/dotnet/api/microsoft.store.partnercenter.ipartner.offercategories) van het resulterende object.

``` csharp
// IAggregatePartner partnerOperations;

ResourceCollection<OfferCategory> offerCategoryResults = partnerOperations.With(RequestContextFactory.Instance.Create()).OfferCategories.ByCountry("US").Get();
```

Zie voor een voorbeeld het volgende:

- Voorbeeld: [Consoletest-app](console-test-app.md)
- Project: **PartnerSDK.FeatureSample**
- Klasse: **PartnerSDK.FeatureSample**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/offercategories?country={country-id} HTTP/1.1 |

#### <a name="uri-parameter"></a>URI-parameter

Deze tabel bevat de vereiste queryparameters om de aanbiedingscategorieën op te halen.

| Naam           | Type       | Vereist | Beschrijving            |
|----------------|------------|----------|------------------------|
| **country-id** | **tekenreeks** | J        | De land-/regio-id. |

### <a name="request-headers"></a>Aanvraagheaders

Er **is een locale-id** vereist die is opgemaakt als een tekenreeks.

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/offercategories?country=<country-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fb54bd5-a4c3-4fac-955f-9b6e3436d606
MS-CorrelationId: 47882653-eaed-4a2e-a552-1070a3fa1089
X-Locale: <locale-id>
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een verzameling **OfferCategory-resources** in de antwoordbody.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor een [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 1184
Content-Type: application/json
MS-CorrelationId: 47882653-eaed-4a2e-a552-1070a3fa1089
MS-RequestId: 4fb54bd5-a4c3-4fac-955f-9b6e3436d606
Date: Thu, 26 Nov 2015 00:07:10 GMT

{
    "totalCount": 4,
    "items": [{
        "id": "Enterprise_Key",
        "name": "Enterprise",
        "rank": 20,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    {
        "id": "SmallBusiness_Key",
        "name": "SmallBusiness",
        "rank": 30,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    {
        "id": "Government_Key",
        "name": "Government",
        "rank": 40,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    {
        "id": "Internal_Key",
        "name": "Internal",
        "rank": 100,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
