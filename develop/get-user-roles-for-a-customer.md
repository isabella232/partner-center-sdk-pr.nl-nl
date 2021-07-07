---
title: Gebruikersrollen voor een klant ophalen
description: Haal een lijst op met alle rollen/machtigingen die zijn gekoppeld aan een gebruikersaccount. Variaties zijn onder andere het verkrijgen van een lijst met alle machtigingen voor alle gebruikersaccounts voor een klant en het verkrijgen van een lijst met gebruikers met een bepaalde rol.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8f58e8b7eae5bb47265bb1ac83fcdcd160f735d2
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445915"
---
# <a name="get-user-roles-for-a-customer"></a>Gebruikersrollen voor een klant ophalen

Haal een lijst op met alle rollen/machtigingen die zijn gekoppeld aan een gebruikersaccount. Variaties zijn onder andere het verkrijgen van een lijst met alle machtigingen voor alle gebruikersaccounts voor een klant en het verkrijgen van een lijst met gebruikers met een bepaalde rol.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u alle directoryrollen voor een opgegeven klant wilt ophalen, haalt u eerst de opgegeven klant-id op. Gebruik vervolgens de verzameling **IAggregatePartner.Customers** en roep de **methode ById()** aan. Roep vervolgens de **eigenschap DirectoryRoles** aan, gevolgd door de **methode Get()** of **GetAsync().**

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var directoryRoles = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.Get();
```

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class:** GetCustomerDirectoryRoles.cs

Als u een lijst met klantgebruikers met een bepaalde rol wilt ophalen, haalt u eerst de opgegeven klant-id en de maprol-id op. Gebruik vervolgens de verzameling **IAggregatePartner.Customers** en roep de **methode ById()** aan. Roep vervolgens de **eigenschap DirectoryRoles** aan, vervolgens de methode **ById()** en vervolgens de eigenschap **UserMembers,** gevolgd door de methode **Get()** of **GetAsync().**

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;
// string selectedDirectoryRoleId;

var userMembers = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedDirectoryRoleId).UserMembers.Get();
```

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project:** Klasse PartnerSDK.FeatureSamples: GetCustomerDirectoryRoleUserMembers.cs 

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id}/directoryroles HTTP/1.1 |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles HTTP/1.1                 |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers    |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de juiste klant te identificeren.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                                                                                                                 |
|------------------------|----------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | **guid** | J        | De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.                                                      |
| **user-id**            | **guid** | N        | De waarde is een guid-opgemaakte **gebruikers-id** die bij één gebruikersaccount hoort.                                                                                                                            |
| **role-id**            | **guid** | N        | De waarde is een **rol-id** met GUID-indeling die bij een type rol hoort. U kunt deze ID's krijgen door een query uit te voeren op alle directoryrollen voor een klant, voor alle gebruikersaccounts. (Het tweede scenario hierboven). |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

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

Als dit lukt, retourneert deze methode een lijst met de rollen die zijn gekoppeld aan het opgegeven gebruikersaccount.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

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
