---
title: Alle maandelijkse gebruiksrecords voor een abonnement ophalen
description: U kunt de resourceverzameling AzureResourceMonthlyUsageRecord gebruiken om een lijst met services op te halen binnen het abonnement van een klant en de bijbehorende beoordeelde gebruiksgegevens.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: ee4bd413eec7d5a2dddbe3803df8839589ab7504
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760280"
---
# <a name="get-all-monthly-usage-records-for-a-subscription"></a><span data-ttu-id="7045d-103">Alle maandelijkse gebruiksrecords voor een abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="7045d-103">Get all monthly usage records for a subscription</span></span>

<span data-ttu-id="7045d-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7045d-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7045d-105">U kunt de resourceverzameling [**AzureResourceMonthlyUsageRecord**](/dotnet/api/microsoft.store.partnercenter.models.usage.azureresourcemonthlyusagerecord) gebruiken om een lijst met services op te halen binnen het abonnement van een klant en de bijbehorende beoordeelde gebruiksgegevens.</span><span class="sxs-lookup"><span data-stu-id="7045d-105">You can use the [**AzureResourceMonthlyUsageRecord**](/dotnet/api/microsoft.store.partnercenter.models.usage.azureresourcemonthlyusagerecord) resource collection to get a list of services within a customer's subscription and their associated rated usage information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7045d-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7045d-106">Prerequisites</span></span>

- <span data-ttu-id="7045d-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7045d-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7045d-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="7045d-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="7045d-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7045d-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7045d-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="7045d-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7045d-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="7045d-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7045d-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="7045d-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7045d-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="7045d-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7045d-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7045d-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7045d-115">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="7045d-115">A subscription identifier.</span></span>

<span data-ttu-id="7045d-116">*Deze API ondersteunt alleen Microsoft Azure (MS-AZR-0145P) abonnementen. Als u een Azure-abonnement gebruikt, zie in [plaats daarvan Gebruiksgegevens voor abonnement per meter](get-a-customer-subscription-meter-usage-records.md) op halen.*</span><span class="sxs-lookup"><span data-stu-id="7045d-116">*This API only supports Microsoft Azure (MS-AZR-0145P) subscriptions. If you are using an Azure plan, see [Get usage data for subscription by meter](get-a-customer-subscription-meter-usage-records.md) instead.*</span></span>

## <a name="c"></a><span data-ttu-id="7045d-117">C\#</span><span class="sxs-lookup"><span data-stu-id="7045d-117">C\#</span></span>

<span data-ttu-id="7045d-118">Informatie over het resourcegebruik van een abonnement verkrijgen:</span><span class="sxs-lookup"><span data-stu-id="7045d-118">To get a subscription's resource usage information:</span></span>

1. <span data-ttu-id="7045d-119">Gebruik de **verzameling IAggregatePartner.Customers om** de **methode ById() aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="7045d-119">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="7045d-120">Roep de **eigenschap Abonnementen** en **UsageRecords** aan en vervolgens de **eigenschap Resources.**</span><span class="sxs-lookup"><span data-stu-id="7045d-120">Call the **Subscriptions** property, and **UsageRecords**, then the **Resources** property.</span></span>
3. <span data-ttu-id="7045d-121">Roep de **methoden Get()** of **GetAsync()** aan.</span><span class="sxs-lookup"><span data-stu-id="7045d-121">Call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// var selectedSubscriptionID as string;

