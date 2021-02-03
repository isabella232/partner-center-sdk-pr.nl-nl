---
title: Een lijst met beschikbaarheid voor een SKU ophalen (per land)
description: Het ophalen van een verzameling van Beschik baarheid voor het opgegeven product en de SKU per klant land.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b97a4ce85b5edd9de1301a577988f8c54096ebeb
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767302"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-country"></a><span data-ttu-id="caa56-103">Een lijst met beschikbaarheid voor een SKU ophalen (per land)</span><span class="sxs-lookup"><span data-stu-id="caa56-103">Get a list of availabilities for a SKU (by country)</span></span>

<span data-ttu-id="caa56-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="caa56-104">**Applies to:**</span></span>

- <span data-ttu-id="caa56-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="caa56-105">Partner Center</span></span>

<span data-ttu-id="caa56-106">In dit artikel wordt beschreven hoe u een verzameling van Beschik baarheid in een bepaald land kunt ophalen voor een opgegeven product en SKU.</span><span class="sxs-lookup"><span data-stu-id="caa56-106">This article describes how to get a collection of availabilities in a particular country for a specified product and SKU.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="caa56-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="caa56-107">Prerequisites</span></span>

- <span data-ttu-id="caa56-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="caa56-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="caa56-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="caa56-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="caa56-110">Een product-id.</span><span class="sxs-lookup"><span data-stu-id="caa56-110">A product identifier.</span></span>

- <span data-ttu-id="caa56-111">Een SKU-id.</span><span class="sxs-lookup"><span data-stu-id="caa56-111">A SKU identifier.</span></span>

- <span data-ttu-id="caa56-112">Een land.</span><span class="sxs-lookup"><span data-stu-id="caa56-112">A country.</span></span>

## <a name="c"></a><span data-ttu-id="caa56-113">C\#</span><span class="sxs-lookup"><span data-stu-id="caa56-113">C\#</span></span>

