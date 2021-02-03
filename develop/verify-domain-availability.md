---
title: Beschikbaarheid van domein verifiëren
description: Bepalen of een domein beschikbaar is voor gebruik.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 84edb5b7510642ec44dad3d4f92349e40eb10b24
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767463"
---
# <a name="verify-domain-availability"></a>Beschikbaarheid van domein verifiëren

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Bepalen of een domein beschikbaar is voor gebruik.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een domein (bijvoorbeeld `contoso.onmicrosoft.com` ).

## <a name="c"></a>C\#

Als u wilt controleren of er een domein beschikbaar is, roept u [**IAggregatePartner. domains**](/dotnet/api/microsoft.store.partnercenter.ipartner.domains) aan om een interface voor domein bewerkingen te verkrijgen. Roep vervolgens de methode [**ByDomain**](/dotnet/api/microsoft.store.partnercenter.domains.idomaincollection.bydomain) aan met het te controleren domein. Met deze methode wordt een interface opgehaald voor de bewerkingen die beschikbaar zijn voor een specifiek domein. Roep tot slot de methode [**Exists**](/dotnet/api/microsoft.store.partnercenter.domains.idomain.exists) aan om te zien of het domein al bestaat.

``` csharp
// IAggregatePartner partnerOperations;
// const string domain = "contoso.onmicrosoft.com";

bool result = partnerOperations.Domains.ByDomain(domain).Exists();
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: CheckDomainAvailability.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                              |
|----------|--------------------------------------------------------------------------|
| **HOREN** | [*{baseURL}*](partner-center-rest-urls.md)/v1/domains/{Domain} http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om de beschik baarheid van het domein te verifiëren.

| Naam       | Type       | Vereist | Beschrijving                                   |
|------------|------------|----------|-----------------------------------------------|
| **domeinen** | **tekenreeksexpressie** | J        | Een teken reeks waarmee het te controleren domein wordt geïdentificeerd. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als het domein bestaat, kan het niet worden gebruikt en wordt de antwoord status code 200 OK geretourneerd. Als het domein niet wordt gevonden, is het beschikbaar voor gebruik en wordt de antwoord status code 404 niet gevonden geretourneerd.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example-for-when-the-domain-is-already-in-use"></a>Antwoord voorbeeld voor wanneer het domein al in gebruik is

```http
HTTP/1.1 200 OK
Content-Length: 0
MS-CorrelationId: ec57501a-a4c3-45ee-ab2b-da4250545fc9
MS-RequestId: cf5b00d6-9240-431c-a973-cc06c904e5bf
MS-CV: 7UXAHds8J0mNUCSp.0
MS-ServerId: 201022015
Date: Tue, 31 Jan 2017 22:22:35 GMT
```

### <a name="response-example-for-when-the-domain-is-available"></a>Antwoord voorbeeld voor wanneer het domein beschikbaar is

```http
HTTP/1.1 404 Not Found
Content-Length: 0
MS-CorrelationId: 54770745-17f0-433c-bd7b-0265e5b38f98
MS-RequestId: 1169a4cd-3be7-4e29-9cb3-0f78ffa2e91e
MS-CV: RRmc+bEw9U2e97CC.0
MS-ServerId: 202010406
Date: Tue, 31 Jan 2017 22:36:01 GMT
```
