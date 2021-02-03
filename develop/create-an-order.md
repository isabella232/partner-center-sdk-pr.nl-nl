---
title: Een klant order maken
description: Meer informatie over het gebruik van partner Center-Api's voor het maken van een bestelling voor een klant. Artikel bevat vereisten, stappen en voor beelden.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ce176909a1f9c350f1c16615171de57a7beb888d
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767636"
---
# <a name="create-an-order-for-a-customer-using-partner-center-apis"></a>Een bestelling maken voor een klant die partner Center-Api's gebruikt

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud for US Government

Het maken van een **order voor voor Azure gereserveerde VM-instantie producten** is *alleen* van toepassing op:

- Partnercentrum

Zie [partner aanbiedingen in het Cloud Solution Provider-programma](/partner-center/csp-offers)voor meer informatie over wat momenteel beschikbaar is om te verkopen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een aanbiedings-id.

## <a name="c"></a>C\#

Voor het maken van een bestelling voor een klant:

1. Maak een exemplaar van een object [**order**](order-resources.md) en stel de eigenschap **ReferenceCustomerID** in op de klant-id voor het registreren van de klant.

2. Maak een lijst met [**OrderLineItem**](order-resources.md#orderlineitem) -objecten en wijs de lijst toe aan de eigenschap **regel items** van de order. Elk order regel item bevat de inkoop gegevens voor één aanbieding. U moet ten minste één order regel item hebben.

3. Een interface voor het best Ellen van bewerkingen verkrijgen. Roep eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren. Haal vervolgens de interface op uit de eigenschap [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) .

4. Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) aan en geef het [**volg orde**](order-resources.md) -object door.

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string offerId;

var order = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            OfferId = offerId,
            FriendlyName = "new offer purchase",
            Quantity = 1,
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", "5198C069-3DAA-403A-8660-5BE11BFD12EE" },
                { "scope", "shared" },
                { "duration", "3Years" }
            }
        }
    }
};

var createdOrder = partnerOperations.Customers.ById(customerId).Orders.Create(order);
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: CreateOrder.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                                            |
|----------|----------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/orders http/1.1 |

#### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende para meter voor het identificeren van de klant.

| Naam        | Type   | Vereist | Beschrijving                                                |
|-------------|--------|----------|------------------------------------------------------------|
| klant-id | tekenreeks | Yes      | Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

#### <a name="order"></a>Volgorde

In deze tabel worden de eigenschappen van de [bestelling](order-resources.md) in de hoofd tekst van de aanvraag beschreven.

