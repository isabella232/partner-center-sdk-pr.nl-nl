---
title: Een lijst met beschikbaarheid voor een SKU ophalen (per klant)
description: U kunt een verzameling van Beschik baarheid voor een opgegeven product en SKU per klant verkrijgen met behulp van de klant-, product-en SKU-id's.
ms.assetid: ''
ms.date: 10/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 5f4067916fea911963182954eed77f4e230e79d6
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767303"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-customer"></a><span data-ttu-id="43c98-103">Een lijst met beschikbaarheid voor een SKU ophalen (per klant)</span><span class="sxs-lookup"><span data-stu-id="43c98-103">Get a list of availabilities for a SKU (by customer)</span></span>

<span data-ttu-id="43c98-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="43c98-104">**Applies to:**</span></span>

- <span data-ttu-id="43c98-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="43c98-105">Partner Center</span></span>
- <span data-ttu-id="43c98-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="43c98-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="43c98-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="43c98-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="43c98-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="43c98-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="43c98-109">U kunt de volgende methoden gebruiken om een verzameling van Availabilities te verkrijgen voor een opgegeven product en SKU die beschikbaar is voor een bepaalde klant.</span><span class="sxs-lookup"><span data-stu-id="43c98-109">You can use the following methods to get a collection of availabilities for a specified product and SKU available to a particular customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="43c98-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="43c98-110">Prerequisites</span></span>

- <span data-ttu-id="43c98-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="43c98-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="43c98-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="43c98-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="43c98-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="43c98-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="43c98-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="43c98-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="43c98-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="43c98-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="43c98-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="43c98-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="43c98-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="43c98-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="43c98-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="43c98-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="43c98-119">Een product-id (**product-id**).</span><span class="sxs-lookup"><span data-stu-id="43c98-119">A product identifier (**product-id**).</span></span>

- <span data-ttu-id="43c98-120">Een SKU-id (**SKU-id**).</span><span class="sxs-lookup"><span data-stu-id="43c98-120">A SKU identifier (**sku-id**).</span></span>

## <a name="rest-request"></a><span data-ttu-id="43c98-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="43c98-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="43c98-122">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="43c98-122">Request syntax</span></span>

| <span data-ttu-id="43c98-123">Methode</span><span class="sxs-lookup"><span data-stu-id="43c98-123">Method</span></span> | <span data-ttu-id="43c98-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="43c98-124">Request URI</span></span>                                                                                                                 |
|--------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="43c98-125">POST</span><span class="sxs-lookup"><span data-stu-id="43c98-125">POST</span></span>   | <span data-ttu-id="43c98-126">[*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/products/{product-id}/SKUs/{SKU-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="43c98-126">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products/{product-id}/skus/{sku-id} HTTP/1.1</span></span> |

### <a name="request-uri-parameters"></a><span data-ttu-id="43c98-127">URI-para meters aanvragen</span><span class="sxs-lookup"><span data-stu-id="43c98-127">Request URI parameters</span></span>

| <span data-ttu-id="43c98-128">Naam</span><span class="sxs-lookup"><span data-stu-id="43c98-128">Name</span></span>               | <span data-ttu-id="43c98-129">Type</span><span class="sxs-lookup"><span data-stu-id="43c98-129">Type</span></span> | <span data-ttu-id="43c98-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="43c98-130">Required</span></span> | <span data-ttu-id="43c98-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="43c98-131">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="43c98-132">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="43c98-132">customer-tenant-id</span></span> | <span data-ttu-id="43c98-133">GUID</span><span class="sxs-lookup"><span data-stu-id="43c98-133">GUID</span></span> | <span data-ttu-id="43c98-134">Yes</span><span class="sxs-lookup"><span data-stu-id="43c98-134">Yes</span></span> | <span data-ttu-id="43c98-135">De waarde is een **klant-Tenant-id** van de GUID-indeling, een id waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="43c98-135">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="43c98-136">product-id</span><span class="sxs-lookup"><span data-stu-id="43c98-136">product-id</span></span> | <span data-ttu-id="43c98-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="43c98-137">string</span></span> | <span data-ttu-id="43c98-138">Yes</span><span class="sxs-lookup"><span data-stu-id="43c98-138">Yes</span></span> | <span data-ttu-id="43c98-139">Een teken reeks waarmee het product wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="43c98-139">A string that identifies the product.</span></span> |
| <span data-ttu-id="43c98-140">SKU-id</span><span class="sxs-lookup"><span data-stu-id="43c98-140">sku-id</span></span> | <span data-ttu-id="43c98-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="43c98-141">string</span></span> | <span data-ttu-id="43c98-142">Yes</span><span class="sxs-lookup"><span data-stu-id="43c98-142">Yes</span></span> | <span data-ttu-id="43c98-143">Een teken reeks waarmee de SKU wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="43c98-143">A string that identifies the SKU.</span></span> |

### <a name="request-header"></a><span data-ttu-id="43c98-144">Aanvraagheader</span><span class="sxs-lookup"><span data-stu-id="43c98-144">Request header</span></span>

<span data-ttu-id="43c98-145">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="43c98-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="43c98-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="43c98-146">Request body</span></span>

<span data-ttu-id="43c98-147">Geen.</span><span class="sxs-lookup"><span data-stu-id="43c98-147">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="43c98-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="43c98-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products/DZH318Z0BPS6/skus/0001/availabilities HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="43c98-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="43c98-149">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="43c98-150">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="43c98-150">Response success and error codes</span></span>

<span data-ttu-id="43c98-151">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="43c98-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="43c98-152">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="43c98-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="43c98-153">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="43c98-153">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="43c98-154">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="43c98-154">This method returns the following error codes:</span></span>

| <span data-ttu-id="43c98-155">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="43c98-155">HTTP Status Code</span></span> | <span data-ttu-id="43c98-156">Foutcode</span><span class="sxs-lookup"><span data-stu-id="43c98-156">Error code</span></span> | <span data-ttu-id="43c98-157">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="43c98-157">Description</span></span> |
|------------------|------------|-------------|
| <span data-ttu-id="43c98-158">404</span><span class="sxs-lookup"><span data-stu-id="43c98-158">404</span></span> | <span data-ttu-id="43c98-159">400013</span><span class="sxs-lookup"><span data-stu-id="43c98-159">400013</span></span> | <span data-ttu-id="43c98-160">Het bovenliggende product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="43c98-160">The parent product was not found.</span></span> |

### <a name="response-example"></a><span data-ttu-id="43c98-161">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="43c98-161">Response example</span></span>

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
