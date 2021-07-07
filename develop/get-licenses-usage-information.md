---
title: Gebruiksgegevens van licenties ophalen
description: Informatie over het gebruik van licenties op workloadniveau voor Office en Dynamics.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ea3658089ce7eb5c1ad7cc65c3db34f9b6353cdd
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445971"
---
# <a name="get-licenses-usage-information"></a><span data-ttu-id="ab0a0-103">Gebruiksgegevens van licenties ophalen</span><span class="sxs-lookup"><span data-stu-id="ab0a0-103">Get licenses usage information</span></span>

<span data-ttu-id="ab0a0-104">Informatie over het gebruik van licenties op workloadniveau voor Office en Dynamics.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-104">How to get licenses usage information at the workload level for Office and Dynamics.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ab0a0-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ab0a0-105">Prerequisites</span></span>

<span data-ttu-id="ab0a0-106">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="ab0a0-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ab0a0-107">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-107">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="ab0a0-108">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ab0a0-108">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ab0a0-109">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="ab0a0-109">Request syntax</span></span>

| <span data-ttu-id="ab0a0-110">Methode</span><span class="sxs-lookup"><span data-stu-id="ab0a0-110">Method</span></span>  | <span data-ttu-id="ab0a0-111">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ab0a0-111">Request URI</span></span>                                                                                |
|---------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="ab0a0-112">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-112">**GET**</span></span> | <span data-ttu-id="ab0a0-113">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/usage/license/ HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ab0a0-113">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/usage/license/ HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ab0a0-114">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ab0a0-114">Request headers</span></span>

<span data-ttu-id="ab0a0-115">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="ab0a0-115">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="uri-parameters"></a><span data-ttu-id="ab0a0-116">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="ab0a0-116">URI parameters</span></span>

