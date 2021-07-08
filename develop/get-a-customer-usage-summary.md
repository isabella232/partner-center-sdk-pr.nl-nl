---
title: Een gebruiksoverzicht voor alle abonnementen van een klant krijgen
description: U kunt de resource CustomerUsageSummary gebruiken om het gebruik van een specifieke Azure-service of -resource van een klant op te halen tijdens de huidige factureringsperiode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 88c69637c94b9263ede6924cf2dd09513aa00f70
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874615"
---
# <a name="get-a-usage-summary-for-all-of-a-customers-subscriptions"></a><span data-ttu-id="b92d5-103">Een gebruiksoverzicht voor alle abonnementen van een klant krijgen</span><span class="sxs-lookup"><span data-stu-id="b92d5-103">Get a usage summary for all of a customer's subscriptions</span></span>

<span data-ttu-id="b92d5-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b92d5-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b92d5-105">U kunt de **resource CustomerUsageSummary** gebruiken om het gebruik van een specifieke Azure-service of -resource van een klant op te halen tijdens de huidige factureringsperiode.</span><span class="sxs-lookup"><span data-stu-id="b92d5-105">You can use the **CustomerUsageSummary** resource to get a customer's usage of a specific Azure service or resource during the current billing period.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b92d5-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b92d5-106">Prerequisites</span></span>

- <span data-ttu-id="b92d5-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b92d5-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b92d5-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="b92d5-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="b92d5-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b92d5-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="b92d5-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="b92d5-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="b92d5-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="b92d5-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="b92d5-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="b92d5-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="b92d5-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="b92d5-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="b92d5-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b92d5-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="b92d5-115">C\#</span><span class="sxs-lookup"><span data-stu-id="b92d5-115">C\#</span></span>

<span data-ttu-id="b92d5-116">Ga als volgt te werk om een gebruiksoverzicht te krijgen voor alle abonnementen van een klant:</span><span class="sxs-lookup"><span data-stu-id="b92d5-116">To get a usage summary for all of a customer's subscriptions:</span></span>

1. <span data-ttu-id="b92d5-117">Gebruik de **verzameling IAggregatePartner.Customers om** de **methode ById() aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="b92d5-117">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="b92d5-118">Roep de **eigenschap UsageSummary** aan, gevolgd door de **methoden Get()** of **GetAsync()** :</span><span class="sxs-lookup"><span data-stu-id="b92d5-118">Call the **UsageSummary** property, followed by the **Get()** or **GetAsync()** methods:</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;

    var usageSummary = partnerOperations.Customers.ById(selectedCustomerId).UsageSummary.Get();
    ```

<span data-ttu-id="b92d5-119">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="b92d5-119">For an example, see the following:</span></span>

- <span data-ttu-id="b92d5-120">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="b92d5-120">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="b92d5-121">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="b92d5-121">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="b92d5-122">Klasse: **GetCustomerUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="b92d5-122">Class: **GetCustomerUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="b92d5-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="b92d5-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b92d5-124">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="b92d5-124">Request syntax</span></span>

| <span data-ttu-id="b92d5-125">Methode</span><span class="sxs-lookup"><span data-stu-id="b92d5-125">Method</span></span>  | <span data-ttu-id="b92d5-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="b92d5-126">Request URI</span></span>                                                                                         |
|---------|-----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b92d5-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="b92d5-127">**GET**</span></span> | <span data-ttu-id="b92d5-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagesummary HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b92d5-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/usagesummary HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="b92d5-129">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="b92d5-129">URI parameter</span></span>

<span data-ttu-id="b92d5-130">Deze tabel bevat de vereiste queryparameter om de beoordeelde gebruiksgegevens van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="b92d5-130">This table lists the required query parameter to get the customer's rated usage information.</span></span>

| <span data-ttu-id="b92d5-131">Naam</span><span class="sxs-lookup"><span data-stu-id="b92d5-131">Name</span></span>                   | <span data-ttu-id="b92d5-132">Type</span><span class="sxs-lookup"><span data-stu-id="b92d5-132">Type</span></span>     | <span data-ttu-id="b92d5-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="b92d5-133">Required</span></span> | <span data-ttu-id="b92d5-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b92d5-134">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="b92d5-135">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="b92d5-135">**customer-tenant-id**</span></span> | <span data-ttu-id="b92d5-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="b92d5-136">**guid**</span></span> | <span data-ttu-id="b92d5-137">J</span><span class="sxs-lookup"><span data-stu-id="b92d5-137">Y</span></span>        | <span data-ttu-id="b92d5-138">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="b92d5-138">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="b92d5-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="b92d5-139">Request headers</span></span>

<span data-ttu-id="b92d5-140">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="b92d5-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b92d5-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="b92d5-141">Request body</span></span>

<span data-ttu-id="b92d5-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="b92d5-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b92d5-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b92d5-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="b92d5-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="b92d5-144">REST response</span></span>

<span data-ttu-id="b92d5-145">Als dit lukt, retourneert deze methode een **CustomerUsageSummary-resource** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="b92d5-145">If successful, this method returns a **CustomerUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b92d5-146">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="b92d5-146">Response success and error codes</span></span>

<span data-ttu-id="b92d5-147">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="b92d5-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b92d5-148">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="b92d5-148">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="b92d5-149">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="b92d5-149">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscription"></a><span data-ttu-id="b92d5-150">Voorbeeld van een Microsoft Azure (MS-AZR-0145P)</span><span class="sxs-lookup"><span data-stu-id="b92d5-150">Response example for Microsoft Azure (MS-AZR-0145P) subscription</span></span>

<span data-ttu-id="b92d5-151">In dit voorbeeld heeft de klant een **Azure PayG-aanbieding van 145P** aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="b92d5-151">In this example, the customer purchased a **145P Azure PayG** offer.</span></span>

<span data-ttu-id="b92d5-152">*Voor klanten met Microsoft Azure-abonnementen (MS-AZR-0145P) is er geen wijziging in het API-antwoord.*</span><span class="sxs-lookup"><span data-stu-id="b92d5-152">*For customers with Microsoft Azure (MS-AZR-0145P) subscriptions, there will be no change to the API response.*</span></span>

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

### <a name="response-example-for-azure-plan"></a><span data-ttu-id="b92d5-153">Voorbeeld van een reactie voor Azure-plan</span><span class="sxs-lookup"><span data-stu-id="b92d5-153">Response example for Azure plan</span></span>

<span data-ttu-id="b92d5-154">In dit voorbeeld heeft de klant een Azure-abonnement aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="b92d5-154">In this example, the customer purchased an Azure plan.</span></span>

<span data-ttu-id="b92d5-155">*Voor klanten met Azure-abonnementen zijn er de volgende wijzigingen in het API-antwoord:*</span><span class="sxs-lookup"><span data-stu-id="b92d5-155">*For customers with Azure plans, there are the following changes to the API response:*</span></span>

- <span data-ttu-id="b92d5-156">**currencyLocale** is vervangen door **currencyCode**</span><span class="sxs-lookup"><span data-stu-id="b92d5-156">**currencyLocale** is replaced with **currencyCode**</span></span>
- <span data-ttu-id="b92d5-157">**usdTotalCost** is een nieuw veld</span><span class="sxs-lookup"><span data-stu-id="b92d5-157">**usdTotalCost** is a new field</span></span>

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
