---
title: Inventarisatie controleren
description: Meer informatie over het gebruik van partner Center-Api's voor het controleren van de inventaris voor een specifieke set catalogus items. U kunt dit doen om de producten of Sku's van een klant te identificeren.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6921760abc0b95aff820467e84b3e8e9435731cd
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767623"
---
# <a name="check-the-inventory-of-catalog-items-using-partner-center-apis"></a>De inventaris van catalogus items controleren met behulp van partner Center-Api's

**Van toepassing op:**

- Partnercentrum

De inventarisatie controleren voor een specifieke set met catalogus items.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een of meer product-Id's. Optioneel kunnen SKU-Id's ook worden opgegeven.

- Eventuele aanvullende context voor het controleren van de inventaris van de SKU ('s) waarnaar wordt verwezen door de gegeven product-of SKU-ID ('s). Deze vereisten kunnen variëren per type product/SKU en kunnen worden bepaald op basis van de **InventoryVariables** -eigenschap van de [SKU](product-resources.md#sku) .

## <a name="c"></a>C\#

Als u de inventarisatie wilt controleren, bouwt u een [InventoryCheckRequest](product-resources.md#inventorycheckrequest) -object op met behulp van een [InventoryItem](product-resources.md#inventoryitem) -object voor elk item dat moet worden gecontroleerd. Gebruik vervolgens een **IAggregatePartner. Extensions** -accessor, bereik deze aan **product** en selecteer vervolgens het land met de methode **ByCountry ()** . Roep ten slotte de methode **CheckInventory ()** aan bij uw **InventoryCheckRequest** -object.

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string subscriptionId;
string countryCode;
string productId;

// Build the inventory check request details object.
var inventoryCheckRequest = new InventoryCheckRequest()
{
    TargetItems = new InventoryItem[]{ new InventoryItem { ProductId = productId } },
    InventoryContext = new Dictionary<string, string>()
    {
      { "customerId", customerId },
      { "azureSubscriptionId", subscriptionId }
      { "armRegionName", armRegionName }
    }
};

// Get the inventory results.
var inventoryResults = partnerOperations.Extensions.Product.ByCountry(countryCode).CheckInventory(inventoryCheckRequest);
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                                                                                              |
|----------|------------------------------------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Extensions/product/checkInventory? land = {land nummer} http/1.1                        |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om de inventaris te controleren.

| Naam                   | Type     | Vereist | Beschrijving                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| land code           | tekenreeks   | Yes      | Een land/regio-ID.                                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

De details van de inventarisatie aanvraag, bestaande uit een [InventoryCheckRequest](product-resources.md#inventorycheckrequest) -resource met een of meer [InventoryItem](product-resources.md#inventoryitem) -resources.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/extensions/product/checkinventory?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: d1b1981a-e088-4610-870a-eebec96d6bcd
MS-CorrelationId: 4acb26a1-3536-4081-bc7d-092869a4961a
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json

{"TargetItems":[{"ProductId":"DZH318Z0BQ3P"}],"InventoryContext":{"customerId":"d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d","azureSubscriptionId":"3A231FBE-37FE-4410-93FD-730D3D5D4C75","armRegionName":"Europe"}}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord tekst een verzameling [InventoryItem](product-resources.md#inventoryitem) -objecten die zijn gevuld met de beperkings Details, indien van toepassing.

>[!NOTE]
>Als een invoer InventoryItem een item vertegenwoordigt dat niet in de catalogus kan worden gevonden, wordt het niet opgenomen in de uitvoer verzameling.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 1021
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 4acb26a1-3536-4081-bc7d-092869a4961a
MS-RequestId: d1b1981a-e088-4610-870a-eebec96d6bcd
X-Locale: en-US
[
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "0039",
        "isRestricted": true,
        "restrictions": [
            {
                "reasonCode": "NotAvailableForSubscription",
                "description": "Restriction identified of type 'Location' with values 'japanwest'.",
                "properties": {
                    "type": "Location",
                    "values": "japanwest"
                }
            }
        ]
    },
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "0038",
        "isRestricted": true,
        "restrictions": [
            {
                "reasonCode": "NotAvailableForSubscription",
                "description": "Restriction identified of type 'Location' with values 'japanwest'.",
                "properties": {
                    "type": "Location",
                    "values": "japanwest"
                }
            }
        ]
    },
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "000S",
        "isRestricted": false,
        "restrictions": []
    },
    {
        "productId": "DZH318Z0BQ3P",
        "skuId": "0011",
        "isRestricted": false,
        "restrictions": []
    }
]
```
