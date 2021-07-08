---
title: Gebruiksgegevens voor het abonnement per bron ophalen
description: U kunt de ResourceUsageRecord-resource gebruiken om de records voor resourcegebruik van een klant op te halen voor specifieke Azure-services of -resources tijdens de huidige factureringsperiode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 50edb9de1d09363b242c080a76c683732f05a5de
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874836"
---
# <a name="get-usage-data-for-subscription-by-resource"></a><span data-ttu-id="8bdea-103">Gebruiksgegevens voor het abonnement per bron ophalen</span><span class="sxs-lookup"><span data-stu-id="8bdea-103">Get usage data for subscription by resource</span></span>

<span data-ttu-id="8bdea-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="8bdea-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="8bdea-105">In dit artikel wordt beschreven hoe u de **resource ResourceUsageRecord op** kunt halen.</span><span class="sxs-lookup"><span data-stu-id="8bdea-105">This article describes how to get the **ResourceUsageRecord** resource.</span></span> <span data-ttu-id="8bdea-106">Deze resource vertegenwoordigt een geaggregeerd totaal voor de maand voor afzonderlijke resources die zijn ingericht in uw Azure-plan.</span><span class="sxs-lookup"><span data-stu-id="8bdea-106">This resource represents an aggregated total for the month for individual resources provisioned in your Azure plan.</span></span> <span data-ttu-id="8bdea-107">U kunt deze resource gebruiken om de records voor resourcegebruik van een klant op te halen voor specifieke Azure-services of -resources tijdens de huidige factureringsperiode.</span><span class="sxs-lookup"><span data-stu-id="8bdea-107">You can use this resource to get a customer's resource usage records for specific Azure services or resources during the current billing period.</span></span> <span data-ttu-id="8bdea-108">Deze API retourneert gegevens die eerder niet beschikbaar waren via Azure-bestedings-API's.</span><span class="sxs-lookup"><span data-stu-id="8bdea-108">This API returns data that was not available previously through Azure spending APIs.</span></span>

<span data-ttu-id="8bdea-109">*Deze route biedt geen ondersteuning Microsoft Azure -abonnementen (MS-AZR-0145P).*</span><span class="sxs-lookup"><span data-stu-id="8bdea-109">*This route does not support Microsoft Azure (MS-AZR-0145P) subscriptions.*</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8bdea-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8bdea-110">Prerequisites</span></span>

- <span data-ttu-id="8bdea-111">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8bdea-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8bdea-112">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="8bdea-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="8bdea-113">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8bdea-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8bdea-114">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="8bdea-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8bdea-115">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="8bdea-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8bdea-116">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="8bdea-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8bdea-117">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="8bdea-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8bdea-118">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8bdea-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="8bdea-119">Een abonnements-id</span><span class="sxs-lookup"><span data-stu-id="8bdea-119">A subscription identifier</span></span>

## <a name="c"></a><span data-ttu-id="8bdea-120">C\#</span><span class="sxs-lookup"><span data-stu-id="8bdea-120">C\#</span></span>

