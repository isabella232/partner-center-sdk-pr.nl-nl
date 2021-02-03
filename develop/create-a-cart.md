---
title: Een winkelwagen maken
description: Meer informatie over het gebruik van partner Center-Api's voor het toevoegen van een bestelling voor een klant in een winkel wagen. Onderwerp bevat informatie over het maken van een winkel wagen en eventuele vereisten.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: a1c559b415a7d42af4e904e09795f92aed7f125f
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767637"
---
# <a name="create-a-cart-with-a-customer-order"></a>Een winkel wagen maken met een klant order

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

U kunt een bestelling voor een klant in een winkel wagen toevoegen. Zie [partner aanbiedingen in het Cloud Solution Provider-programma](/partner-center/csp-offers)voor meer informatie over wat momenteel beschikbaar is om te verkopen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Voor het maken van een bestelling voor een klant:

1. Een object voor een winkel wagen instantiëren.

2. Maak een lijst met **CartLineItem** -objecten en wijs de lijst toe aan de eigenschap regel items van de winkel wagen. Elk winkelwagen regel item bevat de aankoop gegevens voor één product. U moet ten minste één winkelwagen regel item hebben.

3. Verkrijg een interface voor winkelwagen bewerkingen door de **IAggregatePartner. Customs. ById** -methode aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de eigenschap **winkel wagen** .

4. Roep de methode **Create** of **CreateAsync** aan om de winkel wagen te maken.

### <a name="c-example"></a>C- \# voor beeld

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

Voor het maken van een bestelling voor een klant:

1. Een object voor een winkel wagen instantiëren.

2. Maak een lijst met **CartLineItem** -objecten en wijs de lijst toe aan de regel items van de wagen. Elk winkelwagen regel item bevat de aankoop gegevens voor één product. U moet ten minste één winkelwagen regel item hebben.

3. Verkrijg een interface voor winkelwagen bewerkingen door de functie **IAggregatePartner. getCustomers (). byId** aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de functie **getCart** .

4. Roep de functie **Create** aan om de winkel wagen te maken.

## <a name="java-example"></a>Java-voor beeld

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

Voor het maken van een bestelling voor een klant:

1. Een object voor een winkel wagen instantiëren.

2. Maak een lijst met **CartLineItem** -objecten en wijs de lijst toe aan de regel items van de wagen. Elk winkelwagen regel item bevat de aankoop gegevens voor één product. U moet ten minste één winkelwagen regel item hebben.

3. Voer de opdracht [**New-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) uit om de winkel wagen te maken.

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

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Carts http/1.1                        |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende para meter voor het identificeren van de klant.

| Naam            | Type     | Vereist | Beschrijving                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **klant-id** | tekenreeks   | Yes      | Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.             |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de eigenschappen van de [winkel wagen](cart-resources.md) in de hoofd tekst van de aanvraag beschreven.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | No              | Een winkel wagen-id die is opgegeven bij het maken van de winkel wagen.                                  |
| creationTimeStamp     | DateTime         | No              | De datum waarop de winkel wagen is gemaakt, in datum-tijd notatie. Wordt toegepast bij het maken van de winkel wagen.         |
| lastModifiedTimeStamp | DateTime         | No              | De datum waarop de winkel wagen voor het laatst is bijgewerkt, in datum-tijd notatie. Wordt toegepast bij het maken van de winkel wagen.    |
| expirationTimeStamp   | DateTime         | No              | De datum waarop de winkel wagen verloopt, in datum-tijd notatie.  Wordt toegepast bij het maken van de winkel wagen.            |
| lastModifiedUser      | tekenreeks           | No              | De gebruiker die de winkel wagen het laatst heeft bijgewerkt. Wordt toegepast bij het maken van de winkel wagen.                             |
| Regel items             | Matrix van objecten | Yes             | Een matrix met [CartLineItem](cart-resources.md#cartlineitem) -resources.                                     |

In deze tabel worden de eigenschappen van [CartLineItem](cart-resources.md#cartlineitem) in de hoofd tekst van de aanvraag beschreven.

|      Eigenschap       |            Type             | Vereist |                                                                                         Beschrijving                                                                                         |
|---------------------|-----------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         id          |           tekenreeks            |    No    |                                                     Een unieke id voor een winkelwagen regel item. Wordt toegepast bij het maken van de winkel wagen.                                                     |
|      catalogId      |           tekenreeks            |   Yes    |                                                                                De id van het catalogus item.                                                                                 |
|    friendlyName     |           tekenreeks            |    No    |                                                    Optioneel. De beschrijvende naam voor het item dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.                                                    |
|      quantity       |             int             |   Ja    |                                                                            Het aantal licenties of exemplaren.                                                                             |
|    currencyCode     |           tekenreeks            |    No    |                                                                                     De valuta code.                                                                                      |
|    billingCycle     |           Object            |   Ja    |                                                                    Het type facturerings cyclus dat voor de huidige periode is ingesteld.                                                                    |
|    deelnemers     | Lijst met object teken reeks paren |    No    |                                                                Een verzameling partner on record (MPNID) voor de aankoop.                                                                 |
| provisioningContext | Dictionary<teken reeks, teken reeks>  |    No    | Informatie die is vereist voor het inrichten van sommige items in de catalogus. De eigenschap provisioningVariables in een SKU geeft aan welke eigenschappen vereist zijn voor specifieke items in de catalogus. |
|     orderGroup      |           tekenreeks            |    No    |                                                                   Een groep om aan te geven welke items bij elkaar kunnen worden geplaatst.                                                                   |
|        fout        |           Object            |    No    |                                                                     Wordt toegepast nadat de winkel wagen is gemaakt in het geval van een fout.                                                                      |
|     renewsTo        | Matrix van objecten            |    No    |                                                    Een matrix met [RenewsTo](cart-resources.md#renewsto) -resources.                                                                            |

In deze tabel worden de eigenschappen van [RenewsTo](cart-resources.md#renewsto) in de hoofd tekst van de aanvraag beschreven.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | tekenreeks           | No              | Een ISO 8601-representatie van de duur van de verlengings termijn. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar). |

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

Als dit lukt, retourneert deze methode de gevulde [Winkelwagen](cart-resources.md) resource in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

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
