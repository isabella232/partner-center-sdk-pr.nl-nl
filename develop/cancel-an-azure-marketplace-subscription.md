---
title: Een commerciële marketplace of nieuw commerce-abonnement annuleren
description: Meer informatie over het gebruik Partner Center API's voor het annuleren van een commerciële marketplace of een nieuwe commerce-abonnementsresource die overeenkomt met een klant en abonnements-id.
ms.date: 02/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ed01a26e22fd814b269b6c8d1769da97e8160619
ms.sourcegitcommit: 3ee00d9fe9da6b9df0fb7027ae506e2abe722770
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2021
ms.locfileid: "129417250"
---
# <a name="cancel-a-commercial-marketplace-or-new-commerce-subscription-using-partner-center-apis"></a>Een commerciële marketplace of nieuw commerce-abonnement annuleren met behulp van Partner Center API's

**Van toepassing op**: Partner Center

In dit artikel wordt beschreven hoe u Partner Center API kunt [](subscription-resources.md) gebruiken om een commerciële marketplace of een nieuwe commerce-abonnementsresource te annuleren die overeenkomt met de klant- en abonnements-id.

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de technical preview van de nieuwe commerce-ervaring M365/D365.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze ops zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een abonnements-id.

## <a name="partner-center-dashboard-method"></a>Partner Center-dashboardmethode

Een abonnement op de commerciële marketplace opzeggen in Partner Center dashboard:

1. [Selecteer een klant.](get-a-customer-by-name.md)

2. Selecteer het abonnement dat u wilt annuleren.

3. Kies de **optie Abonnement annuleren** en selecteer vervolgens **Verzenden.**

## <a name="c"></a>C\#

Het abonnement van een klant annuleren:

1. [Haal het abonnement op id op.](get-a-subscription-by-id.md)

2. Wijzig de eigenschap Status van [**het**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) abonnement. Zie [SubscriptionStatus enumeration voor meer informatie over statuscodes.](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus) 

3. Nadat de wijziging is aangebracht, gebruikt u uw **`IAggregatePartner.Customers`** verzameling en roept u de methode **ById()** aan.

4. Roep de [**eigenschap Abonnementen aan,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) gevolgd door de [**methode ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)

5. Roep de **methode Patch()** aan.

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// Subscription selectedSubscription;

selectedSubscription.Status = SubscriptionStatus.Deleted;
var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

### <a name="sample-console-test-app"></a>Voorbeeldconsoletest-app

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project:** PartnerSDK.FeatureSample-klasse: UpdateSubscription.cs 

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode    | Aanvraag-URI                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| **PATCH** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Deze tabel bevat de vereiste queryparameter om het abonnement op te schorten.

| Naam                    | Type     | Vereist | Beschrijving                               |
|-------------------------|----------|----------|-------------------------------------------|
| **customer-tenant-id**  | **guid** | J        | Een GUID die overeenkomt met de klant.     |
| **subscription-id** | **guid** | J        | Een GUID die overeenkomt met het abonnement. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Een volledige **abonnementsresource** is vereist in de aanvraag. Zorg ervoor dat **de eigenschap Status** is bijgewerkt.

### <a name="request-example-for-a-commercial-marketplace-subscription"></a>Voorbeeld aanvragen voor een abonnement op de commerciële marketplace

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscription-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
If-Match: <etag>
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "id": "6e7aa601-629e-461b-8933-0898c3cc3c7c",
    "offerId": "DZH318Z0BXWC:0001:DZH318Z0BMJX",
    "offerName": "offer Name",
    "friendlyName": "friendly Name",
    "quantity": 1,
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "deleted",
    "autoRenewEnabled": false,
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [{
        "type": "Full",
        "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
    }],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "publisherName": "publisher Name",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {"objectType": "Subscription"},
}
```

### <a name="request-example-for-a-new-commerce-subscription"></a>Voorbeeld aanvragen voor een nieuw commerce-abonnement

Nieuwe commerce-abonnementen kunnen binnen 72 uur na aankoop of verlenging worden geannuleerd. Na 72 uur kunnen abonnementen niet meer worden geannuleerd en wordt er door de API een foutmelding weergegeven.


> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de technical preview van de nieuwe commerce-ervaring M365/D365.

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<subscription-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
If-Match: <etag>
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
    "quantity": 1, 
    "unitType": "Licenses",
    "hasPurchasableAddons": false,
    "creationDate": "2021-01-14T16:57:15.0966728Z",
    "effectiveStartDate": "2021-01-14T16:57:14.498252Z",
    "commitmentEndDate": "2022-01-13T00:00:00Z",
    "status": "deleted", // original value = “active”
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

Als de aanvraag is geslaagd, retourneert deze methode verwijderde eigenschappen van abonnementsresources in de antwoord-body. [](subscription-resources.md)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 1322
Content-Type: application/json; charset=utf-8
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
X-Locale: en-US

{
    "id": "6e7aa601-629e-461b-8933-0898c3cc3c7c",
    "offerId": "DZH318Z0BXWC:0001:DZH318Z0BMJX",
    "offerName": "offer Name",
    "friendlyName": "friendly Name",
    "quantity": 1,
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "deleted",
    "autoRenewEnabled": false,
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [
        {
            "type": "Full",
            "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
        }
    ],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "links": {
        "product": {
            "uri": "/products/DZH318Z0BXWC?country=US",
            "method": "GET",
            "headers": []
        },
        "sku": {
            "uri": "/products/DZH318Z0BXWC/skus/0001?country=US",
            "method": "GET",
            "headers": []
        },
        "availability": {
            "uri": "/products/DZH318Z0BXWC/skus/0001/availabilities/DZH318Z0BMJX?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/5921f00a-32c0-4457-aaa1-e8018c650895/subscriptions/6e7aa601-629e-461b-8933-0898c3cc3c7c",
            "method": "GET",
            "headers": []
        }
    },
    "publisherName": "publishe rName",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {
        "etag": "",
        "objectType": "Subscription"
    }
}
```
