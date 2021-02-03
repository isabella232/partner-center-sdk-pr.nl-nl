---
title: De registratiestatus van het abonnement ophalen
description: De status ophalen van een abonnement dat is geregistreerd voor gebruik met Azure Reserved VM Instances.
ms.date: 03/19/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e06cf8a450d6c281f7f83a68c899d1e5b29e9855
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767544"
---
# <a name="get-subscription-registration-status"></a>De registratiestatus van het abonnement ophalen

**Van toepassing op**

- Partnercentrum

De registratie status van abonnementen ophalen voor een klant abonnement dat is ingeschakeld voor aankoop van Azure Reserved VM Instances.

Als u een voor Azure gereserveerde VM-instantie wilt kopen met de Partner Center API, moet u ten minste één bestaand CSP Azure-abonnement hebben. Met de methode [een abonnement registreren](register-a-subscription.md) kunt u uw bestaande CSP Azure-abonnement registreren, zodat deze kan worden gekocht Azure reserved VM instances. Met deze methode kunt u de status van die registratie ophalen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een abonnements-ID.

## <a name="c"></a>C\#

Als u de registratie status van een abonnement wilt ophalen, begint u met de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren. Vervolgens krijgt u een interface voor abonnements bewerkingen door de methode [**Subscription. ById ()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) aan te roepen met de abonnements-id om het abonnement te identificeren. Vervolgens gebruikt u de eigenschap RegistrationStatus om een interface te verkrijgen voor de registratie status bewerkingen van het huidige abonnement en roept u de methode **Get** of **GetAsync** aan om het **SubscriptionRegistrationStatus** -object op te halen.

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve a subscription's registration status details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).RegistrationStatus.Get();
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode    | Aanvraag-URI                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions/{Subscription-id}/registrationstatus http/1.1 |

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
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-id>/subscriptions/<subscription-id>/registrationstatus HTTP/1.1
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

Als dit lukt, bevat de antwoord tekst een [SubscriptionRegistrationStatus](subscription-resources.md#subscriptionregistrationstatus) -resource.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
MS-CV: InswEQre402koceL.0
MS-ServerId: 030020344

{
    "subscriptionId":"<subscription-id>",
    "status":"NotRegistered",
    "attributes":{
        "objectType":"SubscriptionRegistrationStatus"
    }
}
```
