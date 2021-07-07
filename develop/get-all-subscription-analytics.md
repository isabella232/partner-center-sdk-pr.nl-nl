---
title: Alle analysegegevens van abonnementen ophalen
description: Informatie over het verkrijgen van alle analysegegevens van het abonnement.
ms.date: 08/02/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: e1f16c92569a02bc51c96a85ecb642fbeb76a9a7
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760246"
---
# <a name="get-all-subscription-analytics-information"></a><span data-ttu-id="ee507-103">Alle analysegegevens van abonnementen ophalen</span><span class="sxs-lookup"><span data-stu-id="ee507-103">Get all subscription analytics information</span></span>

<span data-ttu-id="ee507-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ee507-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ee507-105">In dit artikel wordt beschreven hoe u alle analysegegevens voor abonnementen voor uw klanten op kunt halen.</span><span class="sxs-lookup"><span data-stu-id="ee507-105">This article describes how to get all the subscription analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ee507-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ee507-106">Prerequisites</span></span>

- <span data-ttu-id="ee507-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ee507-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ee507-108">Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="ee507-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="ee507-109">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ee507-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ee507-110">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="ee507-110">Request syntax</span></span>

| <span data-ttu-id="ee507-111">Methode</span><span class="sxs-lookup"><span data-stu-id="ee507-111">Method</span></span> | <span data-ttu-id="ee507-112">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ee507-112">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="ee507-113">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ee507-113">**GET**</span></span> | <span data-ttu-id="ee507-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ee507-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="ee507-115">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="ee507-115">URI parameters</span></span>

<span data-ttu-id="ee507-116">De volgende tabel bevat optionele parameters en de bijbehorende beschrijvingen:</span><span class="sxs-lookup"><span data-stu-id="ee507-116">The following table lists optional parameters and their descriptions:</span></span>

