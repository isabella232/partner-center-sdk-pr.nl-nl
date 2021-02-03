---
title: Een lijst met de apparaten voor de opgegeven batch en klant ophalen
description: Een verzameling apparaten en apparaatgegevens ophalen in de opgegeven apparaats batch voor een klant.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 36fe3b97612adfd26c1b498f31b90f743bf774cb
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767444"
---
# <a name="get-a-list-of-devices-for-the-specified-batch-and-customer"></a><span data-ttu-id="81dc5-103">Een lijst met de apparaten voor de opgegeven batch en klant ophalen</span><span class="sxs-lookup"><span data-stu-id="81dc5-103">Get a list of devices for the specified batch and customer</span></span>

<span data-ttu-id="81dc5-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="81dc5-104">**Applies to:**</span></span>

- <span data-ttu-id="81dc5-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="81dc5-105">Partner Center</span></span>
- <span data-ttu-id="81dc5-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="81dc5-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="81dc5-107">In dit artikel wordt beschreven hoe u een verzameling apparaten kunt ophalen in een opgegeven batch voor een opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="81dc5-107">This article describes how to retrieve a collection of devices in a specified device batch for a specified customer.</span></span> <span data-ttu-id="81dc5-108">Elke bron van het apparaat bevat details over het apparaat.</span><span class="sxs-lookup"><span data-stu-id="81dc5-108">Each device resource contains details about the device.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="81dc5-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="81dc5-109">Prerequisites</span></span>

- <span data-ttu-id="81dc5-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="81dc5-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="81dc5-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="81dc5-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="81dc5-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="81dc5-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="81dc5-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="81dc5-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="81dc5-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="81dc5-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="81dc5-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="81dc5-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="81dc5-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="81dc5-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="81dc5-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="81dc5-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="81dc5-118">Een batch-id voor het apparaat.</span><span class="sxs-lookup"><span data-stu-id="81dc5-118">A device batch identifier.</span></span>

## <a name="c"></a><span data-ttu-id="81dc5-119">C\#</span><span class="sxs-lookup"><span data-stu-id="81dc5-119">C\#</span></span>

<span data-ttu-id="81dc5-120">Ophalen van een verzameling van de apparaten in een opgegeven batch voor de opgegeven klant:</span><span class="sxs-lookup"><span data-stu-id="81dc5-120">To retrieve a collection of the devices in a specified device batch for the specified customer:</span></span>

1. <span data-ttu-id="81dc5-121">Roep de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="81dc5-121">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="81dc5-122">Roep de methode [**DeviceBatches. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) aan om een interface te verkrijgen voor het verzamelen van batch-bewerkingen voor het apparaat voor de opgegeven batch.</span><span class="sxs-lookup"><span data-stu-id="81dc5-122">Call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method to get an interface to device batch collection operations for the specified batch.</span></span>

3. <span data-ttu-id="81dc5-123">Haal de eigenschap [**apparaten**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatch.devices) op om een interface voor het verzamelen van apparaten op te halen voor de batch.</span><span class="sxs-lookup"><span data-stu-id="81dc5-123">Retrieve the [**Devices**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatch.devices) property to get an interface to device collection operations for the batch.</span></span>

4. <span data-ttu-id="81dc5-124">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.getasync) aan om de verzameling van apparaten op te halen.</span><span class="sxs-lookup"><span data-stu-id="81dc5-124">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.getasync) method to retrieve the collection of devices.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;

