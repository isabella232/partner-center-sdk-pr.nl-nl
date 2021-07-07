---
title: Een lijst met apparaten uploaden naar een bestaande batch voor de opgegeven klant
description: Een lijst met informatie over apparaten uploaden naar een bestaande batch voor de opgegeven klant. Hiermee koppelt u de apparaten aan een apparaatbatch die al is gemaakt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 3fa9cff39113130c54cecfaef1f8ca28e0ac5adf
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530307"
---
# <a name="upload-a-list-of-devices-to-an-existing-batch-for-the-specified-customer"></a><span data-ttu-id="8cd38-104">Een lijst met apparaten uploaden naar een bestaande batch voor de opgegeven klant</span><span class="sxs-lookup"><span data-stu-id="8cd38-104">Upload a list of devices to an existing batch for the specified customer</span></span>

<span data-ttu-id="8cd38-105">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="8cd38-105">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="8cd38-106">Een lijst met informatie over apparaten uploaden naar een bestaande batch voor de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="8cd38-106">How to upload a list of information about devices to an existing batch for the specified customer.</span></span> <span data-ttu-id="8cd38-107">Hiermee koppelt u de apparaten aan een apparaatbatch die al is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="8cd38-107">This associates the devices with a device batch already created.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8cd38-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8cd38-108">Prerequisites</span></span>

- <span data-ttu-id="8cd38-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8cd38-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8cd38-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="8cd38-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="8cd38-111">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8cd38-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8cd38-112">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="8cd38-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8cd38-113">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="8cd38-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8cd38-114">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="8cd38-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8cd38-115">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="8cd38-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8cd38-116">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8cd38-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="8cd38-117">De batch-id van het apparaat.</span><span class="sxs-lookup"><span data-stu-id="8cd38-117">The device batch identifier.</span></span>

- <span data-ttu-id="8cd38-118">De lijst met apparaatbronnen die de informatie over de afzonderlijke apparaten bevatten.</span><span class="sxs-lookup"><span data-stu-id="8cd38-118">The list of device resources that provide the information about the individual devices.</span></span>

## <a name="c"></a><span data-ttu-id="8cd38-119">C\#</span><span class="sxs-lookup"><span data-stu-id="8cd38-119">C\#</span></span>

<span data-ttu-id="8cd38-120">Als u een lijst met apparaten wilt uploaden naar een bestaande apparaatbatch, instantieer dan eerst een nieuw [List/dotnet/api/system.collections.generic.list-1) van het type [**Apparaat**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) en vul de lijst met de apparaten in.</span><span class="sxs-lookup"><span data-stu-id="8cd38-120">To upload a list of devices to an existing device batch, first, instantiate a new [List/dotnet/api/system.collections.generic.list-1) of type [**Device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) and populate the list with the devices.</span></span> <span data-ttu-id="8cd38-121">De volgende combinaties van ingevulde eigenschappen zijn minimaal vereist voor het identificeren van elk apparaat:</span><span class="sxs-lookup"><span data-stu-id="8cd38-121">The following combinations of populated properties are required at a minimum for identifying each device:</span></span>

- <span data-ttu-id="8cd38-122">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span><span class="sxs-lookup"><span data-stu-id="8cd38-122">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span></span>

- <span data-ttu-id="8cd38-123">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="8cd38-123">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>

- <span data-ttu-id="8cd38-124">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)  +  [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="8cd38-124">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>

- <span data-ttu-id="8cd38-125">[**Alleen HardwareHash.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)</span><span class="sxs-lookup"><span data-stu-id="8cd38-125">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) only.</span></span>

- <span data-ttu-id="8cd38-126">[**Alleen ProductKey.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)</span><span class="sxs-lookup"><span data-stu-id="8cd38-126">[**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) only.</span></span>

