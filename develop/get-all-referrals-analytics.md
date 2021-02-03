---
title: Alle analysegegevens van verwijzingen ophalen
description: Instructies voor het ophalen van de analyse-informatie over verwijzingen.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: Kim-Davis
ms.author: kimnich
ms.openlocfilehash: b470c59cecf8b214e6d90a244e928e5d15ebd3e0
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767288"
---
# <a name="get-all-referrals-analytics-information"></a><span data-ttu-id="fafb7-103">Alle analysegegevens van verwijzingen ophalen</span><span class="sxs-lookup"><span data-stu-id="fafb7-103">Get all referrals analytics information</span></span>

<span data-ttu-id="fafb7-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="fafb7-104">**Applies To**</span></span>

- <span data-ttu-id="fafb7-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="fafb7-105">Partner Center</span></span>
- <span data-ttu-id="fafb7-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="fafb7-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="fafb7-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="fafb7-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="fafb7-108">Meer informatie over het ophalen van de verwijzingen voor uw klanten.</span><span class="sxs-lookup"><span data-stu-id="fafb7-108">How to get all the referrals analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fafb7-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fafb7-109">Prerequisites</span></span>

- <span data-ttu-id="fafb7-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fafb7-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fafb7-111">Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="fafb7-111">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="fafb7-112">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fafb7-112">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fafb7-113">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fafb7-113">Request syntax</span></span>

| <span data-ttu-id="fafb7-114">Methode</span><span class="sxs-lookup"><span data-stu-id="fafb7-114">Method</span></span>  | <span data-ttu-id="fafb7-115">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fafb7-115">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="fafb7-116">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fafb7-116">**GET**</span></span> | <span data-ttu-id="fafb7-117">[*\{ BASEURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/referrals http/1.1</span><span class="sxs-lookup"><span data-stu-id="fafb7-117">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/referrals HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="fafb7-118">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="fafb7-118">URI parameters</span></span>

| <span data-ttu-id="fafb7-119">Parameter</span><span class="sxs-lookup"><span data-stu-id="fafb7-119">Parameter</span></span> | <span data-ttu-id="fafb7-120">Type</span><span class="sxs-lookup"><span data-stu-id="fafb7-120">Type</span></span> | <span data-ttu-id="fafb7-121">Description</span><span class="sxs-lookup"><span data-stu-id="fafb7-121">Description</span></span> |
|-----------|------|-------------|
| <span data-ttu-id="fafb7-122">filter</span><span class="sxs-lookup"><span data-stu-id="fafb7-122">filter</span></span> | <span data-ttu-id="fafb7-123">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fafb7-123">string</span></span> | <span data-ttu-id="fafb7-124">Hiermee worden gegevens geretourneerd die overeenkomen met de filter voorwaarde.</span><span class="sxs-lookup"><span data-stu-id="fafb7-124">Returns data matching the filter condition.</span></span></br> <span data-ttu-id="fafb7-125">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="fafb7-125">**Example:**</span></span></br>  `.../referrals?filter=field eq 'value'` |
| <span data-ttu-id="fafb7-126">GroupBy</span><span class="sxs-lookup"><span data-stu-id="fafb7-126">groupby</span></span> | <span data-ttu-id="fafb7-127">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fafb7-127">string</span></span> | <span data-ttu-id="fafb7-128">Ondersteunt zowel termen als datums.</span><span class="sxs-lookup"><span data-stu-id="fafb7-128">Supports both terms and dates.</span></span> <span data-ttu-id="fafb7-129">Korte circuit logica om het aantal buckets te beperken.</span><span class="sxs-lookup"><span data-stu-id="fafb7-129">Short circuit logic to limit the number of buckets.</span></span></br> <span data-ttu-id="fafb7-130">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="fafb7-130">**Example:**</span></span></br>  `.../referrals?groupby=termField1,dateField1,termField2` |
| <span data-ttu-id="fafb7-131">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="fafb7-131">aggregationLevel</span></span> | <span data-ttu-id="fafb7-132">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fafb7-132">string</span></span> | <span data-ttu-id="fafb7-133">Voor de para meter *aggregationLevel* is een *GroupBy* vereist.</span><span class="sxs-lookup"><span data-stu-id="fafb7-133">The *aggregationLevel* parameter requires a *groupby*.</span></span> <span data-ttu-id="fafb7-134">De para meter *aggregationLevel* is van toepassing op alle datum velden die in de *GroupBy* worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="fafb7-134">The *aggregationLevel* parameter applies to all date fields present in the *groupby*.</span></span></br> <span data-ttu-id="fafb7-135">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="fafb7-135">**Example:**</span></span></br> `.../referrals?groupby=termField1,dateField1,termField2&aggregationLevel=day` |
| <span data-ttu-id="fafb7-136">top</span><span class="sxs-lookup"><span data-stu-id="fafb7-136">top</span></span> | <span data-ttu-id="fafb7-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fafb7-137">string</span></span> | <span data-ttu-id="fafb7-138">De pagina limiet is 10000.</span><span class="sxs-lookup"><span data-stu-id="fafb7-138">The page limit is 10000.</span></span> <span data-ttu-id="fafb7-139">Neemt een waarde op die kleiner is dan 10000.</span><span class="sxs-lookup"><span data-stu-id="fafb7-139">Takes any value less than 10000.</span></span></br> <span data-ttu-id="fafb7-140">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="fafb7-140">**Example:**</span></span></br> `.../referrals?top=100`</br> |
| <span data-ttu-id="fafb7-141">skip</span><span class="sxs-lookup"><span data-stu-id="fafb7-141">skip</span></span> | <span data-ttu-id="fafb7-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fafb7-142">string</span></span> | <span data-ttu-id="fafb7-143">Het aantal rijen dat moet worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="fafb7-143">Number of rows to skip.</span></span></br> <span data-ttu-id="fafb7-144">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="fafb7-144">**Example:**</span></span></br>  `.../referrals?top=100&skip=100` |

### <a name="request-headers"></a><span data-ttu-id="fafb7-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fafb7-145">Request headers</span></span>

<span data-ttu-id="fafb7-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="fafb7-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fafb7-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fafb7-147">Request body</span></span>

<span data-ttu-id="fafb7-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="fafb7-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="fafb7-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fafb7-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/referrals HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="fafb7-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fafb7-150">REST response</span></span>

<span data-ttu-id="fafb7-151">Als dit lukt, bevat de antwoord tekst een verzameling [verwijzingen](partner-center-analytics-resources.md#referrals-resource) -resources.</span><span class="sxs-lookup"><span data-stu-id="fafb7-151">If successful, the response body contains a collection of [Referrals](partner-center-analytics-resources.md#referrals-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fafb7-152">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="fafb7-152">Response success and error codes</span></span>

<span data-ttu-id="fafb7-153">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="fafb7-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fafb7-154">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fafb7-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fafb7-155">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="fafb7-155">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fafb7-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fafb7-156">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="fafb7-157">Zie ook</span><span class="sxs-lookup"><span data-stu-id="fafb7-157">See also</span></span>

- [<span data-ttu-id="fafb7-158">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="fafb7-158">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
