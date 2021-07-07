---
title: Een SKU ophalen op basis van id
description: Hiermee haalt u een SKU op voor het opgegeven product met behulp van de opgegeven SKU-id.
ms.date: 01/08/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 9516a87a438a0a84a6f6069c1f9b2a2e97e90fba
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873850"
---
# <a name="get-a-sku-by-id"></a><span data-ttu-id="fdff2-103">Een SKU ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="fdff2-103">Get a SKU by ID</span></span>

<span data-ttu-id="fdff2-104">Hiermee haalt u een SKU op voor het opgegeven product met behulp van de opgegeven SKU-id.</span><span class="sxs-lookup"><span data-stu-id="fdff2-104">Gets a SKU for the specified product using the specified SKU ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fdff2-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fdff2-105">Prerequisites</span></span>

- <span data-ttu-id="fdff2-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fdff2-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fdff2-107">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="fdff2-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="fdff2-108">Een product-id.</span><span class="sxs-lookup"><span data-stu-id="fdff2-108">A product ID.</span></span>

- <span data-ttu-id="fdff2-109">Een SKU-id.</span><span class="sxs-lookup"><span data-stu-id="fdff2-109">A SKU ID.</span></span>

## <a name="c"></a><span data-ttu-id="fdff2-110">C\#</span><span class="sxs-lookup"><span data-stu-id="fdff2-110">C\#</span></span>

<span data-ttu-id="fdff2-111">Als u de details van een specifieke SKU wilt weten, volgt u eerst de stappen in Een [product op id](get-a-product-by-id.md) op halen om de interface voor de bewerkingen van een specifiek product op te halen.</span><span class="sxs-lookup"><span data-stu-id="fdff2-111">To get the details of a specific SKU, start by following the steps in [Get a product by ID](get-a-product-by-id.md) to get the interface for a specific product's operations.</span></span> <span data-ttu-id="fdff2-112">Selecteer in de resulterende interface de eigenschap **Skus** om een interface te verkrijgen met de beschikbare bewerkingen voor SKU's.</span><span class="sxs-lookup"><span data-stu-id="fdff2-112">From the resulting interface, select the **Skus** property to obtain an interface with the available operations for SKUs.</span></span> <span data-ttu-id="fdff2-113">Geef de SKU-id door aan de **methode ById()** en roep **Get()** of **GetAsync()** aan om de SKU-details op te halen.</span><span class="sxs-lookup"><span data-stu-id="fdff2-113">Pass the SKU ID to the **ById()** method, and call **Get()** or **GetAsync()** to retrieve the SKU details.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;

