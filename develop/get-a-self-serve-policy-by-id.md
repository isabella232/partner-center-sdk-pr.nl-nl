---
title: Een beleid voor eigen beheer op basis van id ophalen
description: Hiermee wordt het opgegeven beleid voor zelf behoud opgehaald met de ID.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: ec01d0d9b7c3858cdacf1dbaad3b2b0bb7b6a1a4
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767290"
---
# <a name="get-a-self-serve-policy-by-id"></a><span data-ttu-id="fe58e-103">Een beleid voor eigen beheer op basis van id ophalen</span><span class="sxs-lookup"><span data-stu-id="fe58e-103">Get a self serve policy by ID</span></span>

<span data-ttu-id="fe58e-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="fe58e-104">**Applies To**</span></span>

- <span data-ttu-id="fe58e-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="fe58e-105">Partner Center</span></span>

<span data-ttu-id="fe58e-106">Hiermee wordt het opgegeven beleid voor zelf behoud opgehaald met de ID.</span><span class="sxs-lookup"><span data-stu-id="fe58e-106">Gets the specified self serve policy using its ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fe58e-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fe58e-107">Prerequisites</span></span>

- <span data-ttu-id="fe58e-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fe58e-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fe58e-109">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="fe58e-109">This scenario supports authentication with App+User credentials.</span></span>
- <span data-ttu-id="fe58e-110">Een selfservice beleids-ID.</span><span class="sxs-lookup"><span data-stu-id="fe58e-110">A self serve policy ID.</span></span>

## <a name="examples"></a><span data-ttu-id="fe58e-111">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="fe58e-111">Examples</span></span>


## <a name="span-idrest_requestspan-idrest_requestspan-idrest_requestrest-request"></a><span data-ttu-id="fe58e-112"><span id="REST_Request"/><span id="rest_request"/><span id="REST_REQUEST"/>REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fe58e-112"><span id="REST_Request"/><span id="rest_request"/><span id="REST_REQUEST"/>REST Request</span></span>

<span data-ttu-id="fe58e-113">**Syntaxis van aanvraag**</span><span class="sxs-lookup"><span data-stu-id="fe58e-113">**Request syntax**</span></span>

| <span data-ttu-id="fe58e-114">Methode</span><span class="sxs-lookup"><span data-stu-id="fe58e-114">Method</span></span>  | <span data-ttu-id="fe58e-115">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fe58e-115">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="fe58e-116">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fe58e-116">**GET**</span></span> | <span data-ttu-id="fe58e-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="fe58e-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span></span> |

<span data-ttu-id="fe58e-118">**URI-para meter**</span><span class="sxs-lookup"><span data-stu-id="fe58e-118">**URI parameter**</span></span>

<span data-ttu-id="fe58e-119">Gebruik de volgende Path-para meters om het opgegeven product op te halen.</span><span class="sxs-lookup"><span data-stu-id="fe58e-119">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="fe58e-120">Naam</span><span class="sxs-lookup"><span data-stu-id="fe58e-120">Name</span></span>                       | <span data-ttu-id="fe58e-121">Type</span><span class="sxs-lookup"><span data-stu-id="fe58e-121">Type</span></span>         | <span data-ttu-id="fe58e-122">Vereist</span><span class="sxs-lookup"><span data-stu-id="fe58e-122">Required</span></span> | <span data-ttu-id="fe58e-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fe58e-123">Description</span></span>                                                     |
|----------------------------|--------------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="fe58e-124">**SelfServePolicy-id**</span><span class="sxs-lookup"><span data-stu-id="fe58e-124">**SelfServePolicy-id**</span></span>     | <span data-ttu-id="fe58e-125">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="fe58e-125">**string**</span></span>   | <span data-ttu-id="fe58e-126">Yes</span><span class="sxs-lookup"><span data-stu-id="fe58e-126">Yes</span></span>      | <span data-ttu-id="fe58e-127">Een teken reeks waarmee het beleid voor zelf beheer wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="fe58e-127">A string that identifies the self serve policy.</span></span>                 |

<span data-ttu-id="fe58e-128">**Aanvraagheaders**</span><span class="sxs-lookup"><span data-stu-id="fe58e-128">**Request headers**</span></span>

- <span data-ttu-id="fe58e-129">Zie [kopteksten](headers.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fe58e-129">See [Headers](headers.md) for more information.</span></span>

<span data-ttu-id="fe58e-130">**Aanvraagbody**</span><span class="sxs-lookup"><span data-stu-id="fe58e-130">**Request body**</span></span>

<span data-ttu-id="fe58e-131">Geen.</span><span class="sxs-lookup"><span data-stu-id="fe58e-131">None.</span></span>

<span data-ttu-id="fe58e-132">**Voorbeeld van aanvraag**</span><span class="sxs-lookup"><span data-stu-id="fe58e-132">**Request example**</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/SelfServePolicy/634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer  <token>
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="fe58e-133">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fe58e-133">REST response</span></span>

<span data-ttu-id="fe58e-134">Als dit lukt, bevat de antwoord tekst een [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) -resource.</span><span class="sxs-lookup"><span data-stu-id="fe58e-134">If successful, the response body contains a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource.</span></span>

<span data-ttu-id="fe58e-135">**Geslaagde en fout codes**</span><span class="sxs-lookup"><span data-stu-id="fe58e-135">**Response success and error codes**</span></span>

<span data-ttu-id="fe58e-136">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="fe58e-136">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fe58e-137">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fe58e-137">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fe58e-138">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="fe58e-138">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="fe58e-139">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="fe58e-139">This method returns the following error codes:</span></span>

| <span data-ttu-id="fe58e-140">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="fe58e-140">HTTP Status Code</span></span>     | <span data-ttu-id="fe58e-141">Foutcode</span><span class="sxs-lookup"><span data-stu-id="fe58e-141">Error code</span></span>   | <span data-ttu-id="fe58e-142">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fe58e-142">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="fe58e-143">404</span><span class="sxs-lookup"><span data-stu-id="fe58e-143">404</span></span>                  | <span data-ttu-id="fe58e-144">600039</span><span class="sxs-lookup"><span data-stu-id="fe58e-144">600039</span></span>       | <span data-ttu-id="fe58e-145">Er is geen beleid voor zelf beheer gevonden.</span><span class="sxs-lookup"><span data-stu-id="fe58e-145">Self serve policy not found.</span></span>                                                     |

<span data-ttu-id="fe58e-146">**Antwoord voorbeeld**</span><span class="sxs-lookup"><span data-stu-id="fe58e-146">**Response example**</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1918
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
Date: Tue, 23 Jan 2018 23:13:01 GMT

{
    "id": "634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415",
    "selfServeEntity": {
        "selfServeEntityType": "customer",
        "tenantID": "0431a72c-7d8a-4393-b25e-ef63f5efb415"
    },
    "grantor": {
        "grantorType": "billToPartner",
        "tenantID": "634f6379-ad54-449b-9821-564f737158ab"
    },
    "permissions": [{
        "resource": "AzureReservedInstances",
        "action": "Purchase"
    }],
    "attributes": {
        "etag": "\"933523d1-3f63-4fc3-8789-5e21c02cdaed\"",
        "objectType": "SelfServePolicy"
    }
}
```