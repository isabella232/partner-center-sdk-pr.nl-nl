---
title: Alle analysegegevens van zoeken ophalen
description: Alle informatie over de zoek analyse ophalen.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 967f8d0ed2d276e0f68a047204b64d83dc69da95
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767180"
---
# <a name="get-all-search-analytics-information"></a><span data-ttu-id="4300d-103">Alle analysegegevens van zoeken ophalen</span><span class="sxs-lookup"><span data-stu-id="4300d-103">Get all search analytics information</span></span>

<span data-ttu-id="4300d-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="4300d-104">**Applies To**</span></span>

- <span data-ttu-id="4300d-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="4300d-105">Partner Center</span></span>
- <span data-ttu-id="4300d-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="4300d-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="4300d-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="4300d-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="4300d-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4300d-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="4300d-109">U kunt alle informatie over de zoek analyse voor uw klanten ophalen.</span><span class="sxs-lookup"><span data-stu-id="4300d-109">How to get all the search analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4300d-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4300d-110">Prerequisites</span></span>

- <span data-ttu-id="4300d-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4300d-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4300d-112">Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="4300d-112">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="4300d-113">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4300d-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4300d-114">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4300d-114">Request syntax</span></span>

| <span data-ttu-id="4300d-115">Methode</span><span class="sxs-lookup"><span data-stu-id="4300d-115">Method</span></span>  | <span data-ttu-id="4300d-116">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4300d-116">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="4300d-117">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="4300d-117">**GET**</span></span> | <span data-ttu-id="4300d-118">[*\{ BASEURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/Search http/1.1</span><span class="sxs-lookup"><span data-stu-id="4300d-118">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/search HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="4300d-119">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="4300d-119">URI parameters</span></span>

|    <span data-ttu-id="4300d-120">Parameter</span><span class="sxs-lookup"><span data-stu-id="4300d-120">Parameter</span></span>     |  <span data-ttu-id="4300d-121">Type</span><span class="sxs-lookup"><span data-stu-id="4300d-121">Type</span></span>  |                                                                                                                   <span data-ttu-id="4300d-122">Description</span><span class="sxs-lookup"><span data-stu-id="4300d-122">Description</span></span>                                                                                                                    |
|------------------|--------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|      <span data-ttu-id="4300d-123">filter</span><span class="sxs-lookup"><span data-stu-id="4300d-123">filter</span></span>      | <span data-ttu-id="4300d-124">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4300d-124">string</span></span> |                                                                     <span data-ttu-id="4300d-125">Hiermee worden gegevens geretourneerd die overeenkomen met de filter voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="4300d-125">Returns data matching the filter condition.</span></span> </br> <span data-ttu-id="4300d-126">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="4300d-126">**Example:**</span></span></br> `.../search?filter=field eq 'value'`                                                                     |
|     <span data-ttu-id="4300d-127">GroupBy</span><span class="sxs-lookup"><span data-stu-id="4300d-127">groupby</span></span>      | <span data-ttu-id="4300d-128">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4300d-128">string</span></span> |                                         <span data-ttu-id="4300d-129">Ondersteunt zowel termen als datums.</span><span class="sxs-lookup"><span data-stu-id="4300d-129">Supports both terms and dates.</span></span> <span data-ttu-id="4300d-130">Korte circuit logica om het aantal buckets te beperken.</span><span class="sxs-lookup"><span data-stu-id="4300d-130">Short circuit logic to limit the number of buckets.</span></span> </br> <span data-ttu-id="4300d-131">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="4300d-131">**Example:**</span></span></br> `.../search?groupby=termField1,dateField1,termField2`                                         |
| <span data-ttu-id="4300d-132">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="4300d-132">aggregationLevel</span></span> | <span data-ttu-id="4300d-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4300d-133">string</span></span> | <span data-ttu-id="4300d-134">Voor de para meter *aggregationLevel* is een *GroupBy* vereist.</span><span class="sxs-lookup"><span data-stu-id="4300d-134">The *aggregationLevel* parameter requires a *groupby*.</span></span> <span data-ttu-id="4300d-135">De para meter *aggregationLevel* is van toepassing op alle datum velden die in de *GroupBy* worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="4300d-135">The *aggregationLevel* parameter applies to all date fields present in the *groupby*.</span></span> </br> <span data-ttu-id="4300d-136">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="4300d-136">**Example:**</span></span></br>  `.../search?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
|       <span data-ttu-id="4300d-137">top</span><span class="sxs-lookup"><span data-stu-id="4300d-137">top</span></span>        | <span data-ttu-id="4300d-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4300d-138">string</span></span> |                                                                     <span data-ttu-id="4300d-139">De pagina limiet is 10000.</span><span class="sxs-lookup"><span data-stu-id="4300d-139">The page limit is 10000.</span></span> <span data-ttu-id="4300d-140">Neemt een waarde op die kleiner is dan 10000.</span><span class="sxs-lookup"><span data-stu-id="4300d-140">Takes any value less than 10000.</span></span>  </br> <span data-ttu-id="4300d-141">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="4300d-141">**Example:**</span></span></br>  `.../search?top=100`                                                                     |
|       <span data-ttu-id="4300d-142">skip</span><span class="sxs-lookup"><span data-stu-id="4300d-142">skip</span></span>       | <span data-ttu-id="4300d-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4300d-143">string</span></span> |                                                                                  <span data-ttu-id="4300d-144">Het aantal rijen dat moet worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="4300d-144">Number of rows to skip.</span></span> </br> <span data-ttu-id="4300d-145">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="4300d-145">**Example:**</span></span></br> `.../search?top=100&skip=100`                                                                                   |

### <a name="request-headers"></a><span data-ttu-id="4300d-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4300d-146">Request headers</span></span>

<span data-ttu-id="4300d-147">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4300d-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4300d-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4300d-148">Request body</span></span>

<span data-ttu-id="4300d-149">Geen.</span><span class="sxs-lookup"><span data-stu-id="4300d-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="4300d-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4300d-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/search HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="4300d-151">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4300d-151">REST response</span></span>

<span data-ttu-id="4300d-152">Als dit lukt, bevat de antwoord tekst een verzameling [Zoek](partner-center-analytics-resources.md#search-resource) bronnen.</span><span class="sxs-lookup"><span data-stu-id="4300d-152">If successful, the response body contains a collection of [Search](partner-center-analytics-resources.md#search-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4300d-153">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="4300d-153">Response success and error codes</span></span>

<span data-ttu-id="4300d-154">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="4300d-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4300d-155">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4300d-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4300d-156">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="4300d-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4300d-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="4300d-157">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4300d-158">Zie ook</span><span class="sxs-lookup"><span data-stu-id="4300d-158">See also</span></span>

- [<span data-ttu-id="4300d-159">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="4300d-159">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
