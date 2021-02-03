---
title: Gebruiksgegevens voor het abonnement per bron ophalen
description: U kunt de ResourceUsageRecord-Resource gebruiken om de resource gebruiks records van een klant te verkrijgen voor specifieke Azure-Services of-resources tijdens de huidige facturerings periode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e815430730dd7182380e9efd1fea80f9e84d2ce7
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767308"
---
# <a name="get-usage-data-for-subscription-by-resource"></a><span data-ttu-id="44778-103">Gebruiksgegevens voor het abonnement per bron ophalen</span><span class="sxs-lookup"><span data-stu-id="44778-103">Get usage data for subscription by resource</span></span>

<span data-ttu-id="44778-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="44778-104">**Applies to:**</span></span>

- <span data-ttu-id="44778-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="44778-105">Partner Center</span></span>
- <span data-ttu-id="44778-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="44778-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="44778-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="44778-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="44778-108">In dit artikel wordt beschreven hoe u de **ResourceUsageRecord** -resource kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="44778-108">This article describes how to get the **ResourceUsageRecord** resource.</span></span> <span data-ttu-id="44778-109">Deze resource vertegenwoordigt een samengevoegd totaal voor de maand voor afzonderlijke resources die zijn ingericht in uw Azure-abonnement.</span><span class="sxs-lookup"><span data-stu-id="44778-109">This resource represents an aggregated total for the month for individual resources provisioned in your Azure plan.</span></span> <span data-ttu-id="44778-110">U kunt deze resource gebruiken om de resource gebruiks records van een klant te verkrijgen voor specifieke Azure-Services of-resources tijdens de huidige facturerings periode.</span><span class="sxs-lookup"><span data-stu-id="44778-110">You can use this resource to get a customer's resource usage records for specific Azure services or resources during the current billing period.</span></span> <span data-ttu-id="44778-111">Deze API retourneert gegevens die eerder niet beschikbaar waren via Azure besteding Api's.</span><span class="sxs-lookup"><span data-stu-id="44778-111">This API returns data that was not available previously through Azure spending APIs.</span></span>

<span data-ttu-id="44778-112">*Deze route biedt geen ondersteuning voor Microsoft Azure (MS-AZR-0145P)-abonnementen.*</span><span class="sxs-lookup"><span data-stu-id="44778-112">*This route does not support Microsoft Azure (MS-AZR-0145P) subscriptions.*</span></span>

## <a name="prerequisites"></a><span data-ttu-id="44778-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="44778-113">Prerequisites</span></span>

- <span data-ttu-id="44778-114">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="44778-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="44778-115">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="44778-115">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="44778-116">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="44778-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="44778-117">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="44778-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="44778-118">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="44778-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="44778-119">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="44778-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="44778-120">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="44778-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="44778-121">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="44778-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="44778-122">Een abonnements-id</span><span class="sxs-lookup"><span data-stu-id="44778-122">A subscription identifier</span></span>

## <a name="c"></a><span data-ttu-id="44778-123">C\#</span><span class="sxs-lookup"><span data-stu-id="44778-123">C\#</span></span>

