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
# <a name="check-the-inventory-of-catalog-items-using-partner-center-apis"></a><span data-ttu-id="c7f58-104">De inventaris van catalogusitems controleren met behulp Partner Center API's</span><span class="sxs-lookup"><span data-stu-id="c7f58-104">Check the inventory of catalog items using Partner Center APIs</span></span>

<span data-ttu-id="c7f58-105">De inventaris controleren op een specifieke set catalogusitems.</span><span class="sxs-lookup"><span data-stu-id="c7f58-105">How to check the inventory for a specific set of catalog items.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7f58-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c7f58-106">Prerequisites</span></span>

- <span data-ttu-id="c7f58-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c7f58-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c7f58-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="c7f58-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="c7f58-109">Een of meer product-ID's.</span><span class="sxs-lookup"><span data-stu-id="c7f58-109">One or more product IDs.</span></span> <span data-ttu-id="c7f58-110">Optioneel kunnen ook SKU-ID's worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="c7f58-110">Optionally, SKU IDs can also be specified.</span></span>

- <span data-ttu-id="c7f58-111">Eventuele aanvullende context die nodig is voor het controleren van de inventaris van de SKU('s) waarnaar wordt verwezen door de opgegeven product-/SKU-id('s).</span><span class="sxs-lookup"><span data-stu-id="c7f58-111">Any additional context needed for verifying the inventory of the SKU(s) referenced by the provided product/SKU ID(s).</span></span> <span data-ttu-id="c7f58-112">Deze vereisten kunnen per product/SKU verschillen en kunnen worden bepaald op basis van de eigenschap **InventoryVariables van de** [SKU.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="c7f58-112">These requirements may vary by type of product/SKU and can be determined from the [SKU's](product-resources.md#sku) **InventoryVariables** property.</span></span>

## <a name="c"></a><span data-ttu-id="c7f58-113">C\#</span><span class="sxs-lookup"><span data-stu-id="c7f58-113">C\#</span></span>

<span data-ttu-id="c7f58-114">Als u de inventaris wilt controleren, maakt u [een InventoryCheckRequest-object](product-resources.md#inventorycheckrequest) met behulp van een [InventoryItem-object](product-resources.md#inventoryitem) voor elk item dat moet worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="c7f58-114">To check the inventory, build an [InventoryCheckRequest](product-resources.md#inventorycheckrequest) object using an [InventoryItem](product-resources.md#inventoryitem) object for each item to be checked.</span></span> <span data-ttu-id="c7f58-115">Gebruik vervolgens een **iAggregatePartner.Extensions-accessoires,** pas het bereik aan op **Product** en selecteer vervolgens het land met behulp van de **methode ByCountry().**</span><span class="sxs-lookup"><span data-stu-id="c7f58-115">Then, use an **IAggregatePartner.Extensions** accessor, scope it down to **Product** and then select the country using the **ByCountry()** method.</span></span> <span data-ttu-id="c7f58-116">Roep ten slotte de **methode CheckInventory()** aan met uw **InventoryCheckRequest-object.**</span><span class="sxs-lookup"><span data-stu-id="c7f58-116">Finally, call the **CheckInventory()** method with your **InventoryCheckRequest** object.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="c7f58-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c7f58-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c7f58-118">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="c7f58-118">Request syntax</span></span>

| <span data-ttu-id="c7f58-119">Methode</span><span class="sxs-lookup"><span data-stu-id="c7f58-119">Method</span></span>   | <span data-ttu-id="c7f58-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c7f58-120">Request URI</span></span>                                                                                                                              |
|----------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c7f58-121">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="c7f58-121">**POST**</span></span> | <span data-ttu-id="c7f58-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/extensions/product/checkInventory?country={country-code} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c7f58-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/extensions/product/checkInventory?country={country-code} HTTP/1.1</span></span>                        |

### <a name="uri-parameter"></a><span data-ttu-id="c7f58-123">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="c7f58-123">URI parameter</span></span>

<span data-ttu-id="c7f58-124">Gebruik de volgende queryparameter om de inventaris te controleren.</span><span class="sxs-lookup"><span data-stu-id="c7f58-124">Use the following query parameter to check the inventory.</span></span>

| <span data-ttu-id="c7f58-125">Naam</span><span class="sxs-lookup"><span data-stu-id="c7f58-125">Name</span></span>                   | <span data-ttu-id="c7f58-126">Type</span><span class="sxs-lookup"><span data-stu-id="c7f58-126">Type</span></span>     | <span data-ttu-id="c7f58-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="c7f58-127">Required</span></span> | <span data-ttu-id="c7f58-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c7f58-128">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="c7f58-129">country-code</span><span class="sxs-lookup"><span data-stu-id="c7f58-129">country-code</span></span>           | <span data-ttu-id="c7f58-130">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="c7f58-130">string</span></span>   | <span data-ttu-id="c7f58-131">Ja</span><span class="sxs-lookup"><span data-stu-id="c7f58-131">Yes</span></span>      | <span data-ttu-id="c7f58-132">Een land-/regio-id.</span><span class="sxs-lookup"><span data-stu-id="c7f58-132">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="c7f58-133">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c7f58-133">Request headers</span></span>

<span data-ttu-id="c7f58-134">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="c7f58-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c7f58-135">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c7f58-135">Request body</span></span>

<span data-ttu-id="c7f58-136">De details van de inventarisaanvraag, bestaande uit een [InventoryCheckRequest-resource](product-resources.md#inventorycheckrequest) die een of meer [InventoryItem-resources](product-resources.md#inventoryitem) bevat.</span><span class="sxs-lookup"><span data-stu-id="c7f58-136">The inventory request details, consisting of an [InventoryCheckRequest](product-resources.md#inventorycheckrequest) resource containing one or more [InventoryItem](product-resources.md#inventoryitem) resources.</span></span>

### <a name="request-example"></a><span data-ttu-id="c7f58-137">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c7f58-137">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="c7f58-138">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c7f58-138">REST response</span></span>

<span data-ttu-id="c7f58-139">Als dit lukt, bevat de antwoord-body een verzameling [InventoryItem-objecten](product-resources.md#inventoryitem) die zijn gevuld met de beperkingsdetails, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="c7f58-139">If successful, the response body contains a collection of [InventoryItem](product-resources.md#inventoryitem) objects populated with the restriction details, if any apply.</span></span>

>[!NOTE]
><span data-ttu-id="c7f58-140">Als een input InventoryItem een item vertegenwoordigt dat niet in de catalogus kan worden gevonden, wordt het niet opgenomen in de uitvoerverzameling.</span><span class="sxs-lookup"><span data-stu-id="c7f58-140">If an input InventoryItem represents an item that could not be found in the catalog, it will not be included in the output collection.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c7f58-141">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="c7f58-141">Response success and error codes</span></span>

<span data-ttu-id="c7f58-142">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="c7f58-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c7f58-143">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c7f58-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c7f58-144">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="c7f58-144">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c7f58-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c7f58-145">Response example</span></span>

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
