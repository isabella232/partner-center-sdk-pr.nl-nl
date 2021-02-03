---
title: Een verwijderde gebruiker voor een klant herstellen
description: Een verwijderde gebruiker herstellen op basis van klant-ID en gebruikers-ID.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9fd86a268c804a2fdd5efd67a8982afc043c95a6
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767527"
---
# <a name="restore-a-deleted-user-for-a-customer"></a>Een verwijderde gebruiker voor een klant herstellen

**Van toepassing op**

- Partnercentrum

Een verwijderde **gebruiker** herstellen op basis van klant-id en gebruikers-id.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- De gebruikers-ID. Als u de gebruikers-ID niet hebt, raadpleegt u [Verwijderde gebruikers voor een klant weer geven](view-a-deleted-user.md).

## <a name="when-can-you-restore-a-deleted-user-account"></a>Wanneer kunt u een verwijderd gebruikers account herstellen?

De gebruikers status wordt ingesteld op ' inactief ' wanneer u een gebruikers account verwijdert. Gedurende dertig dagen blijft het de gebruikers account en de bijbehorende gegevens verwijderd en worden ze onherstelbaar gemaakt. U kunt een verwijderd gebruikers account alleen herstellen tijdens deze periode van dertig dagen. Nadat het gebruikers account is verwijderd en gemarkeerd als ' inactief ', wordt het niet meer weer gegeven als lid van de gebruikers verzameling (bijvoorbeeld met behulp [van een lijst met alle gebruikers accounts voor een klant](get-a-list-of-all-user-accounts-for-a-customer.md)).

## <a name="c"></a>C\#

Als u een gebruiker wilt herstellen, maakt u een nieuw exemplaar van de klasse [**CustomerUser**](/dotnet/api/microsoft.store.partnercenter.models.users.customeruser) en stelt u de waarde van de eigenschap [**User. State**](/dotnet/api/microsoft.store.partnercenter.models.users.user.state) in op [**UserState. Active**](/dotnet/api/microsoft.store.partnercenter.models.users.userstate).

U herstelt een verwijderde gebruiker door de status van de gebruiker in te stellen op actief. U hoeft de resterende velden niet opnieuw in te vullen in de gebruikers resource. Deze waarden worden automatisch hersteld op basis van de verwijderde, niet-actieve gebruikers resource. Gebruik vervolgens de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren en de [**gebruikers. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) -methode om de gebruiker te identificeren.

Ten slotte roept u de [**patch**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.patch) -methode aan en geeft u het **CustomerUser** -exemplaar door om de aanvraag te verzenden om de gebruiker te herstellen.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedCustomerUserId;

var updatedCustomerUser = new CustomerUser()
{
    State = UserState.Active
};

// Restore customer user information.
var restoredCustomerUserInfo = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Patch(updatedCustomerUser);
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: CustomerUserRestore.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode    | Aanvraag-URI                                                                                            |
|-----------|--------------------------------------------------------------------------------------------------------|
| **VERZENDEN** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users/{user-id} http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameters om de klant-id en gebruikers-id op te geven.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                              |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------|
| **klant-Tenant-id** | **guid** | J        | De waarde is een **klant-Tenant-id** die de wederverkoper toestaat de resultaten te filteren op een bepaalde klant. |
| **gebruikers-id**            | **guid** | J        | De waarde is een **gebruikers-id** met een GUID-indeling die tot één gebruikers account behoort.                                         |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.

| Naam       | Type   | Vereist | Beschrijving                                                            |
|------------|--------|----------|------------------------------------------------------------------------|
| Staat      | tekenreeks | J        | De gebruikers status. Deze teken reeks moet ' Active ' bevatten om een verwijderde gebruiker te herstellen. |
| Kenmerken | object | N        | Bevat "object type": "CustomerUser".                                 |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 6e668bc0-5bd7-44d6-b6fa-529d41ce9659
MS-CorrelationId: 32be760f-8282-4e01-a37b-829c8a700e8a
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 269
Expect: 100-continue

{
    "State": "active",
    "Attributes": {
        "ObjectType": "CustomerUser"
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert het antwoord de herstelde gebruikers gegevens in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 465
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 32be760f-8282-4e01-a37b-829c8a700e8a
MS-RequestId: 6e668bc0-5bd7-44d6-b6fa-529d41ce9659
MS-CV: ZTeBriO7mEaiM13+.0
MS-ServerId: 101112616
Date: Fri, 20 Jan 2017 22:24:55 GMT

{
    "usageLocation": "US",
    "id": "a45f1416-3300-4f65-9e8d-f123b397a4ea",
    "userPrincipalName": "e83763f7f2204ac384cfcd49f79f2749@dtdemocspcustomer005.onmicrosoft.com",
    "firstName": "Ferdinand",
    "lastName": "Filibuster",
    "displayName": "Ferdinand",
    "userDomainType": "none",
    "state": "active",
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
```
