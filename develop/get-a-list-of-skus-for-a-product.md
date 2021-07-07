---
title: Een lijst met SKU’s voor een product ophalen (per land/regio)
description: U kunt een verzameling SKU's per land ophalen en filteren voor een product met behulp van Partner Center API's.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 27a2391a22a9439461fb53764b87c1cafa68b875
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873884"
---
# <a name="get-a-list-of-skus-for-a-product-by-country"></a><span data-ttu-id="55e43-103">Een lijst met SKU’s voor een product ophalen (per land/regio)</span><span class="sxs-lookup"><span data-stu-id="55e43-103">Get a list of SKUs for a product (by country)</span></span>

<span data-ttu-id="55e43-104">U kunt een verzameling SKU's ophalen die beschikbaar zijn in een land voor een specifiek product met behulp Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="55e43-104">You can get a collection of SKUs available in a country for a specific product using Partner Center APIs.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="55e43-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="55e43-105">Prerequisites</span></span>

- <span data-ttu-id="55e43-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="55e43-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="55e43-107">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="55e43-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="55e43-108">Een product-id.</span><span class="sxs-lookup"><span data-stu-id="55e43-108">A product identifier.</span></span>

## <a name="c"></a><span data-ttu-id="55e43-109">C\#</span><span class="sxs-lookup"><span data-stu-id="55e43-109">C\#</span></span>

<span data-ttu-id="55e43-110">De lijst met SKU's voor een product op te halen:</span><span class="sxs-lookup"><span data-stu-id="55e43-110">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="55e43-111">Haal een interface op voor de bewerkingen van een specifiek product door de stappen in [Een product op id krijgen te volgen.](get-a-product-by-id.md)</span><span class="sxs-lookup"><span data-stu-id="55e43-111">Get an interface for a specific product's operations by following the steps in [Get a product by ID](get-a-product-by-id.md).</span></span>

2. <span data-ttu-id="55e43-112">Selecteer in de interface de eigenschap **SKU's** om een interface te verkrijgen met de beschikbare bewerkingen voor SKU's.</span><span class="sxs-lookup"><span data-stu-id="55e43-112">From the interface, select the **Skus** property to obtain an interface with the available operations for SKUs.</span></span>

3. <span data-ttu-id="55e43-113">Roep de **methode Get()** of **GetAsync()** aan om een verzameling van de beschikbare SKU's voor het product op te halen.</span><span class="sxs-lookup"><span data-stu-id="55e43-113">Call the **Get()** or **GetAsync()** method to retrieve a collection of the available SKUs for the product.</span></span>

4. <span data-ttu-id="55e43-114">(Optioneel) Selecteer het reserveringsbereik met behulp **van de methode ByReservationScope().**</span><span class="sxs-lookup"><span data-stu-id="55e43-114">(Optional) Select the reservation scope using the **ByReservationScope()** method.</span></span>

5. <span data-ttu-id="55e43-115">(Optioneel) Gebruik de **methode ByTargetSegment() om** de SKU's te filteren op doelsegment voordat u **Get()** of **GetAsync() aanroept.**</span><span class="sxs-lookup"><span data-stu-id="55e43-115">(Optional) Use the **ByTargetSegment()** method to filter the SKUs by target segment before calling **Get()** or **GetAsync()**.</span></span>

``` csharp
IAggregatePartner partnerOperations;

string countryCode;
string productId;
string productIdForAzureReservation;
string targetSegment;

// Get the available SKUs.
var skus = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.Get();

// Get the available SKUs, filtered by target segment.
var segmentSkus = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ByTargetSegment(targetSegment).Get();

// Get the skus for an Azure reservation product which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
var skus = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.Get();

// Get the skus for an Azure reservation product which are applicable to Azure plans only.
var skus = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.ByReservationScope("AzurePlan").Get();

```

## <a name="java"></a><span data-ttu-id="55e43-116">Java</span><span class="sxs-lookup"><span data-stu-id="55e43-116">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="55e43-117">De lijst met SKU's voor een product op te halen:</span><span class="sxs-lookup"><span data-stu-id="55e43-117">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="55e43-118">Haal een interface op voor de bewerkingen van een specifiek product door de stappen in [Een product op id krijgen te volgen.](get-a-product-by-id.md)</span><span class="sxs-lookup"><span data-stu-id="55e43-118">Get an interface for a specific product's operations by following the steps in [Get a product by ID](get-a-product-by-id.md).</span></span>

