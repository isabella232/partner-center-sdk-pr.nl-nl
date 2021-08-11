---
title: Een invoegtoepassing voor een abonnement kopen
description: Een invoegaanvoeging aanschaffen voor een bestaand abonnement.
ms.date: 11/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 5227b917faf663c129b1abed1d10318620667e9b47524eb8c91867fb6b453ee8
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997359"
---
# <a name="purchase-an-add-on-to-a-subscription"></a>Een invoegtoepassing voor een abonnement kopen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud for US Government

Een invoegaanvoeging aanschaffen voor een bestaand abonnement.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een abonnements-id. Dit is het bestaande abonnement waarvoor u een invoegaanbieding wilt aanschaffen.

- Een aanbiedings-id die de invoegaankoopaanbieding identificeert.

## <a name="purchasing-an-add-on-through-code"></a>Een invoegproces aanschaffen via code

Wanneer u een invoegaanvoeging voor een abonnement aanschaft, wordt de oorspronkelijke abonnementsorder bijgewerkt met de bestelling voor de invoeg-app. In het volgende is customerId de klant-id, subscriptionId de abonnements-id en addOnOfferId de aanbiedings-id voor de invoeg-on.

Dit zijn de stappen:

1.  Haal een interface op voor de bewerkingen voor het abonnement.

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2.  Gebruik deze interface om een abonnementsobject te instanteren. Hiermee haalt u de details van het bovenliggende abonnement op, inclusief de order-id.

    ``` csharp
    var parentSubscription = subscriptionOperations.Get();
    ```

3.  Een nieuw [**orderobject**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) maken. Dit order-exemplaar wordt gebruikt om de oorspronkelijke order bij te werken die wordt gebruikt om het abonnement aan te schaffen. Voeg een item met één regel toe aan de volgorde die de invoeg-on vertegenwoordigt.
    ``` csharp
    var orderToUpdate = new Order()
    {
        ReferenceCustomerId = customerId,
        LineItems = new List<OrderLineItem>()
        {
            new OrderLineItem()
            {
                LineItemNumber = 0,
                OfferId = addOnOfferId,
                FriendlyName = "Some friendly name",
                Quantity = 2,
                ParentSubscriptionId = subscriptionId
            }
        }
    };
    ```

4.  Werk de oorspronkelijke order voor het abonnement bij met de nieuwe order voor de invoegvoeging.
    ``` csharp
    Order updatedOrder = partnerOperations.Customers.ById(customerId).Orders.ById(parentSubscription.OrderId).Patch(orderToUpdate);
    ```

## <a name="c"></a>C\#

Als u een invoegbewerking wilt aanschaffen, begint u met het verkrijgen van een interface voor de abonnementsbewerkingen door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om de klant te identificeren en de methode [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om het abonnement te identificeren dat de invoegaankoopaanbieding heeft. Gebruik deze [**interface om de**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) abonnementsgegevens op te halen door Get aan te [**roepen.**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get) De abonnementsgegevens bevatten de order-id van de abonnementsorder. Dit is de order die moet worden bijgewerkt met de invoegvoeging.

Vervolgens instantieer u een nieuw [**Order-object**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) en vult u dit met één [**LineItem-exemplaar**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) dat de informatie bevat om de invoeg-on te identificeren, zoals wordt weergegeven in het volgende codefragment. U gebruikt dit nieuwe object om de abonnementsorder bij te werken met de invoeg-on. Roep ten slotte de [**patchmethode**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.patch) aan om de abonnementsorder bij te werken, nadat u eerst de klant hebt identificeert met [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) en de order met [**Orders.ById**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid).

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;
// string addOnOfferId;

// Get an interface to the operations for the subscription.
var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);

// Get the parent subscription details.
var parentSubscription = subscriptionOperations.Get();

// In order to buy an add-on subscription for this offer, we need to patch/update the order through which the base offer was purchased
// by creating an order object with a single line item which represents the add-on offer purchase.
var orderToUpdate = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            LineItemNumber = 0,
            OfferId = addOnOfferId,
            FriendlyName = "Some friendly name",
            Quantity = 2,
            ParentSubscriptionId = subscriptionId
        }
    }
};

