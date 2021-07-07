---
title: Een self-serve-beleid maken
description: Een nieuw self-serve-beleid maken.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 14f46e22fbd294c765b745204cf62474250cbfbd
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973685"
---
# <a name="create-a-selfservepolicy"></a><span data-ttu-id="e7a16-103">Een SelfServePolicy maken</span><span class="sxs-lookup"><span data-stu-id="e7a16-103">Create a SelfServePolicy</span></span>

<span data-ttu-id="e7a16-104">In dit artikel wordt uitgelegd hoe u een nieuw beleid voor self-serve maakt.</span><span class="sxs-lookup"><span data-stu-id="e7a16-104">This article explains how to create a new self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e7a16-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e7a16-105">Prerequisites</span></span>

- <span data-ttu-id="e7a16-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e7a16-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e7a16-107">Dit scenario ondersteunt verificatie met referenties voor toepassing en gebruiker.</span><span class="sxs-lookup"><span data-stu-id="e7a16-107">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="e7a16-108">C\#</span><span class="sxs-lookup"><span data-stu-id="e7a16-108">C\#</span></span>

<span data-ttu-id="e7a16-109">Een self-serve-beleid maken:</span><span class="sxs-lookup"><span data-stu-id="e7a16-109">Create a self-serve policy:</span></span>

1. <span data-ttu-id="e7a16-110">Roep de [**methode IAggregatePartner.SelfServePolicies.Create**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.create) of [**IAggregatePartner.SelfServePolicies.CreateAsync**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.createasync) aan met de selfservicebeleidsgegevens.</span><span class="sxs-lookup"><span data-stu-id="e7a16-110">Call the [**IAggregatePartner.SelfServePolicies.Create**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.create) or [**IAggregatePartner.SelfServePolicies.CreateAsync**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.createasync) method with the self-serve policy info.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
string customerIdAsEntity;

