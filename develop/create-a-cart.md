---
title: Een winkelwagen maken
description: Meer informatie over het gebruik Partner Center API's om een order voor een klant in een winkelwagen toe te voegen. Onderwerp bevat informatie over het maken van een winkelwagen en eventuele vereisten.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: dba54d4f6b97f3d0a51e2f87b32edca686466b89
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973771"
---
# <a name="create-a-cart-with-a-customer-order"></a>Een winkelwagen maken met een klantorder

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

U kunt een order voor een klant toevoegen in een winkelwagen. Zie Partneraanbiedingen in het Cloud Solution Provider programma voor meer informatie over [wat momenteel beschikbaar is om Cloud Solution Provider verkopen.](/partner-center/csp-offers)

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Een order voor een klant maken:

1. Een winkelwagenobject instanteren.

2. Maak een lijst met **CartLineItem-objecten** en wijs de lijst toe aan de eigenschap LineItems van de winkelwagen. Elk winkelwagenregelitem bevat de aankoopgegevens voor één product. U moet ten minste één winkelwagenregelitem hebben.

3. Verkrijg een interface voor winkelwagenbewerkingen door de methode **IAggregatePartner.Customers.ById** aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de eigenschap **Winkelwagen.**

4. Roep de **methode Create** of **CreateAsync aan** om de winkelwagen te maken.

### <a name="c-example"></a>\#C-voorbeeld

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

var cart = new Cart()
{
    LineItems = new List<CartLineItem>()
    {
        new CartLineItem()
        {
      /* Microsoft Azure Subscription */
            Id = 0,
            CatalogItemId = "MS-AZR-0145P",
            Quantity = 1,
            BillingCycle = BillingCycleType.Monthly,
            TermDuration = "P1Y"
        },
        new CartLineItem()
        {
      /* Azure Reserved Instance */
            Id = 1,
            CatalogItemId = "DZH318Z0BQ36:004G:DZH318Z08C0S",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime,
            TermDuration = "P1Y",
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", subscriptionId },
                { "scope", "shared" }
            }
        },
        new CartLineItem()
        {
      /* Azure Reserved Instance */
            Id = 2,
            CatalogItemId = "DZH318Z0BQ36:004J:DZH318Z08B8X",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime,
            TermDuration = "P3Y",
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", subscriptionId },
                { "scope", "shared" }
            }
        },
        new CartLineItem()
        {
      /* Perpetual Software */
            Id = 3,
            CatalogItemId = "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime
        },
        new CartLineItem()
        {
      /* SaaS */
            Id = 4,
            CatalogItemId = "DZH318Z0BXWC:0002:DZH318Z0BMRV",
            Quantity = 1,
            BillingCycle = BillingCycleType.Monthly,
            TermDuration = "P1M"
        },
        new CartLineItem()
        {
      /* SaaS Free Trial */
            Id = 5,
            CatalogItemId = "DZH318Z0C0WF:0001:DZH318Z0BP69",
            Quantity = 10,
            BillingCycle = BillingCycleType.None,
            TermDuration = "P1M",
            RenewsTo = new RenewsTo
            {
                TermDuration = "P1Y"
            }
        }
    }
};

cart = partnerOperations.Customers.ById(customerId).Carts.Create(cart);
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Een order voor een klant maken:

1. Een winkelwagenobject instanteren.

2. Maak een lijst met **CartLineItem-objecten** en wijs de lijst toe aan de regelitems van de winkelwagen. Elk winkelwagenregelitem bevat de aankoopgegevens voor één product. U moet ten minste één winkelwagenregelitem hebben.

3. Verkrijg een interface voor winkelwagenbewerkingen door de functie **IAggregatePartner.getCustomers().byId** aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de **functie getCart.**

4. Roep de **functie create aan** om de winkelwagen te maken.

## <a name="java-example"></a>Java-voorbeeld

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String subscriptionId;
// String catalogItemId;

CartLineItem lineItem = new CartLineItem();

lineItem.setBillingCycle(BillingCycleType.OneTime);
lineItem.setCatalogItemId(catalogItemId);
lineItem.setFriendlyName("Sample RI Purchase");
lineItem.setQuantity(1);

Map<String, String> provisioningContext = new HashMap<String,String>();

provisioningContext.put("duration", "3Years");
provisioningContext.put("scope", "shared");
provisioningContext.put("subscriptionId", subscriptionId);

