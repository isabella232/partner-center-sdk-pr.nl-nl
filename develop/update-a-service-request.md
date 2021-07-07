---
title: Een serviceaanvraag bijwerken
description: Een bestaande klantenserviceaanvraag bijwerken die een Cloud Solution Provider namens de klant heeft ingediend bij Microsoft.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: efa7b2a98b6f95a763ca6e3811c43cc655c18e2b
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530086"
---
# <a name="update-a-service-request"></a>Een serviceaanvraag bijwerken

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Een bestaande klantenserviceaanvraag bijwerken die een Cloud Solution Provider namens de klant heeft ingediend bij Microsoft.

In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst [een klant te selecteren.](get-a-customer-by-name.md) Selecteer vervolgens **Servicebeheer op** de linkerzijbalk. Selecteer onder de header **Ondersteuningsaanvragen** de serviceaanvraag in kwestie. Als u wilt voltooien, moet u de gewenste wijzigingen aanbrengen in de serviceaanvraag en vervolgens **Verzenden selecteren.**

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een serviceaanvraag-id.

## <a name="c"></a>C\#

Als u de serviceaanvraag van een klant wilt bijwerken, roept u de methode [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) aan met de serviceaanvraag-id om de interface voor serviceaanvraag te identificeren en te retourneren. Roep vervolgens de [**methode IServiceRequest.Patch**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patch) of [**PatchAsync aan**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patchasync) om de serviceaanvraag bij te werken. Als u de bijgewerkte waarden wilt verstrekken, maakt u een nieuw, leeg [**ServiceRequest-object**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) en stelt u alleen de eigenschapswaarden in die u wilt wijzigen. Geef dat object vervolgens door in de aanroep van de methode Patch of PatchAsync.

``` csharp
// IAggregatePartner partnerOperations;
// ServiceRequest existingServiceRequest;

ServiceRequest updatedServiceRequest = partnerOperations.ServiceRequests.ById(existingServiceRequest.Id).Patch(new ServiceRequest
{
   NewNote = note
});
```

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: UpdatePartnerServiceRequest.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode    | Aanvraag-URI                                                                                 |
|-----------|---------------------------------------------------------------------------------------------|
| **Patch** | [*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende URI-parameter om de serviceaanvraag bij te werken.

| Naam                  | Type     | Vereist | Beschrijving                                 |
|-----------------------|----------|----------|---------------------------------------------|
| **servicerequest-id** | **guid** | J        | Een GUID die de serviceaanvraag identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

De aanvraag body moet een [ServiceRequest-resource](service-request-resources.md) bevatten. De enige vereiste waarden zijn de waarden die moeten worden bijgewerkt.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PATCH https://api.partnercenter.microsoft.com/v1/servicerequests/616122292874576 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f9a030bd-e492-4c1a-9c70-021f18234981
MS-CorrelationId: fd969070-4e5f-4c6b-a3c6-1941283b39ae
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 508
Expect: 100-continue

{
    "Id": null,
    "Title": null,
    "Description": null,
    "Severity": "unknown",
    "SupportTopicId": null,
    "SupportTopicName": null,
    "Status": "none",
    "Organization": null,
    "PrimaryContact": null,
    "LastUpdatedBy": null,
    "ProductName": null,
    "ProductId": null,
    "CreatedDate": "0001-01-01T00:00:00",
    "LastModifiedDate": "0001-01-01T00:00:00",
    "LastClosedDate": "0001-01-01T00:00:00",
    "NewNote": {
        "CreatedByName": null,
        "CreatedDate": null,
        "Text": "Sample Note"
    },
    "Notes": null,
    "CountryCode": null,
    "FileLinks": null,
    "Attributes": {
        "ObjectType": "ServiceRequest"
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een **serviceaanvraagresource** met bijgewerkte eigenschappen in de antwoord-body.

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
