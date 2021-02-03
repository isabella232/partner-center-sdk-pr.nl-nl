---
title: Gebruiksgegevens van licenties ophalen
description: Informatie over het gebruik van licenties op het niveau van de werk belasting voor Office en Dynamics ophalen.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a144fd078a36289e4a2c70880817b1f0ca627e8a
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767404"
---
# <a name="get-licenses-usage-information"></a><span data-ttu-id="d2e8f-103">Gebruiksgegevens van licenties ophalen</span><span class="sxs-lookup"><span data-stu-id="d2e8f-103">Get licenses usage information</span></span>

<span data-ttu-id="d2e8f-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-104">**Applies To**</span></span>

- <span data-ttu-id="d2e8f-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d2e8f-105">Partner Center</span></span>

<span data-ttu-id="d2e8f-106">Informatie over het gebruik van licenties op het niveau van de werk belasting voor Office en Dynamics ophalen.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-106">How to get licenses usage information at the workload level for Office and Dynamics.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d2e8f-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d2e8f-107">Prerequisites</span></span>

<span data-ttu-id="d2e8f-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d2e8f-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d2e8f-109">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="d2e8f-110">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d2e8f-110">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d2e8f-111">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d2e8f-111">Request syntax</span></span>

| <span data-ttu-id="d2e8f-112">Methode</span><span class="sxs-lookup"><span data-stu-id="d2e8f-112">Method</span></span>  | <span data-ttu-id="d2e8f-113">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d2e8f-113">Request URI</span></span>                                                                                |
|---------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="d2e8f-114">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-114">**GET**</span></span> | <span data-ttu-id="d2e8f-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/Analytics/Commercial/Usage/License/http/1.1</span><span class="sxs-lookup"><span data-stu-id="d2e8f-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/usage/license/ HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d2e8f-116">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d2e8f-116">Request headers</span></span>

<span data-ttu-id="d2e8f-117">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d2e8f-117">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="uri-parameters"></a><span data-ttu-id="d2e8f-118">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="d2e8f-118">URI parameters</span></span>

