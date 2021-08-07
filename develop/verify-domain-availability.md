---
title: Beschikbaarheid van domein verifiëren
description: Bepalen of een domein beschikbaar is voor gebruik.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 3515216127219908aeefb2e070b138e75dc1f0e72b1f57f07f1dbff65ab79558
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989046"
---
# <a name="verify-domain-availability"></a>Beschikbaarheid van domein verifiëren

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Bepalen of een domein beschikbaar is voor gebruik.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een domein (bijvoorbeeld `contoso.onmicrosoft.com` ).

## <a name="c"></a>C\#

Als u wilt controleren of een domein beschikbaar is, roept u [**eerst IAggregatePartner.Domains**](/dotnet/api/microsoft.store.partnercenter.ipartner.domains) aan om een interface voor domeinbewerkingen te verkrijgen. Roep vervolgens de [**bydomain-methode**](/dotnet/api/microsoft.store.partnercenter.domains.idomaincollection.bydomain) aan met het domein om dit te controleren. Met deze methode wordt een interface opgehaald voor de bewerkingen die beschikbaar zijn voor een specifiek domein. Roep ten slotte de [**methode Exists**](/dotnet/api/microsoft.store.partnercenter.domains.idomain.exists) aan om te zien of het domein al bestaat.

``` csharp
// IAggregatePartner partnerOperations;
// const string domain = "contoso.onmicrosoft.com";

bool result = partnerOperations.Domains.ByDomain(domain).Exists();
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project:** Partnercentrum-SDK Klasse **Samples:** CheckDomainAvailability.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                              |
|----------|--------------------------------------------------------------------------|
| **Hoofd** | [*{baseURL}*](partner-center-rest-urls.md)/v1/domains/{domain} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de beschikbaarheid van domeinen te controleren.

| Naam       | Type       | Vereist | Beschrijving                                   |
|------------|------------|----------|-----------------------------------------------|
| **Domein** | **tekenreeks** | J        | Een tekenreeks die het te controleren domein identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
HEAD https://api.partnercenter.microsoft.com/v1/domains/contoso.onmicrosoft.com HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: cf5b00d6-9240-431c-a973-cc06c904e5bf
MS-CorrelationId: ec57501a-a4c3-45ee-ab2b-da4250545fc9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als het domein bestaat, is het niet beschikbaar voor gebruik en wordt de antwoordstatuscode 200 OK geretourneerd. Als het domein niet wordt gevonden, is het beschikbaar voor gebruik en wordt de antwoordstatuscode 404 Niet gevonden geretourneerd.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example-for-when-the-domain-is-already-in-use"></a>Voorbeeld van een reactie wanneer het domein al in gebruik is

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: ec57501a-a4c3-45ee-ab2b-da4250545fc9
MS-RequestId: cf5b00d6-9240-431c-a973-cc06c904e5bf
MS-CV: 7UXAHds8J0mNUCSp.0
MS-ServerId: 201022015
Date: Tue, 31 Jan 2017 22:22:35 GMT
```

### <a name="response-example-for-when-the-domain-is-available"></a>Voorbeeld van een reactie wanneer het domein beschikbaar is

```http
HTTP/1.1 404 Not Found
Content-Length: 0
MS-CorrelationId: 54770745-17f0-433c-bd7b-0265e5b38f98
MS-RequestId: 1169a4cd-3be7-4e29-9cb3-0f78ffa2e91e
MS-CV: RRmc+bEw9U2e97CC.0
MS-ServerId: 202010406
Date: Tue, 31 Jan 2017 22:36:01 GMT
```
