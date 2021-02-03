---
title: Verwijderde gebruikers voor een klant weergeven
description: Hiermee wordt een lijst met verwijderde CustomerUser-resources voor een klant opgehaald op basis van de klant-ID. U kunt desgewenst een pagina grootte instellen. U moet een filter opgeven.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9b1a9b85e3eba7ae7ec1dab8e951134d03371604
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767439"
---
# <a name="view-deleted-users-for-a-customer"></a>Verwijderde gebruikers voor een klant weergeven

**Van toepassing op**

- Partnercentrum

Hiermee wordt een lijst met verwijderde CustomerUser-resources voor een klant opgehaald op basis van de klant-ID. U kunt desgewenst een pagina grootte instellen. U moet een filter opgeven.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="what-happens-when-you-delete-a-user-account"></a>Wat gebeurt er wanneer u een gebruikers account verwijdert?

De gebruikers status wordt ingesteld op ' inactief ' wanneer u een gebruikers account verwijdert. Gedurende dertig dagen blijft het de gebruikers account en de bijbehorende gegevens verwijderd en worden ze onherstelbaar gemaakt. Als u een verwijderd gebruikers account in het venster van de dertig dag wilt herstellen, raadpleegt u [een verwijderde gebruiker herstellen voor een klant](restore-a-user-for-a-customer.md). Eenmaal verwijderd en gemarkeerd als ' inactief ', wordt het gebruikers account niet langer geretourneerd als lid van de gebruikers verzameling (bijvoorbeeld met behulp [van een lijst met alle gebruikers accounts voor een klant ophalen](get-a-list-of-all-user-accounts-for-a-customer.md)). Als u een lijst wilt weer geven met verwijderde gebruikers die nog niet zijn opgeschoond, moet u een query uitvoeren voor gebruikers accounts die zijn ingesteld op inactief.

## <a name="c"></a>C\#

Als u een lijst met verwijderde gebruikers wilt ophalen, moet u een query maken die filtert op klant gebruikers waarvan de status is ingesteld op inactief. Maak eerst het filter door een [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) -object te instantiëren met de para meters, zoals wordt weer gegeven in het volgende code fragment. Maak vervolgens de query met behulp van de methode [**BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) . Als u geen pagina-resultaten wilt, kunt u in plaats daarvan de [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) -methode gebruiken. Gebruik vervolgens de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren. Roep ten slotte de [**query**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.query) methode aan om de aanvraag te verzenden.

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

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: GetCustomerInactiveUsers.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                                       |
|---------|-------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/users? grootte = {size} &filter = {filter} http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende pad-en query parameters bij het maken van de aanvraag.

| Naam        | Type   | Vereist | Beschrijving                                                                                                                                                                        |
|-------------|--------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| klant-id | guid   | Yes      | De waarde is een klant-id met een GUID-indeling waarmee de klant wordt geïdentificeerd.                                                                                                            |
| grootte        | int    | No       | Het aantal resultaten dat tegelijk moet worden weer gegeven. Deze parameter is optioneel.                                                                                                     |
| filter      | filter | Yes      | De query die de zoek opdracht van de gebruiker filtert. Als u verwijderde gebruikers wilt ophalen, moet u de volgende teken reeks insluiten en coderen: {"veld": "UserState", "waarde": "inactieve", "operator": "is gelijk aan"}. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, retourneert deze methode een verzameling [CustomerUser](user-resources.md#customeruser) -resources in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

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
