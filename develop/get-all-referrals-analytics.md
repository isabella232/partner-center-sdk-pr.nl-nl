---
title: Alle analysegegevens van verwijzingen ophalen
description: Instructies voor het ophalen van de analyse-informatie over verwijzingen.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: Kim-Davis
ms.author: kimnich
ms.openlocfilehash: b470c59cecf8b214e6d90a244e928e5d15ebd3e0
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767288"
---
# <a name="get-all-referrals-analytics-information"></a>Alle analysegegevens van verwijzingen ophalen

**Van toepassing op**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Meer informatie over het ophalen van de verwijzingen voor uw klanten.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI |
|---------|-------------|
| **Toevoegen** | [*\{ BASEURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/referrals http/1.1 |

### <a name="uri-parameters"></a>URI-para meters

| Parameter | Type | Description |
|-----------|------|-------------|
| filter | tekenreeks | Hiermee worden gegevens geretourneerd die overeenkomen met de filter voorwaarde.</br> **Voorbeeld:**</br>  `.../referrals?filter=field eq 'value'` |
| GroupBy | tekenreeks | Ondersteunt zowel termen als datums. Korte circuit logica om het aantal buckets te beperken.</br> **Voorbeeld:**</br>  `.../referrals?groupby=termField1,dateField1,termField2` |
| aggregationLevel | tekenreeks | Voor de para meter *aggregationLevel* is een *GroupBy* vereist. De para meter *aggregationLevel* is van toepassing op alle datum velden die in de *GroupBy* worden weer gegeven.</br> **Voorbeeld:**</br> `.../referrals?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
| top | tekenreeks | De pagina limiet is 10000. Neemt een waarde op die kleiner is dan 10000.</br> **Voorbeeld:**</br> `.../referrals?top=100`</br> |
| skip | tekenreeks | Het aantal rijen dat moet worden overgeslagen.</br> **Voorbeeld:**</br>  `.../referrals?top=100&skip=100` |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, bevat de antwoord tekst een verzameling [verwijzingen](partner-center-analytics-resources.md#referrals-resource) -resources.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

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
