---
title: Haal de details van de serviceaanvraag op op id.
description: De details van een bestaande klantenserviceaanvraag ophalen op id.
ms.date: 02/06/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 66488cf9592d630cb1f0237d379e8df5ead6a3a8
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548767"
---
# <a name="get-service-request-details-by-id"></a><span data-ttu-id="170c6-103">Details van serviceaanvraag ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="170c6-103">Get service request details by ID</span></span>

<span data-ttu-id="170c6-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="170c6-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="170c6-105">De details van een bestaande klantenserviceaanvraag ophalen met behulp van de serviceaanvraag-id.</span><span class="sxs-lookup"><span data-stu-id="170c6-105">How to retrieve the details of an existing customer service request using the service request identifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="170c6-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="170c6-106">Prerequisites</span></span>

- <span data-ttu-id="170c6-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="170c6-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="170c6-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="170c6-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="170c6-109">Een serviceaanvraag-id.</span><span class="sxs-lookup"><span data-stu-id="170c6-109">A service request ID.</span></span>

## <a name="c"></a><span data-ttu-id="170c6-110">C\#</span><span class="sxs-lookup"><span data-stu-id="170c6-110">C\#</span></span>

<span data-ttu-id="170c6-111">Als u de details van een bestaande klantenserviceaanvraag wilt ophalen, roept u de methode [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) aan en geeft u een [**ServiceRequest.Id**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest.id#Microsoft_Store_PartnerCenter_Models_ServiceRequests_ServiceRequest_Id) door om een interface te identificeren en te retourneren naar het specifieke [**ServiceRequest-object.**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest)</span><span class="sxs-lookup"><span data-stu-id="170c6-111">To retrieve the details of an existing customer service request, call the [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) method, and pass in a [**ServiceRequest.Id**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest.id#Microsoft_Store_PartnerCenter_Models_ServiceRequests_ServiceRequest_Id) to identify and return an interface to the specific [**ServiceRequest**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) object.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// ServiceRequest existingServiceRequest as ServiceRequest;

ServiceRequest serviceRequestDetails = partnerOperations.ServiceRequests.ById(existingServiceRequest.Id).Get();

Console.WriteLine(string.Format("The primary contact for the service request {0} is {1} {2}.",
    serviceRequestDetails.Title,
    serviceRequestDetails.PrimaryContact.FirstName,
    serviceRequestDetails.PrimaryContact.LastName,
));
```

## <a name="rest-request"></a><span data-ttu-id="170c6-112">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="170c6-112">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="170c6-113">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="170c6-113">Request syntax</span></span>

| <span data-ttu-id="170c6-114">Methode</span><span class="sxs-lookup"><span data-stu-id="170c6-114">Method</span></span>    | <span data-ttu-id="170c6-115">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="170c6-115">Request URI</span></span>                                                                                 |
|-----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="170c6-116">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="170c6-116">**GET**</span></span> | <span data-ttu-id="170c6-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="170c6-117">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="170c6-118">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="170c6-118">URI parameter</span></span>

<span data-ttu-id="170c6-119">Gebruik de volgende URI-parameter om de opgegeven serviceaanvraag op te halen.</span><span class="sxs-lookup"><span data-stu-id="170c6-119">Use the following URI parameter to get the specified service request.</span></span>

| <span data-ttu-id="170c6-120">Naam</span><span class="sxs-lookup"><span data-stu-id="170c6-120">Name</span></span>                  | <span data-ttu-id="170c6-121">Type</span><span class="sxs-lookup"><span data-stu-id="170c6-121">Type</span></span>     | <span data-ttu-id="170c6-122">Vereist</span><span class="sxs-lookup"><span data-stu-id="170c6-122">Required</span></span> | <span data-ttu-id="170c6-123">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="170c6-123">Description</span></span>                                 |
|-----------------------|----------|----------|---------------------------------------------|
| <span data-ttu-id="170c6-124">**servicerequest-id**</span><span class="sxs-lookup"><span data-stu-id="170c6-124">**servicerequest-id**</span></span> | <span data-ttu-id="170c6-125">**guid**</span><span class="sxs-lookup"><span data-stu-id="170c6-125">**guid**</span></span> | <span data-ttu-id="170c6-126">J</span><span class="sxs-lookup"><span data-stu-id="170c6-126">Y</span></span>        | <span data-ttu-id="170c6-127">Een GUID die de serviceaanvraag identificeert.</span><span class="sxs-lookup"><span data-stu-id="170c6-127">A GUID that identifies the service request.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="170c6-128">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="170c6-128">Request headers</span></span>

<span data-ttu-id="170c6-129">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="170c6-129">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="170c6-130">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="170c6-130">Request body</span></span>

<span data-ttu-id="170c6-131">Geen.</span><span class="sxs-lookup"><span data-stu-id="170c6-131">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="170c6-132">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="170c6-132">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/servicerequests/616122292874576 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f9a030bd-e492-4c1a-9c70-021f18234981
MS-CorrelationId: fd969070-4e5f-4c6b-a3c6-1941283b39ae
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="170c6-133">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="170c6-133">REST response</span></span>

<span data-ttu-id="170c6-134">Als dit lukt, retourneert deze methode een **serviceaanvraagresource** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="170c6-134">If successful, this method returns a **Service Request** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="170c6-135">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="170c6-135">Response success and error codes</span></span>

<span data-ttu-id="170c6-136">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="170c6-136">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="170c6-137">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="170c6-137">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="170c6-138">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="170c6-138">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="170c6-139">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="170c6-139">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 566
Content-Type: application/json; charset=utf-8
MS-CorrelationId: fd969070-4e5f-4c6b-a3c6-1941283b39ae
MS-RequestId: f9a030bd-e492-4c1a-9c70-021f18234981
MS-CV: rjLONPum/Uq94UQA.0
MS-ServerId: 030011719
Date: Mon, 09 Jan 2017 23:31:15 GMT

{
    "title": "TrialSR",
    "description": "Ignore this SR",
    "severity": "critical",
    "supportTopicId": "32444671",
    "supportTopicName": "Cannot manage my profile",
    "id": "616122292874576",
    "status": "open",
    "organization": {
        "id": "3b33e682-00c3-41ee-9dd2-a548adf56438",
        "name": "TEST_TEST_BugBash1"
    },
    "productId": "15960",
    "createdDate": "2016-12-22T20:31:17.24Z",
    "lastModifiedDate": "2017-01-09T23:31:15.373Z",
    "lastClosedDate": "0001-01-01T00:00:00",
    "notes": [{
            "createdByName": "Account",
            "createdDate": "2017-01-09T23:31:15.373",
            "text": "Sample Note"
        }
    ],
    "attributes": {
        "objectType": "ServiceRequest"
    }
}
```
