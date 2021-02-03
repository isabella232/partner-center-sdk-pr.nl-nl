---
title: Een lijst met indirecte resellers ophalen
description: Een lijst met de indirecte wederverkopers van de aangemelde partner ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e53237b97fa26d3a987f0ee7de491084b596af4a
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767523"
---
# <a name="retrieve-a-list-of-indirect-resellers"></a>Een lijst met indirecte resellers ophalen

**Van toepassing op**

- Partnercentrum

Een lijst met de indirecte wederverkopers van de aangemelde partner ophalen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

## <a name="c"></a>C\#

Als u een lijst wilt ophalen met de indirecte wederverkopers met wie de aangemelde partner een relatie heeft, moet u eerst een interface voor het verzamelen van relaties ophalen uit de eigenschap [**partnerOperations. relationships**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) . Roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.get) of [**Get \_ async**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.getasync) aan, waarbij een lid van de [**PartnerRelationshipType**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype) -inventarisatie wordt door gegeven om het relatie type te identificeren. Als u indirecte wederverkopers wilt ophalen, moet u IsIndirectCloudSolutionProviderOf gebruiken.

``` csharp
// IAggregatePartner partnerOperations;

var indirectResellers = partnerOperations.Relationships.Get(PartnerRelationshipType.IsIndirectCloudSolutionProviderOf);
```

Voor **beeld**: [console test app](console-test-app.md)**project**: Partner Center SDK samples **klasse**: GetIndirectResellers.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/relationships? Relationship \_ type = IsIndirectCloudSolutionProviderOf http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om het relatie type te identificeren.

| Naam               | Type    | Vereist  | Beschrijving                         |
|--------------------|---------|-----------|-------------------------------------|
| relationship_type  | tekenreeks  | Yes       | De waarde is de teken reeks representatie van een van de lidnamen gevonden in [PartnerRelationshipType](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype).<br/><br/> Als de partner is aangemeld als provider en u een lijst wilt weer geven met de indirecte wederverkopers met wie ze een relatie tot stand hebben gebracht, gebruikt u IsIndirectCloudSolutionProviderOf.<br/><br/> Als de partner is aangemeld als wederverkoper en u een lijst wilt krijgen met de indirecte providers met wie ze een relatie tot stand hebben gebracht, gebruikt u IsIndirectResellerOf.    |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/relationships?relationship_type=IsIndirectCloudSolutionProviderOf HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 144391a4-fb06-41ae-b684-3308ce4706bd
MS-CorrelationId: 72524ef8-81aa-4141-a049-45a4fece5d84
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord tekst een verzameling [PartnerRelationship](relationships-resources.md) -resources om de wederverkopers te identificeren.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 298
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 72524ef8-81aa-4141-a049-45a4fece5d84
MS-RequestId: 144391a4-fb06-41ae-b684-3308ce4706bd
MS-CV: b21Ll1miM0yFMPQQ.0
MS-ServerId: 030020643
Date: Wed, 05 Apr 2017 21:08:44 GMT

{
    "totalCount": 2,
    "items": [{
            "id": "484e548c-f5f3-4528-93a9-c16c6373cb59",
            "name": "First Up Consultants",
            "relationshipType": "is_indirect_cloud_solution_provider_of",
            "state": "Active",
            "mpnId": "4847383",
            "location": "US",
            "attributes": {
                "objectType": "PartnerRelationship"
            }
        }, {
            "id": "b01b1487-b36e-4e6d-9b5e-0b58974c4b28",
            "name": "ReleCloud",
            "relationshipType": "is_indirect_cloud_solution_provider_of",
            "state": "Active",
            "mpnId": "4847433",
            "location": "BR",
            "attributes": {
                "objectType": "PartnerRelationship"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```