---
title: Een apparaat voor de opgegeven klant verwijderen
description: Een apparaat verwijderen dat bij een opgegeven klant hoort.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a1e05ceb8615d6f84c1df101c542342f9a6eb04b
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973074"
---
# <a name="delete-a-device-for-the-specified-customer"></a><span data-ttu-id="7c0bd-103">Een apparaat voor de opgegeven klant verwijderen</span><span class="sxs-lookup"><span data-stu-id="7c0bd-103">Delete a device for the specified customer</span></span>

<span data-ttu-id="7c0bd-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="7c0bd-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="7c0bd-105">In dit artikel wordt uitgelegd hoe u een apparaat verwijdert dat bij een opgegeven klant hoort.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-105">This article explains how to delete a device that belongs to a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c0bd-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7c0bd-106">Prerequisites</span></span>

- <span data-ttu-id="7c0bd-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7c0bd-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7c0bd-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="7c0bd-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7c0bd-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7c0bd-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="7c0bd-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7c0bd-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="7c0bd-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7c0bd-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7c0bd-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="7c0bd-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7c0bd-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7c0bd-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7c0bd-115">De batch-id van het apparaat.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-115">The device batch identifier.</span></span>

- <span data-ttu-id="7c0bd-116">De apparaat-id.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-116">The device identifier.</span></span>

## <a name="c"></a><span data-ttu-id="7c0bd-117">C\#</span><span class="sxs-lookup"><span data-stu-id="7c0bd-117">C\#</span></span>

<span data-ttu-id="7c0bd-118">Een apparaat voor de opgegeven klant verwijderen:</span><span class="sxs-lookup"><span data-stu-id="7c0bd-118">To delete a device for the specified customer:</span></span>

1. <span data-ttu-id="7c0bd-119">Roep de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface voor bewerkingen op de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-119">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the customer.</span></span>

2. <span data-ttu-id="7c0bd-120">Roep de [**methode DeviceBatches.ById aan met**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) de batch-id van het apparaat om een interface op te halen voor bewerkingen voor de opgegeven batch.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-120">Call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method with the device batch identifier to get an interface to operations for the specified batch.</span></span>

3. <span data-ttu-id="7c0bd-121">Roep de [**methode Devices.ById aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.byid) om een interface op te halen voor bewerking op het opgegeven apparaat.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-121">Call the [**Devices.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.byid) method to get an interface to operation on the specified device.</span></span>

4. <span data-ttu-id="7c0bd-122">Roep de [**methode Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.delete) of [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.deleteasync) aan om het apparaat uit de batch te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-122">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.deleteasync) method to delete the device from the batch.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;
string selectedDeviceId;

partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.ById(selectedDeviceId).Delete();
```

<span data-ttu-id="7c0bd-123">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="7c0bd-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="7c0bd-124">**Project:** Partnercentrum-SDK Klasse **Samples:** DeleteDevice.cs</span><span class="sxs-lookup"><span data-stu-id="7c0bd-124">**Project**: Partner Center SDK Samples **Class**: DeleteDevice.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="7c0bd-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7c0bd-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7c0bd-126">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="7c0bd-126">Request syntax</span></span>

| <span data-ttu-id="7c0bd-127">Methode</span><span class="sxs-lookup"><span data-stu-id="7c0bd-127">Method</span></span>     | <span data-ttu-id="7c0bd-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7c0bd-128">Request URI</span></span>                                                                                                                        |
|------------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7c0bd-129">DELETE</span><span class="sxs-lookup"><span data-stu-id="7c0bd-129">DELETE</span></span>     | <span data-ttu-id="7c0bd-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices/{device-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7c0bd-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices/{device-id} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="7c0bd-131">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="7c0bd-131">URI parameters</span></span>

<span data-ttu-id="7c0bd-132">Gebruik de volgende padparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-132">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="7c0bd-133">Naam</span><span class="sxs-lookup"><span data-stu-id="7c0bd-133">Name</span></span>           | <span data-ttu-id="7c0bd-134">Type</span><span class="sxs-lookup"><span data-stu-id="7c0bd-134">Type</span></span>   | <span data-ttu-id="7c0bd-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="7c0bd-135">Required</span></span> | <span data-ttu-id="7c0bd-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7c0bd-136">Description</span></span>                                                        |
|----------------|--------|----------|--------------------------------------------------------------------|
| <span data-ttu-id="7c0bd-137">customer-id</span><span class="sxs-lookup"><span data-stu-id="7c0bd-137">customer-id</span></span>    | <span data-ttu-id="7c0bd-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7c0bd-138">string</span></span> | <span data-ttu-id="7c0bd-139">Ja</span><span class="sxs-lookup"><span data-stu-id="7c0bd-139">Yes</span></span>      | <span data-ttu-id="7c0bd-140">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-140">A GUID-formatted string that identifies the customer.</span></span>              |
| <span data-ttu-id="7c0bd-141">devicebatch-id</span><span class="sxs-lookup"><span data-stu-id="7c0bd-141">devicebatch-id</span></span> | <span data-ttu-id="7c0bd-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7c0bd-142">string</span></span> | <span data-ttu-id="7c0bd-143">Ja</span><span class="sxs-lookup"><span data-stu-id="7c0bd-143">Yes</span></span>      | <span data-ttu-id="7c0bd-144">De batch-id van het apparaat van de batch die het apparaat bevat.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-144">The device batch identifier of the batch that contains the device.</span></span> |
| <span data-ttu-id="7c0bd-145">device-id</span><span class="sxs-lookup"><span data-stu-id="7c0bd-145">device-id</span></span>      | <span data-ttu-id="7c0bd-146">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7c0bd-146">string</span></span> | <span data-ttu-id="7c0bd-147">Ja</span><span class="sxs-lookup"><span data-stu-id="7c0bd-147">Yes</span></span>      | <span data-ttu-id="7c0bd-148">De apparaat-id.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-148">The device identifier.</span></span>                                             |

### <a name="request-headers"></a><span data-ttu-id="7c0bd-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7c0bd-149">Request headers</span></span>

<span data-ttu-id="7c0bd-150">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="7c0bd-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7c0bd-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7c0bd-151">Request body</span></span>

<span data-ttu-id="7c0bd-152">Geen</span><span class="sxs-lookup"><span data-stu-id="7c0bd-152">None</span></span>

### <a name="request-example"></a><span data-ttu-id="7c0bd-153">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7c0bd-153">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches/testbatch/devices/7b11cd8b-dd1e-4840-8c4a-84215e4de782 HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Content-Length: 0
Content-Type: application/json
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="7c0bd-154">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7c0bd-154">REST response</span></span>

<span data-ttu-id="7c0bd-155">Als dit lukt, retourneert het antwoord de statuscode **204 Geen** inhoud.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-155">If successful, the response returns a **204 No Content** status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7c0bd-156">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="7c0bd-156">Response success and error codes</span></span>

<span data-ttu-id="7c0bd-157">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7c0bd-158">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7c0bd-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7c0bd-159">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="7c0bd-159">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7c0bd-160">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="7c0bd-160">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 394d96d0-05b2-4b02-b907-0697632ee3bb
MS-RequestId: 8b3e6f78-220b-4177-861b-33d6f38f7b97
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:58:53 GMT
```
