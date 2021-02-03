---
title: Een URL voor relatie aanvragen ophalen
description: Een URL voor relatie aanvragen ophalen om naar een klant te verzenden.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 5f899734b774ff460e005e20df8658275b2ce9d5
ms.sourcegitcommit: d4e652e3b73c6137704d43d4a472cc5aa5549f11
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "97768681"
---
# <a name="retrieve-a-relationship-request-url"></a>Een URL voor relatie aanvragen ophalen

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland

Een URL voor relatie aanvragen ophalen om naar een klant te verzenden.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

## <a name="c"></a>C\#

Als u een URL voor de relatie aanvraag wilt ophalen, moet u eerst [**IAggregatePartner. klanten**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) gebruiken om een interface te verkrijgen voor de klant bewerkingen van de partner. Gebruik vervolgens de eigenschap [**RelationshipRequest**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.relationshiprequest) om een interface op te halen voor de bewerkingen van klant relatie aanvragen. Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.getasync) aan om de URL op te halen.

``` csharp
// IAggregatePartner partnerOperations;

var customerRelationshipRequest = partnerOperations.Customers.RelationshipRequest.Get();
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: GetCustomerRelationshipRequest.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                            |
|---------|----------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/relationshiprequests http/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/relationshiprequests HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ee519026-4c67-4113-bec7-a38aca621bf0
MS-CorrelationId: 02971f0f-1029-47b2-9fdb-1932f0987470
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als dit is gelukt, bevat het antwoord het [RelationshipRequest](relationships-resources.md#relationshiprequest) -object.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 196
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 02971f0f-1029-47b2-9fdb-1932f0987470
MS-RequestId: ee519026-4c67-4113-bec7-a38aca621bf0
MS-CV: jbYZRWjU3E262f8o.0
MS-ServerId: 030020643
Date: Fri, 19 May 2017 22:32:07 GMT

{
    "url": "https://admin.microsoft.com/Adminportal/Home?invType=ResellerRelationship&partnerId=3b33e682-00c3-41ee-9dd2-a548adf56438&msppId=0&DAP=false#/BillingAccounts/partner-invitation",
    "attributes": {
        "objectType": "RelationshipRequest"
    }
}
```
