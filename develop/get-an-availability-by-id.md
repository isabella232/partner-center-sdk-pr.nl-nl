---
title: De beschikbaarheid op id op halen
description: Hiermee haalt u de beschikbaarheid op voor het opgegeven product en de SKU met behulp van een beschikbaarheids-id.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: c31bc12d8d484cc8042f36aa865145600d9e6738
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760195"
---
# <a name="get-the-availability-by-id"></a><span data-ttu-id="0f4fd-103">De beschikbaarheid op id op halen</span><span class="sxs-lookup"><span data-stu-id="0f4fd-103">Get the availability by ID</span></span>

<span data-ttu-id="0f4fd-104">Hiermee haalt u de beschikbaarheid op voor het opgegeven product en de SKU met behulp van een beschikbaarheids-id.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-104">Gets the availability for the specified product and SKU using an availability ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0f4fd-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0f4fd-105">Prerequisites</span></span>

- <span data-ttu-id="0f4fd-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0f4fd-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0f4fd-107">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="0f4fd-108">Een product-id.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-108">A product ID.</span></span>

- <span data-ttu-id="0f4fd-109">Een SKU-id.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-109">A SKU ID.</span></span>

- <span data-ttu-id="0f4fd-110">Een beschikbaarheids-id.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-110">An availability ID.</span></span>

## <a name="c"></a><span data-ttu-id="0f4fd-111">C\#</span><span class="sxs-lookup"><span data-stu-id="0f4fd-111">C\#</span></span>

<span data-ttu-id="0f4fd-112">Als u meer informatie wilt over een specifieke [beschikbaarheid,](product-resources.md#availability)gebruikt u eerst de stappen in Een [SKU](get-a-sku-by-id.md) op id op halen om de interface voor de bewerkingen van een specifieke [SKU op te](product-resources.md#sku) halen.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-112">To get details of a specific [availability](product-resources.md#availability), start by using the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific [SKU's](product-resources.md#sku) operations.</span></span> <span data-ttu-id="0f4fd-113">Selecteer in de resulterende interface de eigenschap **Beschikbaarheid** om een interface te verkrijgen met de beschikbare bewerkingen voor beschikbaarheid.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-113">From the resulting interface, select the **Availabilities** property to obtain an interface with the available operations for Availabilities.</span></span> <span data-ttu-id="0f4fd-114">Geef daarna de beschikbaarheids-id door aan de **methode ById()** om de bewerkingen voor die specifieke beschikbaarheid op te halen en roep vervolgens **Get()** of **GetAsync()** aan om de beschikbaarheidsgegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-114">After that, pass the availability ID to the **ById()** method to get the operations for that specific availability and then call **Get()** or **GetAsync()** to retrieve the availability details.</span></span>

```csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;
string availabilityId;

// Get the availability details.
var availability = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.ById(availabilityId).Get();
```

## <a name="java"></a><span data-ttu-id="0f4fd-115">Java</span><span class="sxs-lookup"><span data-stu-id="0f4fd-115">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="0f4fd-116">Als u meer informatie wilt over een specifieke [beschikbaarheid,](product-resources.md#availability)gebruikt u eerst de stappen in Een [SKU](get-a-sku-by-id.md) op id op halen om de interface voor de bewerkingen van een specifieke [SKU op te](product-resources.md#sku) halen.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-116">To get details of a specific [availability](product-resources.md#availability), start by using the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific [SKU's](product-resources.md#sku) operations.</span></span> <span data-ttu-id="0f4fd-117">Selecteer in de resulterende interface de **functie getAvailabilities** om een interface te verkrijgen met de beschikbare bewerkingen voor Beschikbaarheid.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-117">From the resulting interface, select the **getAvailabilities** function to obtain an interface with the available operations for Availabilities.</span></span> <span data-ttu-id="0f4fd-118">Geef daarna de beschikbaarheids-id door aan de **functie byId()** om de bewerkingen voor die specifieke beschikbaarheid op te halen en roep vervolgens de **functie get()** aan om de beschikbaarheidsdetails op te halen.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-118">After that, pass the availability ID to the **byId()** function to get the operations for that specific availability and then call the **get()** function to retrieve the availability details.</span></span>

```java
IAggregatePartner partnerOperations;
String countryCode;
String productId;
String skuId;
String availabilityId;

// Get the availability details.
Availability availability = partnerOperations.getProducts().byCountry(countryCode).byId(productId).getSkus().byId(skuId).getAvailabilities().byId(availabilityId).get();
```

## <a name="powershell"></a><span data-ttu-id="0f4fd-119">PowerShell</span><span class="sxs-lookup"><span data-stu-id="0f4fd-119">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="0f4fd-120">Als u details over een specifieke beschikbaarheid wilt [ophalen,](product-resources.md#availability)voert u de parameters [**Get-PartnerProductAvailability**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) en geeft u de parameters **AvailabilityId,** **CountryCode,** **ProductId** en **SkuId** op om de beschikbaarheidsgegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-120">To get details of a specific [availability](product-resources.md#availability), execute the [**Get-PartnerProductAvailability**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) and specify the **AvailabilityId**, **CountryCode**, **ProductId**, and **SkuId** parameters to retrieve the availability details.</span></span>

```powershell
Get-PartnerProductAvailability -Product $productId -SkuId $skuId -AvailabilityId $availabilityId
```

## <a name="rest-request"></a><span data-ttu-id="0f4fd-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="0f4fd-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0f4fd-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="0f4fd-122">Request syntax</span></span>

| <span data-ttu-id="0f4fd-123">Methode</span><span class="sxs-lookup"><span data-stu-id="0f4fd-123">Method</span></span>  | <span data-ttu-id="0f4fd-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="0f4fd-124">Request URI</span></span> |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0f4fd-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="0f4fd-125">**GET**</span></span> | <span data-ttu-id="0f4fd-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0f4fd-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code} HTTP/1.1</span></span>         |

