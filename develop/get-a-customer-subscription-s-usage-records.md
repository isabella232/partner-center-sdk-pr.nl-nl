---
title: Alle gebruiksrecords voor abonnementen voor een klant ophalen
description: U kunt de resource verzameling SubscriptionMonthlyUsageRecord gebruiken om gebruiks records voor abonnementen op te halen voor een klant van een specifieke Azure-service of-resource tijdens de huidige facturerings periode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 765ea16ff58b462d83ae3b8764b8b34c3ef804dc
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767309"
---
# <a name="get-subscription-usage-records-for-a-customer"></a><span data-ttu-id="470e0-103">Gebruiks records voor abonnementen voor een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="470e0-103">Get subscription usage records for a customer</span></span>

<span data-ttu-id="470e0-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="470e0-104">**Applies to:**</span></span>

- <span data-ttu-id="470e0-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="470e0-105">Partner Center</span></span>
- <span data-ttu-id="470e0-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="470e0-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="470e0-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="470e0-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="470e0-108">U kunt de resource verzameling **SubscriptionMonthlyUsageRecord** gebruiken om gebruiks records voor abonnementen op te halen voor een klant van een specifieke Azure-service of-resource tijdens de huidige facturerings periode.</span><span class="sxs-lookup"><span data-stu-id="470e0-108">You can use the **SubscriptionMonthlyUsageRecord** resource collection to get subscription usage records for a customer of a specific Azure service or resource during the current billing period.</span></span> <span data-ttu-id="470e0-109">Deze resource vertegenwoordigt alle abonnementen voor de klant.</span><span class="sxs-lookup"><span data-stu-id="470e0-109">This resource represents all subscriptions for the customer.</span></span> <span data-ttu-id="470e0-110">Voor een klant met een Azure-abonnement retourneert deze resource een lijst met deze plannen (geen afzonderlijke Azure-abonnementen).</span><span class="sxs-lookup"><span data-stu-id="470e0-110">For a customer with an Azure plan, this resource returns a list of those plans (not individual Azure subscriptions).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="470e0-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="470e0-111">Prerequisites</span></span>

- <span data-ttu-id="470e0-112">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="470e0-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="470e0-113">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="470e0-113">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="470e0-114">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="470e0-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="470e0-115">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="470e0-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="470e0-116">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="470e0-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="470e0-117">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="470e0-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="470e0-118">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="470e0-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="470e0-119">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="470e0-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="470e0-120">C\#</span><span class="sxs-lookup"><span data-stu-id="470e0-120">C\#</span></span>

<span data-ttu-id="470e0-121">Voor het ophalen van abonnements gebruiks records voor een klant van een specifieke Azure-service of-resource tijdens de huidige facturerings periode.:</span><span class="sxs-lookup"><span data-stu-id="470e0-121">To get subscription usage records for a customer of a specific Azure service or resource during the current billing period.:</span></span>

