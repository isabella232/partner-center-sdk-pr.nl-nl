---
title: Gebruiks overzicht van het abonnement van de klant ophalen
description: U kunt de SubscriptionUsageSummary-Resource gebruiken om een samen vatting van het gebruik van een specifieke Azure-service of resource te verkrijgen tijdens de huidige facturerings periode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 30334b6f08829eccf0693b566c11f94cb3ece976
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767307"
---
# <a name="get-usage-summary-for-customers-subscription"></a><span data-ttu-id="c7535-103">Gebruiks overzicht van het abonnement van de klant ophalen</span><span class="sxs-lookup"><span data-stu-id="c7535-103">Get usage summary for customer's subscription</span></span>

<span data-ttu-id="c7535-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="c7535-104">**Applies to:**</span></span>

- <span data-ttu-id="c7535-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="c7535-105">Partner Center</span></span>
- <span data-ttu-id="c7535-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="c7535-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="c7535-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c7535-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c7535-108">U kunt de **SubscriptionUsageSummary** -Resource gebruiken om een samen vatting van het gebruik van een abonnement voor een klant te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="c7535-108">You can use the **SubscriptionUsageSummary** resource to get a subscription usage summary for a customer.</span></span> <span data-ttu-id="c7535-109">Deze resource vertegenwoordigt de samen vatting van het abonnements gebruik van een specifieke Azure-service of resource tijdens de huidige facturerings periode.</span><span class="sxs-lookup"><span data-stu-id="c7535-109">This resource represents the subscription usage summary of a specific Azure service or resource during the current billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c7535-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c7535-110">Prerequisites</span></span>

- <span data-ttu-id="c7535-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c7535-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c7535-112">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c7535-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="c7535-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c7535-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c7535-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="c7535-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c7535-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="c7535-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c7535-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="c7535-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c7535-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="c7535-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c7535-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c7535-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="c7535-119">Een abonnements-id</span><span class="sxs-lookup"><span data-stu-id="c7535-119">A subscription identifier</span></span>

## <a name="c"></a><span data-ttu-id="c7535-120">C\#</span><span class="sxs-lookup"><span data-stu-id="c7535-120">C\#</span></span>

<span data-ttu-id="c7535-121">Voor een overzicht van het gebruik van een abonnement voor het abonnement van een klant:</span><span class="sxs-lookup"><span data-stu-id="c7535-121">To get a subscription usage summary for a customer's subscription:</span></span>