var devices =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.Get();
```

<span data-ttu-id="81dc5-125">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="81dc5-125">For an example, see the following:</span></span>

- <span data-ttu-id="81dc5-126">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="81dc5-126">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="81dc5-127">Project: **Partner Center SDK** -voor beelden</span><span class="sxs-lookup"><span data-stu-id="81dc5-127">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="81dc5-128">Klasse: **GetDevices.cs**</span><span class="sxs-lookup"><span data-stu-id="81dc5-128">Class: **GetDevices.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="81dc5-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="81dc5-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="81dc5-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="81dc5-130">Request syntax</span></span>

| <span data-ttu-id="81dc5-131">Methode</span><span class="sxs-lookup"><span data-stu-id="81dc5-131">Method</span></span>  | <span data-ttu-id="81dc5-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="81dc5-132">Request URI</span></span>                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="81dc5-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="81dc5-133">**GET**</span></span> | <span data-ttu-id="81dc5-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/deviceBatches/{devicebatch-ID}/devices http/1.1</span><span class="sxs-lookup"><span data-stu-id="81dc5-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="81dc5-135">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="81dc5-135">URI parameters</span></span>

<span data-ttu-id="81dc5-136">Gebruik de volgende Path-para meters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="81dc5-136">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="81dc5-137">Naam</span><span class="sxs-lookup"><span data-stu-id="81dc5-137">Name</span></span>           | <span data-ttu-id="81dc5-138">Type</span><span class="sxs-lookup"><span data-stu-id="81dc5-138">Type</span></span>   | <span data-ttu-id="81dc5-139">Vereist</span><span class="sxs-lookup"><span data-stu-id="81dc5-139">Required</span></span> | <span data-ttu-id="81dc5-140">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="81dc5-140">Description</span></span>                                           |
|----------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="81dc5-141">klant-id</span><span class="sxs-lookup"><span data-stu-id="81dc5-141">customer-id</span></span>    | <span data-ttu-id="81dc5-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="81dc5-142">string</span></span> | <span data-ttu-id="81dc5-143">Yes</span><span class="sxs-lookup"><span data-stu-id="81dc5-143">Yes</span></span>      | <span data-ttu-id="81dc5-144">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="81dc5-144">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="81dc5-145">devicebatch-id</span><span class="sxs-lookup"><span data-stu-id="81dc5-145">devicebatch-id</span></span> | <span data-ttu-id="81dc5-146">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="81dc5-146">string</span></span> | <span data-ttu-id="81dc5-147">Yes</span><span class="sxs-lookup"><span data-stu-id="81dc5-147">Yes</span></span>      | <span data-ttu-id="81dc5-148">Een teken reeks-id waarmee de apparaat-batch wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="81dc5-148">A string identifier that identifies the device batch.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="81dc5-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="81dc5-149">Request headers</span></span>

<span data-ttu-id="81dc5-150">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="81dc5-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="81dc5-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="81dc5-151">Request body</span></span>

<span data-ttu-id="81dc5-152">Geen</span><span class="sxs-lookup"><span data-stu-id="81dc5-152">None</span></span>

### <a name="request-example"></a><span data-ttu-id="81dc5-153">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="81dc5-153">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches/testbatch/devices HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="81dc5-154">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="81dc5-154">REST response</span></span>

<span data-ttu-id="81dc5-155">Als dit lukt, bevat de antwoord tekst een wissel bare verzameling van bronnen voor [apparaten](device-deployment-resources.md#device) .</span><span class="sxs-lookup"><span data-stu-id="81dc5-155">If successful, the response body contains a paged collection of [Device](device-deployment-resources.md#device) resources.</span></span> <span data-ttu-id="81dc5-156">De verzameling bevat 100-apparaten op een pagina.</span><span class="sxs-lookup"><span data-stu-id="81dc5-156">The collection contains 100 devices in a page.</span></span> <span data-ttu-id="81dc5-157">Als u de volgende pagina van 100 apparaten wilt ophalen, moet de continuationToken in de antwoord tekst worden opgenomen in de volgende aanvraag als MS-ContinuationToken-header.</span><span class="sxs-lookup"><span data-stu-id="81dc5-157">To retrieve the next page of 100 devices, the continuationToken in the response body must be included in the subsequent request as an MS-ContinuationToken header.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="81dc5-158">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="81dc5-158">Response success and error codes</span></span>

<span data-ttu-id="81dc5-159">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="81dc5-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="81dc5-160">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="81dc5-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="81dc5-161">Zie voor een volledige lijst de [rest-fout codes van het partner centrum](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="81dc5-161">For a full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="81dc5-162">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="81dc5-162">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1742
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 4a5002a2-0c1b-4e57-b491-dbcf19c0e7b8
MS-RequestId: 7b3e2e00-b330-4480-9d84-59ace713427f
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:52:41 GMT

{
    "totalCount": 2,
    "items":
    [{
            "id": "7c141ea9-2816-4e15-a819-53f6856499ff",
            "serialNumber": "2R9-ZNP67",
            "productKey": "00329-00000-0003-AA6069",
            "modelName": "Precision WorkStation T7500",
            "oemManufacturerName":"Dell Inc.",
            "policies":[{
                    "key": "o_o_b_e",
                    "value": null
                }
            ],
            "uploadedDate":"2017-08-09T14:43:26.0092288-07:00",
            " attributes": {
                "objectType": "Device"
            }
        }, {
            "id": "e528a62f-5031-49f4-bea7-5fafe47388fd",
            "serialNumber": "1234567890",
            "productKey": "12345-67890-09876-54321-13579",
            "modelName": "HP Z420 Workstation",
            "oemManufacturerName": "Hewlett-Packard",
            "policies": [{
                    "key": "o_o_b_e",
                    "value": null
                }
            ],
            "uploadedDate": "2017-08-09T14:35:51.3126144-07:00",
            "attributes": {
                "objectType": "Device"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
