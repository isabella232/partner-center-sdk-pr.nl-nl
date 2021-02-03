---
title: Een SKU ophalen op basis van id
description: Hiermee wordt een SKU opgehaald voor het opgegeven product met behulp van de opgegeven SKU-ID.
ms.date: 01/08/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 54ef72413d2d2b9e7154e82e4bbdd7427a79a2dd
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767291"
---
# <a name="get-a-sku-by-id"></a><span data-ttu-id="38799-103">Een SKU ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="38799-103">Get a SKU by ID</span></span>

<span data-ttu-id="38799-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="38799-104">**Applies To**</span></span>

- <span data-ttu-id="38799-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="38799-105">Partner Center</span></span>

<span data-ttu-id="38799-106">Hiermee wordt een SKU opgehaald voor het opgegeven product met behulp van de opgegeven SKU-ID.</span><span class="sxs-lookup"><span data-stu-id="38799-106">Gets a SKU for the specified product using the specified SKU ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="38799-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="38799-107">Prerequisites</span></span>

- <span data-ttu-id="38799-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="38799-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="38799-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="38799-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="38799-110">Een product-ID.</span><span class="sxs-lookup"><span data-stu-id="38799-110">A product ID.</span></span>

- <span data-ttu-id="38799-111">EEN SKU-ID.</span><span class="sxs-lookup"><span data-stu-id="38799-111">A SKU ID.</span></span>

## <a name="c"></a><span data-ttu-id="38799-112">C\#</span><span class="sxs-lookup"><span data-stu-id="38799-112">C\#</span></span>

<span data-ttu-id="38799-113">Als u de details van een specifieke SKU wilt ophalen, gaat u eerst aan de hand van de stappen in [een product ophalen op id](get-a-product-by-id.md) om de interface voor de bewerkingen van een specifiek product op te halen.</span><span class="sxs-lookup"><span data-stu-id="38799-113">To get the details of a specific SKU, start by following the steps in [Get a product by ID](get-a-product-by-id.md) to get the interface for a specific product's operations.</span></span> <span data-ttu-id="38799-114">Selecteer in de resulterende interface de eigenschap **sku's** om een interface te verkrijgen met de beschik bare bewerkingen voor sku's.</span><span class="sxs-lookup"><span data-stu-id="38799-114">From the resulting interface, select the **Skus** property to obtain an interface with the available operations for SKUs.</span></span> <span data-ttu-id="38799-115">Geef de SKU-ID door aan de methode **ById ()** en roep **Get ()** of **GetAsync (** ) aan om de SKU-gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="38799-115">Pass the SKU ID to the **ById()** method, and call **Get()** or **GetAsync()** to retrieve the SKU details.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;

