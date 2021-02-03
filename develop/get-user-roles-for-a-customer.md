---
title: Gebruikersrollen voor een klant ophalen
description: Een lijst ophalen met alle rollen/machtigingen die zijn gekoppeld aan een gebruikers account. Variaties zijn onder andere het ophalen van een lijst met alle machtigingen voor alle gebruikers accounts voor een klant en het ophalen van een lijst met gebruikers die een bepaalde rol hebben.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8dad5c035c08905c3d39052de07ebb912452a16b
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767230"
---
# <a name="get-user-roles-for-a-customer"></a>Gebruikersrollen voor een klant ophalen

**Van toepassing op**

- Partnercentrum

Een lijst ophalen met alle rollen/machtigingen die zijn gekoppeld aan een gebruikers account. Variaties zijn onder andere het ophalen van een lijst met alle machtigingen voor alle gebruikers accounts voor een klant en het ophalen van een lijst met gebruikers die een bepaalde rol hebben.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u alle Directory rollen voor een opgegeven klant wilt ophalen, moet u eerst de opgegeven klant-ID ophalen. Vervolgens gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode **ById ()** aan. Roep vervolgens de eigenschap **DirectoryRoles** aan, gevolgd door de methode **Get ()** of **GetAsync ()**.

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var directoryRoles = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.Get();
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: GetCustomerDirectoryRoles.cs

Als u een lijst met klant gebruikers met een bepaalde rol wilt ophalen, moet u eerst de opgegeven klant-ID en de ID van de Directory-rol ophalen. Vervolgens gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode **ById ()** aan. Roep vervolgens de eigenschap **DirectoryRoles** en vervolgens de methode **ById ()** aan, vervolgens de eigenschap **UserMembers** , gevolgd door de methode **Get ()** of **GetAsync ()** .

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;
// string selectedDirectoryRoleId;

var userMembers = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedDirectoryRoleId).UserMembers.Get();
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: PartnerSDK. FeatureSamples- **klasse**: GetCustomerDirectoryRoleUserMembers.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users/{user-id}/directoryroles http/1.1 |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/directoryroles http/1.1                 |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/directoryroles/{Role-id}/usermembers    |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om de juiste klant te identificeren.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                                                                                                                 |
|------------------------|----------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **klant-Tenant-id** | **guid** | J        | De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.                                                      |
| **gebruikers-id**            | **guid** | N        | De waarde is een **gebruikers-id** met een GUID-indeling die tot één gebruikers account behoort.                                                                                                                            |
| **rol-id**            | **guid** | N        | De waarde is een GUID-indeling met een **rol-id** die tot een type rol behoort. U kunt deze Id's ophalen door de Directory rollen voor een klant te doorzoeken op alle gebruikers accounts. (Het tweede scenario hierboven). |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id>/directoryroles HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
```

## <a name="rest-response"></a>REST-antwoord

Als deze methode is geslaagd, wordt een lijst geretourneerd met de rollen die zijn gekoppeld aan het opgegeven gebruikers account.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST

{
      "totalCount": 2,
      "items": [
        {
          "name": "Helpdesk Administrator",
          "id": "729827e3-9c14-49f7-bb1b-9608f156bbb8",
          "attributes": { "objectType": "DirectoryRole" }
        },
        {
          "name": "User Account Administrator",
          "id": "fe930be7-5e62-47db-91af-98c3a49a38b1",
          "attributes": { "objectType": "DirectoryRole" }
        }
      ],
      "attributes": { "objectType": "Collection" }
}
```
