---
title: Indirecte reseller verwijderen in Sandbox
description: Bevat informatie over het verwijderen van indirecte sandbox-resellers en het inschakelen van end-to-end testen met behulp van API's.
ms.date: 5/24/2021
ms.author: vijvala
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ba1fd002ac62aba4e414d263b33ecc8153054602
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973006"
---
# <a name="delete-indirect-reseller-in-sandbox"></a><span data-ttu-id="2ca79-103">Indirecte reseller verwijderen in Sandbox</span><span class="sxs-lookup"><span data-stu-id="2ca79-103">Delete Indirect Reseller in Sandbox</span></span>

<span data-ttu-id="2ca79-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="2ca79-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="2ca79-105">In dit document ziet u hoe u indirecte Sandbox-providers verwijdert en end-to-end-tests inschakelen met behulp van API's.</span><span class="sxs-lookup"><span data-stu-id="2ca79-105">This document shows how to delete Sandbox Indirect Providers and enable end-to-end testing using APIs.</span></span>

> [!Important]
> <span data-ttu-id="2ca79-106">In dit document worden functies beschreven die alleen zijn toegestaan in de Sandbox-omgeving voor indirecte modelervaringen.</span><span class="sxs-lookup"><span data-stu-id="2ca79-106">This document describes features that are only allowed in the Sandbox environment for Indirect Model experiences.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2ca79-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2ca79-107">Prerequisites</span></span>