| <span data-ttu-id="ee507-117">Parameter</span><span class="sxs-lookup"><span data-stu-id="ee507-117">Parameter</span></span> | <span data-ttu-id="ee507-118">Type</span><span class="sxs-lookup"><span data-stu-id="ee507-118">Type</span></span> |  <span data-ttu-id="ee507-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ee507-119">Description</span></span> |
|-----------|------|--------------|
| <span data-ttu-id="ee507-120">top</span><span class="sxs-lookup"><span data-stu-id="ee507-120">top</span></span> | <span data-ttu-id="ee507-121">int</span><span class="sxs-lookup"><span data-stu-id="ee507-121">int</span></span> | <span data-ttu-id="ee507-122">Het aantal rijen met gegevens dat in de aanvraag moet worden retourneren.</span><span class="sxs-lookup"><span data-stu-id="ee507-122">The number of rows of data to return in the request.</span></span> <span data-ttu-id="ee507-123">Als de waarde niet is opgegeven, zijn de maximumwaarde en de standaardwaarde `10000` .</span><span class="sxs-lookup"><span data-stu-id="ee507-123">If the value isn't specified, the maximum value and the default value are `10000`.</span></span> <span data-ttu-id="ee507-124">Als er meer rijen in de query staan, bevat de hoofdpagina van het antwoord een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="ee507-124">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |
| <span data-ttu-id="ee507-125">skip</span><span class="sxs-lookup"><span data-stu-id="ee507-125">skip</span></span> | <span data-ttu-id="ee507-126">int</span><span class="sxs-lookup"><span data-stu-id="ee507-126">int</span></span> | <span data-ttu-id="ee507-127">Het aantal rijen dat moet worden overgeslagen in de query.</span><span class="sxs-lookup"><span data-stu-id="ee507-127">The number of rows to skip in the query.</span></span> <span data-ttu-id="ee507-128">Gebruik deze parameter om grote gegevenssets te bekijken.</span><span class="sxs-lookup"><span data-stu-id="ee507-128">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="ee507-129">En haalt bijvoorbeeld de eerste 10000 rijen met gegevens op en haalt de volgende `top=10000` `skip=0` `top=10000` `skip=10000` 10.000 rijen met gegevens op.</span><span class="sxs-lookup"><span data-stu-id="ee507-129">For example, `top=10000` and `skip=0` retrieves the first 10000 rows of data, `top=10000` and `skip=10000` retrieves the next 10000 rows of data.</span></span> |
| <span data-ttu-id="ee507-130">filter</span><span class="sxs-lookup"><span data-stu-id="ee507-130">filter</span></span> | <span data-ttu-id="ee507-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ee507-131">string</span></span> | <span data-ttu-id="ee507-132">Een of meer instructies die de rijen in het antwoord filteren.</span><span class="sxs-lookup"><span data-stu-id="ee507-132">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="ee507-133">Elke filter-instructie bevat een veldnaam uit de antwoord-body en een waarde die zijn gekoppeld aan de operator , of voor **`eq`** **`ne`** bepaalde **`contains`** velden.</span><span class="sxs-lookup"><span data-stu-id="ee507-133">Each filter statement contains a field name from the response body and a value that are associated with the **`eq`**, **`ne`**, or for certain fields, the **`contains`** operator.</span></span> <span data-ttu-id="ee507-134">Instructies kunnen worden gecombineerd met **`and`** of **`or`** .</span><span class="sxs-lookup"><span data-stu-id="ee507-134">Statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="ee507-135">Tekenreekswaarden moeten tussen enkele aanhalingstekens in de **filterparameter staan.**</span><span class="sxs-lookup"><span data-stu-id="ee507-135">String values must be surrounded by single quotes in the **filter** parameter.</span></span> <span data-ttu-id="ee507-136">Zie de volgende sectie voor een lijst met velden die kunnen worden gefilterd en de operators die worden ondersteund met deze velden.</span><span class="sxs-lookup"><span data-stu-id="ee507-136">See the following section for a list of fields that can be filtered and the operators that are supported with those fields.</span></span> |
| <span data-ttu-id="ee507-137">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="ee507-137">aggregationLevel</span></span> | <span data-ttu-id="ee507-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ee507-138">string</span></span> | <span data-ttu-id="ee507-139">Hiermee geeft u het tijdsbereik op waarvoor geaggregeerde gegevens moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ee507-139">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="ee507-140">Kan een van de volgende tekenreeksen zijn: **dag,** **week** of **maand.**</span><span class="sxs-lookup"><span data-stu-id="ee507-140">Can be one of the following strings: **day**, **week**, or **month**.</span></span> <span data-ttu-id="ee507-141">Als de waarde niet is opgegeven, is de **standaardwaarde dateRange.**</span><span class="sxs-lookup"><span data-stu-id="ee507-141">If the value isn't specified, the default is **dateRange**.</span></span> <span data-ttu-id="ee507-142">Deze parameter is alleen van toepassing wanneer een datumveld wordt doorgegeven als onderdeel van de **groupBy-parameter.**</span><span class="sxs-lookup"><span data-stu-id="ee507-142">This parameter applies only when a date field is passed as part of the **groupBy** parameter.</span></span> |
| <span data-ttu-id="ee507-143">groupBy</span><span class="sxs-lookup"><span data-stu-id="ee507-143">groupBy</span></span> | <span data-ttu-id="ee507-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ee507-144">string</span></span> | <span data-ttu-id="ee507-145">Een instructie die gegevensaggregatie alleen op de opgegeven velden van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="ee507-145">A statement that applies data aggregation only to the specified fields.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ee507-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ee507-146">Request headers</span></span>

<span data-ttu-id="ee507-147">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="ee507-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ee507-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ee507-148">Request body</span></span>

<span data-ttu-id="ee507-149">Geen.</span><span class="sxs-lookup"><span data-stu-id="ee507-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ee507-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ee507-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="ee507-151">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ee507-151">REST response</span></span>

<span data-ttu-id="ee507-152">Als dit lukt, bevat de antwoord-body een verzameling [**abonnementsresources.**](partner-center-analytics-resources.md#subscription-resource)</span><span class="sxs-lookup"><span data-stu-id="ee507-152">If successful, the response body contains a collection of [**Subscription**](partner-center-analytics-resources.md#subscription-resource) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ee507-153">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="ee507-153">Response success and error codes</span></span>

<span data-ttu-id="ee507-154">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="ee507-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ee507-155">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ee507-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ee507-156">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="ee507-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ee507-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ee507-157">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ee507-158">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ee507-158">See also</span></span>

- [<span data-ttu-id="ee507-159">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="ee507-159">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
