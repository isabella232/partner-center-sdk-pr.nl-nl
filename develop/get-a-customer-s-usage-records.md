---
title: Gebruiks records voor alle klanten ophalen
description: U kunt de resource verzameling CustomerMonthlyUsageRecord gebruiken om gebruiks records op te halen voor alle klanten die een specifieke Azure-service of-resource hebben gekocht.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: da829a6de3690a9b1117ce9dfa58fbe381cafd81
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767314"
---
# <a name="get-usage-records-for-all-customers"></a><span data-ttu-id="cc59a-103">Gebruiks records voor alle klanten ophalen</span><span class="sxs-lookup"><span data-stu-id="cc59a-103">Get usage records for all customers</span></span>

<span data-ttu-id="cc59a-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="cc59a-104">**Applies to:**</span></span>

- <span data-ttu-id="cc59a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="cc59a-105">Partner Center</span></span>
- <span data-ttu-id="cc59a-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="cc59a-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="cc59a-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="cc59a-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="cc59a-108">Partners kunnen de resource verzameling **CustomerMonthlyUsageRecord** gebruiken om gebruiks records voor al hun klanten op te halen.</span><span class="sxs-lookup"><span data-stu-id="cc59a-108">Partners can use the **CustomerMonthlyUsageRecord** resource collection to get usage records for all their customers.</span></span> <span data-ttu-id="cc59a-109">Deze resource vertegenwoordigt gebruiks records voor alle klanten.</span><span class="sxs-lookup"><span data-stu-id="cc59a-109">This resource represents usage records for all customers.</span></span> <span data-ttu-id="cc59a-110">Deze klanten bevatten een Microsoft Azure (MS-AZR-0145P) of een Azure-abonnement.</span><span class="sxs-lookup"><span data-stu-id="cc59a-110">That includes those customers with a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc59a-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cc59a-111">Prerequisites</span></span>

- <span data-ttu-id="cc59a-112">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cc59a-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cc59a-113">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="cc59a-113">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="cc59a-114">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cc59a-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="cc59a-115">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="cc59a-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="cc59a-116">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="cc59a-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="cc59a-117">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="cc59a-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="cc59a-118">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="cc59a-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="cc59a-119">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cc59a-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="cc59a-120">C\#</span><span class="sxs-lookup"><span data-stu-id="cc59a-120">C\#</span></span>

