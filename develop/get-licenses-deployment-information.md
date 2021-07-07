---
title: Implementatiegegevens van licenties ophalen
description: Informatie over de implementatie van Office en Dynamics-licenties.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9eb0dc655affb2216b11635e58e00ed6464d6792
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445660"
---
# <a name="get-licenses-deployment-information"></a><span data-ttu-id="fdb0f-103">Implementatiegegevens van licenties ophalen</span><span class="sxs-lookup"><span data-stu-id="fdb0f-103">Get licenses deployment information</span></span>

<span data-ttu-id="fdb0f-104">Informatie over de implementatie van Office en Dynamics-licenties.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-104">How to get deployment information for Office and Dynamics licenses.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fdb0f-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fdb0f-105">Prerequisites</span></span>

<span data-ttu-id="fdb0f-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fdb0f-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fdb0f-107">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-107">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="fdb0f-108">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fdb0f-108">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fdb0f-109">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="fdb0f-109">Request syntax</span></span>

| <span data-ttu-id="fdb0f-110">Methode</span><span class="sxs-lookup"><span data-stu-id="fdb0f-110">Method</span></span>  | <span data-ttu-id="fdb0f-111">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fdb0f-111">Request URI</span></span>                                                                                     |
|---------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fdb0f-112">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-112">**GET**</span></span> | <span data-ttu-id="fdb0f-113">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/deployment/license/ HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fdb0f-113">[*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/deployment/license/ HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fdb0f-114">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fdb0f-114">Request headers</span></span>

<span data-ttu-id="fdb0f-115">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="fdb0f-115">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="uri-parameters"></a><span data-ttu-id="fdb0f-116">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="fdb0f-116">URI parameters</span></span>

