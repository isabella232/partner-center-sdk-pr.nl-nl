---
title: Klantorder voor indirecte reseller maken
description: Meer informatie over het gebruik Partner Center API's om een order te maken voor een klant van een indirecte reseller. Het artikel bevat vereisten, stappen en voorbeelden.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ba46b151e423df27f1378ac8441a23702e47746911b4e05e370bbf0aa7b53233
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991545"
---
# <a name="create-an-order-for-a-customer-of-an-indirect-reseller"></a>Een bestelling maken voor een klant van een indirecte reseller

Een order maken voor een klant van een indirecte reseller.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- De aanbiedings-id van het item dat moet worden gekocht.

- De tenant-id van de indirecte reseller.

## <a name="c"></a>C\#

Een order maken voor een klant van een indirecte reseller:

1. Haal een verzameling van de indirecte resellers op die een relatie hebben met de aangemelde partner.

2. Haal een lokale variabele op voor het item in de verzameling dat overeenkomt met de indirecte reseller-id. Met deze stap krijgt u toegang tot de [**mpnId-eigenschap**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationship.mpnid) van de reseller wanneer u de order maakt.

3. Instantieer een [**Order-object**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) en stel de eigenschap [**ReferenceCustomerID**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.referencecustomerid) in op de klant-id om de klant vast te stellen.

4. Maak een lijst met [**OrderLineItem-objecten**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) en wijs de lijst toe aan de eigenschap [**LineItems van de**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.lineitems) order. Elk orderregelitem bevat de aankoopgegevens voor één aanbieding. Zorg ervoor dat u de [**eigenschap PartnerIdOnRecord**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem.partneridonrecord) in elk regelitem vult met de MPN-id van de indirecte reseller. U moet ten minste één orderregelitem hebben.

5. Verkrijg een interface voor orderbewerkingen door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de [**eigenschap Orders.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders)

6. Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) om de order te maken.

### <a name="c-example"></a>\#C-voorbeeld

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string offerId;
// string indirectResellerId;

// Get the indirect resellers with a relationship to the signed-in partner.
var indirectResellers = partnerOperations.Relationships.Get(PartnerRelationshipType.IsIndirectCloudSolutionProviderOf);

// Find the matching reseller in the collection.
var selectedIndirectReseller = (indirectResellers != null && indirectResellers.Items.Any()) ?
    indirectResellers.Items.FirstOrDefault(reseller => reseller.Id.Equals(indirectResellerId, StringComparison.OrdinalIgnoreCase)) :
    null;

// Prepare the order and populate the PartnerIdOnRecord with the reseller&#39;s Microsoft Partner Network Id.
var order = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            OfferId = offerId,
            FriendlyName = "New offer purchase.",
            Quantity = 5,
            PartnerIdOnRecord = selectedIndirectReseller != null ? selectedIndirectReseller.MpnId : null
        }
    }
};

