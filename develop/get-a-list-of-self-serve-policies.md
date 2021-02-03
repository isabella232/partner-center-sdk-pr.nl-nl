---
title: Een lijst met selfservice beleid ophalen
description: Informatie over het ophalen van een verzameling resources die het zelf-onderhanden beleid van een klant vertegenwoordigen.
ms.date: 07/06/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: ff3116b8757e28e03615930ebd19bc75f34e2efe
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/08/2020
ms.locfileid: "97768665"
---
# <a name="get-a-list-of-self-serve-policies"></a><span data-ttu-id="29a55-103">Een lijst met selfservice beleid ophalen</span><span class="sxs-lookup"><span data-stu-id="29a55-103">Get a list of self-serve policies</span></span>

<span data-ttu-id="29a55-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="29a55-104">**Applies to:**</span></span>

- <span data-ttu-id="29a55-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="29a55-105">Partner Center</span></span>

<span data-ttu-id="29a55-106">In dit artikel wordt beschreven hoe u een verzameling resources kunt ophalen die het beleid voor de selfservice voor een entiteit vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="29a55-106">This article describes how to get a collection of resources that represents self-serve policies for an entity.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="29a55-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="29a55-107">Prerequisites</span></span>

- <span data-ttu-id="29a55-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="29a55-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="29a55-109">Dit scenario ondersteunt verificatie met toepassings-en gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="29a55-109">This scenario supports authentication with Application+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="29a55-110">C\#</span><span class="sxs-lookup"><span data-stu-id="29a55-110">C\#</span></span>

<span data-ttu-id="29a55-111">Een lijst met alle selfservice beleid ophalen:</span><span class="sxs-lookup"><span data-stu-id="29a55-111">To get a list of all self-serve policies:</span></span>

1. <span data-ttu-id="29a55-112">Roep de methode [**IAggregatePartner. SelfServePolicies**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection) aan met de entiteit-id om een interface op te halen voor bewerkingen in het beleid.</span><span class="sxs-lookup"><span data-stu-id="29a55-112">Call the [**IAggregatePartner.SelfServePolicies**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection) method with the entity identifier to retrieve an interface to operations on the policies.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// gets the self-serve policies
var SelfServePolicies = scopedPartnerOperations.SelfServePolicies.Get(customerIdAsEntity);
```

<span data-ttu-id="29a55-113">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="29a55-113">For an example, see the following:</span></span>

- <span data-ttu-id="29a55-114">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="29a55-114">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="29a55-115">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="29a55-115">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="29a55-116">Klasse: **GetSelfServePolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="29a55-116">Class: **GetSelfServePolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="29a55-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="29a55-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="29a55-118">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="29a55-118">Request syntax</span></span>

| <span data-ttu-id="29a55-119">Methode</span><span class="sxs-lookup"><span data-stu-id="29a55-119">Method</span></span>  | <span data-ttu-id="29a55-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="29a55-120">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="29a55-121">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="29a55-121">**GET**</span></span> | <span data-ttu-id="29a55-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy? entity_id = {ENTITY_ID} http/1.1</span><span class="sxs-lookup"><span data-stu-id="29a55-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy?entity_id={entity_id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="29a55-123">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="29a55-123">URI parameter</span></span>

<span data-ttu-id="29a55-124">Gebruik de volgende query parameter om een lijst met klanten op te halen.</span><span class="sxs-lookup"><span data-stu-id="29a55-124">Use the following query parameter to get a list of customers.</span></span>

| <span data-ttu-id="29a55-125">Naam</span><span class="sxs-lookup"><span data-stu-id="29a55-125">Name</span></span>          | <span data-ttu-id="29a55-126">Type</span><span class="sxs-lookup"><span data-stu-id="29a55-126">Type</span></span>       | <span data-ttu-id="29a55-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="29a55-127">Required</span></span> | <span data-ttu-id="29a55-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="29a55-128">Description</span></span>                                        |
|---------------|------------|----------|----------------------------------------------------|
| <span data-ttu-id="29a55-129">**entity_id**</span><span class="sxs-lookup"><span data-stu-id="29a55-129">**entity_id**</span></span> | <span data-ttu-id="29a55-130">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="29a55-130">**string**</span></span> | <span data-ttu-id="29a55-131">J</span><span class="sxs-lookup"><span data-stu-id="29a55-131">Y</span></span>        | <span data-ttu-id="29a55-132">De entiteits-id die toegang vraagt voor.</span><span class="sxs-lookup"><span data-stu-id="29a55-132">The entity identifier requesting access for.</span></span> <span data-ttu-id="29a55-133">Dit is de Tenant-ID van de klant.</span><span class="sxs-lookup"><span data-stu-id="29a55-133">This will be the customer's tenant ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="29a55-134">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="29a55-134">Request headers</span></span>

<span data-ttu-id="29a55-135">Zie [kopteksten](headers.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="29a55-135">For more information, see [Headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="29a55-136">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="29a55-136">Request body</span></span>

<span data-ttu-id="29a55-137">Geen.</span><span class="sxs-lookup"><span data-stu-id="29a55-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="29a55-138">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="29a55-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/SelfServePolicy?entity_id=0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 3705fc6d-4127-4a87-bdba-9658f73fe019
MS-CorrelationId: b12260fb-82de-4701-a25f-dcd367690645
```

## <a name="rest-response"></a><span data-ttu-id="29a55-139">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="29a55-139">REST response</span></span>

<span data-ttu-id="29a55-140">Als dit lukt, retourneert deze methode een verzameling [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) -resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="29a55-140">If successful, this method returns a collection of [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="29a55-141">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="29a55-141">Response success and error codes</span></span>

<span data-ttu-id="29a55-142">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="29a55-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="29a55-143">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="29a55-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="29a55-144">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="29a55-144">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="29a55-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="29a55-145">Response example</span></span>

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
