---
title: Gebruiksgegevens voor het abonnement per meter ophalen
description: U kunt de MeterUsageRecord-resourceverzameling gebruiken om metergebruiksrecords van een klant op te halen voor specifieke Azure-services of -resources tijdens de huidige factureringsperiode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0bd6143c80059bd140a4c4332ab4ec19c54d99f1
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874853"
---
# <a name="get-usage-data-for-subscription-by-meter"></a><span data-ttu-id="1e296-103">Gebruiksgegevens voor het abonnement per meter ophalen</span><span class="sxs-lookup"><span data-stu-id="1e296-103">Get usage data for subscription by meter</span></span>

<span data-ttu-id="1e296-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1e296-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1e296-105">U kunt de **MeterUsageRecord-resourceverzameling** gebruiken om metergebruiksrecords van een klant op te halen voor specifieke Azure-services of -resources tijdens de huidige factureringsperiode.</span><span class="sxs-lookup"><span data-stu-id="1e296-105">You can use the **MeterUsageRecord** resource collection to get meter usage records of a customer for specific Azure services or resources during the current billing period.</span></span> <span data-ttu-id="1e296-106">Deze resourceverzameling vertegenwoordigt een geaggregeerd totaal voor elke meter voor de huidige factureringscyclus, voor uw hele Azure-plan.</span><span class="sxs-lookup"><span data-stu-id="1e296-106">This resource collection represents an aggregated total for each meter for the current billing cycle, across your entire Azure plan.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1e296-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1e296-107">Prerequisites</span></span>

- <span data-ttu-id="1e296-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1e296-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1e296-109">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="1e296-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="1e296-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1e296-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="1e296-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="1e296-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="1e296-112">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="1e296-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="1e296-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="1e296-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="1e296-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="1e296-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="1e296-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1e296-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="1e296-116">Een abonnements-id</span><span class="sxs-lookup"><span data-stu-id="1e296-116">A subscription ID</span></span>

<span data-ttu-id="1e296-117">*Deze nieuwe route is gelijk aan , die alleen blijft werken `subscriptions/{subscription-id}/usagerecords/resources` voor Microsoft Azure(MS-AZR-0145P)-abonnementen.*</span><span class="sxs-lookup"><span data-stu-id="1e296-117">*This new route is equivalent to `subscriptions/{subscription-id}/usagerecords/resources`, which will continue to function only for Microsoft Azure (MS-AZR-0145P) subscriptions.*</span></span> <span data-ttu-id="1e296-118">Deze nieuwe route ondersteunt zowel Microsoft Azure-abonnementen (MS-AZR-0145P) als Azure-abonnementen.</span><span class="sxs-lookup"><span data-stu-id="1e296-118">This new route will support both Microsoft Azure (MS-AZR-0145P) subscriptions and Azure plans.</span></span> <span data-ttu-id="1e296-119">Als u deze informatie voor uw Azure-plan wilt ontvangen, moet u overschakelen naar deze nieuwe route.</span><span class="sxs-lookup"><span data-stu-id="1e296-119">In order to get this information for your Azure plan, you need to switch to this new route.</span></span> <span data-ttu-id="1e296-120">Af tegenstelling tot de eigenschappen die in de volgende secties worden vermeld, is het antwoord hetzelfde als de oude route.</span><span class="sxs-lookup"><span data-stu-id="1e296-120">Other than the properties mentioned in the following sections, the response is the same as the old route.</span></span>

## <a name="c"></a><span data-ttu-id="1e296-121">C\#</span><span class="sxs-lookup"><span data-stu-id="1e296-121">C\#</span></span>

