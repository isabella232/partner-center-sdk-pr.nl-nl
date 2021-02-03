---
title: Alle maandelijkse gebruiks records voor een abonnement ophalen.
description: U kunt de resource verzameling AzureResourceMonthlyUsageRecord gebruiken om een lijst met services te verkrijgen binnen het abonnement van een klant en de bijbehorende geclassificeerde gebruiks gegevens.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 1dd09d4976c9626e088cda02ce36669dd7121a99
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767506"
---
# <a name="get-all-monthly-usage-records-for-a-subscription"></a><span data-ttu-id="d4abd-103">Alle maandelijkse gebruiks records voor een abonnement ophalen.</span><span class="sxs-lookup"><span data-stu-id="d4abd-103">Get all monthly usage records for a subscription.</span></span>

<span data-ttu-id="d4abd-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="d4abd-104">**Applies to:**</span></span>

- <span data-ttu-id="d4abd-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d4abd-105">Partner Center</span></span>
- <span data-ttu-id="d4abd-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="d4abd-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="d4abd-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d4abd-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d4abd-108">U kunt de resource verzameling [**AzureResourceMonthlyUsageRecord**](/dotnet/api/microsoft.store.partnercenter.models.usage.azureresourcemonthlyusagerecord) gebruiken om een lijst met services te verkrijgen binnen het abonnement van een klant en de bijbehorende geclassificeerde gebruiks gegevens.</span><span class="sxs-lookup"><span data-stu-id="d4abd-108">You can use the [**AzureResourceMonthlyUsageRecord**](/dotnet/api/microsoft.store.partnercenter.models.usage.azureresourcemonthlyusagerecord) resource collection to get a list of services within a customer's subscription and their associated rated usage information.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d4abd-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d4abd-109">Prerequisites</span></span>

- <span data-ttu-id="d4abd-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d4abd-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d4abd-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="d4abd-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="d4abd-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d4abd-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d4abd-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="d4abd-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d4abd-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="d4abd-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d4abd-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="d4abd-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d4abd-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="d4abd-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d4abd-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d4abd-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="d4abd-118">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="d4abd-118">A subscription identifier.</span></span>

<span data-ttu-id="d4abd-119">*Deze API ondersteunt alleen Microsoft Azure (MS-AZR-0145P)-abonnementen. Als u een Azure-abonnement gebruikt, raadpleegt u in plaats daarvan [gebruiks gegevens voor abonnement op meter ophalen](get-a-customer-subscription-meter-usage-records.md) .*</span><span class="sxs-lookup"><span data-stu-id="d4abd-119">*This API only supports Microsoft Azure (MS-AZR-0145P) subscriptions. If you are using an Azure plan, see [Get usage data for subscription by meter](get-a-customer-subscription-meter-usage-records.md) instead.*</span></span>

## <a name="c"></a><span data-ttu-id="d4abd-120">C\#</span><span class="sxs-lookup"><span data-stu-id="d4abd-120">C\#</span></span>

<span data-ttu-id="d4abd-121">Informatie over het resource gebruik van een abonnement ophalen:</span><span class="sxs-lookup"><span data-stu-id="d4abd-121">To get a subscription's resource usage information:</span></span>

1. <span data-ttu-id="d4abd-122">Gebruik uw verzameling **IAggregatePartner. Customers** om de methode **ById ()** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="d4abd-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="d4abd-123">Roep de eigenschap **abonnementen** aan, evenals **UsageRecords**, en vervolgens de eigenschap **resources** .</span><span class="sxs-lookup"><span data-stu-id="d4abd-123">Call the **Subscriptions** property, as well as **UsageRecords**, then the **Resources** property.</span></span>
3. <span data-ttu-id="d4abd-124">Roep de methoden **Get ()** of **GetAsync ()** aan.</span><span class="sxs-lookup"><span data-stu-id="d4abd-124">Call the **Get()** or **GetAsync()** methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// var selectedSubscriptionID as string;

var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Resources.Get();
```

<span data-ttu-id="d4abd-125">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="d4abd-125">For an example, see the following:</span></span>

- <span data-ttu-id="d4abd-126">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="d4abd-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="d4abd-127">Project: **PartnerSDK. FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="d4abd-127">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="d4abd-128">Klasse: **SubscriptionResourceUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="d4abd-128">Class: **SubscriptionResourceUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="d4abd-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d4abd-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d4abd-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d4abd-130">Request syntax</span></span>

| <span data-ttu-id="d4abd-131">Methode</span><span class="sxs-lookup"><span data-stu-id="d4abd-131">Method</span></span>  | <span data-ttu-id="d4abd-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d4abd-132">Request URI</span></span>                                                                                                                                       |
|---------|---------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d4abd-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="d4abd-133">**GET**</span></span> | <span data-ttu-id="d4abd-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{id-for-Subscription}/usagerecords/resources http/1.1</span><span class="sxs-lookup"><span data-stu-id="d4abd-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/usagerecords/resources HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="d4abd-135">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="d4abd-135">URI parameters</span></span>

<span data-ttu-id="d4abd-136">Deze tabel bevat de vereiste query parameters voor het verkrijgen van de geclassificeerde gebruiks gegevens.</span><span class="sxs-lookup"><span data-stu-id="d4abd-136">This table lists the required query parameters to get the rated usage information.</span></span>

| <span data-ttu-id="d4abd-137">Naam</span><span class="sxs-lookup"><span data-stu-id="d4abd-137">Name</span></span>                    | <span data-ttu-id="d4abd-138">Type</span><span class="sxs-lookup"><span data-stu-id="d4abd-138">Type</span></span>     | <span data-ttu-id="d4abd-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="d4abd-139">Required</span></span> | <span data-ttu-id="d4abd-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d4abd-140">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="d4abd-141">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="d4abd-141">**customer-tenant-id**</span></span>  | <span data-ttu-id="d4abd-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="d4abd-142">**guid**</span></span> | <span data-ttu-id="d4abd-143">J</span><span class="sxs-lookup"><span data-stu-id="d4abd-143">Y</span></span>        | <span data-ttu-id="d4abd-144">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="d4abd-144">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="d4abd-145">**abonnement-id**</span><span class="sxs-lookup"><span data-stu-id="d4abd-145">**subscription-id**</span></span> | <span data-ttu-id="d4abd-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="d4abd-146">**guid**</span></span> | <span data-ttu-id="d4abd-147">J</span><span class="sxs-lookup"><span data-stu-id="d4abd-147">Y</span></span>        | <span data-ttu-id="d4abd-148">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="d4abd-148">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d4abd-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d4abd-149">Request headers</span></span>

<span data-ttu-id="d4abd-150">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d4abd-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d4abd-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="d4abd-151">Request body</span></span>

<span data-ttu-id="d4abd-152">Geen.</span><span class="sxs-lookup"><span data-stu-id="d4abd-152">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d4abd-153">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d4abd-153">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/usagerecords/resources HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 65b26053-37d0-4303-9fd1-46ad8012bcb6
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="d4abd-154">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d4abd-154">REST response</span></span>

<span data-ttu-id="d4abd-155">Als dit lukt, retourneert deze methode een verzameling **AzureResourceMonthlyUsageRecord** -resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="d4abd-155">If successful, this method returns a collection of **AzureResourceMonthlyUsageRecord** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d4abd-156">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="d4abd-156">Response success and error codes</span></span>

<span data-ttu-id="d4abd-157">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="d4abd-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d4abd-158">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d4abd-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d4abd-159">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="d4abd-159">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d4abd-160">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d4abd-160">Response example</span></span>

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
