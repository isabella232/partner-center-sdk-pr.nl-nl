---
title: Een samen vatting van het gebruik voor alle abonnementen van een klant ophalen
description: U kunt de CustomerUsageSummary-Resource gebruiken om het gebruik van een specifieke Azure-service of resource binnen de huidige facturerings periode te verkrijgen.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0c918434367a3514e6a6ad6034b4897c33f51025
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767304"
---
# <a name="get-a-usage-summary-for-all-of-a-customers-subscriptions"></a><span data-ttu-id="c54ec-103">Een samen vatting van het gebruik voor alle abonnementen van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="c54ec-103">Get a usage summary for all of a customer's subscriptions</span></span>

<span data-ttu-id="c54ec-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="c54ec-104">**Applies to:**</span></span>

- <span data-ttu-id="c54ec-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="c54ec-105">Partner Center</span></span>
- <span data-ttu-id="c54ec-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="c54ec-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="c54ec-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="c54ec-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="c54ec-108">U kunt de **CustomerUsageSummary** -Resource gebruiken om het gebruik van een specifieke Azure-service of resource binnen de huidige facturerings periode te verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="c54ec-108">You can use the **CustomerUsageSummary** resource to get a customer's usage of a specific Azure service or resource during the current billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c54ec-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c54ec-109">Prerequisites</span></span>

- <span data-ttu-id="c54ec-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c54ec-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c54ec-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c54ec-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="c54ec-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c54ec-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c54ec-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="c54ec-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c54ec-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="c54ec-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c54ec-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="c54ec-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c54ec-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="c54ec-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c54ec-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c54ec-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="c54ec-118">C\#</span><span class="sxs-lookup"><span data-stu-id="c54ec-118">C\#</span></span>

<span data-ttu-id="c54ec-119">Voor een overzicht van het gebruik van alle abonnementen van een klant:</span><span class="sxs-lookup"><span data-stu-id="c54ec-119">To get a usage summary for all of a customer's subscriptions:</span></span>

