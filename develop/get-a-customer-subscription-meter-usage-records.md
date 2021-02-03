---
title: Gebruiksgegevens voor het abonnement per meter ophalen
description: U kunt de resource verzameling MeterUsageRecord gebruiken om gegevens over het gebruik van metingen van een klant voor specifieke Azure-Services of-resources tijdens de huidige facturerings periode op te halen.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: df981eae8d2caee2dcb7f36696725ec011ead75b
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767310"
---
# <a name="get-usage-data-for-subscription-by-meter"></a><span data-ttu-id="7f76c-103">Gebruiksgegevens voor het abonnement per meter ophalen</span><span class="sxs-lookup"><span data-stu-id="7f76c-103">Get usage data for subscription by meter</span></span>

<span data-ttu-id="7f76c-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="7f76c-104">**Applies to:**</span></span>

- <span data-ttu-id="7f76c-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="7f76c-105">Partner Center</span></span>
- <span data-ttu-id="7f76c-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="7f76c-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="7f76c-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7f76c-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7f76c-108">U kunt de resource verzameling **MeterUsageRecord** gebruiken om gegevens over het gebruik van metingen van een klant voor specifieke Azure-Services of-resources tijdens de huidige facturerings periode op te halen.</span><span class="sxs-lookup"><span data-stu-id="7f76c-108">You can use the **MeterUsageRecord** resource collection to get meter usage records of a customer for specific Azure services or resources during the current billing period.</span></span> <span data-ttu-id="7f76c-109">Deze resource verzameling vertegenwoordigt een samengevoegd totaal voor elke meter voor de huidige facturerings cyclus, in het hele Azure-abonnement.</span><span class="sxs-lookup"><span data-stu-id="7f76c-109">This resource collection represents an aggregated total for each meter for the current billing cycle, across your entire Azure plan.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f76c-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7f76c-110">Prerequisites</span></span>

- <span data-ttu-id="7f76c-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7f76c-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7f76c-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="7f76c-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="7f76c-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7f76c-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7f76c-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="7f76c-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7f76c-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="7f76c-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7f76c-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="7f76c-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7f76c-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="7f76c-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7f76c-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7f76c-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7f76c-119">Een abonnements-ID</span><span class="sxs-lookup"><span data-stu-id="7f76c-119">A subscription ID</span></span>

<span data-ttu-id="7f76c-120">*Deze nieuwe route is gelijk aan `subscriptions/{subscription-id}/usagerecords/resources` , die alleen zal blijven functioneren voor Microsoft Azure (MS-AZR-0145P)-abonnementen.*</span><span class="sxs-lookup"><span data-stu-id="7f76c-120">*This new route is equivalent to `subscriptions/{subscription-id}/usagerecords/resources`, which will continue to function only for Microsoft Azure (MS-AZR-0145P) subscriptions.*</span></span> <span data-ttu-id="7f76c-121">Deze nieuwe route ondersteunt zowel Microsoft Azure (MS-AZR-0145P)-abonnementen en Azure-plannen.</span><span class="sxs-lookup"><span data-stu-id="7f76c-121">This new route will support both Microsoft Azure (MS-AZR-0145P) subscriptions and Azure plans.</span></span> <span data-ttu-id="7f76c-122">Als u deze informatie wilt ophalen voor uw Azure-abonnement, moet u overschakelen naar deze nieuwe route.</span><span class="sxs-lookup"><span data-stu-id="7f76c-122">In order to get this information for your Azure plan, you need to switch to this new route.</span></span> <span data-ttu-id="7f76c-123">Behalve de eigenschappen die in de volgende secties worden genoemd, is het antwoord hetzelfde als de oude route.</span><span class="sxs-lookup"><span data-stu-id="7f76c-123">Other than the properties mentioned in the following sections, the response is the same as the old route.</span></span>

## <a name="c"></a><span data-ttu-id="7f76c-124">C\#</span><span class="sxs-lookup"><span data-stu-id="7f76c-124">C\#</span></span>

