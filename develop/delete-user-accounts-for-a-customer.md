---
title: Een gebruikersaccount voor een klant verwijderen
description: Een bestaand gebruikersaccount voor een klant verwijderen.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 64e9175a2a4545022175b326a2d765ecd6a1106242b8926fe19e32c7e2ab6ec2
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994877"
---
# <a name="delete-a-user-account-for-a-customer"></a>Een gebruikersaccount voor een klant verwijderen

In dit artikel wordt uitgelegd hoe u een bestaand gebruikersaccount voor een klant verwijdert.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een gebruikers-id. Zie Get a list of all user accounts for a customer (Een lijst met alle gebruikersaccounts voor een klant opmaken) als u niet over de [gebruikers-id hebt.](get-a-list-of-all-user-accounts-for-a-customer.md)

## <a name="deleting-a-user-account"></a>Een gebruikersaccount verwijderen

Wanneer u een gebruikersaccount verwijdert, wordt de gebruikerstoestand ingesteld op **inactief** voor 30 dagen. Na dertig dagen worden het gebruikersaccount en de bijbehorende gegevens verwijderd en onherkenbaar gemaakt.

U kunt [een verwijderd gebruikersaccount voor een](restore-a-user-for-a-customer.md) klant herstellen als het inactieve account binnen het venster van 30 dagen valt. Wanneer u echter een account herstelt dat is verwijderd en gemarkeerd als inactief, wordt het account niet meer geretourneerd als lid van de gebruikersverzameling (bijvoorbeeld wanneer u een lijst met alle gebruikersaccounts voor een klant [krijgt).](get-a-list-of-all-user-accounts-for-a-customer.md)

## <a name="c"></a>C\#

Een bestaand gebruikersaccount van de klant verwijderen:

1. Gebruik de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.

2. Roep de [**methode Users.ById aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om de gebruiker te identificeren.

3. Roep de [**methode Delete**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) aan om de gebruiker te verwijderen en stel de gebruikerstoestand in op inactief.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string customerUserIdToDelete;

partnerOperations.Customers.ById(selectedCustomerId).Users.ById(customerUserIdToDelete).Delete();
```

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: DeleteCustomerUser.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode     | Aanvraag-URI                                                                                            |
|------------|--------------------------------------------------------------------------------------------------------|
| DELETE     | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende queryparameters om de klant en gebruiker te identificeren.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                               |
|------------------------|----------|----------|---------------------------------------------------------------------------------------------------------------------------|
| customer-tenant-id     | GUID     | J        | De waarde is een in GUID **opgemaakte klant-tenant-id** waarmee de reseller de resultaten voor een bepaalde klant kan filteren. |
| user-id                | GUID     | J        | De waarde is een gebruikers-id met **GUID-indeling** die bij één gebruikersaccount hoort.                                          |

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

Als dit lukt, retourneert deze methode de statuscode Geen inhoud **204.**

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
