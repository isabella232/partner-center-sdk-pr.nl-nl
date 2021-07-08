---
title: Gebruiksrecords voor alle klanten op halen
description: U kunt de resourceverzameling CustomerMonthlyUsageRecord gebruiken om gebruiksrecords op te halen voor alle klanten die een specifieke Azure-service of -resource hebben aangeschaft.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6b3fb0e1989336810f2afcc2a5bfc3a1d2849b7f
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874887"
---
# <a name="get-usage-records-for-all-customers"></a><span data-ttu-id="e2490-103">Gebruiksrecords voor alle klanten op halen</span><span class="sxs-lookup"><span data-stu-id="e2490-103">Get usage records for all customers</span></span>

<span data-ttu-id="e2490-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e2490-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e2490-105">Partners kunnen de **resourceverzameling CustomerMonthlyUsageRecord** gebruiken om gebruiksrecords voor al hun klanten op te halen.</span><span class="sxs-lookup"><span data-stu-id="e2490-105">Partners can use the **CustomerMonthlyUsageRecord** resource collection to get usage records for all their customers.</span></span> <span data-ttu-id="e2490-106">Deze resource vertegenwoordigt gebruiksrecords voor alle klanten.</span><span class="sxs-lookup"><span data-stu-id="e2490-106">This resource represents usage records for all customers.</span></span> <span data-ttu-id="e2490-107">Dit geldt ook voor klanten met een Microsoft Azure (MS-AZR-0145P) of een Azure-abonnement.</span><span class="sxs-lookup"><span data-stu-id="e2490-107">That includes those customers with a Microsoft Azure (MS-AZR-0145P) subscription or an Azure plan.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e2490-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e2490-108">Prerequisites</span></span>

- <span data-ttu-id="e2490-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e2490-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e2490-110">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e2490-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e2490-111">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e2490-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e2490-112">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="e2490-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e2490-113">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="e2490-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e2490-114">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="e2490-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e2490-115">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="e2490-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e2490-116">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e2490-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="e2490-117">C\#</span><span class="sxs-lookup"><span data-stu-id="e2490-117">C\#</span></span>

<span data-ttu-id="e2490-118">Alle gebruiksrecords op te halen voor alle klanten die een specifieke Azure-service of -resource hebben aangeschaft tijdens de huidige factureringsperiode:</span><span class="sxs-lookup"><span data-stu-id="e2490-118">To get all the usage records for all customers who purchased a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="e2490-119">Gebruik de **verzameling IAggregatePartner.Customers om** de **methode ById() aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="e2490-119">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="e2490-120">Roep **de eigenschap UsageRecords** aan en roep vervolgens de **methode Get()** of **GetAsync()** aan.</span><span class="sxs-lookup"><span data-stu-id="e2490-120">Call **UsageRecords** property, then call the **Get()** or **GetAsync()** method.</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;
    var usageRecords = partnerOperations.Customers.UsageRecords.Get();
    ```

<span data-ttu-id="e2490-121">Zie het volgende voorbeeld voor een voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="e2490-121">For an example, see the following sample:</span></span>

- <span data-ttu-id="e2490-122">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="e2490-122">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="e2490-123">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="e2490-123">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="e2490-124">Klasse: **GetCustomerUsageRecords.cs**</span><span class="sxs-lookup"><span data-stu-id="e2490-124">Class: **GetCustomerUsageRecords.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="e2490-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e2490-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e2490-126">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e2490-126">Request syntax</span></span>

| <span data-ttu-id="e2490-127">Methode</span><span class="sxs-lookup"><span data-stu-id="e2490-127">Method</span></span>  | <span data-ttu-id="e2490-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e2490-128">Request URI</span></span>                                                                   |
|---------|-------------------------------------------------------------------------------|
| <span data-ttu-id="e2490-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e2490-129">**GET**</span></span> | <span data-ttu-id="e2490-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/usagerecords HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e2490-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/usagerecords HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e2490-131">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e2490-131">Request headers</span></span>

<span data-ttu-id="e2490-132">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e2490-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e2490-133">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e2490-133">Request body</span></span>

<span data-ttu-id="e2490-134">Geen.</span><span class="sxs-lookup"><span data-stu-id="e2490-134">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e2490-135">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e2490-135">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/usagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="e2490-136">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e2490-136">REST response</span></span>

<span data-ttu-id="e2490-137">Als dit is gelukt, retourneert deze methode een **CustomerMonthlyUsageRecord-resource** in de hoofd body van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="e2490-137">If successful, this method returns a **CustomerMonthlyUsageRecord** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e2490-138">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e2490-138">Response success and error codes</span></span>

<span data-ttu-id="e2490-139">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e2490-139">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e2490-140">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e2490-140">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="e2490-141">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e2490-141">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e2490-142">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e2490-142">Response example</span></span>

<span data-ttu-id="e2490-143">U kunt de eigenschap **isUpgraded gebruiken om** klanten te identificeren die een Azure-plan hebben.</span><span class="sxs-lookup"><span data-stu-id="e2490-143">You can use the **isUpgraded** property to identify customers who have an Azure plan.</span></span> <span data-ttu-id="e2490-144">Als de waarde voor **isUpgraded** **true** is, betekent dit dat de klanten Azure-plannen hebben.</span><span class="sxs-lookup"><span data-stu-id="e2490-144">If the value for **isUpgraded** is **true**, it means the customers have Azure plans.</span></span>

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
