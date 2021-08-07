---
title: Alle analysegegevens van verwijzingen ophalen
description: Informatie over verwijzingsanalyses verkrijgen.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: Kim-Davis
ms.author: kimnich
ms.openlocfilehash: 8fded9cc9d540fa1f7f3fcb38620c26b85c1c6032ef0176e9bd043943a425f65
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115992718"
---
# <a name="get-all-referrals-analytics-information"></a>Alle analysegegevens van verwijzingen ophalen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Informatie over verwijzingsanalyses voor uw klanten verkrijgen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI |
|---------|-------------|
| **Toevoegen** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/referrals HTTP/1.1 |

### <a name="uri-parameters"></a>URI-parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| filter | tekenreeks | Retourneert gegevens die overeenkomen met de filtervoorwaarde.</br> **Voorbeeld:**</br>  `.../referrals?filter=field eq 'value'` |
| groupby | tekenreeks | Ondersteunt zowel voorwaarden als datums. Kortcircuitlogica om het aantal buckets te beperken.</br> **Voorbeeld:**</br>  `.../referrals?groupby=termField1,dateField1,termField2` |
| aggregationLevel | tekenreeks | De *parameter aggregationLevel* vereist een *groupby*. De *parameter aggregationLevel* is van toepassing op alle datumvelden die aanwezig zijn in *de groupby*.</br> **Voorbeeld:**</br> `.../referrals?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
| top | tekenreeks | De paginalimiet is 10000. Neemt een waarde die kleiner is dan 10000.</br> **Voorbeeld:**</br> `.../referrals?top=100`</br> |
| skip | tekenreeks | Aantal rijen dat moet worden overgeslagen.</br> **Voorbeeld:**</br>  `.../referrals?top=100&skip=100` |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/referrals HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body een verzameling [verwijzingenresources.](partner-center-analytics-resources.md#referrals-resource)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
{
  "id": "112310",
  "status": "Accepted",
  "customerMarket": "US",
  "customerName": "Best Customer Ever",
  "customerOrgSize": "10to50employees",
  "acceptedDate": "2018-02-07T23:43:19",
  "acknowledgedDate": "2018-02-07T23:40:50",
  "archivedDate": null,
  "declinedDate": null,
  "expiredDate": null,
  "lostDate": null,
  "missedDate": null,
  "createdDate": "2018-02-04T23:08:59",
  "skippedDate": null,
  "wonDate": null,
  "partnerMarket": "US"
}
```

## <a name="see-also"></a>Zie ook

- [Partnercentrum Analytics - Bronnen](partner-center-analytics-resources.md)
