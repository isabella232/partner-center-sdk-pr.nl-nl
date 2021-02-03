---
title: Alle analysegegevens van abonnementen ophalen
description: Hoe u de analyse gegevens van het abonnement ophaalt.
ms.date: 08/02/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: f32fb99ad52939ae8e9de26276588d3022f18fbc
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767179"
---
# <a name="get-all-subscription-analytics-information"></a><span data-ttu-id="2b3c8-103">Alle analysegegevens van abonnementen ophalen</span><span class="sxs-lookup"><span data-stu-id="2b3c8-103">Get all subscription analytics information</span></span>

<span data-ttu-id="2b3c8-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="2b3c8-104">**Applies to:**</span></span>

- <span data-ttu-id="2b3c8-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="2b3c8-105">Partner Center</span></span>
- <span data-ttu-id="2b3c8-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="2b3c8-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="2b3c8-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="2b3c8-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="2b3c8-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2b3c8-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2b3c8-109">In dit artikel wordt beschreven hoe u de analyse gegevens van het abonnement voor uw klanten kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-109">This article describes how to get all the subscription analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2b3c8-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2b3c8-110">Prerequisites</span></span>

- <span data-ttu-id="2b3c8-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2b3c8-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2b3c8-112">Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-112">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="2b3c8-113">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="2b3c8-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2b3c8-114">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2b3c8-114">Request syntax</span></span>

