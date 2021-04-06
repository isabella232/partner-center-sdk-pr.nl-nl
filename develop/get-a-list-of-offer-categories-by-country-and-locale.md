---
title: Een lijst met categorieën van aanbiedingen per markt ophalen
description: Meer informatie over het ophalen van een verzameling die alle categorieën van de aanbieding bevat in een bepaald land/regio en land instelling voor alle micro soft-Clouds.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 05aad095c6cb8eaee4cbf7ce976ca1b4b7a408c4
ms.sourcegitcommit: f72173df911aee3ab29b008637190b4d85ffebfe
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/06/2021
ms.locfileid: "106500053"
---
# <a name="get-a-list-of-offer-categories-by-market"></a><span data-ttu-id="55758-103">Een lijst met categorieën van aanbiedingen per markt ophalen</span><span class="sxs-lookup"><span data-stu-id="55758-103">Get a list of offer categories by market</span></span>

<span data-ttu-id="55758-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="55758-104">**Applies to:**</span></span>

- <span data-ttu-id="55758-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="55758-105">Partner Center</span></span>
- <span data-ttu-id="55758-106">Partnercentrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="55758-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="55758-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="55758-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="55758-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="55758-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="55758-109">In dit artikel wordt beschreven hoe u een verzameling kunt ophalen die alle categorieën van de aanbieding bevat in een bepaald land/regio en land instelling.</span><span class="sxs-lookup"><span data-stu-id="55758-109">This article describes how to get a collection that contains all the offer categories in a given country/region and locale.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="55758-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="55758-110">Prerequisites</span></span>

- <span data-ttu-id="55758-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="55758-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="55758-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="55758-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

## <a name="c"></a><span data-ttu-id="55758-113">C\#</span><span class="sxs-lookup"><span data-stu-id="55758-113">C\#</span></span>

<span data-ttu-id="55758-114">Een lijst met aanbiedings categorieën in een bepaald land/regio en land instellingen ophalen:</span><span class="sxs-lookup"><span data-stu-id="55758-114">To get a list of offer categories in a given country/region and locale:</span></span>

1. <span data-ttu-id="55758-115">Gebruik uw [**IAggregatePartner. Operations**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) -verzameling om de methode [**with ()**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner.with) aan te roepen voor een bepaalde context.</span><span class="sxs-lookup"><span data-stu-id="55758-115">Use your [**IAggregatePartner.Operations**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) collection to call the [**With()**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner.with) method on a given context.</span></span>

2. <span data-ttu-id="55758-116">Inspecteer de eigenschap [**OfferCategories**](/dotnet/api/microsoft.store.partnercenter.ipartner.offercategories) van het resulterende object.</span><span class="sxs-lookup"><span data-stu-id="55758-116">Inspect the [**OfferCategories**](/dotnet/api/microsoft.store.partnercenter.ipartner.offercategories) property of the resulting object.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

ResourceCollection<OfferCategory> offerCategoryResults = partnerOperations.With(RequestContextFactory.Instance.Create()).OfferCategories.ByCountry("US").Get();
```

<span data-ttu-id="55758-117">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="55758-117">For an example, see the following:</span></span>

- <span data-ttu-id="55758-118">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="55758-118">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="55758-119">Project: **PartnerSDK. FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="55758-119">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="55758-120">Klasse: **PartnerSDK. FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="55758-120">Class: **PartnerSDK.FeatureSample**</span></span>

## <a name="rest-request"></a><span data-ttu-id="55758-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="55758-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="55758-122">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="55758-122">Request syntax</span></span>

| <span data-ttu-id="55758-123">Methode</span><span class="sxs-lookup"><span data-stu-id="55758-123">Method</span></span>  | <span data-ttu-id="55758-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="55758-124">Request URI</span></span>                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="55758-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="55758-125">**GET**</span></span> | <span data-ttu-id="55758-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/offercategories? land = {land-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="55758-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/offercategories?country={country-id} HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="55758-127">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="55758-127">URI parameter</span></span>

<span data-ttu-id="55758-128">Deze tabel bevat de vereiste query parameters om de aanbiedings Categorieën op te halen.</span><span class="sxs-lookup"><span data-stu-id="55758-128">This table lists the required query parameters to get the offer categories.</span></span>

| <span data-ttu-id="55758-129">Naam</span><span class="sxs-lookup"><span data-stu-id="55758-129">Name</span></span>           | <span data-ttu-id="55758-130">Type</span><span class="sxs-lookup"><span data-stu-id="55758-130">Type</span></span>       | <span data-ttu-id="55758-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="55758-131">Required</span></span> | <span data-ttu-id="55758-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="55758-132">Description</span></span>            |
|----------------|------------|----------|------------------------|
| <span data-ttu-id="55758-133">**land-id**</span><span class="sxs-lookup"><span data-stu-id="55758-133">**country-id**</span></span> | <span data-ttu-id="55758-134">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="55758-134">**string**</span></span> | <span data-ttu-id="55758-135">J</span><span class="sxs-lookup"><span data-stu-id="55758-135">Y</span></span>        | <span data-ttu-id="55758-136">De ID van het land/de regio.</span><span class="sxs-lookup"><span data-stu-id="55758-136">The country/region ID.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="55758-137">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="55758-137">Request headers</span></span>

<span data-ttu-id="55758-138">Een **land instellingen-id** die is opgemaakt als een teken reeks is vereist.</span><span class="sxs-lookup"><span data-stu-id="55758-138">A **locale-id** formatted as a string is required.</span></span>

<span data-ttu-id="55758-139">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="55758-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="55758-140">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="55758-140">Request body</span></span>

<span data-ttu-id="55758-141">Geen.</span><span class="sxs-lookup"><span data-stu-id="55758-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="55758-142">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="55758-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/offercategories?country=<country-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fb54bd5-a4c3-4fac-955f-9b6e3436d606
MS-CorrelationId: 47882653-eaed-4a2e-a552-1070a3fa1089
X-Locale: <locale-id>
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="55758-143">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="55758-143">REST response</span></span>

<span data-ttu-id="55758-144">Als dit lukt, retourneert deze methode een verzameling **OfferCategory** -resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="55758-144">If successful, this method returns a collection of **OfferCategory** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="55758-145">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="55758-145">Response success and error codes</span></span>

<span data-ttu-id="55758-146">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="55758-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="55758-147">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="55758-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="55758-148">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="55758-148">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="55758-149">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="55758-149">Response example</span></span>

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
