---
title: Een gebruikersaccount voor een klant verwijderen
description: Een bestaand gebruikersaccount voor een klant verwijderen.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c45646da43b8926f911942374de5da07f318c526
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973057"
---
# <a name="delete-a-user-account-for-a-customer"></a>Een gebruikersaccount voor een klant verwijderen

In dit artikel wordt uitgelegd hoe u een bestaand gebruikersaccount voor een klant verwijdert.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een gebruikers-id. Zie Get a list of all user accounts for a customer (Een lijst met alle gebruikersaccounts voor een klant opmaken) als u niet over de [gebruikers-id hebt.](get-a-list-of-all-user-accounts-for-a-customer.md)

## <a name="deleting-a-user-account"></a>Een gebruikersaccount verwijderen

Wanneer u een gebruikersaccount verwijdert, wordt de gebruikerstoestand ingesteld op **inactief** voor 30 dagen. Na dertig dagen worden het gebruikersaccount en de bijbehorende gegevens verwijderd en onherkenbaar gemaakt.

U kunt [een verwijderd gebruikersaccount voor een](restore-a-user-for-a-customer.md) klant herstellen als het inactieve account binnen het venster van 30 dagen valt. Wanneer u echter een account herstelt dat is verwijderd en gemarkeerd als inactief, wordt het account niet meer geretourneerd als lid van de gebruikersverzameling (bijvoorbeeld wanneer u een lijst met alle gebruikersaccounts voor een klant [krijgt).](get-a-list-of-all-user-accounts-for-a-customer.md)

## <a name="c"></a>C\#

Een bestaand klantgebruikersaccount verwijderen:

1. Gebruik de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.

2. Roep de [**methode Users.ById aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om de gebruiker te identificeren.

3. Roep de [**methode Delete**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) aan om de gebruiker te verwijderen en de gebruikerstoestand in te stellen op inactief.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string customerUserIdToDelete;

partnerOperations.Customers.ById(selectedCustomerId).Users.ById(customerUserIdToDelete).Delete();
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK **Voorbeeldklasse:** DeleteCustomerUser.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode     | Aanvraag-URI                                                                                            |
|------------|--------------------------------------------------------------------------------------------------------|
| DELETE     | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende queryparameters om de klant en gebruiker te identificeren.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                               |
|------------------------|----------|----------|---------------------------------------------------------------------------------------------------------------------------|
| customer-tenant-id     | GUID     | J        | De waarde is een **klant-tenant-id** in GUID-indeling waarmee de reseller de resultaten voor een bepaalde klant kan filteren. |
| user-id                | GUID     | J        | De waarde is een gebruikers-id in **GUID-indeling** die bij één gebruikersaccount hoort.                                          |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

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

Als dit lukt, retourneert deze methode de statuscode **204 Geen** inhoud.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center de volledige lijst.](error-codes.md)

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