| <span data-ttu-id="ab0a0-117">Parameter</span><span class="sxs-lookup"><span data-stu-id="ab0a0-117">Parameter</span></span>         | <span data-ttu-id="ab0a0-118">Type</span><span class="sxs-lookup"><span data-stu-id="ab0a0-118">Type</span></span>     | <span data-ttu-id="ab0a0-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ab0a0-119">Description</span></span> | <span data-ttu-id="ab0a0-120">Vereist</span><span class="sxs-lookup"><span data-stu-id="ab0a0-120">Required</span></span> |
|-------------------|----------|-------------|----------|
| <span data-ttu-id="ab0a0-121">top</span><span class="sxs-lookup"><span data-stu-id="ab0a0-121">top</span></span>               | <span data-ttu-id="ab0a0-122">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-122">string</span></span>   | <span data-ttu-id="ab0a0-123">Het aantal rijen met gegevens dat in de aanvraag moet worden retourneren.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-123">The number of rows of data to return in the request.</span></span> <span data-ttu-id="ab0a0-124">De maximumwaarde en de standaardwaarde als deze niet is opgegeven, is 10000.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-124">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="ab0a0-125">Als er meer rijen in de query staan, bevat de antwoord-body een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-125">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> | <span data-ttu-id="ab0a0-126">Nee</span><span class="sxs-lookup"><span data-stu-id="ab0a0-126">No</span></span> |
| <span data-ttu-id="ab0a0-127">skip</span><span class="sxs-lookup"><span data-stu-id="ab0a0-127">skip</span></span>              | <span data-ttu-id="ab0a0-128">int</span><span class="sxs-lookup"><span data-stu-id="ab0a0-128">int</span></span>      | <span data-ttu-id="ab0a0-129">Het aantal rijen dat moet worden overgeslagen in de query.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-129">The number of rows to skip in the query.</span></span> <span data-ttu-id="ab0a0-130">Gebruik deze parameter om door grote gegevenssets te gaan.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-130">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="ab0a0-131">Top=10000 en skip=0 haalt bijvoorbeeld de eerste 10.000 rijen met gegevens op, top=10000 en skip=10000 haalt de volgende 10000 rijen met gegevens op, bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-131">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> | <span data-ttu-id="ab0a0-132">Nee</span><span class="sxs-lookup"><span data-stu-id="ab0a0-132">No</span></span> |
| <span data-ttu-id="ab0a0-133">filter</span><span class="sxs-lookup"><span data-stu-id="ab0a0-133">filter</span></span>            | <span data-ttu-id="ab0a0-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-134">string</span></span>   | <span data-ttu-id="ab0a0-135">De *filterparameter* van de aanvraag bevat een of meer instructies die de rijen in het antwoord filteren.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-135">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="ab0a0-136">Elke instructie bevat een veld en waarde die zijn gekoppeld aan de operators of en instructies **`eq`** kunnen worden gecombineerd met behulp van of **`ne`** **`and`** **`or`** .</span><span class="sxs-lookup"><span data-stu-id="ab0a0-136">Each statement contains a field and value that are associated with the **`eq`** or **`ne`** operators, and statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="ab0a0-137">Hier volgen enkele *voorbeeldfilterparameters:*</span><span class="sxs-lookup"><span data-stu-id="ab0a0-137">Here are some example *filter* parameters:</span></span><br/><br/><span data-ttu-id="ab0a0-138">*filter=workloadCode eq 'SFB'*</span><span class="sxs-lookup"><span data-stu-id="ab0a0-138">*filter=workloadCode eq 'SFB'*</span></span><br/><br/><span data-ttu-id="ab0a0-139">*filter=workloadCode eq 'SFB'* of (*kanaal eq 'Reseller'*)</span><span class="sxs-lookup"><span data-stu-id="ab0a0-139">*filter=workloadCode eq 'SFB'* or (*channel eq 'Reseller'*)</span></span><br/><br/><span data-ttu-id="ab0a0-140">U kunt de volgende velden opgeven:</span><span class="sxs-lookup"><span data-stu-id="ab0a0-140">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="ab0a0-141">**workloadCode**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-141">**workloadCode**</span></span><br/><span data-ttu-id="ab0a0-142">**workloadName**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-142">**workloadName**</span></span><br/><span data-ttu-id="ab0a0-143">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-143">**serviceCode**</span></span><br/><span data-ttu-id="ab0a0-144">**Servicenaam**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-144">**serviceName**</span></span><br/><span data-ttu-id="ab0a0-145">**Kanaal**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-145">**channel**</span></span><br/><span data-ttu-id="ab0a0-146">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-146">**customerTenantId**</span></span><br/><span data-ttu-id="ab0a0-147">**customerName**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-147">**customerName**</span></span><br/><span data-ttu-id="ab0a0-148">**Productid**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-148">**productId**</span></span><br/><span data-ttu-id="ab0a0-149">**Productnaam**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-149">**productName**</span></span> | <span data-ttu-id="ab0a0-150">Nee</span><span class="sxs-lookup"><span data-stu-id="ab0a0-150">No</span></span> |
| <span data-ttu-id="ab0a0-151">groupby</span><span class="sxs-lookup"><span data-stu-id="ab0a0-151">groupby</span></span>           | <span data-ttu-id="ab0a0-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-152">string</span></span>   | <span data-ttu-id="ab0a0-153">Een instructie die gegevensaggregatie alleen op de opgegeven velden van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-153">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="ab0a0-154">U kunt de volgende velden opgeven:</span><span class="sxs-lookup"><span data-stu-id="ab0a0-154">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="ab0a0-155">**workloadCode**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-155">**workloadCode**</span></span><br/><span data-ttu-id="ab0a0-156">**workloadName**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-156">**workloadName**</span></span><br/><span data-ttu-id="ab0a0-157">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-157">**serviceCode**</span></span><br/><span data-ttu-id="ab0a0-158">**Servicenaam**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-158">**serviceName**</span></span><br/><span data-ttu-id="ab0a0-159">**channelcustomerTenantId**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-159">**channelcustomerTenantId**</span></span><br/><span data-ttu-id="ab0a0-160">**customerName**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-160">**customerName**</span></span><br/><span data-ttu-id="ab0a0-161">**Productid**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-161">**productId**</span></span><br/><span data-ttu-id="ab0a0-162">**Productnaam**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-162">**productName**</span></span><br/><br/><span data-ttu-id="ab0a0-163">De geretourneerde gegevensrijen bevatten de velden die zijn opgegeven in de *groupby-parameter* en het volgende:</span><span class="sxs-lookup"><span data-stu-id="ab0a0-163">The returned data rows will contain the fields specified in the *groupby* parameter and the following:</span></span><br/><br/><span data-ttu-id="ab0a0-164">**licensesActive**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-164">**licensesActive**</span></span><br/><span data-ttu-id="ab0a0-165">**licensesQualified**</span><span class="sxs-lookup"><span data-stu-id="ab0a0-165">**licensesQualified**</span></span> | <span data-ttu-id="ab0a0-166">Nee</span><span class="sxs-lookup"><span data-stu-id="ab0a0-166">No</span></span> |
| <span data-ttu-id="ab0a0-167">processedDateTime</span><span class="sxs-lookup"><span data-stu-id="ab0a0-167">processedDateTime</span></span> | <span data-ttu-id="ab0a0-168">DateTime</span><span class="sxs-lookup"><span data-stu-id="ab0a0-168">DateTime</span></span> | <span data-ttu-id="ab0a0-169">U kunt de datum opgeven vanaf welke gebruiksgegevens zijn verwerkt.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-169">One can specify the date from which usage data was processed.</span></span> <span data-ttu-id="ab0a0-170">De standaardwaarde is de laatste datum waarop de gegevens zijn verwerkt</span><span class="sxs-lookup"><span data-stu-id="ab0a0-170">Defaults to the latest date when the data was processed</span></span> | <span data-ttu-id="ab0a0-171">Nee</span><span class="sxs-lookup"><span data-stu-id="ab0a0-171">No</span></span> |

