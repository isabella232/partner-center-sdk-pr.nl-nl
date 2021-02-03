---
title: Een klant order maken voor een indirecte wederverkoper
description: Meer informatie over het gebruik van partner Center-Api's voor het maken van een bestelling voor een klant van een indirecte wederverkoper. Artikel bevat vereisten, stappen en exmaples.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f72ecec8d82e6b8a1bc53c277206cafd7d8a4e03
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767644"
---
# <a name="create-an-order-for-a-customer-of-an-indirect-reseller"></a>Een bestelling maken voor een klant van een indirecte reseller

**Van toepassing op:**

- Partnercentrum

Hoe u een bestelling maakt voor een klant van een indirecte wederverkoper.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- De aanbiedings-id van het item dat moet worden gekocht.

- De Tenant-id van de indirecte wederverkoper.

## <a name="c"></a>C\#

Voor het maken van een bestelling voor een klant van een indirecte wederverkoper:

1. Een verzameling van de indirecte wederverkopers ophalen die een relatie hebben met de aangemelde partner.

2. Een lokale variabele ophalen voor het item in de verzameling dat overeenkomt met de ID van de indirecte wederverkoper. Deze stap helpt u bij het openen van de [**MpnId**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationship.mpnid) -eigenschap van de wederverkoper wanneer u de order maakt.

3. Maak een exemplaar van een object [**order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) en stel de eigenschap [**ReferenceCustomerID**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.referencecustomerid) in op de klant-id om de klant op te nemen.

4. Maak een lijst met [**OrderLineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) -objecten en wijs de lijst toe aan de eigenschap [**regel items**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.lineitems) van de order. Elk order regel item bevat de inkoop gegevens voor één aanbieding. Zorg ervoor dat u de eigenschap [**PartnerIdOnRecord**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem.partneridonrecord) in elk regel item vult met de MPN-id van de indirecte wederverkoper. U moet ten minste één order regel item hebben.

5. Schaf een interface aan om bewerkingen uit te best Ellen door de [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met de klant-id om de klant te identificeren en haal vervolgens de interface op uit de eigenschap [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) .

6. Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) aan om de order te maken.

### <a name="c-example"></a>C- \# voor beeld

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

Voor **beeld**: [console test app](console-test-app.md)**project**: Partner Center SDK samples **klasse**: PlaceOrderForCustomer.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                                            |
|----------|----------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/orders http/1.1 |

#### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende para meter voor het identificeren van de klant.

| Naam        | Type   | Vereist | Beschrijving                                           |
|-------------|--------|----------|-------------------------------------------------------|
| klant-id | tekenreeks | Yes      | Een teken reeks met een GUID-indeling die de klant identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

#### <a name="order"></a>Volgorde

In deze tabel worden de eigenschappen van de **bestelling** in de hoofd tekst van de aanvraag beschreven.

| Naam | Type | Vereist | Beschrijving |
| ---- | ---- | -------- | ----------- |
| id | tekenreeks | No | Een order-id die wordt geleverd bij het maken van de order. |
| referenceCustomerId | tekenreeks | Yes | De klant-id. |
| billingCycle | tekenreeks | No | De frequentie waarmee de partner voor deze order wordt gefactureerd. De standaard waarde is &quot; maandelijks &quot; en wordt toegepast bij het maken van de order. Ondersteunde waarden zijn de lidnamen in [**BillingCycleType**](/dotnet/api/microsoft.store.partnercenter.models.offers.billingcycletype). Opmerking: de jaarlijkse facturerings functie is nog niet algemeen beschikbaar. De ondersteuning voor jaarlijkse facturering is binnenkort beschikbaar. |
| Regel items | matrix van objecten | Yes | Een matrix met [**OrderLineItem**](#orderlineitem) -resources. |
| creationDate | tekenreeks | No | De datum waarop de order is gemaakt, in datum-tijd notatie. Wordt toegepast bij het maken van de order. |
| kenmerken | object | No | Bevat "object type": "order". |

#### <a name="orderlineitem"></a>OrderLineItem

In deze tabel worden de eigenschappen van **OrderLineItem** in de hoofd tekst van de aanvraag beschreven.

| Naam | Type | Vereist | Beschrijving |
| ---- | ---- | -------- | ----------- |
| lineItemNumber | int | Ja | Elk regel item in de verzameling krijgt een uniek regel nummer, geteld van 0 tot aantal-1. |
| offerId | tekenreeks | Yes | De aanbiedings-id. |
| subscriptionId | tekenreeks | No | De abonnements-id. |
| parentSubscriptionId | tekenreeks | No | Optioneel. De ID van het bovenliggende abonnement in een invoeg toepassing. Is alleen van toepassing op PATCH. |
| friendlyName | tekenreeks | No | Optioneel. De beschrijvende naam voor het abonnement dat is gedefinieerd door de partner om dubbel zinnigheid te helpen. |
| quantity | int | Ja | Het aantal licenties voor een abonnement op basis van licenties. |
| partnerIdOnRecord | tekenreeks | No | Wanneer een indirecte provider een bestelling namens een indirecte wederverkoper plaatst, vult u dit veld alleen met de MPN-ID van de **indirecte wederverkoper** (nooit de id van de indirecte provider). Dit zorgt voor een goede administratieve verwerking van prikkels. **Als de wederverkoper MPN-ID niet kan worden verstrekt, mislukt de order niet. De wederverkoper wordt echter niet geregistreerd en als gevolg hiervan kan de verkoop niet worden inbegrepen.** |
| kenmerken | object | No | Bevat "object type": "OrderLineItem". |

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

Als dit lukt, bevat de antwoord tekst de ingevulde [order](order-resources.md) resource.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.

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