| <span data-ttu-id="2b3c8-115">Methode</span><span class="sxs-lookup"><span data-stu-id="2b3c8-115">Method</span></span> | <span data-ttu-id="2b3c8-116">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="2b3c8-116">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="2b3c8-117">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="2b3c8-117">**GET**</span></span> | <span data-ttu-id="2b3c8-118">[*\{ BASEURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/Subscriptions http/1.1</span><span class="sxs-lookup"><span data-stu-id="2b3c8-118">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="2b3c8-119">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="2b3c8-119">URI parameters</span></span>

<span data-ttu-id="2b3c8-120">De volgende tabel bevat optionele para meters en de bijbehorende beschrijvingen:</span><span class="sxs-lookup"><span data-stu-id="2b3c8-120">The following table lists optional parameters and their descriptions:</span></span>

| <span data-ttu-id="2b3c8-121">Parameter</span><span class="sxs-lookup"><span data-stu-id="2b3c8-121">Parameter</span></span> | <span data-ttu-id="2b3c8-122">Type</span><span class="sxs-lookup"><span data-stu-id="2b3c8-122">Type</span></span> |  <span data-ttu-id="2b3c8-123">Description</span><span class="sxs-lookup"><span data-stu-id="2b3c8-123">Description</span></span> |
|-----------|------|--------------|
| <span data-ttu-id="2b3c8-124">top</span><span class="sxs-lookup"><span data-stu-id="2b3c8-124">top</span></span> | <span data-ttu-id="2b3c8-125">int</span><span class="sxs-lookup"><span data-stu-id="2b3c8-125">int</span></span> | <span data-ttu-id="2b3c8-126">Het aantal rijen met gegevens dat in de aanvraag moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-126">The number of rows of data to return in the request.</span></span> <span data-ttu-id="2b3c8-127">Als de waarde niet is opgegeven, zijn de maximum waarde en de standaard waarde `10000` .</span><span class="sxs-lookup"><span data-stu-id="2b3c8-127">If the value isn't specified, the maximum value and the default value are `10000`.</span></span> <span data-ttu-id="2b3c8-128">Als er meer rijen in de query staan, bevat de antwoord tekst een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-128">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |
| <span data-ttu-id="2b3c8-129">skip</span><span class="sxs-lookup"><span data-stu-id="2b3c8-129">skip</span></span> | <span data-ttu-id="2b3c8-130">int</span><span class="sxs-lookup"><span data-stu-id="2b3c8-130">int</span></span> | <span data-ttu-id="2b3c8-131">Het aantal rijen dat in de query moet worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-131">The number of rows to skip in the query.</span></span> <span data-ttu-id="2b3c8-132">Gebruik deze para meter om door grote gegevens sets te bladeren.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-132">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="2b3c8-133">U kunt bijvoorbeeld `top=10000` `skip=0` de eerste 10000 rijen met gegevens ophalen en `top=10000` `skip=10000` de volgende 10000 rijen met gegevens ophalen.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-133">For example, `top=10000` and `skip=0` retrieves the first 10000 rows of data, `top=10000` and `skip=10000` retrieves the next 10000 rows of data.</span></span> |
| <span data-ttu-id="2b3c8-134">filter</span><span class="sxs-lookup"><span data-stu-id="2b3c8-134">filter</span></span> | <span data-ttu-id="2b3c8-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2b3c8-135">string</span></span> | <span data-ttu-id="2b3c8-136">Een of meer instructies waarmee de rijen in het antwoord worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-136">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="2b3c8-137">Elke filter instructie bevat een veld naam uit de hoofd tekst van het antwoord en een waarde die is gekoppeld aan de **`eq`** , **`ne`** , of voor bepaalde velden, de **`contains`** operator.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-137">Each filter statement contains a field name from the response body and a value that are associated with the **`eq`**, **`ne`**, or for certain fields, the **`contains`** operator.</span></span> <span data-ttu-id="2b3c8-138">Instructies kunnen worden gecombineerd met **`and`** of **`or`** .</span><span class="sxs-lookup"><span data-stu-id="2b3c8-138">Statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="2b3c8-139">Teken reeks waarden moeten tussen enkele aanhalings tekens in de **filter** parameter worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-139">String values must be surrounded by single quotes in the **filter** parameter.</span></span> <span data-ttu-id="2b3c8-140">Zie de volgende sectie voor een lijst met velden die kunnen worden gefilterd en de Opera tors die worden ondersteund door deze velden.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-140">See the following section for a list of fields that can be filtered and the operators that are supported with those fields.</span></span> |
| <span data-ttu-id="2b3c8-141">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="2b3c8-141">aggregationLevel</span></span> | <span data-ttu-id="2b3c8-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2b3c8-142">string</span></span> | <span data-ttu-id="2b3c8-143">Hiermee geeft u het tijds bereik op waarvoor u de samengevoegde gegevens wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-143">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="2b3c8-144">Dit kan een van de volgende teken reeksen zijn: **dag**, **week** of **maand**.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-144">Can be one of the following strings: **day**, **week**, or **month**.</span></span> <span data-ttu-id="2b3c8-145">Als de waarde niet is opgegeven, is de standaard instelling **dateRange**.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-145">If the value isn't specified, the default is **dateRange**.</span></span> <span data-ttu-id="2b3c8-146">Deze para meter is alleen van toepassing wanneer een datum veld wordt door gegeven als onderdeel van de para meter **groupBy** .</span><span class="sxs-lookup"><span data-stu-id="2b3c8-146">This parameter applies only when a date field is passed as part of the **groupBy** parameter.</span></span> |
| <span data-ttu-id="2b3c8-147">groupBy</span><span class="sxs-lookup"><span data-stu-id="2b3c8-147">groupBy</span></span> | <span data-ttu-id="2b3c8-148">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2b3c8-148">string</span></span> | <span data-ttu-id="2b3c8-149">Een instructie die alleen gegevens aggregatie toepast op de opgegeven velden.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-149">A statement that applies data aggregation only to the specified fields.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2b3c8-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="2b3c8-150">Request headers</span></span>

<span data-ttu-id="2b3c8-151">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2b3c8-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2b3c8-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="2b3c8-152">Request body</span></span>

<span data-ttu-id="2b3c8-153">Geen.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="2b3c8-154">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2b3c8-154">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="2b3c8-155">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="2b3c8-155">REST response</span></span>

<span data-ttu-id="2b3c8-156">Als dit lukt, bevat de antwoord tekst een verzameling [**abonnements**](partner-center-analytics-resources.md#subscription-resource) resources.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-156">If successful, the response body contains a collection of [**Subscription**](partner-center-analytics-resources.md#subscription-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2b3c8-157">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="2b3c8-157">Response success and error codes</span></span>

<span data-ttu-id="2b3c8-158">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2b3c8-159">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2b3c8-160">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="2b3c8-160">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2b3c8-161">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="2b3c8-161">Response example</span></span>

```http
{
    "customerTenantId": "76906668-27FC-4F5B-A35C-75A9823E13AF",
    "customerName": "TESTORG65656565",
    "customerMarket": "US",
    "id": "4BF546B2-8998-4838-BEE2-5F1BBE65A04F",
    "status": "ACTIVE",
    "productName": "OFFICE 365 BUSINESS PREMIUM",
    "subscriptionType": "Office",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "FULL OFFICE SUITE",
    "partnerName": "Partner Name",
    "providerName": "Provider Name",
    "creationDate": "2016-02-04T19:29:38.037",
   "effectiveStartDate": "2016-02-04T00:00:00",
    "commitmentEndDate": "2019-02-10T00:00:00",
    "currentStateEndDate": "2019-02-10T00:00:00",
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": "2018-02-10T02:39:57.729",
    "licenseCount": 2,
    "churnRisk": "High",
    "billingCycleName": "MONTHLY"

}
```

## <a name="see-also"></a><span data-ttu-id="2b3c8-162">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2b3c8-162">See also</span></span>

- [<span data-ttu-id="2b3c8-163">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="2b3c8-163">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