1. <span data-ttu-id="470e0-122">Gebruik uw verzameling **IAggregatePartner. Customers** om de methode **ById ()** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="470e0-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="470e0-123">Roep vervolgens de eigenschap **abonnementen** aan, evenals de eigenschap **UsageRecords** .</span><span class="sxs-lookup"><span data-stu-id="470e0-123">Then call the **Subscriptions** property, as well as **UsageRecords** property.</span></span> <span data-ttu-id="470e0-124">Voltooi door de methoden Get () of GetAsync () aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="470e0-124">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.UsageRecords.Get();
    ```

<span data-ttu-id="470e0-125">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="470e0-125">For an example, see the following:</span></span>

- <span data-ttu-id="470e0-126">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="470e0-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="470e0-127">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="470e0-127">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="470e0-128">Klasse: **GetSubscriptionUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="470e0-128">Class: **GetSubscriptionUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="470e0-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="470e0-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="470e0-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="470e0-130">Request syntax</span></span>

| <span data-ttu-id="470e0-131">Methode</span><span class="sxs-lookup"><span data-stu-id="470e0-131">Method</span></span>  | <span data-ttu-id="470e0-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="470e0-132">Request URI</span></span>                                                                                                      |
|---------|------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="470e0-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="470e0-133">**GET**</span></span> | <span data-ttu-id="470e0-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/usagerecords http/1.1</span><span class="sxs-lookup"><span data-stu-id="470e0-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="470e0-135">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="470e0-135">URI parameter</span></span>

<span data-ttu-id="470e0-136">Deze tabel bevat de vereiste query parameter voor het ophalen van de geclassificeerde gebruiks gegevens van de klant.</span><span class="sxs-lookup"><span data-stu-id="470e0-136">This table lists the required query parameter to get the customer's rated usage information.</span></span>

| <span data-ttu-id="470e0-137">Naam</span><span class="sxs-lookup"><span data-stu-id="470e0-137">Name</span></span>                   | <span data-ttu-id="470e0-138">Type</span><span class="sxs-lookup"><span data-stu-id="470e0-138">Type</span></span>     | <span data-ttu-id="470e0-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="470e0-139">Required</span></span> | <span data-ttu-id="470e0-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="470e0-140">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="470e0-141">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="470e0-141">**customer-tenant-id**</span></span> | <span data-ttu-id="470e0-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="470e0-142">**guid**</span></span> | <span data-ttu-id="470e0-143">J</span><span class="sxs-lookup"><span data-stu-id="470e0-143">Y</span></span>        | <span data-ttu-id="470e0-144">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="470e0-144">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="470e0-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="470e0-145">Request headers</span></span>

<span data-ttu-id="470e0-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="470e0-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="470e0-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="470e0-147">Request body</span></span>

<span data-ttu-id="470e0-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="470e0-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="470e0-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="470e0-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="470e0-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="470e0-150">REST response</span></span>

<span data-ttu-id="470e0-151">Als dit lukt, retourneert deze methode een **SubscriptionMonthlyUsageRecord** -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="470e0-151">If successful, this method returns a **SubscriptionMonthlyUsageRecord** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="470e0-152">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="470e0-152">Response success and error codes</span></span>

<span data-ttu-id="470e0-153">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="470e0-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="470e0-154">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="470e0-154">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="470e0-155">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="470e0-155">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="470e0-156">Antwoord voorbeeld voor Microsoft Azure-abonnementen (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="470e0-156">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="470e0-157">In dit voor beeld heeft de klant een **145P Azure PayG** -aanbieding aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="470e0-157">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="470e0-158">*Voor klanten met Microsoft Azure-abonnementen (MS-AZR-0145P) is er geen wijziging in de API-reactie.*</span><span class="sxs-lookup"><span data-stu-id="470e0-158">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

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
            "uri": "/customers/<customer-tenant-id>/subscriptions/usagerecords/",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="470e0-159">Voor beeld van REST Response voor Azure-abonnement</span><span class="sxs-lookup"><span data-stu-id="470e0-159">REST response example for Azure plan</span></span>

<span data-ttu-id="470e0-160">In dit voor beeld heeft de klant een Azure-abonnement aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="470e0-160">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="470e0-161">*Voor klanten met Azure-abonnementen zijn de volgende wijzigingen in de API-reactie:*</span><span class="sxs-lookup"><span data-stu-id="470e0-161">*For customers with Azure plans, there are the following changes in the API response:*</span></span>

- <span data-ttu-id="470e0-162">**currencyLocale** wordt vervangen door **currencyCode**</span><span class="sxs-lookup"><span data-stu-id="470e0-162">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="470e0-163">**usdTotalCost** is een nieuw veld</span><span class="sxs-lookup"><span data-stu-id="470e0-163">**usdTotalCost** is a new field</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 2,
    "items": [
        {
            "status": "active",
            "partnerOnRecord": "some-id",
            "offerId": "DZH318Z0BPS6:0001:DZH318Z0BML6",
            "resourceId": "11111111-7d58-6654-69fa-0797198155d3",
            "id": "11111111-7d58-6654-69fa-0797198155d3",
            "resourceName": "Azure plan",
            "name": "Azure plan",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        },
        {
            "status": "active",
            "partnerOnRecord": "some-id",
            "offerId": "DZH318Z0BPS6:0001:DZH318Z0BML6",
            "resourceId": "11111111-25aa-ebb8-2bb4-fb406307babd",
            "id": "11111111-25aa-ebb8-2bb4-fb406307babd",
            "resourceName": "Azure plan",
            "name": "Azure plan",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/usagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
