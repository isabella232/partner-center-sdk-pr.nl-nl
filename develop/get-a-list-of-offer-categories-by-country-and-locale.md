---
title: Een lijst met categorieën van aanbiedingen per markt ophalen
description: Meer informatie over het ophalen van een verzameling die alle aanbiedingscategorieën in een bepaald land/regio en land/regio voor alle Microsoft Clouds bevat.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: e699355f07dda3941eafed32f5f635d94000abd1
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874275"
---
# <a name="get-a-list-of-offer-categories-by-market"></a><span data-ttu-id="300a6-103">Een lijst met categorieën van aanbiedingen per markt ophalen</span><span class="sxs-lookup"><span data-stu-id="300a6-103">Get a list of offer categories by market</span></span>

<span data-ttu-id="300a6-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="300a6-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="300a6-105">In dit artikel wordt beschreven hoe u een verzameling ophaalt die alle aanbiedingscategorieën in een bepaald land/regio en land/regio bevat.</span><span class="sxs-lookup"><span data-stu-id="300a6-105">This article describes how to get a collection that contains all the offer categories in a given country/region and locale.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="300a6-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="300a6-106">Prerequisites</span></span>

- <span data-ttu-id="300a6-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="300a6-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="300a6-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="300a6-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="300a6-109">C\#</span><span class="sxs-lookup"><span data-stu-id="300a6-109">C\#</span></span>

<span data-ttu-id="300a6-110">Een lijst met aanbiedingscategorieën in een bepaald land/regio en land/regio op te halen:</span><span class="sxs-lookup"><span data-stu-id="300a6-110">To get a list of offer categories in a given country/region and locale:</span></span>

1. <span data-ttu-id="300a6-111">Gebruik de [**verzameling IAggregatePartner.Operations**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) om de [**methode With() aan te**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner.with) roepen voor een bepaalde context.</span><span class="sxs-lookup"><span data-stu-id="300a6-111">Use your [**IAggregatePartner.Operations**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) collection to call the [**With()**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner.with) method on a given context.</span></span>

2. <span data-ttu-id="300a6-112">Inspecteer [**de eigenschap OfferCategories**](/dotnet/api/microsoft.store.partnercenter.ipartner.offercategories) van het resulterende object.</span><span class="sxs-lookup"><span data-stu-id="300a6-112">Inspect the [**OfferCategories**](/dotnet/api/microsoft.store.partnercenter.ipartner.offercategories) property of the resulting object.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

ResourceCollection<OfferCategory> offerCategoryResults = partnerOperations.With(RequestContextFactory.Instance.Create()).OfferCategories.ByCountry("US").Get();
```

<span data-ttu-id="300a6-113">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="300a6-113">For an example, see the following:</span></span>

- <span data-ttu-id="300a6-114">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="300a6-114">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="300a6-115">Project: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="300a6-115">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="300a6-116">Klasse: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="300a6-116">Class: **PartnerSDK.FeatureSample**</span></span>

## <a name="rest-request"></a><span data-ttu-id="300a6-117">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="300a6-117">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="300a6-118">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="300a6-118">Request syntax</span></span>

| <span data-ttu-id="300a6-119">Methode</span><span class="sxs-lookup"><span data-stu-id="300a6-119">Method</span></span>  | <span data-ttu-id="300a6-120">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="300a6-120">Request URI</span></span>                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="300a6-121">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="300a6-121">**GET**</span></span> | <span data-ttu-id="300a6-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/offercategories?country={country-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="300a6-122">[*{baseURL}*](partner-center-rest-urls.md)/v1/offercategories?country={country-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="300a6-123">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="300a6-123">URI parameter</span></span>

<span data-ttu-id="300a6-124">Deze tabel bevat de vereiste queryparameters om de aanbiedingscategorieën op te halen.</span><span class="sxs-lookup"><span data-stu-id="300a6-124">This table lists the required query parameters to get the offer categories.</span></span>

| <span data-ttu-id="300a6-125">Naam</span><span class="sxs-lookup"><span data-stu-id="300a6-125">Name</span></span>           | <span data-ttu-id="300a6-126">Type</span><span class="sxs-lookup"><span data-stu-id="300a6-126">Type</span></span>       | <span data-ttu-id="300a6-127">Vereist</span><span class="sxs-lookup"><span data-stu-id="300a6-127">Required</span></span> | <span data-ttu-id="300a6-128">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="300a6-128">Description</span></span>            |
|----------------|------------|----------|------------------------|
| <span data-ttu-id="300a6-129">**country-id**</span><span class="sxs-lookup"><span data-stu-id="300a6-129">**country-id**</span></span> | <span data-ttu-id="300a6-130">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="300a6-130">**string**</span></span> | <span data-ttu-id="300a6-131">J</span><span class="sxs-lookup"><span data-stu-id="300a6-131">Y</span></span>        | <span data-ttu-id="300a6-132">De land-/regio-id.</span><span class="sxs-lookup"><span data-stu-id="300a6-132">The country/region ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="300a6-133">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="300a6-133">Request headers</span></span>

<span data-ttu-id="300a6-134">Er **is een locale-id** vereist die is opgemaakt als een tekenreeks.</span><span class="sxs-lookup"><span data-stu-id="300a6-134">A **locale-id** formatted as a string is required.</span></span>

<span data-ttu-id="300a6-135">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="300a6-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="300a6-136">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="300a6-136">Request body</span></span>

<span data-ttu-id="300a6-137">Geen.</span><span class="sxs-lookup"><span data-stu-id="300a6-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="300a6-138">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="300a6-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offercategories?country=<country-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fb54bd5-a4c3-4fac-955f-9b6e3436d606
MS-CorrelationId: 47882653-eaed-4a2e-a552-1070a3fa1089
X-Locale: <locale-id>
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="300a6-139">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="300a6-139">REST response</span></span>

<span data-ttu-id="300a6-140">Als dit lukt, retourneert deze methode een verzameling **OfferCategory-resources** in de antwoordbody.</span><span class="sxs-lookup"><span data-stu-id="300a6-140">If successful, this method returns a collection of **OfferCategory** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="300a6-141">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="300a6-141">Response success and error codes</span></span>

<span data-ttu-id="300a6-142">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="300a6-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="300a6-143">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="300a6-143">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="300a6-144">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="300a6-144">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="300a6-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="300a6-145">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1184
Content-Type: application/json
MS-CorrelationId: 47882653-eaed-4a2e-a552-1070a3fa1089
MS-RequestId: 4fb54bd5-a4c3-4fac-955f-9b6e3436d606
Date: Thu, 26 Nov 2015 00:07:10 GMT

{
    "totalCount": 4,
    "items": [{
        "id": "Enterprise_Key",
        "name": "Enterprise",
        "rank": 20,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    {
        "id": "SmallBusiness_Key",
        "name": "SmallBusiness",
        "rank": 30,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    {
        "id": "Government_Key",
        "name": "Government",
        "rank": 40,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    },
    {
        "id": "Internal_Key",
        "name": "Internal",
        "rank": 100,
        "locale": "en-us",
        "country": "US",
        "attributes": {
            "objectType": "OfferCategory"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
