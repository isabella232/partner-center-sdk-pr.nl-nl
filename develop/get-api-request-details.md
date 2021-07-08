---
title: Een lijst met alle aanvragen van partnergebruikers opvragen
description: Een lijst met alle aanvragen van partnergebruikers opvragen met behulp van de partner REST API.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
author: cychua
ms.author: cychua
ms.openlocfilehash: 9a367f912669114969f8792a5afcc7020af1112e
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760501"
---
# <a name="get-app-and-user-api-requests"></a><span data-ttu-id="14d1b-103">App- en gebruikers-API-aanvragen downloaden</span><span class="sxs-lookup"><span data-stu-id="14d1b-103">Get App and User API requests</span></span>

<span data-ttu-id="14d1b-104">**Van toepassing op**: Partner Center API</span><span class="sxs-lookup"><span data-stu-id="14d1b-104">**Applies to**: Partner Center API</span></span>

<span data-ttu-id="14d1b-105">In dit artikel wordt uitgelegd hoe u een lijst met alle aanvragen van partnergebruikers binnen een tenant kunt verkrijgen met behulp van REST API's.</span><span class="sxs-lookup"><span data-stu-id="14d1b-105">This article explains how to obtain a list of all partner user requests within a tenant using REST APIs.</span></span>

 > [!NOTE]
 > <span data-ttu-id="14d1b-106">Deze API retourneert alleen de meest recente API-aanvragen die zijn gedaan door APP + Gebruikersreferenties met een limiet van maximaal 10.000.</span><span class="sxs-lookup"><span data-stu-id="14d1b-106">This API only returns the most recent API requests made by APP + User credential with maximum 10K limit.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="14d1b-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="14d1b-107">Prerequisites</span></span>

- <span data-ttu-id="14d1b-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="14d1b-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="14d1b-109">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="14d1b-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="14d1b-110">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="14d1b-110">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="14d1b-111">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="14d1b-111">Request syntax</span></span>

| <span data-ttu-id="14d1b-112">Methode</span><span class="sxs-lookup"><span data-stu-id="14d1b-112">Method</span></span>  | <span data-ttu-id="14d1b-113">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="14d1b-113">Request URI</span></span>                                                        |
|---------|--------------------------------------------------------------------|
| <span data-ttu-id="14d1b-114">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="14d1b-114">**GET**</span></span> | <span data-ttu-id="14d1b-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/partnerRequests</span><span class="sxs-lookup"><span data-stu-id="14d1b-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/partnerRequests</span></span> |

### <a name="request-headers"></a><span data-ttu-id="14d1b-116">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="14d1b-116">Request headers</span></span>

- <span data-ttu-id="14d1b-117">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="14d1b-117">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="14d1b-118">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="14d1b-118">Request body</span></span>

<span data-ttu-id="14d1b-119">Geen.</span><span class="sxs-lookup"><span data-stu-id="14d1b-119">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="14d1b-120">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="14d1b-120">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/partnerRequests HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Type: application/json
```

## <a name="rest-response"></a><span data-ttu-id="14d1b-121">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="14d1b-121">REST response</span></span>

<span data-ttu-id="14d1b-122">Als dit lukt, retourneert deze methode een verzameling resources met details van [de API-aanvraag](mfa-resources.md#api-request-details) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="14d1b-122">If successful, this method returns a collection of [API request details](mfa-resources.md#api-request-details) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="14d1b-123">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="14d1b-123">Response success and error codes</span></span>

<span data-ttu-id="14d1b-124">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="14d1b-124">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="14d1b-125">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="14d1b-125">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="14d1b-126">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="14d1b-126">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="14d1b-127">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="14d1b-127">Response example</span></span>

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