| Eigenschap             | Type                        | Vereist                        | Beschrijving                                                                   |
|----------------------|-----------------------------|---------------------------------|-------------------------------------------------------------------------------|
| id                   | tekenreeks                      | No                              | Een order-id die wordt geleverd bij het maken van de order.   |
| referenceCustomerId  | tekenreeks                      | No                              | De klant-id. |
| billingCycle         | tekenreeks                      | No                              | Hiermee wordt de frequentie aangegeven waarmee de partner voor deze order wordt gefactureerd. Ondersteunde waarden zijn de lidnamen in [BillingCycleType](product-resources.md#billingcycletype). De standaard waarde is ' maandelijks ' of ' eenmalige ' bij het maken van de order. Dit veld wordt toegepast bij het maken van de order. |
| Regel items            | matrix van [OrderLineItem](order-resources.md#orderlineitem) -resources | Yes      | Een gespecificeerde lijst met de aanbiedingen die de klant koopt, met inbegrip van de hoeveelheid.        |
| currencyCode         | tekenreeks                      | No                              | Alleen-lezen. De valuta die wordt gebruikt bij het plaatsen van de order. Wordt toegepast bij het maken van de order.           |
| creationDate         | datum/tijd                    | No                              | Alleen-lezen. De datum waarop de order is gemaakt, in datum-tijd notatie. Wordt toegepast bij het maken van de order.                                   |
| status               | tekenreeks                      | No                              | Alleen-lezen. De status van de order.  Ondersteunde waarden zijn de lidnamen in [OrderStatus](order-resources.md#orderstatus).        |
| koppelen                | [OrderLinks](utility-resources.md#resourcelinks)              | No                              | De resource koppelingen die overeenkomen met de volg orde. |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | No                              | De meta gegevens kenmerken die overeenkomen met de volg orde. |

#### <a name="orderlineitem"></a>OrderLineItem

In deze tabel worden de eigenschappen van [OrderLineItem](order-resources.md#orderlineitem) in de hoofd tekst van de aanvraag beschreven.

>[!NOTE]
>De partnerIdOnRecord mag alleen worden gegeven wanneer een indirecte provider een bestelling namens een indirecte wederverkoper plaatst. Het wordt gebruikt voor het opslaan van de Microsoft Partner Network ID alleen van de indirecte wederverkoper (nooit de ID van de indirecte provider).

| Naam                 | Type   | Vereist | Beschrijving                                                                                                                                                                                                                                |
|----------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| lineItemNumber       | int    | Ja      | Elk regel item in de verzameling krijgt een uniek regel nummer, geteld van 0 tot aantal-1.                                                                                                                                                 |
| offerId              | tekenreeks | Yes      | De aanbiedings-id.                                                                                                                                                                                                                      |
| subscriptionId       | tekenreeks | No       | De abonnements-id.                                                                                                                                                                                                               |
| parentSubscriptionId | tekenreeks | No       | Optioneel. De ID van het bovenliggende abonnement in een invoeg toepassing. Is alleen van toepassing op PATCH.                                                                                                                                                     |
| friendlyName         | tekenreeks | No       | Optioneel. De beschrijvende naam voor het abonnement dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.                                                                                                                                              |
| quantity             | int    | Ja      | Het aantal licenties voor een abonnement op basis van licenties.                                                                                                                                                                                   |
| partnerIdOnRecord    | tekenreeks | No       | Wanneer een indirecte provider een bestelling namens een indirecte wederverkoper plaatst, vult u dit veld alleen met de MPN-ID van de **indirecte wederverkoper** (nooit de id van de indirecte provider). Dit zorgt voor een goede administratieve verwerking van prikkels. |
| provisioningContext  | Dictionary<teken reeks, teken reeks>                | No       |  Informatie die is vereist voor het inrichten van sommige items in de catalogus. De eigenschap provisioningVariables in een SKU geeft aan welke eigenschappen vereist zijn voor specifieke items in de catalogus.                  |
| koppelen                | [OrderLineItemLinks](order-resources.md#orderlineitemlinks) | No       |  Alleen-lezen. De resource koppelingen die overeenkomen met het order regel item.  |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | No       | De meta gegevens kenmerken die overeenkomen met de OrderLineItem. |
| renewsTo             | Matrix van objecten                          | No    |Een matrix met [RenewsTo](order-resources.md#renewsto) -resources.                                                                            |

##### <a name="renewsto"></a>RenewsTo

In deze tabel worden de eigenschappen van [RenewsTo](order-resources.md#renewsto) in de hoofd tekst van de aanvraag beschreven.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | tekenreeks           | No              | Een ISO 8601-representatie van de duur van de verlengings termijn. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar). |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Length: 691
Content-Type: application/json

{
  "BillingCycle": "one_time",
  "CurrencyCode": "USD",
  "LineItems": [
    {
      "LineItemNumber": 0,
      "ProvisioningContext": {
        "subscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
        "scope": "shared",
        "duration": "1Year"
      },
      "OfferId": "DZH318Z0BQ4B:0047:DZH318Z0DSM8",
      "FriendlyName": "A_sample_Azure_RI",
      "Quantity": 1
    }
  ]
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert de methode een [order](order-resources.md) resource in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 201 Created
Content-Length: 788
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b593cbb7-b358-4b31-81fc-e60b9c277a7f
MS-RequestId: 025f4c19-217f-49d6-a056-391902c62fb3
Date: Thu, 15 Mar 2018 22:30:02 GMT

{
  "id": "Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1",
  "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
  "billingCycle": "one_time",
  "currencyCode": "USD",
  "lineItems": [
    {
        "lineItemNumber": 0,
        "offerId": "84A03D81-6B37-4D66-8D4A-FAEA24541538",
        "friendlyName": "A_sample_Azure_RI",
        "quantity": 1,
        "links": {
            "sku": {
                "uri": "/products/DZH318Z0BQ4B/skus/0047?country=US",
                "method": "GET",
                "headers": []
            }
        }
    } ],
    "creationDate": "2018-03-15T22:30:02.085152Z",
    "status": "pending",
    "links": {
        "provisioningStatus": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Order"
    }
}
```
