---
title: Alle analysegegevens van zoeken ophalen
description: Hoe u alle zoekanalysegegevens opzoekt.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e789a013b01fb63a38c72f4fe94864ecf21f7e4b
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760161"
---
# <a name="get-all-search-analytics-information"></a><span data-ttu-id="4ea9d-103">Alle analysegegevens van zoeken ophalen</span><span class="sxs-lookup"><span data-stu-id="4ea9d-103">Get all search analytics information</span></span>

<span data-ttu-id="4ea9d-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4ea9d-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="4ea9d-105">Informatie over het verkrijgen van alle zoekanalysegegevens voor uw klanten.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-105">How to get all the search analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4ea9d-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4ea9d-106">Prerequisites</span></span>

- <span data-ttu-id="4ea9d-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4ea9d-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4ea9d-108">Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="4ea9d-109">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4ea9d-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4ea9d-110">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="4ea9d-110">Request syntax</span></span>

| <span data-ttu-id="4ea9d-111">Methode</span><span class="sxs-lookup"><span data-stu-id="4ea9d-111">Method</span></span>  | <span data-ttu-id="4ea9d-112">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4ea9d-112">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="4ea9d-113">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="4ea9d-113">**GET**</span></span> | <span data-ttu-id="4ea9d-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/search HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4ea9d-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/search HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="4ea9d-115">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="4ea9d-115">URI parameters</span></span>

|    <span data-ttu-id="4ea9d-116">Parameter</span><span class="sxs-lookup"><span data-stu-id="4ea9d-116">Parameter</span></span>     |  <span data-ttu-id="4ea9d-117">Type</span><span class="sxs-lookup"><span data-stu-id="4ea9d-117">Type</span></span>  |                                                                                                                   <span data-ttu-id="4ea9d-118">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4ea9d-118">Description</span></span>                                                                                                                    |
|------------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      <span data-ttu-id="4ea9d-119">filter</span><span class="sxs-lookup"><span data-stu-id="4ea9d-119">filter</span></span>      | <span data-ttu-id="4ea9d-120">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4ea9d-120">string</span></span> |                                                                     <span data-ttu-id="4ea9d-121">Retourneert gegevens die overeenkomen met de filtervoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-121">Returns data matching the filter condition.</span></span> </br> <span data-ttu-id="4ea9d-122">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="4ea9d-122">**Example:**</span></span></br> `.../search?filter=field eq 'value'`                                                                     |
|     <span data-ttu-id="4ea9d-123">groupby</span><span class="sxs-lookup"><span data-stu-id="4ea9d-123">groupby</span></span>      | <span data-ttu-id="4ea9d-124">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4ea9d-124">string</span></span> |                                         <span data-ttu-id="4ea9d-125">Ondersteunt zowel voorwaarden als datums.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-125">Supports both terms and dates.</span></span> <span data-ttu-id="4ea9d-126">Kortcircuitlogica om het aantal buckets te beperken.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-126">Short circuit logic to limit the number of buckets.</span></span> </br> <span data-ttu-id="4ea9d-127">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="4ea9d-127">**Example:**</span></span></br> `.../search?groupby=termField1,dateField1,termField2`                                         |
| <span data-ttu-id="4ea9d-128">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="4ea9d-128">aggregationLevel</span></span> | <span data-ttu-id="4ea9d-129">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4ea9d-129">string</span></span> | <span data-ttu-id="4ea9d-130">De *parameter aggregationLevel* vereist een *groupby*.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-130">The *aggregationLevel* parameter requires a *groupby*.</span></span> <span data-ttu-id="4ea9d-131">De *parameter aggregationLevel* is van toepassing op alle datumvelden die aanwezig zijn in *de groupby*.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-131">The *aggregationLevel* parameter applies to all date fields present in the *groupby*.</span></span> </br> <span data-ttu-id="4ea9d-132">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="4ea9d-132">**Example:**</span></span></br>  `.../search?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
|       <span data-ttu-id="4ea9d-133">top</span><span class="sxs-lookup"><span data-stu-id="4ea9d-133">top</span></span>        | <span data-ttu-id="4ea9d-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4ea9d-134">string</span></span> |                                                                     <span data-ttu-id="4ea9d-135">De paginalimiet is 10000.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-135">The page limit is 10000.</span></span> <span data-ttu-id="4ea9d-136">Neemt een waarde die kleiner is dan 10000.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-136">Takes any value less than 10000.</span></span>  </br> <span data-ttu-id="4ea9d-137">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="4ea9d-137">**Example:**</span></span></br>  `.../search?top=100`                                                                     |
|       <span data-ttu-id="4ea9d-138">skip</span><span class="sxs-lookup"><span data-stu-id="4ea9d-138">skip</span></span>       | <span data-ttu-id="4ea9d-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4ea9d-139">string</span></span> |                                                                                  <span data-ttu-id="4ea9d-140">Aantal rijen dat moet worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-140">Number of rows to skip.</span></span> </br> <span data-ttu-id="4ea9d-141">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="4ea9d-141">**Example:**</span></span></br> `.../search?top=100&skip=100`                                                                                   |

### <a name="request-headers"></a><span data-ttu-id="4ea9d-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4ea9d-142">Request headers</span></span>

<span data-ttu-id="4ea9d-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="4ea9d-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4ea9d-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4ea9d-144">Request body</span></span>

<span data-ttu-id="4ea9d-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="4ea9d-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4ea9d-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/search HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="4ea9d-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4ea9d-147">REST response</span></span>

<span data-ttu-id="4ea9d-148">Als dit lukt, bevat de antwoord-body een verzameling [zoekresources.](partner-center-analytics-resources.md#search-resource)</span><span class="sxs-lookup"><span data-stu-id="4ea9d-148">If successful, the response body contains a collection of [Search](partner-center-analytics-resources.md#search-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4ea9d-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="4ea9d-149">Response success and error codes</span></span>

<span data-ttu-id="4ea9d-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4ea9d-151">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4ea9d-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4ea9d-152">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="4ea9d-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4ea9d-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="4ea9d-153">Response example</span></span>

```http
{
  "companyName": "my company",
  "contactButtonClicked": false,
  "keywordCountry": null,
  "detailsViewed": true,
  "keywordIndustryFocus": null,
  "mpnId": 2604568,
  "partnerMarket": "CN",
  "keywordProduct": null,
  "referralSubmitted": false,
  "searchDate": "2018-05-30",
  "keywordSearchText": " my company"
}
```

## <a name="see-also"></a><span data-ttu-id="4ea9d-154">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4ea9d-154">See also</span></span>

- [<span data-ttu-id="4ea9d-155">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="4ea9d-155">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