| <span data-ttu-id="d2e8f-119">Parameter</span><span class="sxs-lookup"><span data-stu-id="d2e8f-119">Parameter</span></span>         | <span data-ttu-id="d2e8f-120">Type</span><span class="sxs-lookup"><span data-stu-id="d2e8f-120">Type</span></span>     | <span data-ttu-id="d2e8f-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d2e8f-121">Description</span></span> | <span data-ttu-id="d2e8f-122">Vereist</span><span class="sxs-lookup"><span data-stu-id="d2e8f-122">Required</span></span> |
|-------------------|----------|-------------|----------|
| <span data-ttu-id="d2e8f-123">top</span><span class="sxs-lookup"><span data-stu-id="d2e8f-123">top</span></span>               | <span data-ttu-id="d2e8f-124">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-124">string</span></span>   | <span data-ttu-id="d2e8f-125">Het aantal rijen met gegevens dat in de aanvraag moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-125">The number of rows of data to return in the request.</span></span> <span data-ttu-id="d2e8f-126">De maximum waarde en de standaard waarde als niet wordt opgegeven, zijn 10000.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-126">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="d2e8f-127">Als er meer rijen in de query staan, bevat de antwoord tekst een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-127">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> | <span data-ttu-id="d2e8f-128">No</span><span class="sxs-lookup"><span data-stu-id="d2e8f-128">No</span></span> |
| <span data-ttu-id="d2e8f-129">skip</span><span class="sxs-lookup"><span data-stu-id="d2e8f-129">skip</span></span>              | <span data-ttu-id="d2e8f-130">int</span><span class="sxs-lookup"><span data-stu-id="d2e8f-130">int</span></span>      | <span data-ttu-id="d2e8f-131">Het aantal rijen dat in de query moet worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-131">The number of rows to skip in the query.</span></span> <span data-ttu-id="d2e8f-132">Gebruik deze para meter om door grote gegevens sets te bladeren.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-132">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="d2e8f-133">Bijvoorbeeld Top = 10000 en skip = 0 haalt de eerste 10000 rijen met gegevens op, Top = 10000 en skip = 10000 de volgende 10000 rijen met gegevens ophalen, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-133">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> | <span data-ttu-id="d2e8f-134">No</span><span class="sxs-lookup"><span data-stu-id="d2e8f-134">No</span></span> |
| <span data-ttu-id="d2e8f-135">filter</span><span class="sxs-lookup"><span data-stu-id="d2e8f-135">filter</span></span>            | <span data-ttu-id="d2e8f-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-136">string</span></span>   | <span data-ttu-id="d2e8f-137">De *filter* parameter van de aanvraag bevat een of meer instructies waarmee de rijen in het antwoord worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-137">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="d2e8f-138">Elke instructie bevat een veld en waarde die zijn gekoppeld aan de **`eq`** or **`ne`** -Opera tors en instructies kunnen worden gecombineerd met **`and`** of **`or`** .</span><span class="sxs-lookup"><span data-stu-id="d2e8f-138">Each statement contains a field and value that are associated with the **`eq`** or **`ne`** operators, and statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="d2e8f-139">Hier volgen enkele voor beelden van *filter* parameters:</span><span class="sxs-lookup"><span data-stu-id="d2e8f-139">Here are some example *filter* parameters:</span></span><br/><br/><span data-ttu-id="d2e8f-140">*filter = workloadCode EQ ' SFB '*</span><span class="sxs-lookup"><span data-stu-id="d2e8f-140">*filter=workloadCode eq 'SFB'*</span></span><br/><br/><span data-ttu-id="d2e8f-141">*filter = workloadCode EQ ' SFB '* of (*Channel EQ ' wederverkoper*')</span><span class="sxs-lookup"><span data-stu-id="d2e8f-141">*filter=workloadCode eq 'SFB'* or (*channel eq 'Reseller'*)</span></span><br/><br/><span data-ttu-id="d2e8f-142">U kunt de volgende velden opgeven:</span><span class="sxs-lookup"><span data-stu-id="d2e8f-142">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="d2e8f-143">**workloadCode**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-143">**workloadCode**</span></span><br/><span data-ttu-id="d2e8f-144">**workload**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-144">**workloadName**</span></span><br/><span data-ttu-id="d2e8f-145">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-145">**serviceCode**</span></span><br/><span data-ttu-id="d2e8f-146">**serviceName**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-146">**serviceName**</span></span><br/><span data-ttu-id="d2e8f-147">**kanalen**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-147">**channel**</span></span><br/><span data-ttu-id="d2e8f-148">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-148">**customerTenantId**</span></span><br/><span data-ttu-id="d2e8f-149">**customerName**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-149">**customerName**</span></span><br/><span data-ttu-id="d2e8f-150">**productId**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-150">**productId**</span></span><br/><span data-ttu-id="d2e8f-151">**Product**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-151">**productName**</span></span> | <span data-ttu-id="d2e8f-152">No</span><span class="sxs-lookup"><span data-stu-id="d2e8f-152">No</span></span> |
| <span data-ttu-id="d2e8f-153">GroupBy</span><span class="sxs-lookup"><span data-stu-id="d2e8f-153">groupby</span></span>           | <span data-ttu-id="d2e8f-154">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-154">string</span></span>   | <span data-ttu-id="d2e8f-155">Een instructie die alleen gegevens aggregatie toepast op de opgegeven velden.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-155">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="d2e8f-156">U kunt de volgende velden opgeven:</span><span class="sxs-lookup"><span data-stu-id="d2e8f-156">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="d2e8f-157">**workloadCode**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-157">**workloadCode**</span></span><br/><span data-ttu-id="d2e8f-158">**workload**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-158">**workloadName**</span></span><br/><span data-ttu-id="d2e8f-159">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-159">**serviceCode**</span></span><br/><span data-ttu-id="d2e8f-160">**serviceName**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-160">**serviceName**</span></span><br/><span data-ttu-id="d2e8f-161">**channelcustomerTenantId**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-161">**channelcustomerTenantId**</span></span><br/><span data-ttu-id="d2e8f-162">**customerName**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-162">**customerName**</span></span><br/><span data-ttu-id="d2e8f-163">**productId**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-163">**productId**</span></span><br/><span data-ttu-id="d2e8f-164">**Product**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-164">**productName**</span></span><br/><br/><span data-ttu-id="d2e8f-165">De geretourneerde gegevens rijen bevatten de velden die zijn opgegeven in de para meter *GroupBy* , evenals de volgende:</span><span class="sxs-lookup"><span data-stu-id="d2e8f-165">The returned data rows will contain the fields specified in the *groupby* parameter as well as the following:</span></span><br/><br/><span data-ttu-id="d2e8f-166">**licensesActive**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-166">**licensesActive**</span></span><br/><span data-ttu-id="d2e8f-167">**licensesQualified**</span><span class="sxs-lookup"><span data-stu-id="d2e8f-167">**licensesQualified**</span></span> | <span data-ttu-id="d2e8f-168">No</span><span class="sxs-lookup"><span data-stu-id="d2e8f-168">No</span></span> |
| <span data-ttu-id="d2e8f-169">processedDateTime</span><span class="sxs-lookup"><span data-stu-id="d2e8f-169">processedDateTime</span></span> | <span data-ttu-id="d2e8f-170">DateTime</span><span class="sxs-lookup"><span data-stu-id="d2e8f-170">DateTime</span></span> | <span data-ttu-id="d2e8f-171">De ene kan de datum opgeven waarop de gebruiks gegevens zijn verwerkt.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-171">One can specify the date from which usage data was processed.</span></span> <span data-ttu-id="d2e8f-172">Wordt standaard ingesteld op de laatste datum waarop de gegevens zijn verwerkt</span><span class="sxs-lookup"><span data-stu-id="d2e8f-172">Defaults to the latest date when the data was processed</span></span> | <span data-ttu-id="d2e8f-173">No</span><span class="sxs-lookup"><span data-stu-id="d2e8f-173">No</span></span> |

