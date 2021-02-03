---
title: Een samen vatting van het gebruik van een partner ophalen
description: U kunt de PartnerUsageSummary-Resource gebruiken om een samen vatting van een partner gebruik te krijgen van alle klanten die tijdens de huidige facturerings periode een specifieke Azure-service of resource hebben aangeschaft.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: ba1885f46043a75274595239fe61ce3ef0998acf
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767273"
---
# <a name="get-a-usage-summary-for-a-partner"></a><span data-ttu-id="ef891-103">Een samen vatting van het gebruik van een partner ophalen</span><span class="sxs-lookup"><span data-stu-id="ef891-103">Get a usage summary for a partner</span></span>

<span data-ttu-id="ef891-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="ef891-104">**Applies to:**</span></span>

- <span data-ttu-id="ef891-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="ef891-105">Partner Center</span></span>
- <span data-ttu-id="ef891-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="ef891-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="ef891-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ef891-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ef891-108">U kunt de **PartnerUsageSummary** -Resource gebruiken om een samen vatting van een partner gebruik te krijgen van alle klanten die tijdens de huidige facturerings periode een specifieke Azure-service of resource hebben aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="ef891-108">You can use the **PartnerUsageSummary** resource to get a partner usage summary of all customers that purchased a specific Azure service or resource during the current billing period.</span></span>

<span data-ttu-id="ef891-109">*Het totaal dat door deze API wordt geretourneerd, retourneert geen verbruik voor klanten die een Azure-abonnement hebben.*</span><span class="sxs-lookup"><span data-stu-id="ef891-109">*The total returned by this API will not return consumption for customers that have an Azure plan.*</span></span> <span data-ttu-id="ef891-110">In de toekomst gepland voor afschaffing.</span><span class="sxs-lookup"><span data-stu-id="ef891-110">Planned for deprecation in the future.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ef891-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ef891-111">Prerequisites</span></span>

- <span data-ttu-id="ef891-112">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ef891-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ef891-113">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="ef891-113">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="ef891-114">C\#</span><span class="sxs-lookup"><span data-stu-id="ef891-114">C\#</span></span>

<span data-ttu-id="ef891-115">Voor een overzicht van het gebruik van alle klanten die een specifieke Azure-service of-resource hebben gekocht tijdens de huidige facturerings periode:</span><span class="sxs-lookup"><span data-stu-id="ef891-115">To get a usage summary for all customers that purchased a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="ef891-116">Gebruik uw **IAggregatePartner**.</span><span class="sxs-lookup"><span data-stu-id="ef891-116">Use your **IAggregatePartner**.</span></span>

2. <span data-ttu-id="ef891-117">Roep de eigenschap **UsageSummary** aan, gevolgd door de methoden **Get ()** of **GetAsync ()** :</span><span class="sxs-lookup"><span data-stu-id="ef891-117">Call the **UsageSummary** property, followed by the **Get()** or **GetAsync()** methods:</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;

    var usageSummary = partnerOperations.UsageSummary.Get();
    ```

<span data-ttu-id="ef891-118">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="ef891-118">For an example, see the following:</span></span>

- <span data-ttu-id="ef891-119">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="ef891-119">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="ef891-120">Project: **PartnerSDK. FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="ef891-120">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="ef891-121">Klasse: **GetPartnerUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="ef891-121">Class: **GetPartnerUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="ef891-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ef891-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ef891-123">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ef891-123">Request syntax</span></span>

| <span data-ttu-id="ef891-124">Methode</span><span class="sxs-lookup"><span data-stu-id="ef891-124">Method</span></span>  | <span data-ttu-id="ef891-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ef891-125">Request URI</span></span>                                                         |
|---------|---------------------------------------------------------------------|
| <span data-ttu-id="ef891-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ef891-126">**GET**</span></span> | <span data-ttu-id="ef891-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/usagesummary http/1.1</span><span class="sxs-lookup"><span data-stu-id="ef891-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/usagesummary HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="ef891-128">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ef891-128">Request headers</span></span>

<span data-ttu-id="ef891-129">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="ef891-129">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ef891-130">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ef891-130">Request body</span></span>

<span data-ttu-id="ef891-131">Geen.</span><span class="sxs-lookup"><span data-stu-id="ef891-131">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ef891-132">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ef891-132">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="ef891-133">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ef891-133">REST response</span></span>

<span data-ttu-id="ef891-134">Als dit lukt, retourneert deze methode een **PartnerUsageSummary** -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="ef891-134">If successful, this method returns a **PartnerUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ef891-135">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="ef891-135">Response success and error codes</span></span>

<span data-ttu-id="ef891-136">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="ef891-136">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ef891-137">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ef891-137">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="ef891-138">Zie [fout codes](error-codes.md)voor een volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="ef891-138">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ef891-139">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ef891-139">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "customersOverBudget": 1,
    "customersTrendingOver": 0,
    "customersWithUsageBasedSubscription": 11,
    "resourceId": "11111111-4574-4539-bc42-0e539b9684c0",
    "id": "11111111-4574-4539-bc42-0e539b9684c0",
    "resourceName": "PLAMUATT2NETNEW",
    "name": "PLAMUATT2NETNEW",
    "billingStartDate": "2019-08-28T00:00:00-07:00",
    "billingEndDate": "2019-09-27T00:00:00-07:00",
    "totalCost": 22.861172,
    "currencyLocale": "fr-FR",
    "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
    "links": {
        "self": {
            "uri": "/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "PartnerUsageSummary"
    }
}
```
