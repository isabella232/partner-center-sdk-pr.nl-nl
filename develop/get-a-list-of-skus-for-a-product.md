---
title: Een lijst met SKU’s voor een product ophalen (per land)
description: U kunt een verzameling van Sku's per land voor een product ophalen en filteren met behulp van de partner centrum-Api's.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 9d5ec9172ed92d33e6ff291eafd523cbc13bfbbd
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767292"
---
# <a name="get-a-list-of-skus-for-a-product-by-country"></a><span data-ttu-id="772a1-103">Een lijst met SKU’s voor een product ophalen (per land)</span><span class="sxs-lookup"><span data-stu-id="772a1-103">Get a list of SKUs for a product (by country)</span></span>

<span data-ttu-id="772a1-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="772a1-104">**Applies to:**</span></span>

- <span data-ttu-id="772a1-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="772a1-105">Partner Center</span></span>

<span data-ttu-id="772a1-106">U kunt een verzameling Sku's die beschikbaar zijn in een land voor een specifiek product ophalen met behulp van partner Center-Api's.</span><span class="sxs-lookup"><span data-stu-id="772a1-106">You can get a collection of SKUs available in a country for a specific product using Partner Center APIs.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="772a1-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="772a1-107">Prerequisites</span></span>

- <span data-ttu-id="772a1-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="772a1-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="772a1-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="772a1-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="772a1-110">Een product-id.</span><span class="sxs-lookup"><span data-stu-id="772a1-110">A product identifier.</span></span>

## <a name="c"></a><span data-ttu-id="772a1-111">C\#</span><span class="sxs-lookup"><span data-stu-id="772a1-111">C\#</span></span>

<span data-ttu-id="772a1-112">De lijst met Sku's voor een product ophalen:</span><span class="sxs-lookup"><span data-stu-id="772a1-112">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="772a1-113">Haal een interface op voor de bewerkingen van een specifiek product door de stappen in [een product ophalen op basis van id](get-a-product-by-id.md)te volgen.</span><span class="sxs-lookup"><span data-stu-id="772a1-113">Get an interface for a specific product's operations by following the steps in [Get a product by ID](get-a-product-by-id.md).</span></span>

2. <span data-ttu-id="772a1-114">Selecteer in de interface de eigenschap **sku's** om een interface te verkrijgen met de beschik bare bewerkingen voor sku's.</span><span class="sxs-lookup"><span data-stu-id="772a1-114">From the interface, select the **Skus** property to obtain an interface with the available operations for SKUs.</span></span>

3. <span data-ttu-id="772a1-115">Roep de methode **Get ()** of **GetAsync ()** aan om een verzameling van de beschik bare sku's voor het product op te halen.</span><span class="sxs-lookup"><span data-stu-id="772a1-115">Call the **Get()** or **GetAsync()** method to retrieve a collection of the available SKUs for the product.</span></span>

4. <span data-ttu-id="772a1-116">Beschrijving Selecteer het reserverings bereik met de methode **ByReservationScope ()** .</span><span class="sxs-lookup"><span data-stu-id="772a1-116">(Optional) Select the reservation scope using the **ByReservationScope()** method.</span></span>

5. <span data-ttu-id="772a1-117">Beschrijving Gebruik de methode **ByTargetSegment ()** om de sku's te filteren op doel segment voordat u **Get ()** of **GetAsync ()** aanroept.</span><span class="sxs-lookup"><span data-stu-id="772a1-117">(Optional) Use the **ByTargetSegment()** method to filter the SKUs by target segment before calling **Get()** or **GetAsync()**.</span></span>

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

## <a name="java"></a><span data-ttu-id="772a1-118">Java</span><span class="sxs-lookup"><span data-stu-id="772a1-118">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="772a1-119">De lijst met Sku's voor een product ophalen:</span><span class="sxs-lookup"><span data-stu-id="772a1-119">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="772a1-120">Haal een interface op voor de bewerkingen van een specifiek product door de stappen in [een product ophalen op basis van id](get-a-product-by-id.md)te volgen.</span><span class="sxs-lookup"><span data-stu-id="772a1-120">Get an interface for a specific product's operations by following the steps in [Get a product by ID](get-a-product-by-id.md).</span></span>

2. <span data-ttu-id="772a1-121">Selecteer de functie **getSkus** van de interface om een interface met de beschik bare bewerkingen voor sku's te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="772a1-121">From the interface, select the **getSkus** function to obtain an interface with the available operations for SKUs.</span></span>

3. <span data-ttu-id="772a1-122">Roep de functie **Get ()** aan om een verzameling van de beschik bare sku's voor het product op te halen.</span><span class="sxs-lookup"><span data-stu-id="772a1-122">Call the **get()** function to retrieve a collection of the available SKUs for the product.</span></span>