<span data-ttu-id="1e296-122">Gebruiksrecords van een klant voor een specifieke Azure-service of -resource op te halen tijdens de huidige factureringsperiode:</span><span class="sxs-lookup"><span data-stu-id="1e296-122">To get meter usage records of a customer for a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="1e296-123">Gebruik de **verzameling IAggregatePartner.Customers om** de **methode ById() aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="1e296-123">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="1e296-124">Roep de eigenschap Abonnementen en **UsageRecords** aan en vervolgens de **eigenschap Meters.**</span><span class="sxs-lookup"><span data-stu-id="1e296-124">Call the Subscriptions property, and **UsageRecords**, then the **Meters** property.</span></span> <span data-ttu-id="1e296-125">Als laatste roept u de methoden Get() of GetAsync() aan.</span><span class="sxs-lookup"><span data-stu-id="1e296-125">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Meters.Get();
    ```

<span data-ttu-id="1e296-126">Zie het volgende voorbeeld voor een voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="1e296-126">For an example, see the following sample:</span></span>

- <span data-ttu-id="1e296-127">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="1e296-127">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="1e296-128">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="1e296-128">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="1e296-129">Klasse: **GetSubscriptionUsageRecordsByMeter.cs**</span><span class="sxs-lookup"><span data-stu-id="1e296-129">Class: **GetSubscriptionUsageRecordsByMeter.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="1e296-130">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="1e296-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1e296-131">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="1e296-131">Request syntax</span></span>

| <span data-ttu-id="1e296-132">Methode</span><span class="sxs-lookup"><span data-stu-id="1e296-132">Method</span></span>  | <span data-ttu-id="1e296-133">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="1e296-133">Request URI</span></span>                                                                                                                             |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1e296-134">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="1e296-134">**GET**</span></span> | <span data-ttu-id="1e296-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1e296-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="1e296-136">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="1e296-136">URI parameters</span></span>

<span data-ttu-id="1e296-137">Deze tabel bevat de vereiste queryparameters om de beoordeelde gebruiksgegevens van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="1e296-137">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="1e296-138">Naam</span><span class="sxs-lookup"><span data-stu-id="1e296-138">Name</span></span>                   | <span data-ttu-id="1e296-139">Type</span><span class="sxs-lookup"><span data-stu-id="1e296-139">Type</span></span>     | <span data-ttu-id="1e296-140">Vereist</span><span class="sxs-lookup"><span data-stu-id="1e296-140">Required</span></span> | <span data-ttu-id="1e296-141">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1e296-141">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="1e296-142">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="1e296-142">**customer-tenant-id**</span></span> | <span data-ttu-id="1e296-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="1e296-143">**guid**</span></span> | <span data-ttu-id="1e296-144">J</span><span class="sxs-lookup"><span data-stu-id="1e296-144">Y</span></span>        | <span data-ttu-id="1e296-145">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="1e296-145">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="1e296-146">**subscription-id**</span><span class="sxs-lookup"><span data-stu-id="1e296-146">**subscription-id**</span></span>    | <span data-ttu-id="1e296-147">**guid**</span><span class="sxs-lookup"><span data-stu-id="1e296-147">**guid**</span></span> | <span data-ttu-id="1e296-148">J</span><span class="sxs-lookup"><span data-stu-id="1e296-148">Y</span></span>        | <span data-ttu-id="1e296-149">Een GUID die overeenkomt met de id van een Partner Center-abonnementsresource [die](subscription-resources.md#subscription)een Microsoft Azure-abonnement (MS-AZR-0145P) of een Azure-abonnement vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1e296-149">A GUID corresponding to the identifier of a Partner Center [subscription resource](subscription-resources.md#subscription), which represents a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span> <span data-ttu-id="1e296-150">*Geef voor azure-abonnementsbronnen de **plan-id** op als **de abonnements-id** in deze route.*</span><span class="sxs-lookup"><span data-stu-id="1e296-150">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1e296-151">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="1e296-151">Request headers</span></span>

<span data-ttu-id="1e296-152">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="1e296-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1e296-153">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="1e296-153">Request body</span></span>

<span data-ttu-id="1e296-154">Geen.</span><span class="sxs-lookup"><span data-stu-id="1e296-154">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="1e296-155">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1e296-155">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="1e296-156">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="1e296-156">REST response</span></span>

<span data-ttu-id="1e296-157">Als dit lukt, retourneert deze methode een **\<MeterUsageRecord> PagedResourceCollection-resource** in de hoofdgedeelte van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="1e296-157">If successful, this method returns a **PagedResourceCollection\<MeterUsageRecord>** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1e296-158">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="1e296-158">Response success and error codes</span></span>

<span data-ttu-id="1e296-159">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="1e296-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1e296-160">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1e296-160">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="1e296-161">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="1e296-161">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="1e296-162">Voorbeeld van een Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="1e296-162">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="1e296-163">In dit voorbeeld heeft de klant **145P Azure PayG aangeschaft.**</span><span class="sxs-lookup"><span data-stu-id="1e296-163">In this example, the customer purchased **145P Azure PayG**.</span></span>

<span data-ttu-id="1e296-164">*Voor klanten met een Microsoft Azure (MS-AZR-0145P) is er geen wijziging in het API-antwoord.*</span><span class="sxs-lookup"><span data-stu-id="1e296-164">*For customers with a Microsoft Azure (MS-AZR-0145P) subscription, there will be no change to API response.*</span></span>

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

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="1e296-165">REST-antwoordvoorbeeld voor Azure-plan</span><span class="sxs-lookup"><span data-stu-id="1e296-165">REST response example for Azure plan</span></span>

<span data-ttu-id="1e296-166">In dit voorbeeld heeft de klant een Azure-abonnement aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="1e296-166">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="1e296-167">*Voor klanten met Azure-plannen zijn er de volgende wijzigingen in het API-antwoord:*</span><span class="sxs-lookup"><span data-stu-id="1e296-167">*For customers with Azure plans, there are the following changes in the API response:*</span></span>

- <span data-ttu-id="1e296-168">**currencyLocale** is vervangen door **currencyCode**</span><span class="sxs-lookup"><span data-stu-id="1e296-168">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="1e296-169">**usdTotalCost** is een nieuw veld</span><span class="sxs-lookup"><span data-stu-id="1e296-169">**usdTotalCost** is a new field</span></span>

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