// Place the order.
var createdOrder = partnerOperations.Customers.ById(customerId).Orders.Create(order);
```

**Voorbeeld:** [Consoletest-app](console-test-app.md)**Project**: Partnercentrum-SDK **Samples Class**: PlaceOrderForCustomer.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                            |
|----------|----------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende padparameter om de klant te identificeren.

| Naam        | Type   | Vereist | Beschrijving                                           |
|-------------|--------|----------|-------------------------------------------------------|
| customer-id | tekenreeks | Yes      | Een tekenreeks met GUID-indeling die de klant identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

#### <a name="order"></a>Volgorde

In deze tabel worden de **ordereigenschappen** in de aanvraag body beschreven.

| Naam | Type | Vereist | Beschrijving |
| ---- | ---- | -------- | ----------- |
| id | tekenreeks | No | Een order-id die wordt opgegeven wanneer de order is gemaakt. |
| referenceCustomerId | tekenreeks | Yes | De klant-id. |
| billingCycle | tekenreeks | No | De frequentie waarmee de partner wordt gefactureerd voor deze bestelling. De standaardwaarde is &quot; Maandelijks en wordt toegepast wanneer de order is &quot; gemaakt. Ondersteunde waarden zijn de ledennamen in [**BillingCycleType.**](/dotnet/api/microsoft.store.partnercenter.models.offers.billingcycletype) Opmerking: de jaarlijkse factureringsfunctie is nog niet algemeen beschikbaar. Ondersteuning voor jaarlijkse facturering is binnenkort beschikbaar. |
| lineItems | matrix van objecten | Yes | Een matrix met [**OrderLineItem-resources.**](#orderlineitem) |
| creationDate | tekenreeks | No | De datum waarop de order is gemaakt, in datum/tijd-indeling. Toegepast wanneer de order is gemaakt. |
| kenmerken | object | No | Bevat 'ObjectType': 'Order'. |

#### <a name="orderlineitem"></a>OrderLineItem

In deze tabel worden de **eigenschappen van OrderLineItem** in de aanvraag body beschreven.

| Naam | Type | Vereist | Beschrijving |
| ---- | ---- | -------- | ----------- |
| lineItemNumber | int | Ja | Elk regelitem in de verzameling krijgt een uniek regelnummer, dat wordt geteld van 0 tot count-1. |
| offerId | tekenreeks | Yes | De aanbiedings-id. |
| subscriptionId | tekenreeks | No | De abonnements-id. |
| parentSubscriptionId | tekenreeks | No | Optioneel. De id van het bovenliggende abonnement in een invoegaanbieding. Alleen van toepassing op PATCH. |
| Friendlyname | tekenreeks | No | Optioneel. De gebruiksvriendelijke naam voor het abonnement dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken. |
| quantity | int | Ja | Het aantal licenties voor een abonnement op basis van een licentie. |
| partnerIdOnRecord | tekenreeks | No | Wanneer een indirecte provider een order plaatst namens een indirecte reseller, vult u dit veld in met de MPN-id van alleen de **indirecte reseller** (nooit de id van de indirecte provider). Dit zorgt voor een juiste boekhouding voor incentives. **Als de MPN-id van de reseller niet wordt verstrekt, mislukt de order niet. De reseller wordt echter niet vastgelegd en als gevolg hiervan is de verkoop mogelijk niet opgenomen in de incentive-berekeningen.** |
| kenmerken | object | No | Bevat "ObjectType":"OrderLineItem". |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/orders HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 02109f46-3ff2-4be4-9f37-b2eb6d58d542
MS-CorrelationId: 85195ae6-3de5-4978-abd4-7be2fbfe4c84
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 410
Expect: 100-continue

{
    "Id": null,
    "ReferenceCustomerId": "c501c3c4-d776-40ef-9ecf-9cefb59442c1",
    "BillingCycle": "unknown",
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "DB2E705F-B82A-4024-A3D5-D88E12F2DB35",
            "SubscriptionId": null,
            "ParentSubscriptionId": null,
            "FriendlyName": "New offer purchase.",
            "Quantity": 5,
            "PartnerIdOnRecord": "4847383",
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

Als dit lukt, bevat de antwoord-body de ingevulde [orderresource.](order-resources.md)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 201 Created
Content-Length: 831
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 85195ae6-3de5-4978-abd4-7be2fbfe4c84
MS-RequestId: 02109f46-3ff2-4be4-9f37-b2eb6d58d542
MS-CV: Nd3Oum/L5EywtKQK.0
MS-ServerId: 020021921
Date: Mon, 10 Apr 2017 23:02:24 GMT

{
    "id": "3eddcac6-63b2-4c40-b0b6-f47e18301492",
    "referenceCustomerId": "c501c3c4-d776-40ef-9ecf-9cefb59442c1",
    "billingCycle": "monthly",
    "lineItems": [{
            "lineItemNumber": 0,
            "offerId": "DB2E705F-B82A-4024-A3D5-D88E12F2DB35",
            "subscriptionId": "42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
            "friendlyName": "New offer purchase.",
            "quantity": 5,
            "partnerIdOnRecord": "4847383",
            "links": {
                "subscription": {
                    "uri": "/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/subscriptions/42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2017-04-10T16:02:25.983-07:00",
    "links": {
        "self": {
            "uri": "/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/orders/3eddcac6-63b2-4c40-b0b6-f47e18301492",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "etag": "eyJpZCI6IjNlZGRjYWM2LTYzYjItNGM0MC1iMGI2LWY0N2UxODMwMTQ5MiIsInZlcnNpb24iOjF9",
        "objectType": "Order"
    }
}
```