// Get the SKU details.
var sku = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Get();
```

## <a name="rest-request"></a><span data-ttu-id="fdff2-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fdff2-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fdff2-115">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="fdff2-115">Request syntax</span></span>

| <span data-ttu-id="fdff2-116">Methode</span><span class="sxs-lookup"><span data-stu-id="fdff2-116">Method</span></span>  | <span data-ttu-id="fdff2-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fdff2-117">Request URI</span></span>                                                                                                         |
|---------|---------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fdff2-118">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fdff2-118">**GET**</span></span> | <span data-ttu-id="fdff2-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}?country={country-code} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fdff2-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}?country={country-code} HTTP/1.1</span></span>   |

### <a name="uri-parameter"></a><span data-ttu-id="fdff2-120">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="fdff2-120">URI parameter</span></span>

<span data-ttu-id="fdff2-121">Gebruik het volgende pad en de queryparameters om een SKU voor het opgegeven product op te halen met behulp van de opgegeven SKU-id.</span><span class="sxs-lookup"><span data-stu-id="fdff2-121">Use the following path and query parameters to get a SKU for the specified product using the specified SKU ID.</span></span>

| <span data-ttu-id="fdff2-122">Naam</span><span class="sxs-lookup"><span data-stu-id="fdff2-122">Name</span></span>                   | <span data-ttu-id="fdff2-123">Type</span><span class="sxs-lookup"><span data-stu-id="fdff2-123">Type</span></span>     | <span data-ttu-id="fdff2-124">Vereist</span><span class="sxs-lookup"><span data-stu-id="fdff2-124">Required</span></span> | <span data-ttu-id="fdff2-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fdff2-125">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="fdff2-126">product-id</span><span class="sxs-lookup"><span data-stu-id="fdff2-126">product-id</span></span>             | <span data-ttu-id="fdff2-127">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdff2-127">string</span></span>   | <span data-ttu-id="fdff2-128">Ja</span><span class="sxs-lookup"><span data-stu-id="fdff2-128">Yes</span></span>      | <span data-ttu-id="fdff2-129">Een tekenreeks die het product identificeert.</span><span class="sxs-lookup"><span data-stu-id="fdff2-129">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="fdff2-130">sku-id</span><span class="sxs-lookup"><span data-stu-id="fdff2-130">sku-id</span></span>                 | <span data-ttu-id="fdff2-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdff2-131">string</span></span>   | <span data-ttu-id="fdff2-132">Ja</span><span class="sxs-lookup"><span data-stu-id="fdff2-132">Yes</span></span>      | <span data-ttu-id="fdff2-133">Een tekenreeks die de SKU identificeert.</span><span class="sxs-lookup"><span data-stu-id="fdff2-133">A string that identifies the SKU.</span></span>                               |
| <span data-ttu-id="fdff2-134">country-code</span><span class="sxs-lookup"><span data-stu-id="fdff2-134">country-code</span></span>           | <span data-ttu-id="fdff2-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdff2-135">string</span></span>   | <span data-ttu-id="fdff2-136">Ja</span><span class="sxs-lookup"><span data-stu-id="fdff2-136">Yes</span></span>      | <span data-ttu-id="fdff2-137">Een land-/regio-id.</span><span class="sxs-lookup"><span data-stu-id="fdff2-137">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="fdff2-138">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fdff2-138">Request headers</span></span>

<span data-ttu-id="fdff2-139">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="fdff2-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fdff2-140">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fdff2-140">Request body</span></span>

<span data-ttu-id="fdff2-141">Geen.</span><span class="sxs-lookup"><span data-stu-id="fdff2-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="fdff2-142">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fdff2-142">Request example</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3V/skus/00G1?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e0ae69a5-6322-4d7e-809d-59e02b51d71f
MS-CorrelationId: 956eae17-7650-4470-94d2-4f61b9b02a23
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="fdff2-143">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fdff2-143">REST response</span></span>

<span data-ttu-id="fdff2-144">Als dit lukt, bevat de antwoord-body een [SKU-resource.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="fdff2-144">If successful, the response body contains a [SKU](product-resources.md#sku) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fdff2-145">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="fdff2-145">Response success and error codes</span></span>

<span data-ttu-id="fdff2-146">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="fdff2-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fdff2-147">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fdff2-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fdff2-148">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="fdff2-148">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="fdff2-149">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="fdff2-149">This method returns the following error codes:</span></span>

| <span data-ttu-id="fdff2-150">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="fdff2-150">HTTP Status Code</span></span>     | <span data-ttu-id="fdff2-151">Foutcode</span><span class="sxs-lookup"><span data-stu-id="fdff2-151">Error code</span></span>   | <span data-ttu-id="fdff2-152">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fdff2-152">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fdff2-153">404</span><span class="sxs-lookup"><span data-stu-id="fdff2-153">404</span></span>                  | <span data-ttu-id="fdff2-154">400013</span><span class="sxs-lookup"><span data-stu-id="fdff2-154">400013</span></span>       | <span data-ttu-id="fdff2-155">Product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="fdff2-155">Product was not found.</span></span>                                                                                    |
| <span data-ttu-id="fdff2-156">404</span><span class="sxs-lookup"><span data-stu-id="fdff2-156">404</span></span>                  | <span data-ttu-id="fdff2-157">400018</span><span class="sxs-lookup"><span data-stu-id="fdff2-157">400018</span></span>       | <span data-ttu-id="fdff2-158">SKU is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="fdff2-158">Sku was not found.</span></span>                                                                                        |

### <a name="response-example"></a><span data-ttu-id="fdff2-159">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fdff2-159">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 956eae17-7650-4470-94d2-4f61b9b02a23,956eae17-7650-4470-94d2-4f61b9b02a23
MS-RequestId: e0ae69a5-6322-4d7e-809d-59e02b51d71f,e0ae69a5-6322-4d7e-809d-59e02b51d71f
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTNWXHNrdXNcMDBHMQ==?=
X-Powered-By: ASP.NET
Date: Thu, 15 Mar 2018 17:43:25 GMT
Content-Length: 1108

{
    "id": "00G1",
    "productId": "DZH318Z0BQ3V",
    "title": "Reserved VM Instance, Standard_D32s_v3, US West 2, 3 Years",
    "description": "Reserved Virtual Machines Instance, Standard_D32s_v3, US West 2, 3 Years",
    "minimumQuantity": 1,
    "maximumQuantity": 999999999,
    "isTrial": false,
    "supportedBillingCycles": [
        "one_time"
    ],
    "purchasePrerequisites": [
        "AzureSubscriptionRegistration",
        "InventoryCheck"
    ],
    "inventoryVariables": [
        "CustomerId",
        "AzureSubscriptionId"
    ],
    "provisioningVariables": [
        "Scope",
        "SubscriptionId"
    ],
    "dynamicAttributes": {
        "armSkuName": "Standard_D32s_v3",
        "cores": "32",
        "ram": "128",
        "skuDisplayName": "D32s v3",
        "category": "General purpose",
        "armRegionName": "westus2",
        "duration": "3Years",
        "region": "US West 2",
        "diskType": "Ssd"
    },
    "links": {
        "availabilities": {
            "uri": "/products/DZH318Z0BQ3V/skus/00G1/availabilities?country=us",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/products/DZH318Z0BQ3V/skus/00G1?country=us",
            "method": "GET",
            "headers": []
        }
    }
}
```
