---
title: De MFA-acceptatiestatus op halen
description: Haal een lijst op van de acceptatiestatus voor meervoudige verificatie voor elke partner met behulp van de Partner REST API.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
author: amitravat
ms.author: amrava
ms.openlocfilehash: 9b8848c2a4531dd6609f86aae6876cec436eeea9
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760518"
---
# <a name="get-mfa-adoption-status"></a><span data-ttu-id="9f33c-103">MFA-acceptatiestatus krijgen</span><span class="sxs-lookup"><span data-stu-id="9f33c-103">Get MFA adoption status</span></span>

<span data-ttu-id="9f33c-104">**Van toepassing op**: Partner Center API</span><span class="sxs-lookup"><span data-stu-id="9f33c-104">**Applies to**: Partner Center API</span></span>

<span data-ttu-id="9f33c-105">In dit artikel wordt uitgelegd hoe u de MFA-acceptatiestatus (Multi-Factor Authentication) kunt krijgen voor elke partner binnen een tenant.</span><span class="sxs-lookup"><span data-stu-id="9f33c-105">This article explains how to get the multi-factor authentication (MFA) adoption status for each partner within a tenant.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9f33c-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9f33c-106">Prerequisites</span></span>

- <span data-ttu-id="9f33c-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9f33c-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9f33c-108">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="9f33c-108">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="9f33c-109">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9f33c-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9f33c-110">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="9f33c-110">Request syntax</span></span>

| <span data-ttu-id="9f33c-111">Methode</span><span class="sxs-lookup"><span data-stu-id="9f33c-111">Method</span></span>  | <span data-ttu-id="9f33c-112">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="9f33c-112">Request URI</span></span>                                                               |
|---------|---------------------------------------------------------------------------|
| <span data-ttu-id="9f33c-113">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="9f33c-113">**GET**</span></span> | <span data-ttu-id="9f33c-114">[*{baseURL}*](partner-center-rest-urls.md)/v1/applicationmfaadoptionstatus></span><span class="sxs-lookup"><span data-stu-id="9f33c-114">[*{baseURL}*](partner-center-rest-urls.md)/v1/applicationmfaadoptionstatus></span></span> |

### <a name="request-headers"></a><span data-ttu-id="9f33c-115">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9f33c-115">Request headers</span></span>

- <span data-ttu-id="9f33c-116">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="9f33c-116">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9f33c-117">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9f33c-117">Request body</span></span>

<span data-ttu-id="9f33c-118">Geen.</span><span class="sxs-lookup"><span data-stu-id="9f33c-118">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="9f33c-119">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9f33c-119">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/applicationmfaadoptionstatus HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Type: application/json
```

## <a name="rest-response"></a><span data-ttu-id="9f33c-120">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9f33c-120">REST response</span></span>

<span data-ttu-id="9f33c-121">Als dit lukt, retourneert deze methode een verzameling [API-aanvragen, samengevat door Toepassingsresources](mfa-resources.md#api-request-summarized-by-application) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="9f33c-121">If successful, this method returns a collection of [API request summarized by Application](mfa-resources.md#api-request-summarized-by-application) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9f33c-122">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="9f33c-122">Response success and error codes</span></span>

<span data-ttu-id="9f33c-123">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="9f33c-123">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9f33c-124">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9f33c-124">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9f33c-125">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="9f33c-125">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9f33c-126">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9f33c-126">Response example</span></span>

``` http
HTTP/1.1 200 OK
Content-Length: 313
Content-Type: application/json
MS-CorrelationId: 4cb80cbe-566b-4d8b-8b8f-af1454b73089
MS-RequestId: 566330a7-1e4b-4848-9c23-f135c70fd810
Date: Thu, 21 May 2020 22:29:17 GMT
[
    {
        "loginDate": "2020-05-20",
        "mfaCompliantRequestCount": 7,
        "totalRequestCount": 7,
        "applicationId": "14f38d7d-c4fc-448a-b2df-0fc60e75465a",
        "applicationName": ""
    },
    {
        "loginDate": "2020-05-19",
        "mfaCompliantRequestCount": 7,
        "totalRequestCount": 14,
        "applicationId": "60a00bf2-0644-4279-83b3-87ddf96f2509",
        "applicationName": ""
    }
]
```