lineItem.setProvisioningContext(provisioningContext);

List<CartLineItem> lineItemList = new ArrayList<CartLineItem>();
lineItemList.add(lineItem);

Cart cart = new Cart();
cart.setLineItems(lineItemList);

Cart cartCreated = partnerOperations.getCustomers().byId(customerId).getCarts().create(cart);
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Een order voor een klant maken:

1. Een winkelwagenobject instanteren.

2. Maak een lijst met **CartLineItem-objecten** en wijs de lijst toe aan de regelitems van de winkelwagen. Elk winkelwagenregelitem bevat de aankoopgegevens voor één product. U moet ten minste één winkelwagenregelitem hebben.

3. Voer de [**opdracht New-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) uit om de winkelwagen te maken.

```powershell
# $customerId
# $subscriptionId
# $catalogItemId

$lineItem = New-Object -TypeName Microsoft.Store.PartnerCenter.PowerShell.Models.Carts.PSCartLineItem

$lineItem.BillingCycle = 'OneTime'
$lineItem.CatalogItemId = $catalogItemId
$lineItem.FriendlyName = 'Sample RI Purchase'
$lineItem.ProvisioningContext.Add('duration', '1Year')
$lineItem.ProvisioningContext.Add('scope', 'shared')
$lineItem.ProvisioningContext.Add('subscriptionId', $subsciptionId)
$lineItem.Quantity = 10

New-PartnerCustomerCart -CustomerId $customerId -LineItems $lineItem
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1                        |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende padparameter om de klant te identificeren.

| Naam            | Type     | Vereist | Beschrijving                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **customer-id** | tekenreeks   | Ja      | Een met GUID opgemaakte klant-id die de klant identificeert.             |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de eigenschappen [van de winkelwagen](cart-resources.md) in de aanvraag body beschreven.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | No              | Een winkelwagen-id die wordt opgegeven wanneer de winkelwagen is gemaakt.                                  |
| creationTimeStamp     | DateTime         | Nee              | De datum waarop de winkelwagen is gemaakt, in datum/tijd-indeling. Toegepast wanneer de winkelwagen is gemaakt.         |
| lastModifiedTimeStamp | DateTime         | Nee              | De datum waarop de winkelwagen het laatst is bijgewerkt, in datum/tijd-indeling. Toegepast wanneer de winkelwagen is gemaakt.    |
| expirationTimeStamp   | DateTime         | Nee              | De datum waarop de winkelwagen verloopt, in datum/tijd-indeling.  Toegepast bij het maken van de winkelwagen.            |
| lastModifiedUser      | tekenreeks           | No              | De gebruiker die de winkelwagen voor het laatst heeft bijgewerkt. Toegepast bij het maken van de winkelwagen.                             |
| lineItems             | Matrix met objecten | Ja             | Een matrix van [CartLineItem-resources.](cart-resources.md#cartlineitem)                                     |

In deze tabel worden de [eigenschappen van CartLineItem](cart-resources.md#cartlineitem) in de aanvraag body beschreven.

|      Eigenschap       |            Type             | Vereist |                                                                                         Beschrijving                                                                                         |
|---------------------|-----------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         id          |           tekenreeks            |    No    |                                                     Een unieke id voor een winkelwagenregelitem. Toegepast nadat de winkelwagen is gemaakt.                                                     |
|      catalogId      |           tekenreeks            |   Ja    |                                                                                De id van het catalogusitem.                                                                                 |
|    Friendlyname     |           tekenreeks            |    No    |                                                    Optioneel. De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.                                                    |
|      quantity       |             int             |   Ja    |                                                                            Het aantal licenties of exemplaren.                                                                             |
|    currencyCode     |           tekenreeks            |    No    |                                                                                     De valutacode.                                                                                      |
|    billingCycle     |           Object            |   Ja    |                                                                    Het type factureringscyclus dat is ingesteld voor de huidige periode.                                                                    |
|    deelnemers     | Lijst met objectreeksparen |    Nee    |                                                                Een verzameling PartnerId on Record (MPNID) voor de aankoop.                                                                 |
| provisioningContext | Woordenlijst<tekenreeks, tekenreeks>  |    Nee    | Informatie die vereist is voor het inrichten van sommige items in de catalogus. De eigenschap provisioningVariables in een SKU geeft aan welke eigenschappen vereist zijn voor specifieke items in de catalogus. |
|     orderGroup      |           tekenreeks            |    No    |                                                                   Een groep om aan te geven welke items samen kunnen worden geplaatst.                                                                   |
|        fout        |           Object            |    Nee    |                                                                     Toegepast nadat de winkelwagen is gemaakt als er een fout is opgetreden.                                                                      |
|     renewsTo        | Matrix met objecten            |    Nee    |                                                    Een matrix van [RenewsTo-resources.](cart-resources.md#renewsto)                                                                            |

In deze tabel worden de [RenewsTo-eigenschappen](cart-resources.md#renewsto) in de aanvraag body beschreven.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | tekenreeks           | No              | Een ISO 8601-weergave van de duur van de verlengingstermijn. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar). |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 496
Expect: 100-continue

{
  "lineItems": [
    {
    /* Microsoft Azure Subscription */
      "id": 0,
      "catalogItemId": "MS-AZR-0145P",
      "quantity": 1,
      "billingCycle": "monthly",
      "termDuration": "P1Y"
    },
    {
    /* Azure Reserved Instance */
      "id": 1,
      "catalogItemId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
      "quantity": 1,
      "billingCycle": "one_time",
      "termDuration": "P1Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      }
    },
    {
    /* Azure Reserved Instance */
      "id": 2,
      "catalogItemId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
      "quantity": 1,
      "billingCycle": "one_time",
      "termDuration": "P3Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "single"
      }
    },
    {
    /* Perpetual Software */
      "id": 3,
      "catalogItemId": "DG7GMGF0DWTL:0001:DG7GMGF0DSFM",
      "quantity": 1,
      "billingCycle": "one_time"
    },
    {
    /* SaaS */
      "id": 4,
      "catalogItemId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
      "quantity": 1,
      "billingCycle": "monthly",
      "termDuration": "P1M"
    },
  {
    /* SaaS Free Trial */
       "id": 5,
       "catalogItemId": "DZH318Z0C0WF:0001:DZH318Z0BP69",
       "quantity": 10,
       "billingCycle": "none",
       "termDuration": "P1M",
       "renewsTo": {
         "termDuration": "P1Y"
       }
    }
  ]
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode de ingevulde [winkelwagenresource](cart-resources.md) in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 201 Created
Content-Length: 764
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
X-Locale: en-US,en-US
MS-CV: sF/wRa2ih0CzbABc.0
MS-ServerId: 000001
Date: Thu, 15 Mar 2018 17:15:01 GMT
{
  "id": "3655b1a0-b1c9-4268-9824-577fdbc4d0be",
  "creationTimestamp": "2019-01-16T00:45:41.6062996Z",
  "lastModifiedTimestamp": "2019-01-16T00:45:41.6062996Z",
  "expirationTimestamp": "2019-01-16T01:00:54.4188497Z",
  "lastModifiedUser": "1824b7fc-2fac-4478-b177-66823c40ab75",
  "status": "Active",
  "lineItems": [
    {
      "id": 0,
      "catalogItemId": "MS-AZR-0145P",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "monthly",
      "termDuration": "P1Y",
      "orderGroup": "OMS-0"
    },
    {
      "id": 1,
      "catalogItemId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "termDuration": "P1Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      },
      "orderGroup": "0"
    },
    {
      "id": 2,
      "catalogItemId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "termDuration": "P3Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      },
      "orderGroup": "0"
    },
    {
      "id": 3,
      "catalogItemId": "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "orderGroup": "0"
    },
    {
      "id": 4,
      "catalogItemId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "monthly",
      "termDuration": "P1M",
      "orderGroup": "1"
    },
  {
      "id": 5,
      "catalogItemId": "DZH318Z0C0WF:0001:DZH318Z0BP69",
      "quantity": 10,
      "currencyCode": "USD",
      "billingCycle": "none",
      "termDuration": "P1M",
      "renewsTo": {
  "termDuration": "P1Y"
      },
    "orderGroup": "2"
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/28045616-f6b9-462f-9701-0d89b5e65c44/carts/3655b1a0-b1c9-4268-9824-577fdbc4d0be",
      "method": "GET",
      "headers": []
    }
  },
  "attributes": {
    "objectType": "Cart"
  }
}
```
