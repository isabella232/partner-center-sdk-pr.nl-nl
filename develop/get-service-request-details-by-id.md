---
title: Details van service aanvraag ophalen op ID.
description: De details van een bestaande klantenservice aanvraag ophalen op basis van de ID.
ms.date: 02/06/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c79fd3f5e5609a1893891e9b2a8078f8678497b3
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767561"
---
# <a name="get-service-request-details-by-id"></a><span data-ttu-id="e356b-103">Details van serviceaanvraag ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="e356b-103">Get service request details by ID</span></span>

<span data-ttu-id="e356b-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="e356b-104">**Applies To**</span></span>

- <span data-ttu-id="e356b-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e356b-105">Partner Center</span></span>
- <span data-ttu-id="e356b-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="e356b-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="e356b-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e356b-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="e356b-108">De details van een bestaande aanvraag van een klanten service ophalen met de service aanvraag-id.</span><span class="sxs-lookup"><span data-stu-id="e356b-108">How to retrieve the details of an existing customer service request using the service request identifier.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e356b-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e356b-109">Prerequisites</span></span>

- <span data-ttu-id="e356b-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e356b-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e356b-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e356b-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e356b-112">Een service aanvraag-ID.</span><span class="sxs-lookup"><span data-stu-id="e356b-112">A service request ID.</span></span>

## <a name="c"></a><span data-ttu-id="e356b-113">C\#</span><span class="sxs-lookup"><span data-stu-id="e356b-113">C\#</span></span>

<span data-ttu-id="e356b-114">Als u de details van een bestaande aanvraag van een klanten service wilt ophalen, roept u de methode [**IServiceRequestCollection. ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) aan en geeft u een [**ServiceRequest.id**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest.id#Microsoft_Store_PartnerCenter_Models_ServiceRequests_ServiceRequest_Id) door om een interface te identificeren en te retour neren aan het specifieke [**ServiceRequest**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) -object.</span><span class="sxs-lookup"><span data-stu-id="e356b-114">To retrieve the details of an existing customer service request, call the [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) method, and pass in a [**ServiceRequest.Id**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest.id#Microsoft_Store_PartnerCenter_Models_ServiceRequests_ServiceRequest_Id) to identify and return an interface to the specific [**ServiceRequest**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) object.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="e356b-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e356b-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e356b-116">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e356b-116">Request syntax</span></span>

| <span data-ttu-id="e356b-117">Methode</span><span class="sxs-lookup"><span data-stu-id="e356b-117">Method</span></span>    | <span data-ttu-id="e356b-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e356b-118">Request URI</span></span>                                                                                 |
|-----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="e356b-119">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e356b-119">**GET**</span></span> | <span data-ttu-id="e356b-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="e356b-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span></span>  |

### <a name="uri-parameter"></a><span data-ttu-id="e356b-121">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="e356b-121">URI parameter</span></span>

<span data-ttu-id="e356b-122">Gebruik de volgende URI-para meter om de opgegeven service aanvraag op te halen.</span><span class="sxs-lookup"><span data-stu-id="e356b-122">Use the following URI parameter to get the specified service request.</span></span>

| <span data-ttu-id="e356b-123">Naam</span><span class="sxs-lookup"><span data-stu-id="e356b-123">Name</span></span>                  | <span data-ttu-id="e356b-124">Type</span><span class="sxs-lookup"><span data-stu-id="e356b-124">Type</span></span>     | <span data-ttu-id="e356b-125">Vereist</span><span class="sxs-lookup"><span data-stu-id="e356b-125">Required</span></span> | <span data-ttu-id="e356b-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e356b-126">Description</span></span>                                 |
|-----------------------|----------|----------|---------------------------------------------|
| <span data-ttu-id="e356b-127">**servicerequest-id**</span><span class="sxs-lookup"><span data-stu-id="e356b-127">**servicerequest-id**</span></span> | <span data-ttu-id="e356b-128">**guid**</span><span class="sxs-lookup"><span data-stu-id="e356b-128">**guid**</span></span> | <span data-ttu-id="e356b-129">J</span><span class="sxs-lookup"><span data-stu-id="e356b-129">Y</span></span>        | <span data-ttu-id="e356b-130">Een GUID waarmee de service aanvraag wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="e356b-130">A GUID that identifies the service request.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e356b-131">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e356b-131">Request headers</span></span>

<span data-ttu-id="e356b-132">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e356b-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e356b-133">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e356b-133">Request body</span></span>

<span data-ttu-id="e356b-134">Geen.</span><span class="sxs-lookup"><span data-stu-id="e356b-134">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="e356b-135">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e356b-135">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e356b-136">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e356b-136">REST response</span></span>

<span data-ttu-id="e356b-137">Als dit lukt, retourneert deze methode een resource van een **service aanvraag** in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="e356b-137">If successful, this method returns a **Service Request** resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e356b-138">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="e356b-138">Response success and error codes</span></span>

<span data-ttu-id="e356b-139">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e356b-139">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e356b-140">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e356b-140">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e356b-141">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="e356b-141">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e356b-142">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e356b-142">Response example</span></span>

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
