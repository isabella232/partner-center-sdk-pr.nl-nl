---
title: Een product ophalen op basis van id
description: Hiermee haalt u de opgegeven productresource op met behulp van een product-id.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 769a4307dc3cebdc7ebbdcf51d9f2b67a9f4b7c2
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874020"
---
# <a name="get-a-product-by-id"></a><span data-ttu-id="b3b19-103">Een product ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="b3b19-103">Get a product by ID</span></span>

<span data-ttu-id="b3b19-104">Hiermee haalt u de opgegeven productresource op met behulp van een product-id.</span><span class="sxs-lookup"><span data-stu-id="b3b19-104">Gets the specified product resource using a product ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b3b19-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b3b19-105">Prerequisites</span></span>

- <span data-ttu-id="b3b19-106">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="b3b19-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b3b19-107">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="b3b19-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="b3b19-108">Een product-id.</span><span class="sxs-lookup"><span data-stu-id="b3b19-108">A product ID.</span></span>

## <a name="c"></a><span data-ttu-id="b3b19-109">C\#</span><span class="sxs-lookup"><span data-stu-id="b3b19-109">C\#</span></span>

<span data-ttu-id="b3b19-110">Als u een specifiek product op id wilt zoeken, gebruikt u de verzameling **IAggregatePartner.Products,** selecteert u het land met behulp van de **methode ByCountry()** en roept u vervolgens de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="b3b19-110">To find a specific product by ID, use your **IAggregatePartner.Products** collection, select the country by using the **ByCountry()** method, then call the **ById()** method.</span></span> <span data-ttu-id="b3b19-111">Roep ten slotte de **methode Get()** of **GetAsync()** aan om het product te retourneren.</span><span class="sxs-lookup"><span data-stu-id="b3b19-111">Finally, call the **Get()** or **GetAsync()** method to return the product.</span></span>

```csharp
// IAggregatePartner partnerOperations;

Product productDetail = partnerOperations.Products.ByCountry("US").ById("DZH318Z0BQ3Q").Get();
```

## <a name="java"></a><span data-ttu-id="b3b19-112">Java</span><span class="sxs-lookup"><span data-stu-id="b3b19-112">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](<../includes/java-sdk-support.md>)]

<span data-ttu-id="b3b19-113">Als u een specifiek product op id wilt zoeken, gebruikt u de functie **IAggregatePartner.getProducts,** selecteert u het land met behulp van de functie **byCountry()** en roept u vervolgens de **functie byId()** aan.</span><span class="sxs-lookup"><span data-stu-id="b3b19-113">To find a specific product by ID, use your **IAggregatePartner.getProducts** function, select the country by using the **byCountry()** function, then call the **byId()** function.</span></span> <span data-ttu-id="b3b19-114">Roep ten slotte de **functie get() aan** om het product te retourneren.</span><span class="sxs-lookup"><span data-stu-id="b3b19-114">Finally, call the **get()** function to return the product.</span></span>

```java
// IAggregatePartner partnerOperations;

Product productDetail = partnerOperations.getProducts().byCountry("US").byId("DZH318Z0BQ3Q").get();
```

## <a name="powershell"></a><span data-ttu-id="b3b19-115">PowerShell</span><span class="sxs-lookup"><span data-stu-id="b3b19-115">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](<../includes/powershell-module-support.md>)]

<span data-ttu-id="b3b19-116">Als u een specifiek product wilt zoeken op id, voert u [**de opdracht Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) uit en geeft u de **parameter ProductId** op.</span><span class="sxs-lookup"><span data-stu-id="b3b19-116">To find a specific product by ID, execute the [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) command and specify the **ProductId** parameter.</span></span> <span data-ttu-id="b3b19-117">De **parameter CountryCode** is opties. Als deze niet is opgegeven, wordt het land gebruikt dat is gekoppeld aan de reseller.</span><span class="sxs-lookup"><span data-stu-id="b3b19-117">The **CountryCode** parameter is options, if it isn't specified then the country associated with the reseller will be used.</span></span>

```powershell
Get-PartnerProduct -ProductId 'DZH318Z0BQ3Q'
```

## <a name="rest-request"></a><span data-ttu-id="b3b19-118">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="b3b19-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b3b19-119">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="b3b19-119">Request syntax</span></span>

| <span data-ttu-id="b3b19-120">Methode</span><span class="sxs-lookup"><span data-stu-id="b3b19-120">Method</span></span>  | <span data-ttu-id="b3b19-121">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="b3b19-121">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="b3b19-122">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="b3b19-122">**GET**</span></span> | <span data-ttu-id="b3b19-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}?country={country} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b3b19-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}?country={country} HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="b3b19-124">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="b3b19-124">URI parameter</span></span>

