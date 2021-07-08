---
title: Een lijst met alle gebruikersaccounts voor een klant ophalen
description: Een lijst met alle gebruikersaccounts van een van uw klanten op te halen.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: f3d5fcc610eae8c1bff056c1e4a9e7a74093c87d
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874564"
---
# <a name="get-a-list-of-all-user-accounts-for-a-customer"></a>Een lijst met alle gebruikersaccounts voor een klant ophalen

In dit artikel wordt beschreven hoe u een lijst op kunt halen met alle gebruikersaccounts die deel uitmaken van een van uw klanten.

Zie Get a user account by ID (Een gebruikersaccount op id opmaken) als u één gebruikersaccount op id [wilt op zoeken.](get-a-user-account-by-id.md)

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="c"></a>C\#

De verzameling van alle gebruikersaccounts voor een opgegeven klant ophalen:

1. Roep de [**methode IAggregatePartner.Customers.ById aan**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de opgegeven klant-id om de klant te identificeren.

2. Roep de [**methode Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) om de verzameling op te halen.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

// Get customer users collection.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.Get();
```

Zie voor een voorbeeld het volgende:

- Voorbeeld: [Consoletest-app](console-test-app.md)
- Project: **Partnercentrum-SDK Voorbeelden**
- Klasse: **GetCustomerUserCollection.cs**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1 |

#### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende URI-parameter om de juiste klant te identificeren.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | **guid** | J        | De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 5d845377-5b7d-4cd4-98f6-19e5ae3faa81
MS-CorrelationId: 5a3d64d4-4490-4932-bf5e-0dc9a58f27ca
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een verzameling gebruikersaccounts voor een klant.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 1030
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5a3d64d4-4490-4932-bf5e-0dc9a58f27ca
MS-RequestId: 5d845377-5b7d-4cd4-98f6-19e5ae3faa81
MS-CV: 6zmKqrSFB0+t7m3y.0
MS-ServerId: 101112616
Date: Wed, 21 Dec 2016 21:13:24 GMT

 {
    "totalCount": 2,
    "items": [{
            "usageLocation": "US",
            "id": "a9ef48bb-8758-4590-a312-d4a47bfaded4",
            "userPrincipalName": "Daniel@dtdemocspcustomer005.onmicrosoft.com",
            "firstName": "Daniel",
            "lastName": "Tsai",
            "displayName": "Daniel Tsai",
            "userDomainType": "none",
            "state": "active",
            "links": {
                "self": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a9ef48bb-8758-4590-a312-d4a47bfaded4",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "CustomerUser"
            }
        }, {
            "id": "6e668259-1f09-479d-bcb8-d9b03e826b8d",
            "userPrincipalName": "admin@dtdemocspcustomer005.onmicrosoft.com",
            "firstName": "Daniel",
            "lastName": "Tsai",
            "displayName": "DT Demo CSP Customer 005",
            "userDomainType": "none",
            "state": "active",
            "links": {
                "self": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/6e668259-1f09-479d-bcb8-d9b03e826b8d",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "CustomerUser"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
