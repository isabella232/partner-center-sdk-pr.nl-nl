---
title: Een serviceaanvraag bijwerken
description: Het bijwerken van een bestaande klanten service-aanvraag die een Cloud solution provider heeft ingediend bij micro soft namens de klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a1df0d1f5fa4630b346d1c8b9cffabb86ce34cfb
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767508"
---
# <a name="update-a-service-request"></a><span data-ttu-id="62701-103">Een serviceaanvraag bijwerken</span><span class="sxs-lookup"><span data-stu-id="62701-103">Update a service request</span></span>

<span data-ttu-id="62701-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="62701-104">**Applies To**</span></span>

- <span data-ttu-id="62701-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="62701-105">Partner Center</span></span>
- <span data-ttu-id="62701-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="62701-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="62701-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="62701-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="62701-108">Het bijwerken van een bestaande klanten service-aanvraag die een Cloud solution provider heeft ingediend bij micro soft namens de klant.</span><span class="sxs-lookup"><span data-stu-id="62701-108">How to update an existing customer service request that a Cloud Solution Provider has filed with Microsoft on the customer's behalf.</span></span>

<span data-ttu-id="62701-109">In het dash board van de partner centrum kan deze bewerking worden uitgevoerd door eerst [een klant te selecteren](get-a-customer-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="62701-109">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="62701-110">Selecteer vervolgens **Service beheer** op de zijbalk links.</span><span class="sxs-lookup"><span data-stu-id="62701-110">Then, select **Service management** on the left sidebar.</span></span> <span data-ttu-id="62701-111">Selecteer in de kop **ondersteunings aanvragen** de service aanvraag in kwestie.</span><span class="sxs-lookup"><span data-stu-id="62701-111">Under the **Support requests** header, select the service request in question.</span></span> <span data-ttu-id="62701-112">Als u wilt volt ooien, brengt u de gewenste wijzigingen aan in de service aanvraag en selecteert u vervolgens **verzenden.**</span><span class="sxs-lookup"><span data-stu-id="62701-112">To finish, make the desired changes to the service request then select **Submit.**</span></span>

## <a name="prerequisites"></a><span data-ttu-id="62701-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="62701-113">Prerequisites</span></span>

- <span data-ttu-id="62701-114">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="62701-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="62701-115">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="62701-115">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="62701-116">Een service aanvraag-ID.</span><span class="sxs-lookup"><span data-stu-id="62701-116">A service request ID.</span></span>

## <a name="c"></a><span data-ttu-id="62701-117">C\#</span><span class="sxs-lookup"><span data-stu-id="62701-117">C\#</span></span>

<span data-ttu-id="62701-118">Als u de service aanvraag van een klant wilt bijwerken, roept u de methode [**IServiceRequestCollection. ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) aan met de service aanvraag-id om de service aanvraag interface te identificeren en te retour neren.</span><span class="sxs-lookup"><span data-stu-id="62701-118">To update a customer's service request, call the [**IServiceRequestCollection.ById**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.byid) method with the service request id to identify and return the service request interface.</span></span> <span data-ttu-id="62701-119">Roep vervolgens de [**IServiceRequest. patch**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patch) -of [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patchasync) -methode aan om de service aanvraag bij te werken.</span><span class="sxs-lookup"><span data-stu-id="62701-119">Then call the [**IServiceRequest.Patch**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patch) or [**PatchAsync**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequest.patchasync) method to update the service request.</span></span> <span data-ttu-id="62701-120">Als u de bijgewerkte waarden wilt opgeven, maakt u een nieuw, leeg [**ServiceRequest**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) -object en stelt u alleen de eigenschaps waarden in die u wilt wijzigen.</span><span class="sxs-lookup"><span data-stu-id="62701-120">To provide the updated values, create a new, empty [**ServiceRequest**](/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest) object and set only the property values that you want to change.</span></span> <span data-ttu-id="62701-121">Geef dat object vervolgens door in de aanroep van de methode patch of PatchAsync.</span><span class="sxs-lookup"><span data-stu-id="62701-121">Then pass that object in the call to the Patch or PatchAsync method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// ServiceRequest existingServiceRequest;

ServiceRequest updatedServiceRequest = partnerOperations.ServiceRequests.ById(existingServiceRequest.Id).Patch(new ServiceRequest
{
   NewNote = note
});
```

<span data-ttu-id="62701-122">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="62701-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="62701-123">**Project**: Partner Center SDK-voor beelden **klasse**: UpdatePartnerServiceRequest.cs</span><span class="sxs-lookup"><span data-stu-id="62701-123">**Project**: Partner Center SDK Samples **Class**: UpdatePartnerServiceRequest.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="62701-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="62701-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="62701-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="62701-125">Request syntax</span></span>

| <span data-ttu-id="62701-126">Methode</span><span class="sxs-lookup"><span data-stu-id="62701-126">Method</span></span>    | <span data-ttu-id="62701-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="62701-127">Request URI</span></span>                                                                                 |
|-----------|---------------------------------------------------------------------------------------------|
| <span data-ttu-id="62701-128">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="62701-128">**PATCH**</span></span> | <span data-ttu-id="62701-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="62701-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/servicerequests/{servicerequest-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="62701-130">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="62701-130">URI parameter</span></span>

<span data-ttu-id="62701-131">Gebruik de volgende URI-para meter om de service aanvraag bij te werken.</span><span class="sxs-lookup"><span data-stu-id="62701-131">Use the following URI parameter to update the service request.</span></span>

| <span data-ttu-id="62701-132">Naam</span><span class="sxs-lookup"><span data-stu-id="62701-132">Name</span></span>                  | <span data-ttu-id="62701-133">Type</span><span class="sxs-lookup"><span data-stu-id="62701-133">Type</span></span>     | <span data-ttu-id="62701-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="62701-134">Required</span></span> | <span data-ttu-id="62701-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="62701-135">Description</span></span>                                 |
|-----------------------|----------|----------|---------------------------------------------|
| <span data-ttu-id="62701-136">**servicerequest-id**</span><span class="sxs-lookup"><span data-stu-id="62701-136">**servicerequest-id**</span></span> | <span data-ttu-id="62701-137">**guid**</span><span class="sxs-lookup"><span data-stu-id="62701-137">**guid**</span></span> | <span data-ttu-id="62701-138">J</span><span class="sxs-lookup"><span data-stu-id="62701-138">Y</span></span>        | <span data-ttu-id="62701-139">Een GUID waarmee de service aanvraag wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="62701-139">A GUID that identifies the service request.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="62701-140">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="62701-140">Request headers</span></span>

<span data-ttu-id="62701-141">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="62701-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="62701-142">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="62701-142">Request body</span></span>

<span data-ttu-id="62701-143">De aanvraag tekst moet een [ServiceRequest](service-request-resources.md) -resource bevatten.</span><span class="sxs-lookup"><span data-stu-id="62701-143">The request body should contain a [ServiceRequest](service-request-resources.md) resource.</span></span> <span data-ttu-id="62701-144">De enige vereiste waarden zijn die die moeten worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="62701-144">The only required values are those to be updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="62701-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="62701-145">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="62701-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="62701-146">REST response</span></span>

<span data-ttu-id="62701-147">Als dit lukt, retourneert deze methode een resource van een **service aanvraag** met bijgewerkte eigenschappen in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="62701-147">If successful, this method returns a **Service Request** resource with updated properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="62701-148">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="62701-148">Response success and error codes</span></span>

<span data-ttu-id="62701-149">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="62701-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="62701-150">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="62701-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="62701-151">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="62701-151">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="62701-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="62701-152">Response example</span></span>

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
