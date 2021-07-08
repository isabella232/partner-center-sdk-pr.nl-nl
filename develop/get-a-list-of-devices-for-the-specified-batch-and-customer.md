---
title: Een lijst met de apparaten voor de opgegeven batch en klant ophalen
description: Een verzameling apparaten en apparaatdetails ophalen in de opgegeven apparaatbatch voor een klant.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 28af1f568f755ba4c50cfac21529d6c677656c8e
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874258"
---
# <a name="get-a-list-of-devices-for-the-specified-batch-and-customer"></a><span data-ttu-id="9de2a-103">Een lijst met de apparaten voor de opgegeven batch en klant ophalen</span><span class="sxs-lookup"><span data-stu-id="9de2a-103">Get a list of devices for the specified batch and customer</span></span>

<span data-ttu-id="9de2a-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="9de2a-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="9de2a-105">In dit artikel wordt beschreven hoe u een verzameling apparaten in een opgegeven apparaatbatch ophaalt voor een opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="9de2a-105">This article describes how to retrieve a collection of devices in a specified device batch for a specified customer.</span></span> <span data-ttu-id="9de2a-106">Elke apparaatresource bevat details over het apparaat.</span><span class="sxs-lookup"><span data-stu-id="9de2a-106">Each device resource contains details about the device.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9de2a-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9de2a-107">Prerequisites</span></span>

- <span data-ttu-id="9de2a-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9de2a-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9de2a-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="9de2a-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="9de2a-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9de2a-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="9de2a-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="9de2a-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="9de2a-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="9de2a-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="9de2a-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="9de2a-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="9de2a-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="9de2a-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="9de2a-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9de2a-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="9de2a-116">Een batch-id van een apparaat.</span><span class="sxs-lookup"><span data-stu-id="9de2a-116">A device batch identifier.</span></span>

## <a name="c"></a><span data-ttu-id="9de2a-117">C\#</span><span class="sxs-lookup"><span data-stu-id="9de2a-117">C\#</span></span>

<span data-ttu-id="9de2a-118">Een verzameling van de apparaten in een opgegeven apparaatbatch ophalen voor de opgegeven klant:</span><span class="sxs-lookup"><span data-stu-id="9de2a-118">To retrieve a collection of the devices in a specified device batch for the specified customer:</span></span>

1. <span data-ttu-id="9de2a-119">Roep de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="9de2a-119">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="9de2a-120">Roep de [**methode DeviceBatches.ById aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) om een interface op te halen voor batchverzamelingsbewerkingen van apparaten voor de opgegeven batch.</span><span class="sxs-lookup"><span data-stu-id="9de2a-120">Call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method to get an interface to device batch collection operations for the specified batch.</span></span>

3. <span data-ttu-id="9de2a-121">Haal de [**eigenschap Apparaten**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatch.devices) op om een interface op te halen voor bewerkingen voor het verzamelen van apparaten voor de batch.</span><span class="sxs-lookup"><span data-stu-id="9de2a-121">Retrieve the [**Devices**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatch.devices) property to get an interface to device collection operations for the batch.</span></span>

4. <span data-ttu-id="9de2a-122">Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.getasync) om de verzameling apparaten op te halen.</span><span class="sxs-lookup"><span data-stu-id="9de2a-122">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.getasync) method to retrieve the collection of devices.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;

