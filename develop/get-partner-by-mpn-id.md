---
title: Een MPN-id van een partner verifiëren
description: Lees hoe u de Microsoft Partner Network-ID van een partner (MPN-ID) kunt controleren door het MPN-Profiel van de partner via C \# of het Partner Center-rest API aan te vragen.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6ef7bcb35274a6bcbaddbe0553ca0cb4dc1b2f9c
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "97767574"
---
# <a name="verify-a-partner-mpn-id-via-c-or-the-partner-center-rest-api"></a>Een partner MPN-ID verifiëren via C \# of het Partner Center rest API

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De Microsoft Partner Network-ID van een partner controleren (MPN-ID).

De hier weer gegeven methode verifieert de Microsoft Partner Network-ID van de partner door het MPN-Profiel van de partner aan te vragen bij het partner centrum. De id wordt als geldig beschouwd als de aanvraag slaagt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- De MPN-ID van de partner die moet worden geverifieerd. Als u deze waarde weglaat, wordt door de aanvraag het MPN-Profiel van de aangemelde partner opgehaald.

## <a name="c"></a>C\#

Als u de MPN-ID van een partner wilt verifiëren, moet u eerst een interface voor het verzamelen van partner profielen ophalen uit de eigenschap [**IAggregatePartner. Profiles**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) . Vervolgens krijgt u een interface voor het MPN van profiel bewerkingen van de eigenschap [**MpnProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.ipartnerprofilecollection.mpnprofile) . Roep ten slotte de methoden [**Get**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.profiles.impnprofile.getasync) aan met de MPN-ID om het MPN-profiel op te halen. Als u de MPN-ID van de aanroep Get of GetAsync weglaat, probeert de aanvraag het MPN-Profiel van de aangemelde partner op te halen.

``` csharp
// IAggregatePartner partnerOperations;
// string partnerMpnId;

var partnerProfile = partnerOperations.Profiles.MpnProfile.Get(partnerMpnId);
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: VerifyPartnerMpnId.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                         |
|---------|-------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Profiles/MPN? mpnId = {MPN-id} http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Geef de volgende query parameter op om de partner te identificeren. Als u deze query parameter weglaat, retourneert de aanvraag het MPN-Profiel van de aangemelde partner.

| Naam   | Type | Vereist | Beschrijving                                                 |
|--------|------|----------|-------------------------------------------------------------|
| MPN-id | int  | No       | Een Microsoft Partner Network-ID waarmee de partner wordt geïdentificeerd. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, bevat de antwoord tekst de [MpnProfile](profile-resources.md#mpnprofile) -resource voor de partner.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example-success"></a>Voor beeld van antwoord (geslaagd)

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

### <a name="response-example-failure"></a>Voor beeld van antwoord (fout)

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
