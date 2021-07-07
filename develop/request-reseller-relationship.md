---
title: Een URL voor relatie aanvragen ophalen
description: De URL van een relatieaanvraag ophalen om naar een klant te verzenden.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 07804b36dfe0892cf8b531e0731188260c014f49
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547444"
---
# <a name="retrieve-a-relationship-request-url"></a><span data-ttu-id="2c13e-103">Een URL voor relatie aanvragen ophalen</span><span class="sxs-lookup"><span data-stu-id="2c13e-103">Retrieve a relationship request URL</span></span>

<span data-ttu-id="2c13e-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="2c13e-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="2c13e-105">De URL van een relatieaanvraag ophalen om naar een klant te verzenden.</span><span class="sxs-lookup"><span data-stu-id="2c13e-105">How to retrieve a relationship request URL to send to a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2c13e-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2c13e-106">Prerequisites</span></span>

- <span data-ttu-id="2c13e-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2c13e-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2c13e-108">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="2c13e-108">This scenario supports authentication with App+User credentials only.</span></span>

## <a name="c"></a><span data-ttu-id="2c13e-109">C\#</span><span class="sxs-lookup"><span data-stu-id="2c13e-109">C\#</span></span>

<span data-ttu-id="2c13e-110">Als u een URL voor een relatieaanvraag wilt ophalen, gebruikt u [**eerst IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) om een interface te krijgen met de klantactiviteiten van de partner.</span><span class="sxs-lookup"><span data-stu-id="2c13e-110">To retrieve a relationship request URL, first use [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) to get an interface to the partner's customer operations.</span></span> <span data-ttu-id="2c13e-111">Gebruik vervolgens de eigenschap [**RelationshipRequest om**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.relationshiprequest) een interface op te halen voor aanvraagbewerkingen voor klantrelaties.</span><span class="sxs-lookup"><span data-stu-id="2c13e-111">Next, use the [**RelationshipRequest**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.relationshiprequest) property to get an interface to customer relationship request operations.</span></span> <span data-ttu-id="2c13e-112">Roep ten slotte de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.getasync) om de URL op te halen.</span><span class="sxs-lookup"><span data-stu-id="2c13e-112">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.relationshiprequests.icustomerrelationshiprequest.getasync) method to retrieve the URL.</span></span>

``` csharp
// IAggregatePartner partnerOperations;

var customerRelationshipRequest = partnerOperations.Customers.RelationshipRequest.Get();
```

<span data-ttu-id="2c13e-113">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="2c13e-113">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="2c13e-114">**Project:** Partnercentrum-SDK Samples **Class**: GetCustomerRelationshipRequest.cs</span><span class="sxs-lookup"><span data-stu-id="2c13e-114">**Project**: Partner Center SDK Samples **Class**: GetCustomerRelationshipRequest.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="2c13e-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="2c13e-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2c13e-116">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="2c13e-116">Request syntax</span></span>

| <span data-ttu-id="2c13e-117">Methode</span><span class="sxs-lookup"><span data-stu-id="2c13e-117">Method</span></span>  | <span data-ttu-id="2c13e-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="2c13e-118">Request URI</span></span>                                                                            |
|---------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="2c13e-119">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="2c13e-119">**GET**</span></span> | <span data-ttu-id="2c13e-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/relationshiprequests HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="2c13e-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/relationshiprequests HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2c13e-121">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="2c13e-121">Request headers</span></span>

<span data-ttu-id="2c13e-122">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="2c13e-122">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2c13e-123">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="2c13e-123">Request body</span></span>

<span data-ttu-id="2c13e-124">Geen</span><span class="sxs-lookup"><span data-stu-id="2c13e-124">None</span></span>

### <a name="request-example"></a><span data-ttu-id="2c13e-125">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2c13e-125">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="2c13e-126">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="2c13e-126">REST response</span></span>

<span data-ttu-id="2c13e-127">Als dit lukt, bevat het antwoord het [object RelationshipRequest.](relationships-resources.md#relationshiprequest)</span><span class="sxs-lookup"><span data-stu-id="2c13e-127">If successful, the response contains the [RelationshipRequest](relationships-resources.md#relationshiprequest) object.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2c13e-128">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="2c13e-128">Response success and error codes</span></span>

<span data-ttu-id="2c13e-129">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="2c13e-129">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2c13e-130">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="2c13e-130">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2c13e-131">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="2c13e-131">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2c13e-132">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="2c13e-132">Response example</span></span>

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