// Update the order to apply the add on purchase.
Order updatedOrder = partnerOperations.Customers.ById(customerId).Orders.ById(parentSubscription.OrderId).Patch(orderToUpdate);
```

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: AddSubscriptionAddOn.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode    | Aanvraag-URI                                                                                              |
|-----------|----------------------------------------------------------------------------------------------------------|
| **Patch** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1 |

### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende parameters om de klant en order te identificeren.

| Naam                   | Type     | Vereist | Beschrijving                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| **customer-tenant-id** | **guid** | J        | De waarde is een in GUID **opgemaakte klant-tenant-id** die de klant identificeert. |
| **order-id**           | **guid** | J        | De order-id.                                                              |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In de volgende tabellen worden de eigenschappen in de aanvraag body beschreven.

## <a name="order"></a>Volgorde

| Naam                | Type             | Vereist | Beschrijving                                          |
|---------------------|------------------|----------|------------------------------------------------------|
| Id                  | tekenreeks           | N        | De order-id.                                        |
| ReferenceCustomerId | tekenreeks           | J        | De klant-id.                                     |
| Regelitems           | matrix van objecten | J        | Een matrix van [OrderLineItem-objecten.](#orderlineitem) |
| CreationDate        | tekenreeks           | N        | De datum waarop de order is gemaakt, in datum/tijd-indeling. |
| Kenmerken          | object           | N        | Bevat 'ObjectType': 'Order'.                      |

## <a name="orderlineitem"></a>OrderLineItem

| Naam                 | Type   | Vereist | Beschrijving                                                  |
|----------------------|--------|----------|--------------------------------------------------------------|
| LineItemNumber       | getal | J        | Het regelitemnummer, beginnend met 0.                       |
| OfferId              | tekenreeks | J        | De aanbiedings-id van de invoeg-on.                                  |
| SubscriptionId       | tekenreeks | N        | De id van het aangeschafte invoegabonnement.                 |
| ParentSubscriptionId | tekenreeks | J        | De id van het bovenliggende abonnement dat de invoeg-aanbieding heeft. |
| FriendlyName         | tekenreeks | N        | De gebruiksvriendelijke naam voor dit regelitem.                        |
| Aantal             | getal | J        | Het aantal licenties.                                      |
| PartnerIdOnRecord    | tekenreeks | N        | De MPN-id van de recordpartner.                         |
| Kenmerken           | object | N        | Bevat 'ObjectType': 'OrderLineItem'.                      |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/orders/CF3B0E37-BE0B-4CDD-B584-D1A97D98A922 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 17a2658e-d2cc-439b-a2f0-2aefd9344fbc
MS-CorrelationId: 60efdd24-17ef-4080-9b02-4fc315f916ff
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 414
Expect: 100-continue

{
    "Id": null,
    "ReferenceCustomerId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "SubscriptionId": null,
            "ParentSubscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
            "FriendlyName": "Some friendly name",
            "Quantity": 2,
            "PartnerIdOnRecord": null,
            "Attributes": {
                "ObjectType": "OrderLineItem"
            }
        }
    ],
    "CreationDate": null,
    "Attributes": {
        "ObjectType": "Order"
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode de bijgewerkte abonnementsorder in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie foutcodes voor de [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 1135
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 60efdd24-17ef-4080-9b02-4fc315f916ff
MS-RequestId: 17a2658e-d2cc-439b-a2f0-2aefd9344fbc
MS-CV: WtFy3zI8V0u2lnT9.0
MS-ServerId: 020021921
Date: Wed, 25 Jan 2017 23:01:08 GMT

{
    "id": "cf3b0e37-be0b-4cdd-b584-d1a97d98a922",
    "referenceCustomerId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "billingCycle": "none",
    "lineItems": [{
            "lineItemNumber": 0,
            "offerId": "195416C1-3447-423A-B37B-EE59A99A19C4",
            "subscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
            "friendlyName": "new offer purchase",
            "quantity": 5,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
                    "method": "GET",
                    "headers": []
                }
            }
        }, {
            "lineItemNumber": 1,
            "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "subscriptionId": "968BA1CF-C146-4ADF-A300-308DCF718EEE",
            "friendlyName": "Some friendly name",
            "quantity": 2,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/968BA1CF-C146-4ADF-A300-308DCF718EEE",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2017-01-25T14:53:12.093-08:00",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/orders/cf3b0e37-be0b-4cdd-b584-d1a97d98a922",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "etag": "eyJpZCI6ImNmM2IwZTM3LWJlMGItNGNkZC1iNTg0LWQxYTk3ZDk4YTkyMiIsInZlcnNpb24iOjJ9",
        "objectType": "Order"
    }
}
```