<span data-ttu-id="8bdea-121">Als u records over resourcegebruik van een klant voor een specifieke Azure-service of -resource wilt op halen tijdens de huidige factureringsperiode:</span><span class="sxs-lookup"><span data-stu-id="8bdea-121">To get resource usage records of a customer for a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="8bdea-122">Gebruik de **verzameling IAggregatePartner.Customers om** de **methode ById() aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="8bdea-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="8bdea-123">Roep de eigenschap Abonnementen en **UsageRecords** aan en vervolgens de **eigenschap Resources.**</span><span class="sxs-lookup"><span data-stu-id="8bdea-123">Call the Subscriptions property and **UsageRecords**, and then the **Resources** property.</span></span> <span data-ttu-id="8bdea-124">Als laatste roept u de methoden Get() of GetAsync() aan.</span><span class="sxs-lookup"><span data-stu-id="8bdea-124">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Resources.Get();
    ```

<span data-ttu-id="8bdea-125">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="8bdea-125">For an example, see the following:</span></span>

- <span data-ttu-id="8bdea-126">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="8bdea-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="8bdea-127">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="8bdea-127">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="8bdea-128">Klasse: **GetSubscriptionUsageRecordsByResource.cs**</span><span class="sxs-lookup"><span data-stu-id="8bdea-128">Class: **GetSubscriptionUsageRecordsByResource.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="8bdea-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="8bdea-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8bdea-130">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="8bdea-130">Request syntax</span></span>

| <span data-ttu-id="8bdea-131">Methode</span><span class="sxs-lookup"><span data-stu-id="8bdea-131">Method</span></span>  | <span data-ttu-id="8bdea-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="8bdea-132">Request URI</span></span>                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8bdea-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="8bdea-133">**GET**</span></span> | <span data-ttu-id="8bdea-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/resourceusagerecords HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8bdea-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/resourceusagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="8bdea-135">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="8bdea-135">URI parameters</span></span>

<span data-ttu-id="8bdea-136">Deze tabel bevat de vereiste queryparameters om de beoordeelde gebruiksgegevens van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="8bdea-136">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="8bdea-137">Naam</span><span class="sxs-lookup"><span data-stu-id="8bdea-137">Name</span></span>                   | <span data-ttu-id="8bdea-138">Type</span><span class="sxs-lookup"><span data-stu-id="8bdea-138">Type</span></span>     | <span data-ttu-id="8bdea-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="8bdea-139">Required</span></span> | <span data-ttu-id="8bdea-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8bdea-140">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="8bdea-141">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="8bdea-141">**customer-tenant-id**</span></span> | <span data-ttu-id="8bdea-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="8bdea-142">**guid**</span></span> | <span data-ttu-id="8bdea-143">J</span><span class="sxs-lookup"><span data-stu-id="8bdea-143">Y</span></span>        | <span data-ttu-id="8bdea-144">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="8bdea-144">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="8bdea-145">**subscription-id**</span><span class="sxs-lookup"><span data-stu-id="8bdea-145">**subscription-id**</span></span>    | <span data-ttu-id="8bdea-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="8bdea-146">**guid**</span></span> | <span data-ttu-id="8bdea-147">J</span><span class="sxs-lookup"><span data-stu-id="8bdea-147">Y</span></span>        | <span data-ttu-id="8bdea-148">Een GUID die overeenkomt met de id van een Partner Center-abonnementsresource [die](subscription-resources.md#subscription)een Microsoft Azure-abonnement (MS-AZR-0145P) of een Azure-abonnement vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="8bdea-148">A GUID corresponding to the identifier of a Partner Center [subscription resource](subscription-resources.md#subscription), which represents a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span> <span data-ttu-id="8bdea-149">*Geef voor azure-abonnementsbronnen de **plan-id** op als **de abonnements-id** in deze route.*</span><span class="sxs-lookup"><span data-stu-id="8bdea-149">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8bdea-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="8bdea-150">Request headers</span></span>

<span data-ttu-id="8bdea-151">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="8bdea-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8bdea-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="8bdea-152">Request body</span></span>

<span data-ttu-id="8bdea-153">Geen.</span><span class="sxs-lookup"><span data-stu-id="8bdea-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="8bdea-154">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="8bdea-154">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/resourceusagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="8bdea-155">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="8bdea-155">REST response</span></span>

<span data-ttu-id="8bdea-156">Als dit lukt, retourneert deze methode een **PagedResourceCollection-resource \<ResourceUsageRecord>** in de hoofdgedeelte van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="8bdea-156">If successful, this method returns a **PagedResourceCollection\<ResourceUsageRecord>** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8bdea-157">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="8bdea-157">Response success and error codes</span></span>

<span data-ttu-id="8bdea-158">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="8bdea-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8bdea-159">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="8bdea-159">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="8bdea-160">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="8bdea-160">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8bdea-161">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="8bdea-161">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 3,
    "items": [
        {
            "subscriptionId": "{subscription-id}",
            "resourceUri": "/subscriptions/{subscription-id}/resourceGroups/TESTRG1/providers/Microsoft.Compute/disks/testVM1_OsDisk_1_531d3c99534b4649ae025d485370143e",
            "resourceType": "Microsoft.Compute",
            "entitlementId": "{entitlemen-id}",
            "entitlementName": "Partner Subscription",
            "resourceGroupName": "TESTRG1",
            "name": "testVM1_OsDisk_1_531d3c99534b4649ae025d485370143e",
            "resourceName": "testVM1_OsDisk_1_531d3c99534b4649ae025d485370143e",
            "totalCost": 2.0211938955034572,
            "currencyCode": "GBP",
            "usdTotalCost": 2.4700000000000001,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "ResourceUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "resourceUri": "/subscriptions/{subscription-id}/resourceGroups/TESTRG1/providers/Microsoft.Compute/virtualMachines/testVM1",
            "resourceType": "Microsoft.Compute",
            "entitlementId": "{entitlement-id}",
            "entitlementName": "Partner Subscription",
            "resourceGroupName": "TESTRG1",
            "name": "testVM1",
            "resourceName": "testVM1",
            "totalCost": 80.3322286322163563,
            "currencyCode": "GBP",
            "usdTotalCost": 98.1699999999999985,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "ResourceUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "resourceUri": "/subscriptions/{subscription-id}/resourceGroups/testrg1/providers/Microsoft.Storage/storageAccounts/testrg1diag153",
            "resourceType": "Microsoft.Storage",
            "entitlementId": "{entitlemen-id}",
            "entitlementName": "Partner Subscription",
            "resourceGroupName": "testrg1",
            "name": "testrg1diag153",
            "resourceName": "testrg1diag153",
            "totalCost": 0.0081829712368561032,
            "currencyCode": "GBP",
            "usdTotalCost": 0.0099999999999999997,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "ResourceUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/resourceusagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