<span data-ttu-id="44778-124">Resource gebruiks records van een klant voor een specifieke Azure-service of resource ophalen tijdens de huidige facturerings periode:</span><span class="sxs-lookup"><span data-stu-id="44778-124">To get resource usage records of a customer for a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="44778-125">Gebruik uw verzameling **IAggregatePartner. Customers** om de methode **ById ()** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="44778-125">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="44778-126">Roep de eigenschap abonnementen aan, evenals **UsageRecords**, en vervolgens de eigenschap **resources** .</span><span class="sxs-lookup"><span data-stu-id="44778-126">Call the Subscriptions property, as well as **UsageRecords**, then the **Resources** property.</span></span> <span data-ttu-id="44778-127">Voltooi door de methoden Get () of GetAsync () aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="44778-127">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Resources.Get();
    ```

<span data-ttu-id="44778-128">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="44778-128">For an example, see the following:</span></span>

- <span data-ttu-id="44778-129">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="44778-129">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="44778-130">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="44778-130">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="44778-131">Klasse: **GetSubscriptionUsageRecordsByResource.cs**</span><span class="sxs-lookup"><span data-stu-id="44778-131">Class: **GetSubscriptionUsageRecordsByResource.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="44778-132">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="44778-132">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="44778-133">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="44778-133">Request syntax</span></span>

| <span data-ttu-id="44778-134">Methode</span><span class="sxs-lookup"><span data-stu-id="44778-134">Method</span></span>  | <span data-ttu-id="44778-135">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="44778-135">Request URI</span></span>                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="44778-136">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="44778-136">**GET**</span></span> | <span data-ttu-id="44778-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{Subscription-id}/resourceusagerecords http/1.1</span><span class="sxs-lookup"><span data-stu-id="44778-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/resourceusagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="44778-138">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="44778-138">URI parameters</span></span>

<span data-ttu-id="44778-139">Deze tabel bevat de vereiste query parameters voor het ophalen van de geclassificeerde gebruiks gegevens van de klant.</span><span class="sxs-lookup"><span data-stu-id="44778-139">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="44778-140">Naam</span><span class="sxs-lookup"><span data-stu-id="44778-140">Name</span></span>                   | <span data-ttu-id="44778-141">Type</span><span class="sxs-lookup"><span data-stu-id="44778-141">Type</span></span>     | <span data-ttu-id="44778-142">Vereist</span><span class="sxs-lookup"><span data-stu-id="44778-142">Required</span></span> | <span data-ttu-id="44778-143">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="44778-143">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="44778-144">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="44778-144">**customer-tenant-id**</span></span> | <span data-ttu-id="44778-145">**guid**</span><span class="sxs-lookup"><span data-stu-id="44778-145">**guid**</span></span> | <span data-ttu-id="44778-146">J</span><span class="sxs-lookup"><span data-stu-id="44778-146">Y</span></span>        | <span data-ttu-id="44778-147">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="44778-147">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="44778-148">**abonnement-id**</span><span class="sxs-lookup"><span data-stu-id="44778-148">**subscription-id**</span></span>    | <span data-ttu-id="44778-149">**guid**</span><span class="sxs-lookup"><span data-stu-id="44778-149">**guid**</span></span> | <span data-ttu-id="44778-150">J</span><span class="sxs-lookup"><span data-stu-id="44778-150">Y</span></span>        | <span data-ttu-id="44778-151">Een GUID die overeenkomt met de id van een partner centrum- [abonnements resource](subscription-resources.md#subscription), die een Microsoft Azure (MS-AZR-0145P) of een Azure-abonnement vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="44778-151">A GUID corresponding to the identifier of a Partner Center [subscription resource](subscription-resources.md#subscription), which represents a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span> <span data-ttu-id="44778-152">*Geef voor Azure-plannen voor abonnements abonnementen het **plan-id** op als de **abonnements-id** in deze route.*</span><span class="sxs-lookup"><span data-stu-id="44778-152">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="44778-153">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="44778-153">Request headers</span></span>

<span data-ttu-id="44778-154">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="44778-154">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="44778-155">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="44778-155">Request body</span></span>

<span data-ttu-id="44778-156">Geen.</span><span class="sxs-lookup"><span data-stu-id="44778-156">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="44778-157">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="44778-157">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/resourceusagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="44778-158">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="44778-158">REST response</span></span>

<span data-ttu-id="44778-159">Als dit lukt, retourneert deze methode **een \<ResourceUsageRecord> PagedResourceCollection** -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="44778-159">If successful, this method returns a **PagedResourceCollection\<ResourceUsageRecord>** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="44778-160">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="44778-160">Response success and error codes</span></span>

<span data-ttu-id="44778-161">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="44778-161">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="44778-162">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="44778-162">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="44778-163">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="44778-163">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="44778-164">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="44778-164">Response example</span></span>

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