var devices =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.Get();
```

<span data-ttu-id="9de2a-123">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="9de2a-123">For an example, see the following:</span></span>

- <span data-ttu-id="9de2a-124">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="9de2a-124">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="9de2a-125">Project: **Partnercentrum-SDK Voorbeelden**</span><span class="sxs-lookup"><span data-stu-id="9de2a-125">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="9de2a-126">Klasse: **GetDevices.cs**</span><span class="sxs-lookup"><span data-stu-id="9de2a-126">Class: **GetDevices.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="9de2a-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9de2a-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9de2a-128">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="9de2a-128">Request syntax</span></span>

| <span data-ttu-id="9de2a-129">Methode</span><span class="sxs-lookup"><span data-stu-id="9de2a-129">Method</span></span>  | <span data-ttu-id="9de2a-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="9de2a-130">Request URI</span></span>                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9de2a-131">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="9de2a-131">**GET**</span></span> | <span data-ttu-id="9de2a-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="9de2a-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="9de2a-133">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="9de2a-133">URI parameters</span></span>

<span data-ttu-id="9de2a-134">Gebruik de volgende padparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="9de2a-134">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="9de2a-135">Naam</span><span class="sxs-lookup"><span data-stu-id="9de2a-135">Name</span></span>           | <span data-ttu-id="9de2a-136">Type</span><span class="sxs-lookup"><span data-stu-id="9de2a-136">Type</span></span>   | <span data-ttu-id="9de2a-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="9de2a-137">Required</span></span> | <span data-ttu-id="9de2a-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9de2a-138">Description</span></span>                                           |
|----------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="9de2a-139">customer-id</span><span class="sxs-lookup"><span data-stu-id="9de2a-139">customer-id</span></span>    | <span data-ttu-id="9de2a-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9de2a-140">string</span></span> | <span data-ttu-id="9de2a-141">Ja</span><span class="sxs-lookup"><span data-stu-id="9de2a-141">Yes</span></span>      | <span data-ttu-id="9de2a-142">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="9de2a-142">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="9de2a-143">devicebatch-id</span><span class="sxs-lookup"><span data-stu-id="9de2a-143">devicebatch-id</span></span> | <span data-ttu-id="9de2a-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9de2a-144">string</span></span> | <span data-ttu-id="9de2a-145">Ja</span><span class="sxs-lookup"><span data-stu-id="9de2a-145">Yes</span></span>      | <span data-ttu-id="9de2a-146">Een tekenreeks-id die de apparaatbatch identificeert.</span><span class="sxs-lookup"><span data-stu-id="9de2a-146">A string identifier that identifies the device batch.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9de2a-147">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9de2a-147">Request headers</span></span>

<span data-ttu-id="9de2a-148">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="9de2a-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9de2a-149">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9de2a-149">Request body</span></span>

<span data-ttu-id="9de2a-150">Geen</span><span class="sxs-lookup"><span data-stu-id="9de2a-150">None</span></span>

### <a name="request-example"></a><span data-ttu-id="9de2a-151">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9de2a-151">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches/testbatch/devices HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="9de2a-152">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9de2a-152">REST response</span></span>

<span data-ttu-id="9de2a-153">Als dit lukt, bevat de antwoord-hoofdverzameling een verzameling [apparaatresources met pagina's.](device-deployment-resources.md#device)</span><span class="sxs-lookup"><span data-stu-id="9de2a-153">If successful, the response body contains a paged collection of [Device](device-deployment-resources.md#device) resources.</span></span> <span data-ttu-id="9de2a-154">De verzameling bevat 100 apparaten op een pagina.</span><span class="sxs-lookup"><span data-stu-id="9de2a-154">The collection contains 100 devices in a page.</span></span> <span data-ttu-id="9de2a-155">Als u de volgende pagina van 100 apparaten wilt ophalen, moet het continuationToken in de hoofdtekst van het antwoord worden opgenomen in de volgende aanvraag als een MS-ContinuationToken header.</span><span class="sxs-lookup"><span data-stu-id="9de2a-155">To retrieve the next page of 100 devices, the continuationToken in the response body must be included in the subsequent request as an MS-ContinuationToken header.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9de2a-156">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="9de2a-156">Response success and error codes</span></span>

<span data-ttu-id="9de2a-157">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="9de2a-157">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9de2a-158">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9de2a-158">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9de2a-159">Zie REST-foutcodes voor [Partner Center een volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="9de2a-159">For a full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9de2a-160">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9de2a-160">Response example</span></span>

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
