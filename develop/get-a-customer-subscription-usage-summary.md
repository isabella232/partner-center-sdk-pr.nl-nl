---
title: Gebruiksoverzicht voor het abonnement van de klant op halen
description: U kunt de resource SubscriptionUsageSummary gebruiken om een abonnementsgebruiksoverzicht van een specifieke Azure-service of -resource op te halen tijdens de huidige factureringsperiode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 362e72e1b54a62a114564d4dc48a082bcdeea012
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874666"
---
# <a name="get-usage-summary-for-customers-subscription"></a><span data-ttu-id="28334-103">Gebruiksoverzicht voor het abonnement van de klant op halen</span><span class="sxs-lookup"><span data-stu-id="28334-103">Get usage summary for customer's subscription</span></span>

<span data-ttu-id="28334-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="28334-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="28334-105">U kunt de resource **SubscriptionUsageSummary gebruiken** om een abonnementsgebruiksoverzicht voor een klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="28334-105">You can use the **SubscriptionUsageSummary** resource to get a subscription usage summary for a customer.</span></span> <span data-ttu-id="28334-106">Deze resource vertegenwoordigt het abonnementsgebruiksoverzicht van een specifieke Azure-service of -resource tijdens de huidige factureringsperiode.</span><span class="sxs-lookup"><span data-stu-id="28334-106">This resource represents the subscription usage summary of a specific Azure service or resource during the current billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28334-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="28334-107">Prerequisites</span></span>

- <span data-ttu-id="28334-108">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="28334-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="28334-109">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="28334-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="28334-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="28334-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="28334-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="28334-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="28334-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="28334-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="28334-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="28334-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="28334-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="28334-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="28334-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="28334-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="28334-116">Een abonnements-id</span><span class="sxs-lookup"><span data-stu-id="28334-116">A subscription identifier</span></span>

## <a name="c"></a><span data-ttu-id="28334-117">C\#</span><span class="sxs-lookup"><span data-stu-id="28334-117">C\#</span></span>

<span data-ttu-id="28334-118">Ga als volgt te werk om een overzicht van het gebruik van een abonnement voor het abonnement van een klant op te halen:</span><span class="sxs-lookup"><span data-stu-id="28334-118">To get a subscription usage summary for a customer's subscription:</span></span>

