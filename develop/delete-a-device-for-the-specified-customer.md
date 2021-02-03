---
title: Een apparaat voor de opgegeven klant verwijderen
description: Een apparaat verwijderen dat bij een opgegeven klant hoort.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 69b5440f2cf07d3cb4ecd5addf429acd64530257
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767390"
---
# <a name="delete-a-device-for-the-specified-customer"></a><span data-ttu-id="cf4c7-103">Een apparaat voor de opgegeven klant verwijderen</span><span class="sxs-lookup"><span data-stu-id="cf4c7-103">Delete a device for the specified customer</span></span>

<span data-ttu-id="cf4c7-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="cf4c7-104">**Applies to:**</span></span>

- <span data-ttu-id="cf4c7-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="cf4c7-105">Partner Center</span></span>
- <span data-ttu-id="cf4c7-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="cf4c7-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="cf4c7-107">In dit artikel wordt uitgelegd hoe u een apparaat verwijdert dat deel uitmaakt van een opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-107">This article explains how to delete a device that belongs to a specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cf4c7-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cf4c7-108">Prerequisites</span></span>

- <span data-ttu-id="cf4c7-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cf4c7-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cf4c7-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="cf4c7-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cf4c7-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="cf4c7-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="cf4c7-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="cf4c7-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="cf4c7-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="cf4c7-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="cf4c7-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cf4c7-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="cf4c7-117">De batch-id van het apparaat.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-117">The device batch identifier.</span></span>

- <span data-ttu-id="cf4c7-118">De apparaat-id.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-118">The device identifier.</span></span>

## <a name="c"></a><span data-ttu-id="cf4c7-119">C\#</span><span class="sxs-lookup"><span data-stu-id="cf4c7-119">C\#</span></span>

<span data-ttu-id="cf4c7-120">Een apparaat voor de opgegeven klant verwijderen:</span><span class="sxs-lookup"><span data-stu-id="cf4c7-120">To delete a device for the specified customer:</span></span>

1. <span data-ttu-id="cf4c7-121">Roep de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de klant.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-121">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the customer.</span></span>

2. <span data-ttu-id="cf4c7-122">Roep de methode [**DeviceBatches. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) aan met de batch-id van het apparaat om een interface te verkrijgen voor bewerkingen voor de opgegeven batch.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-122">Call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method with the device batch identifier to get an interface to operations for the specified batch.</span></span>

3. <span data-ttu-id="cf4c7-123">Roep de methode [**devices. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.byid) aan om een interface te verkrijgen voor bewerking op het opgegeven apparaat.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-123">Call the [**Devices.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.byid) method to get an interface to operation on the specified device.</span></span>

4. <span data-ttu-id="cf4c7-124">Roep de methode [**Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.delete) of [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.deleteasync) aan om het apparaat uit de batch te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-124">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.delete) or [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.deleteasync) method to delete the device from the batch.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;
string selectedDeviceId;

partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.ById(selectedDeviceId).Delete();
```

<span data-ttu-id="cf4c7-125">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="cf4c7-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="cf4c7-126">**Project**: Partner Center SDK-voor beelden **klasse**: DeleteDevice.cs</span><span class="sxs-lookup"><span data-stu-id="cf4c7-126">**Project**: Partner Center SDK Samples **Class**: DeleteDevice.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="cf4c7-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="cf4c7-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cf4c7-128">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cf4c7-128">Request syntax</span></span>

| <span data-ttu-id="cf4c7-129">Methode</span><span class="sxs-lookup"><span data-stu-id="cf4c7-129">Method</span></span>     | <span data-ttu-id="cf4c7-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="cf4c7-130">Request URI</span></span>                                                                                                                        |
|------------|------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cf4c7-131">DELETE</span><span class="sxs-lookup"><span data-stu-id="cf4c7-131">DELETE</span></span>     | <span data-ttu-id="cf4c7-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/deviceBatches/{devicebatch-ID}/devices/{Device-ID} http/1.1</span><span class="sxs-lookup"><span data-stu-id="cf4c7-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices/{device-id} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="cf4c7-133">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="cf4c7-133">URI parameters</span></span>

<span data-ttu-id="cf4c7-134">Gebruik de volgende Path-para meters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-134">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="cf4c7-135">Naam</span><span class="sxs-lookup"><span data-stu-id="cf4c7-135">Name</span></span>           | <span data-ttu-id="cf4c7-136">Type</span><span class="sxs-lookup"><span data-stu-id="cf4c7-136">Type</span></span>   | <span data-ttu-id="cf4c7-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="cf4c7-137">Required</span></span> | <span data-ttu-id="cf4c7-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cf4c7-138">Description</span></span>                                                        |
|----------------|--------|----------|--------------------------------------------------------------------|
| <span data-ttu-id="cf4c7-139">klant-id</span><span class="sxs-lookup"><span data-stu-id="cf4c7-139">customer-id</span></span>    | <span data-ttu-id="cf4c7-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="cf4c7-140">string</span></span> | <span data-ttu-id="cf4c7-141">Yes</span><span class="sxs-lookup"><span data-stu-id="cf4c7-141">Yes</span></span>      | <span data-ttu-id="cf4c7-142">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-142">A GUID-formatted string that identifies the customer.</span></span>              |
| <span data-ttu-id="cf4c7-143">devicebatch-id</span><span class="sxs-lookup"><span data-stu-id="cf4c7-143">devicebatch-id</span></span> | <span data-ttu-id="cf4c7-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="cf4c7-144">string</span></span> | <span data-ttu-id="cf4c7-145">Yes</span><span class="sxs-lookup"><span data-stu-id="cf4c7-145">Yes</span></span>      | <span data-ttu-id="cf4c7-146">De batch-id van het apparaat van de batch die het apparaat bevat.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-146">The device batch identifier of the batch that contains the device.</span></span> |
| <span data-ttu-id="cf4c7-147">apparaat-id</span><span class="sxs-lookup"><span data-stu-id="cf4c7-147">device-id</span></span>      | <span data-ttu-id="cf4c7-148">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="cf4c7-148">string</span></span> | <span data-ttu-id="cf4c7-149">Yes</span><span class="sxs-lookup"><span data-stu-id="cf4c7-149">Yes</span></span>      | <span data-ttu-id="cf4c7-150">De apparaat-id.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-150">The device identifier.</span></span>                                             |

### <a name="request-headers"></a><span data-ttu-id="cf4c7-151">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="cf4c7-151">Request headers</span></span>

<span data-ttu-id="cf4c7-152">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cf4c7-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cf4c7-153">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="cf4c7-153">Request body</span></span>

<span data-ttu-id="cf4c7-154">Geen</span><span class="sxs-lookup"><span data-stu-id="cf4c7-154">None</span></span>

### <a name="request-example"></a><span data-ttu-id="cf4c7-155">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cf4c7-155">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="cf4c7-156">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="cf4c7-156">REST response</span></span>

<span data-ttu-id="cf4c7-157">Als de aanvraag is voltooid, wordt de status code van **204 geen inhoud** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-157">If successful, the response returns a **204 No Content** status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cf4c7-158">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="cf4c7-158">Response success and error codes</span></span>

<span data-ttu-id="cf4c7-159">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cf4c7-160">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cf4c7-161">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="cf4c7-161">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cf4c7-162">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="cf4c7-162">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 394d96d0-05b2-4b02-b907-0697632ee3bb
MS-RequestId: 8b3e6f78-220b-4177-861b-33d6f38f7b97
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:58:53 GMT
```