| <span data-ttu-id="fdb0f-117">Parameter</span><span class="sxs-lookup"><span data-stu-id="fdb0f-117">Parameter</span></span>         | <span data-ttu-id="fdb0f-118">Type</span><span class="sxs-lookup"><span data-stu-id="fdb0f-118">Type</span></span>     | <span data-ttu-id="fdb0f-119">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fdb0f-119">Description</span></span> | <span data-ttu-id="fdb0f-120">Vereist</span><span class="sxs-lookup"><span data-stu-id="fdb0f-120">Required</span></span> |
|-------------------|----------|-------------|----------|
| <span data-ttu-id="fdb0f-121">top</span><span class="sxs-lookup"><span data-stu-id="fdb0f-121">top</span></span>               | <span data-ttu-id="fdb0f-122">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb0f-122">string</span></span>   | <span data-ttu-id="fdb0f-123">Het aantal rijen met gegevens dat in de aanvraag moet worden retourneren.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-123">The number of rows of data to return in the request.</span></span> <span data-ttu-id="fdb0f-124">De maximumwaarde en de standaardwaarde als deze niet is opgegeven, is 10.000.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-124">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="fdb0f-125">Als er meer rijen in de query staan, bevat de hoofdpagina van het antwoord een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-125">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> | <span data-ttu-id="fdb0f-126">Nee</span><span class="sxs-lookup"><span data-stu-id="fdb0f-126">No</span></span> |
| <span data-ttu-id="fdb0f-127">skip</span><span class="sxs-lookup"><span data-stu-id="fdb0f-127">skip</span></span>              | <span data-ttu-id="fdb0f-128">int</span><span class="sxs-lookup"><span data-stu-id="fdb0f-128">int</span></span>      | <span data-ttu-id="fdb0f-129">Het aantal rijen dat moet worden overgeslagen in de query.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-129">The number of rows to skip in the query.</span></span> <span data-ttu-id="fdb0f-130">Gebruik deze parameter om grote gegevenssets te bekijken.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-130">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="fdb0f-131">Top=10000 en skip=0 haalt bijvoorbeeld de eerste 10000 rijen met gegevens op, top=10000 en skip=10000 haalt de volgende 10000 rijen met gegevens op, bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-131">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data, and so on.</span></span> | <span data-ttu-id="fdb0f-132">Nee</span><span class="sxs-lookup"><span data-stu-id="fdb0f-132">No</span></span> |
| <span data-ttu-id="fdb0f-133">filter</span><span class="sxs-lookup"><span data-stu-id="fdb0f-133">filter</span></span>            | <span data-ttu-id="fdb0f-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb0f-134">string</span></span>   | <span data-ttu-id="fdb0f-135">De *filterparameter* van de aanvraag bevat een of meer instructies die de rijen in het antwoord filteren.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-135">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="fdb0f-136">Elke instructie bevat een veld en waarde die zijn gekoppeld aan de operators of en instructies `eq` kunnen worden gecombineerd met of `ne` `and` `or` .</span><span class="sxs-lookup"><span data-stu-id="fdb0f-136">Each statement contains a field and value that are associated with the `eq` or `ne` operators, and statements can be combined using `and` or `or`.</span></span> <span data-ttu-id="fdb0f-137">Hier volgen enkele *voorbeeldfilterparameters:*</span><span class="sxs-lookup"><span data-stu-id="fdb0f-137">Here are some example *filter* parameters:</span></span><br/><br/> <span data-ttu-id="fdb0f-138">*filter=serviceCode eq 'O365'*</span><span class="sxs-lookup"><span data-stu-id="fdb0f-138">*filter=serviceCode eq 'O365'*</span></span><br/> <span data-ttu-id="fdb0f-139">*filter=serviceCode eq 'O365'* of (*kanaal eq 'Reseller'*)</span><span class="sxs-lookup"><span data-stu-id="fdb0f-139">*filter=serviceCode eq 'O365'* or (*channel eq 'Reseller'*)</span></span><br/><br/> <span data-ttu-id="fdb0f-140">U kunt de volgende velden opgeven:</span><span class="sxs-lookup"><span data-stu-id="fdb0f-140">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="fdb0f-141">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-141">**serviceCode**</span></span><br/><span data-ttu-id="fdb0f-142">**Servicenaam**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-142">**serviceName**</span></span><br/><span data-ttu-id="fdb0f-143">**Kanaal**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-143">**channel**</span></span><br/><span data-ttu-id="fdb0f-144">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-144">**customerTenantId**</span></span><br/><span data-ttu-id="fdb0f-145">**customerName**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-145">**customerName**</span></span><br/><span data-ttu-id="fdb0f-146">**Productid**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-146">**productId**</span></span><br/><span data-ttu-id="fdb0f-147">**Productnaam**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-147">**productName**</span></span>  | <span data-ttu-id="fdb0f-148">Nee</span><span class="sxs-lookup"><span data-stu-id="fdb0f-148">No</span></span> |
| <span data-ttu-id="fdb0f-149">groupby</span><span class="sxs-lookup"><span data-stu-id="fdb0f-149">groupby</span></span>           | <span data-ttu-id="fdb0f-150">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb0f-150">string</span></span>   | <span data-ttu-id="fdb0f-151">Een instructie die gegevensaggregatie alleen op de opgegeven velden van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-151">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="fdb0f-152">U kunt de volgende velden opgeven:</span><span class="sxs-lookup"><span data-stu-id="fdb0f-152">You can specify the following fields:</span></span><br/><br/><span data-ttu-id="fdb0f-153">**serviceCode**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-153">**serviceCode**</span></span><br/><span data-ttu-id="fdb0f-154">**Servicenaam**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-154">**serviceName**</span></span><br/><span data-ttu-id="fdb0f-155">**Kanaal**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-155">**channel**</span></span><br/><span data-ttu-id="fdb0f-156">**customerTenantId**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-156">**customerTenantId**</span></span><br/><span data-ttu-id="fdb0f-157">**customerName**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-157">**customerName**</span></span><br/><span data-ttu-id="fdb0f-158">**Productid**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-158">**productId**</span></span><br/><span data-ttu-id="fdb0f-159">**Productnaam**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-159">**productName**</span></span><br/><br/> <span data-ttu-id="fdb0f-160">De geretourneerde gegevensrijen bevatten de velden die zijn opgegeven in de *groupby-parameter* en het volgende:</span><span class="sxs-lookup"><span data-stu-id="fdb0f-160">The returned data rows will contain the fields specified in the *groupby* parameter and the following:</span></span><br/><br/><span data-ttu-id="fdb0f-161">**licenties Geïmplementeerd**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-161">**licensesDeployed**</span></span><br/><span data-ttu-id="fdb0f-162">**licentiesVerkocht**</span><span class="sxs-lookup"><span data-stu-id="fdb0f-162">**licensesSold**</span></span>  | <span data-ttu-id="fdb0f-163">Nee</span><span class="sxs-lookup"><span data-stu-id="fdb0f-163">No</span></span> |
| <span data-ttu-id="fdb0f-164">processedDateTime</span><span class="sxs-lookup"><span data-stu-id="fdb0f-164">processedDateTime</span></span> | <span data-ttu-id="fdb0f-165">DateTime</span><span class="sxs-lookup"><span data-stu-id="fdb0f-165">DateTime</span></span> | <span data-ttu-id="fdb0f-166">U kunt de datum opgeven vanaf welke gebruiksgegevens zijn verwerkt.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-166">One can specify the date from which usage data was processed.</span></span> <span data-ttu-id="fdb0f-167">De standaardwaarde is de laatste datum waarop de gegevens zijn verwerkt</span><span class="sxs-lookup"><span data-stu-id="fdb0f-167">Defaults to the latest date when the data was processed</span></span> | <span data-ttu-id="fdb0f-168">Nee</span><span class="sxs-lookup"><span data-stu-id="fdb0f-168">No</span></span> |

### <a name="request-example"></a><span data-ttu-id="fdb0f-169">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fdb0f-169">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/deployment/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="fdb0f-170">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fdb0f-170">REST response</span></span>

<span data-ttu-id="fdb0f-171">Als dit lukt, bevat de antwoord-body de volgende velden met gegevens over de geïmplementeerde licenties.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-171">If successful, the response body contains the following fields containing data about the licenses deployed.</span></span>

