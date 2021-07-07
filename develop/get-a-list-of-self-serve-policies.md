---
title: Een lijst met self-serve-beleidsregels op halen
description: Een verzameling resources ophalen die het self-servicebeleid van een klant vertegenwoordigen.
ms.date: 07/06/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b18fde8a11d3ed3dd31e50fdba746dd6b0bf3f97
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025727"
---
# <a name="get-a-list-of-self-serve-policies"></a><span data-ttu-id="c3964-103">Een lijst met self-serve-beleidsregels op halen</span><span class="sxs-lookup"><span data-stu-id="c3964-103">Get a list of self-serve policies</span></span>

<span data-ttu-id="c3964-104">Haalt een verzameling resources op die self-serve-beleidsregels voor een entiteit vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c3964-104">Gets a collection of resources that represents self-serve policies for an entity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c3964-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c3964-105">Prerequisites</span></span>

- <span data-ttu-id="c3964-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c3964-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c3964-107">Dit scenario ondersteunt verificatie met referenties voor toepassing en gebruiker.</span><span class="sxs-lookup"><span data-stu-id="c3964-107">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="c3964-108">C\#</span><span class="sxs-lookup"><span data-stu-id="c3964-108">C\#</span></span>

<span data-ttu-id="c3964-109">Een lijst met alle self-serve-beleidsregels op te halen:</span><span class="sxs-lookup"><span data-stu-id="c3964-109">To get a list of all self-serve policies:</span></span>

1. <span data-ttu-id="c3964-110">Roep de [**methode IAggregatePartner.SelfServePolicies**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection) aan met de entiteits-id om een interface op te halen voor bewerkingen op het beleid.</span><span class="sxs-lookup"><span data-stu-id="c3964-110">Call the [**IAggregatePartner.SelfServePolicies**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// gets the self-serve policies
var SelfServePolicies = scopedPartnerOperations.SelfServePolicies.Get(customerIdAsEntity);
```

<span data-ttu-id="c3964-111">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="c3964-111">For an example, see the following:</span></span>

- <span data-ttu-id="c3964-112">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="c3964-112">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="c3964-113">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="c3964-113">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="c3964-114">Klasse: **GetSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="c3964-114">Class: **GetSelfServePolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="c3964-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c3964-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c3964-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="c3964-116">Request syntax</span></span>

| <span data-ttu-id="c3964-117">Methode</span><span class="sxs-lookup"><span data-stu-id="c3964-117">Method</span></span>  | <span data-ttu-id="c3964-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c3964-118">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="c3964-119">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="c3964-119">**GET**</span></span> | <span data-ttu-id="c3964-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy?entity_id={entity_id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="c3964-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy?entity_id={entity_id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="c3964-121">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="c3964-121">URI parameter</span></span>

<span data-ttu-id="c3964-122">Gebruik de volgende queryparameter om een lijst met klanten op te halen.</span><span class="sxs-lookup"><span data-stu-id="c3964-122">Use the following query parameter to get a list of customers.</span></span>

| <span data-ttu-id="c3964-123">Naam</span><span class="sxs-lookup"><span data-stu-id="c3964-123">Name</span></span>          | <span data-ttu-id="c3964-124">Type</span><span class="sxs-lookup"><span data-stu-id="c3964-124">Type</span></span>       | <span data-ttu-id="c3964-125">Vereist</span><span class="sxs-lookup"><span data-stu-id="c3964-125">Required</span></span> | <span data-ttu-id="c3964-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c3964-126">Description</span></span>                                        |
|---------------|------------|----------|----------------------------------------------------|
| <span data-ttu-id="c3964-127">**entity_id**</span><span class="sxs-lookup"><span data-stu-id="c3964-127">**entity_id**</span></span> | <span data-ttu-id="c3964-128">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="c3964-128">**string**</span></span> | <span data-ttu-id="c3964-129">J</span><span class="sxs-lookup"><span data-stu-id="c3964-129">Y</span></span>        | <span data-ttu-id="c3964-130">De entiteits-id die toegang aanvraagt.</span><span class="sxs-lookup"><span data-stu-id="c3964-130">The entity identifier requesting access for.</span></span> <span data-ttu-id="c3964-131">Dit is de tenant-id van de klant.</span><span class="sxs-lookup"><span data-stu-id="c3964-131">This will be the customer's tenant ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c3964-132">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c3964-132">Request headers</span></span>

<span data-ttu-id="c3964-133">Zie [Headers voor meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="c3964-133">For more information, see [Headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c3964-134">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c3964-134">Request body</span></span>

<span data-ttu-id="c3964-135">Geen.</span><span class="sxs-lookup"><span data-stu-id="c3964-135">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c3964-136">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c3964-136">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/SelfServePolicy?entity_id=0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="c3964-137">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c3964-137">REST response</span></span>

<span data-ttu-id="c3964-138">Als dit lukt, retourneert deze methode een verzameling [SelfServePolicy-resources](self-serve-policy-resources.md#selfservepolicy) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="c3964-138">If successful, this method returns a collection of [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c3964-139">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="c3964-139">Response success and error codes</span></span>

<span data-ttu-id="c3964-140">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="c3964-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c3964-141">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c3964-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c3964-142">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="c3964-142">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c3964-143">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c3964-143">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 15650
Content-Type: application/json
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
Date: Fri, 20 Nov 2015 01:08:23 GMT

{
    "totalCount": 1,
    "items": [{
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
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
