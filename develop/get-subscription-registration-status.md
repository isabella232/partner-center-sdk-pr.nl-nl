---
title: De registratiestatus van het abonnement ophalen
description: Haal de status op van een abonnement dat is geregistreerd voor gebruik met Azure Reserved VM Instances.
ms.date: 03/19/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0e0a65abba94f1f05a98282fa67ff1d185ba4e082488d2d7887b4e9346c38967
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989658"
---
# <a name="get-subscription-registration-status"></a>De registratiestatus van het abonnement ophalen

De registratiestatus van het abonnement voor een klantabonnement dat is ingeschakeld voor het kopen van Azure Reserved VM Instances.

Als u een gereserveerde VM-instantie van Azure wilt kopen met behulp van Partner Center API, moet u ten minste één bestaand CSP Azure-abonnement hebben. Met [de methode Een abonnement](register-a-subscription.md) registreren kunt u uw bestaande CSP Azure-abonnement registreren en deze inschakelen voor Azure Reserved VM Instances. Met deze methode kunt u de status van die registratie ophalen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een abonnements-id.

## <a name="c"></a>C\#

Als u de registratiestatus van een abonnement wilt weten, gebruikt u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren. Haal vervolgens een interface op voor abonnementsbewerkingen door de [**methode Subscription.ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) aan te roepen met de abonnements-id om het abonnement te identificeren. Gebruik vervolgens de eigenschap RegistrationStatus om een interface te verkrijgen voor de registratiestatusbewerkingen van het huidige abonnement en roep de methode **Get** of **GetAsync** aan om het object **SubscriptionRegistrationStatus op te** halen.

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId;
// var selectedSubscriptionId;

// Retrieve a subscription's registration status details.
var subscriptionRegistrationDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).RegistrationStatus.Get();
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode    | Aanvraag-URI                                                                                                                        |
|-----------|------------------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/registrationstatus HTTP/1.1 |

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

Als dit lukt, bevat de antwoord-body een [resource SubscriptionRegistrationStatus.](subscription-resources.md#subscriptionregistrationstatus)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

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