<span data-ttu-id="7f76c-125">Het gebruik van gegevens over het meten van een klant voor een specifieke Azure-service of-resource tijdens de huidige facturerings periode ophalen:</span><span class="sxs-lookup"><span data-stu-id="7f76c-125">To get meter usage records of a customer for a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="7f76c-126">Gebruik uw verzameling **IAggregatePartner. Customers** om de methode **ById ()** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="7f76c-126">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="7f76c-127">Roep de eigenschap abonnementen aan en **UsageRecords** en vervolgens de eigenschap **meters** .</span><span class="sxs-lookup"><span data-stu-id="7f76c-127">Call the Subscriptions property, and **UsageRecords**, then the **Meters** property.</span></span> <span data-ttu-id="7f76c-128">Voltooi door de methoden Get () of GetAsync () aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="7f76c-128">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Meters.Get();
    ```

<span data-ttu-id="7f76c-129">Zie het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="7f76c-129">For an example, see the following sample:</span></span>

- <span data-ttu-id="7f76c-130">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="7f76c-130">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="7f76c-131">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="7f76c-131">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="7f76c-132">Klasse: **GetSubscriptionUsageRecordsByMeter.cs**</span><span class="sxs-lookup"><span data-stu-id="7f76c-132">Class: **GetSubscriptionUsageRecordsByMeter.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="7f76c-133">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f76c-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7f76c-134">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f76c-134">Request syntax</span></span>

| <span data-ttu-id="7f76c-135">Methode</span><span class="sxs-lookup"><span data-stu-id="7f76c-135">Method</span></span>  | <span data-ttu-id="7f76c-136">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7f76c-136">Request URI</span></span>                                                                                                                             |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7f76c-137">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7f76c-137">**GET**</span></span> | <span data-ttu-id="7f76c-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{Subscription-id}/meterusagerecords http/1.1</span><span class="sxs-lookup"><span data-stu-id="7f76c-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="7f76c-139">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="7f76c-139">URI parameters</span></span>

<span data-ttu-id="7f76c-140">Deze tabel bevat de vereiste query parameters voor het ophalen van de geclassificeerde gebruiks gegevens van de klant.</span><span class="sxs-lookup"><span data-stu-id="7f76c-140">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="7f76c-141">Naam</span><span class="sxs-lookup"><span data-stu-id="7f76c-141">Name</span></span>                   | <span data-ttu-id="7f76c-142">Type</span><span class="sxs-lookup"><span data-stu-id="7f76c-142">Type</span></span>     | <span data-ttu-id="7f76c-143">Vereist</span><span class="sxs-lookup"><span data-stu-id="7f76c-143">Required</span></span> | <span data-ttu-id="7f76c-144">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7f76c-144">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="7f76c-145">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="7f76c-145">**customer-tenant-id**</span></span> | <span data-ttu-id="7f76c-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="7f76c-146">**guid**</span></span> | <span data-ttu-id="7f76c-147">J</span><span class="sxs-lookup"><span data-stu-id="7f76c-147">Y</span></span>        | <span data-ttu-id="7f76c-148">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="7f76c-148">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="7f76c-149">**abonnement-id**</span><span class="sxs-lookup"><span data-stu-id="7f76c-149">**subscription-id**</span></span>    | <span data-ttu-id="7f76c-150">**guid**</span><span class="sxs-lookup"><span data-stu-id="7f76c-150">**guid**</span></span> | <span data-ttu-id="7f76c-151">J</span><span class="sxs-lookup"><span data-stu-id="7f76c-151">Y</span></span>        | <span data-ttu-id="7f76c-152">Een GUID die overeenkomt met de id van een partner centrum- [abonnements resource](subscription-resources.md#subscription), die een Microsoft Azure (MS-AZR-0145P) of een Azure-abonnement vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="7f76c-152">A GUID corresponding to the identifier of a Partner Center [subscription resource](subscription-resources.md#subscription), which represents a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span> <span data-ttu-id="7f76c-153">*Geef voor Azure-plannen voor abonnements abonnementen het **plan-id** op als de **abonnements-id** in deze route.*</span><span class="sxs-lookup"><span data-stu-id="7f76c-153">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="7f76c-154">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7f76c-154">Request headers</span></span>

<span data-ttu-id="7f76c-155">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="7f76c-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7f76c-156">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7f76c-156">Request body</span></span>

<span data-ttu-id="7f76c-157">Geen.</span><span class="sxs-lookup"><span data-stu-id="7f76c-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7f76c-158">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f76c-158">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="7f76c-159">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7f76c-159">REST response</span></span>

<span data-ttu-id="7f76c-160">Als dit lukt, retourneert deze methode **een \<MeterUsageRecord> PagedResourceCollection** -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="7f76c-160">If successful, this method returns a **PagedResourceCollection\<MeterUsageRecord>** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7f76c-161">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="7f76c-161">Response success and error codes</span></span>

<span data-ttu-id="7f76c-162">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="7f76c-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7f76c-163">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7f76c-163">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="7f76c-164">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="7f76c-164">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="7f76c-165">Antwoord voorbeeld voor Microsoft Azure-abonnementen (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="7f76c-165">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="7f76c-166">In dit voor beeld heeft de klant **145P Azure PayG** aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="7f76c-166">In this example, the customer purchased **145P Azure PayG**.</span></span>

<span data-ttu-id="7f76c-167">*Voor klanten met een Microsoft Azure-abonnement (MS-AZR-0145P) is er geen wijziging in de API-reactie.*</span><span class="sxs-lookup"><span data-stu-id="7f76c-167">*For customers with a Microsoft Azure (MS-AZR-0145P) subscription, there will be no change to API response.*</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 1,
    "items": [
        {
            "status": "active",
            "offerId": "MS-AZR-0145P",
            "resourceId": "11111111-F347-41B6-B02C-187B1B778A43",
            "id": "11111111-F347-41B6-B02C-187B1B778A43",
            "resourceName": "Microsoft Azure",
            "name": "Microsoft Azure",
            "totalCost": 22.861172,
            "currencyLocale": "fr-FR",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/{customer-tenant-id}/subscriptions/usagerecords/",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="7f76c-168">Voor beeld van REST Response voor Azure-abonnement</span><span class="sxs-lookup"><span data-stu-id="7f76c-168">REST response example for Azure plan</span></span>

<span data-ttu-id="7f76c-169">In dit voor beeld heeft de klant een Azure-abonnement aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="7f76c-169">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="7f76c-170">*Voor klanten met Azure-abonnementen zijn de volgende wijzigingen in de API-reactie:*</span><span class="sxs-lookup"><span data-stu-id="7f76c-170">*For customers with Azure plans, there are the following changes in the API response:*</span></span>

- <span data-ttu-id="7f76c-171">**currencyLocale** wordt vervangen door **currencyCode**</span><span class="sxs-lookup"><span data-stu-id="7f76c-171">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="7f76c-172">**usdTotalCost** is een nieuw veld</span><span class="sxs-lookup"><span data-stu-id="7f76c-172">**usdTotalCost** is a new field</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Fri, 26 Feb 2016 20:31:45 GMT

{
    "totalCount": 4,
    "items": [
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNVX-005J-Data Transfer In (GB)",
            "meterName": "Data Transfer In",
            "category": "Bandwidth",
            "subcategory": "Bandwidth",
            "quantityUsed": 0.01129,
            "unit": "1 GB",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNVX-005J-Data Transfer Out (GB)",
            "meterName": "Data Transfer Out",
            "category": "Bandwidth",
            "subcategory": "Bandwidth",
            "quantityUsed": 0.000224,
            "unit": "1 GB",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNZ5-006G-10K Batch Write Operations",
            "meterName": "Batch Write Operations",
            "category": "Storage",
            "subcategory": "Tables",
            "quantityUsed": 0.2462,
            "unit": "10K",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNZ5-006G-Data Stored (GB/Month)",
            "meterName": "LRS Data Stored",
            "category": "Storage",
            "subcategory": "Tables",
            "quantityUsed": 0.002632,
            "unit": "1 GB/Month",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/meterusagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
