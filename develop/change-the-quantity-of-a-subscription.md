---
title: De hoeveelheid van een abonnement wijzigen
description: Meer informatie over het gebruik Partner Center API's om het aantal licenties voor een klantabonnement te wijzigen. U kunt dit ook doen in het Partner Center dashboard.
ms.date: 02/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 85048dbbdc605f46c12c00484961fbb3068c4f16
ms.sourcegitcommit: 3ee00d9fe9da6b9df0fb7027ae506e2abe722770
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2021
ms.locfileid: "129417233"
---
# <a name="change-the-quantity-of-licenses-in-a-customer-subscription"></a>Het aantal licenties in een klantabonnement wijzigen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Werkt een [abonnement bij](subscription-resources.md) om het aantal licenties te verhogen of te verlagen.

In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst [een klant te selecteren.](get-a-customer-by-name.md) Selecteer vervolgens het abonnement in kwestie dat u een andere naam wilt geven. Als u wilt voltooien, wijzigt u de waarde in **het veld Hoeveelheid** en selecteert u vervolgens **Verzenden.**

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een abonnements-id.

## <a name="c"></a>C\#

Als u de hoeveelheid van het abonnement van een klant wilt wijzigen, moet u eerst [het](get-a-subscription-by-id.md)abonnement op halen en vervolgens de eigenschap [**Quantity van het abonnement**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.quantity) wijzigen. Zodra de wijziging is aangebracht, gebruikt u de **verzameling IAggregatePartner.Customers** en roept u de **methode ById()** aan. Roep vervolgens de [**eigenschap Abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de [**methode ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) Vervolgens roept u de methode **Patch()** aan.

``` csharp
// IAggregatePartner partnerOperations;
// var customerId;
// var subscriptionId;

//retrieving the subscription, for the purpose of the sample
ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.Get();
Subscription selectedSubscription = customerSubscriptions.Items.FirstOrDefault(sub => sub.Status == SubscriptionStatus.Active);

//update selected subscription,
selectedSubscription.Quantity++;

var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project:** PartnerSDK.FeatureSample-klasse: UpdateSubscription.cs 

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode    | Aanvraag-URI                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Deze tabel bevat de vereiste queryparameter om de hoeveelheid van het abonnement te wijzigen.

| Naam                    | Type     | Vereist | Beschrijving                               |
|-------------------------|----------|----------|-------------------------------------------|
| **customer-tenant-id**  | **guid** | J        | Een GUID die overeenkomt met de klant.     |
| **subscription-id** | **guid** | J        | Een GUID die overeenkomt met het abonnement. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Een volledige **abonnementsresource** is vereist in de aanvraag body. Zorg ervoor dat **de eigenschap Quantity** is bijgewerkt.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
    "FriendlyName": "nickname",
    "Quantity": 2,
    "UnitType": "none",
    "ParentSubscriptionId": null,
    "CreationDate": "2015-11-25T06:41:12Z",
    "EffectiveStartDate": "2015-11-24T08:00:00Z",
    "CommitmentEndDate": "2016-12-12T08:00:00Z",
    "Status": "active",
    "AutoRenewEnabled": false,
    "BillingType": "none",
    "PartnerId": null,
    "ContractType": "subscription",
    "OrderId": "6183db3d-6318-4e52-877e-25806e4971be",
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "Subscription"
    }
}
```

### <a name="request-example-for-new-commerce-subscription-to-reduce-quantity"></a>Voorbeeld aanvragen voor een nieuw commerce-abonnement om de hoeveelheid te verminderen

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de technical preview van de nieuwe commerce-ervaring M365/D365.

Het aantal licenties kan slechts binnen 72 uur na aankoop of verlenging van een abonnement worden verlaagd. Licenties die tijdens de tussentijdse termijn worden toegevoegd, kunnen ook slechts binnen 72 uur worden verlaagd, alleen via klantondersteuning.

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscription-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "id": "a4c1340d-6911-4758-bba3-0c4c6007d161",
    "offerId": "CFQ7TTC0LH18:0001:CFQ7TTC0K971",
    "offerName": "Microsoft 365 Business Basic",
    "friendlyName": "Microsoft 365 Business Basic",
    "productType": {
        "id": "OnlineServicesNCE",
        "displayName": "OnlineServicesNCE"
    },
    "quantity": 1, // original value = 10
    "unitType": "Licenses",
    "hasPurchasableAddons": false,
    "creationDate": "2021-01-14T16:57:15.0966728Z",
    "effectiveStartDate": "2021-01-14T16:57:14.498252Z",
    "commitmentEndDate": "2022-01-13T00:00:00Z",
    "status": "active", 
    "autoRenewEnabled": true, 
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1Y",
    "renewalTermDuration": "",
    "refundOptions": [
        {
            "type": "Full",
            "expiresAt": "2021-01-15T00:00:00Z"
        }
    ],
    "isMicrosoftProduct": true,
    "partnerId": "",
    "attentionNeeded": false,
    "actionTaken": false,
    "contractType": "subscription",
    "links": {
        "product": {
            "uri": "/products/CFQ7TTC0LH18?country=US",
            "method": "GET",
            "headers": []
        },
        "sku": {
            "uri": "/products/CFQ7TTC0LH18/skus/0001?country=US",
            "method": "GET",
            "headers": []
        },
        "availability": {
            "uri": "/products/CFQ7TTC0LH18/skus/0001/availabilities/CFQ7TTC0K971?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/d8202a51-69f9-4228-b900-d0e081af17d7/subscriptions/a4c1340d-6911-4758-bba3-0c4c6007d161",
            "method": "GET",
            "headers": []
        }
    },
    "publisherName": "Microsoft Corporation",
    "orderId": "34b37d7340cc",
    "attributes": {
        "objectType": "Subscription"
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een **HTTP-statuscode 200** en [bijgewerkte](subscription-resources.md)  eigenschappen van abonnementsresources in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord retourneert een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende foutopsporingsinformatie. Gebruik een hulpprogramma voor netwerk traceer om de statuscode, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

Wanneer de patchbewerking langer duurt dan de verwachte tijd, verzendt de Partner Center een **HTTP-statuscode 202** en een locatieheader die wijst naar waar het abonnement moet worden opgehaald. U kunt periodiek een query uitvoeren op het abonnement om de status- en hoeveelheidswijzigingen te controleren.

### <a name="response-examples"></a>Antwoordvoorbeelden

#### <a name="response-example-1"></a>Voorbeeld van #1

Geslaagde aanvraag met een **HTTP-statuscode 200:**

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscriptionID> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-Contract-Version: v1
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
    "FriendlyName": "nickname",
    "Quantity": 2,
    "UnitType": "none",
    "ParentSubscriptionId": null,
    "CreationDate": "2015-11-25T06:41:12Z",
    "EffectiveStartDate": "2015-11-24T08:00:00Z",
    "CommitmentEndDate": "2016-12-12T08:00:00Z",
    "Status": "active",
    "AutoRenewEnabled": false,
    "BillingType": "none",
    "PartnerId": null,
    "ContractType": "subscription",
    "Links": {
        "Offer": {
            "Uri": "/v1/offers/0CCA44D6-68E9-4762-94EE-31ECE98783B9",
            "Method": "GET",
            "Headers": []
        },
        "Entitlement": {
            "Uri": "/entitlements?key=<key>",
            "Method": "GET",
            "Headers": []
        },
        "Self": {
            "Uri": "/subscriptions?key=<key>",
            "Method": "GET",
            "Headers": []
        }
    },
    "OrderId": "6183db3d-6318-4e52-877e-25806e4971be",
    "Attributes": {
        "Etag": "<etag>",
        "ObjectType": "Subscription"
    }
}
```

#### <a name="response-example-2"></a>Voorbeeld van #2

Geslaagde aanvraag met een **HTTP-statuscode 202:**

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscriptionID> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 01880c1b-1966-40f0-d470-501a66d9948b
MS-CorrelationId: 2c5827c1-d5f9-4835-cc6d-f1918b782c79
Content-Type: application/json
Content-Length: 1432
Connection: Keep-Alive
Location: /customers/<customer-tenant-id>/subscriptions/<subscriptionID>
```

#### <a name="response-example-for-new-commerce-license-reduction"></a>Voorbeeld van een reactie voor het verminderen van de licentie voor nieuwe commerce

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de technical preview van de nieuwe commerce-ervaring M365/D365.

Voorbeeld van een API-reactie wanneer wordt geprobeerd de licentiehoeveelheden voor nieuwe commerce-abonnementen te verminderen buiten het annuleringsvenster van 72 uur.

```http
{
    "code": 800090,
    "description": "Subscription quantity cannot be decreased.",
    "data": [],
    "source": "PartnerFD"
}
```

