---
title: Een beleid voor zelf behoud maken
description: Een nieuw beleid voor zelf behoud maken.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fd1579b2775ead57a440db0d6afb3bf22164c319
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/08/2020
ms.locfileid: "97768653"
---
# <a name="create-a-selfservepolicy"></a><span data-ttu-id="58a9f-103">Een SelfServePolicy maken</span><span class="sxs-lookup"><span data-stu-id="58a9f-103">Create a SelfServePolicy</span></span>

<span data-ttu-id="58a9f-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="58a9f-104">**Applies to:**</span></span>

- <span data-ttu-id="58a9f-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="58a9f-105">Partner Center</span></span>

<span data-ttu-id="58a9f-106">In dit onderwerp wordt uitgelegd hoe u een nieuw beleid voor zelf behoud maakt.</span><span class="sxs-lookup"><span data-stu-id="58a9f-106">This topic explains how to create a new self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="58a9f-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="58a9f-107">Prerequisites</span></span>

- <span data-ttu-id="58a9f-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="58a9f-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="58a9f-109">Dit scenario ondersteunt verificatie met toepassings-en gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="58a9f-109">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="58a9f-110">C\#</span><span class="sxs-lookup"><span data-stu-id="58a9f-110">C\#</span></span>

<span data-ttu-id="58a9f-111">Een beleid voor zelf behoud maken:</span><span class="sxs-lookup"><span data-stu-id="58a9f-111">Create a self-serve policy:</span></span>

1. <span data-ttu-id="58a9f-112">Roep de [**IAggregatePartner. SelfServePolicies. Create**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.create) -of [**IAggregatePartner. SelfServePolicies. CreateAsync**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.createasync) -methode aan met de selfservice-beleids gegevens.</span><span class="sxs-lookup"><span data-stu-id="58a9f-112">Call the [**IAggregatePartner.SelfServePolicies.Create**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.create) or [**IAggregatePartner.SelfServePolicies.CreateAsync**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.createasync) method with the self-serve policy info.</span></span>

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

<span data-ttu-id="58a9f-113">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="58a9f-113">For an example, see the following:</span></span>

- <span data-ttu-id="58a9f-114">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="58a9f-114">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="58a9f-115">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="58a9f-115">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="58a9f-116">Klasse: **CreateSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="58a9f-116">Class: **CreateSelfServePolicies.cs**</span></span>


## <a name="rest-request"></a><span data-ttu-id="58a9f-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="58a9f-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="58a9f-118">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="58a9f-118">Request syntax</span></span>

| <span data-ttu-id="58a9f-119">Methode</span><span class="sxs-lookup"><span data-stu-id="58a9f-119">Method</span></span>   | <span data-ttu-id="58a9f-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="58a9f-120">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="58a9f-121">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="58a9f-121">**POST**</span></span> | <span data-ttu-id="58a9f-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy http/1.1</span><span class="sxs-lookup"><span data-stu-id="58a9f-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="58a9f-123">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="58a9f-123">Request headers</span></span>

