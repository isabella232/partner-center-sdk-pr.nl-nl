---
title: Een lijst met beschikbaarheid voor een SKU ophalen (per land)
description: Een verzameling beschikbaarheid voor het opgegeven product en de SKU per klantland ophalen.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b29c005e74ad8a4da547a888b78e4599e74ebd02
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874530"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-country"></a><span data-ttu-id="40fa1-103">Een lijst met beschikbaarheid voor een SKU ophalen (per land)</span><span class="sxs-lookup"><span data-stu-id="40fa1-103">Get a list of availabilities for a SKU (by country)</span></span>

<span data-ttu-id="40fa1-104">In dit artikel wordt beschreven hoe u een verzameling beschikbaarheid krijgt in een bepaald land voor een opgegeven product en SKU.</span><span class="sxs-lookup"><span data-stu-id="40fa1-104">This article describes how to get a collection of availabilities in a particular country for a specified product and SKU.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="40fa1-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="40fa1-105">Prerequisites</span></span>

- <span data-ttu-id="40fa1-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="40fa1-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="40fa1-107">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="40fa1-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="40fa1-108">Een product-id.</span><span class="sxs-lookup"><span data-stu-id="40fa1-108">A product identifier.</span></span>

- <span data-ttu-id="40fa1-109">Een SKU-id.</span><span class="sxs-lookup"><span data-stu-id="40fa1-109">A SKU identifier.</span></span>

- <span data-ttu-id="40fa1-110">Een land.</span><span class="sxs-lookup"><span data-stu-id="40fa1-110">A country.</span></span>

## <a name="c"></a><span data-ttu-id="40fa1-111">C\#</span><span class="sxs-lookup"><span data-stu-id="40fa1-111">C\#</span></span>