var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Resources.Get();
```

<span data-ttu-id="7045d-122">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="7045d-122">For an example, see the following:</span></span>

- <span data-ttu-id="7045d-123">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="7045d-123">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="7045d-124">Project: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="7045d-124">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="7045d-125">Klasse: **SubscriptionResourceUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="7045d-125">Class: **SubscriptionResourceUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="7045d-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7045d-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7045d-127">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="7045d-127">Request syntax</span></span>

| <span data-ttu-id="7045d-128">Methode</span><span class="sxs-lookup"><span data-stu-id="7045d-128">Method</span></span>  | <span data-ttu-id="7045d-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7045d-129">Request URI</span></span>                                                                                                                                       |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7045d-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7045d-130">**GET**</span></span> | <span data-ttu-id="7045d-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/usagerecords/resources HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7045d-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/usagerecords/resources HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="7045d-132">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="7045d-132">URI parameters</span></span>

<span data-ttu-id="7045d-133">Deze tabel bevat de vereiste queryparameters om de beoordeelde gebruiksgegevens op te halen.</span><span class="sxs-lookup"><span data-stu-id="7045d-133">This table lists the required query parameters to get the rated usage information.</span></span>

| <span data-ttu-id="7045d-134">Naam</span><span class="sxs-lookup"><span data-stu-id="7045d-134">Name</span></span>                    | <span data-ttu-id="7045d-135">Type</span><span class="sxs-lookup"><span data-stu-id="7045d-135">Type</span></span>     | <span data-ttu-id="7045d-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="7045d-136">Required</span></span> | <span data-ttu-id="7045d-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7045d-137">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="7045d-138">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="7045d-138">**customer-tenant-id**</span></span>  | <span data-ttu-id="7045d-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="7045d-139">**guid**</span></span> | <span data-ttu-id="7045d-140">J</span><span class="sxs-lookup"><span data-stu-id="7045d-140">Y</span></span>        | <span data-ttu-id="7045d-141">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="7045d-141">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="7045d-142">**subscription-id**</span><span class="sxs-lookup"><span data-stu-id="7045d-142">**subscription-id**</span></span> | <span data-ttu-id="7045d-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="7045d-143">**guid**</span></span> | <span data-ttu-id="7045d-144">J</span><span class="sxs-lookup"><span data-stu-id="7045d-144">Y</span></span>        | <span data-ttu-id="7045d-145">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="7045d-145">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="7045d-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7045d-146">Request headers</span></span>

<span data-ttu-id="7045d-147">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="7045d-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7045d-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7045d-148">Request body</span></span>

<span data-ttu-id="7045d-149">Geen.</span><span class="sxs-lookup"><span data-stu-id="7045d-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7045d-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7045d-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/usagerecords/resources HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 65b26053-37d0-4303-9fd1-46ad8012bcb6
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="7045d-151">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7045d-151">REST response</span></span>

<span data-ttu-id="7045d-152">Als dit lukt, retourneert deze methode een verzameling **AzureResourceMonthlyUsageRecord-resources** in de hoofdbestel van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="7045d-152">If successful, this method returns a collection of **AzureResourceMonthlyUsageRecord** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7045d-153">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="7045d-153">Response success and error codes</span></span>

<span data-ttu-id="7045d-154">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="7045d-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7045d-155">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7045d-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7045d-156">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="7045d-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7045d-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="7045d-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 12014
Content-Type: application/json
MS-CorrelationId: 648a26a4-a63e-459f-844b-4f29d7913353
MS-RequestId: be82a8ba-4a53-49f7-8313-b033c058687e
Date: Tue, 10 Nov 2015 19:09:59 GMT

{
    "totalCount":20,
    "items":[{
        "category":"Storage",
        "subcategory":"LOCALLY REDUNDANT",
        "quantityUsed":0.151287527825352,
        "unit":"GB",
        "id":"2a2419c0-cefe-46b2-8004-8eb002ad606c",
        "name":"Azure Resource 1",
        "totalCost":0.195779159290613,
        "currencyLocale":"en-US",
        "attributes":{
            "objectType":"AzureResourceMonthlyUsageRecord"
        }
    },
    {
        "category":"Remote App",
        "subcategory":"Remote App",
        "quantityUsed":0.932546524299563,
        "unit":"GB",
        "id":"7e4099c8-2b3d-41a6-a1bd-d5cf315989b2",
        "name":"Azure Resource 2",
        "totalCost":0.920983775016379,
        "currencyLocale":"en-US",
        "attributes":{
            "objectType":"AzureResourceMonthlyUsageRecord"
        }
    }],
    "links":{
        "self":{
            "uri":"/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription>%20/usagerecords",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "objectType":"Collection"
    }
}
```
