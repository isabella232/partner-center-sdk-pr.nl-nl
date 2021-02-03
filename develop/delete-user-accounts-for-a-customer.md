---
title: Een gebruikersaccount voor een klant verwijderen
description: Een bestaand gebruikers account voor een klant verwijderen.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 77fc1a1c7264779ca549be8d52798e90c91138bb
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767388"
---
# <a name="delete-a-user-account-for-a-customer"></a>Een gebruikersaccount voor een klant verwijderen

**Van toepassing op:**

- Partnercentrum

In dit artikel wordt uitgelegd hoe u een bestaand gebruikers account voor een klant verwijdert.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een gebruikers-ID. Als u de gebruikers-ID niet hebt, raadpleegt u [een lijst met alle gebruikers accounts voor een klant ophalen](get-a-list-of-all-user-accounts-for-a-customer.md).

## <a name="deleting-a-user-account"></a>Een gebruikers account verwijderen

Wanneer u een gebruikers account verwijdert, wordt de gebruikers status op dertig dagen ingesteld op **inactief** . Na dertig dagen worden het gebruikers account en de bijbehorende gegevens verwijderd en onherstelbaar gemaakt.

U kunt [een verwijderd gebruikers account voor een klant herstellen](restore-a-user-for-a-customer.md) als het inactieve account zich in het venster van dertig dagen bevindt. Wanneer u echter een account herstelt dat is verwijderd en als inactief is gemarkeerd, wordt het account niet langer geretourneerd als lid van de gebruikers verzameling (bijvoorbeeld wanneer u [een lijst met alle gebruikers accounts voor een klant krijgt](get-a-list-of-all-user-accounts-for-a-customer.md)).

## <a name="c"></a>C\#

Een bestaand gebruikers account van de klant verwijderen:

1. Gebruik de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.

2. Roep de [**gebruikers. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) -methode aan om de gebruiker te identificeren.

3. Roep de [**verwijderings**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) methode aan om de gebruiker te verwijderen en stel de gebruikers status in op inactief.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string customerUserIdToDelete;

partnerOperations.Customers.ById(selectedCustomerId).Users.ById(customerUserIdToDelete).Delete();
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: DeleteCustomerUser.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode     | Aanvraag-URI                                                                                            |
|------------|--------------------------------------------------------------------------------------------------------|
| DELETE     | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users/{user-id} http/1.1 |

#### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende query parameters om de klant en gebruiker te identificeren.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                               |
|------------------------|----------|----------|---------------------------------------------------------------------------------------------------------------------------|
| klant-Tenant-id     | GUID     | J        | De waarde is een **klant-Tenant-id** van de GUID-indeling waarmee de wederverkoper de resultaten voor een bepaalde klant kan filteren. |
| user-id                | GUID     | J        | De waarde is een **gebruikers-id** met een GUID-indeling die tot één gebruikers account behoort.                                          |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als deze methode is geslaagd, wordt de status code van **204 geen inhoud** geretourneerd.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CV: 90KUJA7HKEaG8wHu.0
MS-ServerId: 101112616
Date: Tue, 24 Jan 2017 23:27:18 GMT
```
