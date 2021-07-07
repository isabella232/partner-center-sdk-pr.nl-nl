---
title: Een self-serve-beleid bijwerken
description: Een beleid voor self-serve bijwerken.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d94382e73fd2a79751fe5f8f8414df2befde584f
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445252"
---
# <a name="update-a-selfservepolicy"></a><span data-ttu-id="a2fd9-103">Een SelfServePolicy bijwerken</span><span class="sxs-lookup"><span data-stu-id="a2fd9-103">Update a SelfServePolicy</span></span>

<span data-ttu-id="a2fd9-104">In dit artikel wordt uitgelegd hoe u een beleid voor self-serve kunt bijwerken.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-104">This article explains how to update a self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="a2fd9-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="a2fd9-105">Prerequisites</span></span>

- <span data-ttu-id="a2fd9-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="a2fd9-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="a2fd9-107">In dit scenario wordt verificatie ondersteund met referenties van toepassing en gebruiker.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-107">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="a2fd9-108">C\#</span><span class="sxs-lookup"><span data-stu-id="a2fd9-108">C\#</span></span>

<span data-ttu-id="a2fd9-109">Een beleid voor self-serve verwijderen:</span><span class="sxs-lookup"><span data-stu-id="a2fd9-109">To delete a self-serve policy:</span></span>

1. <span data-ttu-id="a2fd9-110">Roep de [**methode IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) aan met de entiteits-id om een interface op te halen voor bewerkingen op het beleid.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-110">Call the [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

2. <span data-ttu-id="a2fd9-111">Roep de [**methode Put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) of [**PutAsync aan**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) om het self-serve-beleid bij te werken.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-111">Call the [**Put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) or [**PutAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) method to update the self-serve policy.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
SelfServePolicy policy;

// All the operations executed on this partner operation instance will share the same correlation identifier but will differ in request identifier
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// updates the self-serve policies
partnerOperations.SelfServePolicies.ById(policy.id).Put(policy);
```

## <a name="rest-request"></a><span data-ttu-id="a2fd9-112">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="a2fd9-112">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="a2fd9-113">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="a2fd9-113">Request syntax</span></span>

| <span data-ttu-id="a2fd9-114">Methode</span><span class="sxs-lookup"><span data-stu-id="a2fd9-114">Method</span></span>   | <span data-ttu-id="a2fd9-115">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="a2fd9-115">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="a2fd9-116">**PUT**</span><span class="sxs-lookup"><span data-stu-id="a2fd9-116">**PUT**</span></span> | <span data-ttu-id="a2fd9-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="a2fd9-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="a2fd9-118">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="a2fd9-118">Request headers</span></span>

- <span data-ttu-id="a2fd9-119">Een aanvraag-id en correlatie-id zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-119">A request identifier and correlation identifier are required.</span></span>
- <span data-ttu-id="a2fd9-120">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="a2fd9-120">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="a2fd9-121">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="a2fd9-121">Request body</span></span>

<span data-ttu-id="a2fd9-122">In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-122">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="a2fd9-123">Naam</span><span class="sxs-lookup"><span data-stu-id="a2fd9-123">Name</span></span>                              | <span data-ttu-id="a2fd9-124">Type</span><span class="sxs-lookup"><span data-stu-id="a2fd9-124">Type</span></span>   | <span data-ttu-id="a2fd9-125">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a2fd9-125">Description</span></span>                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="a2fd9-126">SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="a2fd9-126">SelfServePolicy</span></span>](self-serve-policy-resources.md#selfservepolicy)| <span data-ttu-id="a2fd9-127">object</span><span class="sxs-lookup"><span data-stu-id="a2fd9-127">object</span></span> | <span data-ttu-id="a2fd9-128">De beleidsinformatie voor self-serve.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-128">The self-serve policy information.</span></span> |

#### <a name="selfservepolicy"></a><span data-ttu-id="a2fd9-129">SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="a2fd9-129">SelfServePolicy</span></span>

<span data-ttu-id="a2fd9-130">In deze tabel worden de minimaal vereiste velden van de [SelfServePolicy-resource](self-serve-policy-resources.md#selfservepolicy) beschreven die nodig zijn om een nieuw beleid voor selfservice te maken.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-130">This table describes the minimum required fields from the [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource needed to create a new self-serve policy.</span></span>

| <span data-ttu-id="a2fd9-131">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="a2fd9-131">Property</span></span>              | <span data-ttu-id="a2fd9-132">Type</span><span class="sxs-lookup"><span data-stu-id="a2fd9-132">Type</span></span>             | <span data-ttu-id="a2fd9-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a2fd9-133">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="a2fd9-134">id</span><span class="sxs-lookup"><span data-stu-id="a2fd9-134">id</span></span>                    | <span data-ttu-id="a2fd9-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a2fd9-135">string</span></span>           | <span data-ttu-id="a2fd9-136">Een self-serve beleids-id die wordt opgegeven wanneer het self-serve-beleid is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-136">A self-serve policy identifier that is supplied upon successful creation of the self-serve policy.</span></span>     |
| <span data-ttu-id="a2fd9-137">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="a2fd9-137">SelfServeEntity</span></span>       | <span data-ttu-id="a2fd9-138">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="a2fd9-138">SelfServeEntity</span></span>  | <span data-ttu-id="a2fd9-139">De zelfhulpentiteit die toegang krijgt.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-139">The self-serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="a2fd9-140">Grantor</span><span class="sxs-lookup"><span data-stu-id="a2fd9-140">Grantor</span></span>               | <span data-ttu-id="a2fd9-141">Grantor</span><span class="sxs-lookup"><span data-stu-id="a2fd9-141">Grantor</span></span>          | <span data-ttu-id="a2fd9-142">De grantor die toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-142">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="a2fd9-143">Machtigingen</span><span class="sxs-lookup"><span data-stu-id="a2fd9-143">Permissions</span></span>           | <span data-ttu-id="a2fd9-144">Matrix van machtigingen</span><span class="sxs-lookup"><span data-stu-id="a2fd9-144">Array of Permission</span></span>| <span data-ttu-id="a2fd9-145">Een matrix met [machtigingsbronnen.](self-serve-policy-resources.md#permission)</span><span class="sxs-lookup"><span data-stu-id="a2fd9-145">An Array of [Permission](self-serve-policy-resources.md#permission) resources.</span></span>                                                      |
| <span data-ttu-id="a2fd9-146">Etag</span><span class="sxs-lookup"><span data-stu-id="a2fd9-146">Etag</span></span>                  | <span data-ttu-id="a2fd9-147">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="a2fd9-147">string</span></span>           | <span data-ttu-id="a2fd9-148">De Etag.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-148">The Etag.</span></span>                                                                                               |


### <a name="request-example"></a><span data-ttu-id="a2fd9-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="a2fd9-149">Request example</span></span>

```http
PUT https://api.partnercenter.microsoft.com/v1/SelfServePolicy HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive

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

