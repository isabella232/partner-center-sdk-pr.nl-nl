---
title: Een lijst met alle partner gebruikers aanvragen ophalen
description: Een lijst met alle partner gebruikers aanvragen ophalen met behulp van de partner REST API.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
author: cychua
ms.author: cychua
ms.openlocfilehash: 43b1e3d4a6220ac8adba8eed0389395113072288
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767178"
---
# <a name="get-app-and-user-api-requests"></a><span data-ttu-id="415b8-103">App-en gebruikers-API-aanvragen ophalen</span><span class="sxs-lookup"><span data-stu-id="415b8-103">Get App and User API requests</span></span>

<span data-ttu-id="415b8-104">Van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="415b8-104">Applies to:</span></span>

- <span data-ttu-id="415b8-105">Partnercentrum-API</span><span class="sxs-lookup"><span data-stu-id="415b8-105">Partner Center API</span></span>

<span data-ttu-id="415b8-106">In dit artikel wordt uitgelegd hoe u een lijst met alle partner gebruikers aanvragen binnen een Tenant kunt ophalen met behulp van REST Api's.</span><span class="sxs-lookup"><span data-stu-id="415b8-106">This article explains how to obtain a list of all partner user requests within a tenant using REST APIs.</span></span>

 > [!NOTE]
 > <span data-ttu-id="415b8-107">Deze API retourneert alleen de meest recente API-aanvragen die zijn gemaakt door de APP + gebruikers referentie met een maximale 10.000 limiet.</span><span class="sxs-lookup"><span data-stu-id="415b8-107">This API only returns the most recent API requests made by APP + User credential with maximum 10K limit.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="415b8-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="415b8-108">Prerequisites</span></span>

- <span data-ttu-id="415b8-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="415b8-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="415b8-110">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="415b8-110">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="415b8-111">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="415b8-111">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="415b8-112">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="415b8-112">Request syntax</span></span>

| <span data-ttu-id="415b8-113">Methode</span><span class="sxs-lookup"><span data-stu-id="415b8-113">Method</span></span>  | <span data-ttu-id="415b8-114">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="415b8-114">Request URI</span></span>                                                        |
|---------|--------------------------------------------------------------------|
| <span data-ttu-id="415b8-115">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="415b8-115">**GET**</span></span> | <span data-ttu-id="415b8-116">[*{baseURL}*](partner-center-rest-urls.md)/v1/partnerRequests</span><span class="sxs-lookup"><span data-stu-id="415b8-116">[*{baseURL}*](partner-center-rest-urls.md)/v1/partnerRequests</span></span> |

### <a name="request-headers"></a><span data-ttu-id="415b8-117">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="415b8-117">Request headers</span></span>

- <span data-ttu-id="415b8-118">Zie de [rest headers van het Partner Center](headers.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="415b8-118">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="415b8-119">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="415b8-119">Request body</span></span>

<span data-ttu-id="415b8-120">Geen.</span><span class="sxs-lookup"><span data-stu-id="415b8-120">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="415b8-121">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="415b8-121">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/partnerRequests HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Type: application/json
```

## <a name="rest-response"></a><span data-ttu-id="415b8-122">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="415b8-122">REST response</span></span>

<span data-ttu-id="415b8-123">Als dit lukt, retourneert deze methode een verzameling van de gegevens bronnen van de [API-aanvraag](mfa-resources.md#api-request-details) in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="415b8-123">If successful, this method returns a collection of [API request details](mfa-resources.md#api-request-details) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="415b8-124">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="415b8-124">Response success and error codes</span></span>

<span data-ttu-id="415b8-125">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="415b8-125">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="415b8-126">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="415b8-126">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="415b8-127">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="415b8-127">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="415b8-128">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="415b8-128">Response example</span></span>

``` http
HTTP/1.1 200 OK
Content-Length: 2960
Content-Type: application/json
MS-CorrelationId: 4cb80cbe-566b-4d8b-8b8f-af1454b73089
MS-RequestId: 566330a7-1e4b-4848-9c23-f135c70fd810
Date: Thu, 21 May 2020 22:29:17 GMT
{
    "totalCount": 2,
    "items": [
        {
            "requestId": "6c583d8d-46cd-420c-ae3d-35b6dfdcdb21",
            "correlationId": "",
            "operationName": "Get /v{version}/nonMfaCompliantPartnerPrincipals",
            "requestDateTime": "2020-05-21T21:02:10.31",
            "sourceIpAddress": "13.88.20.150",
            "objectId": "c69854fe-5fb4-4527-a28f-f24f1acaffd6",
            "tenantId": "6e6aef4a-4ca9-40a8-b5bf-b53a1923c540",
            "upn": "admin@yourdomain.onmicrosoft.com",
            "applicationId": "60a00bf2-0644-4279-83b3-87ddf96f2509",
            "mfaCompliant": true
        },
        {
            "requestId": "09f8e434-a9ce-43ea-a9ac-270fbb22371a",
            "correlationId": "",
            "operationName": "Get /v{version}/customers/{customer_id}/subscriptions?order_id={order_id_value}&mpn_id={mpn_id_value}",
            "requestDateTime": "2020-05-21T22:18:35.73",
            "sourceIpAddress": "13.88.20.150",
            "objectId": "adc77aa5-7968-4c57-9f48-361018265c1a",
            "tenantId": "6e6aef4a-4ca9-40a8-b5bf-b53a1923c540",
            "upn": "portalnonmfa@yourdomain.onmicrosoft.com",
            "applicationId": "60a00bf2-0644-4279-83b3-87ddf96f2509",
            "mfaCompliant": false
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