- <span data-ttu-id="8cd38-127">[**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber)  +  [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername)  +  [**ModelName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span><span class="sxs-lookup"><span data-stu-id="8cd38-127">[**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber) + [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername) + [**ModelName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span></span>

<span data-ttu-id="8cd38-128">Roep vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="8cd38-128">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="8cd38-129">Roep vervolgens de [**methode DeviceBatches.ById aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) met de batch-id van het apparaat om een interface op te halen voor bewerkingen voor de opgegeven batch.</span><span class="sxs-lookup"><span data-stu-id="8cd38-129">Next, call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method with the device batch identifier to get an interface to operations for the specified batch.</span></span> <span data-ttu-id="8cd38-130">Roep ten slotte de [**methode Devices.Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.createasync) aan met de lijst met apparaten om de apparaten toe te voegen aan de apparaatbatch.</span><span class="sxs-lookup"><span data-stu-id="8cd38-130">Finally, call the [**Devices.Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.createasync) method with the list of devices to add the devices to the device batch.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;

List<Device> devicesToBeUploaded = new List<Device>
{
    new Device
    {
        HardwareHash = "DummyHash1234",
        ProductKey = "00329-00000-0003-AA606",
        SerialNumber = "2R9-ZNP67"
    },

    new Device
    {
        HardwareHash = "DummyHash12345",
        ProductKey = "00329-00000-0003-AA606",
        SerialNumber = "2R9-ZNP67"
    }
};

var trackingLocation =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.Create(devicesToBeUploaded);
```

<span data-ttu-id="8cd38-131">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="8cd38-131">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="8cd38-132">**Project**: Partnercentrum-SDK Samples **Class**: CreateDevices.cs</span><span class="sxs-lookup"><span data-stu-id="8cd38-132">**Project**: Partner Center SDK Samples **Class**: CreateDevices.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="8cd38-133">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="8cd38-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8cd38-134">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="8cd38-134">Request syntax</span></span>

| <span data-ttu-id="8cd38-135">Methode</span><span class="sxs-lookup"><span data-stu-id="8cd38-135">Method</span></span>   | <span data-ttu-id="8cd38-136">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="8cd38-136">Request URI</span></span>                                                                                                            |
|----------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8cd38-137">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="8cd38-137">**POST**</span></span> | <span data-ttu-id="8cd38-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8cd38-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="8cd38-139">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="8cd38-139">URI parameter</span></span>

<span data-ttu-id="8cd38-140">Gebruik het volgende pad en de queryparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="8cd38-140">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="8cd38-141">Naam</span><span class="sxs-lookup"><span data-stu-id="8cd38-141">Name</span></span>           | <span data-ttu-id="8cd38-142">Type</span><span class="sxs-lookup"><span data-stu-id="8cd38-142">Type</span></span>   | <span data-ttu-id="8cd38-143">Vereist</span><span class="sxs-lookup"><span data-stu-id="8cd38-143">Required</span></span> | <span data-ttu-id="8cd38-144">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8cd38-144">Description</span></span>                                           |
|----------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="8cd38-145">customer-id</span><span class="sxs-lookup"><span data-stu-id="8cd38-145">customer-id</span></span>    | <span data-ttu-id="8cd38-146">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="8cd38-146">string</span></span> | <span data-ttu-id="8cd38-147">Ja</span><span class="sxs-lookup"><span data-stu-id="8cd38-147">Yes</span></span>      | <span data-ttu-id="8cd38-148">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="8cd38-148">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="8cd38-149">devicebatch-id</span><span class="sxs-lookup"><span data-stu-id="8cd38-149">devicebatch-id</span></span> | <span data-ttu-id="8cd38-150">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="8cd38-150">string</span></span> | <span data-ttu-id="8cd38-151">Ja</span><span class="sxs-lookup"><span data-stu-id="8cd38-151">Yes</span></span>      | <span data-ttu-id="8cd38-152">Een tekenreeks-id die de apparaatbatch identificeert.</span><span class="sxs-lookup"><span data-stu-id="8cd38-152">A string identifier that identifies the device batch.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8cd38-153">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="8cd38-153">Request headers</span></span>

<span data-ttu-id="8cd38-154">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="8cd38-154">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8cd38-155">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="8cd38-155">Request body</span></span>

<span data-ttu-id="8cd38-156">De aanvraag body moet een matrix van [apparaatobjecten](device-deployment-resources.md#device) bevatten.</span><span class="sxs-lookup"><span data-stu-id="8cd38-156">The request body must contain an array of [Device](device-deployment-resources.md#device) objects.</span></span> <span data-ttu-id="8cd38-157">De volgende combinaties van velden voor het identificeren van een apparaat worden geaccepteerd:</span><span class="sxs-lookup"><span data-stu-id="8cd38-157">The following combinations of fields for identifying a device are accepted:</span></span>

- <span data-ttu-id="8cd38-158">hardwareHash + productKey.</span><span class="sxs-lookup"><span data-stu-id="8cd38-158">hardwareHash + productKey.</span></span>
- <span data-ttu-id="8cd38-159">hardwareHash + serialNumber.</span><span class="sxs-lookup"><span data-stu-id="8cd38-159">hardwareHash + serialNumber.</span></span>
- <span data-ttu-id="8cd38-160">hardwareHash + productKey + serialNumber.</span><span class="sxs-lookup"><span data-stu-id="8cd38-160">hardwareHash + productKey + serialNumber.</span></span>
- <span data-ttu-id="8cd38-161">alleen hardwareHash.</span><span class="sxs-lookup"><span data-stu-id="8cd38-161">hardwareHash only.</span></span>
- <span data-ttu-id="8cd38-162">alleen productKey.</span><span class="sxs-lookup"><span data-stu-id="8cd38-162">productKey only.</span></span>
- <span data-ttu-id="8cd38-163">serialNumber + oemManufacturerName + modelName.</span><span class="sxs-lookup"><span data-stu-id="8cd38-163">serialNumber + oemManufacturerName + modelName.</span></span>

### <a name="request-example"></a><span data-ttu-id="8cd38-164">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="8cd38-164">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/deviceBatches/Test/devices HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e286d69b-7f5f-4098-8999-21d3b54e4e47
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 482
Expect: 100-continue

[{
        "Id": null,
        "SerialNumber": "2R9-ZNP67",
        "ProductKey": "00329-00000-0003-AA606",
        "HardwareHash": "DummyHash1234",
        "Policies": null,
        "CreatedBy": null,
        "UploadedDate": "0001-01-01T00:00:00",
        "AllowedOperations": null,
        "Attributes": {
            "ObjectType": "Device"
        }
    }, {
        "Id": null,
        "SerialNumber": "2R9-ZNP67",
        "ProductKey": "00329-00000-0003-AA606",
        "HardwareHash": "DummyHash12345",
        "Policies": null,
        "CreatedBy": null,
        "UploadedDate": "0001-01-01T00:00:00",
        "AllowedOperations": null,
        "Attributes": {
            "ObjectType": "Device"
        }
    }
]
```

## <a name="rest-response"></a><span data-ttu-id="8cd38-165">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="8cd38-165">REST response</span></span>

<span data-ttu-id="8cd38-166">Als dit lukt, bevat het antwoord een **Location-header** met een URI die kan worden gebruikt om de uploadstatus van het apparaat op te halen.</span><span class="sxs-lookup"><span data-stu-id="8cd38-166">If successful, the response contains a **Location** header that has a URI that can be used to retrieve device upload status.</span></span> <span data-ttu-id="8cd38-167">Sla deze URI op voor gebruik met andere gerelateerde REST API's.</span><span class="sxs-lookup"><span data-stu-id="8cd38-167">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8cd38-168">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="8cd38-168">Response success and error codes</span></span>

<span data-ttu-id="8cd38-169">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="8cd38-169">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8cd38-170">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="8cd38-170">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8cd38-171">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="8cd38-171">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8cd38-172">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="8cd38-172">Response example</span></span>

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/batchJobStatus/16c00110-e79a-433d-aa28-f69dd60df671
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: e286d69b-7f5f-4098-8999-21d3b54e4e47
MS-CV: OBkGN9pSN0a5xvua.0
MS-ServerId: 101112012
Date: Thu, 28 Sep 2017 20:08:46 GMT
```
