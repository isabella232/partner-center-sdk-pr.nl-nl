---
title: Ondersteuningsprofiel bijwerken
description: Werkt het ondersteuningsprofiel van een gebruiker bij.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 143328c5501f525d52911eead805d420f79b78ff
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530341"
---
# <a name="update-support-profile"></a>Ondersteuningsprofiel bijwerken

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Werkt het ondersteuningsprofiel van een gebruiker bij.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

## <a name="c"></a>C\#

Als u uw ondersteuningsprofiel wilt bijwerken, [moet u eerst uw ondersteuningsprofiel op](get-support-profile.md) halen en eventuele wijzigingen aanbrengen. Gebruik vervolgens de [**verzameling IPartnerOperations.Profiles.**](/dotnet/api/microsoft.store.partnercenter.ipartner.profiles) Roep de [**eigenschap SupportProfile**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile) aan, gevolgd door de [**methode Update()**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.update) of [**UpdateAsync().**](/dotnet/api/microsoft.store.partnercenter.profiles.isupportprofile.updateasync)

``` csharp
// IAggregatePartner partnerOperations;

// updated profile
SupportProfile newSupportProfile = new SupportProfile
{
   Email = supportProfile.Email,
   Website = supportProfile.Website,
   Telephone = new Random().Next(10000000, 99999999).ToString(CultureInfo.InvariantCulture)
};

SupportProfile updatedSupportProfile = partnerOperations.Profiles.SupportProfile.Update(newSupportProfile);
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project:** PartnerCenterSDK.FeaturesSamples-klasse: UpdateSupportProfile.cs 

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                     |
|---------|---------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/supportprofile HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

De volledige ondersteuningsprofielresource.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PUT https://api.partnercenter.microsoft.com/v1/profiles/supportprofile HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 603f3cd9-01b8-48f2-b65d-855a246f5bfd
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
Content-Type: application/json
Content-Length: 167
Expect: 100-continue

{
    "Email": "email@sample.com",
    "Telephone": "4255555555",
    "Website": "www.microsoft.com",
    "ProfileType": "support_profile",
    "Attributes": {
        "ObjectType": "PartnerSupportProfile"
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode **bijgewerkte SupportProfile-objecteigenschappen** in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 502
Content-Type: application/json
MS-CorrelationId: 20604323-50bf-4738-9968-c5486ab32be0
MS-RequestId: 603f3cd9-01b8-48f2-b65d-855a246f5bfd
Date: Wed, 25 Nov 2015 07:16:18 GMT

{
    "email": "email@sample.com",
    "telephone": "4255555555",
    "website": "www.microsoft.com",
    "profileType": "support_profile",
    "links": {
        "self": {
            "uri": "/v1/profiles/support",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "PartnerSupportProfile"
    }
}
```
