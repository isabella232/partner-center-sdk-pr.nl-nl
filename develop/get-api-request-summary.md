---
title: De acceptatie status voor MFA ophalen
description: Een lijst met de acceptatie status voor multi-factor Authentication ophalen voor elke partner met behulp van de partner REST API.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
author: amitravat
ms.author: amrava
ms.openlocfilehash: f82d163b704323c81e2948b78eb9b9d1a14ddc52
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767268"
---
# <a name="get-mfa-adoption-status"></a><span data-ttu-id="bc9dd-103">Status van MFA-acceptatie ophalen</span><span class="sxs-lookup"><span data-stu-id="bc9dd-103">Get MFA adoption status</span></span>

<span data-ttu-id="bc9dd-104">Van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="bc9dd-104">Applies to:</span></span>

- <span data-ttu-id="bc9dd-105">Partnercentrum-API</span><span class="sxs-lookup"><span data-stu-id="bc9dd-105">Partner Center API</span></span>

<span data-ttu-id="bc9dd-106">In dit artikel wordt uitgelegd hoe u de acceptatie status van multi-factor Authentication (MFA) kunt ophalen voor elke partner binnen een Tenant.</span><span class="sxs-lookup"><span data-stu-id="bc9dd-106">This article explains how to get the multi-factor authentication (MFA) adoption status for each partner within a tenant.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bc9dd-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bc9dd-107">Prerequisites</span></span>

- <span data-ttu-id="bc9dd-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bc9dd-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bc9dd-109">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="bc9dd-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="bc9dd-110">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="bc9dd-110">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bc9dd-111">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bc9dd-111">Request syntax</span></span>

| <span data-ttu-id="bc9dd-112">Methode</span><span class="sxs-lookup"><span data-stu-id="bc9dd-112">Method</span></span>  | <span data-ttu-id="bc9dd-113">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="bc9dd-113">Request URI</span></span>                                                               |
|---------|---------------------------------------------------------------------------|
| <span data-ttu-id="bc9dd-114">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="bc9dd-114">**GET**</span></span> | <span data-ttu-id="bc9dd-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/applicationmfaadoptionstatus></span><span class="sxs-lookup"><span data-stu-id="bc9dd-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/applicationmfaadoptionstatus></span></span> |

### <a name="request-headers"></a><span data-ttu-id="bc9dd-116">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="bc9dd-116">Request headers</span></span>

- <span data-ttu-id="bc9dd-117">Zie de [rest headers van het Partner Center](headers.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="bc9dd-117">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="bc9dd-118">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="bc9dd-118">Request body</span></span>

<span data-ttu-id="bc9dd-119">Geen.</span><span class="sxs-lookup"><span data-stu-id="bc9dd-119">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="bc9dd-120">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bc9dd-120">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/applicationmfaadoptionstatus HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Type: application/json
```

## <a name="rest-response"></a><span data-ttu-id="bc9dd-121">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="bc9dd-121">REST response</span></span>

<span data-ttu-id="bc9dd-122">Als dit lukt, retourneert deze methode een verzameling [API-aanvragen, samen vatting van toepassings](mfa-resources.md#api-request-summarized-by-application) resources, in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="bc9dd-122">If successful, this method returns a collection of [API request summarized by Application](mfa-resources.md#api-request-summarized-by-application) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bc9dd-123">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="bc9dd-123">Response success and error codes</span></span>

<span data-ttu-id="bc9dd-124">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="bc9dd-124">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bc9dd-125">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="bc9dd-125">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bc9dd-126">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="bc9dd-126">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="bc9dd-127">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="bc9dd-127">Response example</span></span>

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
