---
title: Een invoegtoepassing voor een abonnement kopen
description: Een invoeg toepassing aanschaffen bij een bestaand abonnement.
ms.date: 11/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 975a2516bccdc6274bfec5d6a3286a649fc4f808
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767480"
---
# <a name="purchase-an-add-on-to-a-subscription"></a>Een invoegtoepassing voor een abonnement kopen

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud for US Government

Een invoeg toepassing aanschaffen bij een bestaand abonnement.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een abonnements-ID. Dit is het bestaande abonnement waarvoor u een add-on-aanbieding wilt aanschaffen.

- Een aanbiedings-ID waarmee de aanbieding van de invoeg toepassing wordt geïdentificeerd om te worden gekocht.

## <a name="purchasing-an-add-on-through-code"></a>Een invoeg toepassing kopen via code

Wanneer u een invoeg toepassing aan een abonnement aanschaft, werkt u de oorspronkelijke abonnements volgorde bij met de volg orde voor de invoeg toepassing. In het volgende het veld customerId is de klant-ID, subscriptionId de abonnements-ID is en addOnOfferId is de aanbiedings-ID voor de invoeg toepassing.

Dit zijn de stappen:

1.  Een interface ophalen voor de bewerkingen voor het abonnement.

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2.  Deze interface gebruiken om een abonnements object te instantiëren. Hiermee krijgt u de details van het bovenliggende abonnement, inclusief de order-id.

    ``` csharp
    var parentSubscription = subscriptionOperations.Get();
    ```

3.  Een nieuw [**order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object instantiëren. Deze order instantie wordt gebruikt om de oorspronkelijke volg orde bij te werken die wordt gebruikt om het abonnement aan te schaffen. Voeg één regel item toe aan de volg orde waarin de invoeg toepassing wordt vertegenwoordigd.
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

4.  Werk de oorspronkelijke volg orde voor het abonnement bij met de nieuwe volg orde voor de invoeg toepassing.
    ``` csharp
    Order updatedOrder = partnerOperations.Customers.ById(customerId).Orders.ById(parentSubscription.OrderId).Patch(orderToUpdate);
    ```

## <a name="c"></a>C\#

Als u een invoeg toepassing wilt kopen, moet u eerst een interface aan de abonnements bewerkingen verkrijgen door de [**IAggregatePartner. Customers. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met de klant-id om de klant te identificeren, en de methode [**abonnementen. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om het abonnement te identificeren dat de invoeg toepassing biedt. Gebruik die [**Interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) om de abonnements gegevens op te halen door [**Get aan**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get)te roepen. Waarom hebt u de abonnements gegevens nodig? Omdat u de order-id van de abonnements order nodig hebt. Dat is de volg orde waarin de invoeg toepassing moet worden bijgewerkt.

Vervolgens moet u een nieuw [**order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object instantiëren en dit vullen met een enkel [**LineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) -exemplaar dat de informatie bevat om de invoeg toepassing te identificeren, zoals wordt weer gegeven in het volgende code fragment. U gebruikt dit nieuwe object om de abonnements volgorde bij te werken met de invoeg toepassing. Ten slotte roept u de [**patch**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.patch) -methode aan om de abonnements volgorde bij te werken, nadat u de klant eerst hebt geïdentificeerd met [**IAggregatePartner. klanten. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) en de order met [**Orders. ById**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid).

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

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: AddSubscriptionAddOn.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode    | Aanvraag-URI                                                                                              |
|-----------|----------------------------------------------------------------------------------------------------------|
| **VERZENDEN** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/orders/{order-id} http/1.1 |

### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende para meters om de klant en order te identificeren.

| Naam                   | Type     | Vereist | Beschrijving                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| **klant-Tenant-id** | **guid** | J        | De waarde is een **klant-Tenant-id** die de klant aanduidt. |
| **order-id**           | **guid** | J        | De order-id.                                                              |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In de volgende tabellen worden de eigenschappen in de hoofd tekst van de aanvraag beschreven.

## <a name="order"></a>Volgorde

| Naam                | Type             | Vereist | Beschrijving                                          |
|---------------------|------------------|----------|------------------------------------------------------|
| Id                  | tekenreeks           | N        | De order-ID.                                        |
| ReferenceCustomerId | tekenreeks           | J        | De klant-ID.                                     |
| Regel items           | matrix van objecten | J        | Een matrix met [OrderLineItem](#orderlineitem) -objecten. |
| CreationDate        | tekenreeks           | N        | De datum waarop de order is gemaakt, in datum-tijd notatie. |
| Kenmerken          | object           | N        | Bevat "object type": "order".                      |

## <a name="orderlineitem"></a>OrderLineItem

| Naam                 | Type   | Vereist | Beschrijving                                                  |
|----------------------|--------|----------|--------------------------------------------------------------|
| LineItemNumber       | getal | J        | Het nummer van het regel item, te beginnen met 0.                       |
| OfferId              | tekenreeks | J        | De aanbiedings-ID van de invoeg toepassing.                                  |
| SubscriptionId       | tekenreeks | N        | De ID van het gekochte abonnement voor de invoeg toepassing.                 |
| ParentSubscriptionId | tekenreeks | J        | De ID van het bovenliggende abonnement met de invoeg toepassing. |
| FriendlyName         | tekenreeks | N        | De beschrijvende naam voor dit regel item.                        |
| Aantal             | getal | J        | Het aantal licenties.                                      |
| PartnerIdOnRecord    | tekenreeks | N        | De MPN-ID van de partner van de record.                         |
| Kenmerken           | object | N        | Bevat "object type": "OrderLineItem".                      |

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

Als dit lukt, retourneert deze methode de bijgewerkte abonnements volgorde in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.

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