4. <span data-ttu-id="772a1-123">Beschrijving Gebruik de functie **byTargetSegment ()** om de sku's te filteren op doel segment voordat u de functie **Get ()** aanroept.</span><span class="sxs-lookup"><span data-stu-id="772a1-123">(Optional) Use the **byTargetSegment()** function to filter the SKUs by target segment before calling the **get()** function.</span></span>

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

## <a name="powershell"></a><span data-ttu-id="772a1-124">PowerShell</span><span class="sxs-lookup"><span data-stu-id="772a1-124">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="772a1-125">De lijst met Sku's voor een product ophalen:</span><span class="sxs-lookup"><span data-stu-id="772a1-125">To get the list of SKUs for a product:</span></span>

1. <span data-ttu-id="772a1-126">Voer de opdracht [**Get-PartnerProductSku**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductSku.md) uit.</span><span class="sxs-lookup"><span data-stu-id="772a1-126">Execute the [**Get-PartnerProductSku**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductSku.md) command.</span></span>

2. <span data-ttu-id="772a1-127">Beschrijving Geef de **segment** parameter op om de sku's te filteren op doel segment.</span><span class="sxs-lookup"><span data-stu-id="772a1-127">(Optional) Specify the **Segment** parameter to filter the SKUs by target segment.</span></span>

```powershell
# $productId
# $targetSegment

# Get the available SKUs.
Get-PartnerProductSku -ProductId $productId

# Get the available SKUs, filtered by target segment.
Get-PartnerProductSku -ProductId $productId -Segment $targetSegment
```

## <a name="rest-request"></a><span data-ttu-id="772a1-128">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="772a1-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="772a1-129">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="772a1-129">Request syntax</span></span>

| <span data-ttu-id="772a1-130">Methode</span><span class="sxs-lookup"><span data-stu-id="772a1-130">Method</span></span>  | <span data-ttu-id="772a1-131">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="772a1-131">Request URI</span></span>                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="772a1-132">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="772a1-132">**GET**</span></span> | <span data-ttu-id="772a1-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/SKUs? land = {land nummer} &targetSegment = {target-segment} http/1.1</span><span class="sxs-lookup"><span data-stu-id="772a1-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus?country={country-code}&targetSegment={target-segment} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="772a1-134">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="772a1-134">URI parameters</span></span>

<span data-ttu-id="772a1-135">Gebruik de volgende pad-en query parameters om een lijst met Sku's voor een product op te halen.</span><span class="sxs-lookup"><span data-stu-id="772a1-135">Use the following path and query parameters to get a list of SKUs for a product.</span></span>

| <span data-ttu-id="772a1-136">Naam</span><span class="sxs-lookup"><span data-stu-id="772a1-136">Name</span></span>                   | <span data-ttu-id="772a1-137">Type</span><span class="sxs-lookup"><span data-stu-id="772a1-137">Type</span></span>     | <span data-ttu-id="772a1-138">Vereist</span><span class="sxs-lookup"><span data-stu-id="772a1-138">Required</span></span> | <span data-ttu-id="772a1-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="772a1-139">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="772a1-140">product-id</span><span class="sxs-lookup"><span data-stu-id="772a1-140">product-id</span></span>             | <span data-ttu-id="772a1-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="772a1-141">string</span></span>   | <span data-ttu-id="772a1-142">Yes</span><span class="sxs-lookup"><span data-stu-id="772a1-142">Yes</span></span>      | <span data-ttu-id="772a1-143">Een teken reeks waarmee het product wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="772a1-143">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="772a1-144">land code</span><span class="sxs-lookup"><span data-stu-id="772a1-144">country-code</span></span>           | <span data-ttu-id="772a1-145">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="772a1-145">string</span></span>   | <span data-ttu-id="772a1-146">Yes</span><span class="sxs-lookup"><span data-stu-id="772a1-146">Yes</span></span>      | <span data-ttu-id="772a1-147">Een land/regio-ID.</span><span class="sxs-lookup"><span data-stu-id="772a1-147">A country/region ID.</span></span>                                            |
| <span data-ttu-id="772a1-148">doel segment</span><span class="sxs-lookup"><span data-stu-id="772a1-148">target-segment</span></span>         | <span data-ttu-id="772a1-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="772a1-149">string</span></span>   | <span data-ttu-id="772a1-150">No</span><span class="sxs-lookup"><span data-stu-id="772a1-150">No</span></span>       | <span data-ttu-id="772a1-151">Een teken reeks die het doel segment identificeert dat wordt gebruikt voor het filteren.</span><span class="sxs-lookup"><span data-stu-id="772a1-151">A string that identifies the target segment used for filtering.</span></span> |
| <span data-ttu-id="772a1-152">reservationScope</span><span class="sxs-lookup"><span data-stu-id="772a1-152">reservationScope</span></span> | <span data-ttu-id="772a1-153">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="772a1-153">string</span></span>   | <span data-ttu-id="772a1-154">No</span><span class="sxs-lookup"><span data-stu-id="772a1-154">No</span></span> | <span data-ttu-id="772a1-155">Bij het uitvoeren van een query op een lijst met Sku's voor een Azure-reserverings product, geeft `reservationScope=AzurePlan` u een lijst op met sku's die van toepassing zijn op AzurePlan.</span><span class="sxs-lookup"><span data-stu-id="772a1-155">When querying for a list of SKUs for an Azure Reservation product, specify `reservationScope=AzurePlan` to get a list of SKUs which are applicable to AzurePlan.</span></span> <span data-ttu-id="772a1-156">Sluit deze para meter uit om een lijst op te halen met Sku's voor een Azure-reserverings product die van toepassing zijn op Microsoft Azure (MS-AZR-0145P)-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="772a1-156">Exclude this parameter to get a list of SKUs for an Azure Reservation products which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="772a1-157">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="772a1-157">Request headers</span></span>

