---
title: Een lijst met beschikbaarheid voor een SKU ophalen (per klant)
description: U kunt een verzameling beschikbaarheid voor een opgegeven product en SKU per klant ophalen met behulp van de klant-, product- en SKU-id's.
ms.assetid: ''
ms.date: 10/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b237bbd17a6108bbcb4e23529cf476a6b8306f68
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874547"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-customer"></a><span data-ttu-id="6aed0-103">Een lijst met beschikbaarheid voor een SKU ophalen (per klant)</span><span class="sxs-lookup"><span data-stu-id="6aed0-103">Get a list of availabilities for a SKU (by customer)</span></span>

<span data-ttu-id="6aed0-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6aed0-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6aed0-105">U kunt de volgende methoden gebruiken om een verzameling beschikbaarheid te verkrijgen voor een opgegeven product en SKU die beschikbaar zijn voor een bepaalde klant.</span><span class="sxs-lookup"><span data-stu-id="6aed0-105">You can use the following methods to get a collection of availabilities for a specified product and SKU available to a particular customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6aed0-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6aed0-106">Prerequisites</span></span>

- <span data-ttu-id="6aed0-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6aed0-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6aed0-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="6aed0-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="6aed0-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6aed0-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6aed0-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="6aed0-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6aed0-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="6aed0-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6aed0-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="6aed0-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6aed0-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="6aed0-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6aed0-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6aed0-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="6aed0-115">Een product-id (**product-id**).</span><span class="sxs-lookup"><span data-stu-id="6aed0-115">A product identifier (**product-id**).</span></span>

- <span data-ttu-id="6aed0-116">Een SKU-id (**sku-id**).</span><span class="sxs-lookup"><span data-stu-id="6aed0-116">A SKU identifier (**sku-id**).</span></span>

## <a name="rest-request"></a><span data-ttu-id="6aed0-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="6aed0-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6aed0-118">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="6aed0-118">Request syntax</span></span>

| <span data-ttu-id="6aed0-119">Methode</span><span class="sxs-lookup"><span data-stu-id="6aed0-119">Method</span></span> | <span data-ttu-id="6aed0-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="6aed0-120">Request URI</span></span>                                                                                                                 |
|--------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6aed0-121">POST</span><span class="sxs-lookup"><span data-stu-id="6aed0-121">POST</span></span>   | <span data-ttu-id="6aed0-122">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products/{product-id}/skus/{sku-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6aed0-122">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products/{product-id}/skus/{sku-id} HTTP/1.1</span></span> |

### <a name="request-uri-parameters"></a><span data-ttu-id="6aed0-123">Aanvraag-URI-parameters</span><span class="sxs-lookup"><span data-stu-id="6aed0-123">Request URI parameters</span></span>

| <span data-ttu-id="6aed0-124">Naam</span><span class="sxs-lookup"><span data-stu-id="6aed0-124">Name</span></span>               | <span data-ttu-id="6aed0-125">Type</span><span class="sxs-lookup"><span data-stu-id="6aed0-125">Type</span></span> | <span data-ttu-id="6aed0-126">Vereist</span><span class="sxs-lookup"><span data-stu-id="6aed0-126">Required</span></span> | <span data-ttu-id="6aed0-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6aed0-127">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="6aed0-128">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="6aed0-128">customer-tenant-id</span></span> | <span data-ttu-id="6aed0-129">GUID</span><span class="sxs-lookup"><span data-stu-id="6aed0-129">GUID</span></span> | <span data-ttu-id="6aed0-130">Ja</span><span class="sxs-lookup"><span data-stu-id="6aed0-130">Yes</span></span> | <span data-ttu-id="6aed0-131">De waarde is een **klant-tenant-id** in GUID-indeling. Dit is een id waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="6aed0-131">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="6aed0-132">product-id</span><span class="sxs-lookup"><span data-stu-id="6aed0-132">product-id</span></span> | <span data-ttu-id="6aed0-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6aed0-133">string</span></span> | <span data-ttu-id="6aed0-134">Ja</span><span class="sxs-lookup"><span data-stu-id="6aed0-134">Yes</span></span> | <span data-ttu-id="6aed0-135">Een tekenreeks die het product identificeert.</span><span class="sxs-lookup"><span data-stu-id="6aed0-135">A string that identifies the product.</span></span> |
| <span data-ttu-id="6aed0-136">sku-id</span><span class="sxs-lookup"><span data-stu-id="6aed0-136">sku-id</span></span> | <span data-ttu-id="6aed0-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6aed0-137">string</span></span> | <span data-ttu-id="6aed0-138">Ja</span><span class="sxs-lookup"><span data-stu-id="6aed0-138">Yes</span></span> | <span data-ttu-id="6aed0-139">Een tekenreeks die de SKU identificeert.</span><span class="sxs-lookup"><span data-stu-id="6aed0-139">A string that identifies the SKU.</span></span> |