<span data-ttu-id="caa56-114">De lijst met beschik [baarheid voor](product-resources.md#availability) een [SKU](product-resources.md#sku)ophalen:</span><span class="sxs-lookup"><span data-stu-id="caa56-114">To get the list of [availabilities](product-resources.md#availability) for a [SKU](product-resources.md#sku):</span></span>

1. <span data-ttu-id="caa56-115">Volg de stappen in [een SKU ophalen op basis](get-a-sku-by-id.md) van de id om de interface te verkrijgen voor een specifieke SKU-bewerking.</span><span class="sxs-lookup"><span data-stu-id="caa56-115">Follow the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific SKU's operations.</span></span>

2. <span data-ttu-id="caa56-116">Selecteer de eigenschap **Availabilities** van de SKU-interface om een interface met de bewerkingen voor Availabilities op te halen.</span><span class="sxs-lookup"><span data-stu-id="caa56-116">From the SKU interface, select the **Availabilities** property to get an interface with the operations for availabilities.</span></span>

3. <span data-ttu-id="caa56-117">Beschrijving Gebruik de methode **ByTargetSegment ()** om de beschik baarheid per doel segment te filteren.</span><span class="sxs-lookup"><span data-stu-id="caa56-117">(Optional) Use the **ByTargetSegment()** method to filter the availabilities by target segment.</span></span>

4. <span data-ttu-id="caa56-118">Roep **Get ()** of **GetAsync ()** aan om een verzameling van de beschik baarheid voor deze SKU op te halen.</span><span class="sxs-lookup"><span data-stu-id="caa56-118">Call **Get()** or **GetAsync()** to retrieve a collection of the availabilities for this SKU.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="caa56-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="caa56-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="caa56-120">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="caa56-120">Request syntax</span></span>

| <span data-ttu-id="caa56-121">Methode</span><span class="sxs-lookup"><span data-stu-id="caa56-121">Method</span></span>  | <span data-ttu-id="caa56-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="caa56-122">Request URI</span></span>                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="caa56-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="caa56-123">**GET**</span></span> | <span data-ttu-id="caa56-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/SKUs/{SKU-id}/Availabilities? land = {land nummer} &targetSegment = {target-segment} http/1.1</span><span class="sxs-lookup"><span data-stu-id="caa56-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities?country={country-code}&targetSegment={target-segment} HTTP/1.1</span></span>     |

### <a name="uri-parameters"></a><span data-ttu-id="caa56-125">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="caa56-125">URI parameters</span></span>

<span data-ttu-id="caa56-126">Gebruik de volgende pad-en query parameters om een lijst met Beschik baarheid voor een SKU op te halen.</span><span class="sxs-lookup"><span data-stu-id="caa56-126">Use the following path and query parameters to get a list of availabilities for a SKU.</span></span>

| <span data-ttu-id="caa56-127">Naam</span><span class="sxs-lookup"><span data-stu-id="caa56-127">Name</span></span>                   | <span data-ttu-id="caa56-128">Type</span><span class="sxs-lookup"><span data-stu-id="caa56-128">Type</span></span>     | <span data-ttu-id="caa56-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="caa56-129">Required</span></span> | <span data-ttu-id="caa56-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="caa56-130">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="caa56-131">product-id</span><span class="sxs-lookup"><span data-stu-id="caa56-131">product-id</span></span>             | <span data-ttu-id="caa56-132">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="caa56-132">string</span></span>   | <span data-ttu-id="caa56-133">Yes</span><span class="sxs-lookup"><span data-stu-id="caa56-133">Yes</span></span>      | <span data-ttu-id="caa56-134">Een teken reeks waarmee het product wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="caa56-134">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="caa56-135">SKU-id</span><span class="sxs-lookup"><span data-stu-id="caa56-135">sku-id</span></span>                 | <span data-ttu-id="caa56-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="caa56-136">string</span></span>   | <span data-ttu-id="caa56-137">Yes</span><span class="sxs-lookup"><span data-stu-id="caa56-137">Yes</span></span>      | <span data-ttu-id="caa56-138">Een teken reeks waarmee de SKU wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="caa56-138">A string that identifies the SKU.</span></span>                               |
| <span data-ttu-id="caa56-139">land code</span><span class="sxs-lookup"><span data-stu-id="caa56-139">country-code</span></span>           | <span data-ttu-id="caa56-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="caa56-140">string</span></span>   | <span data-ttu-id="caa56-141">Yes</span><span class="sxs-lookup"><span data-stu-id="caa56-141">Yes</span></span>      | <span data-ttu-id="caa56-142">Een land/regio-ID.</span><span class="sxs-lookup"><span data-stu-id="caa56-142">A country/region ID.</span></span>                                            |
| <span data-ttu-id="caa56-143">doel segment</span><span class="sxs-lookup"><span data-stu-id="caa56-143">target-segment</span></span>         | <span data-ttu-id="caa56-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="caa56-144">string</span></span>   | <span data-ttu-id="caa56-145">No</span><span class="sxs-lookup"><span data-stu-id="caa56-145">No</span></span>       | <span data-ttu-id="caa56-146">Een teken reeks die het doel segment identificeert dat wordt gebruikt voor het filteren.</span><span class="sxs-lookup"><span data-stu-id="caa56-146">A string that identifies the target segment used for filtering.</span></span> |
| <span data-ttu-id="caa56-147">reservationScope</span><span class="sxs-lookup"><span data-stu-id="caa56-147">reservationScope</span></span> | <span data-ttu-id="caa56-148">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="caa56-148">string</span></span>   | <span data-ttu-id="caa56-149">No</span><span class="sxs-lookup"><span data-stu-id="caa56-149">No</span></span> | <span data-ttu-id="caa56-150">Bij het uitvoeren van een query op een lijst met Beschik baarheid voor een Azure reservation-SKU, geeft `reservationScope=AzurePlan` u een lijst op met Availabilities die van toepassing is op AzurePlan.</span><span class="sxs-lookup"><span data-stu-id="caa56-150">When querying for a list of availabilities for an Azure Reservation SKU, specify `reservationScope=AzurePlan` to get a list of availabilities which are applicable to AzurePlan.</span></span> <span data-ttu-id="caa56-151">Sluit deze para meter uit voor een lijst met Beschik baarheid die van toepassing is op Microsoft Azure (MS-AZR-0145P)-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="caa56-151">Exclude this parameter to get a list of availabilities which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>  |

### <a name="request-headers"></a><span data-ttu-id="caa56-152">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="caa56-152">Request headers</span></span>

<span data-ttu-id="caa56-153">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="caa56-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="caa56-154">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="caa56-154">Request body</span></span>

<span data-ttu-id="caa56-155">Geen.</span><span class="sxs-lookup"><span data-stu-id="caa56-155">None.</span></span>

### <a name="request-examples"></a><span data-ttu-id="caa56-156">Aanvraag voorbeelden</span><span class="sxs-lookup"><span data-stu-id="caa56-156">Request examples</span></span>

#### <a name="availabilities-for-sku-by-country"></a><span data-ttu-id="caa56-157">Beschik baarheid voor SKU per land</span><span class="sxs-lookup"><span data-stu-id="caa56-157">Availabilities for SKU by country</span></span>

<span data-ttu-id="caa56-158">Volg dit voor beeld voor een lijst met Beschik baarheid voor een bepaalde SKU per land:</span><span class="sxs-lookup"><span data-stu-id="caa56-158">Follow this example to get a list of availabilities for a given SKU by country:</span></span>

```http
GET http:// api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 70324727-62d8-4195-8f99-70ea25058d02
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58
```

#### <a name="availabilities-for-vm-reservations-azure-plan"></a><span data-ttu-id="caa56-159">Beschik baarheid voor VM-reserve ringen (Azure-abonnement)</span><span class="sxs-lookup"><span data-stu-id="caa56-159">Availabilities for VM reservations (Azure plan)</span></span>

<span data-ttu-id="caa56-160">Volg dit voor beeld voor een lijst met Beschik baarheid per land voor Sku's voor Azure VM-reserve ring.</span><span class="sxs-lookup"><span data-stu-id="caa56-160">Follow this example to get a list of availabilities by country for Azure VM reservation SKUs.</span></span> <span data-ttu-id="caa56-161">Dit voor beeld is voor Sku's die van toepassing zijn op Azure-abonnementen:</span><span class="sxs-lookup"><span data-stu-id="caa56-161">This example is for SKUs that apply to Azure plans:</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="availabilities-for-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="caa56-162">Beschik baarheid voor VM-reserve ringen voor Microsoft Azure-abonnementen (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="caa56-162">Availabilities for VM reservations for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="caa56-163">Volg dit voor beeld om een lijst op te halen van Beschik baarheid per land voor Azure VM-reserve ringen die van toepassing zijn op Microsoft Azure (MS-AZR-0145P)-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="caa56-163">Follow this example to get a list of availabilities by country for Azure VM reservations that are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions.</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/productsDZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureAzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="caa56-164">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="caa56-164">REST response</span></span>

<span data-ttu-id="caa56-165">Als dit lukt, bevat de antwoord tekst een verzameling [**beschik**](product-resources.md#availability) bare resources.</span><span class="sxs-lookup"><span data-stu-id="caa56-165">If successful, the response body contains a collection of [**Availability**](product-resources.md#availability) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="caa56-166">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="caa56-166">Response success and error codes</span></span>

<span data-ttu-id="caa56-167">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="caa56-167">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="caa56-168">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="caa56-168">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="caa56-169">Zie [fout codes voor Partner Center](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="caa56-169">For a full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="caa56-170">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="caa56-170">This method returns the following error codes:</span></span>

| <span data-ttu-id="caa56-171">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="caa56-171">HTTP Status Code</span></span>     | <span data-ttu-id="caa56-172">Foutcode</span><span class="sxs-lookup"><span data-stu-id="caa56-172">Error code</span></span>   | <span data-ttu-id="caa56-173">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="caa56-173">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="caa56-174">403</span><span class="sxs-lookup"><span data-stu-id="caa56-174">403</span></span>                  | <span data-ttu-id="caa56-175">400030</span><span class="sxs-lookup"><span data-stu-id="caa56-175">400030</span></span>       | <span data-ttu-id="caa56-176">Toegang tot de aangevraagde **targetSegment** is niet toegestaan.</span><span class="sxs-lookup"><span data-stu-id="caa56-176">Access to the requested **targetSegment** is not allowed.</span></span>                                                     |

### <a name="response-example"></a><span data-ttu-id="caa56-177">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="caa56-177">Response example</span></span>

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
