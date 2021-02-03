---
title: Implementatiegegevens van licenties ophalen
description: Implementatie-informatie over Office-en Dynamics-licenties ophalen.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ef0e5d73d34bc51e4cc58143db6c9fc49cb58fcb
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767406"
---
# <a name="get-licenses-deployment-information"></a><span data-ttu-id="33de0-103">Implementatiegegevens van licenties ophalen</span><span class="sxs-lookup"><span data-stu-id="33de0-103">Get licenses deployment information</span></span>

<span data-ttu-id="33de0-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="33de0-104">**Applies To**</span></span>

- <span data-ttu-id="33de0-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="33de0-105">Partner Center</span></span>

<span data-ttu-id="33de0-106">Implementatie-informatie over Office-en Dynamics-licenties ophalen.</span><span class="sxs-lookup"><span data-stu-id="33de0-106">How to get deployment information for Office and Dynamics licenses.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="33de0-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="33de0-107">Prerequisites</span></span>

<span data-ttu-id="33de0-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="33de0-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="33de0-109">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="33de0-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="33de0-110">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="33de0-110">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="33de0-111">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="33de0-111">Request syntax</span></span>

| <span data-ttu-id="33de0-112">Methode</span><span class="sxs-lookup"><span data-stu-id="33de0-112">Method</span></span>  | <span data-ttu-id="33de0-113">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="33de0-113">Request URI</span></span>                                                                                     |
|---------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="33de0-114">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="33de0-114">**GET**</span></span> | <span data-ttu-id="33de0-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/Analytics/Commercial/Deployment/License/http/1.1</span><span class="sxs-lookup"><span data-stu-id="33de0-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/deployment/license/ HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="33de0-116">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="33de0-116">Request headers</span></span>

<span data-ttu-id="33de0-117">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="33de0-117">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="uri-parameters"></a><span data-ttu-id="33de0-118">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="33de0-118">URI parameters</span></span>