### <a name="uri-parameter"></a><span data-ttu-id="0f4fd-127">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="0f4fd-127">URI parameter</span></span>

<span data-ttu-id="0f4fd-128">Gebruik het volgende pad en de queryparameters om een specifieke beschikbaarheid te krijgen met behulp van een beschikbaarheids-id.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-128">Use the following path and query parameters to get a specific availability using an availability ID.</span></span>

| <span data-ttu-id="0f4fd-129">Naam</span><span class="sxs-lookup"><span data-stu-id="0f4fd-129">Name</span></span>                   | <span data-ttu-id="0f4fd-130">Type</span><span class="sxs-lookup"><span data-stu-id="0f4fd-130">Type</span></span>     | <span data-ttu-id="0f4fd-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="0f4fd-131">Required</span></span> | <span data-ttu-id="0f4fd-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0f4fd-132">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="0f4fd-133">product-id</span><span class="sxs-lookup"><span data-stu-id="0f4fd-133">product-id</span></span>             | <span data-ttu-id="0f4fd-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="0f4fd-134">string</span></span>   | <span data-ttu-id="0f4fd-135">Ja</span><span class="sxs-lookup"><span data-stu-id="0f4fd-135">Yes</span></span>      | <span data-ttu-id="0f4fd-136">Een tekenreeks met GUID-indeling die het product identificeert.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-136">A GUID formatted string that identifies the product.</span></span>            |
| <span data-ttu-id="0f4fd-137">sku-id</span><span class="sxs-lookup"><span data-stu-id="0f4fd-137">sku-id</span></span>                 | <span data-ttu-id="0f4fd-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="0f4fd-138">string</span></span>   | <span data-ttu-id="0f4fd-139">Ja</span><span class="sxs-lookup"><span data-stu-id="0f4fd-139">Yes</span></span>      | <span data-ttu-id="0f4fd-140">Een tekenreeks met GUID-indeling die de SKU identificeert.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-140">A GUID formatted string that identifies the SKU.</span></span>                |
| <span data-ttu-id="0f4fd-141">availability-id</span><span class="sxs-lookup"><span data-stu-id="0f4fd-141">availability-id</span></span>        | <span data-ttu-id="0f4fd-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="0f4fd-142">string</span></span>   | <span data-ttu-id="0f4fd-143">Ja</span><span class="sxs-lookup"><span data-stu-id="0f4fd-143">Yes</span></span>      | <span data-ttu-id="0f4fd-144">Een tekenreeks met GUID-indeling die de beschikbaarheid identificeert.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-144">A GUID formatted string that identifies the availability.</span></span>       |
| <span data-ttu-id="0f4fd-145">country-code</span><span class="sxs-lookup"><span data-stu-id="0f4fd-145">country-code</span></span>           | <span data-ttu-id="0f4fd-146">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="0f4fd-146">string</span></span>   | <span data-ttu-id="0f4fd-147">Ja</span><span class="sxs-lookup"><span data-stu-id="0f4fd-147">Yes</span></span>      | <span data-ttu-id="0f4fd-148">Een land-/regio-id.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-148">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="0f4fd-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="0f4fd-149">Request headers</span></span>

