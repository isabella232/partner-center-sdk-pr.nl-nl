---
title: Een lijst met categorieën van aanbiedingen per markt ophalen
description: Meer informatie over het ophalen van een verzameling die alle categorieën van de aanbieding bevat in een bepaald land/regio en land instelling voor alle micro soft-Clouds.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 05aad095c6cb8eaee4cbf7ce976ca1b4b7a408c4
ms.sourcegitcommit: f72173df911aee3ab29b008637190b4d85ffebfe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/06/2021
ms.locfileid: "106500053"
---
# <a name="get-a-list-of-offer-categories-by-market"></a>Een lijst met categorieën van aanbiedingen per markt ophalen

**Van toepassing op:**

- Partnercentrum
- Partnercentrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt beschreven hoe u een verzameling kunt ophalen die alle categorieën van de aanbieding bevat in een bepaald land/regio en land instelling.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

## <a name="c"></a>C\#

Een lijst met aanbiedings categorieën in een bepaald land/regio en land instellingen ophalen:

1. Gebruik uw [**IAggregatePartner. Operations**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) -verzameling om de methode [**with ()**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner.with) aan te roepen voor een bepaalde context.

2. Inspecteer de eigenschap [**OfferCategories**](/dotnet/api/microsoft.store.partnercenter.ipartner.offercategories) van het resulterende object.

``` csharp
// IAggregatePartner partnerOperations;

ResourceCollection<OfferCategory> offerCategoryResults = partnerOperations.With(RequestContextFactory.Instance.Create()).OfferCategories.ByCountry("US").Get();
```

Voor een voor beeld ziet u het volgende:

- Voor beeld: [console test-app](console-test-app.md)
- Project: **PartnerSDK. FeatureSample**
- Klasse: **PartnerSDK. FeatureSample**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/offercategories? land = {land-id} http/1.1 |

#### <a name="uri-parameter"></a>URI-para meter

Deze tabel bevat de vereiste query parameters om de aanbiedings Categorieën op te halen.

| Naam           | Type       | Vereist | Beschrijving            |
|----------------|------------|----------|------------------------|
| **land-id** | **tekenreeks** | J        | De ID van het land/de regio. |

### <a name="request-headers"></a>Aanvraagheaders

Een **land instellingen-id** die is opgemaakt als een teken reeks is vereist.

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, retourneert deze methode een verzameling **OfferCategory** -resources in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor een volledige lijst.

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