// Get the SKU details.
var sku = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Get();
```

## <a name="rest-request"></a><span data-ttu-id="38799-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="38799-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="38799-117">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="38799-117">Request syntax</span></span>

| <span data-ttu-id="38799-118">Methode</span><span class="sxs-lookup"><span data-stu-id="38799-118">Method</span></span>  | <span data-ttu-id="38799-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="38799-119">Request URI</span></span>                                                                                                         |
|---------|---------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="38799-120">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="38799-120">**GET**</span></span> | <span data-ttu-id="38799-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/SKUs/{SKU-id}? land = {land nummer} http/1.1</span><span class="sxs-lookup"><span data-stu-id="38799-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}?country={country-code} HTTP/1.1</span></span>   |

### <a name="uri-parameter"></a><span data-ttu-id="38799-122">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="38799-122">URI parameter</span></span>

<span data-ttu-id="38799-123">Gebruik de volgende pad-en query parameters om een SKU voor het opgegeven product op te halen met behulp van de opgegeven SKU-ID.</span><span class="sxs-lookup"><span data-stu-id="38799-123">Use the following path and query parameters to get a SKU for the specified product using the specified SKU ID.</span></span>

| <span data-ttu-id="38799-124">Naam</span><span class="sxs-lookup"><span data-stu-id="38799-124">Name</span></span>                   | <span data-ttu-id="38799-125">Type</span><span class="sxs-lookup"><span data-stu-id="38799-125">Type</span></span>     | <span data-ttu-id="38799-126">Vereist</span><span class="sxs-lookup"><span data-stu-id="38799-126">Required</span></span> | <span data-ttu-id="38799-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="38799-127">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="38799-128">product-id</span><span class="sxs-lookup"><span data-stu-id="38799-128">product-id</span></span>             | <span data-ttu-id="38799-129">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="38799-129">string</span></span>   | <span data-ttu-id="38799-130">Yes</span><span class="sxs-lookup"><span data-stu-id="38799-130">Yes</span></span>      | <span data-ttu-id="38799-131">Een teken reeks waarmee het product wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="38799-131">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="38799-132">SKU-id</span><span class="sxs-lookup"><span data-stu-id="38799-132">sku-id</span></span>                 | <span data-ttu-id="38799-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="38799-133">string</span></span>   | <span data-ttu-id="38799-134">Yes</span><span class="sxs-lookup"><span data-stu-id="38799-134">Yes</span></span>      | <span data-ttu-id="38799-135">Een teken reeks waarmee de SKU wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="38799-135">A string that identifies the SKU.</span></span>                               |
| <span data-ttu-id="38799-136">land code</span><span class="sxs-lookup"><span data-stu-id="38799-136">country-code</span></span>           | <span data-ttu-id="38799-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="38799-137">string</span></span>   | <span data-ttu-id="38799-138">Yes</span><span class="sxs-lookup"><span data-stu-id="38799-138">Yes</span></span>      | <span data-ttu-id="38799-139">Een land/regio-ID.</span><span class="sxs-lookup"><span data-stu-id="38799-139">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="38799-140">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="38799-140">Request headers</span></span>

<span data-ttu-id="38799-141">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="38799-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="38799-142">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="38799-142">Request body</span></span>

<span data-ttu-id="38799-143">Geen.</span><span class="sxs-lookup"><span data-stu-id="38799-143">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="38799-144">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="38799-144">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="38799-145">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="38799-145">REST response</span></span>

<span data-ttu-id="38799-146">Als dit lukt, bevat de antwoord tekst een [SKU](product-resources.md#sku) -resource.</span><span class="sxs-lookup"><span data-stu-id="38799-146">If successful, the response body contains a [SKU](product-resources.md#sku) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="38799-147">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="38799-147">Response success and error codes</span></span>

<span data-ttu-id="38799-148">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="38799-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="38799-149">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="38799-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="38799-150">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="38799-150">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="38799-151">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="38799-151">This method returns the following error codes:</span></span>

| <span data-ttu-id="38799-152">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="38799-152">HTTP Status Code</span></span>     | <span data-ttu-id="38799-153">Foutcode</span><span class="sxs-lookup"><span data-stu-id="38799-153">Error code</span></span>   | <span data-ttu-id="38799-154">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="38799-154">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="38799-155">404</span><span class="sxs-lookup"><span data-stu-id="38799-155">404</span></span>                  | <span data-ttu-id="38799-156">400013</span><span class="sxs-lookup"><span data-stu-id="38799-156">400013</span></span>       | <span data-ttu-id="38799-157">Het product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="38799-157">Product was not found.</span></span>                                                                                    |
| <span data-ttu-id="38799-158">404</span><span class="sxs-lookup"><span data-stu-id="38799-158">404</span></span>                  | <span data-ttu-id="38799-159">400018</span><span class="sxs-lookup"><span data-stu-id="38799-159">400018</span></span>       | <span data-ttu-id="38799-160">SKU is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="38799-160">Sku was not found.</span></span>                                                                                        |

### <a name="response-example"></a><span data-ttu-id="38799-161">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="38799-161">Response example</span></span>

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
