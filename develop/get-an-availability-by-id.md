---
title: De beschik baarheid op basis van ID ophalen
description: Hiermee wordt de beschik baarheid voor het opgegeven product en de SKU opgehaald met behulp van een beschikbaarheids-ID.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 824303d40e1dcb0405246c8e29562c4527d147fd
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767181"
---
# <a name="get-the-availability-by-id"></a><span data-ttu-id="df523-103">De beschik baarheid op basis van ID ophalen</span><span class="sxs-lookup"><span data-stu-id="df523-103">Get the availability by ID</span></span>

<span data-ttu-id="df523-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="df523-104">**Applies To**</span></span>

- <span data-ttu-id="df523-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="df523-105">Partner Center</span></span>

<span data-ttu-id="df523-106">Hiermee wordt de beschik baarheid voor het opgegeven product en de SKU opgehaald met behulp van een beschikbaarheids-ID.</span><span class="sxs-lookup"><span data-stu-id="df523-106">Gets the availability for the specified product and SKU using an availability ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="df523-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="df523-107">Prerequisites</span></span>

- <span data-ttu-id="df523-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="df523-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="df523-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="df523-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="df523-110">Een product-ID.</span><span class="sxs-lookup"><span data-stu-id="df523-110">A product ID.</span></span>

- <span data-ttu-id="df523-111">EEN SKU-ID.</span><span class="sxs-lookup"><span data-stu-id="df523-111">A SKU ID.</span></span>

- <span data-ttu-id="df523-112">Een beschikbaarheids-ID.</span><span class="sxs-lookup"><span data-stu-id="df523-112">An availability ID.</span></span>

## <a name="c"></a><span data-ttu-id="df523-113">C\#</span><span class="sxs-lookup"><span data-stu-id="df523-113">C\#</span></span>