var selfServePolicy = new SelfServePolicy
{
    SelfServeEntity = new SelfServeEntity
    {
        SelfServeEntityType = "customer",
        TenantID = customerIdAsEntity,
    },
    Grantor = new Grantor
    {
        GrantorType = "billToPartner",
        TenantID = partnerIdAsGrantor,
    },
    Permissions = new Permission[]
    {
        new Permission
        {
        Action = "Purchase",
        Resource = "AzureReservedInstances",
        },
    },
};

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// creates the self-serve policy
SelfServePolicy createdSelfServePolicy = scopedPartnerOperations.selfServePolicies.Create(selfServePolicy);
```

<span data-ttu-id="e7a16-111">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="e7a16-111">For an example, see the following:</span></span>

- <span data-ttu-id="e7a16-112">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="e7a16-112">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="e7a16-113">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="e7a16-113">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="e7a16-114">Klasse: **CreateSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="e7a16-114">Class: **CreateSelfServePolicies.cs**</span></span>


## <a name="rest-request"></a><span data-ttu-id="e7a16-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e7a16-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e7a16-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e7a16-116">Request syntax</span></span>

| <span data-ttu-id="e7a16-117">Methode</span><span class="sxs-lookup"><span data-stu-id="e7a16-117">Method</span></span>   | <span data-ttu-id="e7a16-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e7a16-118">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="e7a16-119">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="e7a16-119">**POST**</span></span> | <span data-ttu-id="e7a16-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e7a16-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e7a16-121">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e7a16-121">Request headers</span></span>

- <span data-ttu-id="e7a16-122">Een aanvraag-id en correlatie-id zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="e7a16-122">A request ID and correlation ID are required.</span></span>
- <span data-ttu-id="e7a16-123">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e7a16-123">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e7a16-124">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e7a16-124">Request body</span></span>

<span data-ttu-id="e7a16-125">In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="e7a16-125">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="e7a16-126">Naam</span><span class="sxs-lookup"><span data-stu-id="e7a16-126">Name</span></span>                              | <span data-ttu-id="e7a16-127">Type</span><span class="sxs-lookup"><span data-stu-id="e7a16-127">Type</span></span>   | <span data-ttu-id="e7a16-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e7a16-128">Description</span></span>                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="e7a16-129">SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="e7a16-129">SelfServePolicy</span></span>](self-serve-policy-resources.md#selfservepolicy)| <span data-ttu-id="e7a16-130">object</span><span class="sxs-lookup"><span data-stu-id="e7a16-130">object</span></span> | <span data-ttu-id="e7a16-131">De informatie over het self-serve-beleid.</span><span class="sxs-lookup"><span data-stu-id="e7a16-131">The self-serve policy information.</span></span> |

#### <a name="selfservepolicy"></a><span data-ttu-id="e7a16-132">SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="e7a16-132">SelfServePolicy</span></span>

<span data-ttu-id="e7a16-133">In deze tabel worden de minimaal vereiste velden van de [SelfServePolicy-resource](self-serve-policy-resources.md#selfservepolicy) beschreven die nodig zijn om een nieuw selfservicebeleid te maken.</span><span class="sxs-lookup"><span data-stu-id="e7a16-133">This table describes the minimum required fields from the [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource needed to create a new self-serve policy.</span></span>

| <span data-ttu-id="e7a16-134">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="e7a16-134">Property</span></span>              | <span data-ttu-id="e7a16-135">Type</span><span class="sxs-lookup"><span data-stu-id="e7a16-135">Type</span></span>             | <span data-ttu-id="e7a16-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e7a16-136">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e7a16-137">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="e7a16-137">SelfServeEntity</span></span>       | <span data-ttu-id="e7a16-138">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="e7a16-138">SelfServeEntity</span></span>  | <span data-ttu-id="e7a16-139">De zelfhulpentiteit die toegang wordt verleend.</span><span class="sxs-lookup"><span data-stu-id="e7a16-139">The self-serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="e7a16-140">Grantor</span><span class="sxs-lookup"><span data-stu-id="e7a16-140">Grantor</span></span>               | <span data-ttu-id="e7a16-141">Grantor</span><span class="sxs-lookup"><span data-stu-id="e7a16-141">Grantor</span></span>          | <span data-ttu-id="e7a16-142">De grantor die toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="e7a16-142">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="e7a16-143">Machtigingen</span><span class="sxs-lookup"><span data-stu-id="e7a16-143">Permissions</span></span>           | <span data-ttu-id="e7a16-144">Matrix van machtigingen</span><span class="sxs-lookup"><span data-stu-id="e7a16-144">Array of Permission</span></span>| <span data-ttu-id="e7a16-145">Een matrix met [machtigingsbronnen.](self-serve-policy-resources.md#permission)</span><span class="sxs-lookup"><span data-stu-id="e7a16-145">An Array of [Permission](self-serve-policy-resources.md#permission) resources.</span></span>                                                                     |


### <a name="request-example"></a><span data-ttu-id="e7a16-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e7a16-146">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/SelfServePolicy HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 789
Expect: 100-continue
Connection: Keep-Alive

{
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
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="e7a16-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e7a16-147">REST response</span></span>

<span data-ttu-id="e7a16-148">Als dit lukt, retourneert deze API een [SelfServePolicy-resource](self-serve-policy-resources.md#selfservepolicy) voor het nieuwe selfservicebeleid.</span><span class="sxs-lookup"><span data-stu-id="e7a16-148">If successful, this API returns a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource for the new self-serve policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e7a16-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e7a16-149">Response success and error codes</span></span>

<span data-ttu-id="e7a16-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e7a16-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e7a16-151">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e7a16-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e7a16-152">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e7a16-152">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

<span data-ttu-id="e7a16-153">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="e7a16-153">This method returns the following error codes:</span></span>

| <span data-ttu-id="e7a16-154">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="e7a16-154">HTTP Status Code</span></span>     | <span data-ttu-id="e7a16-155">Foutcode</span><span class="sxs-lookup"><span data-stu-id="e7a16-155">Error code</span></span>   | <span data-ttu-id="e7a16-156">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e7a16-156">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="e7a16-157">409</span><span class="sxs-lookup"><span data-stu-id="e7a16-157">409</span></span>                  | <span data-ttu-id="e7a16-158">600041</span><span class="sxs-lookup"><span data-stu-id="e7a16-158">600041</span></span>       | <span data-ttu-id="e7a16-159">Self-serve beleid bestaat al.</span><span class="sxs-lookup"><span data-stu-id="e7a16-159">Self-serve policy already exists.</span></span>                                                     |


### <a name="response-example"></a><span data-ttu-id="e7a16-160">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e7a16-160">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 834
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
Date: Tue, 14 Feb 2017 20:06:02 GMT

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
