---
title: Alle gebruiksrecords voor abonnementen voor een klant ophalen
description: U kunt de resourceverzameling SubscriptionMonthlyUsageRecord gebruiken om in de huidige factureringsperiode abonnementsgebruiksrecords op te halen voor een klant van een specifieke Azure-service of -resource.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 976abd86f34c1c27184f277ffc89fbc65f16bb37
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874683"
---
# <a name="get-subscription-usage-records-for-a-customer"></a><span data-ttu-id="84e84-103">Abonnementsgebruiksrecords voor een klant op halen</span><span class="sxs-lookup"><span data-stu-id="84e84-103">Get subscription usage records for a customer</span></span>

<span data-ttu-id="84e84-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="84e84-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="84e84-105">U kunt de resourceverzameling **SubscriptionMonthlyUsageRecord** gebruiken om in de huidige factureringsperiode abonnementsgebruiksrecords op te halen voor een klant van een specifieke Azure-service of -resource.</span><span class="sxs-lookup"><span data-stu-id="84e84-105">You can use the **SubscriptionMonthlyUsageRecord** resource collection to get subscription usage records for a customer of a specific Azure service or resource during the current billing period.</span></span> <span data-ttu-id="84e84-106">Deze resource vertegenwoordigt alle abonnementen voor de klant.</span><span class="sxs-lookup"><span data-stu-id="84e84-106">This resource represents all subscriptions for the customer.</span></span> <span data-ttu-id="84e84-107">Voor een klant met een Azure-plan retourneert deze resource een lijst met deze abonnementen (geen afzonderlijke Azure-abonnementen).</span><span class="sxs-lookup"><span data-stu-id="84e84-107">For a customer with an Azure plan, this resource returns a list of those plans (not individual Azure subscriptions).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="84e84-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="84e84-108">Prerequisites</span></span>

- <span data-ttu-id="84e84-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="84e84-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="84e84-110">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="84e84-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="84e84-111">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="84e84-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="84e84-112">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="84e84-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="84e84-113">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="84e84-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="84e84-114">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="84e84-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="84e84-115">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="84e84-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="84e84-116">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="84e84-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="84e84-117">C\#</span><span class="sxs-lookup"><span data-stu-id="84e84-117">C\#</span></span>

<span data-ttu-id="84e84-118">Als u gebruiksrecords voor abonnementen wilt op halen voor een klant van een specifieke Azure-service of -resource tijdens de huidige factureringsperiode, moet u de volgende stappen uitvoeren:</span><span class="sxs-lookup"><span data-stu-id="84e84-118">To get subscription usage records for a customer of a specific Azure service or resource during the current billing period, do the following steps:</span></span>

1. <span data-ttu-id="84e84-119">Gebruik de **verzameling IAggregatePartner.Customers** om de **methode ById() aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="84e84-119">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="84e84-120">Roep vervolgens de **eigenschap Abonnementen en** de eigenschap **UsageRecords aan.**</span><span class="sxs-lookup"><span data-stu-id="84e84-120">Then call the **Subscriptions** property and the **UsageRecords** property.</span></span> <span data-ttu-id="84e84-121">Als laatste roept u de methoden Get() of GetAsync() aan.</span><span class="sxs-lookup"><span data-stu-id="84e84-121">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.UsageRecords.Get();
    ```

<span data-ttu-id="84e84-122">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="84e84-122">For an example, see the following:</span></span>

- <span data-ttu-id="84e84-123">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="84e84-123">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="84e84-124">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="84e84-124">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="84e84-125">Klasse: **GetSubscriptionUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="84e84-125">Class: **GetSubscriptionUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="84e84-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="84e84-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="84e84-127">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="84e84-127">Request syntax</span></span>

| <span data-ttu-id="84e84-128">Methode</span><span class="sxs-lookup"><span data-stu-id="84e84-128">Method</span></span>  | <span data-ttu-id="84e84-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="84e84-129">Request URI</span></span>                                                                                                      |
|---------|------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="84e84-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="84e84-130">**GET**</span></span> | <span data-ttu-id="84e84-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="84e84-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="84e84-132">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="84e84-132">URI parameter</span></span>

<span data-ttu-id="84e84-133">Deze tabel bevat de vereiste queryparameter om de beoordeelde gebruiksgegevens van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="84e84-133">This table lists the required query parameter to get the customer's rated usage information.</span></span>

| <span data-ttu-id="84e84-134">Naam</span><span class="sxs-lookup"><span data-stu-id="84e84-134">Name</span></span>                   | <span data-ttu-id="84e84-135">Type</span><span class="sxs-lookup"><span data-stu-id="84e84-135">Type</span></span>     | <span data-ttu-id="84e84-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="84e84-136">Required</span></span> | <span data-ttu-id="84e84-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="84e84-137">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="84e84-138">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="84e84-138">**customer-tenant-id**</span></span> | <span data-ttu-id="84e84-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="84e84-139">**guid**</span></span> | <span data-ttu-id="84e84-140">J</span><span class="sxs-lookup"><span data-stu-id="84e84-140">Y</span></span>        | <span data-ttu-id="84e84-141">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="84e84-141">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="84e84-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="84e84-142">Request headers</span></span>

<span data-ttu-id="84e84-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="84e84-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="84e84-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="84e84-144">Request body</span></span>

<span data-ttu-id="84e84-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="84e84-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="84e84-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="84e84-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="84e84-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="84e84-147">REST response</span></span>

<span data-ttu-id="84e84-148">Als dit lukt, retourneert deze methode een **SubscriptionMonthlyUsageRecord-resource** in de hoofd body van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="84e84-148">If successful, this method returns a **SubscriptionMonthlyUsageRecord** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="84e84-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="84e84-149">Response success and error codes</span></span>

<span data-ttu-id="84e84-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="84e84-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="84e84-151">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="84e84-151">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="84e84-152">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="84e84-152">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="84e84-153">Voorbeeld van een Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="84e84-153">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="84e84-154">In dit voorbeeld heeft de klant een **Azure PayG-aanbieding van 145P** aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="84e84-154">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="84e84-155">*Voor klanten met Microsoft Azure -abonnementen (MS-AZR-0145P) is er geen wijziging in het API-antwoord.*</span><span class="sxs-lookup"><span data-stu-id="84e84-155">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

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

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="84e84-156">REST-antwoordvoorbeeld voor Azure-plan</span><span class="sxs-lookup"><span data-stu-id="84e84-156">REST response example for Azure plan</span></span>

<span data-ttu-id="84e84-157">In dit voorbeeld heeft de klant een Azure-abonnement aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="84e84-157">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="84e84-158">*Voor klanten met Azure-plannen zijn er de volgende wijzigingen in het API-antwoord:*</span><span class="sxs-lookup"><span data-stu-id="84e84-158">*For customers with Azure plans, there are the following changes in the API response:*</span></span>

- <span data-ttu-id="84e84-159">**currencyLocale** is vervangen door **currencyCode**</span><span class="sxs-lookup"><span data-stu-id="84e84-159">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="84e84-160">**usdTotalCost** is een nieuw veld</span><span class="sxs-lookup"><span data-stu-id="84e84-160">**usdTotalCost** is a new field</span></span>

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
