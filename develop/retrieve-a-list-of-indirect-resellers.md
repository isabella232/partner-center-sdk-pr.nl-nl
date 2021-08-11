---
title: Een lijst met indirecte resellers ophalen
description: Een lijst met indirecte resellers van de aangemelde partner ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 901bf045d1de29744114bb58ed445f9eb17f70a4744786fd4617da9697e7c683
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996916"
---
# <a name="retrieve-a-list-of-indirect-resellers"></a>Een lijst met indirecte resellers ophalen

Een lijst met indirecte resellers van de aangemelde partner ophalen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.

## <a name="c"></a>C\#

Als u een lijst wilt ophalen met indirecte resellers met wie de aangemelde partner een relatie heeft, haalt u eerst een interface op met bewerkingen voor het verzamelen van relaties van de [**eigenschap partnerOperations.Relationships.**](/dotnet/api/microsoft.store.partnercenter.ipartner.relationships) Roep vervolgens de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.get) of [**Get \_ Async**](/dotnet/api/microsoft.store.partnercenter.relationships.irelationshipcollection.getasync) aan, waarbij een lid van de Enumeration [**PartnerRelationshipType**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype) wordt doorgeven om het relatietype te identificeren. Als u indirecte resellers wilt ophalen, moet u IsIndirectCloudSolutionProviderOf gebruiken.

``` csharp
// IAggregatePartner partnerOperations;

var indirectResellers = partnerOperations.Relationships.Get(PartnerRelationshipType.IsIndirectCloudSolutionProviderOf);
```

**Voorbeeld**: [Consoletest-app](console-test-app.md)**Project**: Partnercentrum-SDK Samples **Class:** GetIndirectResellers.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/relationships?relatietype=IsIndirectCloudSolutionProviderOf \_ HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om het relatietype te identificeren.

| Naam               | Type    | Vereist  | Beschrijving                         |
|--------------------|---------|-----------|-------------------------------------|
| relationship_type  | tekenreeks  | Yes       | De waarde is de tekenreeksweergave van een van de lidnamen in [PartnerRelationshipType](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationshiptype).<br/><br/> Als de partner is aangemeld als provider en u een lijst wilt krijgen van de indirecte resellers met wie ze een relatie tot stand hebben gebracht, gebruikt u IsIndirectCloudSolutionProviderOf.<br/><br/> Als de partner is aangemeld als een reseller en u een lijst wilt krijgen met de indirecte providers met wie ze een relatie hebben gemaakt, gebruikt u IsIndirectResellerOf.    |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

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

Als dit lukt, bevat de antwoord-body een verzameling [PartnerRelationship-resources](relationships-resources.md) om de resellers te identificeren.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)

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