2. <span data-ttu-id="55e43-119">Selecteer in de interface de **functie getSkus** om een interface te verkrijgen met de beschikbare bewerkingen voor SKU's.</span><span class="sxs-lookup"><span data-stu-id="55e43-119">From the interface, select the **getSkus** function to obtain an interface with the available operations for SKUs.</span></span>

3. <span data-ttu-id="55e43-120">Roep de **functie get()** aan om een verzameling van de beschikbare SKU's voor het product op te halen.</span><span class="sxs-lookup"><span data-stu-id="55e43-120">Call the **get()** function to retrieve a collection of the available SKUs for the product.</span></span>

4. <span data-ttu-id="55e43-121">(Optioneel) Gebruik de **functie byTargetSegment() om** de SKU's te filteren op doelsegment voordat u de **functie get()** aanroept.</span><span class="sxs-lookup"><span data-stu-id="55e43-121">(Optional) Use the **byTargetSegment()** function to filter the SKUs by target segment before calling the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;

// String countryCode;
// String productId;
// String targetSegment;

// Get the available SKUs.
ResourceCollection<Sku> skus = partnerOperations.getProducts().byCountry(countryCode).byId(productId).getSkus().get();

// Get the available SKUs, filtered by target segment.
var segmentSkus = partnerOperations.getProducts().byCountry(countryCode).byId(productId).getSkus().byTargetSegment(targetSegment).get();
```

## <a name="powershell"></a><span data-ttu-id="55e43-122">PowerShell</span><span class="sxs-lookup"><span data-stu-id="55e43-122">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="55e43-123">De lijst met SKU's voor een product op te halen:</span><span class="sxs-lookup"><span data-stu-id="55e43-123">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="55e43-124">Voer de [**opdracht Get-PartnerProductSku**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductSku.md) uit.</span><span class="sxs-lookup"><span data-stu-id="55e43-124">Execute the [**Get-PartnerProductSku**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductSku.md) command.</span></span>

2. <span data-ttu-id="55e43-125">(Optioneel) Geef de **parameter Segment** op om de SKU's te filteren op doelsegment.</span><span class="sxs-lookup"><span data-stu-id="55e43-125">(Optional) Specify the **Segment** parameter to filter the SKUs by target segment.</span></span>

```powershell
# $productId
# $targetSegment

# Get the available SKUs.
Get-PartnerProductSku -ProductId $productId