<span data-ttu-id="df523-114">Als u meer wilt weten over een specifieke [Beschik baarheid](product-resources.md#availability), kunt u beginnen met de stappen in [een SKU ophalen op basis](get-a-sku-by-id.md) van de id om de interface te verkrijgen voor een specifieke [SKU](product-resources.md#sku) -bewerking.</span><span class="sxs-lookup"><span data-stu-id="df523-114">To get details of a specific [availability](product-resources.md#availability), start by using the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific [SKU's](product-resources.md#sku) operations.</span></span> <span data-ttu-id="df523-115">Selecteer in de resulterende interface de eigenschap **Availabilities** om een interface te verkrijgen met de beschik bare bewerkingen voor Availabilities.</span><span class="sxs-lookup"><span data-stu-id="df523-115">From the resulting interface, select the **Availabilities** property to obtain an interface with the available operations for Availabilities.</span></span> <span data-ttu-id="df523-116">Daarna geeft u de beschikbaarheids-ID door aan de methode **ById ()** om de bewerkingen voor die specifieke Beschik baarheid te verkrijgen en roept u **Get ()** of **GetAsync (** ) aan om de beschikbaarheids gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="df523-116">After that, pass the availability ID to the **ById()** method to get the operations for that specific availability and then call **Get()** or **GetAsync()** to retrieve the availability details.</span></span>

```csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;
string availabilityId;

// Get the availability details.
var availability = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.ById(availabilityId).Get();
```

## <a name="java"></a><span data-ttu-id="df523-117">Java</span><span class="sxs-lookup"><span data-stu-id="df523-117">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="df523-118">Als u meer wilt weten over een specifieke [Beschik baarheid](product-resources.md#availability), kunt u beginnen met de stappen in [een SKU ophalen op basis](get-a-sku-by-id.md) van de id om de interface te verkrijgen voor een specifieke [SKU](product-resources.md#sku) -bewerking.</span><span class="sxs-lookup"><span data-stu-id="df523-118">To get details of a specific [availability](product-resources.md#availability), start by using the steps in [Get a SKU by ID](get-a-sku-by-id.md) to get the interface for a specific [SKU's](product-resources.md#sku) operations.</span></span> <span data-ttu-id="df523-119">Selecteer in de resulterende interface de functie **getAvailabilities** om een interface te verkrijgen met de beschik bare bewerkingen voor Availabilities.</span><span class="sxs-lookup"><span data-stu-id="df523-119">From the resulting interface, select the **getAvailabilities** function to obtain an interface with the available operations for Availabilities.</span></span> <span data-ttu-id="df523-120">Daarna geeft u de beschikbaarheids-ID door aan de functie **byId ()** om de bewerkingen voor die specifieke Beschik baarheid op te halen. Vervolgens roept u de functie **Get ()** aan om de beschikbaarheids gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="df523-120">After that, pass the availability ID to the **byId()** function to get the operations for that specific availability and then call the **get()** function to retrieve the availability details.</span></span>

```java
IAggregatePartner partnerOperations;
String countryCode;
String productId;
String skuId;
String availabilityId;

// Get the availability details.
Availability availability = partnerOperations.getProducts().byCountry(countryCode).byId(productId).getSkus().byId(skuId).getAvailabilities().byId(availabilityId).get();
```

## <a name="powershell"></a><span data-ttu-id="df523-121">PowerShell</span><span class="sxs-lookup"><span data-stu-id="df523-121">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="df523-122">Als u meer wilt weten over een specifieke [Beschik baarheid](product-resources.md#availability), voert u de [**Get-PartnerProductAvailability**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) uit en geeft u de para meters **AvailabilityId**, **CountryCode**, **ProductID** en **SkuId** op om de beschikbaarheids gegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="df523-122">To get details of a specific [availability](product-resources.md#availability), execute the [**Get-PartnerProductAvailability**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) and specify the **AvailabilityId**, **CountryCode**, **ProductId**, and **SkuId** parameters to retrieve the availability details.</span></span>

```powershell
Get-PartnerProductAvailability -Product $productId -SkuId $skuId -AvailabilityId $availabilityId
```

## <a name="rest-request"></a><span data-ttu-id="df523-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="df523-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="df523-124">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="df523-124">Request syntax</span></span>

| <span data-ttu-id="df523-125">Methode</span><span class="sxs-lookup"><span data-stu-id="df523-125">Method</span></span>  | <span data-ttu-id="df523-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="df523-126">Request URI</span></span> |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="df523-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="df523-127">**GET**</span></span> | <span data-ttu-id="df523-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/SKUs/{SKU-id}/Availabilities/{Availability-id}? land = {land nummer} http/1.1</span><span class="sxs-lookup"><span data-stu-id="df523-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code} HTTP/1.1</span></span>         |

### <a name="uri-parameter"></a><span data-ttu-id="df523-129">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="df523-129">URI parameter</span></span>

<span data-ttu-id="df523-130">Gebruik de volgende pad-en query parameters om een specifieke Beschik baarheid te verkrijgen met behulp van een beschikbaarheids-ID.</span><span class="sxs-lookup"><span data-stu-id="df523-130">Use the following path and query parameters to get a specific availability using an availability ID.</span></span>

