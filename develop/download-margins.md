---
title: Haalt een lijst met marges op in door komma's scheidingstekens voor een bepaalde partner.
description: Haalt een lijst met marges op in door komma's scheidingstekens voor een bepaalde partner.
ms.date: 09/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 6328ab962b2f210cee76b585ce2cf883c41eac3f
ms.sourcegitcommit: deb3207935fb5a74df515ed0fd4ffec90e6a143c
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/07/2021
ms.locfileid: "129646387"
---
# <a name="download-margins"></a>Marges downloaden


**Van toepassing op**: Partner Center 

**Juiste rollen:** Globale | Beheeragent

Partners kunnen een lijst met actieve marges voor een bepaalde partner krijgen. Deze methode retourneert marges op basis van de partner en de beschikbare begin- en einddatums. Downloadmarges retourneert de gegevens in een door komma's scheidingstekens.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.


## <a name="rest-request"></a>REST-aanvraag
[GET] /v1/margins

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **TOEVOEGEN**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/margins/download HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/margins/download HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode de prijslijst als een bestandsstroom als a.csv bestand

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

"id","productId","publisherName","productTitle","productType"","marginPercentage","startDate","endDate","status","statusDate"
"97620c21cc32_97cdce68-cce4-42aa-9410-233fd0269502","DZH318Z08L40","Market Place Test","Software As A Service Support Preview App","SaaS","10.0","2021-08-04T23:16:22.4736653Z","2022-03-31T23:59:59Z","live","2021-08-04T23:16:22.4736653Z"

```
