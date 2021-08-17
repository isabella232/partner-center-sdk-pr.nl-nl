---
title: Een MPN-id van een partner verifiëren
description: Leer hoe u de MPN-id (Microsoft Partner Network-id) van een partner kunt controleren door het MPN-profiel van de partner aan te vragen via C of de \# Partner Center REST API.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 471a94153ab4baffe45d43bee473bf68230106ad
ms.sourcegitcommit: b0534995c36d644cc5f7bdf31b2afd5355cf7149
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/16/2021
ms.locfileid: "122208055"
---
# <a name="verify-a-partner-mpn-id-via-c-or-the-partner-center-rest-api"></a>Controleer een MPN-id van een partner via C \# of de Partner Center REST API

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De id van een partner Microsoft Partner Network (MPN-id).

Met de hier getoonde techniek wordt de id van de partner Microsoft Partner Network door het MPN-profiel van de partner aan te vragen bij Partner Center. De id wordt als geldig beschouwd als de aanvraag slaagt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- De MPN-id van de partner die moet worden geverifieerd. Als u deze waarde weglaten, haalt de aanvraag het MPN-profiel van de aangemelde partner op.

## <a name="c"></a>C\#

Als u de MPN-id van een partner wilt controleren, haalt u eerst een interface op voor bewerkingen voor het verzamelen van partnerprofielen van de [**eigenschap IAggregatePartner.Profiles.**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) Haal vervolgens een interface op voor MPN-profielbewerkingen van de [**eigenschap MpnProfile.**](/dotnet/api/microsoft.store.partnercenter.profiles.ipartnerprofilecollection.mpnprofile) Roep ten slotte de [**methoden Get**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) met de MPN-id om het MPN-profiel op te halen. Als u de MPN-id weglaten van de Get- of GetAsync-aanroep, probeert de aanvraag het MPN-profiel van de aangemelde partner op te halen.

``` csharp
// IAggregatePartner partnerOperations;
// string partnerMpnId;

var partnerProfile = partnerOperations.Profiles.MpnProfile.Get(partnerMpnId);
```

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: VerifyPartnerMpnId.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                         |
|---------|-------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/mpn?mpnId={mpn-id} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Geef de volgende queryparameter op om de partner te identificeren. Als u deze queryparameter weglaten, retourneert de aanvraag het MPN-profiel van de aangemelde partner.

| Naam   | Type | Vereist | Beschrijving                                                 |
|--------|------|----------|-------------------------------------------------------------|
| mpn-id | int  | Nee       | Een Microsoft Partner Network-id die de partner identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/mpn?mpnId=9999999 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 560df6b9-6e53-4954-aed7-133477ac1194
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body de [MpnProfile-resource](profile-resources.md#mpnprofile) voor de partner.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes [voor Partner Center lijst.](error-codes.md)

### <a name="response-example-success"></a>Voorbeeld van antwoord (geslaagd)

```http
HTTP/1.1 200 OK
Content-Length: 159
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: e39e0ddf-3fd0-4b7e-bb4e-8aebe242d3ee
MS-CV: s2GvkNgZsUSadxQX.0
MS-ServerId: 030011719
Date: Thu, 13 Apr 2017 18:13:40 GMT

{
    "mpnId": "4391507",
    "profileType": "MpnProfile",
    "links": {
        "self": {
            "uri": "/profiles/mpn",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "MpnProfile"
    }
}
```

### <a name="response-example-failure"></a>Voorbeeld van een reactie (fout)

```http
HTTP/1.1 404 Not Found
Content-Length: 124
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e937630b-8341-4d70-8f73-450d32ee0189
MS-RequestId: 560df6b9-6e53-4954-aed7-133477ac1194
MS-CV: sLRFZMWm+EKuL47u.0
MS-ServerId: 102030524
Date: Thu, 13 Apr 2017 18:26:51 GMT

{
    "code": 3000,
    "description": "Partner Organization with partner_id 9999999 could not be found",
    "data": [],
    "source": "PartnerFD"
}
```
