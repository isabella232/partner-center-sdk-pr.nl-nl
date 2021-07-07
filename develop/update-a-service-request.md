---
title: Een serviceaanvraag bijwerken
description: Een bestaande klantenserviceaanvraag bijwerken die een Cloud Solution Provider namens de klant heeft ingediend bij Microsoft.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: efa7b2a98b6f95a763ca6e3811c43cc655c18e2b
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530086"
---
# <a name="update-a-service-request"></a><span data-ttu-id="eb81b-103">Een serviceaanvraag bijwerken</span><span class="sxs-lookup"><span data-stu-id="eb81b-103">Update a service request</span></span>

<span data-ttu-id="eb81b-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="eb81b-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="eb81b-105">Een bestaande klantenserviceaanvraag bijwerken die een Cloud Solution Provider namens de klant heeft ingediend bij Microsoft.</span><span class="sxs-lookup"><span data-stu-id="eb81b-105">How to update an existing customer service request that a Cloud Solution Provider has filed with Microsoft on the customer's behalf.</span></span>

<span data-ttu-id="eb81b-106">In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst [een klant te selecteren.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="eb81b-106">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="eb81b-107">Selecteer vervolgens **Servicebeheer op** de linkerzijbalk.</span><span class="sxs-lookup"><span data-stu-id="eb81b-107">Then, select **Service management** on the left sidebar.</span></span> <span data-ttu-id="eb81b-108">Selecteer onder de header **Ondersteuningsaanvragen** de serviceaanvraag in kwestie.</span><span class="sxs-lookup"><span data-stu-id="eb81b-108">Under the **Support requests** header, select the service request in question.</span></span> <span data-ttu-id="eb81b-109">Als u wilt voltooien, moet u de gewenste wijzigingen aanbrengen in de serviceaanvraag en vervolgens **Verzenden selecteren.**</span><span class="sxs-lookup"><span data-stu-id="eb81b-109">To finish, make the desired changes to the service request then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eb81b-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="eb81b-110">Prerequisites</span></span>

- <span data-ttu-id="eb81b-111">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="eb81b-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="eb81b-112">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="eb81b-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="eb81b-113">Een serviceaanvraag-id.</span><span class="sxs-lookup"><span data-stu-id="eb81b-113">A service request ID.</span></span>

## <a name="c"></a><span data-ttu-id="eb81b-114">C\#</span><span class="sxs-lookup"><span data-stu-id="eb81b-114">C\#</span></span>

<span data-ttu-id="eb81b-115">Als u de serviceaanvraag van een klant wilt bijwerken, roept u de methode [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) aan met de serviceaanvraag-id om de interface voor serviceaanvraag te identificeren en te retourneren.</span><span class="sxs-lookup"><span data-stu-id="eb81b-115">To update a customer's service request, call the [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) method with the service request ID to identify and return the service request interface.</span></span> <span data-ttu-id="eb81b-116">Roep vervolgens de [**methode IServiceRequest.Patch**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patch) of [**PatchAsync aan**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patchasync) om de serviceaanvraag bij te werken.</span><span class="sxs-lookup"><span data-stu-id="eb81b-116">Then call the [**IServiceRequest.Patch**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patch) or [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patchasync) method to update the service request.</span></span> <span data-ttu-id="eb81b-117">Als u de bijgewerkte waarden wilt verstrekken, maakt u een nieuw, leeg [**ServiceRequest-object**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) en stelt u alleen de eigenschapswaarden in die u wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="eb81b-117">To provide the updated values, create a new, empty [**ServiceRequest**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) object and set only the property values that you want to change.</span></span> <span data-ttu-id="eb81b-118">Geef dat object vervolgens door in de aanroep van de methode Patch of PatchAsync.</span><span class="sxs-lookup"><span data-stu-id="eb81b-118">Then pass that object in the call to the Patch or PatchAsync method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// ServiceRequest existingServiceRequest;

ServiceRequest updatedServiceRequest = partnerOperations.ServiceRequests.ById(existingServiceRequest.Id).Patch(new ServiceRequest
{
   NewNote = note
});
```

<span data-ttu-id="eb81b-119">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="eb81b-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="eb81b-120">**Project**: Partnercentrum-SDK Samples **Class**: UpdatePartnerServiceRequest.cs</span><span class="sxs-lookup"><span data-stu-id="eb81b-120">**Project**: Partner Center SDK Samples **Class**: UpdatePartnerServiceRequest.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="eb81b-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="eb81b-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="eb81b-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="eb81b-122">Request syntax</span></span>

| <span data-ttu-id="eb81b-123">Methode</span><span class="sxs-lookup"><span data-stu-id="eb81b-123">Method</span></span>    | <span data-ttu-id="eb81b-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="eb81b-124">Request URI</span></span>                                                                                 |
|-----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="eb81b-125">**Patch**</span><span class="sxs-lookup"><span data-stu-id="eb81b-125">**PATCH**</span></span> | <span data-ttu-id="eb81b-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="eb81b-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="eb81b-127">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="eb81b-127">URI parameter</span></span>

<span data-ttu-id="eb81b-128">Gebruik de volgende URI-parameter om de serviceaanvraag bij te werken.</span><span class="sxs-lookup"><span data-stu-id="eb81b-128">Use the following URI parameter to update the service request.</span></span>

| <span data-ttu-id="eb81b-129">Naam</span><span class="sxs-lookup"><span data-stu-id="eb81b-129">Name</span></span>                  | <span data-ttu-id="eb81b-130">Type</span><span class="sxs-lookup"><span data-stu-id="eb81b-130">Type</span></span>     | <span data-ttu-id="eb81b-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="eb81b-131">Required</span></span> | <span data-ttu-id="eb81b-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="eb81b-132">Description</span></span>                                 |
|-----------------------|----------|----------|---------------------------------------------|
| <span data-ttu-id="eb81b-133">**servicerequest-id**</span><span class="sxs-lookup"><span data-stu-id="eb81b-133">**servicerequest-id**</span></span> | <span data-ttu-id="eb81b-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="eb81b-134">**guid**</span></span> | <span data-ttu-id="eb81b-135">J</span><span class="sxs-lookup"><span data-stu-id="eb81b-135">Y</span></span>        | <span data-ttu-id="eb81b-136">Een GUID die de serviceaanvraag identificeert.</span><span class="sxs-lookup"><span data-stu-id="eb81b-136">A GUID that identifies the service request.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="eb81b-137">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="eb81b-137">Request headers</span></span>

<span data-ttu-id="eb81b-138">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="eb81b-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="eb81b-139">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="eb81b-139">Request body</span></span>

<span data-ttu-id="eb81b-140">De aanvraag body moet een [ServiceRequest-resource](service-request-resources.md) bevatten.</span><span class="sxs-lookup"><span data-stu-id="eb81b-140">The request body should contain a [ServiceRequest](service-request-resources.md) resource.</span></span> <span data-ttu-id="eb81b-141">De enige vereiste waarden zijn de waarden die moeten worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="eb81b-141">The only required values are those to be updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="eb81b-142">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="eb81b-142">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/servicerequests/616122292874576 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f9a030bd-e492-4c1a-9c70-021f18234981
MS-CorrelationId: fd969070-4e5f-4c6b-a3c6-1941283b39ae
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 508
Expect: 100-continue

{
    "Id": null,
    "Title": null,
    "Description": null,
    "Severity": "unknown",
    "SupportTopicId": null,
    "SupportTopicName": null,
    "Status": "none",
    "Organization": null,
    "PrimaryContact": null,
    "LastUpdatedBy": null,
    "ProductName": null,
    "ProductId": null,
    "CreatedDate": "0001-01-01T00:00:00",
    "LastModifiedDate": "0001-01-01T00:00:00",
    "LastClosedDate": "0001-01-01T00:00:00",
    "NewNote": {
        "CreatedByName": null,
        "CreatedDate": null,
        "Text": "Sample Note"
    },
    "Notes": null,
    "CountryCode": null,
    "FileLinks": null,
    "Attributes": {
        "ObjectType": "ServiceRequest"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="eb81b-143">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="eb81b-143">REST response</span></span>

<span data-ttu-id="eb81b-144">Als dit lukt, retourneert deze methode een **serviceaanvraagresource** met bijgewerkte eigenschappen in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="eb81b-144">If successful, this method returns a **Service Request** resource with updated properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="eb81b-145">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="eb81b-145">Response success and error codes</span></span>

<span data-ttu-id="eb81b-146">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="eb81b-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="eb81b-147">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="eb81b-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="eb81b-148">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="eb81b-148">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="eb81b-149">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="eb81b-149">Response example</span></span>

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