- <span data-ttu-id="2ca79-108">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="2ca79-108">Credentials as described in [Partner Center Authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2ca79-109">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="2ca79-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="sandbox-indirect-provider--delete-sandbox-indirect-reseller"></a><span data-ttu-id="2ca79-110">Indirecte sandboxprovider : indirecte sandbox-reseller verwijderen</span><span class="sxs-lookup"><span data-stu-id="2ca79-110">Sandbox Indirect Provider – Delete Sandbox Indirect Reseller</span></span> 

<span data-ttu-id="2ca79-111">Deze functie is alleen beschikbaar in de sandbox en biedt indirecte sandboxproviders de mogelijkheid om indirecte sandbox-resellers te maken.</span><span class="sxs-lookup"><span data-stu-id="2ca79-111">This feature is only available in the Sandbox and gives Sandbox Indirect Providers an ability to create Sandbox Indirect Resellers.</span></span>

1. <span data-ttu-id="2ca79-112">Vereisten voor het verwijderen van een indirecte sandbox-reseller</span><span class="sxs-lookup"><span data-stu-id="2ca79-112">Prerequisites for Deleting a Sandbox Indirect Reseller</span></span>
    1. <span data-ttu-id="2ca79-113">De abonnementen voor elke klant van de indirecte sandbox-reseller opschorten</span><span class="sxs-lookup"><span data-stu-id="2ca79-113">Suspend the subscriptions for each customer of Sandbox Indirect Reseller</span></span>
    2. <span data-ttu-id="2ca79-114">Alle klanten van indirecte resellers verwijderen</span><span class="sxs-lookup"><span data-stu-id="2ca79-114">Delete all customers of Indirect Reseller</span></span>
2. <span data-ttu-id="2ca79-115">Limiet van vijf indirecte sandbox-resellers die zijn toegestaan per indirecte sandboxprovider.</span><span class="sxs-lookup"><span data-stu-id="2ca79-115">Limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider.</span></span> <span data-ttu-id="2ca79-116">Zodra de indirecte sandbox-reseller is verwijderd, wordt het quotum opnieuw ingesteld.</span><span class="sxs-lookup"><span data-stu-id="2ca79-116">Once the Sandbox Indirect reseller is deleted, the quota will be reset.</span></span>

## <a name="delete-sandbox-indirect-reseller-through-api"></a><span data-ttu-id="2ca79-117">Indirecte sandbox-reseller verwijderen via API</span><span class="sxs-lookup"><span data-stu-id="2ca79-117">Delete Sandbox Indirect Reseller through API</span></span>

### <a name="rest-request"></a><span data-ttu-id="2ca79-118">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="2ca79-118">REST request</span></span>

#### <a name="request-syntax"></a><span data-ttu-id="2ca79-119">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="2ca79-119">Request syntax</span></span>

| <span data-ttu-id="2ca79-120">Methode</span><span class="sxs-lookup"><span data-stu-id="2ca79-120">Method</span></span> | <span data-ttu-id="2ca79-121">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="2ca79-121">Request URI</span></span>                                                                             |
|------------|-------------------------------------------------------------------------------------|
| <span data-ttu-id="2ca79-122">**Verwijderen**</span><span class="sxs-lookup"><span data-stu-id="2ca79-122">**DELETE**</span></span> | <span data-ttu-id="2ca79-123">[*{baseURL}*](partner-center-rest-urls.md)/v1 sandboxIndirectReseller/{resellerId}</span><span class="sxs-lookup"><span data-stu-id="2ca79-123">[*{baseURL}*](partner-center-rest-urls.md)/v1//sandboxIndirectReseller/{resellerId}</span></span> |

#### <a name="request-headers"></a><span data-ttu-id="2ca79-124">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="2ca79-124">Request headers</span></span>

- <span data-ttu-id="2ca79-125">Deze API is idempotent (het levert geen ander resultaat op als u deze meerdere keren aanroept)</span><span class="sxs-lookup"><span data-stu-id="2ca79-125">This API is idempotent (it will not yield a different result if you call it multiple times)</span></span>
- <span data-ttu-id="2ca79-126">Een aanvraag-id en correlatie-id zijn vereist</span><span class="sxs-lookup"><span data-stu-id="2ca79-126">A request ID and correlation ID are required</span></span>
- <span data-ttu-id="2ca79-127">Zie REST-headers [Partner Center meer informatie](headers.md)</span><span class="sxs-lookup"><span data-stu-id="2ca79-127">For more information, see [Partner Center REST headers](headers.md)</span></span>

### <a name="request-example"></a><span data-ttu-id="2ca79-128">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2ca79-128">Request Example</span></span>

<span data-ttu-id="2ca79-129">Verwijderen https://api.partnercenter.microsoft.com/v1/sandboxIndirectReseller/{resellerID}</span><span class="sxs-lookup"><span data-stu-id="2ca79-129">DELETE https://api.partnercenter.microsoft.com/v1/sandboxIndirectReseller/{resellerID}</span></span>

```http
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

####  <a name="response-example"></a><span data-ttu-id="2ca79-130">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="2ca79-130">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Feb 2021 00:43:02 GMT
```

#### <a name="response-success-and-error-codes"></a><span data-ttu-id="2ca79-131">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="2ca79-131">Response success and error codes</span></span>

<span data-ttu-id="2ca79-132">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en andere informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="2ca79-132">Each response comes with an HTTP status code that indicates success or failure and other debugging information.</span></span> <span data-ttu-id="2ca79-133">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="2ca79-133">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2ca79-134">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="2ca79-134">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

<span data-ttu-id="2ca79-135">Deze methode retourneert de volgende status en foutcodes:</span><span class="sxs-lookup"><span data-stu-id="2ca79-135">This method returns the following status success and error codes:</span></span>

| <span data-ttu-id="2ca79-136">HTTP-statuscode</span><span class="sxs-lookup"><span data-stu-id="2ca79-136">HTTP Status Code</span></span>                     | <span data-ttu-id="2ca79-137">Foutcode</span><span class="sxs-lookup"><span data-stu-id="2ca79-137">Error code</span></span>     | <span data-ttu-id="2ca79-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2ca79-138">Description</span></span>                                      |
|--------------------------------------|----------------|--------------------------------------------------|
| <span data-ttu-id="2ca79-139">401</span><span class="sxs-lookup"><span data-stu-id="2ca79-139">401</span></span>                                  | <span data-ttu-id="2ca79-140">6002</span><span class="sxs-lookup"><span data-stu-id="2ca79-140">6002</span></span>           | <span data-ttu-id="2ca79-141">Niet-geautoriseerd token of geen tipprovideraccount</span><span class="sxs-lookup"><span data-stu-id="2ca79-141">Unauthorized token or Not a Tip Provider Account</span></span> |
| <span data-ttu-id="2ca79-142">403</span><span class="sxs-lookup"><span data-stu-id="2ca79-142">403</span></span>                                  | <span data-ttu-id="2ca79-143">6003</span><span class="sxs-lookup"><span data-stu-id="2ca79-143">6003</span></span>           | <span data-ttu-id="2ca79-144">Sandbox-IR verwijderen is niet toegestaan</span><span class="sxs-lookup"><span data-stu-id="2ca79-144">Delete Sandbox IR is not allowed</span></span>                 |
| <span data-ttu-id="2ca79-145">403</span><span class="sxs-lookup"><span data-stu-id="2ca79-145">403</span></span>                                  | <span data-ttu-id="2ca79-146">6004</span><span class="sxs-lookup"><span data-stu-id="2ca79-146">6004</span></span>           | <span data-ttu-id="2ca79-147">Een sandbox-IR-bewerking maken die niet is toegestaan</span><span class="sxs-lookup"><span data-stu-id="2ca79-147">Create Sandbox IR operation not allowed</span></span>          |
| <span data-ttu-id="2ca79-148">409</span><span class="sxs-lookup"><span data-stu-id="2ca79-148">409</span></span>                                  | <span data-ttu-id="2ca79-149">1003</span><span class="sxs-lookup"><span data-stu-id="2ca79-149">1003</span></span>           | <span data-ttu-id="2ca79-150">Conflict tijdens het maken van tenant</span><span class="sxs-lookup"><span data-stu-id="2ca79-150">Conflict while creating tenant</span></span>                   |
