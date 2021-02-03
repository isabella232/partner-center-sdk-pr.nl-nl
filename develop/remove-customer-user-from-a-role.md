---
title: Een klantgebruiker uit een rol verwijderen
description: Een gebruiker verwijderen uit een directory-rol binnen een klant account.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6253e86f3733bbf2b9c593c5ca3f3e2fccce7c2c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767477"
---
# <a name="remove-a-customer-user-from-a-role"></a>Een klantgebruiker uit een rol verwijderen

**Van toepassing op**

- Partnercentrum

Een gebruiker verwijderen uit een directory-rol binnen een klant account.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u een gebruiker uit een directory-rol wilt verwijderen, selecteert u de klant met de gebruiker die u wilt wijzigen met een aanroep van de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) , geeft u de functie op met behulp van de methode [**DirectoryRoles. ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) met de rol-id van de Directory. Vervolgens opent u de methode [**UserMembers. ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.byid) om de gebruiker te identificeren die moet worden verwijderd en de [**Verwijder**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermember.delete) methode om de gebruiker te verwijderen uit de rol.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedRoleId;
// string selectedUserMemberId;

partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedRoleId).UserMembers.ById(selectedUserMemberId).Delete();
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: RemoveCustomerUserMemberFromDirectoryRole.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode     | Aanvraag-URI                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| **VERWIJDERD** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/directoryroles/{Role-id}/usermembers/{User-ID} http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende URI-para meters om de juiste klant, rol en gebruiker te identificeren.

| Naam                   | Type     | Vereist | Beschrijving                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| **klant-Tenant-id** | **guid** | J        | De waarde is een **klant-Tenant-id** die de klant aanduidt. |
| **rol-id**            | **guid** | J        | De waarde is een GUID-indeling met een **rol-id** waarmee de rol wordt geïdentificeerd.                |
| **gebruikers-id**            | **guid** | J        | De waarde is een **gebruikers-id** met een GUID-indeling waarmee één gebruikers account wordt geïdentificeerd.   |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04%20/directoryroles/729827e3-9c14-49f7-bb1b-9608f156bbb8/usermembers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04%20 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0a00ec08-6273-46bb-ab6f-14a13959b381
MS-CorrelationId: 87d18a45-81fc-40cf-921a-b91cb82d67fe
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 0
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als de gebruiker is verwijderd uit de rol, is de antwoord tekst leeg.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
MS-RequestId: e784d7aa-8c8d-45ee-8f97-9e09823d7338
MS-CV: es01VX8do0u2aTXw.0
MS-ServerId: 101112616
Date: Tue, 20 Dec 2016 23:16:35 GMT
```