### <a name="request-example"></a><span data-ttu-id="ab0a0-172">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ab0a0-172">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/usage/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="ab0a0-173">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ab0a0-173">REST response</span></span>

<span data-ttu-id="ab0a0-174">Als dit lukt, bevat de antwoord-body de volgende velden met gegevens over het gebruik van licenties.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-174">If successful, the response body contains the following fields containing data about licenses usage.</span></span>

| <span data-ttu-id="ab0a0-175">Veld</span><span class="sxs-lookup"><span data-stu-id="ab0a0-175">Field</span></span>             | <span data-ttu-id="ab0a0-176">Type</span><span class="sxs-lookup"><span data-stu-id="ab0a0-176">Type</span></span>     | <span data-ttu-id="ab0a0-177">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ab0a0-177">Description</span></span>                                   |
|-------------------|----------|-----------------------------------------------|
| <span data-ttu-id="ab0a0-178">workloadCode</span><span class="sxs-lookup"><span data-stu-id="ab0a0-178">workloadCode</span></span>      | <span data-ttu-id="ab0a0-179">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-179">string</span></span>   | <span data-ttu-id="ab0a0-180">Workloadcode</span><span class="sxs-lookup"><span data-stu-id="ab0a0-180">Workload code</span></span>                                 |
| <span data-ttu-id="ab0a0-181">workloadName</span><span class="sxs-lookup"><span data-stu-id="ab0a0-181">workloadName</span></span>      | <span data-ttu-id="ab0a0-182">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-182">string</span></span>   | <span data-ttu-id="ab0a0-183">Workloadnaam</span><span class="sxs-lookup"><span data-stu-id="ab0a0-183">Workload name</span></span>                                 |
| <span data-ttu-id="ab0a0-184">serviceCode</span><span class="sxs-lookup"><span data-stu-id="ab0a0-184">serviceCode</span></span>       | <span data-ttu-id="ab0a0-185">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-185">string</span></span>   | <span data-ttu-id="ab0a0-186">Servicecode</span><span class="sxs-lookup"><span data-stu-id="ab0a0-186">Service code</span></span>                                  |
| <span data-ttu-id="ab0a0-187">Servicenaam</span><span class="sxs-lookup"><span data-stu-id="ab0a0-187">serviceName</span></span>       | <span data-ttu-id="ab0a0-188">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-188">string</span></span>   | <span data-ttu-id="ab0a0-189">Servicenaam</span><span class="sxs-lookup"><span data-stu-id="ab0a0-189">Service name</span></span>                                  |
| <span data-ttu-id="ab0a0-190">Kanaal</span><span class="sxs-lookup"><span data-stu-id="ab0a0-190">channel</span></span>           | <span data-ttu-id="ab0a0-191">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-191">string</span></span>   | <span data-ttu-id="ab0a0-192">Kanaalnaam, reseller</span><span class="sxs-lookup"><span data-stu-id="ab0a0-192">Channel name, reseller</span></span>                        |
| <span data-ttu-id="ab0a0-193">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="ab0a0-193">customerTenantId</span></span>  | <span data-ttu-id="ab0a0-194">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-194">string</span></span>   | <span data-ttu-id="ab0a0-195">Unieke id voor de klant</span><span class="sxs-lookup"><span data-stu-id="ab0a0-195">Unique identifier for the customer</span></span>            |
| <span data-ttu-id="ab0a0-196">customerName</span><span class="sxs-lookup"><span data-stu-id="ab0a0-196">customerName</span></span>      | <span data-ttu-id="ab0a0-197">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-197">string</span></span>   | <span data-ttu-id="ab0a0-198">Klantnaam</span><span class="sxs-lookup"><span data-stu-id="ab0a0-198">Customer name</span></span>                                 |
| <span data-ttu-id="ab0a0-199">productId</span><span class="sxs-lookup"><span data-stu-id="ab0a0-199">productId</span></span>         | <span data-ttu-id="ab0a0-200">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-200">string</span></span>   | <span data-ttu-id="ab0a0-201">Unieke id voor het product</span><span class="sxs-lookup"><span data-stu-id="ab0a0-201">Unique identifier for the product</span></span>             |
| <span data-ttu-id="ab0a0-202">Productnaam</span><span class="sxs-lookup"><span data-stu-id="ab0a0-202">productName</span></span>       | <span data-ttu-id="ab0a0-203">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ab0a0-203">string</span></span>   | <span data-ttu-id="ab0a0-204">Productnaam</span><span class="sxs-lookup"><span data-stu-id="ab0a0-204">Product name</span></span>                                  |
| <span data-ttu-id="ab0a0-205">licensesActive</span><span class="sxs-lookup"><span data-stu-id="ab0a0-205">licensesActive</span></span>    | <span data-ttu-id="ab0a0-206">long</span><span class="sxs-lookup"><span data-stu-id="ab0a0-206">long</span></span>     | <span data-ttu-id="ab0a0-207">Aantal actieve licenties per workload</span><span class="sxs-lookup"><span data-stu-id="ab0a0-207">Number of active licenses per workload</span></span>        |
| <span data-ttu-id="ab0a0-208">licensesQualified</span><span class="sxs-lookup"><span data-stu-id="ab0a0-208">licensesQualified</span></span> | <span data-ttu-id="ab0a0-209">long</span><span class="sxs-lookup"><span data-stu-id="ab0a0-209">long</span></span>     | <span data-ttu-id="ab0a0-210">Aantal gekwalificeerde licenties voor de workload</span><span class="sxs-lookup"><span data-stu-id="ab0a0-210">Number of qualified licenses for the workload</span></span> |
| <span data-ttu-id="ab0a0-211">processedDateTime</span><span class="sxs-lookup"><span data-stu-id="ab0a0-211">processedDateTime</span></span> | <span data-ttu-id="ab0a0-212">DateTime</span><span class="sxs-lookup"><span data-stu-id="ab0a0-212">DateTime</span></span> | <span data-ttu-id="ab0a0-213">De datum waarop de gegevens voor het laatst zijn verwerkt</span><span class="sxs-lookup"><span data-stu-id="ab0a0-213">Date when the data was last processed</span></span>         |

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ab0a0-214">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="ab0a0-214">Response success and error codes</span></span>

<span data-ttu-id="ab0a0-215">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-215">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ab0a0-216">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ab0a0-216">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ab0a0-217">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="ab0a0-217">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ab0a0-218">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ab0a0-218">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 487
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CV: f0trvmq8mEScHcFS.0
MS-ServerId: 4
Date: Wed, 24 Oct 2018 22:37:18 GMT

{
"Value": [
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "workloadCode": "SPO",
      "workloadName": "SharePoint",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "6FD2C87F-B296-42F0-B197-1E91E994B900",
      "productName": "OFFICE 365 ENTERPRISE E3",
      "licenseActive": 0,
      "licensesQualified": 1
    },
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "workloadCode": "EXO",
      "workloadName": "Exchange",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "45A2423B-E884-448D-A831-D9E139C52D2F",
      "productName": "EXCHANGE ONLINE PROTECTION",
      "licenseActive": 0,
      "licensesQualified": 1
    }
}
```