<span data-ttu-id="b3b19-125">Gebruik de volgende padparameters om het opgegeven product op te halen.</span><span class="sxs-lookup"><span data-stu-id="b3b19-125">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="b3b19-126">Naam</span><span class="sxs-lookup"><span data-stu-id="b3b19-126">Name</span></span>                   | <span data-ttu-id="b3b19-127">Type</span><span class="sxs-lookup"><span data-stu-id="b3b19-127">Type</span></span>     | <span data-ttu-id="b3b19-128">Vereist</span><span class="sxs-lookup"><span data-stu-id="b3b19-128">Required</span></span> | <span data-ttu-id="b3b19-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b3b19-129">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="b3b19-130">product-id</span><span class="sxs-lookup"><span data-stu-id="b3b19-130">product-id</span></span>             | <span data-ttu-id="b3b19-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b3b19-131">string</span></span>   | <span data-ttu-id="b3b19-132">Ja</span><span class="sxs-lookup"><span data-stu-id="b3b19-132">Yes</span></span>      | <span data-ttu-id="b3b19-133">Een tekenreeks die het product identificeert.</span><span class="sxs-lookup"><span data-stu-id="b3b19-133">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="b3b19-134">country</span><span class="sxs-lookup"><span data-stu-id="b3b19-134">country</span></span>                | <span data-ttu-id="b3b19-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b3b19-135">string</span></span>   | <span data-ttu-id="b3b19-136">Ja</span><span class="sxs-lookup"><span data-stu-id="b3b19-136">Yes</span></span>      | <span data-ttu-id="b3b19-137">Een land-/regio-id.</span><span class="sxs-lookup"><span data-stu-id="b3b19-137">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="b3b19-138">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="b3b19-138">Request headers</span></span>

<span data-ttu-id="b3b19-139">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="b3b19-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b3b19-140">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="b3b19-140">Request body</span></span>

<span data-ttu-id="b3b19-141">Geen.</span><span class="sxs-lookup"><span data-stu-id="b3b19-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b3b19-142">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b3b19-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products/{product-id}?country=US HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="b3b19-143">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="b3b19-143">REST response</span></span>

<span data-ttu-id="b3b19-144">Als dit lukt, bevat de antwoord-body een [Product-resource.](product-resources.md#product)</span><span class="sxs-lookup"><span data-stu-id="b3b19-144">If successful, the response body contains a [Product](product-resources.md#product) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b3b19-145">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="b3b19-145">Response success and error codes</span></span>

<span data-ttu-id="b3b19-146">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="b3b19-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b3b19-147">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="b3b19-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b3b19-148">Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="b3b19-148">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="b3b19-149">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="b3b19-149">This method returns the following error codes:</span></span>

| <span data-ttu-id="b3b19-150">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="b3b19-150">HTTP Status Code</span></span>     | <span data-ttu-id="b3b19-151">Foutcode</span><span class="sxs-lookup"><span data-stu-id="b3b19-151">Error code</span></span>   | <span data-ttu-id="b3b19-152">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b3b19-152">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="b3b19-153">404</span><span class="sxs-lookup"><span data-stu-id="b3b19-153">404</span></span>                  | <span data-ttu-id="b3b19-154">400013</span><span class="sxs-lookup"><span data-stu-id="b3b19-154">400013</span></span>       | <span data-ttu-id="b3b19-155">Product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="b3b19-155">Product was not found.</span></span>                                                     |

### <a name="response-example"></a><span data-ttu-id="b3b19-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b3b19-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1918
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
Date: Tue, 23 Jan 2018 23:13:01 GMT

{
    "id": "DZH318Z0BQ3Q",
    "title": "Virtual Machines DSv2 Series",
    "description": "Dsv2-series instances are the latest generation of D-series instances that will carry more powerful CPUs which are on average about 35% faster than D-series instances, and carry the same memory and disk configurations as the D-series. Dsv2-series instances are based on the latest generation 2.4 GHz Intel Xeon® E5-2673 v3 (Haswell) processor, and with Intel Turbo Boost Technology 2.0 can go to 3.2 GHz.",
    "productType": {
        "id": "Azure",
        "displayName": "Azure",
        "subType": {
            "id": "VirtualMachines",
            "displayName": "VirtualMachines"
        }
    },
    "isMicrosoftProduct": true,
    "publisherName": "Microsoft",
    "links": {
        "skus": {
            "uri": "/products/DZH318Z0BQ3Q/skus?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/products/DZH318Z0BQ3Q?country=US",
            "method": "GET",
            "headers": []
        }
    }
}
```
