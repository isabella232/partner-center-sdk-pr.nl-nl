---
title: Verwijderde gebruikers voor een klant weergeven
description: Haalt een lijst met verwijderde CustomerUser-resources voor een klant op op klant-id. U kunt desgewenst een paginaformaat instellen. U moet een filter leveren.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f4fec958a9a6bb580d35de1cf3007e1db3b2b650
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445303"
---
# <a name="view-deleted-users-for-a-customer"></a>Verwijderde gebruikers voor een klant weergeven

Haalt een lijst met verwijderde CustomerUser-resources voor een klant op op klant-id. U kunt desgewenst een paginaformaat instellen. U moet een filter leveren.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="what-happens-when-you-delete-a-user-account"></a>Wat gebeurt er wanneer u een gebruikersaccount verwijdert?

De gebruikerstoestand wordt ingesteld op 'inactief' wanneer u een gebruikersaccount verwijdert. Dit blijft 30 dagen zo, waarna het gebruikersaccount en de bijbehorende gegevens worden verwijderd en onherkenbaar worden gemaakt. Zie Een verwijderde gebruiker herstellen voor een klant als u een verwijderd gebruikersaccount binnen het venster van 30 dagen [wilt herstellen.](restore-a-user-for-a-customer.md) Zodra het gebruikersaccount is verwijderd en als 'inactief' is gemarkeerd, wordt het niet meer geretourneerd als lid van de gebruikersverzameling (bijvoorbeeld met Een lijst met alle gebruikersaccounts voor een klant [ophalen).](get-a-list-of-all-user-accounts-for-a-customer.md) Als u een lijst met verwijderde gebruikers wilt opvragen die nog niet zijn verwijderd, moet u een query uitvoeren voor gebruikersaccounts die zijn ingesteld op inactief.

## <a name="c"></a>C\#

Als u een lijst met verwijderde gebruikers wilt ophalen, maakt u een query die filtert op gebruikers van klanten waarvan de status is ingesteld op inactief. Maak eerst het filter door een [**SimpleFieldFilter-object**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) te instantiëren met de parameters, zoals wordt weergegeven in het volgende codefragment. Maak vervolgens de query met behulp van [**de methode BuildIndexedQuery.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) Als u geen paginaresultaten wilt, kunt u in plaats daarvan de [**methode BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) gebruiken. Gebruik vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren. Roep ten slotte de [**querymethode aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.query) om de aanvraag te verzenden.

``` csharp
// IAggregatePartner partnerOperations;
// int customerUserPageSize;

// Create a filter for users whose status is inactive (i.e. deleted).
var filter = new SimpleFieldFilter("UserState", FieldFilterOperation.Equals, "Inactive");

// Build a paged query.
var simpleQueryWithFilter = QueryFactory.Instance.BuildIndexedQuery(customerUserPageSize, 0, filter);

// Send the request.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.Query(simpleQueryWithFilter);
```

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: GetCustomerInactiveUsers.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                       |
|---------|-------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users?size={size}&filter={filter} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik het volgende pad en de queryparameters bij het maken van de aanvraag.

| Naam        | Type   | Vereist | Beschrijving                                                                                                                                                                        |
|-------------|--------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| customer-id | guid   | Ja      | De waarde is een in GUID opgemaakte klant-id die de klant identificeert.                                                                                                            |
| grootte        | int    | Nee       | Het aantal resultaten dat in één keer moet worden weergegeven. Deze parameter is optioneel.                                                                                                     |
| filter      | filter | Ja      | De query die de zoekopdracht van de gebruiker filtert. Als u verwijderde gebruikers wilt ophalen, moet u de volgende tekenreeks opnemen en coderen: {"Field":"UserState","Value":"Inactive","Operator":"equals"}. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users?size=500&filter=%7B%22Field%22%3A%22UserState%22%2C%22Value%22%3A%22Inactive%22%2C%22Operator%22%3A%22equals%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c11feb95-55d2-45b6-9d1b-74b55d2221fb
MS-CorrelationId: 2b4ab588-f48c-4874-b479-a61895e107b2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een verzameling [CustomerUser-resources](user-resources.md#customeruser) in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 802
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 690b34ca-07c8-4f8a-ab13-f22a50594a43
MS-RequestId: 1187f9ad-02b4-4d96-b668-7cf3d289467b
MS-CV: 3TLmR9gz6EaCVCjR.0
MS-ServerId: 101112616
Date: Fri, 20 Jan 2017 19:13:14 GMT

{
    "totalCount": 1,
    "items": [{
            "usageLocation": "US",
            "id": "a45f1416-3300-4f65-9e8d-f123b397a4ea",
            "userPrincipalName": "e83763f7f2204ac384cfcd49f79f2749@dtdemocspcustomer005.onmicrosoft.com",
            "firstName": "Ferdinand",
            "lastName": "Filibuster",
            "displayName": "Ferdinand",
            "userDomainType": "none",
            "state": "inactive",
            "softDeletionTime": "2017-01-20T00:33:34Z",
            "links": {
                "self": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea",
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
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users?size=500&filter=%7B%22Field%22%3A%22UserStatus%22%2C%22Value%22%3A%22Inactive%22%2C%22Operator%22%3A%22equals%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
