---
title: Haal de details van de serviceaanvraag op op id.
description: De details van een bestaande klantenserviceaanvraag ophalen op id.
ms.date: 02/06/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 66488cf9592d630cb1f0237d379e8df5ead6a3a8
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548767"
---
# <a name="get-service-request-details-by-id"></a>Details van serviceaanvraag ophalen op basis van id

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De details van een bestaande klantenserviceaanvraag ophalen met behulp van de serviceaanvraag-id.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een serviceaanvraag-id.

## <a name="c"></a>C\#

Als u de details van een bestaande klantenserviceaanvraag wilt ophalen, roept u de methode [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) aan en geeft u een [**ServiceRequest.Id**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest.id#Microsoft_Store_PartnerCenter_Models_ServiceRequests_ServiceRequest_Id) door om een interface te identificeren en te retourneren naar het specifieke [**ServiceRequest-object.**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest)

``` csharp
// IAggregatePartner partnerOperations;
// ServiceRequest existingServiceRequest as ServiceRequest;

ServiceRequest serviceRequestDetails = partnerOperations.ServiceRequests.ById(existingServiceRequest.Id).Get();

Console.WriteLine(string.Format("The primary contact for the service request {0} is {1} {2}.",
    serviceRequestDetails.Title,
    serviceRequestDetails.PrimaryContact.FirstName,
    serviceRequestDetails.PrimaryContact.LastName,
));
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode    | Aanvraag-URI                                                                                 |
|-----------|---------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1  |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende URI-parameter om de opgegeven serviceaanvraag op te halen.

| Naam                  | Type     | Vereist | Beschrijving                                 |
|-----------------------|----------|----------|---------------------------------------------|
| **servicerequest-id** | **guid** | J        | Een GUID die de serviceaanvraag identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/servicerequests/616122292874576 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f9a030bd-e492-4c1a-9c70-021f18234981
MS-CorrelationId: fd969070-4e5f-4c6b-a3c6-1941283b39ae
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een **serviceaanvraagresource** in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 566
Content-Type: application/json; charset=utf-8
MS-CorrelationId: fd969070-4e5f-4c6b-a3c6-1941283b39ae
MS-RequestId: f9a030bd-e492-4c1a-9c70-021f18234981
MS-CV: rjLONPum/Uq94UQA.0
MS-ServerId: 030011719
Date: Mon, 09 Jan 2017 23:31:15 GMT

{
    "title": "TrialSR",
    "description": "Ignore this SR",
    "severity": "critical",
    "supportTopicId": "32444671",
    "supportTopicName": "Cannot manage my profile",
    "id": "616122292874576",
    "status": "open",
    "organization": {
        "id": "3b33e682-00c3-41ee-9dd2-a548adf56438",
        "name": "TEST_TEST_BugBash1"
    },
    "productId": "15960",
    "createdDate": "2016-12-22T20:31:17.24Z",
    "lastModifiedDate": "2017-01-09T23:31:15.373Z",
    "lastClosedDate": "0001-01-01T00:00:00",
    "notes": [{
            "createdByName": "Account",
            "createdDate": "2017-01-09T23:31:15.373",
            "text": "Sample Note"
        }
    ],
    "attributes": {
        "objectType": "ServiceRequest"
    }
}
```
