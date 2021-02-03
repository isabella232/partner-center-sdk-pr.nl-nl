---
title: Alle gebruiksanalysegegevens van Azure ophalen
description: Alle informatie over Azure Usage Analytics ophalen.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: c281dcdeb93771a69a388ad64e1127b24156c809
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767408"
---
# <a name="get-all-azure-usage-analytics-information"></a><span data-ttu-id="abe5e-103">Alle gebruiksanalysegegevens van Azure ophalen</span><span class="sxs-lookup"><span data-stu-id="abe5e-103">Get all Azure usage analytics information</span></span>

<span data-ttu-id="abe5e-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="abe5e-104">**Applies To**</span></span>

- <span data-ttu-id="abe5e-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="abe5e-105">Partner Center</span></span>
- <span data-ttu-id="abe5e-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="abe5e-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="abe5e-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="abe5e-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="abe5e-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="abe5e-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="abe5e-109">Hoe u alle informatie over Azure Usage Analytics kunt verkrijgen voor uw klanten.</span><span class="sxs-lookup"><span data-stu-id="abe5e-109">How to get all the Azure usage analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="abe5e-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="abe5e-110">Prerequisites</span></span>

- <span data-ttu-id="abe5e-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="abe5e-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="abe5e-112">Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="abe5e-112">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="abe5e-113">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="abe5e-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="abe5e-114">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="abe5e-114">Request syntax</span></span>

