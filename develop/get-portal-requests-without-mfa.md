---
title: Portal-aanvragen zonder MFA ophalen
description: Een lijst met gebruikers aanvragen zonder multi-factor Authentication (MFA) ophalen met behulp van de partner REST API.
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.date: 05/29/2020
ms.openlocfilehash: fd350aa3301f00926942ae6c6af359b0d0edc423
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767286"
---
# <a name="get-portal-requests-without-mfa"></a><span data-ttu-id="fd1b2-103">Portal-aanvragen zonder MFA ophalen</span><span class="sxs-lookup"><span data-stu-id="fd1b2-103">Get portal requests without MFA</span></span>

<span data-ttu-id="fd1b2-104">Van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="fd1b2-104">Applies to:</span></span>

- <span data-ttu-id="fd1b2-105">Partnercentrum-API</span><span class="sxs-lookup"><span data-stu-id="fd1b2-105">Partner Center API</span></span>

<span data-ttu-id="fd1b2-106">In dit artikel wordt uitgelegd hoe u een lijst kunt verkrijgen met de meest recente aanvragen van gebruikers die toegang hebben tot de Partner Center-Portal zonder multi-factor Authentication (MFA) in te voeren.</span><span class="sxs-lookup"><span data-stu-id="fd1b2-106">This article explains how to obtain a list of the most recent requests from users who access Partner Center portal without completing multi-factor authentication (MFA).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fd1b2-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fd1b2-107">Prerequisites</span></span>

- <span data-ttu-id="fd1b2-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fd1b2-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fd1b2-109">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="fd1b2-109">This scenario supports authentication with App+User credentials.</span></span>

## <a name="rest-request"></a><span data-ttu-id="fd1b2-110">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fd1b2-110">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fd1b2-111">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fd1b2-111">Request syntax</span></span>

| <span data-ttu-id="fd1b2-112">Methode</span><span class="sxs-lookup"><span data-stu-id="fd1b2-112">Method</span></span>  | <span data-ttu-id="fd1b2-113">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fd1b2-113">Request URI</span></span>                                                  |
|---------|--------------------------------------------------------------|
| <span data-ttu-id="fd1b2-114">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fd1b2-114">**GET**</span></span> | <span data-ttu-id="fd1b2-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/nonMfaCompliantPartnerPrincipals</span><span class="sxs-lookup"><span data-stu-id="fd1b2-115">[*{baseURL}*](partner-center-rest-urls.md)/v1/nonMfaCompliantPartnerPrincipals</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fd1b2-116">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fd1b2-116">Request headers</span></span>

- <span data-ttu-id="fd1b2-117">Zie de [rest headers van het Partner Center](headers.md) voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="fd1b2-117">See [Partner Center REST headers](headers.md) for more information.</span></span>

### <a name="request-body"></a><span data-ttu-id="fd1b2-118">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fd1b2-118">Request body</span></span>

<span data-ttu-id="fd1b2-119">Geen.</span><span class="sxs-lookup"><span data-stu-id="fd1b2-119">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="fd1b2-120">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fd1b2-120">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/nonMfaCompliantPartnerPrincipals HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Accept: application/json
MS-RequestId: 8f489776-a3f3-47cb-91c3-538e1f70f560
MS-CorrelationId: e72e1dc3-4abd-4ce0-908b-d23fdaedcb28
Connection: keep-alive

```

## <a name="rest-response"></a><span data-ttu-id="fd1b2-121">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fd1b2-121">REST response</span></span>

<span data-ttu-id="fd1b2-122">Als dit lukt, retourneert deze methode een verzameling van [Portal aanvraag](mfa-resources.md#portal-request-without-mfa) bronnen in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="fd1b2-122">If successful, this method returns a collection of [Portal request](mfa-resources.md#portal-request-without-mfa) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fd1b2-123">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="fd1b2-123">Response success and error codes</span></span>

<span data-ttu-id="fd1b2-124">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="fd1b2-124">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fd1b2-125">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fd1b2-125">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fd1b2-126">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="fd1b2-126">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fd1b2-127">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fd1b2-127">Response example</span></span>

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
