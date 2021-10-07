---
title: Haalt een lijst met marges op voor een bepaalde partner.
description: Haalt een lijst met marges op voor een bepaalde partner.
ms.date: 09/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 3b36d2d560f3afe43af45e6001f6d407acf3f537
ms.sourcegitcommit: deb3207935fb5a74df515ed0fd4ffec90e6a143c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/07/2021
ms.locfileid: "129646388"
---
# <a name="get-margins"></a>Marges op halen

**Van toepassing op**: Partner Center 

**Juiste rollen:** Globale | Beheeragent

Partners kunnen een lijst met actieve marges voor een bepaalde partner krijgen. Deze methode retourneert marges op basis van de partner en de beschikbare begin- en einddatums. 

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.


## <a name="rest-request"></a>REST-aanvraag
[GET] /v1/margins

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **TOEVOEGEN**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/margins HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/margins HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een lijst met marges.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en meer foutopsporingsinformatie. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en meer parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
  "pageSize": 1,
  "totalSize": 2,
  "results": [
    {
      "id": "97620c21cc32_97cdce68-cce4-42aa-9410-233fd0269502",
      "productId": "DZH318Z08L40",
      "publisherName": "Market Place Test",
      "productTitle": "Software As A Service Support Preview App",
      "productType": "SaaS",
      "marginPercentage": 10.0,
      "startDate": "2021-08-04T23:16:22.4736653Z",
      "endDate": "2022-03-31T23:59:59Z",
      "status": "live",
      "statusDate": "2021-08-04T23:16:22.4736653Z"
    },
    {
      "id": "9f342f8c8f59_3be201f5-256d-4488-bd5c-6ffdeb9877ea",
      "productId": "DZH318Z08L40",
      "publisherName": "Market Place Test",
      "productTitle": "Software As A Service Support Preview App",
      "productType": "SaaS",
      "marginPercentage": 1.0,
      "startDate": "2021-08-05T21:44:35.8870924Z",
      "endDate": "2022-03-31T23:59:59Z",
      "status": "live",
      "statusDate": "2021-08-05T21:44:35.8870924Z"
    }
  ]
}
```