1. <span data-ttu-id="c54ec-120">Gebruik uw verzameling **IAggregatePartner. Customers** om de methode **ById ()** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="c54ec-120">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="c54ec-121">Roep de eigenschap **UsageSummary** aan, gevolgd door de methoden **Get ()** of **GetAsync ()** :</span><span class="sxs-lookup"><span data-stu-id="c54ec-121">Call the **UsageSummary** property, followed by the **Get()** or **GetAsync()** methods:</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;

    var usageSummary = partnerOperations.Customers.ById(selectedCustomerId).UsageSummary.Get();
    ```

<span data-ttu-id="c54ec-122">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="c54ec-122">For an example, see the following:</span></span>

- <span data-ttu-id="c54ec-123">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="c54ec-123">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="c54ec-124">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="c54ec-124">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="c54ec-125">Klasse: **GetCustomerUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="c54ec-125">Class: **GetCustomerUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="c54ec-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c54ec-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c54ec-127">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c54ec-127">Request syntax</span></span>

| <span data-ttu-id="c54ec-128">Methode</span><span class="sxs-lookup"><span data-stu-id="c54ec-128">Method</span></span>  | <span data-ttu-id="c54ec-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c54ec-129">Request URI</span></span>                                                                                         |
|---------|-----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c54ec-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="c54ec-130">**GET**</span></span> | <span data-ttu-id="c54ec-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/usagesummary http/1.1</span><span class="sxs-lookup"><span data-stu-id="c54ec-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagesummary HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="c54ec-132">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="c54ec-132">URI parameter</span></span>

<span data-ttu-id="c54ec-133">Deze tabel bevat de vereiste query parameter voor het ophalen van de geclassificeerde gebruiks gegevens van de klant.</span><span class="sxs-lookup"><span data-stu-id="c54ec-133">This table lists the required query parameter to get the customer's rated usage information.</span></span>

| <span data-ttu-id="c54ec-134">Naam</span><span class="sxs-lookup"><span data-stu-id="c54ec-134">Name</span></span>                   | <span data-ttu-id="c54ec-135">Type</span><span class="sxs-lookup"><span data-stu-id="c54ec-135">Type</span></span>     | <span data-ttu-id="c54ec-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="c54ec-136">Required</span></span> | <span data-ttu-id="c54ec-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c54ec-137">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="c54ec-138">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="c54ec-138">**customer-tenant-id**</span></span> | <span data-ttu-id="c54ec-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="c54ec-139">**guid**</span></span> | <span data-ttu-id="c54ec-140">J</span><span class="sxs-lookup"><span data-stu-id="c54ec-140">Y</span></span>        | <span data-ttu-id="c54ec-141">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="c54ec-141">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="c54ec-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c54ec-142">Request headers</span></span>

<span data-ttu-id="c54ec-143">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c54ec-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c54ec-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c54ec-144">Request body</span></span>

<span data-ttu-id="c54ec-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="c54ec-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="c54ec-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c54ec-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="c54ec-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c54ec-147">REST response</span></span>

<span data-ttu-id="c54ec-148">Als dit lukt, retourneert deze methode een **CustomerUsageSummary** -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="c54ec-148">If successful, this method returns a **CustomerUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c54ec-149">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="c54ec-149">Response success and error codes</span></span>

<span data-ttu-id="c54ec-150">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="c54ec-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c54ec-151">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c54ec-151">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="c54ec-152">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="c54ec-152">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscription"></a><span data-ttu-id="c54ec-153">Antwoord voorbeeld voor Microsoft Azure-abonnement (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="c54ec-153">Response example for Microsoft Azure (MS-AZR-0145P) subscription</span></span>

<span data-ttu-id="c54ec-154">In dit voor beeld heeft de klant een **145P Azure PayG** -aanbieding aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="c54ec-154">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="c54ec-155">*Voor klanten met Microsoft Azure-abonnementen (MS-AZR-0145P) is er geen wijziging in de API-reactie.*</span><span class="sxs-lookup"><span data-stu-id="c54ec-155">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "budget":{
        "ammount":300.000000,
        "attributes":{
            "objectType":"SpendingBudget"
        }
    },
    "id":"65726577-C208-40FD-9735-8C85AC9CAC68",
    "name":"600 test",
    "billingStartDate":"2016-02-06T00:00:00-08:00",
    "billingEndDate":"2016-03-05T00:00:00-08:00",
    "totalCost":0.0,
    "currencyLocale":"en-US",
    "lastModifiedDate":"2016-02-26T09:42:54.5130558+00:00",
    "links":{
        "self":{
            "uri":"/customers/{customer-tenant-id}/usagesummary",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"CustomerUsageSummary"
    }
}
```

### <a name="response-example-for-azure-plan"></a><span data-ttu-id="c54ec-156">Antwoord voorbeeld voor Azure-abonnement</span><span class="sxs-lookup"><span data-stu-id="c54ec-156">Response example for Azure plan</span></span>

<span data-ttu-id="c54ec-157">In dit voor beeld heeft de klant een Azure-abonnement aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="c54ec-157">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="c54ec-158">*Voor klanten met Azure-abonnementen zijn de volgende wijzigingen aangebracht in de API-reactie:*</span><span class="sxs-lookup"><span data-stu-id="c54ec-158">*For customers with Azure plans, there are the following changes to the API response:*</span></span>

- <span data-ttu-id="c54ec-159">**currencyLocale** wordt vervangen door **currencyCode**</span><span class="sxs-lookup"><span data-stu-id="c54ec-159">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="c54ec-160">**usdTotalCost** is een nieuw veld</span><span class="sxs-lookup"><span data-stu-id="c54ec-160">**usdTotalCost** is a new field</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "budget": {
        "amount": 97,
        "attributes": {
            "objectType": "SpendingBudget"
        }
    },
    "resourceId": "44908a11-641b-4c53-b7fc-0f2bfca8a581",
    "resourceName": "Modern Azure Customer UK",
    "billingStartDate": "2019-09-01T00:00:00+00:00",
    "billingEndDate": "2019-10-01T00:00:00+00:00",
    "totalCost": 28.82860766744404945074,
    "currencyCode": "GBP",
    "usdTotalCost": 35.23000000000000362337,
    "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
    "attributes": {
        "objectType": "CustomerUsageSummary"
    }
}
```
