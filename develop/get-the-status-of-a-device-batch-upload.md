---
title: De status ophalen van het uploaden van een apparaat-batch
description: De status van het batchupload van een apparaat voor een opgegeven klant krijgen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fd8726af41fe4399797f39a0790cf962fde64acc
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548478"
---
# <a name="get-the-status-of-a-device-batch-upload"></a><span data-ttu-id="e9b5d-103">De status ophalen van het uploaden van een apparaat-batch</span><span class="sxs-lookup"><span data-stu-id="e9b5d-103">Get the status of a device batch upload</span></span>

<span data-ttu-id="e9b5d-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="e9b5d-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="e9b5d-105">De status van het batchupload van een apparaat voor een opgegeven klant krijgen.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-105">How to get the status of a device batch upload for a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e9b5d-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e9b5d-106">Prerequisites</span></span>

- <span data-ttu-id="e9b5d-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e9b5d-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e9b5d-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e9b5d-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e9b5d-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e9b5d-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="e9b5d-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e9b5d-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="e9b5d-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e9b5d-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e9b5d-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="e9b5d-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e9b5d-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e9b5d-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="e9b5d-115">De batchtracking-id die wordt geretourneerd in de Location-header toen de apparaatbatch werd verzonden.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-115">The batch tracking identifier returned in the Location header when the device batch was submitted.</span></span> <span data-ttu-id="e9b5d-116">Zie een lijst Upload apparaten voor de opgegeven klant voor [meer informatie.](upload-a-list-of-devices-for-the-specified-customer.md)</span><span class="sxs-lookup"><span data-stu-id="e9b5d-116">For more information, see [Upload a list of devices for the specified customer](upload-a-list-of-devices-for-the-specified-customer.md).</span></span>

## <a name="c"></a><span data-ttu-id="e9b5d-117">C\#</span><span class="sxs-lookup"><span data-stu-id="e9b5d-117">C\#</span></span>

<span data-ttu-id="e9b5d-118">Als u de status van een batchupload van een apparaat wilt ophalen, roept u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-118">To get the status of a device batch upload, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="e9b5d-119">Roep vervolgens de methode [**BatchUploadStatus.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatuscollection.byid) aan met de batchtracking-id om een interface op te halen voor batchuploadstatusbewerkingen.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-119">Then, call the [**BatchUploadStatus.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatuscollection.byid) method with the batch tracking ID to get an interface to batch upload status operations.</span></span> <span data-ttu-id="e9b5d-120">Roep ten slotte de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.getasync) om de status op te halen.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-120">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.ibatchjobstatus.getasync) method to retrieve the status.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedTrackingId;

var status =
    partnerOperations.Customers.ById(selectedCustomerId).BatchUploadStatus.ById(selectedTrackingId).Get();
```

<span data-ttu-id="e9b5d-121">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e9b5d-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e9b5d-122">**Project**: Partnercentrum-SDK Samples **Class**: GetBatchUploadStatus.cs</span><span class="sxs-lookup"><span data-stu-id="e9b5d-122">**Project**: Partner Center SDK Samples **Class**: GetBatchUploadStatus.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e9b5d-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e9b5d-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e9b5d-124">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e9b5d-124">Request syntax</span></span>

| <span data-ttu-id="e9b5d-125">Methode</span><span class="sxs-lookup"><span data-stu-id="e9b5d-125">Method</span></span>  | <span data-ttu-id="e9b5d-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e9b5d-126">Request URI</span></span>                                                                                                       |
|---------|-------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e9b5d-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="e9b5d-127">**GET**</span></span> | <span data-ttu-id="e9b5d-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/batchJobStatus/{batchtracking-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e9b5d-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/batchJobStatus/{batchtracking-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="e9b5d-129">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="e9b5d-129">URI parameter</span></span>

<span data-ttu-id="e9b5d-130">Gebruik de volgende padparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-130">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="e9b5d-131">Naam</span><span class="sxs-lookup"><span data-stu-id="e9b5d-131">Name</span></span>             | <span data-ttu-id="e9b5d-132">Type</span><span class="sxs-lookup"><span data-stu-id="e9b5d-132">Type</span></span>   | <span data-ttu-id="e9b5d-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="e9b5d-133">Required</span></span> | <span data-ttu-id="e9b5d-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e9b5d-134">Description</span></span>                                                                                                                                                                    |
|------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e9b5d-135">customer-id</span><span class="sxs-lookup"><span data-stu-id="e9b5d-135">customer-id</span></span>      | <span data-ttu-id="e9b5d-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e9b5d-136">string</span></span> | <span data-ttu-id="e9b5d-137">Ja</span><span class="sxs-lookup"><span data-stu-id="e9b5d-137">Yes</span></span>      | <span data-ttu-id="e9b5d-138">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-138">A GUID-formatted string that identifies the customer.</span></span>                                                                                                                          |
| <span data-ttu-id="e9b5d-139">batchtracking-id</span><span class="sxs-lookup"><span data-stu-id="e9b5d-139">batchtracking-id</span></span> | <span data-ttu-id="e9b5d-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e9b5d-140">string</span></span> | <span data-ttu-id="e9b5d-141">Ja</span><span class="sxs-lookup"><span data-stu-id="e9b5d-141">Yes</span></span>      | <span data-ttu-id="e9b5d-142">Een id met GUID-indeling die wordt gebruikt om de status van het batchupload van een apparaat op te halen.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-142">A GUID-formatted identifier that is used to retrieve a device batch upload status.</span></span> <span data-ttu-id="e9b5d-143">Deze id wordt geretourneerd in de Location-header wanneer de batch van het apparaat is verzonden.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-143">This ID is returned in the Location header when the device batch is successfully submitted.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e9b5d-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e9b5d-144">Request headers</span></span>

<span data-ttu-id="e9b5d-145">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e9b5d-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e9b5d-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e9b5d-146">Request body</span></span>

<span data-ttu-id="e9b5d-147">Geen</span><span class="sxs-lookup"><span data-stu-id="e9b5d-147">None</span></span>

### <a name="request-example"></a><span data-ttu-id="e9b5d-148">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e9b5d-148">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/batchjobstatus/0127ed8e-ff72-4983-a3d8-e8d8bd378932 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="e9b5d-149">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e9b5d-149">REST response</span></span>

<span data-ttu-id="e9b5d-150">Als dit lukt, bevat het antwoord een [BatchUploadDetails-resource.](device-deployment-resources.md#batchuploaddetails)</span><span class="sxs-lookup"><span data-stu-id="e9b5d-150">If successful, the response contains a [BatchUploadDetails](device-deployment-resources.md#batchuploaddetails) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e9b5d-151">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e9b5d-151">Response success and error codes</span></span>

<span data-ttu-id="e9b5d-152">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-152">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e9b5d-153">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e9b5d-153">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e9b5d-154">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e9b5d-154">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e9b5d-155">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e9b5d-155">Response example</span></span>

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