<span data-ttu-id="772a1-158">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="772a1-158">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="772a1-159">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="772a1-159">Request body</span></span>

<span data-ttu-id="772a1-160">Geen.</span><span class="sxs-lookup"><span data-stu-id="772a1-160">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="772a1-161">Aanvraag voorbeelden</span><span class="sxs-lookup"><span data-stu-id="772a1-161">Request examples</span></span>

<span data-ttu-id="772a1-162">Een lijst met Sku's voor een bepaald product ophalen:</span><span class="sxs-lookup"><span data-stu-id="772a1-162">Get a list of SKUs for a given product:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BPS6/skus?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

<span data-ttu-id="772a1-163">Haal een lijst op met Sku's voor een reserve ring product van Azure.</span><span class="sxs-lookup"><span data-stu-id="772a1-163">Get a list of SKUs for an Azure Reservation product.</span></span> <span data-ttu-id="772a1-164">Neem alleen de Sku's op die van toepassing zijn op Azure-abonnementen en niet Microsoft Azure (MS-AZR-0145P):</span><span class="sxs-lookup"><span data-stu-id="772a1-164">Only include the SKUs which are applicable to Azure plans and not Microsoft Azure (MS-AZR-0145P) subscriptions:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ5S/skus?country=US&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

<span data-ttu-id="772a1-165">Haal een lijst op met Sku's voor een reserve ring product van Azure.</span><span class="sxs-lookup"><span data-stu-id="772a1-165">Get a list of SKUs for an Azure Reservation product.</span></span> <span data-ttu-id="772a1-166">Neem alleen de Sku's op die van toepassing zijn op Microsoft Azure (MS-AZR-0145P) en niet voor Azure-abonnementen:</span><span class="sxs-lookup"><span data-stu-id="772a1-166">Only include the SKUs which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions and not Azure plans:</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ5S/skus?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18b41adf-29b5-48eb-b14f-c9683a4e5b7d
MS-CorrelationId: e75c1060-852e-4b49-92b0-cd15167a0d51
```

## <a name="rest-response"></a><span data-ttu-id="772a1-167">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="772a1-167">REST response</span></span>

<span data-ttu-id="772a1-168">Als dit lukt, bevat de antwoord tekst een verzameling [SKU](product-resources.md#sku) -resources.</span><span class="sxs-lookup"><span data-stu-id="772a1-168">If successful, the response body contains a collection of [SKU](product-resources.md#sku) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="772a1-169">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="772a1-169">Response success and error codes</span></span>

<span data-ttu-id="772a1-170">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="772a1-170">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="772a1-171">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="772a1-171">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="772a1-172">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="772a1-172">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="772a1-173">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="772a1-173">This method returns the following error codes:</span></span>

| <span data-ttu-id="772a1-174">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="772a1-174">HTTP Status Code</span></span>     | <span data-ttu-id="772a1-175">Foutcode</span><span class="sxs-lookup"><span data-stu-id="772a1-175">Error code</span></span>   | <span data-ttu-id="772a1-176">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="772a1-176">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="772a1-177">403</span><span class="sxs-lookup"><span data-stu-id="772a1-177">403</span></span>                  | <span data-ttu-id="772a1-178">400030</span><span class="sxs-lookup"><span data-stu-id="772a1-178">400030</span></span>       | <span data-ttu-id="772a1-179">Toegang tot de aangevraagde targetSegment is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="772a1-179">Access to the requested targetSegment is not allowed.</span></span>                                                     |
| <span data-ttu-id="772a1-180">404</span><span class="sxs-lookup"><span data-stu-id="772a1-180">404</span></span>                  | <span data-ttu-id="772a1-181">400013</span><span class="sxs-lookup"><span data-stu-id="772a1-181">400013</span></span>       | <span data-ttu-id="772a1-182">Het bovenliggende product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="772a1-182">The parent product was not found.</span></span>                                                                         |

### <a name="response-example"></a><span data-ttu-id="772a1-183">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="772a1-183">Response example</span></span>

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
