---
title: Alle gebruiksanalysegegevens van Azure ophalen
description: Informatie over het verkrijgen van alle azure-gebruiksanalysegegevens.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 7fe987c7dc50d55b26cd72d5aead52963eb1cfbe
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760212"
---
# <a name="get-all-azure-usage-analytics-information"></a><span data-ttu-id="ad852-103">Alle gebruiksanalysegegevens van Azure ophalen</span><span class="sxs-lookup"><span data-stu-id="ad852-103">Get all Azure usage analytics information</span></span>

<span data-ttu-id="ad852-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ad852-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ad852-105">Informatie over het verkrijgen van alle Azure-gebruiksanalysegegevens voor uw klanten.</span><span class="sxs-lookup"><span data-stu-id="ad852-105">How to get all the Azure usage analytics information for your customers.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ad852-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ad852-106">Prerequisites</span></span>

- <span data-ttu-id="ad852-107">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="ad852-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ad852-108">Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="ad852-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="ad852-109">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ad852-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ad852-110">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="ad852-110">Request syntax</span></span>

| <span data-ttu-id="ad852-111">Methode</span><span class="sxs-lookup"><span data-stu-id="ad852-111">Method</span></span>  | <span data-ttu-id="ad852-112">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ad852-112">Request URI</span></span> |
|---------|-------------|
| <span data-ttu-id="ad852-113">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ad852-113">**GET**</span></span> | <span data-ttu-id="ad852-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/usage/azure HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ad852-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/usage/azure HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="ad852-115">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="ad852-115">URI parameters</span></span>

