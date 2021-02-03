---
title: Een lijst met Sku's voor een product ophalen (per klant)
description: Hiermee wordt een verzameling Sku's opgehaald voor het opgegeven product per klant.
ms.assetid: ''
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 6b9c9bcd52798006d7f686405f059192a722c7e8
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767293"
---
# <a name="get-a-list-of-skus-for-a-product-by-customer"></a><span data-ttu-id="5765a-103">Een lijst met Sku's voor een product ophalen (per klant)</span><span class="sxs-lookup"><span data-stu-id="5765a-103">Get a list of SKUs for a product (by customer)</span></span>

<span data-ttu-id="5765a-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="5765a-104">**Applies To**</span></span>

- <span data-ttu-id="5765a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="5765a-105">Partner Center</span></span>
- <span data-ttu-id="5765a-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="5765a-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="5765a-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="5765a-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="5765a-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="5765a-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="5765a-109">Hiermee wordt een verzameling Sku's opgehaald voor een bepaald product dat beschikbaar is voor een bestaande klant.</span><span class="sxs-lookup"><span data-stu-id="5765a-109">Gets a collection of SKUs for a particular product that is available to an existing customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5765a-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5765a-110">Prerequisites</span></span>

- <span data-ttu-id="5765a-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5765a-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5765a-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="5765a-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="5765a-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5765a-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5765a-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="5765a-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5765a-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="5765a-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5765a-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="5765a-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5765a-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="5765a-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5765a-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5765a-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="5765a-119">Een product-ID (**product-id**).</span><span class="sxs-lookup"><span data-stu-id="5765a-119">A product ID (**product-id**).</span></span>

## <a name="rest-request"></a><span data-ttu-id="5765a-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="5765a-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5765a-121">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5765a-121">Request syntax</span></span>

| <span data-ttu-id="5765a-122">Methode</span><span class="sxs-lookup"><span data-stu-id="5765a-122">Method</span></span> | <span data-ttu-id="5765a-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="5765a-123">Request URI</span></span>                                                                                                        |
|--------|--------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5765a-124">POST</span><span class="sxs-lookup"><span data-stu-id="5765a-124">POST</span></span>   | <span data-ttu-id="5765a-125">[*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/products/{product-id}/SKUs http/1.1</span><span class="sxs-lookup"><span data-stu-id="5765a-125">[*\{baseURL\}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/products/{product-id}/skus HTTP/1.1</span></span> |

### <a name="request-uri-parameter"></a><span data-ttu-id="5765a-126">URI-para meter aanvragen</span><span class="sxs-lookup"><span data-stu-id="5765a-126">Request URI parameter</span></span>

| <span data-ttu-id="5765a-127">Naam</span><span class="sxs-lookup"><span data-stu-id="5765a-127">Name</span></span>               | <span data-ttu-id="5765a-128">Type</span><span class="sxs-lookup"><span data-stu-id="5765a-128">Type</span></span> | <span data-ttu-id="5765a-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="5765a-129">Required</span></span> | <span data-ttu-id="5765a-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5765a-130">Description</span></span>                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="5765a-131">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="5765a-131">customer-tenant-id</span></span> | <span data-ttu-id="5765a-132">GUID</span><span class="sxs-lookup"><span data-stu-id="5765a-132">GUID</span></span> | <span data-ttu-id="5765a-133">Yes</span><span class="sxs-lookup"><span data-stu-id="5765a-133">Yes</span></span> | <span data-ttu-id="5765a-134">De waarde is een **klant-Tenant-id** van de GUID-indeling, een id waarmee u een klant kunt opgeven.</span><span class="sxs-lookup"><span data-stu-id="5765a-134">The value is a GUID-formatted **customer-tenant-id**, which is an identifier that allows you to specify a customer.</span></span> |
| <span data-ttu-id="5765a-135">product-id</span><span class="sxs-lookup"><span data-stu-id="5765a-135">product-id</span></span> | <span data-ttu-id="5765a-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="5765a-136">string</span></span> | <span data-ttu-id="5765a-137">Yes</span><span class="sxs-lookup"><span data-stu-id="5765a-137">Yes</span></span> | <span data-ttu-id="5765a-138">Een teken reeks waarmee het product wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="5765a-138">A string that identifies the product.</span></span> |

### <a name="request-header"></a><span data-ttu-id="5765a-139">Aanvraagheader</span><span class="sxs-lookup"><span data-stu-id="5765a-139">Request header</span></span>

<span data-ttu-id="5765a-140">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5765a-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5765a-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="5765a-141">Request body</span></span>

<span data-ttu-id="5765a-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="5765a-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5765a-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5765a-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65543400-f8b0-4783-8530-6d35ab8c6801/products/DZH318Z0BPS6 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 83643f5e-5dfd-4375-88ed-054412460dc8
MS-CorrelationId: b1939cb2-e83d-4fb0-989f-514fb741b734
```

## <a name="rest-response"></a><span data-ttu-id="5765a-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="5765a-144">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5765a-145">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="5765a-145">Response success and error codes</span></span>

<span data-ttu-id="5765a-146">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="5765a-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5765a-147">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="5765a-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5765a-148">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="5765a-148">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="5765a-149">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="5765a-149">This method returns the following error codes:</span></span>

| <span data-ttu-id="5765a-150">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="5765a-150">HTTP Status Code</span></span> | <span data-ttu-id="5765a-151">Foutcode</span><span class="sxs-lookup"><span data-stu-id="5765a-151">Error code</span></span> | <span data-ttu-id="5765a-152">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5765a-152">Description</span></span> |
|------------------|------------|-------------|
| <span data-ttu-id="5765a-153">404</span><span class="sxs-lookup"><span data-stu-id="5765a-153">404</span></span> | <span data-ttu-id="5765a-154">400013</span><span class="sxs-lookup"><span data-stu-id="5765a-154">400013</span></span> | <span data-ttu-id="5765a-155">Het bovenliggende product is niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="5765a-155">The parent product was not found.</span></span> |

### <a name="response-example"></a><span data-ttu-id="5765a-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="5765a-156">Response example</span></span>

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