<span data-ttu-id="40fa1-112">De lijst met beschikbaarheid [voor een](product-resources.md#availability) [SKU op te halen:](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="40fa1-112">To get the list of [availabilities](product-resources.md#availability) for a [SKU](product-resources.md#sku):</span></span>

1. <span data-ttu-id="40fa1-113">Volg de stappen in [Een SKU op id op halen om](get-a-sku-by-id.md) de interface voor de bewerkingen van een specifieke SKU op te halen.</span><span class="sxs-lookup"><span data-stu-id="40fa1-113">Follow the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific SKU's operations.</span></span>

2. <span data-ttu-id="40fa1-114">Selecteer in de SKU-interface de eigenschap **Beschikbaarheid** om een interface op te halen met de bewerkingen voor beschikbaarheid.</span><span class="sxs-lookup"><span data-stu-id="40fa1-114">From the SKU interface, select the **Availabilities** property to get an interface with the operations for availabilities.</span></span>

3. <span data-ttu-id="40fa1-115">(Optioneel) Gebruik de **methode ByTargetSegment()** om de beschikbaarheid te filteren op doelsegment.</span><span class="sxs-lookup"><span data-stu-id="40fa1-115">(Optional) Use the **ByTargetSegment()** method to filter the availabilities by target segment.</span></span>

4. <span data-ttu-id="40fa1-116">Roep **Get()** of **GetAsync()** aan om een verzameling van de beschikbaarheid voor deze SKU op te halen.</span><span class="sxs-lookup"><span data-stu-id="40fa1-116">Call **Get()** or **GetAsync()** to retrieve a collection of the availabilities for this SKU.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;
string targetSegment;
string productIdForAzureReservation;
string skuIdForAzureReservation;

// Get the availabilities.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.Get();

// Get the availabilities, filtered by target segment.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.BySegment(targetSegment).Get();

// Get the availabilities for an Azure reservation product and sku which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.ById(skuIdForAzureReservation).Availabilities.ByReservationScope("AzurePlan").Get();

// Get the availabilities for an Azure reservation product and sku which are applicable to Azure plans only.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.ById(skuIdForAzureReservation).Availabilities.Get();

```

## <a name="rest-request"></a><span data-ttu-id="40fa1-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="40fa1-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="40fa1-118">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="40fa1-118">Request syntax</span></span>

| <span data-ttu-id="40fa1-119">Methode</span><span class="sxs-lookup"><span data-stu-id="40fa1-119">Method</span></span>  | <span data-ttu-id="40fa1-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="40fa1-120">Request URI</span></span>                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="40fa1-121">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="40fa1-121">**GET**</span></span> | <span data-ttu-id="40fa1-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="40fa1-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment} HTTP/1.1</span></span>     |

### <a name="uri-parameters"></a><span data-ttu-id="40fa1-123">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="40fa1-123">URI parameters</span></span>

<span data-ttu-id="40fa1-124">Gebruik het volgende pad en de queryparameters om een lijst met beschikbaarheid voor een SKU op te halen.</span><span class="sxs-lookup"><span data-stu-id="40fa1-124">Use the following path and query parameters to get a list of availabilities for a SKU.</span></span>

| <span data-ttu-id="40fa1-125">Naam</span><span class="sxs-lookup"><span data-stu-id="40fa1-125">Name</span></span>                   | <span data-ttu-id="40fa1-126">Type</span><span class="sxs-lookup"><span data-stu-id="40fa1-126">Type</span></span>     | <span data-ttu-id="40fa1-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="40fa1-127">Required</span></span> | <span data-ttu-id="40fa1-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="40fa1-128">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="40fa1-129">product-id</span><span class="sxs-lookup"><span data-stu-id="40fa1-129">product-id</span></span>             | <span data-ttu-id="40fa1-130">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="40fa1-130">string</span></span>   | <span data-ttu-id="40fa1-131">Ja</span><span class="sxs-lookup"><span data-stu-id="40fa1-131">Yes</span></span>      | <span data-ttu-id="40fa1-132">Een tekenreeks die het product identificeert.</span><span class="sxs-lookup"><span data-stu-id="40fa1-132">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="40fa1-133">sku-id</span><span class="sxs-lookup"><span data-stu-id="40fa1-133">sku-id</span></span>                 | <span data-ttu-id="40fa1-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="40fa1-134">string</span></span>   | <span data-ttu-id="40fa1-135">Ja</span><span class="sxs-lookup"><span data-stu-id="40fa1-135">Yes</span></span>      | <span data-ttu-id="40fa1-136">Een tekenreeks die de SKU identificeert.</span><span class="sxs-lookup"><span data-stu-id="40fa1-136">A string that identifies the SKU.</span></span>                               |
| <span data-ttu-id="40fa1-137">country-code</span><span class="sxs-lookup"><span data-stu-id="40fa1-137">country-code</span></span>           | <span data-ttu-id="40fa1-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="40fa1-138">string</span></span>   | <span data-ttu-id="40fa1-139">Ja</span><span class="sxs-lookup"><span data-stu-id="40fa1-139">Yes</span></span>      | <span data-ttu-id="40fa1-140">Een land-/regio-id.</span><span class="sxs-lookup"><span data-stu-id="40fa1-140">A country/region ID.</span></span>                                            |
| <span data-ttu-id="40fa1-141">doelsegment</span><span class="sxs-lookup"><span data-stu-id="40fa1-141">target-segment</span></span>         | <span data-ttu-id="40fa1-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="40fa1-142">string</span></span>   | <span data-ttu-id="40fa1-143">No</span><span class="sxs-lookup"><span data-stu-id="40fa1-143">No</span></span>       | <span data-ttu-id="40fa1-144">Een tekenreeks die het doelsegment identificeert dat wordt gebruikt voor filteren.</span><span class="sxs-lookup"><span data-stu-id="40fa1-144">A string that identifies the target segment used for filtering.</span></span> |
| <span data-ttu-id="40fa1-145">reservationScope</span><span class="sxs-lookup"><span data-stu-id="40fa1-145">reservationScope</span></span> | <span data-ttu-id="40fa1-146">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="40fa1-146">string</span></span>   | <span data-ttu-id="40fa1-147">No</span><span class="sxs-lookup"><span data-stu-id="40fa1-147">No</span></span> | <span data-ttu-id="40fa1-148">Wanneer u een query uitvoert voor een lijst met beschikbaarheid voor een Azure Reservation SKU, geeft u op om een lijst met beschikbaarheid op te halen die van toepassing `reservationScope=AzurePlan` zijn op AzurePlan.</span><span class="sxs-lookup"><span data-stu-id="40fa1-148">When querying for a list of availabilities for an Azure Reservation SKU, specify `reservationScope=AzurePlan` to get a list of availabilities that are applicable to AzurePlan.</span></span> <span data-ttu-id="40fa1-149">Sluit deze parameter uit om een lijst met beschikbaarheid op te halen die van toepassing zijn op Microsoft Azure (MS-AZR-0145P)-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="40fa1-149">Exclude this parameter to get a list of availabilities that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="40fa1-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="40fa1-150">Request headers</span></span>

<span data-ttu-id="40fa1-151">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="40fa1-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="40fa1-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="40fa1-152">Request body</span></span>

<span data-ttu-id="40fa1-153">Geen.</span><span class="sxs-lookup"><span data-stu-id="40fa1-153">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="40fa1-154">Voorbeelden van aanvragen</span><span class="sxs-lookup"><span data-stu-id="40fa1-154">Request examples</span></span>

#### <a name="availabilities-for-sku-by-country"></a><span data-ttu-id="40fa1-155">Beschikbaarheid voor SKU per land</span><span class="sxs-lookup"><span data-stu-id="40fa1-155">Availabilities for SKU by country</span></span>

<span data-ttu-id="40fa1-156">Volg dit voorbeeld om een lijst met beschikbaarheid voor een bepaalde SKU per land op te halen:</span><span class="sxs-lookup"><span data-stu-id="40fa1-156">Follow this example to get a list of availabilities for a given SKU by country:</span></span>

```http
GET http:// api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 70324727-62d8-4195-8f99-70ea25058d02
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58
```

#### <a name="availabilities-for-vm-reservations-azure-plan"></a><span data-ttu-id="40fa1-157">Beschikbaarheid voor VM-reserveringen (Azure-plan)</span><span class="sxs-lookup"><span data-stu-id="40fa1-157">Availabilities for VM reservations (Azure plan)</span></span>

<span data-ttu-id="40fa1-158">Volg dit voorbeeld voor een lijst met beschikbaarheid per land voor Azure VM-reserverings-SKU's.</span><span class="sxs-lookup"><span data-stu-id="40fa1-158">Follow this example to get a list of availabilities by country for Azure VM reservation SKUs.</span></span> <span data-ttu-id="40fa1-159">Dit voorbeeld is voor SKU's die van toepassing zijn op Azure-plannen:</span><span class="sxs-lookup"><span data-stu-id="40fa1-159">This example is for SKUs that apply to Azure plans:</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="availabilities-for-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="40fa1-160">Beschikbaarheid voor VM-reserveringen voor Microsoft Azure -abonnementen (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="40fa1-160">Availabilities for VM reservations for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="40fa1-161">Volg dit voorbeeld om een lijst met beschikbaarheid per land op te halen voor Azure VM-reserveringen die van toepassing zijn op Microsoft Azure-abonnementen (MS-AZR-0145P).</span><span class="sxs-lookup"><span data-stu-id="40fa1-161">Follow this example to get a list of availabilities by country for Azure VM reservations that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/productsDZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureAzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="40fa1-162">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="40fa1-162">REST response</span></span>

<span data-ttu-id="40fa1-163">Als dit lukt, bevat de antwoord-body een verzameling [**beschikbaarheidsresources.**](product-resources.md#availability)</span><span class="sxs-lookup"><span data-stu-id="40fa1-163">If successful, the response body contains a collection of [**Availability**](product-resources.md#availability) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="40fa1-164">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="40fa1-164">Response success and error codes</span></span>

<span data-ttu-id="40fa1-165">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="40fa1-165">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="40fa1-166">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="40fa1-166">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="40fa1-167">Zie voor een volledige lijst Partner Center [foutcodes.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="40fa1-167">For a full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="40fa1-168">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="40fa1-168">This method returns the following error codes:</span></span>

| <span data-ttu-id="40fa1-169">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="40fa1-169">HTTP Status Code</span></span>     | <span data-ttu-id="40fa1-170">Foutcode</span><span class="sxs-lookup"><span data-stu-id="40fa1-170">Error code</span></span>   | <span data-ttu-id="40fa1-171">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="40fa1-171">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="40fa1-172">403</span><span class="sxs-lookup"><span data-stu-id="40fa1-172">403</span></span>                  | <span data-ttu-id="40fa1-173">400030</span><span class="sxs-lookup"><span data-stu-id="40fa1-173">400030</span></span>       | <span data-ttu-id="40fa1-174">Toegang tot het **aangevraagde targetSegment** is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="40fa1-174">Access to the requested **targetSegment** is not allowed.</span></span>                                                     |

### <a name="response-example"></a><span data-ttu-id="40fa1-175">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="40fa1-175">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58,83b644b5-e54a-4bdc-b354-f96c525b3c58
MS-RequestId: 70324727-62d8-4195-8f99-70ea25058d02,70324727-62d8-4195-8f99-70ea25058d02
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTNRXHNrdXNcMDAwMVxhdmFpbGFiaWxpdGllcw==?=
X-Powered-By: ASP.NET
Date: Wed, 14 Mar 2018 22:19:37 GMT
Content-Length: 808

{
    "totalCount": 1,
    "items": [
        {
            "id": "DZH318XZXVNF",
            "productId": "DZH318Z0BQ3Q",
            "skuId": "0001",
            "catalogItemId": "DZH318Z0BQ3Q:0001:DZH318XZXVNF",
            "defaultCurrency": {
                "code": "USD",
                "symbol": "$"
            },
            "segment": "commercial",
            "country": "US",
            "isPurchasable": true,
            "isRenewable": false,
            "terms": [{
                "duration": "P1Y",
                "description": "1 Year Prepaid"
            }],
            "product": { ... },
            "sku": { ... },
            "links": {
                "self": {
                    "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318Z0HMKQ?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetSegment=commercial",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