| <span data-ttu-id="df523-131">Naam</span><span class="sxs-lookup"><span data-stu-id="df523-131">Name</span></span>                   | <span data-ttu-id="df523-132">Type</span><span class="sxs-lookup"><span data-stu-id="df523-132">Type</span></span>     | <span data-ttu-id="df523-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="df523-133">Required</span></span> | <span data-ttu-id="df523-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="df523-134">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="df523-135">product-id</span><span class="sxs-lookup"><span data-stu-id="df523-135">product-id</span></span>             | <span data-ttu-id="df523-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="df523-136">string</span></span>   | <span data-ttu-id="df523-137">Yes</span><span class="sxs-lookup"><span data-stu-id="df523-137">Yes</span></span>      | <span data-ttu-id="df523-138">Een teken reeks met een GUID-indeling waarmee het product wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="df523-138">A GUID formatted string that identifies the product.</span></span>            |
| <span data-ttu-id="df523-139">SKU-id</span><span class="sxs-lookup"><span data-stu-id="df523-139">sku-id</span></span>                 | <span data-ttu-id="df523-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="df523-140">string</span></span>   | <span data-ttu-id="df523-141">Yes</span><span class="sxs-lookup"><span data-stu-id="df523-141">Yes</span></span>      | <span data-ttu-id="df523-142">Een teken reeks met een GUID-indeling waarmee de SKU wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="df523-142">A GUID formatted string that identifies the SKU.</span></span>                |
| <span data-ttu-id="df523-143">Beschik baarheid-id</span><span class="sxs-lookup"><span data-stu-id="df523-143">availability-id</span></span>        | <span data-ttu-id="df523-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="df523-144">string</span></span>   | <span data-ttu-id="df523-145">Yes</span><span class="sxs-lookup"><span data-stu-id="df523-145">Yes</span></span>      | <span data-ttu-id="df523-146">Een teken reeks met een GUID-indeling waarmee de beschik baarheid wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="df523-146">A GUID formatted string that identifies the availability.</span></span>       |
| <span data-ttu-id="df523-147">land code</span><span class="sxs-lookup"><span data-stu-id="df523-147">country-code</span></span>           | <span data-ttu-id="df523-148">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="df523-148">string</span></span>   | <span data-ttu-id="df523-149">Yes</span><span class="sxs-lookup"><span data-stu-id="df523-149">Yes</span></span>      | <span data-ttu-id="df523-150">Een land/regio-ID.</span><span class="sxs-lookup"><span data-stu-id="df523-150">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="df523-151">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="df523-151">Request headers</span></span>

<span data-ttu-id="df523-152">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="df523-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="df523-153">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="df523-153">Request body</span></span>

<span data-ttu-id="df523-154">Geen.</span><span class="sxs-lookup"><span data-stu-id="df523-154">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="df523-155">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="df523-155">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="df523-156">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="df523-156">REST response</span></span>

<span data-ttu-id="df523-157">Als dit lukt, bevat de antwoord tekst een [beschikbaarheids](product-resources.md#availability) resource.</span><span class="sxs-lookup"><span data-stu-id="df523-157">If successful, the response body contains an [Availability](product-resources.md#availability) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="df523-158">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="df523-158">Response success and error codes</span></span>

<span data-ttu-id="df523-159">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="df523-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="df523-160">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="df523-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="df523-161">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="df523-161">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="df523-162">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="df523-162">This method returns the following error codes:</span></span>

| <span data-ttu-id="df523-163">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="df523-163">HTTP Status Code</span></span>     | <span data-ttu-id="df523-164">Foutcode</span><span class="sxs-lookup"><span data-stu-id="df523-164">Error code</span></span>   | <span data-ttu-id="df523-165">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="df523-165">Description</span></span>                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="df523-166">404</span><span class="sxs-lookup"><span data-stu-id="df523-166">404</span></span>                  | <span data-ttu-id="df523-167">400013</span><span class="sxs-lookup"><span data-stu-id="df523-167">400013</span></span>       | <span data-ttu-id="df523-168">Het product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="df523-168">Product was not found.</span></span>                                                                                    |
| <span data-ttu-id="df523-169">404</span><span class="sxs-lookup"><span data-stu-id="df523-169">404</span></span>                  | <span data-ttu-id="df523-170">400018</span><span class="sxs-lookup"><span data-stu-id="df523-170">400018</span></span>       | <span data-ttu-id="df523-171">SKU is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="df523-171">Sku was not found.</span></span>                                                                                        |
| <span data-ttu-id="df523-172">404</span><span class="sxs-lookup"><span data-stu-id="df523-172">404</span></span>                  | <span data-ttu-id="df523-173">400019</span><span class="sxs-lookup"><span data-stu-id="df523-173">400019</span></span>       | <span data-ttu-id="df523-174">Kan geen Beschik baarheid vinden.</span><span class="sxs-lookup"><span data-stu-id="df523-174">Availability not found.</span></span>                                                                                   |

### <a name="response-example"></a><span data-ttu-id="df523-175">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="df523-175">Response example</span></span>

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
