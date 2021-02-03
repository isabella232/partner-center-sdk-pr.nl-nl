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
# <a name="check-the-inventory-of-catalog-items-using-partner-center-apis"></a><span data-ttu-id="970a7-104">De inventaris van catalogus items controleren met behulp van partner Center-Api's</span><span class="sxs-lookup"><span data-stu-id="970a7-104">Check the inventory of catalog items using Partner Center APIs</span></span>

<span data-ttu-id="970a7-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="970a7-105">**Applies to:**</span></span>

- <span data-ttu-id="970a7-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="970a7-106">Partner Center</span></span>

<span data-ttu-id="970a7-107">De inventarisatie controleren voor een specifieke set met catalogus items.</span><span class="sxs-lookup"><span data-stu-id="970a7-107">How to check the inventory for a specific set of catalog items.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="970a7-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="970a7-108">Prerequisites</span></span>

- <span data-ttu-id="970a7-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="970a7-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="970a7-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="970a7-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="970a7-111">Een of meer product-Id's.</span><span class="sxs-lookup"><span data-stu-id="970a7-111">One or more product IDs.</span></span> <span data-ttu-id="970a7-112">Optioneel kunnen SKU-Id's ook worden opgegeven.</span><span class="sxs-lookup"><span data-stu-id="970a7-112">Optionally, SKU IDs can also be specified.</span></span>

- <span data-ttu-id="970a7-113">Eventuele aanvullende context voor het controleren van de inventaris van de SKU ('s) waarnaar wordt verwezen door de gegeven product-of SKU-ID ('s).</span><span class="sxs-lookup"><span data-stu-id="970a7-113">Any additional context needed for verifying the inventory of the SKU(s) referenced by the provided product/SKU ID(s).</span></span> <span data-ttu-id="970a7-114">Deze vereisten kunnen variëren per type product/SKU en kunnen worden bepaald op basis van de **InventoryVariables** -eigenschap van de [SKU](product-resources.md#sku) .</span><span class="sxs-lookup"><span data-stu-id="970a7-114">These requirements may vary by type of product/SKU and can be determined from the [SKU's](product-resources.md#sku) **InventoryVariables** property.</span></span>

## <a name="c"></a><span data-ttu-id="970a7-115">C\#</span><span class="sxs-lookup"><span data-stu-id="970a7-115">C\#</span></span>

<span data-ttu-id="970a7-116">Als u de inventarisatie wilt controleren, bouwt u een [InventoryCheckRequest](product-resources.md#inventorycheckrequest) -object op met behulp van een [InventoryItem](product-resources.md#inventoryitem) -object voor elk item dat moet worden gecontroleerd.</span><span class="sxs-lookup"><span data-stu-id="970a7-116">To check the inventory, build an [InventoryCheckRequest](product-resources.md#inventorycheckrequest) object using an [InventoryItem](product-resources.md#inventoryitem) object for each item to be checked.</span></span> <span data-ttu-id="970a7-117">Gebruik vervolgens een **IAggregatePartner. Extensions** -accessor, bereik deze aan **product** en selecteer vervolgens het land met de methode **ByCountry ()** .</span><span class="sxs-lookup"><span data-stu-id="970a7-117">Then, use an **IAggregatePartner.Extensions** accessor, scope it down to **Product** and then select the country using the **ByCountry()** method.</span></span> <span data-ttu-id="970a7-118">Roep ten slotte de methode **CheckInventory ()** aan bij uw **InventoryCheckRequest** -object.</span><span class="sxs-lookup"><span data-stu-id="970a7-118">Finally, call the **CheckInventory()** method with your **InventoryCheckRequest** object.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="970a7-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="970a7-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="970a7-120">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="970a7-120">Request syntax</span></span>

| <span data-ttu-id="970a7-121">Methode</span><span class="sxs-lookup"><span data-stu-id="970a7-121">Method</span></span>   | <span data-ttu-id="970a7-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="970a7-122">Request URI</span></span>                                                                                                                              |
|----------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="970a7-123">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="970a7-123">**POST**</span></span> | <span data-ttu-id="970a7-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/Extensions/product/checkInventory? land = {land nummer} http/1.1</span><span class="sxs-lookup"><span data-stu-id="970a7-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/extensions/product/checkInventory?country={country-code} HTTP/1.1</span></span>                        |

### <a name="uri-parameter"></a><span data-ttu-id="970a7-125">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="970a7-125">URI parameter</span></span>

<span data-ttu-id="970a7-126">Gebruik de volgende query parameter om de inventaris te controleren.</span><span class="sxs-lookup"><span data-stu-id="970a7-126">Use the following query parameter to check the inventory.</span></span>

| <span data-ttu-id="970a7-127">Naam</span><span class="sxs-lookup"><span data-stu-id="970a7-127">Name</span></span>                   | <span data-ttu-id="970a7-128">Type</span><span class="sxs-lookup"><span data-stu-id="970a7-128">Type</span></span>     | <span data-ttu-id="970a7-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="970a7-129">Required</span></span> | <span data-ttu-id="970a7-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="970a7-130">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="970a7-131">land code</span><span class="sxs-lookup"><span data-stu-id="970a7-131">country-code</span></span>           | <span data-ttu-id="970a7-132">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="970a7-132">string</span></span>   | <span data-ttu-id="970a7-133">Yes</span><span class="sxs-lookup"><span data-stu-id="970a7-133">Yes</span></span>      | <span data-ttu-id="970a7-134">Een land/regio-ID.</span><span class="sxs-lookup"><span data-stu-id="970a7-134">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="970a7-135">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="970a7-135">Request headers</span></span>

<span data-ttu-id="970a7-136">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="970a7-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="970a7-137">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="970a7-137">Request body</span></span>

<span data-ttu-id="970a7-138">De details van de inventarisatie aanvraag, bestaande uit een [InventoryCheckRequest](product-resources.md#inventorycheckrequest) -resource met een of meer [InventoryItem](product-resources.md#inventoryitem) -resources.</span><span class="sxs-lookup"><span data-stu-id="970a7-138">The inventory request details, consisting of an [InventoryCheckRequest](product-resources.md#inventorycheckrequest) resource containing one or more [InventoryItem](product-resources.md#inventoryitem) resources.</span></span>

### <a name="request-example"></a><span data-ttu-id="970a7-139">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="970a7-139">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="970a7-140">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="970a7-140">REST response</span></span>

<span data-ttu-id="970a7-141">Als dit lukt, bevat de antwoord tekst een verzameling [InventoryItem](product-resources.md#inventoryitem) -objecten die zijn gevuld met de beperkings Details, indien van toepassing.</span><span class="sxs-lookup"><span data-stu-id="970a7-141">If successful, the response body contains a collection of [InventoryItem](product-resources.md#inventoryitem) objects populated with the restriction details, if any apply.</span></span>

>[!NOTE]
><span data-ttu-id="970a7-142">Als een invoer InventoryItem een item vertegenwoordigt dat niet in de catalogus kan worden gevonden, wordt het niet opgenomen in de uitvoer verzameling.</span><span class="sxs-lookup"><span data-stu-id="970a7-142">If an input InventoryItem represents an item that could not be found in the catalog, it will not be included in the output collection.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="970a7-143">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="970a7-143">Response success and error codes</span></span>

<span data-ttu-id="970a7-144">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="970a7-144">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="970a7-145">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="970a7-145">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="970a7-146">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="970a7-146">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="970a7-147">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="970a7-147">Response example</span></span>

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
