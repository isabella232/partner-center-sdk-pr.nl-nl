---
title: De factureringscyclus wijzigen
description: Meer informatie over het bijwerken van een klantabonnement naar maandelijkse of jaarlijkse facturering met behulp Partner Center API's. U kunt dit ook doen vanuit het Partner Center dashboard.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: 435309229e2cb038c936028943f4c2cf27b032a7
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974111"
---
# <a name="change-a-customer-subscription-billing-cycle"></a>Factureringscyclus van een klantabonnement wijzigen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Werkt een [order bij](order-resources.md) van maandelijkse naar jaarlijkse facturering of van jaarlijkse naar maandelijkse facturering.

In het Partner Center dashboard kunt u deze bewerking uitvoeren door te navigeren naar de pagina met abonnementsgegevens van een klant. Daar ziet u een optie voor het definiëren van de huidige factureringscyclus voor het abonnement met de mogelijkheid om deze te wijzigen en te verzenden.

**Buiten het bereik** van dit artikel:

- De factureringscyclus voor proefversies wijzigen
- De factureringscycli wijzigen voor niet-jaarlijkse termijnaanbiedingen (maandelijks, zes jaar) & Azure-abonnementen
- De factureringscycli voor inactieve abonnementen wijzigen
- Factureringscycli wijzigen voor Microsoft onlineservices op licenties gebaseerde abonnementen

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een order-id.

## <a name="c"></a>C\#

Als u de frequentie van de factureringscyclus wilt wijzigen, werkt u de [**eigenschap Order.BillingCycle**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.billingcycle#Microsoft_Store_PartnerCenter_Models_Orders_Order_BillingCycle) bij.

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

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode    | Aanvraag-URI                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| **Patch** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Deze tabel bevat de vereiste queryparameter om de hoeveelheid van het abonnement te wijzigen.

| Naam                   | Type | Vereist | Beschrijving                                                          |
|------------------------|------|----------|----------------------------------------------------------------------|
| **customer-tenant-id** | GUID |    J     | Een met GUID **opgemaakte klant-tenant-id** die de klant identificeert |
| **order-id**           | GUID |    J     | De order-id                                                 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In de volgende tabellen worden de eigenschappen in de aanvraag body beschreven.

### <a name="order"></a>Volgorde

| Eigenschap           | Type             | Vereist | Beschrijving                                                                |
|--------------------|------------------|----------|----------------------------------------------------------------------------|
| Id                 | tekenreeks           |    N     | Een order-id die wordt opgegeven wanneer de order is gemaakt |
|ReferenceCustomerId | tekenreeks           |    J     | De klant-id                                                    |
| BillingCycle       | tekenreeks           |    J     | Geeft de frequentie aan waarmee de partner wordt gefactureerd voor deze bestelling. Ondersteunde waarden zijn de ledennamen in [BillingCycleType.](product-resources.md#billingcycletype) |
| Regelitems          | matrix met objecten |    J     | Een matrix met [OrderLineItem-resources](#orderlineitem)                      |
| CreationDate       | datum/tijd         |    N     | De datum waarop de order is gemaakt, in datum/tijd-indeling                        |
| Kenmerken         | Object           |    N     | Bevat "ObjectType": "OrderLineItem"                                     |

### <a name="orderlineitem"></a>OrderLineItem

| Eigenschap             | Type   | Vereist | Beschrijving                                                                        |
|----------------------|--------|----------|------------------------------------------------------------------------------------|
| LineItemNumber       | getal |    J     | Het regelitemnummer, beginnend met 0                                              |
| OfferId              | tekenreeks |    J     | De id van de aanbieding                                                                |
| SubscriptionId       | tekenreeks |    J     | De id van het abonnement                                                         |
| FriendlyName         | tekenreeks |    N     | De gebruiksvriendelijke naam voor het abonnement dat is gedefinieerd door de partner om dubbelzinnigheid te helpen |
| Aantal             | getal |    J     | Het aantal licenties of exemplaren                                                |
| PartnerIdOnRecord    | tekenreeks |    N     | De MPN-id van de recordpartner                                                |
| Kenmerken           | Object |    N     | Bevat "ObjectType": "OrderLineItem"                                             |

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

Als dit lukt, retourneert deze methode de bijgewerkte abonnementsorder in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

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