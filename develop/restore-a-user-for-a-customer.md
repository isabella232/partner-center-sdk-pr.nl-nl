---
title: Een verwijderde gebruiker voor een klant herstellen
description: Een verwijderde gebruiker herstellen op klant-id en gebruikers-id.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 23caf91c6b29b292c2638b4a1ad208c606c47492
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445711"
---
# <a name="restore-a-deleted-user-for-a-customer"></a>Een verwijderde gebruiker voor een klant herstellen

Een verwijderde gebruiker herstellen op **klant-id** en gebruikers-id.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- De gebruikers-id. Zie Verwijderde gebruikers weergeven voor een klant als u niet over de gebruikers-id [hebt.](view-a-deleted-user.md)

## <a name="when-can-you-restore-a-deleted-user-account"></a>Wanneer kunt u een verwijderd gebruikersaccount herstellen?

De gebruikerstoestand wordt ingesteld op 'inactief' wanneer u een gebruikersaccount verwijdert. Dit blijft 30 dagen zo, waarna het gebruikersaccount en de bijbehorende gegevens worden verwijderd en onherkenbaar worden gemaakt. U kunt een verwijderd gebruikersaccount alleen herstellen tijdens dit venster van 30 dagen. Zodra het gebruikersaccount is verwijderd en als 'inactief' is gemarkeerd, wordt het niet meer geretourneerd als lid van de gebruikersverzameling (bijvoorbeeld met Een lijst met alle gebruikersaccounts voor een [klant ophalen).](get-a-list-of-all-user-accounts-for-a-customer.md)

## <a name="c"></a>C\#

Als u een gebruiker wilt herstellen, maakt u een nieuw exemplaar van de klasse [**CustomerUser**](/dotnet/api/microsoft.store.partnercenter.models.users.customeruser) en stelt u de waarde van de eigenschap [**User.State**](/dotnet/api/microsoft.store.partnercenter.models.users.user.state) in [**op UserState.Active.**](/dotnet/api/microsoft.store.partnercenter.models.users.userstate)

U herstelt een verwijderde gebruiker door de status van de gebruiker in te stellen op actief. U hoeft de resterende velden in de gebruikersresource niet opnieuw in tepopuleren. Deze waarden worden automatisch hersteld vanuit de verwijderde, inactieve gebruikersresource. Gebruik vervolgens de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren en de [**methode Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om de gebruiker te identificeren.

Roep ten slotte de [**patchmethode aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.patch) en geef het **CustomerUser-exemplaar** door om de aanvraag voor het herstellen van de gebruiker te verzenden.

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

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: CustomerUserRestore.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode    | Aanvraag-URI                                                                                            |
|-----------|--------------------------------------------------------------------------------------------------------|
| **Patch** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameters om de klant-id en gebruikers-id op te geven.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                              |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | **guid** | J        | De waarde is een in GUID **opgemaakte klant-tenant-id** waarmee de reseller de resultaten kan filteren op een bepaalde klant. |
| **user-id**            | **guid** | J        | De waarde is een guid-opgemaakte **gebruikers-id** die bij één gebruikersaccount hoort.                                         |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.

| Naam       | Type   | Vereist | Beschrijving                                                            |
|------------|--------|----------|------------------------------------------------------------------------|
| Staat      | tekenreeks | J        | De gebruikerstoestand. Als u een verwijderde gebruiker wilt herstellen, moet deze tekenreeks 'actief' bevatten. |
| Kenmerken | object | N        | Bevat 'ObjectType': 'CustomerUser'.                                 |

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

Als dit lukt, retourneert het antwoord de herstelde gebruikersgegevens in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