### <a name="request-header"></a><span data-ttu-id="6aed0-140">Aanvraagheader</span><span class="sxs-lookup"><span data-stu-id="6aed0-140">Request header</span></span>

<span data-ttu-id="6aed0-141">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="6aed0-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6aed0-142">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="6aed0-142">Request body</span></span>

<span data-ttu-id="6aed0-143">Geen.</span><span class="sxs-lookup"><span data-stu-id="6aed0-143">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6aed0-144">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6aed0-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products/DZH318Z0BPS6/skus/0001/availabilities HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="6aed0-145">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="6aed0-145">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6aed0-146">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="6aed0-146">Response success and error codes</span></span>

<span data-ttu-id="6aed0-147">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="6aed0-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6aed0-148">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="6aed0-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6aed0-149">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="6aed0-149">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="6aed0-150">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="6aed0-150">This method returns the following error codes:</span></span>

| <span data-ttu-id="6aed0-151">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="6aed0-151">HTTP Status Code</span></span> | <span data-ttu-id="6aed0-152">Foutcode</span><span class="sxs-lookup"><span data-stu-id="6aed0-152">Error code</span></span> | <span data-ttu-id="6aed0-153">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6aed0-153">Description</span></span> |
|------------------|------------|-------------|
| <span data-ttu-id="6aed0-154">404</span><span class="sxs-lookup"><span data-stu-id="6aed0-154">404</span></span> | <span data-ttu-id="6aed0-155">400013</span><span class="sxs-lookup"><span data-stu-id="6aed0-155">400013</span></span> | <span data-ttu-id="6aed0-156">Het bovenliggende product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="6aed0-156">The parent product was not found.</span></span> |

### <a name="response-example"></a><span data-ttu-id="6aed0-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="6aed0-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1909
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cad955c2-8efc-47fe-b112-548ff002ba18
MS-RequestId: ae7288e2-2673-4ad4-8c12-7aad818d5949
{
    "id": "0001",
    "productId": "DZH318Z0BPS6",
    "title": "Microsoft Azure plan",
    "description": "Microsoft Azure plan (MS-AZR-0017G)",
    "minimumQuantity": 1,
    "maximumQuantity": 1,
    "isTrial": false,
    "supportedBillingCycles": [
        "one_time"
    ],
    "purchasePrerequisites": [
        "MicrosoftCustomerAgreement"
    ],
    "inventoryVariables": [],
    "provisioningVariables": [],
    "actions": [
        "Refund"
    ],
    "dynamicAttributes": {
        "isMicrosoftProduct": true,
        "pilotProgram": "modernazurepilot"
    },
    "links": {
        "availabilities": {
            "uri": "/products/DZH318Z0BPS6/skus/0001/availabilities?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/products/DZH318Z0BPS6/skus/0001?country=US",
            "method": "GET",
            "headers": []
        }
    }
}
```
