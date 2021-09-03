---
title: Een klantorder maken
description: Meer informatie over het gebruik Partner Center API's om een order voor een klant te maken. Het artikel bevat vereisten, stappen en voorbeelden.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f8a18ef4a6fbdfcd659e6ec1c11bc6bd61c80472
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/03/2021
ms.locfileid: "123456032"
---
# <a name="create-an-order-for-a-customer-using-partner-center-apis"></a>Een order voor een klant maken met behulp van Partner Center API's

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud for US Government

Het maken van **een bestelling voor azure-producten voor gereserveerde VM-instanties** is *alleen van toepassing op:*

- Partnercentrum

Zie Partneraanbiedingen in het Cloud Solution Provider voor informatie over [wat momenteel beschikbaar is om te verkopen.](/partner-center/csp-offers)

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een aanbiedings-id.

## <a name="c"></a>C\#

Een order voor een klant maken:

1. Instantieer een [**Order-object**](order-resources.md) en stel de **eigenschap ReferenceCustomerID** in op de klant-id om de klant vast te stellen.

2. Maak een lijst met [**OrderLineItem-objecten**](order-resources.md#orderlineitem) en wijs de lijst toe aan de eigenschap **LineItems van de** order. Elk orderregelitem bevat de aankoopgegevens voor één aanbieding. U moet ten minste één orderregelitem hebben.

3. Een interface verkrijgen voor het orden van bewerkingen. Roep eerst de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren. Haal vervolgens de interface op uit de [**eigenschap Orders.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders)

4. Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) en geef het [**orderobject**](order-resources.md) door.

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

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: CreateOrder.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                            |
|----------|----------------------------------------------------------------------------------------|
| **VERZENDEN** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende padparameter om de klant te identificeren.

| Naam        | Type   | Vereist | Beschrijving                                                |
|-------------|--------|----------|------------------------------------------------------------|
| customer-id | tekenreeks | Yes      | Een in GUID opgemaakte klant-id die de klant identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

#### <a name="order"></a>Volgorde

In deze tabel worden de [ordereigenschappen](order-resources.md) in de aanvraag body beschreven.

| Eigenschap             | Type                        | Vereist                        | Beschrijving                                                                   |
|----------------------|-----------------------------|---------------------------------|-------------------------------------------------------------------------------|
| id                   | tekenreeks                      | No                              | Een order-id die wordt opgegeven wanneer de order is gemaakt.   |
| referenceCustomerId  | tekenreeks                      | No                              | De klant-id. |
| billingCycle         | tekenreeks                      | No                              | Geeft de frequentie aan waarmee de partner wordt gefactureerd voor deze bestelling. Ondersteunde waarden zijn de ledennamen in [BillingCycleType.](product-resources.md#billingcycletype) De standaardwaarde is 'Maandelijks' of 'OneTime' bij het maken van de order. Dit veld wordt toegepast wanneer de order is gemaakt. |
| lineItems            | matrix van [OrderLineItem-resources](order-resources.md#orderlineitem) | Yes      | Een gespecificeerde lijst met aanbiedingen die de klant aanschaft, inclusief de hoeveelheid.        |
| currencyCode         | tekenreeks                      | No                              | Alleen-lezen. De valuta die wordt gebruikt bij het plaatsen van de order. Toegepast wanneer de order is gemaakt.           |
| creationDate         | datum/tijd                    | No                              | Alleen-lezen. De datum waarop de order is gemaakt, in datum/tijd-indeling. Toegepast wanneer de order is gemaakt.                                   |
| status               | tekenreeks                      | No                              | Alleen-lezen. De status van de bestelling.  Ondersteunde waarden zijn de ledennamen in [OrderStatus](order-resources.md#orderstatus).        |
| Verwijzigingen                | [OrderLinks](utility-resources.md#resourcelinks)              | No                              | De resourcekoppelingen die overeenkomen met de Bestelling. |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | No                              | De metagegevenskenmerken die overeenkomen met de order. |

#### <a name="orderlineitem"></a>OrderLineItem

In deze tabel worden de [eigenschappen van OrderLineItem](order-resources.md#orderlineitem) in de aanvraag body beschreven.

>[!NOTE]
>De partnerIdOnRecord mag alleen worden opgegeven wanneer een indirecte provider een order namens een indirecte reseller plaatst. Deze wordt gebruikt voor het opslaan van Microsoft Partner Network id van de indirecte reseller (nooit de id van de indirecte provider).

| Naam                 | Type   | Vereist | Beschrijving                                                                                                                                                                                                                                |
|----------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| lineItemNumber       | int    | Ja      | Elk regelitem in de verzameling krijgt een uniek regelnummer, dat wordt geteld van 0 tot count-1.                                                                                                                                                 |
| offerId              | tekenreeks | Yes      | De aanbiedings-id.                                                                                                                                                                                                                      |
| subscriptionId       | tekenreeks | No       | De abonnements-id.                                                                                                                                                                                                               |
| parentSubscriptionId | tekenreeks | No       | Optioneel. De id van het bovenliggende abonnement in een invoegaanbieding. Alleen van toepassing op PATCH.                                                                                                                                                     |
| Friendlyname         | tekenreeks | No       | Optioneel. De gebruiksvriendelijke naam voor het abonnement dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.                                                                                                                                              |
| quantity             | int    | Ja      | Het aantal licenties voor een abonnement op basis van een licentie.                                                                                                                                                                                   |
| partnerIdOnRecord    | tekenreeks | No       | Wanneer een indirecte provider een order plaatst namens een indirecte reseller, vult u dit veld in met de MPN-id van alleen de **indirecte reseller** (nooit de id van de indirecte provider). Dit zorgt voor een juiste boekhouding voor incentives. |
| provisioningContext  | Woordenlijst<tekenreeks, tekenreeks>                | No       |  Informatie die vereist is voor het inrichten van sommige items in de catalogus. De eigenschap provisioningVariables in een SKU geeft aan welke eigenschappen vereist zijn voor specifieke items in de catalogus.                  |
| Verwijzigingen                | [OrderLineItemLinks](order-resources.md#orderlineitemlinks) | No       |  Alleen-lezen. De resourcekoppelingen die overeenkomen met het regelitem Order.  |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | No       | De metagegevenskenmerken die overeenkomen met de OrderLineItem. |
| renewsTo             | Matrix met objecten                          | No    |Een matrix van [RenewsTo-resources.](order-resources.md#renewsto)                                                                            |
| AttestationAccepted             | booleaans                 | No   |  Geeft aan dat u akkoord gaat met de aanbieding of SKU-voorwaarden. Alleen vereist voor aanbiedingen of SKU's waarbij SkuAttestationProperties of OfferAttestationProperties enforceAttestation true is.          |

##### <a name="renewsto"></a>RenewsTo

In deze tabel worden de [RenewsTo-eigenschappen](order-resources.md#renewsto) in de aanvraag body beschreven.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | tekenreeks           | No              | Een ISO 8601-weergave van de duur van de verlengingstermijn. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar). |

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

Als dit lukt, retourneert de [methode](order-resources.md) een Order-resource in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)

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