<span data-ttu-id="cc59a-121">Alle gebruiks records ophalen voor alle klanten die tijdens de huidige facturerings periode een specifieke Azure-service of resource hebben gekocht:</span><span class="sxs-lookup"><span data-stu-id="cc59a-121">To get all the usage records for all customers who purchased a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="cc59a-122">Gebruik uw verzameling **IAggregatePartner. Customers** om de methode **ById ()** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="cc59a-122">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="cc59a-123">Roep de eigenschap **UsageRecords** aan en roep vervolgens de methode **Get ()** of **GetAsync ()** aan.</span><span class="sxs-lookup"><span data-stu-id="cc59a-123">Call **UsageRecords** property, then call the **Get()** or **GetAsync()** method.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    var usageRecords = partnerOperations.Customers.UsageRecords.Get();
    ```

<span data-ttu-id="cc59a-124">Zie het volgende voor beeld:</span><span class="sxs-lookup"><span data-stu-id="cc59a-124">For an example, see the following sample:</span></span>

- <span data-ttu-id="cc59a-125">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="cc59a-125">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="cc59a-126">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="cc59a-126">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="cc59a-127">Klasse: **GetCustomerUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="cc59a-127">Class: **GetCustomerUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="cc59a-128">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="cc59a-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cc59a-129">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cc59a-129">Request syntax</span></span>

| <span data-ttu-id="cc59a-130">Methode</span><span class="sxs-lookup"><span data-stu-id="cc59a-130">Method</span></span>  | <span data-ttu-id="cc59a-131">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="cc59a-131">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="cc59a-132">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="cc59a-132">**GET**</span></span> | <span data-ttu-id="cc59a-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/usagerecords http/1.1</span><span class="sxs-lookup"><span data-stu-id="cc59a-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/usagerecords HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="cc59a-134">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="cc59a-134">Request headers</span></span>

<span data-ttu-id="cc59a-135">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cc59a-135">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cc59a-136">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="cc59a-136">Request body</span></span>

<span data-ttu-id="cc59a-137">Geen.</span><span class="sxs-lookup"><span data-stu-id="cc59a-137">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="cc59a-138">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cc59a-138">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/usagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="cc59a-139">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="cc59a-139">REST response</span></span>

<span data-ttu-id="cc59a-140">Als dit lukt, retourneert deze methode een **CustomerMonthlyUsageRecord** -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="cc59a-140">If successful, this method returns a **CustomerMonthlyUsageRecord** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cc59a-141">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="cc59a-141">Response success and error codes</span></span>

<span data-ttu-id="cc59a-142">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="cc59a-142">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cc59a-143">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="cc59a-143">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="cc59a-144">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="cc59a-144">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cc59a-145">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="cc59a-145">Response example</span></span>

<span data-ttu-id="cc59a-146">U kunt de eigenschap **isUpgraded** gebruiken om klanten te identificeren die een Azure-abonnement hebben.</span><span class="sxs-lookup"><span data-stu-id="cc59a-146">You can use the **isUpgraded** property to identify customers who have an Azure plan.</span></span> <span data-ttu-id="cc59a-147">Als de waarde voor **isUpgraded** **True** is, betekent dit dat de klanten Azure-abonnementen hebben.</span><span class="sxs-lookup"><span data-stu-id="cc59a-147">If the value for **isUpgraded** is **true**, it means the customers have Azure plans.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 25,
    "items": [
        {
            "budget": {
                "attributes": {
                    "objectType": "SpendingBudget"
                }
            },
            "customerSpendingBudget": {
                "attributes": {
                    "objectType": "SpendingBudget"
                }
            },
            "percentUsed": 0,
            "isUpgraded": false,
            "resourceId": "11111111-1843-4b3b-872f-206e08a08e51",
            "id": "11111111-1843-4b3b-872f-206e08a08e51",
            "resourceName": "LEGACY AZURE CUSTOMER SE",
            "name": "LEGACY AZURE CUSTOMER SE",
            "totalCost": 0,
            "currencyLocale": "fr-FR",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-08-01T23:00:16.57+00:00",
            "attributes": {
                "objectType": "CustomerMonthlyUsageRecord"
            }
        },
        {
            "budget": {
                "amount": 20,
                "attributes": {
                    "objectType": "SpendingBudget"
                }
            },
            "percentUsed": 602.84,
            "isUpgraded": true,
            "resourceId": "11111111-6fb9-4b05-8f15-b3d72e0596e6",
            "id": "11111111-6fb9-4b05-8f15-b3d72e0596e6",
            "resourceName": "Modern Azure Customer SE",
            "name": "Modern Azure Customer SE",
            "totalCost": 120.5682999999995904716,
            "currencyCode": "SEK",
            "usdTotalCost": 12.39999999999999985235,
            "lastModifiedDate": "2019-09-17T17:08:11.1433333+00:00",
            "attributes": {
                "objectType": "CustomerMonthlyUsageRecord"
            }
        },
        {
            "budget": {
                "attributes": {
                    "objectType": "SpendingBudget"
                }
            },
            "percentUsed": 0,
            "isUpgraded": true,
            "resourceId": "11111111-5892-4326-8541-9da1fdb233fb",
            "id": "11111111-5892-4326-8541-9da1fdb233fb",
            "resourceName": "Test_Test_MA20190829_14",
            "name": "Test_Test_MA20190829_14",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T17:08:11.1433333+00:00",
            "attributes": {
                "objectType": "CustomerMonthlyUsageRecord"
            }
        },
           {
            "budget": {
                "amount": 97,
                "attributes": {
                    "objectType": "SpendingBudget"
                }
            },
            "percentUsed": 28.08,
            "isUpgraded": true,
            "resourceId": "11111111-641b-4c53-b7fc-0f2bfca8a581",
            "id": "11111111-641b-4c53-b7fc-0f2bfca8a581",
            "resourceName": "Modern Azure Customer UK",
            "name": "Modern Azure Customer UK",
            "totalCost": 27.23292827625710931604,
            "currencyCode": "GBP",
            "usdTotalCost": 33.280000000000001044,
            "lastModifiedDate": "2019-09-17T17:08:11.1433333+00:00",
            "attributes": {
                "objectType": "CustomerMonthlyUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/usagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