# Get the available SKUs, filtered by target segment.
Get-PartnerProductSku -ProductId $productId -Segment $targetSegment
```

## <a name="rest-request"></a><span data-ttu-id="55e43-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="55e43-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="55e43-127">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="55e43-127">Request syntax</span></span>

| <span data-ttu-id="55e43-128">Methode</span><span class="sxs-lookup"><span data-stu-id="55e43-128">Method</span></span>  | <span data-ttu-id="55e43-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="55e43-129">Request URI</span></span>                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="55e43-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="55e43-130">**GET**</span></span> | <span data-ttu-id="55e43-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="55e43-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="55e43-132">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="55e43-132">URI parameters</span></span>

<span data-ttu-id="55e43-133">Gebruik het volgende pad en de queryparameters om een lijst met SKU's voor een product op te halen.</span><span class="sxs-lookup"><span data-stu-id="55e43-133">Use the following path and query parameters to get a list of SKUs for a product.</span></span>

| <span data-ttu-id="55e43-134">Naam</span><span class="sxs-lookup"><span data-stu-id="55e43-134">Name</span></span>                   | <span data-ttu-id="55e43-135">Type</span><span class="sxs-lookup"><span data-stu-id="55e43-135">Type</span></span>     | <span data-ttu-id="55e43-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="55e43-136">Required</span></span> | <span data-ttu-id="55e43-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="55e43-137">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="55e43-138">product-id</span><span class="sxs-lookup"><span data-stu-id="55e43-138">product-id</span></span>             | <span data-ttu-id="55e43-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="55e43-139">string</span></span>   | <span data-ttu-id="55e43-140">Ja</span><span class="sxs-lookup"><span data-stu-id="55e43-140">Yes</span></span>      | <span data-ttu-id="55e43-141">Een tekenreeks die het product identificeert.</span><span class="sxs-lookup"><span data-stu-id="55e43-141">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="55e43-142">country-code</span><span class="sxs-lookup"><span data-stu-id="55e43-142">country-code</span></span>           | <span data-ttu-id="55e43-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="55e43-143">string</span></span>   | <span data-ttu-id="55e43-144">Ja</span><span class="sxs-lookup"><span data-stu-id="55e43-144">Yes</span></span>      | <span data-ttu-id="55e43-145">Een land-/regio-id.</span><span class="sxs-lookup"><span data-stu-id="55e43-145">A country/region ID.</span></span>                                            |
| <span data-ttu-id="55e43-146">doelsegment</span><span class="sxs-lookup"><span data-stu-id="55e43-146">target-segment</span></span>         | <span data-ttu-id="55e43-147">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="55e43-147">string</span></span>   | <span data-ttu-id="55e43-148">No</span><span class="sxs-lookup"><span data-stu-id="55e43-148">No</span></span>       | <span data-ttu-id="55e43-149">Een tekenreeks die het doelsegment identificeert dat wordt gebruikt voor filteren.</span><span class="sxs-lookup"><span data-stu-id="55e43-149">A string that identifies the target segment used for filtering.</span></span> |
| <span data-ttu-id="55e43-150">reservationScope</span><span class="sxs-lookup"><span data-stu-id="55e43-150">reservationScope</span></span> | <span data-ttu-id="55e43-151">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="55e43-151">string</span></span>   | <span data-ttu-id="55e43-152">No</span><span class="sxs-lookup"><span data-stu-id="55e43-152">No</span></span> | <span data-ttu-id="55e43-153">Wanneer u een query uitvoert voor een lijst met SKU's voor een Azure Reservation-product, geeft u op om een lijst op te halen met SKU's die van `reservationScope=AzurePlan` toepassing zijn op AzurePlan.</span><span class="sxs-lookup"><span data-stu-id="55e43-153">When querying for a list of SKUs for an Azure Reservation product, specify `reservationScope=AzurePlan` to get a list of SKUs that are applicable to AzurePlan.</span></span> <span data-ttu-id="55e43-154">Sluit deze parameter uit om een lijst met SKU's voor Azure Reservation-producten op te halen die van toepassing zijn op Microsoft Azure-abonnementen (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="55e43-154">Exclude this parameter to get a list of SKUs for Azure Reservation products that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="55e43-155">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="55e43-155">Request headers</span></span>

<span data-ttu-id="55e43-156">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="55e43-156">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="55e43-157">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="55e43-157">Request body</span></span>

<span data-ttu-id="55e43-158">Geen.</span><span class="sxs-lookup"><span data-stu-id="55e43-158">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="55e43-159">Voorbeelden van aanvragen</span><span class="sxs-lookup"><span data-stu-id="55e43-159">Request examples</span></span>

<span data-ttu-id="55e43-160">Een lijst met SKU's voor een bepaald product op te halen:</span><span class="sxs-lookup"><span data-stu-id="55e43-160">Get a list of SKUs for a given product:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BPS6/skus?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

<span data-ttu-id="55e43-161">Haal een lijst met SKU's op voor een Azure Reservation-product.</span><span class="sxs-lookup"><span data-stu-id="55e43-161">Get a list of SKUs for an Azure Reservation product.</span></span> <span data-ttu-id="55e43-162">Neem alleen de SKU's op die van toepassing zijn op Azure-abonnementen en niet Microsoft Azure (MS-AZR-0145P) abonnementen:</span><span class="sxs-lookup"><span data-stu-id="55e43-162">Only include the SKUs that are applicable to Azure plans and not Microsoft Azure (MS-AZR-0145P) subscriptions:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ5S/skus?country=US&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

<span data-ttu-id="55e43-163">Haal een lijst met SKU's op voor een Azure Reservation-product.</span><span class="sxs-lookup"><span data-stu-id="55e43-163">Get a list of SKUs for an Azure Reservation product.</span></span> <span data-ttu-id="55e43-164">Neem alleen de SKU's op die van toepassing zijn op Microsoft Azure-abonnementen (MS-AZR-0145P) en niet op Azure-abonnementen:</span><span class="sxs-lookup"><span data-stu-id="55e43-164">Only include the SKUs that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions and not Azure plans:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ5S/skus?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

## <a name="rest-response"></a><span data-ttu-id="55e43-165">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="55e43-165">REST response</span></span>

<span data-ttu-id="55e43-166">Als dit lukt, bevat de antwoord-body een verzameling [SKU-resources.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="55e43-166">If successful, the response body contains a collection of [SKU](product-resources.md#sku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="55e43-167">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="55e43-167">Response success and error codes</span></span>

<span data-ttu-id="55e43-168">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="55e43-168">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="55e43-169">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="55e43-169">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="55e43-170">Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="55e43-170">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="55e43-171">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="55e43-171">This method returns the following error codes:</span></span>

| <span data-ttu-id="55e43-172">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="55e43-172">HTTP Status Code</span></span>     | <span data-ttu-id="55e43-173">Foutcode</span><span class="sxs-lookup"><span data-stu-id="55e43-173">Error code</span></span>   | <span data-ttu-id="55e43-174">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="55e43-174">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="55e43-175">403</span><span class="sxs-lookup"><span data-stu-id="55e43-175">403</span></span>                  | <span data-ttu-id="55e43-176">400030</span><span class="sxs-lookup"><span data-stu-id="55e43-176">400030</span></span>       | <span data-ttu-id="55e43-177">Toegang tot het aangevraagde targetSegment is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="55e43-177">Access to the requested targetSegment is not allowed.</span></span>                                                     |
| <span data-ttu-id="55e43-178">404</span><span class="sxs-lookup"><span data-stu-id="55e43-178">404</span></span>                  | <span data-ttu-id="55e43-179">400013</span><span class="sxs-lookup"><span data-stu-id="55e43-179">400013</span></span>       | <span data-ttu-id="55e43-180">Het bovenliggende product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="55e43-180">The parent product was not found.</span></span>                                                                         |

### <a name="response-example"></a><span data-ttu-id="55e43-181">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="55e43-181">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51,e75c1060-852e-4b49-92b0-cd15167a0d51
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d,18b41adf-29b5-48eb-b14f-c9683a4e5b7d
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTVTXHNrdXM=?=
X-Powered-By: ASP.NET
Date: Thu, 15 Mar 2018 21:06:03 GMT
Content-Length: 50917

{
    "totalCount": 40,
    "items": [
        {
            "id": "0001",
            "productId": "DZH318Z0BQ5S",
            "title": "Reserved VM Instance, Standard_ND12s, US West 2, 1 Year",
            "description": "Reserved Virtual Machines Instance, Standard_ND12s, US West 2, 1 Year",
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
            "provisioningVariables": [
                "Scope",
                "SubscriptionId"
            ],
            "dynamicAttributes": {
                "armSkuName": "Standard_ND12s",
                "cores": "12",
                "ram": "224",
                "skuDisplayName": "ND12",
                "category": "GPU",
                "armRegionName": "westus2",
                "duration": "1Year",
                "region": "US West 2",
                "diskType": "Hdd"
            },
            "links": {
                "availabilities": {
                    "uri": "/products/DZH318Z0BQ5S/skus/0001/availabilities?country=US",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/products/DZH318Z0BQ5S/skus/0001?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        {
            "id": "0002",
            "productId": "DZH318Z0BQ5S",
            "title": "Reserved VM Instance, Standard_ND6s, US West 2, 1 Year",
            "description": "Reserved Virtual Machines Instance, Standard_ND6s, US West 2, 1 Year",
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
            "provisioningVariables": [
                "Scope",
                "SubscriptionId"
            ],
            "dynamicAttributes": {
                "armSkuName": "Standard_ND6s",
                "cores": "6",
                "ram": "112",
                "skuDisplayName": "ND6",
                "category": "GPU",
                "armRegionName": "westus2",
                "duration": "1Year",
                "region": "US West 2",
                "diskType": "Hdd"
            },
            "links": {
                "availabilities": {
                    "uri": "/products/DZH318Z0BQ5S/skus/0002/availabilities?country=US",
                    "method": "GET",
                    "headers": []
                },
            "self": {
                    "uri": "/products/DZH318Z0BQ5S/skus/0002?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
        [...]
    ],
    "links": {
        "self": {
            "uri": "/products/DZH318Z0BQ5S/skus?country=US",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