1. <span data-ttu-id="c7535-122">Gebruik uw verzameling **IAggregatePartner. Customers** om de methode **ById ()** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c7535-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="c7535-123">Roep vervolgens de eigenschap abonnementen aan, evenals de eigenschap **UsageSummary** .</span><span class="sxs-lookup"><span data-stu-id="c7535-123">Then call the Subscriptions property, as well as **UsageSummary** property.</span></span> <span data-ttu-id="c7535-124">Voltooi door de methoden Get () of GetAsync () aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c7535-124">Finish by calling the Get() or GetAsync() methods.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var subscriptionUsageSummary = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageSummary.Get();
    ```

<span data-ttu-id="c7535-125">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="c7535-125">For an example, see the following:</span></span>

- <span data-ttu-id="c7535-126">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="c7535-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="c7535-127">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="c7535-127">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="c7535-128">Klasse: **GetSubscriptionUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="c7535-128">Class: **GetSubscriptionUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="c7535-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c7535-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c7535-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c7535-130">Request syntax</span></span>

| <span data-ttu-id="c7535-131">Methode</span><span class="sxs-lookup"><span data-stu-id="c7535-131">Method</span></span>  | <span data-ttu-id="c7535-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c7535-132">Request URI</span></span>                                                                                                                        |
|---------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c7535-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="c7535-133">**GET**</span></span> | <span data-ttu-id="c7535-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{Subscription-id}/usagesummary http/1.1</span><span class="sxs-lookup"><span data-stu-id="c7535-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="c7535-135">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="c7535-135">URI parameters</span></span>

<span data-ttu-id="c7535-136">Deze tabel bevat de vereiste query parameters voor het ophalen van de geclassificeerde gebruiks gegevens van de klant.</span><span class="sxs-lookup"><span data-stu-id="c7535-136">This table lists the required query parameters to get the customer's rated usage information.</span></span>

| <span data-ttu-id="c7535-137">Naam</span><span class="sxs-lookup"><span data-stu-id="c7535-137">Name</span></span>                   | <span data-ttu-id="c7535-138">Type</span><span class="sxs-lookup"><span data-stu-id="c7535-138">Type</span></span>     | <span data-ttu-id="c7535-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="c7535-139">Required</span></span> | <span data-ttu-id="c7535-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c7535-140">Description</span></span>                               |
|------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="c7535-141">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="c7535-141">**customer-tenant-id**</span></span> | <span data-ttu-id="c7535-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="c7535-142">**guid**</span></span> | <span data-ttu-id="c7535-143">J</span><span class="sxs-lookup"><span data-stu-id="c7535-143">Y</span></span>        | <span data-ttu-id="c7535-144">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="c7535-144">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="c7535-145">**abonnement-id**</span><span class="sxs-lookup"><span data-stu-id="c7535-145">**subscription-id**</span></span>    | <span data-ttu-id="c7535-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="c7535-146">**guid**</span></span> | <span data-ttu-id="c7535-147">J</span><span class="sxs-lookup"><span data-stu-id="c7535-147">Y</span></span>        | <span data-ttu-id="c7535-148">Een GUID die overeenkomt met de id van een abonnement.</span><span class="sxs-lookup"><span data-stu-id="c7535-148">A GUID corresponding to the identifier of a subscription.</span></span> <span data-ttu-id="c7535-149">Voor een Azure-abonnement is dit de id van het bijbehorende partner centrum- [abonnements resource](subscription-resources.md#subscription), dat het Azure-plan vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="c7535-149">For an Azure plan, this is the identifier of the corresponding Partner Center [subscription resource](subscription-resources.md#subscription), which represents the Azure plan.</span></span> <span data-ttu-id="c7535-150">*Geef voor Azure-plannen voor abonnements abonnementen het **plan-id** op als de **abonnements-id** in deze route.*</span><span class="sxs-lookup"><span data-stu-id="c7535-150">*For Azure plan subscription resources, provide the **plan-id** as the **subscription-id** in this route.*</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c7535-151">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c7535-151">Request headers</span></span>

<span data-ttu-id="c7535-152">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c7535-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c7535-153">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c7535-153">Request body</span></span>

<span data-ttu-id="c7535-154">Geen.</span><span class="sxs-lookup"><span data-stu-id="c7535-154">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c7535-155">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c7535-155">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="c7535-156">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c7535-156">REST response</span></span>

<span data-ttu-id="c7535-157">Als dit lukt, retourneert deze methode een **SubscriptionUsageSummary** -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="c7535-157">If successful, this method returns a **SubscriptionUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c7535-158">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="c7535-158">Response success and error codes</span></span>

<span data-ttu-id="c7535-159">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="c7535-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c7535-160">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c7535-160">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="c7535-161">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="c7535-161">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a><span data-ttu-id="c7535-162">Antwoord voorbeeld voor Microsoft Azure-abonnementen (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="c7535-162">Response example for Microsoft Azure (MS-AZR-0145P) subscriptions</span></span>

<span data-ttu-id="c7535-163">In dit voor beeld heeft de klant een **145P Azure PayG** -aanbieding aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="c7535-163">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="c7535-164">*Voor klanten met Microsoft Azure-abonnementen (MS-AZR-0145P) is er geen wijziging in de API-reactie.*</span><span class="sxs-lookup"><span data-stu-id="c7535-164">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

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

## <a name="rest-response-example-for-azure-plan"></a><span data-ttu-id="c7535-165">Voor beeld van REST Response voor Azure-abonnement</span><span class="sxs-lookup"><span data-stu-id="c7535-165">REST response example for Azure plan</span></span>

<span data-ttu-id="c7535-166">In dit voor beeld heeft de klant een Azure-abonnement aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="c7535-166">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="c7535-167">*Voor klanten met Azure-abonnementen zijn de volgende wijzigingen van de API-reactie:*</span><span class="sxs-lookup"><span data-stu-id="c7535-167">*For customers with Azure plans, there are the following API response changes:*</span></span>

- <span data-ttu-id="c7535-168">**currencyLocale** wordt vervangen door **currencyCode**</span><span class="sxs-lookup"><span data-stu-id="c7535-168">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="c7535-169">**usdTotalCost** is een nieuw veld</span><span class="sxs-lookup"><span data-stu-id="c7535-169">**usdTotalCost** is a new field</span></span>

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
