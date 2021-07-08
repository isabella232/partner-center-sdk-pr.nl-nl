---
title: Een lijst met SKU's voor een product (per klant) op halen
description: Hiermee haalt u een verzameling SKU's op voor het opgegeven product door de klant.
ms.assetid: ''
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b76526d97ba9027897fc88954ba45186d58aefb8
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874156"
---
# <a name="get-a-list-of-skus-for-a-product-by-customer"></a><span data-ttu-id="62b5a-103">Een lijst met SKU's voor een product (per klant) op halen</span><span class="sxs-lookup"><span data-stu-id="62b5a-103">Get a list of SKUs for a product (by customer)</span></span>

<span data-ttu-id="62b5a-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="62b5a-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="62b5a-105">Haalt een verzameling SKU's op voor een bepaald product dat beschikbaar is voor een bestaande klant.</span><span class="sxs-lookup"><span data-stu-id="62b5a-105">Gets a collection of SKUs for a particular product that is available to an existing customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="62b5a-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="62b5a-106">Prerequisites</span></span>

- <span data-ttu-id="62b5a-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="62b5a-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="62b5a-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="62b5a-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="62b5a-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="62b5a-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="62b5a-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="62b5a-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="62b5a-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="62b5a-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="62b5a-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="62b5a-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="62b5a-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="62b5a-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="62b5a-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="62b5a-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="62b5a-115">Een product-id (**product-id**).</span><span class="sxs-lookup"><span data-stu-id="62b5a-115">A product ID (**product-id**).</span></span>

## <a name="rest-request"></a><span data-ttu-id="62b5a-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="62b5a-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="62b5a-117">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="62b5a-117">Request syntax</span></span>

| <span data-ttu-id="62b5a-118">Methode</span><span class="sxs-lookup"><span data-stu-id="62b5a-118">Method</span></span> | <span data-ttu-id="62b5a-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="62b5a-119">Request URI</span></span>                                                                                                        |
|--------|--------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="62b5a-120">POST</span><span class="sxs-lookup"><span data-stu-id="62b5a-120">POST</span></span>   | <span data-ttu-id="62b5a-121">[*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products/{product-id}/skus HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="62b5a-121">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products/{product-id}/skus HTTP/1.1</span></span> |

### <a name="request-uri-parameter"></a><span data-ttu-id="62b5a-122">Aanvraag-URI-parameter</span><span class="sxs-lookup"><span data-stu-id="62b5a-122">Request URI parameter</span></span>

| <span data-ttu-id="62b5a-123">Naam</span><span class="sxs-lookup"><span data-stu-id="62b5a-123">Name</span></span>               | <span data-ttu-id="62b5a-124">Type</span><span class="sxs-lookup"><span data-stu-id="62b5a-124">Type</span></span> | <span data-ttu-id="62b5a-125">Vereist</span><span class="sxs-lookup"><span data-stu-id="62b5a-125">Required</span></span> | <span data-ttu-id="62b5a-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="62b5a-126">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="62b5a-127">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="62b5a-127">customer-tenant-id</span></span> | <span data-ttu-id="62b5a-128">GUID</span><span class="sxs-lookup"><span data-stu-id="62b5a-128">GUID</span></span> | <span data-ttu-id="62b5a-129">Ja</span><span class="sxs-lookup"><span data-stu-id="62b5a-129">Yes</span></span> | <span data-ttu-id="62b5a-130">De waarde is een **klant-tenant-id** in GUID-indeling. Dit is een id waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="62b5a-130">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="62b5a-131">product-id</span><span class="sxs-lookup"><span data-stu-id="62b5a-131">product-id</span></span> | <span data-ttu-id="62b5a-132">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="62b5a-132">string</span></span> | <span data-ttu-id="62b5a-133">Ja</span><span class="sxs-lookup"><span data-stu-id="62b5a-133">Yes</span></span> | <span data-ttu-id="62b5a-134">Een tekenreeks die het product identificeert.</span><span class="sxs-lookup"><span data-stu-id="62b5a-134">A string that identifies the product.</span></span> |

### <a name="request-header"></a><span data-ttu-id="62b5a-135">Aanvraagheader</span><span class="sxs-lookup"><span data-stu-id="62b5a-135">Request header</span></span>

<span data-ttu-id="62b5a-136">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="62b5a-136">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="62b5a-137">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="62b5a-137">Request body</span></span>

<span data-ttu-id="62b5a-138">Geen.</span><span class="sxs-lookup"><span data-stu-id="62b5a-138">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="62b5a-139">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="62b5a-139">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products/DZH318Z0BPS6 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="62b5a-140">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="62b5a-140">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="62b5a-141">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="62b5a-141">Response success and error codes</span></span>

<span data-ttu-id="62b5a-142">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="62b5a-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="62b5a-143">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="62b5a-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="62b5a-144">Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="62b5a-144">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="62b5a-145">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="62b5a-145">This method returns the following error codes:</span></span>

| <span data-ttu-id="62b5a-146">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="62b5a-146">HTTP Status Code</span></span> | <span data-ttu-id="62b5a-147">Foutcode</span><span class="sxs-lookup"><span data-stu-id="62b5a-147">Error code</span></span> | <span data-ttu-id="62b5a-148">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="62b5a-148">Description</span></span> |
|------------------|------------|-------------|
| <span data-ttu-id="62b5a-149">404</span><span class="sxs-lookup"><span data-stu-id="62b5a-149">404</span></span> | <span data-ttu-id="62b5a-150">400013</span><span class="sxs-lookup"><span data-stu-id="62b5a-150">400013</span></span> | <span data-ttu-id="62b5a-151">Het bovenliggende product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="62b5a-151">The parent product was not found.</span></span> |

### <a name="response-example"></a><span data-ttu-id="62b5a-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="62b5a-152">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1909
Content-Type: application/json; charset=utf-8
MS-CorrelationId: cad955c2-8efc-47fe-b112-548ff002ba18
MS-RequestId: ae7288e2-2673-4ad4-8c12-7aad818d5949

{
    "id": "DZH318Z0BPS6",
    "title": "Microsoft Azure plan",
    "description": "Gain access to Azure Services.",
    "productType": {
        "id": "Azure",
        "displayName": "Azure",
        "subType": {
            "id": "Azure",
            "displayName": "Azure"
        }
    },
    "isMicrosoftProduct": true,
    "publisherName": "Microsoft Corporation",
    "links": {
        "skus": {
            "uri": "/products/DZH318Z0BPS6/skus?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/products/DZH318Z0BPS6?country=US",
            "method": "GET",
            "headers": []
        }
    },
    "localizedAttributes": [
        {
            "key": "OfferType",
            "value": "OfferType"
        },
        {
            "key": "Standard",
            "value": "Standard"
        },
        {
            "key": "DevTest",
            "value": "Dev/Test"
        }
    ]
}
```
