---
title: Een URL voor relatie aanvragen ophalen
description: Een URL voor relatie aanvragen ophalen om naar een klant te verzenden.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 5f899734b774ff460e005e20df8658275b2ce9d5
ms.sourcegitcommit: d4e652e3b73c6137704d43d4a472cc5aa5549f11
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/09/2020
ms.locfileid: "97768681"
---
# <a name="retrieve-a-relationship-request-url"></a><span data-ttu-id="d3f85-103">Een URL voor relatie aanvragen ophalen</span><span class="sxs-lookup"><span data-stu-id="d3f85-103">Retrieve a relationship request URL</span></span>

<span data-ttu-id="d3f85-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="d3f85-104">**Applies To**</span></span>

- <span data-ttu-id="d3f85-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d3f85-105">Partner Center</span></span>
- <span data-ttu-id="d3f85-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="d3f85-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="d3f85-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="d3f85-107">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="d3f85-108">Een URL voor relatie aanvragen ophalen om naar een klant te verzenden.</span><span class="sxs-lookup"><span data-stu-id="d3f85-108">How to retrieve a relationship request URL to send to a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d3f85-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d3f85-109">Prerequisites</span></span>

- <span data-ttu-id="d3f85-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d3f85-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d3f85-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d3f85-111">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="d3f85-112">C\#</span><span class="sxs-lookup"><span data-stu-id="d3f85-112">C\#</span></span>

<span data-ttu-id="d3f85-113">Als u een URL voor de relatie aanvraag wilt ophalen, moet u eerst [**IAggregatePartner. klanten**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) gebruiken om een interface te verkrijgen voor de klant bewerkingen van de partner.</span><span class="sxs-lookup"><span data-stu-id="d3f85-113">To retrieve a relationship request URL, first use [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) to get an interface to the partner's customer operations.</span></span> <span data-ttu-id="d3f85-114">Gebruik vervolgens de eigenschap [**RelationshipRequest**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.relationshiprequest) om een interface op te halen voor de bewerkingen van klant relatie aanvragen.</span><span class="sxs-lookup"><span data-stu-id="d3f85-114">Next, use the [**RelationshipRequest**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.relationshiprequest) property to get an interface to customer relationship request operations.</span></span> <span data-ttu-id="d3f85-115">Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.getasync) aan om de URL op te halen.</span><span class="sxs-lookup"><span data-stu-id="d3f85-115">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.getasync) method to retrieve the URL.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var customerRelationshipRequest = partnerOperations.Customers.RelationshipRequest.Get();
```

<span data-ttu-id="d3f85-116">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d3f85-116">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d3f85-117">**Project**: Partner Center SDK-voor beelden **klasse**: GetCustomerRelationshipRequest.cs</span><span class="sxs-lookup"><span data-stu-id="d3f85-117">**Project**: Partner Center SDK Samples **Class**: GetCustomerRelationshipRequest.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="d3f85-118">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d3f85-118">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d3f85-119">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d3f85-119">Request syntax</span></span>

| <span data-ttu-id="d3f85-120">Methode</span><span class="sxs-lookup"><span data-stu-id="d3f85-120">Method</span></span>  | <span data-ttu-id="d3f85-121">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d3f85-121">Request URI</span></span>                                                                            |
|---------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="d3f85-122">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="d3f85-122">**GET**</span></span> | <span data-ttu-id="d3f85-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/relationshiprequests http/1.1</span><span class="sxs-lookup"><span data-stu-id="d3f85-123">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/relationshiprequests HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d3f85-124">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d3f85-124">Request headers</span></span>

<span data-ttu-id="d3f85-125">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d3f85-125">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d3f85-126">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="d3f85-126">Request body</span></span>

<span data-ttu-id="d3f85-127">Geen</span><span class="sxs-lookup"><span data-stu-id="d3f85-127">None</span></span>

### <a name="request-example"></a><span data-ttu-id="d3f85-128">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d3f85-128">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/relationshiprequests HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ee519026-4c67-4113-bec7-a38aca621bf0
MS-CorrelationId: 02971f0f-1029-47b2-9fdb-1932f0987470
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="d3f85-129">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d3f85-129">REST response</span></span>

<span data-ttu-id="d3f85-130">Als dit is gelukt, bevat het antwoord het [RelationshipRequest](relationships-resources.md#relationshiprequest) -object.</span><span class="sxs-lookup"><span data-stu-id="d3f85-130">If successful, the response contains the [RelationshipRequest](relationships-resources.md#relationshiprequest) object.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d3f85-131">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="d3f85-131">Response success and error codes</span></span>

<span data-ttu-id="d3f85-132">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="d3f85-132">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d3f85-133">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d3f85-133">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d3f85-134">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="d3f85-134">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d3f85-135">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d3f85-135">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 196
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 02971f0f-1029-47b2-9fdb-1932f0987470
MS-RequestId: ee519026-4c67-4113-bec7-a38aca621bf0
MS-CV: jbYZRWjU3E262f8o.0
MS-ServerId: 030020643
Date: Fri, 19 May 2017 22:32:07 GMT

{
    "url": "https://admin.microsoft.com/Adminportal/Home?invType=ResellerRelationship&partnerId=3b33e682-00c3-41ee-9dd2-a548adf56438&msppId=0&DAP=false#/BillingAccounts/partner-invitation",
    "attributes": {
        "objectType": "RelationshipRequest"
    }
}
```