### <a name="request-example"></a><span data-ttu-id="d2e8f-174">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d2e8f-174">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/usage/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="d2e8f-175">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d2e8f-175">REST response</span></span>

<span data-ttu-id="d2e8f-176">Als dit lukt, bevat de antwoord tekst de volgende velden met gegevens over het gebruik van licenties.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-176">If successful, the response body contains the following fields containing data about licenses usage.</span></span>

| <span data-ttu-id="d2e8f-177">Veld</span><span class="sxs-lookup"><span data-stu-id="d2e8f-177">Field</span></span>             | <span data-ttu-id="d2e8f-178">Type</span><span class="sxs-lookup"><span data-stu-id="d2e8f-178">Type</span></span>     | <span data-ttu-id="d2e8f-179">Description</span><span class="sxs-lookup"><span data-stu-id="d2e8f-179">Description</span></span>                                   |
|-------------------|----------|-----------------------------------------------|
| <span data-ttu-id="d2e8f-180">workloadCode</span><span class="sxs-lookup"><span data-stu-id="d2e8f-180">workloadCode</span></span>      | <span data-ttu-id="d2e8f-181">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-181">string</span></span>   | <span data-ttu-id="d2e8f-182">Werkbelasting code</span><span class="sxs-lookup"><span data-stu-id="d2e8f-182">Workload code</span></span>                                 |
| <span data-ttu-id="d2e8f-183">workload</span><span class="sxs-lookup"><span data-stu-id="d2e8f-183">workloadName</span></span>      | <span data-ttu-id="d2e8f-184">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-184">string</span></span>   | <span data-ttu-id="d2e8f-185">Werkbelasting naam</span><span class="sxs-lookup"><span data-stu-id="d2e8f-185">Workload name</span></span>                                 |
| <span data-ttu-id="d2e8f-186">serviceCode</span><span class="sxs-lookup"><span data-stu-id="d2e8f-186">serviceCode</span></span>       | <span data-ttu-id="d2e8f-187">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-187">string</span></span>   | <span data-ttu-id="d2e8f-188">Service code</span><span class="sxs-lookup"><span data-stu-id="d2e8f-188">Service code</span></span>                                  |
| <span data-ttu-id="d2e8f-189">serviceName</span><span class="sxs-lookup"><span data-stu-id="d2e8f-189">serviceName</span></span>       | <span data-ttu-id="d2e8f-190">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-190">string</span></span>   | <span data-ttu-id="d2e8f-191">Servicenaam</span><span class="sxs-lookup"><span data-stu-id="d2e8f-191">Service name</span></span>                                  |
| <span data-ttu-id="d2e8f-192">kanalen</span><span class="sxs-lookup"><span data-stu-id="d2e8f-192">channel</span></span>           | <span data-ttu-id="d2e8f-193">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-193">string</span></span>   | <span data-ttu-id="d2e8f-194">Kanaal naam, wederverkoper</span><span class="sxs-lookup"><span data-stu-id="d2e8f-194">Channel name, reseller</span></span>                        |
| <span data-ttu-id="d2e8f-195">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="d2e8f-195">customerTenantId</span></span>  | <span data-ttu-id="d2e8f-196">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-196">string</span></span>   | <span data-ttu-id="d2e8f-197">De unieke id voor de klant</span><span class="sxs-lookup"><span data-stu-id="d2e8f-197">Unique identifier for the customer</span></span>            |
| <span data-ttu-id="d2e8f-198">customerName</span><span class="sxs-lookup"><span data-stu-id="d2e8f-198">customerName</span></span>      | <span data-ttu-id="d2e8f-199">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-199">string</span></span>   | <span data-ttu-id="d2e8f-200">Klantnaam</span><span class="sxs-lookup"><span data-stu-id="d2e8f-200">Customer name</span></span>                                 |
| <span data-ttu-id="d2e8f-201">productId</span><span class="sxs-lookup"><span data-stu-id="d2e8f-201">productId</span></span>         | <span data-ttu-id="d2e8f-202">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-202">string</span></span>   | <span data-ttu-id="d2e8f-203">De unieke id voor het product</span><span class="sxs-lookup"><span data-stu-id="d2e8f-203">Unique identifier for the product</span></span>             |
| <span data-ttu-id="d2e8f-204">Product</span><span class="sxs-lookup"><span data-stu-id="d2e8f-204">productName</span></span>       | <span data-ttu-id="d2e8f-205">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d2e8f-205">string</span></span>   | <span data-ttu-id="d2e8f-206">Productnaam</span><span class="sxs-lookup"><span data-stu-id="d2e8f-206">Product name</span></span>                                  |
| <span data-ttu-id="d2e8f-207">licensesActive</span><span class="sxs-lookup"><span data-stu-id="d2e8f-207">licensesActive</span></span>    | <span data-ttu-id="d2e8f-208">long</span><span class="sxs-lookup"><span data-stu-id="d2e8f-208">long</span></span>     | <span data-ttu-id="d2e8f-209">Aantal actieve licenties per werk belasting</span><span class="sxs-lookup"><span data-stu-id="d2e8f-209">Number of active licenses per workload</span></span>        |
| <span data-ttu-id="d2e8f-210">licensesQualified</span><span class="sxs-lookup"><span data-stu-id="d2e8f-210">licensesQualified</span></span> | <span data-ttu-id="d2e8f-211">long</span><span class="sxs-lookup"><span data-stu-id="d2e8f-211">long</span></span>     | <span data-ttu-id="d2e8f-212">Aantal gekwalificeerde licenties voor de werk belasting</span><span class="sxs-lookup"><span data-stu-id="d2e8f-212">Number of qualified licenses for the workload</span></span> |
| <span data-ttu-id="d2e8f-213">processedDateTime</span><span class="sxs-lookup"><span data-stu-id="d2e8f-213">processedDateTime</span></span> | <span data-ttu-id="d2e8f-214">DateTime</span><span class="sxs-lookup"><span data-stu-id="d2e8f-214">DateTime</span></span> | <span data-ttu-id="d2e8f-215">Datum waarop de gegevens voor het laatst zijn verwerkt</span><span class="sxs-lookup"><span data-stu-id="d2e8f-215">Date when the data was last processed</span></span>         |

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d2e8f-216">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="d2e8f-216">Response success and error codes</span></span>

<span data-ttu-id="d2e8f-217">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-217">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d2e8f-218">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-218">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d2e8f-219">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="d2e8f-219">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d2e8f-220">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d2e8f-220">Response example</span></span>

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
