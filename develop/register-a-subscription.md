---
title: Een abonnement registreren
description: Registreer een bestaand abonnement zodat het is ingeschakeld voor het bestellen van Azure-reserveringen.
ms.date: 07/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4ea2183ab0c2367c7772bdf40b5988c2b7eff7c539686760332bec4addda8bbe
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997189"
---
# <a name="register-a-subscription"></a>Een abonnement registreren

Registreer een bestaand [abonnement](subscription-resources.md) zodat dit is ingeschakeld voor het bestellen van Azure-reserveringen.

Als u een Azure-reservering wilt aanschaffen, moet u ten minste één bestaand CSP Azure-abonnement hebben. Met deze methode kunt u uw bestaande CSP Azure-abonnement registreren en het inschakelen voor het kopen van Azure-reserveringen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een abonnements-id.

## <a name="c"></a>C\#

Als u het abonnement van een klant wilt registreren, haalt u een interface op voor abonnementsbewerkingen door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om de klant te identificeren. Roep vervolgens de [**methode Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) aan met de abonnements-id om het abonnement te identificeren dat u registreert.

Roep ten slotte de **methode Registration.Register()** aan om het abonnement te registreren en een URI op te halen die kan worden gebruikt om de registratiestatus van het abonnement op te halen. Zie Registratiestatus van abonnement verkrijgen [voor meer informatie.](get-subscription-registration-status.md)

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve the subscription registration details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).Registration.Register();
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode    | Aanvraag-URI                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| **Verzenden**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrations HTTP/1.1 |

### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende padparameters om de klant en het abonnement te identificeren.

| Naam                    | Type       | Vereist | Beschrijving                                                   |
|-------------------------|------------|----------|---------------------------------------------------------------|
| customer-id             | tekenreeks     | Yes      | Een tekenreeks met GUID-indeling die de klant identificeert.         |
| subscription-id         | tekenreeks     | Yes      | Een tekenreeks met GUID-indeling die het abonnement identificeert.     |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

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

Als dit lukt, bevat het antwoord een **Location-header** met een URI die kan worden gebruikt om de registratiestatus van het abonnement op te halen. Sla deze URI op voor gebruik met andere gerelateerde REST API's. Zie Registratiestatus van abonnement ophalen voor een voorbeeld van het ophalen [van de status.](get-subscription-registration-status.md)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

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
