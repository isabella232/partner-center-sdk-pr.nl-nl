---
title: Een product ophalen op basis van id
description: Hiermee wordt de opgegeven product resource opgehaald met behulp van een product-ID.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 8aca626597e9ec903ebecca7d55577ba636c518e
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767272"
---
# <a name="get-a-product-by-id"></a><span data-ttu-id="aecdf-103">Een product ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="aecdf-103">Get a product by ID</span></span>

<span data-ttu-id="aecdf-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="aecdf-104">**Applies To**</span></span>

- <span data-ttu-id="aecdf-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="aecdf-105">Partner Center</span></span>

<span data-ttu-id="aecdf-106">Hiermee wordt de opgegeven product resource opgehaald met behulp van een product-ID.</span><span class="sxs-lookup"><span data-stu-id="aecdf-106">Gets the specified product resource using a product ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aecdf-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="aecdf-107">Prerequisites</span></span>

- <span data-ttu-id="aecdf-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="aecdf-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="aecdf-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="aecdf-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="aecdf-110">Een product-ID.</span><span class="sxs-lookup"><span data-stu-id="aecdf-110">A product ID.</span></span>

## <a name="c"></a><span data-ttu-id="aecdf-111">C\#</span><span class="sxs-lookup"><span data-stu-id="aecdf-111">C\#</span></span>

<span data-ttu-id="aecdf-112">Als u een specifiek product op ID wilt zoeken, gebruikt u de verzameling **IAggregatePartner. Products** , selecteert u het land met behulp van de methode **ByCountry ()** en roept u vervolgens de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="aecdf-112">To find a specific product by ID, use your **IAggregatePartner.Products** collection, select the country by using the **ByCountry()** method, then call the **ById()** method.</span></span> <span data-ttu-id="aecdf-113">Roep ten slotte de methode **Get ()** of **GetAsync ()** aan om het product te retour neren.</span><span class="sxs-lookup"><span data-stu-id="aecdf-113">Finally, call the **Get()** or **GetAsync()** method to return the product.</span></span>

```csharp
// IAggregatePartner partnerOperations;

Product productDetail = partnerOperations.Products.ByCountry("US").ById("DZH318Z0BQ3Q").Get();
```

## <a name="java"></a><span data-ttu-id="aecdf-114">Java</span><span class="sxs-lookup"><span data-stu-id="aecdf-114">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](<../includes/java-sdk-support.md>)]

<span data-ttu-id="aecdf-115">Als u een specifiek product op ID wilt zoeken, gebruikt u de functie **IAggregatePartner. getProducts** , selecteert u het land met behulp van de functie **byCountry ()** en roept u vervolgens de functie **byId ()** aan.</span><span class="sxs-lookup"><span data-stu-id="aecdf-115">To find a specific product by ID, use your **IAggregatePartner.getProducts** function, select the country by using the **byCountry()** function, then call the **byId()** function.</span></span> <span data-ttu-id="aecdf-116">Roep tot slot de functie **Get ()** aan om het product te retour neren.</span><span class="sxs-lookup"><span data-stu-id="aecdf-116">Finally, call the **get()** function to return the product.</span></span>

```java
// IAggregatePartner partnerOperations;

Product productDetail = partnerOperations.getProducts().byCountry("US").byId("DZH318Z0BQ3Q").get();
```

## <a name="powershell"></a><span data-ttu-id="aecdf-117">PowerShell</span><span class="sxs-lookup"><span data-stu-id="aecdf-117">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](<../includes/powershell-module-support.md>)]

<span data-ttu-id="aecdf-118">Als u een specifiek product op ID wilt zoeken, voert u de opdracht [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) uit en geeft u de para meter **ProductID** op.</span><span class="sxs-lookup"><span data-stu-id="aecdf-118">To find a specific product by ID, execute the [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) command and specify the **ProductId** parameter.</span></span> <span data-ttu-id="aecdf-119">De para meter **CountryCode** is opties. als deze niet is opgegeven, wordt het land dat is gekoppeld aan de wederverkoper gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aecdf-119">The **CountryCode** parameter is options, if it isn't specified then the country associated with the reseller will be used.</span></span>

```powershell
Get-PartnerProduct -ProductId 'DZH318Z0BQ3Q'
```