| <span data-ttu-id="33de0-119">Parameter</span><span class="sxs-lookup"><span data-stu-id="33de0-119">Parameter</span></span>         | <span data-ttu-id="33de0-120">Type</span><span class="sxs-lookup"><span data-stu-id="33de0-120">Type</span></span>     | <span data-ttu-id="33de0-121">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="33de0-121">Description</span></span> | <span data-ttu-id="33de0-122">Vereist</span><span class="sxs-lookup"><span data-stu-id="33de0-122">Required</span></span> |
|-------------------|----------|-------------|----------|
| <span data-ttu-id="33de0-123">top</span><span class="sxs-lookup"><span data-stu-id="33de0-123">top</span></span>               | <span data-ttu-id="33de0-124">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="33de0-124">string</span></span>   | <span data-ttu-id="33de0-125">Het aantal rijen met gegevens dat in de aanvraag moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="33de0-125">The number of rows of data to return in the request.</span></span> <span data-ttu-id="33de0-126">De maximum waarde en de standaard waarde als niet wordt opgegeven, zijn 10000.</span><span class="sxs-lookup"><span data-stu-id="33de0-126">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="33de0-127">Als er meer rijen in de query staan, bevat de antwoord tekst een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="33de0-127">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> | <span data-ttu-id="33de0-128">No</span><span class="sxs-lookup"><span data-stu-id="33de0-128">No</span></span> |
| <span data-ttu-id="33de0-129">skip</span><span class="sxs-lookup"><span data-stu-id="33de0-129">skip</span></span>              | <span data-ttu-id="33de0-130">int</span><span class="sxs-lookup"><span data-stu-id="33de0-130">int</span></span>      | <span data-ttu-id="33de0-131">Het aantal rijen dat in de query moet worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="33de0-131">The number of rows to skip in the query.</span></span> <span data-ttu-id="33de0-132">Gebruik deze para meter om door grote gegevens sets te bladeren.</span><span class="sxs-lookup"><span data-stu-id="33de0-132">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="33de0-133">Bijvoorbeeld Top = 10000 en skip = 0 haalt de eerste 10000 rijen met gegevens op, Top = 10000 en skip = 10000 de volgende 10000 rijen met gegevens ophalen, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="33de0-133">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> | <span data-ttu-id="33de0-134">No</span><span class="sxs-lookup"><span data-stu-id="33de0-134">No</span></span> |
| <span data-ttu-id="33de0-135">filter</span><span class="sxs-lookup"><span data-stu-id="33de0-135">filter</span></span>            | <span data-ttu-id="33de0-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="33de0-136">string</span></span>   | <span data-ttu-id="33de0-137">De *filter* parameter van de aanvraag bevat een of meer instructies waarmee de rijen in het antwoord worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="33de0-137">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="33de0-138">Elke instructie bevat een veld en waarde die zijn gekoppeld aan de `eq` or `ne` -Opera tors en instructies kunnen worden gecombineerd met `and` of `or` .</span><span class="sxs-lookup"><span data-stu-id="33de0-138">Each statement contains a field and value that are associated with the `eq` or `ne` operators, and statements can be combined using `and` or `or`.</span></span> <span data-ttu-id="33de0-139">Hier volgen enkele voor beelden van *filter* parameters:</span><span class="sxs-lookup"><span data-stu-id="33de0-139">Here are some example *filter* parameters:</span></span><br/><br/> <span data-ttu-id="33de0-140">*filter = serviceCode EQ ' O365 '*</span><span class="sxs-lookup"><span data-stu-id="33de0-140">*filter=serviceCode eq 'O365'*</span></span><br/> <span data-ttu-id="33de0-141">*filter = serviceCode EQ ' O365 '* of (*Channel EQ ' wederverkoper*')</span><span class="sxs-lookup"><span data-stu-id="33de0-141">*filter=serviceCode eq 'O365'* or (*channel eq 'Reseller'*)</span></span><br/><br/> <span data-ttu-id="33de0-142">U kunt de volgende velden opgeven:</span><span class="sxs-lookup"><span data-stu-id="33de0-142">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="33de0-143">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="33de0-143">**serviceCode**</span></span><br/><span data-ttu-id="33de0-144">**serviceName**</span><span class="sxs-lookup"><span data-stu-id="33de0-144">**serviceName**</span></span><br/><span data-ttu-id="33de0-145">**kanalen**</span><span class="sxs-lookup"><span data-stu-id="33de0-145">**channel**</span></span><br/><span data-ttu-id="33de0-146">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="33de0-146">**customerTenantId**</span></span><br/><span data-ttu-id="33de0-147">**customerName**</span><span class="sxs-lookup"><span data-stu-id="33de0-147">**customerName**</span></span><br/><span data-ttu-id="33de0-148">**productId**</span><span class="sxs-lookup"><span data-stu-id="33de0-148">**productId**</span></span><br/><span data-ttu-id="33de0-149">**Product**</span><span class="sxs-lookup"><span data-stu-id="33de0-149">**productName**</span></span>  | <span data-ttu-id="33de0-150">No</span><span class="sxs-lookup"><span data-stu-id="33de0-150">No</span></span> |
| <span data-ttu-id="33de0-151">GroupBy</span><span class="sxs-lookup"><span data-stu-id="33de0-151">groupby</span></span>           | <span data-ttu-id="33de0-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="33de0-152">string</span></span>   | <span data-ttu-id="33de0-153">Een instructie die alleen gegevens aggregatie toepast op de opgegeven velden.</span><span class="sxs-lookup"><span data-stu-id="33de0-153">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="33de0-154">U kunt de volgende velden opgeven:</span><span class="sxs-lookup"><span data-stu-id="33de0-154">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="33de0-155">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="33de0-155">**serviceCode**</span></span><br/><span data-ttu-id="33de0-156">**serviceName**</span><span class="sxs-lookup"><span data-stu-id="33de0-156">**serviceName**</span></span><br/><span data-ttu-id="33de0-157">**kanalen**</span><span class="sxs-lookup"><span data-stu-id="33de0-157">**channel**</span></span><br/><span data-ttu-id="33de0-158">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="33de0-158">**customerTenantId**</span></span><br/><span data-ttu-id="33de0-159">**customerName**</span><span class="sxs-lookup"><span data-stu-id="33de0-159">**customerName**</span></span><br/><span data-ttu-id="33de0-160">**productId**</span><span class="sxs-lookup"><span data-stu-id="33de0-160">**productId**</span></span><br/><span data-ttu-id="33de0-161">**Product**</span><span class="sxs-lookup"><span data-stu-id="33de0-161">**productName**</span></span><br/><br/> <span data-ttu-id="33de0-162">De geretourneerde gegevens rijen bevatten de velden die zijn opgegeven in de para meter *GroupBy* , evenals de volgende:</span><span class="sxs-lookup"><span data-stu-id="33de0-162">The returned data rows will contain the fields specified in the *groupby* parameter as well as the following:</span></span><br/><br/><span data-ttu-id="33de0-163">**licensesDeployed**</span><span class="sxs-lookup"><span data-stu-id="33de0-163">**licensesDeployed**</span></span><br/><span data-ttu-id="33de0-164">**licensesSold**</span><span class="sxs-lookup"><span data-stu-id="33de0-164">**licensesSold**</span></span>  | <span data-ttu-id="33de0-165">No</span><span class="sxs-lookup"><span data-stu-id="33de0-165">No</span></span> |
| <span data-ttu-id="33de0-166">processedDateTime</span><span class="sxs-lookup"><span data-stu-id="33de0-166">processedDateTime</span></span> | <span data-ttu-id="33de0-167">DateTime</span><span class="sxs-lookup"><span data-stu-id="33de0-167">DateTime</span></span> | <span data-ttu-id="33de0-168">De ene kan de datum opgeven waarop de gebruiks gegevens zijn verwerkt.</span><span class="sxs-lookup"><span data-stu-id="33de0-168">One can specify the date from which usage data was processed.</span></span> <span data-ttu-id="33de0-169">Wordt standaard ingesteld op de laatste datum waarop de gegevens zijn verwerkt</span><span class="sxs-lookup"><span data-stu-id="33de0-169">Defaults to the latest date when the data was processed</span></span> | <span data-ttu-id="33de0-170">No</span><span class="sxs-lookup"><span data-stu-id="33de0-170">No</span></span> |

