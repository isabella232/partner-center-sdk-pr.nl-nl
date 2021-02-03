---
title: Een selfservice beleid bijwerken
description: Een selfservice beleid bijwerken.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4d53ab8e5b8ef5b7be83360a3f43ec7791b2e3b4
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/08/2020
ms.locfileid: "97768669"
---
# <a name="update-a-selfservepolicy"></a><span data-ttu-id="bd83c-103">Een SelfServePolicy bijwerken</span><span class="sxs-lookup"><span data-stu-id="bd83c-103">Update a SelfServePolicy</span></span>

<span data-ttu-id="bd83c-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="bd83c-104">**Applies to:**</span></span>

- <span data-ttu-id="bd83c-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="bd83c-105">Partner Center</span></span>

<span data-ttu-id="bd83c-106">In dit onderwerp wordt uitgelegd hoe u een beleid voor zelf behoud bijwerkt.</span><span class="sxs-lookup"><span data-stu-id="bd83c-106">This topic explains how to update a self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd83c-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bd83c-107">Prerequisites</span></span>

- <span data-ttu-id="bd83c-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bd83c-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bd83c-109">Dit scenario ondersteunt verificatie met toepassings-en gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="bd83c-109">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="bd83c-110">C\#</span><span class="sxs-lookup"><span data-stu-id="bd83c-110">C\#</span></span>

<span data-ttu-id="bd83c-111">Een beleid voor zelf behoud verwijderen:</span><span class="sxs-lookup"><span data-stu-id="bd83c-111">To delete a self-serve policy:</span></span>