|<span data-ttu-id="ad852-116">Parameter</span><span class="sxs-lookup"><span data-stu-id="ad852-116">Parameter</span></span>        |<span data-ttu-id="ad852-117">Type</span><span class="sxs-lookup"><span data-stu-id="ad852-117">Type</span></span>                        |<span data-ttu-id="ad852-118">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ad852-118">Description</span></span>               |
|:----------------|:---------------------------|:-------------------------|
|<span data-ttu-id="ad852-119">top</span><span class="sxs-lookup"><span data-stu-id="ad852-119">top</span></span>              | <span data-ttu-id="ad852-120">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ad852-120">string</span></span>                     | <span data-ttu-id="ad852-121">Het aantal rijen met gegevens dat in de aanvraag moet worden retourneren.</span><span class="sxs-lookup"><span data-stu-id="ad852-121">The number of rows of data to return in the request.</span></span> <span data-ttu-id="ad852-122">De maximumwaarde en de standaardwaarde als deze niet is opgegeven, is 10000.</span><span class="sxs-lookup"><span data-stu-id="ad852-122">The maximum value and the default value if not specified is 10000.</span></span> <span data-ttu-id="ad852-123">Als er meer rijen in de query staan, bevat de antwoord-body een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="ad852-123">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span>                        |
|<span data-ttu-id="ad852-124">skip</span><span class="sxs-lookup"><span data-stu-id="ad852-124">skip</span></span>             | <span data-ttu-id="ad852-125">int</span><span class="sxs-lookup"><span data-stu-id="ad852-125">int</span></span>                        | <span data-ttu-id="ad852-126">Het aantal rijen dat moet worden overgeslagen in de query.</span><span class="sxs-lookup"><span data-stu-id="ad852-126">The number of rows to skip in the query.</span></span> <span data-ttu-id="ad852-127">Gebruik deze parameter om door grote gegevenssets te gaan.</span><span class="sxs-lookup"><span data-stu-id="ad852-127">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="ad852-128">Haalt bijvoorbeeld de eerste 10000 rijen met gegevens op, haalt de volgende `top=10000 and skip=0` 10000 rijen met gegevens `top=10000 and skip=10000` op, en meer.</span><span class="sxs-lookup"><span data-stu-id="ad852-128">For example, `top=10000 and skip=0` retrieves the first 10000 rows of data, `top=10000 and skip=10000` retrieves the next 10000 rows of data, and so on.</span></span>                       |
|<span data-ttu-id="ad852-129">filter</span><span class="sxs-lookup"><span data-stu-id="ad852-129">filter</span></span>           | <span data-ttu-id="ad852-130">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ad852-130">string</span></span>                     | <span data-ttu-id="ad852-131">De *filterparameter* van de aanvraag bevat een of meer instructies die de rijen in het antwoord filteren.</span><span class="sxs-lookup"><span data-stu-id="ad852-131">The *filter* parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="ad852-132">Elke instructie bevat een veld en waarde die zijn gekoppeld aan de operators of en instructies `eq` kunnen worden gecombineerd met behulp van of `ne` `and` `or` .</span><span class="sxs-lookup"><span data-stu-id="ad852-132">Each statement contains a field and value that are associated with the `eq` or `ne` operators, and statements can be combined using `and` or `or`.</span></span> <span data-ttu-id="ad852-133">U kunt de volgende tekenreeksen opgeven:</span><span class="sxs-lookup"><span data-stu-id="ad852-133">You can specify the following strings:</span></span><br/><br/>                                                       `customerTenantId`<br/> `customerName`<br/> `subscriptionId`<br/> `subscriptionName`<br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/><span data-ttu-id="ad852-134">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="ad852-134">**Example:**</span></span><br/> `.../usage/azure?filter=meterCategory eq 'Data Management'`<br/><br/> <span data-ttu-id="ad852-135">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="ad852-135">**Example:**</span></span><br/>`.../usage/azure?filter=meterCategory eq 'Data Management' or (usageDate le cast('2018-01-01', Edm.DateTimeOffset) and usageDate le cast('2018-04-01', Edm.DateTimeOffset))`                        |
|<span data-ttu-id="ad852-136">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="ad852-136">aggregationLevel</span></span> | <span data-ttu-id="ad852-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ad852-137">string</span></span>                    | <span data-ttu-id="ad852-138">Hiermee geeft u het tijdsbereik op waarvoor geaggregeerde gegevens moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="ad852-138">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="ad852-139">Kan een van de volgende tekenreeksen zijn: `day` `week` , of `month` .</span><span class="sxs-lookup"><span data-stu-id="ad852-139">Can be one of the following strings: `day`, `week`, or `month`.</span></span> <span data-ttu-id="ad852-140">Als dit niet is gespecificeerd, is de standaardwaarde `day` .</span><span class="sxs-lookup"><span data-stu-id="ad852-140">If unspecified, the default is `day`.</span></span><br/><br/>                                              <span data-ttu-id="ad852-141">De `aggregationLevel` parameter wordt niet ondersteund zonder een `groupby` .</span><span class="sxs-lookup"><span data-stu-id="ad852-141">The `aggregationLevel` parameter isn't supported without a `groupby`.</span></span> <span data-ttu-id="ad852-142">De `aggregationLevel` parameter is van toepassing op alle datumvelden die aanwezig zijn in de `groupby` .</span><span class="sxs-lookup"><span data-stu-id="ad852-142">The `aggregationLevel` parameter applies to all date fields present in the `groupby`.</span></span>                                                      |
|<span data-ttu-id="ad852-143">Orderby</span><span class="sxs-lookup"><span data-stu-id="ad852-143">orderby</span></span>          |<span data-ttu-id="ad852-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ad852-144">string</span></span>                     | <span data-ttu-id="ad852-145">Een instructie die de resultaatgegevenswaarden voor elke installatie bestelt.</span><span class="sxs-lookup"><span data-stu-id="ad852-145">A statement that orders the result data values for each install.</span></span> <span data-ttu-id="ad852-146">De syntaxis is `...&orderby=field [order],field [order],...`.</span><span class="sxs-lookup"><span data-stu-id="ad852-146">The syntax is `...&orderby=field [order],field [order],...`.</span></span> <span data-ttu-id="ad852-147">De `field` parameter kan een van de volgende tekenreeksen zijn:</span><span class="sxs-lookup"><span data-stu-id="ad852-147">The `field` parameter can be one of the following strings:</span></span><br/><br/>                    `customerTenantId`<br/>`customerName`<br/>`subscriptionId`<br/>`subscriptionName`<br/>`usageDate`<br/>`resourceLocation`<br/>`meterCategory`<br/>`meterSubcategory`<br/>`meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/> <span data-ttu-id="ad852-148">De *orderparameter* is optioneel en kan of zijn om respectievelijk de oplopende of aflopende volgorde voor `asc` elk veld op te `desc` geven.</span><span class="sxs-lookup"><span data-stu-id="ad852-148">The *order* parameter is optional and can be `asc` or `desc` to specify ascending or descending order for each field, respectively.</span></span> <span data-ttu-id="ad852-149">De standaardwaarde is `asc`.</span><span class="sxs-lookup"><span data-stu-id="ad852-149">The default is `asc`.</span></span><br/><br/><span data-ttu-id="ad852-150">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="ad852-150">**Example:**</span></span><br/> `...&orderby=meterCategory,meterUnit`                                                                                           |
|<span data-ttu-id="ad852-151">groupby</span><span class="sxs-lookup"><span data-stu-id="ad852-151">groupby</span></span>          |<span data-ttu-id="ad852-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ad852-152">string</span></span>                    | <span data-ttu-id="ad852-153">Een instructie die gegevensaggregatie alleen op de opgegeven velden van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="ad852-153">A statement that applies data aggregation only to the specified fields.</span></span> <span data-ttu-id="ad852-154">U kunt de volgende velden opgeven:</span><span class="sxs-lookup"><span data-stu-id="ad852-154">You can specify the following fields:</span></span><br/><br/>                                                                                                                     `customerTenantId`<br/>`customerName`<br/> `subscriptionId` <br/> `subscriptionName` <br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit` <br/> `reservationOrderId` <br/> `reservationId` <br/> `consumptionMeterId` <br/> `serviceType` <br/><br/><span data-ttu-id="ad852-155">De geretourneerde gegevensrijen bevatten de velden die zijn opgegeven in de `groupby`  parameter en de *Hoeveelheid*.</span><span class="sxs-lookup"><span data-stu-id="ad852-155">The returned data rows will contain the fields specified in the `groupby`  parameter and the *Quantity*.</span></span><br/><br/><span data-ttu-id="ad852-156">De `groupby` parameter kan worden gebruikt met de parameter `aggregationLevel` .</span><span class="sxs-lookup"><span data-stu-id="ad852-156">The `groupby` parameter can be used with the `aggregationLevel` parameter.</span></span><br/><br/><span data-ttu-id="ad852-157">**Voorbeeld:**</span><span class="sxs-lookup"><span data-stu-id="ad852-157">**Example:**</span></span><br/>`...&groupby=meterCategory,meterUnit` |

