---
title: De status ophalen van het uploaden van een apparaat-batch
description: De status ophalen van een batch upload voor een specifieke klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fb887ba257d6fbe68f95ae4b59d701ac4c934860
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767526"
---
# <a name="get-the-status-of-a-device-batch-upload"></a><span data-ttu-id="80ef8-103">De status ophalen van het uploaden van een apparaat-batch</span><span class="sxs-lookup"><span data-stu-id="80ef8-103">Get the status of a device batch upload</span></span>

<span data-ttu-id="80ef8-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="80ef8-104">**Applies To**</span></span>

- <span data-ttu-id="80ef8-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="80ef8-105">Partner Center</span></span>
- <span data-ttu-id="80ef8-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="80ef8-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="80ef8-107">De status ophalen van een batch upload voor een specifieke klant.</span><span class="sxs-lookup"><span data-stu-id="80ef8-107">How to get the status of a device batch upload for a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="80ef8-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="80ef8-108">Prerequisites</span></span>

- <span data-ttu-id="80ef8-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="80ef8-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="80ef8-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="80ef8-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="80ef8-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="80ef8-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="80ef8-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="80ef8-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="80ef8-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="80ef8-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="80ef8-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="80ef8-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="80ef8-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="80ef8-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="80ef8-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="80ef8-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="80ef8-117">De batch tracerings-ID die wordt geretourneerd in de locatie header wanneer de batch met het apparaat is ingediend.</span><span class="sxs-lookup"><span data-stu-id="80ef8-117">The batch tracking identifier returned in the Location header when the device batch was submitted.</span></span> <span data-ttu-id="80ef8-118">Zie [een lijst met apparaten uploaden voor de opgegeven klant](upload-a-list-of-devices-for-the-specified-customer.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="80ef8-118">For more information, see [Upload a list of devices for the specified customer](upload-a-list-of-devices-for-the-specified-customer.md).</span></span>

## <a name="c"></a><span data-ttu-id="80ef8-119">C\#</span><span class="sxs-lookup"><span data-stu-id="80ef8-119">C\#</span></span>

<span data-ttu-id="80ef8-120">Als u de status van een batch upload wilt ophalen, roept u eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="80ef8-120">To get the status of a device batch upload, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="80ef8-121">Vervolgens roept u de methode [**BatchUploadStatus. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatuscollection.byid) aan met de batch TRACERINGS-id om een interface te verkrijgen voor het uploaden van batch-upload status bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="80ef8-121">Then, call the [**BatchUploadStatus.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatuscollection.byid) method with the batch tracking ID to get an interface to batch upload status operations.</span></span> <span data-ttu-id="80ef8-122">Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.getasync) aan om de status op te halen.</span><span class="sxs-lookup"><span data-stu-id="80ef8-122">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.getasync) method to retrieve the status.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedTrackingId;

var status =
    partnerOperations.Customers.ById(selectedCustomerId).BatchUploadStatus.ById(selectedTrackingId).Get();
