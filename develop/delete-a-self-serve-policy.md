---
title: Een beleid voor zelf behoud verwijderen
description: Een selfservice beleid verwijderen.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 3450145d6daf2ffca5e2886245e592406cb0886d
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/08/2020
ms.locfileid: "97768657"
---
# <a name="delete-a-selfservepolicy"></a><span data-ttu-id="f7054-103">Een SelfServePolicy verwijderen</span><span class="sxs-lookup"><span data-stu-id="f7054-103">Delete a SelfServePolicy</span></span>

<span data-ttu-id="f7054-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="f7054-104">**Applies to:**</span></span>

- <span data-ttu-id="f7054-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="f7054-105">Partner Center</span></span>

<span data-ttu-id="f7054-106">In dit onderwerp wordt uitgelegd hoe u een beleid voor zelf behoud bijwerkt.</span><span class="sxs-lookup"><span data-stu-id="f7054-106">This topic explains how to update a self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f7054-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="f7054-107">Prerequisites</span></span>

- <span data-ttu-id="f7054-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="f7054-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="f7054-109">Dit scenario ondersteunt verificatie met toepassings-en gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="f7054-109">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="f7054-110">C\#</span><span class="sxs-lookup"><span data-stu-id="f7054-110">C\#</span></span>

<span data-ttu-id="f7054-111">Een beleid voor zelf behoud verwijderen:</span><span class="sxs-lookup"><span data-stu-id="f7054-111">To delete a self-serve policy:</span></span>

1. <span data-ttu-id="f7054-112">Roep de [**IAggregatePartner. SelfServePolicies. ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) -methode aan met de entiteit-id om een interface op te halen voor bewerkingen op het beleid.</span><span class="sxs-lookup"><span data-stu-id="f7054-112">Call the [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

2. <span data-ttu-id="f7054-113">Roep de methode [**Delete**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.delete) of [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.deleteasync) aan om het beleid voor zelf behoud te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="f7054-113">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.deleteasync) method to delete the self-serve policy.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
string policyId;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// deletes the self-serve policies
partnerOperations.SelfServePolicies.ById(policyId).Delete();
```

<span data-ttu-id="f7054-114">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="f7054-114">For an example, see the following:</span></span>

- <span data-ttu-id="f7054-115">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="f7054-115">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="f7054-116">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="f7054-116">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="f7054-117">Klasse: **DeleteSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="f7054-117">Class: **DeleteSelfServePolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="f7054-118">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="f7054-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="f7054-119">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f7054-119">Request syntax</span></span>

| <span data-ttu-id="f7054-120">Methode</span><span class="sxs-lookup"><span data-stu-id="f7054-120">Method</span></span>  | <span data-ttu-id="f7054-121">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="f7054-121">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="f7054-122">**VERWIJDERD**</span><span class="sxs-lookup"><span data-stu-id="f7054-122">**DELETE**</span></span> | <span data-ttu-id="f7054-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="f7054-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span></span> |

<span data-ttu-id="f7054-124">**URI-para meter**</span><span class="sxs-lookup"><span data-stu-id="f7054-124">**URI parameter**</span></span>

<span data-ttu-id="f7054-125">Gebruik de volgende Path-para meters om het opgegeven product op te halen.</span><span class="sxs-lookup"><span data-stu-id="f7054-125">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="f7054-126">Naam</span><span class="sxs-lookup"><span data-stu-id="f7054-126">Name</span></span>                       | <span data-ttu-id="f7054-127">Type</span><span class="sxs-lookup"><span data-stu-id="f7054-127">Type</span></span>         | <span data-ttu-id="f7054-128">Vereist</span><span class="sxs-lookup"><span data-stu-id="f7054-128">Required</span></span> | <span data-ttu-id="f7054-129">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="f7054-129">Description</span></span>                                                     |
|----------------------------|--------------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="f7054-130">**SelfServePolicy-id**</span><span class="sxs-lookup"><span data-stu-id="f7054-130">**SelfServePolicy-id**</span></span>     | <span data-ttu-id="f7054-131">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="f7054-131">**string**</span></span>   | <span data-ttu-id="f7054-132">Yes</span><span class="sxs-lookup"><span data-stu-id="f7054-132">Yes</span></span>      | <span data-ttu-id="f7054-133">Een teken reeks die het selfservice beleid identificeert.</span><span class="sxs-lookup"><span data-stu-id="f7054-133">A string that identifies the self-serve policy.</span></span>                 |

### <a name="request-headers"></a><span data-ttu-id="f7054-134">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="f7054-134">Request headers</span></span>

- <span data-ttu-id="f7054-135">Een aanvraag-ID en correlatie-ID zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="f7054-135">A request ID and correlation ID are required.</span></span>
- <span data-ttu-id="f7054-136">Zie de [rest headers van het Partner Center](headers.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="f7054-136">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="f7054-137">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="f7054-137">Request body</span></span>

<span data-ttu-id="f7054-138">Geen.</span><span class="sxs-lookup"><span data-stu-id="f7054-138">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="f7054-139">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="f7054-139">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/SelfServePolicy/634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 789
Connection: Keep-Alive

```

## <a name="rest-response"></a><span data-ttu-id="f7054-140">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="f7054-140">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="f7054-141">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="f7054-141">Response success and error codes</span></span>

<span data-ttu-id="f7054-142">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="f7054-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="f7054-143">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="f7054-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="f7054-144">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="f7054-144">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="f7054-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="f7054-145">Response example</span></span>

```http
HTTP/1.1 204 deleted
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
Date: Tue, 14 Feb 2017 20:06:02 GMT

```