- <span data-ttu-id="58a9f-124">Een aanvraag-ID en correlatie-ID zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="58a9f-124">A request ID and correlation ID are required.</span></span>
- <span data-ttu-id="58a9f-125">Zie de [rest headers van het Partner Center](headers.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="58a9f-125">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="58a9f-126">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="58a9f-126">Request body</span></span>

<span data-ttu-id="58a9f-127">In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="58a9f-127">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="58a9f-128">Naam</span><span class="sxs-lookup"><span data-stu-id="58a9f-128">Name</span></span>                              | <span data-ttu-id="58a9f-129">Type</span><span class="sxs-lookup"><span data-stu-id="58a9f-129">Type</span></span>   | <span data-ttu-id="58a9f-130">Description</span><span class="sxs-lookup"><span data-stu-id="58a9f-130">Description</span></span>                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="58a9f-131">SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="58a9f-131">SelfServePolicy</span></span>](self-serve-policy-resources.md#selfservepolicy)| <span data-ttu-id="58a9f-132">object</span><span class="sxs-lookup"><span data-stu-id="58a9f-132">object</span></span> | <span data-ttu-id="58a9f-133">De informatie over zelf-beleids regels.</span><span class="sxs-lookup"><span data-stu-id="58a9f-133">The self-serve policy information.</span></span> |

#### <a name="selfservepolicy"></a><span data-ttu-id="58a9f-134">SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="58a9f-134">SelfServePolicy</span></span>

<span data-ttu-id="58a9f-135">In deze tabel worden de minimale vereiste velden uit de [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) -resource beschreven die nodig zijn voor het maken van een nieuw beleid voor zelf behoud.</span><span class="sxs-lookup"><span data-stu-id="58a9f-135">This table describes the minimum required fields from the [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource needed to create a new self-serve policy.</span></span>

| <span data-ttu-id="58a9f-136">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="58a9f-136">Property</span></span>              | <span data-ttu-id="58a9f-137">Type</span><span class="sxs-lookup"><span data-stu-id="58a9f-137">Type</span></span>             | <span data-ttu-id="58a9f-138">Description</span><span class="sxs-lookup"><span data-stu-id="58a9f-138">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="58a9f-139">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="58a9f-139">SelfServeEntity</span></span>       | <span data-ttu-id="58a9f-140">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="58a9f-140">SelfServeEntity</span></span>  | <span data-ttu-id="58a9f-141">De selfservice-entiteit waarvoor toegang wordt verleend.</span><span class="sxs-lookup"><span data-stu-id="58a9f-141">The self-serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="58a9f-142">Verlener</span><span class="sxs-lookup"><span data-stu-id="58a9f-142">Grantor</span></span>               | <span data-ttu-id="58a9f-143">Verlener</span><span class="sxs-lookup"><span data-stu-id="58a9f-143">Grantor</span></span>          | <span data-ttu-id="58a9f-144">De subsidie die toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="58a9f-144">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="58a9f-145">Machtigingen</span><span class="sxs-lookup"><span data-stu-id="58a9f-145">Permissions</span></span>           | <span data-ttu-id="58a9f-146">Matrix van machtigingen</span><span class="sxs-lookup"><span data-stu-id="58a9f-146">Array of Permission</span></span>| <span data-ttu-id="58a9f-147">Een matrix met [machtigings](self-serve-policy-resources.md#permission) bronnen.</span><span class="sxs-lookup"><span data-stu-id="58a9f-147">An Array of [Permission](self-serve-policy-resources.md#permission) resources.</span></span>                                                                     |


### <a name="request-example"></a><span data-ttu-id="58a9f-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="58a9f-148">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="58a9f-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="58a9f-149">REST response</span></span>

<span data-ttu-id="58a9f-150">Als deze is geslaagd, retourneert deze API een [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) -resource voor het nieuwe beleid voor zelf behoud.</span><span class="sxs-lookup"><span data-stu-id="58a9f-150">If successful, this API returns a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource for the new self-serve policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="58a9f-151">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="58a9f-151">Response success and error codes</span></span>

<span data-ttu-id="58a9f-152">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="58a9f-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="58a9f-153">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="58a9f-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="58a9f-154">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="58a9f-154">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

<span data-ttu-id="58a9f-155">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="58a9f-155">This method returns the following error codes:</span></span>

| <span data-ttu-id="58a9f-156">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="58a9f-156">HTTP Status Code</span></span>     | <span data-ttu-id="58a9f-157">Foutcode</span><span class="sxs-lookup"><span data-stu-id="58a9f-157">Error code</span></span>   | <span data-ttu-id="58a9f-158">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="58a9f-158">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="58a9f-159">409</span><span class="sxs-lookup"><span data-stu-id="58a9f-159">409</span></span>                  | <span data-ttu-id="58a9f-160">600041</span><span class="sxs-lookup"><span data-stu-id="58a9f-160">600041</span></span>       | <span data-ttu-id="58a9f-161">Het beleid voor selfservice beheer bestaat al.</span><span class="sxs-lookup"><span data-stu-id="58a9f-161">Self-serve policy already exists.</span></span>                                                     |


### <a name="response-example"></a><span data-ttu-id="58a9f-162">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="58a9f-162">Response example</span></span>

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
