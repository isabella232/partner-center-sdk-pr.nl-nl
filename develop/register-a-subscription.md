---
title: Een abonnement registreren
description: Registreer een bestaand abonnement zodat het geschikt is voor het best Ellen van Azure-reserve ringen.
ms.date: 07/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9a96bb350f22430c9fd7a1759e336cc9f3ca1939
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767478"
---
# <a name="register-a-subscription"></a>Een abonnement registreren

**Van toepassing op**

- Partnercentrum

Registreer een bestaand [abonnement](subscription-resources.md) zodat het geschikt is voor het best Ellen van Azure-reserve ringen.

Als u een Azure-reserve ring wilt kopen, moet u ten minste één bestaand CSP Azure-abonnement hebben. Met deze methode kunt u uw bestaande CSP Azure-abonnement registreren, zodat het Azure-reserve ringen kan aanschaffen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een abonnements-ID.

## <a name="c"></a>C\#

Als u het abonnement van een klant wilt registreren, haalt u een interface op voor abonnements bewerkingen door de [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met de klant-id om de klant te identificeren. Vervolgens roept u de methode [**Subscription. ById ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) aan met de abonnements-id om het abonnement te identificeren dat u registreert.

Roep ten slotte de methode **Registration. REGI ster ()** aan om het abonnement te registreren en haal een URI op die kan worden gebruikt om de registratie status van het abonnement op te halen. Zie [inschrijvings status van abonnementen ophalen](get-subscription-registration-status.md)voor meer informatie.

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve the subscription registration details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).Registration.Register();
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode    | Aanvraag-URI                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| **Verzenden**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions/{Subscription-id}/Registrations http/1.1 |

### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende Path-para meters om de klant en het abonnement te identificeren.

| Naam                    | Type       | Vereist | Beschrijving                                                   |
|-------------------------|------------|----------|---------------------------------------------------------------|
| klant-id             | tekenreeks     | Yes      | Een teken reeks met een GUID-indeling die de klant identificeert.         |
| abonnement-id         | tekenreeks     | Yes      | Een teken reeks met een GUID-indeling waarmee het abonnement wordt geïdentificeerd.     |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-id>/subscriptions/<subscription-id>/registrations HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als dit is gelukt, bevat het antwoord een **locatie** header met een URI die kan worden gebruikt om de registratie status van het abonnement op te halen. Sla deze URI op voor gebruik met andere verwante REST Api's. Zie [inschrijvings status van abonnementen ophalen](get-subscription-registration-status.md)voor een voor beeld van het ophalen van de status.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/<customer-id>/subscriptions/<subscription-id>/registrationstatus
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
```