1. <span data-ttu-id="bd83c-112">Roep de [**IAggregatePartner. SelfServePolicies. ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) -methode aan met de entiteit-id om een interface op te halen voor bewerkingen op het beleid.</span><span class="sxs-lookup"><span data-stu-id="bd83c-112">Call the [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

2. <span data-ttu-id="bd83c-113">Roep de [**put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) -of [**PutAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) -methode aan om het beleid voor eigen beheer bij te werken.</span><span class="sxs-lookup"><span data-stu-id="bd83c-113">Call the [**Put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) or [**PutAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) method to update the self-serve policy.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
SelfServePolicy policy;

// All the operations executed on this partner operation instance will share the same correlation identifier but will differ in request identifier
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// updates the self-serve policies
partnerOperations.SelfServePolicies.ById(policy.id).Put(policy);
```

## <a name="rest-request"></a><span data-ttu-id="bd83c-114">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="bd83c-114">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bd83c-115">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bd83c-115">Request syntax</span></span>

| <span data-ttu-id="bd83c-116">Methode</span><span class="sxs-lookup"><span data-stu-id="bd83c-116">Method</span></span>   | <span data-ttu-id="bd83c-117">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="bd83c-117">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="bd83c-118">**PUT**</span><span class="sxs-lookup"><span data-stu-id="bd83c-118">**PUT**</span></span> | <span data-ttu-id="bd83c-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy http/1.1</span><span class="sxs-lookup"><span data-stu-id="bd83c-119">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="bd83c-120">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="bd83c-120">Request headers</span></span>

- <span data-ttu-id="bd83c-121">Een aanvraag-id en correlatie-id zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="bd83c-121">A request identifier and correlation identifier are required.</span></span>
- <span data-ttu-id="bd83c-122">Zie de [rest headers van het Partner Center](headers.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bd83c-122">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="bd83c-123">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="bd83c-123">Request body</span></span>

<span data-ttu-id="bd83c-124">In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="bd83c-124">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="bd83c-125">Naam</span><span class="sxs-lookup"><span data-stu-id="bd83c-125">Name</span></span>                              | <span data-ttu-id="bd83c-126">Type</span><span class="sxs-lookup"><span data-stu-id="bd83c-126">Type</span></span>   | <span data-ttu-id="bd83c-127">Description</span><span class="sxs-lookup"><span data-stu-id="bd83c-127">Description</span></span>                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="bd83c-128">SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="bd83c-128">SelfServePolicy</span></span>](self-serve-policy-resources.md#selfservepolicy)| <span data-ttu-id="bd83c-129">object</span><span class="sxs-lookup"><span data-stu-id="bd83c-129">object</span></span> | <span data-ttu-id="bd83c-130">De informatie over zelf-beleids regels.</span><span class="sxs-lookup"><span data-stu-id="bd83c-130">The self-serve policy information.</span></span> |

#### <a name="selfservepolicy"></a><span data-ttu-id="bd83c-131">SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="bd83c-131">SelfServePolicy</span></span>

<span data-ttu-id="bd83c-132">In deze tabel worden de minimale vereiste velden uit de [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) -resource beschreven die nodig zijn voor het maken van een nieuw beleid voor zelf behoud.</span><span class="sxs-lookup"><span data-stu-id="bd83c-132">This table describes the minimum required fields from the [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource needed to create a new self-serve policy.</span></span>

| <span data-ttu-id="bd83c-133">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="bd83c-133">Property</span></span>              | <span data-ttu-id="bd83c-134">Type</span><span class="sxs-lookup"><span data-stu-id="bd83c-134">Type</span></span>             | <span data-ttu-id="bd83c-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bd83c-135">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bd83c-136">id</span><span class="sxs-lookup"><span data-stu-id="bd83c-136">id</span></span>                    | <span data-ttu-id="bd83c-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bd83c-137">string</span></span>           | <span data-ttu-id="bd83c-138">Een selfservice beleids-id die wordt geleverd bij het maken van het selfservice beleid.</span><span class="sxs-lookup"><span data-stu-id="bd83c-138">A self-serve policy identifier that is supplied upon successful creation of the self-serve policy.</span></span>     |
| <span data-ttu-id="bd83c-139">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="bd83c-139">SelfServeEntity</span></span>       | <span data-ttu-id="bd83c-140">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="bd83c-140">SelfServeEntity</span></span>  | <span data-ttu-id="bd83c-141">De selfservice-entiteit waarvoor toegang wordt verleend.</span><span class="sxs-lookup"><span data-stu-id="bd83c-141">The self-serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="bd83c-142">Verlener</span><span class="sxs-lookup"><span data-stu-id="bd83c-142">Grantor</span></span>               | <span data-ttu-id="bd83c-143">Verlener</span><span class="sxs-lookup"><span data-stu-id="bd83c-143">Grantor</span></span>          | <span data-ttu-id="bd83c-144">De subsidie die toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="bd83c-144">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="bd83c-145">Machtigingen</span><span class="sxs-lookup"><span data-stu-id="bd83c-145">Permissions</span></span>           | <span data-ttu-id="bd83c-146">Matrix van machtigingen</span><span class="sxs-lookup"><span data-stu-id="bd83c-146">Array of Permission</span></span>| <span data-ttu-id="bd83c-147">Een matrix met [machtigings](self-serve-policy-resources.md#permission) bronnen.</span><span class="sxs-lookup"><span data-stu-id="bd83c-147">An Array of [Permission](self-serve-policy-resources.md#permission) resources.</span></span>                                                      |
| <span data-ttu-id="bd83c-148">ETAG</span><span class="sxs-lookup"><span data-stu-id="bd83c-148">Etag</span></span>                  | <span data-ttu-id="bd83c-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bd83c-149">string</span></span>           | <span data-ttu-id="bd83c-150">De ETag.</span><span class="sxs-lookup"><span data-stu-id="bd83c-150">The Etag.</span></span>                                                                                               |


### <a name="request-example"></a><span data-ttu-id="bd83c-151">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bd83c-151">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="bd83c-152">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="bd83c-152">REST response</span></span>

<span data-ttu-id="bd83c-153">Als deze is geslaagd, retourneert deze API een [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) -resource voor het bijgewerkte beleid voor zelf behoud.</span><span class="sxs-lookup"><span data-stu-id="bd83c-153">If successful, this API returns a [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resource for the updated self-serve policy.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bd83c-154">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="bd83c-154">Response success and error codes</span></span>

<span data-ttu-id="bd83c-155">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="bd83c-155">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bd83c-156">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="bd83c-156">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bd83c-157">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="bd83c-157">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

<span data-ttu-id="bd83c-158">Deze methode retourneert de volgende fout codes:</span><span class="sxs-lookup"><span data-stu-id="bd83c-158">This method returns the following error codes:</span></span>

| <span data-ttu-id="bd83c-159">HTTP-status code</span><span class="sxs-lookup"><span data-stu-id="bd83c-159">HTTP Status Code</span></span>     | <span data-ttu-id="bd83c-160">Foutcode</span><span class="sxs-lookup"><span data-stu-id="bd83c-160">Error code</span></span>   | <span data-ttu-id="bd83c-161">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bd83c-161">Description</span></span>                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| <span data-ttu-id="bd83c-162">404</span><span class="sxs-lookup"><span data-stu-id="bd83c-162">404</span></span>                  | <span data-ttu-id="bd83c-163">600039</span><span class="sxs-lookup"><span data-stu-id="bd83c-163">600039</span></span>       | <span data-ttu-id="bd83c-164">Het beleid voor selfservice beheer is niet gevonden</span><span class="sxs-lookup"><span data-stu-id="bd83c-164">Self-serve policy was not found</span></span>                                            |
| <span data-ttu-id="bd83c-165">404</span><span class="sxs-lookup"><span data-stu-id="bd83c-165">404</span></span>                  | <span data-ttu-id="bd83c-166">600040</span><span class="sxs-lookup"><span data-stu-id="bd83c-166">600040</span></span>       | <span data-ttu-id="bd83c-167">De beleids-id zelf behouden is onjuist</span><span class="sxs-lookup"><span data-stu-id="bd83c-167">Self-serve policy identifier is incorrect</span></span>                                  |


### <a name="response-example"></a><span data-ttu-id="bd83c-168">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="bd83c-168">Response example</span></span>

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