1. <span data-ttu-id="28334-119">Gebruik de **verzameling IAggregatePartner.Customers om** de **methode ById() aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="28334-119">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="28334-120">Roep vervolgens de eigenschap Abonnementen en de **eigenschap UsageSummary** aan.</span><span class="sxs-lookup"><span data-stu-id="28334-120">Then call the Subscriptions property and the **UsageSummary** property.</span></span> <span data-ttu-id="28334-121">Als laatste roept u de methoden Get() of GetAsync() aan.</span><span class="sxs-lookup"><span data-stu-id="28334-121">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var subscriptionUsageSummary = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageSummary.Get();
    ```

<span data-ttu-id="28334-122">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="28334-122">For an example, see the following:</span></span>

- <span data-ttu-id="28334-123">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="28334-123">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="28334-124">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="28334-124">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="28334-125">Klasse: **GetSubscriptionUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="28334-125">Class: **GetSubscriptionUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="28334-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="28334-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="28334-127">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="28334-127">Request syntax</span></span>

| <span data-ttu-id="28334-128">Methode</span><span class="sxs-lookup"><span data-stu-id="28334-128">Method</span></span>  | <span data-ttu-id="28334-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="28334-129">Request URI</span></span>                                                                                                                        |
|---------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="28334-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="28334-130">**GET**</span></span> | <span data-ttu-id="28334-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="28334-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="28334-132">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="28334-132">URI parameters</span></span>

<span data-ttu-id="28334-133">Deze tabel bevat de vereiste queryparameters om de beoordeelde gebruiksgegevens van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="28334-133">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="28334-134">Naam</span><span class="sxs-lookup"><span data-stu-id="28334-134">Name</span></span>                   | <span data-ttu-id="28334-135">Type</span><span class="sxs-lookup"><span data-stu-id="28334-135">Type</span></span>     | <span data-ttu-id="28334-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="28334-136">Required</span></span> | <span data-ttu-id="28334-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="28334-137">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="28334-138">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="28334-138">**customer-tenant-id**</span></span> | <span data-ttu-id="28334-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="28334-139">**guid**</span></span> | <span data-ttu-id="28334-140">J</span><span class="sxs-lookup"><span data-stu-id="28334-140">Y</span></span>        | <span data-ttu-id="28334-141">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="28334-141">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="28334-142">**subscription-id**</span><span class="sxs-lookup"><span data-stu-id="28334-142">**subscription-id**</span></span>    | <span data-ttu-id="28334-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="28334-143">**guid**</span></span> | <span data-ttu-id="28334-144">J</span><span class="sxs-lookup"><span data-stu-id="28334-144">Y</span></span>        | <span data-ttu-id="28334-145">Een GUID die overeenkomt met de id van een abonnement.</span><span class="sxs-lookup"><span data-stu-id="28334-145">A GUID corresponding to the identifier of a subscription.</span></span> <span data-ttu-id="28334-146">Voor een Azure-plan is dit de id van de bijbehorende Partner Center [abonnementsresource](subscription-resources.md#subscription), die het Azure-plan vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="28334-146">For an Azure plan, this is the identifier of the corresponding Partner Center [subscription resource](subscription-resources.md#subscription), which represents the Azure plan.</span></span> <span data-ttu-id="28334-147">*Geef voor azure-abonnementsbronnen de **plan-id** op als **de abonnements-id** in deze route.*</span><span class="sxs-lookup"><span data-stu-id="28334-147">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="28334-148">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="28334-148">Request headers</span></span>

<span data-ttu-id="28334-149">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="28334-149">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="28334-150">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="28334-150">Request body</span></span>

<span data-ttu-id="28334-151">Geen.</span><span class="sxs-lookup"><span data-stu-id="28334-151">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="28334-152">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="28334-152">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="28334-153">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="28334-153">REST response</span></span>

<span data-ttu-id="28334-154">Als dit lukt, retourneert deze methode een **SubscriptionUsageSummary-resource** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="28334-154">If successful, this method returns a **SubscriptionUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="28334-155">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="28334-155">Response success and error codes</span></span>

<span data-ttu-id="28334-156">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="28334-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="28334-157">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="28334-157">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="28334-158">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="28334-158">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="28334-159">Voorbeeld van een Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="28334-159">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="28334-160">In dit voorbeeld heeft de klant een **Azure PayG-aanbieding van 145P** aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="28334-160">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="28334-161">*Voor klanten met Microsoft Azure-abonnementen (MS-AZR-0145P) is er geen wijziging in het API-antwoord.*</span><span class="sxs-lookup"><span data-stu-id="28334-161">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "resourceId": "ABCDEFGH-F347-41B6-B02C-187B1B778A43",
    "id": "ABCDEFGH-F347-41B6-B02C-187B1B778A43",
    "resourceName": "Microsoft Azure",
    "name": "Microsoft Azure",
    "billingStartDate": "2019-08-28T00:00:00-07:00",
    "billingEndDate": "2019-09-27T00:00:00-07:00",
    "totalCost": 22.861172,
    "currencyLocale": "fr-FR",
    "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SubscriptionUsageSummary"
    }
}
```

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="28334-162">VOORBEELD VAN REST-antwoord voor Azure-plan</span><span class="sxs-lookup"><span data-stu-id="28334-162">REST response example for Azure plan</span></span>

<span data-ttu-id="28334-163">In dit voorbeeld heeft de klant een Azure-abonnement aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="28334-163">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="28334-164">*Voor klanten met Azure-abonnementen zijn er de volgende API-antwoordwijzigingen:*</span><span class="sxs-lookup"><span data-stu-id="28334-164">*For customers with Azure plans, there are the following API response changes:*</span></span>

- <span data-ttu-id="28334-165">**currencyLocale** is vervangen door **currencyCode**</span><span class="sxs-lookup"><span data-stu-id="28334-165">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="28334-166">**usdTotalCost** is een nieuw veld</span><span class="sxs-lookup"><span data-stu-id="28334-166">**usdTotalCost** is a new field</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac1
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "resourceId": "11111111-dca5-6f31-d3a6-dbbfad9be0fc",
    "resourceName": "Azure plan",
    "billingStartDate": "2019-09-01T00:00:00+00:00",
    "billingEndDate": "2019-10-01T00:00:00+00:00",
    "totalCost": 28.82860766744404945074,
    "currencyCode": "GBP",
    "usdTotalCost": 35.23000000000000362337,
    "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SubscriptionUsageSummary"
    }
}
```