| <span data-ttu-id="abe5e-115">Methode</span><span class="sxs-lookup"><span data-stu-id="abe5e-115">Method</span></span>  | <span data-ttu-id="abe5e-116">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="abe5e-116">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="abe5e-117">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="abe5e-117">**GET**</span></span> | <span data-ttu-id="abe5e-118">[*\{ BASEURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/Usage/Azure http/1.1</span><span class="sxs-lookup"><span data-stu-id="abe5e-118">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/usage/azure HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="abe5e-119">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="abe5e-119">URI parameters</span></span>

|<span data-ttu-id="abe5e-120">Parameter</span><span class="sxs-lookup"><span data-stu-id="abe5e-120">Parameter</span></span>        |<span data-ttu-id="abe5e-121">Type</span><span class="sxs-lookup"><span data-stu-id="abe5e-121">Type</span></span>                        |<span data-ttu-id="abe5e-122">Description</span><span class="sxs-lookup"><span data-stu-id="abe5e-122">Description</span></span>               |
|:----------------|:---------------------------|:-------------------------|
|<span data-ttu-id="abe5e-123">top</span><span class="sxs-lookup"><span data-stu-id="abe5e-123">top</span></span>              | <span data-ttu-id="abe5e-124">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="abe5e-124">string</span></span>                     | <span data-ttu-id="abe5e-125">Het aantal rijen met gegevens dat in de aanvraag moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="abe5e-125">The number of rows of data to return in the request.</span></span> <span data-ttu-id="abe5e-126">De maximum waarde en de standaard waarde als niet wordt opgegeven, zijn 10000.</span><span class="sxs-lookup"><span data-stu-id="abe5e-126">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="abe5e-127">Als er meer rijen in de query staan, bevat de antwoord tekst een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="abe5e-127">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span>                        |
|<span data-ttu-id="abe5e-128">skip</span><span class="sxs-lookup"><span data-stu-id="abe5e-128">skip</span></span>             | <span data-ttu-id="abe5e-129">int</span><span class="sxs-lookup"><span data-stu-id="abe5e-129">int</span></span>                        | <span data-ttu-id="abe5e-130">Het aantal rijen dat in de query moet worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="abe5e-130">The number of rows to skip in the query.</span></span> <span data-ttu-id="abe5e-131">Gebruik deze para meter om door grote gegevens sets te bladeren.</span><span class="sxs-lookup"><span data-stu-id="abe5e-131">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="abe5e-132">Zo `top=10000 and skip=0` haalt de eerste 10000 rijen met gegevens op, `top=10000 and skip=10000` haalt de volgende 10000 rijen met gegevens op, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="abe5e-132">For example, `top=10000 and skip=0` retrieves the first 10000 rows of data, `top=10000 and skip=10000` retrieves the next 10000 rows of data, and so on.</span></span>                       |
|<span data-ttu-id="abe5e-133">filter</span><span class="sxs-lookup"><span data-stu-id="abe5e-133">filter</span></span>           | <span data-ttu-id="abe5e-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="abe5e-134">string</span></span>                     | <span data-ttu-id="abe5e-135">De *filter* parameter van de aanvraag bevat een of meer instructies waarmee de rijen in het antwoord worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="abe5e-135">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="abe5e-136">Elke instructie bevat een veld en waarde die zijn gekoppeld aan de `eq` or `ne` -Opera tors en instructies kunnen worden gecombineerd met `and` of `or` .</span><span class="sxs-lookup"><span data-stu-id="abe5e-136">Each statement contains a field and value that are associated with the `eq` or `ne` operators, and statements can be combined using `and` or `or`.</span></span> <span data-ttu-id="abe5e-137">U kunt de volgende teken reeksen opgeven:</span><span class="sxs-lookup"><span data-stu-id="abe5e-137">You can specify the following strings:</span></span><br/><br/>                                                       `customerTenantId`<br/> `customerName`<br/> `subscriptionId`<br/> `subscriptionName`<br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/><span data-ttu-id="abe5e-138">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="abe5e-138">**Example:**</span></span><br/> `.../usage/azure?filter=meterCategory eq 'Data Management'`<br/><br/> <span data-ttu-id="abe5e-139">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="abe5e-139">**Example:**</span></span><br/>`.../usage/azure?filter=meterCategory eq 'Data Management' or (usageDate le cast('2018-01-01', Edm.DateTimeOffset) and usageDate le cast('2018-04-01', Edm.DateTimeOffset))`                        |
|<span data-ttu-id="abe5e-140">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="abe5e-140">aggregationLevel</span></span> | <span data-ttu-id="abe5e-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="abe5e-141">string</span></span>                    | <span data-ttu-id="abe5e-142">Hiermee geeft u het tijds bereik op waarvoor u de samengevoegde gegevens wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="abe5e-142">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="abe5e-143">Dit kan een van de volgende teken reeksen zijn: `day` , `week` of `month` .</span><span class="sxs-lookup"><span data-stu-id="abe5e-143">Can be one of the following strings: `day`, `week`, or `month`.</span></span> <span data-ttu-id="abe5e-144">Als u dit niet opgeeft, wordt de standaard waarde `day` .</span><span class="sxs-lookup"><span data-stu-id="abe5e-144">If unspecified, the default is `day`.</span></span><br/><br/>                                              <span data-ttu-id="abe5e-145">De `aggregationLevel` para meter wordt niet ondersteund zonder een `groupby` .</span><span class="sxs-lookup"><span data-stu-id="abe5e-145">The `aggregationLevel` parameter isn't supported without a `groupby`.</span></span> <span data-ttu-id="abe5e-146">De `aggregationLevel` para meter is van toepassing op alle datum velden in de `groupby` .</span><span class="sxs-lookup"><span data-stu-id="abe5e-146">The `aggregationLevel` parameter applies to all date fields present in the `groupby`.</span></span>                                                      |
|<span data-ttu-id="abe5e-147">OrderBy</span><span class="sxs-lookup"><span data-stu-id="abe5e-147">orderby</span></span>          |<span data-ttu-id="abe5e-148">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="abe5e-148">string</span></span>                     | <span data-ttu-id="abe5e-149">Een instructie waarmee de resultaat gegevens voor elke installatie worden gesorteerd.</span><span class="sxs-lookup"><span data-stu-id="abe5e-149">A statement that orders the result data values for each install.</span></span> <span data-ttu-id="abe5e-150">De syntaxis is `...&orderby=field [order],field [order],...`.</span><span class="sxs-lookup"><span data-stu-id="abe5e-150">The syntax is `...&orderby=field [order],field [order],...`.</span></span> <span data-ttu-id="abe5e-151">De `field` para meter kan een van de volgende teken reeksen zijn:</span><span class="sxs-lookup"><span data-stu-id="abe5e-151">The `field` parameter can be one of the following strings:</span></span><br/><br/>                    `customerTenantId`<br/>`customerName`<br/>`subscriptionId`<br/>`subscriptionName`<br/>`usageDate`<br/>`resourceLocation`<br/>`meterCategory`<br/>`meterSubcategory`<br/>`meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/> <span data-ttu-id="abe5e-152">De *volg orde* van de para meters is optioneel en kan worden `asc` `desc` opgegeven of om respectievelijk een oplopende of aflopende volg orde voor elk veld op te geven.</span><span class="sxs-lookup"><span data-stu-id="abe5e-152">The *order* parameter is optional and can be `asc` or `desc` to specify ascending or descending order for each field, respectively.</span></span> <span data-ttu-id="abe5e-153">De standaardwaarde is `asc`.</span><span class="sxs-lookup"><span data-stu-id="abe5e-153">The default is `asc`.</span></span><br/><br/><span data-ttu-id="abe5e-154">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="abe5e-154">**Example:**</span></span><br/> `...&orderby=meterCategory,meterUnit`                                                                                           |
|<span data-ttu-id="abe5e-155">GroupBy</span><span class="sxs-lookup"><span data-stu-id="abe5e-155">groupby</span></span>          |<span data-ttu-id="abe5e-156">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="abe5e-156">string</span></span>                    | <span data-ttu-id="abe5e-157">Een instructie die alleen gegevens aggregatie toepast op de opgegeven velden.</span><span class="sxs-lookup"><span data-stu-id="abe5e-157">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="abe5e-158">U kunt de volgende velden opgeven:</span><span class="sxs-lookup"><span data-stu-id="abe5e-158">You can specify the following fields:</span></span><br/><br/>                                                                                                                     `customerTenantId`<br/>`customerName`<br/> `subscriptionId` <br/> `subscriptionName` <br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit` <br/> `reservationOrderId` <br/> `reservationId` <br/> `consumptionMeterId` <br/> `serviceType` <br/><br/><span data-ttu-id="abe5e-159">De geretourneerde gegevens rijen bevatten de velden die zijn opgegeven in de `groupby`  para meter en de *hoeveelheid*.</span><span class="sxs-lookup"><span data-stu-id="abe5e-159">The returned data rows will contain the fields specified in the `groupby`  parameter as well as the *Quantity*.</span></span><br/><br/><span data-ttu-id="abe5e-160">De `groupby` para meter kan worden gebruikt met de `aggregationLevel` para meter.</span><span class="sxs-lookup"><span data-stu-id="abe5e-160">The `groupby` parameter can be used with the `aggregationLevel` parameter.</span></span><br/><br/><span data-ttu-id="abe5e-161">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="abe5e-161">**Example:**</span></span><br/>`...&groupby=meterCategory,meterUnit` |

### <a name="request-headers"></a><span data-ttu-id="abe5e-162">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="abe5e-162">Request headers</span></span>

<span data-ttu-id="abe5e-163">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="abe5e-163">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="abe5e-164">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="abe5e-164">Request body</span></span>

<span data-ttu-id="abe5e-165">Geen.</span><span class="sxs-lookup"><span data-stu-id="abe5e-165">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="abe5e-166">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="abe5e-166">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/usage/azure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="abe5e-167">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="abe5e-167">REST response</span></span>

<span data-ttu-id="abe5e-168">Als dit lukt, bevat de antwoord tekst een verzameling [Azure-gebruiks](partner-center-analytics-resources.md#csp-program-azure-usage-analytics) resources.</span><span class="sxs-lookup"><span data-stu-id="abe5e-168">If successful, the response body contains a collection of [Azure usage](partner-center-analytics-resources.md#csp-program-azure-usage-analytics) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="abe5e-169">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="abe5e-169">Response success and error codes</span></span>

<span data-ttu-id="abe5e-170">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="abe5e-170">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="abe5e-171">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="abe5e-171">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="abe5e-172">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="abe5e-172">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="abe5e-173">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="abe5e-173">Response example</span></span>

```http
{
  "customerTenantId": "39A1DFAC-4969-4F31-AF94-D76588189CFE",
  "customerName": "A",
  "subscriptionId": "EC649980-D623-49F5-B7C1-80CC772B83A8",
  "subscriptionName": "AZURE PURCHSE SAMPLE APP",
  "usageDate": "2018-05-27T00:00:00",
  "resourceLocation": "useast",
  "meterCategory": "Data Management",
  "meterSubcategory": "None",
  "meterUnit": "10,000s",
  "reservationOrderId": "",
  "reservationId": "",
  "consumptionMeterId": "",
  "serviceType": "",
  "quantity": 20
}
```

## <a name="see-also"></a><span data-ttu-id="abe5e-174">Zie ook</span><span class="sxs-lookup"><span data-stu-id="abe5e-174">See also</span></span>

- [<span data-ttu-id="abe5e-175">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="abe5e-175">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
