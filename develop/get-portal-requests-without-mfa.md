---
title: Portal-aanvragen zonder MFA ophalen
description: Haal een lijst met gebruikersaanvragen op zonder meervoudige verificatie (MFA) met behulp van de partner REST API.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
ms.openlocfilehash: 41627751d3402d7712d96c15c4281a25ed9a44a7
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445575"
---
# <a name="get-portal-requests-without-mfa"></a><span data-ttu-id="48149-103">Portal-aanvragen zonder MFA ophalen</span><span class="sxs-lookup"><span data-stu-id="48149-103">Get portal requests without MFA</span></span>

<span data-ttu-id="48149-104">In dit artikel wordt uitgelegd hoe u een lijst met de meest recente aanvragen kunt verkrijgen van gebruikers die toegang hebben tot Partner Center portal zonder meervoudige verificatie (MFA) te voltooien.</span><span class="sxs-lookup"><span data-stu-id="48149-104">This article explains how to obtain a list of the most recent requests from users who access Partner Center portal without completing multi-factor authentication (MFA).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="48149-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="48149-105">Prerequisites</span></span>

- <span data-ttu-id="48149-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="48149-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="48149-107">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="48149-107">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="48149-108">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="48149-108">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="48149-109">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="48149-109">Request syntax</span></span>

| <span data-ttu-id="48149-110">Methode</span><span class="sxs-lookup"><span data-stu-id="48149-110">Method</span></span>  | <span data-ttu-id="48149-111">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="48149-111">Request URI</span></span>                                                  |
|---------|--------------------------------------------------------------|
| <span data-ttu-id="48149-112">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="48149-112">**GET**</span></span> | <span data-ttu-id="48149-113">[*{baseURL}*](partner-center-rest-urls.md)/v1/nonMfaCompliantPartnerPrincipals</span><span class="sxs-lookup"><span data-stu-id="48149-113">[*{baseURL}*](partner-center-rest-urls.md)/v1/nonMfaCompliantPartnerPrincipals</span></span> |

### <a name="request-headers"></a><span data-ttu-id="48149-114">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="48149-114">Request headers</span></span>

- <span data-ttu-id="48149-115">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="48149-115">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="48149-116">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="48149-116">Request body</span></span>

<span data-ttu-id="48149-117">Geen.</span><span class="sxs-lookup"><span data-stu-id="48149-117">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="48149-118">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="48149-118">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/nonMfaCompliantPartnerPrincipals HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Accept: application/json
MS-RequestId: 8f489776-a3f3-47cb-91c3-538e1f70f560
MS-CorrelationId: e72e1dc3-4abd-4ce0-908b-d23fdaedcb28
Connection: keep-alive

```

## <a name="rest-response"></a><span data-ttu-id="48149-119">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="48149-119">REST response</span></span>

<span data-ttu-id="48149-120">Als dit lukt, retourneert deze methode een verzameling [portalaanvraagresources](mfa-resources.md#portal-request-without-mfa) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="48149-120">If successful, this method returns a collection of [Portal request](mfa-resources.md#portal-request-without-mfa) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="48149-121">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="48149-121">Response success and error codes</span></span>

<span data-ttu-id="48149-122">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="48149-122">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="48149-123">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="48149-123">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="48149-124">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="48149-124">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="48149-125">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="48149-125">Response example</span></span>

``` http
HTTP/1.1 200 OK
Content-Length: 296
Content-Type: application/json
MS-CorrelationId: 4cb80cbe-566b-4d8b-8b8f-af1454b73089
MS-RequestId: 566330a7-1e4b-4848-9c23-f135c70fd810
Date: Thu, 23 Apr 2020 22:10:30 GMT
{
    "totalCount": 1,
    "items": [
        {
            "objectId": "adc77aa5-7968-4c57-9f48-361018265c1a",
            "tenantId": "6e6aef4a-4ca9-40a8-b5bf-b53a1923c540",
            "upn": "portalnonmfa@yourdomain.onmicrosoft.com",
            "lastNonMfaCompliantRequestDateTime": "2020-04-21T22:09:53.051"
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