| <span data-ttu-id="fdb0f-172">Veld</span><span class="sxs-lookup"><span data-stu-id="fdb0f-172">Field</span></span>             | <span data-ttu-id="fdb0f-173">Type</span><span class="sxs-lookup"><span data-stu-id="fdb0f-173">Type</span></span>     | <span data-ttu-id="fdb0f-174">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fdb0f-174">Description</span></span>                           |
|-------------------|----------|---------------------------------------|
| <span data-ttu-id="fdb0f-175">serviceCode</span><span class="sxs-lookup"><span data-stu-id="fdb0f-175">serviceCode</span></span>       | <span data-ttu-id="fdb0f-176">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb0f-176">string</span></span>   | <span data-ttu-id="fdb0f-177">Servicecode</span><span class="sxs-lookup"><span data-stu-id="fdb0f-177">Service code</span></span>                          |
| <span data-ttu-id="fdb0f-178">Servicenaam</span><span class="sxs-lookup"><span data-stu-id="fdb0f-178">serviceName</span></span>       | <span data-ttu-id="fdb0f-179">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb0f-179">string</span></span>   | <span data-ttu-id="fdb0f-180">Servicenaam</span><span class="sxs-lookup"><span data-stu-id="fdb0f-180">Service name</span></span>                          |
| <span data-ttu-id="fdb0f-181">Kanaal</span><span class="sxs-lookup"><span data-stu-id="fdb0f-181">channel</span></span>           | <span data-ttu-id="fdb0f-182">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb0f-182">string</span></span>   | <span data-ttu-id="fdb0f-183">Kanaalnaam, reseller</span><span class="sxs-lookup"><span data-stu-id="fdb0f-183">Channel name, reseller</span></span>                |
| <span data-ttu-id="fdb0f-184">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="fdb0f-184">customerTenantId</span></span>  | <span data-ttu-id="fdb0f-185">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb0f-185">string</span></span>   | <span data-ttu-id="fdb0f-186">Unieke id voor de klant</span><span class="sxs-lookup"><span data-stu-id="fdb0f-186">Unique identifier for the customer</span></span>    |
| <span data-ttu-id="fdb0f-187">customerName</span><span class="sxs-lookup"><span data-stu-id="fdb0f-187">customerName</span></span>      | <span data-ttu-id="fdb0f-188">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb0f-188">string</span></span>   | <span data-ttu-id="fdb0f-189">Klantnaam</span><span class="sxs-lookup"><span data-stu-id="fdb0f-189">Customer name</span></span>                         |
| <span data-ttu-id="fdb0f-190">productId</span><span class="sxs-lookup"><span data-stu-id="fdb0f-190">productId</span></span>         | <span data-ttu-id="fdb0f-191">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb0f-191">string</span></span>   | <span data-ttu-id="fdb0f-192">Unieke id voor het product</span><span class="sxs-lookup"><span data-stu-id="fdb0f-192">Unique identifier for the product</span></span>     |
| <span data-ttu-id="fdb0f-193">Productnaam</span><span class="sxs-lookup"><span data-stu-id="fdb0f-193">productName</span></span>       | <span data-ttu-id="fdb0f-194">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb0f-194">string</span></span>   | <span data-ttu-id="fdb0f-195">Productnaam</span><span class="sxs-lookup"><span data-stu-id="fdb0f-195">Product name</span></span>                          |
| <span data-ttu-id="fdb0f-196">licenties Geïmplementeerd</span><span class="sxs-lookup"><span data-stu-id="fdb0f-196">licensesDeployed</span></span>  | <span data-ttu-id="fdb0f-197">long</span><span class="sxs-lookup"><span data-stu-id="fdb0f-197">long</span></span>     | <span data-ttu-id="fdb0f-198">Aantal geïmplementeerde licenties</span><span class="sxs-lookup"><span data-stu-id="fdb0f-198">Number of licenses deployed</span></span>           |
| <span data-ttu-id="fdb0f-199">licentiesVerkocht</span><span class="sxs-lookup"><span data-stu-id="fdb0f-199">licensesSold</span></span>      | <span data-ttu-id="fdb0f-200">long</span><span class="sxs-lookup"><span data-stu-id="fdb0f-200">long</span></span>     | <span data-ttu-id="fdb0f-201">Aantal verkochte licenties</span><span class="sxs-lookup"><span data-stu-id="fdb0f-201">Number of licenses sold</span></span>               |
| <span data-ttu-id="fdb0f-202">processedDateTime</span><span class="sxs-lookup"><span data-stu-id="fdb0f-202">processedDateTime</span></span> | <span data-ttu-id="fdb0f-203">DateTime</span><span class="sxs-lookup"><span data-stu-id="fdb0f-203">DateTime</span></span> | <span data-ttu-id="fdb0f-204">De datum waarop de gegevens voor het laatst zijn verwerkt</span><span class="sxs-lookup"><span data-stu-id="fdb0f-204">Date when the data was last processed</span></span> |

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fdb0f-205">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="fdb0f-205">Response success and error codes</span></span>

<span data-ttu-id="fdb0f-206">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-206">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fdb0f-207">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fdb0f-207">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fdb0f-208">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="fdb0f-208">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fdb0f-209">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fdb0f-209">Response example</span></span>

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