## <a name="rest-response"></a><span data-ttu-id="a2fd9-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="a2fd9-150">REST response</span></span>

<span data-ttu-id="a2fd9-151">Als dit lukt, retourneert deze API een [SelfServePolicy-resource](self-serve-policy-resources.md#selfservepolicy) voor het bijgewerkte beleid voor selfservice.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-151">If successful, this API returns a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource for the updated self-serve policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="a2fd9-152">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="a2fd9-152">Response success and error codes</span></span>

<span data-ttu-id="a2fd9-153">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="a2fd9-154">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="a2fd9-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="a2fd9-155">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="a2fd9-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

<span data-ttu-id="a2fd9-156">Deze methode retourneert de volgende foutcodes:</span><span class="sxs-lookup"><span data-stu-id="a2fd9-156">This method returns the following error codes:</span></span>

| <span data-ttu-id="a2fd9-157">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="a2fd9-157">HTTP Status Code</span></span>     | <span data-ttu-id="a2fd9-158">Foutcode</span><span class="sxs-lookup"><span data-stu-id="a2fd9-158">Error code</span></span>   | <span data-ttu-id="a2fd9-159">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="a2fd9-159">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="a2fd9-160">404</span><span class="sxs-lookup"><span data-stu-id="a2fd9-160">404</span></span>                  | <span data-ttu-id="a2fd9-161">600039</span><span class="sxs-lookup"><span data-stu-id="a2fd9-161">600039</span></span>       | <span data-ttu-id="a2fd9-162">Self-serve-beleid is niet gevonden</span><span class="sxs-lookup"><span data-stu-id="a2fd9-162">Self-serve policy was not found</span></span>                                            |
| <span data-ttu-id="a2fd9-163">404</span><span class="sxs-lookup"><span data-stu-id="a2fd9-163">404</span></span>                  | <span data-ttu-id="a2fd9-164">600040</span><span class="sxs-lookup"><span data-stu-id="a2fd9-164">600040</span></span>       | <span data-ttu-id="a2fd9-165">De beleids-id voor self-serve is onjuist</span><span class="sxs-lookup"><span data-stu-id="a2fd9-165">Self-serve policy identifier is incorrect</span></span>                                  |


### <a name="response-example"></a><span data-ttu-id="a2fd9-166">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="a2fd9-166">Response example</span></span>

```http
HTTP/1.1 200 Ok
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
        "etag": "\"1ec98034-a249-46f4-b9dd-9cd464fb5e47\"",
        "objectType": "SelfServePolicy"
    }
}
```