```

<span data-ttu-id="80ef8-123">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="80ef8-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="80ef8-124">**Project**: Partner Center SDK-voor beelden **klasse**: GetBatchUploadStatus.cs</span><span class="sxs-lookup"><span data-stu-id="80ef8-124">**Project**: Partner Center SDK Samples **Class**: GetBatchUploadStatus.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="80ef8-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="80ef8-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="80ef8-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="80ef8-126">Request syntax</span></span>

| <span data-ttu-id="80ef8-127">Methode</span><span class="sxs-lookup"><span data-stu-id="80ef8-127">Method</span></span>  | <span data-ttu-id="80ef8-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="80ef8-128">Request URI</span></span>                                                                                                       |
|---------|-------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="80ef8-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="80ef8-129">**GET**</span></span> | <span data-ttu-id="80ef8-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/batchJobStatus/{batchtracking-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="80ef8-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/batchJobStatus/{batchtracking-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="80ef8-131">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="80ef8-131">URI parameter</span></span>

<span data-ttu-id="80ef8-132">Gebruik de volgende Path-para meters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="80ef8-132">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="80ef8-133">Naam</span><span class="sxs-lookup"><span data-stu-id="80ef8-133">Name</span></span>             | <span data-ttu-id="80ef8-134">Type</span><span class="sxs-lookup"><span data-stu-id="80ef8-134">Type</span></span>   | <span data-ttu-id="80ef8-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="80ef8-135">Required</span></span> | <span data-ttu-id="80ef8-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="80ef8-136">Description</span></span>                                                                                                                                                                    |
|------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="80ef8-137">klant-id</span><span class="sxs-lookup"><span data-stu-id="80ef8-137">customer-id</span></span>      | <span data-ttu-id="80ef8-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="80ef8-138">string</span></span> | <span data-ttu-id="80ef8-139">Yes</span><span class="sxs-lookup"><span data-stu-id="80ef8-139">Yes</span></span>      | <span data-ttu-id="80ef8-140">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="80ef8-140">A GUID-formatted string that identifies the customer.</span></span>                                                                                                                          |
| <span data-ttu-id="80ef8-141">batchtracking-id</span><span class="sxs-lookup"><span data-stu-id="80ef8-141">batchtracking-id</span></span> | <span data-ttu-id="80ef8-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="80ef8-142">string</span></span> | <span data-ttu-id="80ef8-143">Yes</span><span class="sxs-lookup"><span data-stu-id="80ef8-143">Yes</span></span>      | <span data-ttu-id="80ef8-144">Een id met de GUID-indeling die wordt gebruikt voor het ophalen van de upload status van een batch.</span><span class="sxs-lookup"><span data-stu-id="80ef8-144">A GUID-formatted identifier that is used to retrieve a device batch upload status.</span></span> <span data-ttu-id="80ef8-145">Deze ID wordt geretourneerd in de locatie header wanneer de apparaat-batch is verzonden.</span><span class="sxs-lookup"><span data-stu-id="80ef8-145">This ID is returned in the Location header when the device batch is successfully submitted.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="80ef8-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="80ef8-146">Request headers</span></span>

<span data-ttu-id="80ef8-147">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="80ef8-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="80ef8-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="80ef8-148">Request body</span></span>

<span data-ttu-id="80ef8-149">Geen</span><span class="sxs-lookup"><span data-stu-id="80ef8-149">None</span></span>

### <a name="request-example"></a><span data-ttu-id="80ef8-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="80ef8-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/batchjobstatus/0127ed8e-ff72-4983-a3d8-e8d8bd378932 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="80ef8-151">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="80ef8-151">REST response</span></span>

<span data-ttu-id="80ef8-152">Als dit is gelukt, bevat het antwoord een [BatchUploadDetails](device-deployment-resources.md#batchuploaddetails) -resource.</span><span class="sxs-lookup"><span data-stu-id="80ef8-152">If successful, the response contains a [BatchUploadDetails](device-deployment-resources.md#batchuploaddetails) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="80ef8-153">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="80ef8-153">Response success and error codes</span></span>

<span data-ttu-id="80ef8-154">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="80ef8-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="80ef8-155">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="80ef8-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="80ef8-156">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="80ef8-156">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="80ef8-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="80ef8-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 400
MS-CorrelationId: 4a5002a2-0c1b-4e57-b491-dbcf19c0e7b8
MS-RequestId: 7b3e2e00-b330-4480-9d84-59ace713427f
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:52:41 GMT

{
    "batchTrackingId": "0127ed8e-ff72-4983-a3d8-e8d8bd378932",
    "status": "finished",
    "startedTime": "2017-07-25T10:00:00",
    "completedTime": "2017-07-25T10:10:00",
    "devicesStatus": [{
            "serialNumber": "1234567890",
            "productKey": "12345-67890-09876-54321-13579",
            "status": "finished_with_errors",
            "errorCode": "808",
            "errorDescription": "ZtdDeviceAssignedToOtherTenant",
            "attributes": {
                "objectType": "DeviceUploadDetails"
            }
        }
    ],
    "attributes": {
        "objectType": "BatchUploadDetails"
    }
}
```
