---
title: Een self-serve-beleid verwijderen
description: Zelfhulpbeleid verwijderen.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 063cf98d4c78e82622e486427baeb1a5721715e5
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973091"
---
# <a name="delete-a-selfservepolicy"></a><span data-ttu-id="0b628-103">Een SelfServePolicy verwijderen</span><span class="sxs-lookup"><span data-stu-id="0b628-103">Delete a SelfServePolicy</span></span>

<span data-ttu-id="0b628-104">In dit artikel wordt uitgelegd hoe u een beleid voor self-serve kunt bijwerken.</span><span class="sxs-lookup"><span data-stu-id="0b628-104">This article explains how to update a self-serve policy.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0b628-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0b628-105">Prerequisites</span></span>

- <span data-ttu-id="0b628-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0b628-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0b628-107">In dit scenario wordt verificatie ondersteund met referenties van toepassing en gebruiker.</span><span class="sxs-lookup"><span data-stu-id="0b628-107">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="0b628-108">C\#</span><span class="sxs-lookup"><span data-stu-id="0b628-108">C\#</span></span>

<span data-ttu-id="0b628-109">Een beleid voor self-serve verwijderen:</span><span class="sxs-lookup"><span data-stu-id="0b628-109">To delete a self-serve policy:</span></span>

1. <span data-ttu-id="0b628-110">Roep de [**methode IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) aan met de entiteits-id om een interface op te halen voor bewerkingen op het beleid.</span><span class="sxs-lookup"><span data-stu-id="0b628-110">Call the [**IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

2. <span data-ttu-id="0b628-111">Roep de [**methode Delete**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.delete) of [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.deleteasync) aan om het self-serve-beleid te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="0b628-111">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.deleteasync) method to delete the self-serve policy.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
string policyId;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// deletes the self-serve policies
partnerOperations.SelfServePolicies.ById(policyId).Delete();
```

<span data-ttu-id="0b628-112">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="0b628-112">For an example, see the following:</span></span>

- <span data-ttu-id="0b628-113">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="0b628-113">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="0b628-114">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="0b628-114">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="0b628-115">Klasse: **DeleteSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="0b628-115">Class: **DeleteSelfServePolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="0b628-116">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="0b628-116">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0b628-117">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="0b628-117">Request syntax</span></span>

| <span data-ttu-id="0b628-118">Methode</span><span class="sxs-lookup"><span data-stu-id="0b628-118">Method</span></span>  | <span data-ttu-id="0b628-119">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="0b628-119">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="0b628-120">**Verwijderen**</span><span class="sxs-lookup"><span data-stu-id="0b628-120">**DELETE**</span></span> | <span data-ttu-id="0b628-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0b628-121">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} HTTP/1.1</span></span> |

<span data-ttu-id="0b628-122">**URI-parameter**</span><span class="sxs-lookup"><span data-stu-id="0b628-122">**URI parameter**</span></span>

<span data-ttu-id="0b628-123">Gebruik de volgende padparameters om het opgegeven product op te halen.</span><span class="sxs-lookup"><span data-stu-id="0b628-123">Use the following path parameters to get the specified product.</span></span>

| <span data-ttu-id="0b628-124">Naam</span><span class="sxs-lookup"><span data-stu-id="0b628-124">Name</span></span>                       | <span data-ttu-id="0b628-125">Type</span><span class="sxs-lookup"><span data-stu-id="0b628-125">Type</span></span>         | <span data-ttu-id="0b628-126">Vereist</span><span class="sxs-lookup"><span data-stu-id="0b628-126">Required</span></span> | <span data-ttu-id="0b628-127">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0b628-127">Description</span></span>                                                     |
|----------------------------|--------------|----------|-----------------------------------------------------------------|
| <span data-ttu-id="0b628-128">**SelfServePolicy-id**</span><span class="sxs-lookup"><span data-stu-id="0b628-128">**SelfServePolicy-id**</span></span>     | <span data-ttu-id="0b628-129">**Tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="0b628-129">**string**</span></span>   | <span data-ttu-id="0b628-130">Ja</span><span class="sxs-lookup"><span data-stu-id="0b628-130">Yes</span></span>      | <span data-ttu-id="0b628-131">Een tekenreeks die het self-serve-beleid identificeert.</span><span class="sxs-lookup"><span data-stu-id="0b628-131">A string that identifies the self-serve policy.</span></span>                 |

### <a name="request-headers"></a><span data-ttu-id="0b628-132">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="0b628-132">Request headers</span></span>

- <span data-ttu-id="0b628-133">Een aanvraag-id en correlatie-id zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="0b628-133">A request ID and correlation ID are required.</span></span>
- <span data-ttu-id="0b628-134">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="0b628-134">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0b628-135">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="0b628-135">Request body</span></span>

<span data-ttu-id="0b628-136">Geen.</span><span class="sxs-lookup"><span data-stu-id="0b628-136">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0b628-137">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="0b628-137">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="0b628-138">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="0b628-138">REST response</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0b628-139">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="0b628-139">Response success and error codes</span></span>

<span data-ttu-id="0b628-140">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="0b628-140">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0b628-141">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="0b628-141">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0b628-142">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="0b628-142">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="0b628-143">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="0b628-143">Response example</span></span>

```http
HTTP/1.1 204 deleted
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
Date: Tue, 14 Feb 2017 20:06:02 GMT

```
