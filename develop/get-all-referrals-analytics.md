---
title: Alle analysegegevens van verwijzingen ophalen
description: Informatie over verwijzingsanalyses verkrijgen.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: Kim-Davis
ms.author: kimnich
ms.openlocfilehash: 7deda4098ceb9eb4e1ee75056c53c754618bf3e2
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760603"
---
# <a name="get-all-referrals-analytics-information"></a><span data-ttu-id="bd53a-103">Alle analysegegevens van verwijzingen ophalen</span><span class="sxs-lookup"><span data-stu-id="bd53a-103">Get all referrals analytics information</span></span>

<span data-ttu-id="bd53a-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="bd53a-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="bd53a-105">Informatie over verwijzingsanalyses voor uw klanten verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="bd53a-105">How to get all the referrals analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd53a-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bd53a-106">Prerequisites</span></span>

- <span data-ttu-id="bd53a-107">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="bd53a-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bd53a-108">Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="bd53a-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="bd53a-109">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="bd53a-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bd53a-110">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="bd53a-110">Request syntax</span></span>

| <span data-ttu-id="bd53a-111">Methode</span><span class="sxs-lookup"><span data-stu-id="bd53a-111">Method</span></span>  | <span data-ttu-id="bd53a-112">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="bd53a-112">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="bd53a-113">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="bd53a-113">**GET**</span></span> | <span data-ttu-id="bd53a-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/referrals HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="bd53a-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/referrals HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="bd53a-115">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="bd53a-115">URI parameters</span></span>

| <span data-ttu-id="bd53a-116">Parameter</span><span class="sxs-lookup"><span data-stu-id="bd53a-116">Parameter</span></span> | <span data-ttu-id="bd53a-117">Type</span><span class="sxs-lookup"><span data-stu-id="bd53a-117">Type</span></span> | <span data-ttu-id="bd53a-118">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bd53a-118">Description</span></span> |
|-----------|------|-------------|
| <span data-ttu-id="bd53a-119">filter</span><span class="sxs-lookup"><span data-stu-id="bd53a-119">filter</span></span> | <span data-ttu-id="bd53a-120">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bd53a-120">string</span></span> | <span data-ttu-id="bd53a-121">Retourneert gegevens die overeenkomen met de filtervoorwaarde.</span><span class="sxs-lookup"><span data-stu-id="bd53a-121">Returns data matching the filter condition.</span></span></br> <span data-ttu-id="bd53a-122">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="bd53a-122">**Example:**</span></span></br>  `.../referrals?filter=field eq 'value'` |
| <span data-ttu-id="bd53a-123">groupby</span><span class="sxs-lookup"><span data-stu-id="bd53a-123">groupby</span></span> | <span data-ttu-id="bd53a-124">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bd53a-124">string</span></span> | <span data-ttu-id="bd53a-125">Ondersteunt zowel voorwaarden als datums.</span><span class="sxs-lookup"><span data-stu-id="bd53a-125">Supports both terms and dates.</span></span> <span data-ttu-id="bd53a-126">Kortcircuitlogica om het aantal buckets te beperken.</span><span class="sxs-lookup"><span data-stu-id="bd53a-126">Short circuit logic to limit the number of buckets.</span></span></br> <span data-ttu-id="bd53a-127">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="bd53a-127">**Example:**</span></span></br>  `.../referrals?groupby=termField1,dateField1,termField2` |
| <span data-ttu-id="bd53a-128">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="bd53a-128">aggregationLevel</span></span> | <span data-ttu-id="bd53a-129">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bd53a-129">string</span></span> | <span data-ttu-id="bd53a-130">De *parameter aggregationLevel* vereist een *groupby*.</span><span class="sxs-lookup"><span data-stu-id="bd53a-130">The *aggregationLevel* parameter requires a *groupby*.</span></span> <span data-ttu-id="bd53a-131">De *parameter aggregationLevel* is van toepassing op alle datumvelden die aanwezig zijn in *de groupby*.</span><span class="sxs-lookup"><span data-stu-id="bd53a-131">The *aggregationLevel* parameter applies to all date fields present in the *groupby*.</span></span></br> <span data-ttu-id="bd53a-132">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="bd53a-132">**Example:**</span></span></br> `.../referrals?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
| <span data-ttu-id="bd53a-133">top</span><span class="sxs-lookup"><span data-stu-id="bd53a-133">top</span></span> | <span data-ttu-id="bd53a-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bd53a-134">string</span></span> | <span data-ttu-id="bd53a-135">De paginalimiet is 10000.</span><span class="sxs-lookup"><span data-stu-id="bd53a-135">The page limit is 10000.</span></span> <span data-ttu-id="bd53a-136">Neemt een waarde die kleiner is dan 10000.</span><span class="sxs-lookup"><span data-stu-id="bd53a-136">Takes any value less than 10000.</span></span></br> <span data-ttu-id="bd53a-137">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="bd53a-137">**Example:**</span></span></br> `.../referrals?top=100`</br> |
| <span data-ttu-id="bd53a-138">skip</span><span class="sxs-lookup"><span data-stu-id="bd53a-138">skip</span></span> | <span data-ttu-id="bd53a-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="bd53a-139">string</span></span> | <span data-ttu-id="bd53a-140">Aantal rijen dat moet worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="bd53a-140">Number of rows to skip.</span></span></br> <span data-ttu-id="bd53a-141">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="bd53a-141">**Example:**</span></span></br>  `.../referrals?top=100&skip=100` |

### <a name="request-headers"></a><span data-ttu-id="bd53a-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="bd53a-142">Request headers</span></span>

<span data-ttu-id="bd53a-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="bd53a-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="bd53a-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="bd53a-144">Request body</span></span>

<span data-ttu-id="bd53a-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="bd53a-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="bd53a-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bd53a-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/referrals HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="bd53a-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="bd53a-147">REST response</span></span>

<span data-ttu-id="bd53a-148">Als dit lukt, bevat de antwoord-body een verzameling [verwijzingenresources.](partner-center-analytics-resources.md#referrals-resource)</span><span class="sxs-lookup"><span data-stu-id="bd53a-148">If successful, the response body contains a collection of [Referrals](partner-center-analytics-resources.md#referrals-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bd53a-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="bd53a-149">Response success and error codes</span></span>

<span data-ttu-id="bd53a-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="bd53a-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bd53a-151">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="bd53a-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bd53a-152">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="bd53a-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="bd53a-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="bd53a-153">Response example</span></span>

```http
{
  "id": "112310",
  "status": "Accepted",
  "customerMarket": "US",
  "customerName": "Best Customer Ever",
  "customerOrgSize": "10to50employees",
  "acceptedDate": "2018-02-07T23:43:19",
  "acknowledgedDate": "2018-02-07T23:40:50",
  "archivedDate": null,
  "declinedDate": null,
  "expiredDate": null,
  "lostDate": null,
  "missedDate": null,
  "createdDate": "2018-02-04T23:08:59",
  "skippedDate": null,
  "wonDate": null,
  "partnerMarket": "US"
}
```

## <a name="see-also"></a><span data-ttu-id="bd53a-154">Zie ook</span><span class="sxs-lookup"><span data-stu-id="bd53a-154">See also</span></span>

- [<span data-ttu-id="bd53a-155">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="bd53a-155">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
