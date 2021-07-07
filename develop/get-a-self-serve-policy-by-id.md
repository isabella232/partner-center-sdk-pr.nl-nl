---
title: Een beleid voor self-serve op id krijgen
description: Hiermee haalt u het opgegeven beleid voor self-serve op met behulp van de id.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 074d7ba65c7aab91687a67f50e871cee913fc2bb
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873833"
---
# <a name="get-a-self-serve-policy-by-id"></a><span data-ttu-id="54781-103">Een beleid voor self-serve op id krijgen</span><span class="sxs-lookup"><span data-stu-id="54781-103">Get a self-serve policy by ID</span></span>

<span data-ttu-id="54781-104">Hiermee haalt u het opgegeven beleid voor self-serve op met behulp van de id.</span><span class="sxs-lookup"><span data-stu-id="54781-104">Gets the specified self-serve policy using its ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="54781-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="54781-105">Prerequisites</span></span>

- <span data-ttu-id="54781-106">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="54781-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="54781-107">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="54781-107">This scenario supports authentication with App+User credentials.</span></span>
- <span data-ttu-id="54781-108">Een beleids-id voor self-serve.</span><span class="sxs-lookup"><span data-stu-id="54781-108">A self-serve policy ID.</span></span>

## <a name="examples"></a><span data-ttu-id="54781-109">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="54781-109">Examples</span></span>


## <a name="span-idrest_requestspan-idrest_requestspan-idrest_requestrest-request"></a><span data-ttu-id="54781-110"><span id="REST_Request"/><span id="rest_request"/><span id="REST_REQUEST"/>REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="54781-110"><span id="REST_Request"/><span id="rest_request"/><span id="REST_REQUEST"/>REST Request</span></span>

<span data-ttu-id="54781-111">**Aanvraagsyntaxis**</span><span class="sxs-lookup"><span data-stu-id="54781-111">**Request syntax**</span></span>

| <span data-ttu-id="54781-112">Methode</span><span class="sxs-lookup"><span data-stu-id="54781-112">Method</span></span>  | <span data-ttu-id="54781-113">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="54781-113">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="54781-114">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="54781-114">**GET**</span></span> | <span data-ttu-id="54781-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="54781-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span></span> |

<span data-ttu-id="54781-116">**URI-parameter**</span><span class="sxs-lookup"><span data-stu-id="54781-116">**URI parameter**</span></span>

<span data-ttu-id="54781-117">Gebruik de volgende padparameters om het opgegeven product op te halen.</span><span class="sxs-lookup"><span data-stu-id="54781-117">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="54781-118">Naam</span><span class="sxs-lookup"><span data-stu-id="54781-118">Name</span></span>                       | <span data-ttu-id="54781-119">Type</span><span class="sxs-lookup"><span data-stu-id="54781-119">Type</span></span>         | <span data-ttu-id="54781-120">Vereist</span><span class="sxs-lookup"><span data-stu-id="54781-120">Required</span></span> | <span data-ttu-id="54781-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="54781-121">Description</span></span>                                                     |
|----------------------------|--------------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="54781-122">**SelfServePolicy-id**</span><span class="sxs-lookup"><span data-stu-id="54781-122">**SelfServePolicy-id**</span></span>     | <span data-ttu-id="54781-123">**Tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="54781-123">**string**</span></span>   | <span data-ttu-id="54781-124">Ja</span><span class="sxs-lookup"><span data-stu-id="54781-124">Yes</span></span>      | <span data-ttu-id="54781-125">Een tekenreeks die het self-serve-beleid identificeert.</span><span class="sxs-lookup"><span data-stu-id="54781-125">A string that identifies the self-serve policy.</span></span>                 |

<span data-ttu-id="54781-126">**Aanvraagheaders**</span><span class="sxs-lookup"><span data-stu-id="54781-126">**Request headers**</span></span>

- <span data-ttu-id="54781-127">Zie Headers voor [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="54781-127">For more information, see [Headers](headers.md).</span></span>

<span data-ttu-id="54781-128">**Aanvraagbody**</span><span class="sxs-lookup"><span data-stu-id="54781-128">**Request body**</span></span>

<span data-ttu-id="54781-129">Geen.</span><span class="sxs-lookup"><span data-stu-id="54781-129">None.</span></span>

<span data-ttu-id="54781-130">**Voorbeeld van aanvraag**</span><span class="sxs-lookup"><span data-stu-id="54781-130">**Request example**</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/SelfServePolicy/634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer  <token>
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a><span data-ttu-id="54781-131">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="54781-131">REST response</span></span>

<span data-ttu-id="54781-132">Als dit lukt, bevat de antwoord-body een [SelfServePolicy-resource.](self-serve-policy-resources.md#selfservepolicy)</span><span class="sxs-lookup"><span data-stu-id="54781-132">If successful, the response body contains a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource.</span></span>

<span data-ttu-id="54781-133">**Antwoord geslaagd en foutcodes**</span><span class="sxs-lookup"><span data-stu-id="54781-133">**Response success and error codes**</span></span>

<span data-ttu-id="54781-134">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="54781-134">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="54781-135">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="54781-135">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="54781-136">Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="54781-136">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="54781-137">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="54781-137">This method returns the following error codes:</span></span>

| <span data-ttu-id="54781-138">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="54781-138">HTTP Status Code</span></span>     | <span data-ttu-id="54781-139">Foutcode</span><span class="sxs-lookup"><span data-stu-id="54781-139">Error code</span></span>   | <span data-ttu-id="54781-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="54781-140">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="54781-141">404</span><span class="sxs-lookup"><span data-stu-id="54781-141">404</span></span>                  | <span data-ttu-id="54781-142">600039</span><span class="sxs-lookup"><span data-stu-id="54781-142">600039</span></span>       | <span data-ttu-id="54781-143">Self-serve beleid niet gevonden.</span><span class="sxs-lookup"><span data-stu-id="54781-143">Self-serve policy not found.</span></span>                                                     |

<span data-ttu-id="54781-144">**Voorbeeld van een antwoord**</span><span class="sxs-lookup"><span data-stu-id="54781-144">**Response example**</span></span>

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