## <a name="rest-request"></a><span data-ttu-id="aecdf-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="aecdf-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="aecdf-121">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="aecdf-121">Request syntax</span></span>

| <span data-ttu-id="aecdf-122">Methode</span><span class="sxs-lookup"><span data-stu-id="aecdf-122">Method</span></span>  | <span data-ttu-id="aecdf-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="aecdf-123">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="aecdf-124">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="aecdf-124">**GET**</span></span> | <span data-ttu-id="aecdf-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}? land = {Country} http/1.1</span><span class="sxs-lookup"><span data-stu-id="aecdf-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}?country={country} HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="aecdf-126">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="aecdf-126">URI parameter</span></span>

<span data-ttu-id="aecdf-127">Gebruik de volgende Path-para meters om het opgegeven product op te halen.</span><span class="sxs-lookup"><span data-stu-id="aecdf-127">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="aecdf-128">Naam</span><span class="sxs-lookup"><span data-stu-id="aecdf-128">Name</span></span>                   | <span data-ttu-id="aecdf-129">Type</span><span class="sxs-lookup"><span data-stu-id="aecdf-129">Type</span></span>     | <span data-ttu-id="aecdf-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="aecdf-130">Required</span></span> | <span data-ttu-id="aecdf-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="aecdf-131">Description</span></span>                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="aecdf-132">product-id</span><span class="sxs-lookup"><span data-stu-id="aecdf-132">product-id</span></span>             | <span data-ttu-id="aecdf-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="aecdf-133">string</span></span>   | <span data-ttu-id="aecdf-134">Yes</span><span class="sxs-lookup"><span data-stu-id="aecdf-134">Yes</span></span>      | <span data-ttu-id="aecdf-135">Een teken reeks waarmee het product wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="aecdf-135">A string that identifies the product.</span></span>                           |
| <span data-ttu-id="aecdf-136">country</span><span class="sxs-lookup"><span data-stu-id="aecdf-136">country</span></span>                | <span data-ttu-id="aecdf-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="aecdf-137">string</span></span>   | <span data-ttu-id="aecdf-138">Yes</span><span class="sxs-lookup"><span data-stu-id="aecdf-138">Yes</span></span>      | <span data-ttu-id="aecdf-139">Een land/regio-ID.</span><span class="sxs-lookup"><span data-stu-id="aecdf-139">A country/region ID.</span></span>                                            |

### <a name="request-headers"></a><span data-ttu-id="aecdf-140">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="aecdf-140">Request headers</span></span>

<span data-ttu-id="aecdf-141">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="aecdf-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="aecdf-142">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="aecdf-142">Request body</span></span>

<span data-ttu-id="aecdf-143">Geen.</span><span class="sxs-lookup"><span data-stu-id="aecdf-143">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="aecdf-144">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="aecdf-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/products/{product-id}?country=US HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="aecdf-145">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="aecdf-145">REST response</span></span>

<span data-ttu-id="aecdf-146">Als dit lukt, bevat de antwoord tekst een [product](product-resources.md#product) bron.</span><span class="sxs-lookup"><span data-stu-id="aecdf-146">If successful, the response body contains a [Product](product-resources.md#product) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="aecdf-147">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="aecdf-147">Response success and error codes</span></span>

<span data-ttu-id="aecdf-148">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="aecdf-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="aecdf-149">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="aecdf-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="aecdf-150">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="aecdf-150">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="aecdf-151">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="aecdf-151">This method returns the following error codes:</span></span>

| <span data-ttu-id="aecdf-152">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="aecdf-152">HTTP Status Code</span></span>     | <span data-ttu-id="aecdf-153">Foutcode</span><span class="sxs-lookup"><span data-stu-id="aecdf-153">Error code</span></span>   | <span data-ttu-id="aecdf-154">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="aecdf-154">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="aecdf-155">404</span><span class="sxs-lookup"><span data-stu-id="aecdf-155">404</span></span>                  | <span data-ttu-id="aecdf-156">400013</span><span class="sxs-lookup"><span data-stu-id="aecdf-156">400013</span></span>       | <span data-ttu-id="aecdf-157">Het product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="aecdf-157">Product was not found.</span></span>                                                     |

### <a name="response-example"></a><span data-ttu-id="aecdf-158">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="aecdf-158">Response example</span></span>

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
