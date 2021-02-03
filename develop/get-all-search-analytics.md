---
title: Alle analysegegevens van zoeken ophalen
description: Alle informatie over de zoek analyse ophalen.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 967f8d0ed2d276e0f68a047204b64d83dc69da95
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767180"
---
# <a name="get-all-search-analytics-information"></a>Alle analysegegevens van zoeken ophalen

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

U kunt alle informatie over de zoek analyse voor uw klanten ophalen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI |
|---------|-------------|
| **Toevoegen** | [*\{ BASEURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/Search http/1.1 |

### <a name="uri-parameters"></a>URI-para meters

|    Parameter     |  Type  |                                                                                                                   Description                                                                                                                    |
|------------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      filter      | tekenreeks |                                                                     Hiermee worden gegevens geretourneerd die overeenkomen met de filter voorwaarde. </br> **Voorbeeld:**</br> `.../search?filter=field eq 'value'`                                                                     |
|     GroupBy      | tekenreeks |                                         Ondersteunt zowel termen als datums. Korte circuit logica om het aantal buckets te beperken. </br> **Voorbeeld:**</br> `.../search?groupby=termField1,dateField1,termField2`                                         |
| aggregationLevel | tekenreeks | Voor de para meter *aggregationLevel* is een *GroupBy* vereist. De para meter *aggregationLevel* is van toepassing op alle datum velden die in de *GroupBy* worden weer gegeven. </br> **Voorbeeld:**</br>  `.../search?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
|       top        | tekenreeks |                                                                     De pagina limiet is 10000. Neemt een waarde op die kleiner is dan 10000.  </br> **Voorbeeld:**</br>  `.../search?top=100`                                                                     |
|       skip       | tekenreeks |                                                                                  Het aantal rijen dat moet worden overgeslagen. </br> **Voorbeeld:**</br> `.../search?top=100&skip=100`                                                                                   |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, bevat de antwoord tekst een verzameling [Zoek](partner-center-analytics-resources.md#search-resource) bronnen.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

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