### <a name="request-example"></a><span data-ttu-id="33de0-171">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="33de0-171">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/deployment/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="33de0-172">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="33de0-172">REST response</span></span>

<span data-ttu-id="33de0-173">Als dit lukt, bevat de antwoord tekst de volgende velden met gegevens over de geïmplementeerde licenties.</span><span class="sxs-lookup"><span data-stu-id="33de0-173">If successful, the response body contains the following fields containing data about the licenses deployed.</span></span>

| <span data-ttu-id="33de0-174">Veld</span><span class="sxs-lookup"><span data-stu-id="33de0-174">Field</span></span>             | <span data-ttu-id="33de0-175">Type</span><span class="sxs-lookup"><span data-stu-id="33de0-175">Type</span></span>     | <span data-ttu-id="33de0-176">Description</span><span class="sxs-lookup"><span data-stu-id="33de0-176">Description</span></span>                           |
|-------------------|----------|---------------------------------------|
| <span data-ttu-id="33de0-177">serviceCode</span><span class="sxs-lookup"><span data-stu-id="33de0-177">serviceCode</span></span>       | <span data-ttu-id="33de0-178">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="33de0-178">string</span></span>   | <span data-ttu-id="33de0-179">Service code</span><span class="sxs-lookup"><span data-stu-id="33de0-179">Service code</span></span>                          |
| <span data-ttu-id="33de0-180">serviceName</span><span class="sxs-lookup"><span data-stu-id="33de0-180">serviceName</span></span>       | <span data-ttu-id="33de0-181">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="33de0-181">string</span></span>   | <span data-ttu-id="33de0-182">Servicenaam</span><span class="sxs-lookup"><span data-stu-id="33de0-182">Service name</span></span>                          |
| <span data-ttu-id="33de0-183">kanalen</span><span class="sxs-lookup"><span data-stu-id="33de0-183">channel</span></span>           | <span data-ttu-id="33de0-184">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="33de0-184">string</span></span>   | <span data-ttu-id="33de0-185">Kanaal naam, wederverkoper</span><span class="sxs-lookup"><span data-stu-id="33de0-185">Channel name, reseller</span></span>                |
| <span data-ttu-id="33de0-186">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="33de0-186">customerTenantId</span></span>  | <span data-ttu-id="33de0-187">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="33de0-187">string</span></span>   | <span data-ttu-id="33de0-188">De unieke id voor de klant</span><span class="sxs-lookup"><span data-stu-id="33de0-188">Unique identifier for the customer</span></span>    |
| <span data-ttu-id="33de0-189">customerName</span><span class="sxs-lookup"><span data-stu-id="33de0-189">customerName</span></span>      | <span data-ttu-id="33de0-190">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="33de0-190">string</span></span>   | <span data-ttu-id="33de0-191">Klantnaam</span><span class="sxs-lookup"><span data-stu-id="33de0-191">Customer name</span></span>                         |
| <span data-ttu-id="33de0-192">productId</span><span class="sxs-lookup"><span data-stu-id="33de0-192">productId</span></span>         | <span data-ttu-id="33de0-193">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="33de0-193">string</span></span>   | <span data-ttu-id="33de0-194">De unieke id voor het product</span><span class="sxs-lookup"><span data-stu-id="33de0-194">Unique identifier for the product</span></span>     |
| <span data-ttu-id="33de0-195">Product</span><span class="sxs-lookup"><span data-stu-id="33de0-195">productName</span></span>       | <span data-ttu-id="33de0-196">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="33de0-196">string</span></span>   | <span data-ttu-id="33de0-197">Productnaam</span><span class="sxs-lookup"><span data-stu-id="33de0-197">Product name</span></span>                          |
| <span data-ttu-id="33de0-198">licensesDeployed</span><span class="sxs-lookup"><span data-stu-id="33de0-198">licensesDeployed</span></span>  | <span data-ttu-id="33de0-199">long</span><span class="sxs-lookup"><span data-stu-id="33de0-199">long</span></span>     | <span data-ttu-id="33de0-200">Aantal geïmplementeerde licenties</span><span class="sxs-lookup"><span data-stu-id="33de0-200">Number of licenses deployed</span></span>           |
| <span data-ttu-id="33de0-201">licensesSold</span><span class="sxs-lookup"><span data-stu-id="33de0-201">licensesSold</span></span>      | <span data-ttu-id="33de0-202">long</span><span class="sxs-lookup"><span data-stu-id="33de0-202">long</span></span>     | <span data-ttu-id="33de0-203">Aantal verkochte licenties</span><span class="sxs-lookup"><span data-stu-id="33de0-203">Number of licenses sold</span></span>               |
| <span data-ttu-id="33de0-204">processedDateTime</span><span class="sxs-lookup"><span data-stu-id="33de0-204">processedDateTime</span></span> | <span data-ttu-id="33de0-205">DateTime</span><span class="sxs-lookup"><span data-stu-id="33de0-205">DateTime</span></span> | <span data-ttu-id="33de0-206">Datum waarop de gegevens voor het laatst zijn verwerkt</span><span class="sxs-lookup"><span data-stu-id="33de0-206">Date when the data was last processed</span></span> |

### <a name="response-success-and-error-codes"></a><span data-ttu-id="33de0-207">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="33de0-207">Response success and error codes</span></span>

<span data-ttu-id="33de0-208">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="33de0-208">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="33de0-209">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="33de0-209">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="33de0-210">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="33de0-210">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="33de0-211">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="33de0-211">Response example</span></span>

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
      "serviceCode": "crm",
      "serviceName": "Microsoft Dynamics",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "54B84594-9C77-4499-8D65-5E0D5F410E78",
      "productName": "DYNAMICS AX TASK",
      "licensesDeployed": 0,
      "licensesSold": 9
    },
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "D3B4FE1F-9992-4930-8ACB-CA6EC609365E",
      "productName": "DOMESTIC AND INTERNATIONAL CALLING PLAN",
      "licensesDeployed": 0,
      "licensesSold": 5
    }
],
  "@nextLink": null,
  "TotalCount": 2
}
```
