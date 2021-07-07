---
title: Een gebruiksoverzicht voor een partner krijgen
description: U kunt de resource PartnerUsageSummary gebruiken om een samenvatting van het gebruik van partners te krijgen van alle klanten die een specifieke Azure-service of -resource hebben aangeschaft tijdens de huidige factureringsperiode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: f003980f1b521ad0ac26dbfd0d4821b9096fdd27
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873901"
---
# <a name="get-a-usage-summary-for-a-partner"></a><span data-ttu-id="1a7b2-103">Een gebruiksoverzicht voor een partner krijgen</span><span class="sxs-lookup"><span data-stu-id="1a7b2-103">Get a usage summary for a partner</span></span>

<span data-ttu-id="1a7b2-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1a7b2-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1a7b2-105">U kunt de resource **PartnerUsageSummary** gebruiken om een samenvatting van het gebruik van partners te krijgen van alle klanten die een specifieke Azure-service of -resource hebben aangeschaft tijdens de huidige factureringsperiode.</span><span class="sxs-lookup"><span data-stu-id="1a7b2-105">You can use the **PartnerUsageSummary** resource to get a partner usage summary of all customers that purchased a specific Azure service or resource during the current billing period.</span></span>

<span data-ttu-id="1a7b2-106">*Het totaal dat door deze API wordt geretourneerd, retourneerd geen verbruik voor klanten die een Azure-plan hebben.*</span><span class="sxs-lookup"><span data-stu-id="1a7b2-106">*The total returned by this API will not return consumption for customers that have an Azure plan.*</span></span> <span data-ttu-id="1a7b2-107">Gepland voor afschaffing in de toekomst.</span><span class="sxs-lookup"><span data-stu-id="1a7b2-107">Planned for deprecation in the future.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1a7b2-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1a7b2-108">Prerequisites</span></span>

- <span data-ttu-id="1a7b2-109">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="1a7b2-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1a7b2-110">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="1a7b2-110">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="1a7b2-111">C\#</span><span class="sxs-lookup"><span data-stu-id="1a7b2-111">C\#</span></span>

<span data-ttu-id="1a7b2-112">Ga als volgt te werk om een gebruiksoverzicht te krijgen voor alle klanten die een specifieke Azure-service of -resource hebben aangeschaft tijdens de huidige factureringsperiode:</span><span class="sxs-lookup"><span data-stu-id="1a7b2-112">To get a usage summary for all customers that purchased a specific Azure service or resource during the current billing period:</span></span>

1. <span data-ttu-id="1a7b2-113">Gebruik uw **IAggregatePartner.**</span><span class="sxs-lookup"><span data-stu-id="1a7b2-113">Use your **IAggregatePartner**.</span></span>

2. <span data-ttu-id="1a7b2-114">Roep de **eigenschap UsageSummary** aan, gevolgd door de **methoden Get()** of **GetAsync()** :</span><span class="sxs-lookup"><span data-stu-id="1a7b2-114">Call the **UsageSummary** property, followed by the **Get()** or **GetAsync()** methods:</span></span>

    ``` csharp
    // IAggregatePartner partnerOperations;

    var usageSummary = partnerOperations.UsageSummary.Get();
    ```

<span data-ttu-id="1a7b2-115">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="1a7b2-115">For an example, see the following:</span></span>

- <span data-ttu-id="1a7b2-116">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="1a7b2-116">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="1a7b2-117">Project: **PartnerSDK.FeatureSamples**</span><span class="sxs-lookup"><span data-stu-id="1a7b2-117">Project: **PartnerSDK.FeatureSamples**</span></span>
- <span data-ttu-id="1a7b2-118">Klasse: **GetPartnerUsageSummary.cs**</span><span class="sxs-lookup"><span data-stu-id="1a7b2-118">Class: **GetPartnerUsageSummary.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="1a7b2-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="1a7b2-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1a7b2-120">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="1a7b2-120">Request syntax</span></span>

| <span data-ttu-id="1a7b2-121">Methode</span><span class="sxs-lookup"><span data-stu-id="1a7b2-121">Method</span></span>  | <span data-ttu-id="1a7b2-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="1a7b2-122">Request URI</span></span>                                                         |
|---------|---------------------------------------------------------------------|
| <span data-ttu-id="1a7b2-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="1a7b2-123">**GET**</span></span> | <span data-ttu-id="1a7b2-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/usagesummary HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1a7b2-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/usagesummary HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="1a7b2-125">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="1a7b2-125">Request headers</span></span>

<span data-ttu-id="1a7b2-126">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="1a7b2-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1a7b2-127">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="1a7b2-127">Request body</span></span>

<span data-ttu-id="1a7b2-128">Geen.</span><span class="sxs-lookup"><span data-stu-id="1a7b2-128">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="1a7b2-129">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1a7b2-129">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a><span data-ttu-id="1a7b2-130">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="1a7b2-130">REST response</span></span>

<span data-ttu-id="1a7b2-131">Als dit lukt, retourneert deze methode een **PartnerUsageSummary-resource** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="1a7b2-131">If successful, this method returns a **PartnerUsageSummary** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1a7b2-132">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="1a7b2-132">Response success and error codes</span></span>

<span data-ttu-id="1a7b2-133">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="1a7b2-133">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1a7b2-134">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1a7b2-134">Use a network trace tool to read this code, the error type, and additional parameters.</span></span> <span data-ttu-id="1a7b2-135">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="1a7b2-135">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1a7b2-136">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="1a7b2-136">Response example</span></span>

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
