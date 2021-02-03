---
title: De factureringscyclus wijzigen
description: Meer informatie over hoe u een klant abonnement bijwerkt naar een maandelijks of jaarlijks factuurt met behulp van partner Center-Api's. U kunt dit ook doen via het dash board van de partner centrum.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: 8a2879db061ced799e29d84e71be5b1259b07689
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767624"
---
# <a name="change-a-customer-subscription-billing-cycle"></a>Een facturerings cyclus voor een klant abonnement wijzigen

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Hiermee wordt een [bestelling](order-resources.md) bijgewerkt van maandelijks naar jaar facturering of van jaarlijkse naar maandelijkse facturering.

In het dash board van de partner centrum kan deze bewerking worden uitgevoerd door te navigeren naar de pagina met abonnements gegevens van een klant. Zodra dit het geval is, ziet u een optie voor het definiëren van de huidige facturerings cyclus voor het abonnement, met de mogelijkheid om deze te wijzigen en in te dienen.

**Buiten het bereik** van dit artikel:

- De facturerings cyclus voor experimenten wijzigen
- Het wijzigen van de facturerings cycli voor aanbiedingen die geen jaar zijn (maandelijks, 6 jaar) & Azure-abonnementen
- De facturerings cycli voor inactieve abonnementen wijzigen
- Facturerings cycli voor micro soft onlineservices op licenties gebaseerde abonnementen wijzigen

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een order-ID.

## <a name="c"></a>C\#

Als u de frequentie van de facturerings cyclus wilt wijzigen, werkt u de eigenschap [**order. BillingCycle**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.billingcycle#Microsoft_Store_PartnerCenter_Models_Orders_Order_BillingCycle) bij.

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string offerId;
// string orderId;

var order = new Order()
{
    ReferenceCustomerId = customerId,
    BillingCycle = BillingCycleType.Annual,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            LineItemNumber = 0,
            OfferId = offerId,
            SubscriptionId = "69829602-C219-40FD-A3D5-4150FCA41A19",
            Quantity = 1
        }
    }
};

var createdOrder = partnerOperations.Customers.ById(customerId).Orders.ById(orderId).Patch(order);
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode    | Aanvraag-URI                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| **VERZENDEN** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/orders/{order-id} http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Deze tabel bevat de vereiste query parameter voor het wijzigen van de hoeveelheid van het abonnement.

| Naam                   | Type | Vereist | Beschrijving                                                          |
|------------------------|------|----------|----------------------------------------------------------------------|
| **klant-Tenant-id** | GUID |    J     | Een in de GUID ingedeelde **klant-Tenant-id** waarmee de klant wordt geïdentificeerd |
| **order-id**           | GUID |    J     | De order-id                                                 |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In de volgende tabellen worden de eigenschappen in de hoofd tekst van de aanvraag beschreven.

### <a name="order"></a>Volgorde

| Eigenschap           | Type             | Vereist | Beschrijving                                                                |
|--------------------|------------------|----------|----------------------------------------------------------------------------|
| Id                 | tekenreeks           |    N     | Een order-id die is opgegeven bij het maken van de order |
|ReferenceCustomerId | tekenreeks           |    J     | De klant-id                                                    |
| BillingCycle       | tekenreeks           |    J     | Hiermee wordt de frequentie aangegeven waarmee de partner voor deze order wordt gefactureerd. Ondersteunde waarden zijn de lidnamen in [BillingCycleType](product-resources.md#billingcycletype). |
| Regel items          | matrix van objecten |    J     | Een matrix met [OrderLineItem](#orderlineitem) -resources                      |
| CreationDate       | datum/tijd         |    N     | De datum waarop de order is gemaakt, in datum-tijd notatie                        |
| Kenmerken         | Object           |    N     | Bevat "object type": "OrderLineItem"                                     |

### <a name="orderlineitem"></a>OrderLineItem

| Eigenschap             | Type   | Vereist | Beschrijving                                                                        |
|----------------------|--------|----------|------------------------------------------------------------------------------------|
| LineItemNumber       | getal |    J     | Het nummer van het regel item, te beginnen met 0                                              |
| OfferId              | tekenreeks |    J     | De ID van de aanbieding                                                                |
| SubscriptionId       | tekenreeks |    J     | De ID van het abonnement                                                         |
| FriendlyName         | tekenreeks |    N     | De beschrijvende naam voor het abonnement dat is gedefinieerd door de partner om dubbel zinnigheid te helpen |
| Aantal             | getal |    J     | Het aantal licenties of exemplaren                                                |
| PartnerIdOnRecord    | tekenreeks |    N     | De MPN-ID van de partner van de record                                                |
| Kenmerken           | Object |    N     | Bevat "object type": "OrderLineItem"                                             |

### <a name="request-example"></a>Voorbeeld van aanvraag

Bijwerken naar jaarlijkse facturering

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
    "BillingCycle" : "Annual",
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "SubscriptionId": "69829602-C219-40FD-A3D5-4150FCA41A19",
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

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

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
    "billingCycle": "Annual",
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
        },
        {
            "lineItemNumber": 1,
            "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "subscriptionId": "69829602-C219-40FD-A3D5-4150FCA41A19",
            "friendlyName": "Some friendly name",
            "quantity": 2,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/69829602-C219-40FD-A3D5-4150FCA41A19",
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