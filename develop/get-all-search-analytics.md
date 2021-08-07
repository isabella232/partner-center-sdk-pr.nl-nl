---
title: Alle analysegegevens van zoeken ophalen
description: Informatie over het verkrijgen van alle zoekanalysegegevens.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a420752264f4d3074ba8a569c931654fda3ad6363d8d5d8b6a7a3e32af126bd1
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115990899"
---
# <a name="get-all-search-analytics-information"></a>Alle analysegegevens van zoeken ophalen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Informatie over het verkrijgen van alle zoekanalysegegevens voor uw klanten.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI |
|---------|-------------|
| **Toevoegen** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/search HTTP/1.1 |

### <a name="uri-parameters"></a>URI-parameters

|    Parameter     |  Type  |                                                                                                                   Description                                                                                                                    |
|------------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      filter      | tekenreeks |                                                                     Retourneert gegevens die overeenkomen met de filtervoorwaarde. </br> **Voorbeeld:**</br> `.../search?filter=field eq 'value'`                                                                     |
|     groupby      | tekenreeks |                                         Ondersteunt zowel voorwaarden als datums. Kortcircuitlogica om het aantal buckets te beperken. </br> **Voorbeeld:**</br> `.../search?groupby=termField1,dateField1,termField2`                                         |
| aggregationLevel | tekenreeks | De *parameter aggregationLevel* vereist een *groupby*. De *parameter aggregationLevel* is van toepassing op alle datumvelden die aanwezig zijn in *de groupby*. </br> **Voorbeeld:**</br>  `.../search?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
|       top        | tekenreeks |                                                                     De paginalimiet is 10000. Neemt een waarde die kleiner is dan 10000.  </br> **Voorbeeld:**</br>  `.../search?top=100`                                                                     |
|       skip       | tekenreeks |                                                                                  Het aantal rijen dat moet worden overgeslagen. </br> **Voorbeeld:**</br> `.../search?top=100&skip=100`                                                                                   |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/search HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body een verzameling [Zoekresources.](partner-center-analytics-resources.md#search-resource)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
{
  "companyName": "my company",
  "contactButtonClicked": false,
  "keywordCountry": null,
  "detailsViewed": true,
  "keywordIndustryFocus": null,
  "mpnId": 2604568,
  "partnerMarket": "CN",
  "keywordProduct": null,
  "referralSubmitted": false,
  "searchDate": "2018-05-30",
  "keywordSearchText": " my company"
}
```

## <a name="see-also"></a>Zie ook

- [Partnercentrum Analytics - Bronnen](partner-center-analytics-resources.md)
