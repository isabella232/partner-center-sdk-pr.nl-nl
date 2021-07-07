---
title: Inventaris controleren
description: Meer informatie over het gebruik Partner Center API's om de inventaris voor een specifieke set catalogusitems te controleren. U kunt dit doen om de producten of SKU's van een klant te identificeren.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b982dbd7e5e10d454ef87a1e750546ea50eb8438
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974077"
---
# <a name="check-the-inventory-of-catalog-items-using-partner-center-apis"></a>De inventaris van catalogusitems controleren met behulp Partner Center API's

De inventaris controleren op een specifieke set catalogusitems.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een of meer product-ID's. Optioneel kunnen ook SKU-ID's worden opgegeven.

- Eventuele aanvullende context die nodig is voor het controleren van de inventaris van de SKU('s) waarnaar wordt verwezen door de opgegeven product-/SKU-id('s). Deze vereisten kunnen per product/SKU verschillen en kunnen worden bepaald op basis van de eigenschap **InventoryVariables van de** [SKU.](product-resources.md#sku)

## <a name="c"></a>C\#

Als u de inventaris wilt controleren, maakt u [een InventoryCheckRequest-object](product-resources.md#inventorycheckrequest) met behulp van een [InventoryItem-object](product-resources.md#inventoryitem) voor elk item dat moet worden gecontroleerd. Gebruik vervolgens een **iAggregatePartner.Extensions-accessoires,** pas het bereik aan op **Product** en selecteer vervolgens het land met behulp van de **methode ByCountry().** Roep ten slotte de **methode CheckInventory()** aan met uw **InventoryCheckRequest-object.**

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

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                                              |
|----------|------------------------------------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/extensions/product/checkInventory?country={country-code} HTTP/1.1                        |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de inventaris te controleren.

| Naam                   | Type     | Vereist | Beschrijving                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| country-code           | tekenreeks   | Ja      | Een land-/regio-id.                                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

De details van de inventarisaanvraag, bestaande uit een [InventoryCheckRequest-resource](product-resources.md#inventorycheckrequest) die een of meer [InventoryItem-resources](product-resources.md#inventoryitem) bevat.

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

Als dit lukt, bevat de antwoord-body een verzameling [InventoryItem-objecten](product-resources.md#inventoryitem) die zijn gevuld met de beperkingsdetails, indien van toepassing.

>[!NOTE]
>Als een input InventoryItem een item vertegenwoordigt dat niet in de catalogus kan worden gevonden, wordt het niet opgenomen in de uitvoerverzameling.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).

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