<span data-ttu-id="0f4fd-150">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="0f4fd-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0f4fd-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="0f4fd-151">Request body</span></span>

<span data-ttu-id="0f4fd-152">Geen.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0f4fd-153">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="0f4fd-153">Request example</span></span>

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318XZXPHL?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 2e12a576-ded5-437e-a5ec-dbfbcbd1624c
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="0f4fd-154">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="0f4fd-154">REST response</span></span>

<span data-ttu-id="0f4fd-155">Als dit lukt, bevat de antwoord-body een [beschikbaarheidsresource.](product-resources.md#availability)</span><span class="sxs-lookup"><span data-stu-id="0f4fd-155">If successful, the response body contains an [Availability](product-resources.md#availability) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0f4fd-156">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="0f4fd-156">Response success and error codes</span></span>

<span data-ttu-id="0f4fd-157">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0f4fd-158">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0f4fd-159">Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="0f4fd-159">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="0f4fd-160">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="0f4fd-160">This method returns the following error codes:</span></span>

| <span data-ttu-id="0f4fd-161">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="0f4fd-161">HTTP Status Code</span></span>     | <span data-ttu-id="0f4fd-162">Foutcode</span><span class="sxs-lookup"><span data-stu-id="0f4fd-162">Error code</span></span>   | <span data-ttu-id="0f4fd-163">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0f4fd-163">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0f4fd-164">404</span><span class="sxs-lookup"><span data-stu-id="0f4fd-164">404</span></span>                  | <span data-ttu-id="0f4fd-165">400013</span><span class="sxs-lookup"><span data-stu-id="0f4fd-165">400013</span></span>       | <span data-ttu-id="0f4fd-166">Product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-166">Product was not found.</span></span>                                                                                    |
| <span data-ttu-id="0f4fd-167">404</span><span class="sxs-lookup"><span data-stu-id="0f4fd-167">404</span></span>                  | <span data-ttu-id="0f4fd-168">400018</span><span class="sxs-lookup"><span data-stu-id="0f4fd-168">400018</span></span>       | <span data-ttu-id="0f4fd-169">SKU is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-169">SKU was not found.</span></span>                                                                                        |
| <span data-ttu-id="0f4fd-170">404</span><span class="sxs-lookup"><span data-stu-id="0f4fd-170">404</span></span>                  | <span data-ttu-id="0f4fd-171">400019</span><span class="sxs-lookup"><span data-stu-id="0f4fd-171">400019</span></span>       | <span data-ttu-id="0f4fd-172">Beschikbaarheid niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="0f4fd-172">Availability not found.</span></span>                                                                                   |

### <a name="response-example"></a><span data-ttu-id="0f4fd-173">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="0f4fd-173">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58,83b644b5-e54a-4bdc-b354-f96c525b3c58
MS-RequestId: 2e12a576-ded5-437e-a5ec-dbfbcbd1624c,2e12a576-ded5-437e-a5ec-dbfbcbd1624c
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTNRXHNrdXNcMDAwMVxhdmFpbGFiaWxpdGllc1xEWkgzMThaMEhNS1E=?=
X-Powered-By: ASP.NET
Date: Wed, 14 Mar 2018 22:19:43 GMT
Content-Length: 440

{
    "id": "DZH318XZXPHL",
    "productId": "DZH318Z0BQ3Q",
    "skuId": "0001",
    "catalogItemId": "DZH318Z0BQ3Q:0001:DZH318XZXPHL",
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
            "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318XZXPHL?country=US",
            "method": "GET",
            "headers": []
        }
    }
}
```