### <a name="request-headers"></a><span data-ttu-id="ad852-158">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ad852-158">Request headers</span></span>

<span data-ttu-id="ad852-159">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="ad852-159">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ad852-160">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ad852-160">Request body</span></span>

<span data-ttu-id="ad852-161">Geen.</span><span class="sxs-lookup"><span data-stu-id="ad852-161">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ad852-162">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ad852-162">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/usage/azure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="ad852-163">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ad852-163">REST response</span></span>

<span data-ttu-id="ad852-164">Als dit lukt, bevat de antwoord-body een verzameling [Azure-gebruiksresources.](partner-center-analytics-resources.md#csp-program-azure-usage-analytics)</span><span class="sxs-lookup"><span data-stu-id="ad852-164">If successful, the response body contains a collection of [Azure usage](partner-center-analytics-resources.md#csp-program-azure-usage-analytics) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ad852-165">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="ad852-165">Response success and error codes</span></span>

<span data-ttu-id="ad852-166">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="ad852-166">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ad852-167">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ad852-167">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ad852-168">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="ad852-168">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ad852-169">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ad852-169">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ad852-170">Zie ook</span><span class="sxs-lookup"><span data-stu-id="ad852-170">See also</span></span>

- [<span data-ttu-id="ad852-171">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="ad852-171">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
