---
title: Een lijst met apparaten uploaden naar een bestaande batch voor de opgegeven klant
description: Een lijst met informatie over apparaten uploaden naar een bestaande batch voor de opgegeven klant. Hiermee worden de apparaten gekoppeld aan een apparaat batch die al is gemaakt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d01ac1a42c50416487167070be9d104562300baf
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767509"
---
# <a name="upload-a-list-of-devices-to-an-existing-batch-for-the-specified-customer"></a><span data-ttu-id="cb64b-104">Een lijst met apparaten uploaden naar een bestaande batch voor de opgegeven klant</span><span class="sxs-lookup"><span data-stu-id="cb64b-104">Upload a list of devices to an existing batch for the specified customer</span></span>

<span data-ttu-id="cb64b-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="cb64b-105">**Applies To**</span></span>

- <span data-ttu-id="cb64b-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="cb64b-106">Partner Center</span></span>
- <span data-ttu-id="cb64b-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="cb64b-107">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="cb64b-108">Een lijst met informatie over apparaten uploaden naar een bestaande batch voor de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="cb64b-108">How to upload a list of information about devices to an existing batch for the specified customer.</span></span> <span data-ttu-id="cb64b-109">Hiermee worden de apparaten gekoppeld aan een apparaat batch die al is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="cb64b-109">This associates the devices with a device batch already created.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cb64b-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="cb64b-110">Prerequisites</span></span>

- <span data-ttu-id="cb64b-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="cb64b-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="cb64b-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="cb64b-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="cb64b-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cb64b-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="cb64b-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="cb64b-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="cb64b-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="cb64b-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="cb64b-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="cb64b-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="cb64b-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="cb64b-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="cb64b-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="cb64b-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="cb64b-119">De batch-id van het apparaat.</span><span class="sxs-lookup"><span data-stu-id="cb64b-119">The device batch identifier.</span></span>

- <span data-ttu-id="cb64b-120">De lijst met apparaten die de informatie over de afzonderlijke apparaten bieden.</span><span class="sxs-lookup"><span data-stu-id="cb64b-120">The list of device resources that provide the information about the individual devices.</span></span>

## <a name="c"></a><span data-ttu-id="cb64b-121">C\#</span><span class="sxs-lookup"><span data-stu-id="cb64b-121">C\#</span></span>

<span data-ttu-id="cb64b-122">Als u een lijst met apparaten wilt uploaden naar een bestaande apparaat batch, maakt u eerst een nieuwe [list/DotNet/API/System. Collections. generic. List -1) van het type [**apparaat**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) en vult u de lijst met de apparaten in.</span><span class="sxs-lookup"><span data-stu-id="cb64b-122">To upload a list of devices to an existing device batch, first, instantiate a new [List/dotnet/api/system.collections.generic.list-1) of type [**Device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) and populate the list with the devices.</span></span> <span data-ttu-id="cb64b-123">De volgende combi Naties van gevulde eigenschappen zijn vereist ten minste voor het identificeren van elk apparaat:</span><span class="sxs-lookup"><span data-stu-id="cb64b-123">The following combinations of populated properties are required at a minimum for identifying each device:</span></span>

- <span data-ttu-id="cb64b-124">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span><span class="sxs-lookup"><span data-stu-id="cb64b-124">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span></span>

- <span data-ttu-id="cb64b-125">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**Serialnumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="cb64b-125">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>

- <span data-ttu-id="cb64b-126">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)  +  [**Serialnumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="cb64b-126">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>

- <span data-ttu-id="cb64b-127">Alleen [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) .</span><span class="sxs-lookup"><span data-stu-id="cb64b-127">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) only.</span></span>

- <span data-ttu-id="cb64b-128">Alleen [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) .</span><span class="sxs-lookup"><span data-stu-id="cb64b-128">[**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) only.</span></span>

- <span data-ttu-id="cb64b-129">[**Serialnumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber)  +  [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername)  +  [**Modelnaam**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span><span class="sxs-lookup"><span data-stu-id="cb64b-129">[**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber) + [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername) + [**ModelName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span></span>

<span data-ttu-id="cb64b-130">Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="cb64b-130">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="cb64b-131">Vervolgens roept u de methode [**DeviceBatches. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) aan met de batch-id van het apparaat om een interface te verkrijgen voor bewerkingen voor de opgegeven batch.</span><span class="sxs-lookup"><span data-stu-id="cb64b-131">Next, call the [**DeviceBatches.ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) method with the device batch identifier to get an interface to operations for the specified batch.</span></span> <span data-ttu-id="cb64b-132">Roep ten slotte de methode [**apparaten. Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.createasync) aan met de lijst met apparaten om de apparaten toe te voegen aan de apparaat batch.</span><span class="sxs-lookup"><span data-stu-id="cb64b-132">Finally, call the [**Devices.Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.createasync) method with the list of devices to add the devices to the device batch.</span></span>

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

<span data-ttu-id="cb64b-133">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="cb64b-133">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="cb64b-134">**Project**: Partner Center SDK-voor beelden **klasse**: CreateDevices.cs</span><span class="sxs-lookup"><span data-stu-id="cb64b-134">**Project**: Partner Center SDK Samples **Class**: CreateDevices.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="cb64b-135">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="cb64b-135">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="cb64b-136">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cb64b-136">Request syntax</span></span>

| <span data-ttu-id="cb64b-137">Methode</span><span class="sxs-lookup"><span data-stu-id="cb64b-137">Method</span></span>   | <span data-ttu-id="cb64b-138">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="cb64b-138">Request URI</span></span>                                                                                                            |
|----------|------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="cb64b-139">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="cb64b-139">**POST**</span></span> | <span data-ttu-id="cb64b-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/deviceBatches/{devicebatch-ID}/devices http/1.1</span><span class="sxs-lookup"><span data-stu-id="cb64b-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="cb64b-141">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="cb64b-141">URI parameter</span></span>

<span data-ttu-id="cb64b-142">Gebruik de volgende pad-en query parameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="cb64b-142">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="cb64b-143">Naam</span><span class="sxs-lookup"><span data-stu-id="cb64b-143">Name</span></span>           | <span data-ttu-id="cb64b-144">Type</span><span class="sxs-lookup"><span data-stu-id="cb64b-144">Type</span></span>   | <span data-ttu-id="cb64b-145">Vereist</span><span class="sxs-lookup"><span data-stu-id="cb64b-145">Required</span></span> | <span data-ttu-id="cb64b-146">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="cb64b-146">Description</span></span>                                           |
|----------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="cb64b-147">klant-id</span><span class="sxs-lookup"><span data-stu-id="cb64b-147">customer-id</span></span>    | <span data-ttu-id="cb64b-148">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="cb64b-148">string</span></span> | <span data-ttu-id="cb64b-149">Yes</span><span class="sxs-lookup"><span data-stu-id="cb64b-149">Yes</span></span>      | <span data-ttu-id="cb64b-150">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="cb64b-150">A GUID-formatted string that identifies the customer.</span></span> |
| <span data-ttu-id="cb64b-151">devicebatch-id</span><span class="sxs-lookup"><span data-stu-id="cb64b-151">devicebatch-id</span></span> | <span data-ttu-id="cb64b-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="cb64b-152">string</span></span> | <span data-ttu-id="cb64b-153">Yes</span><span class="sxs-lookup"><span data-stu-id="cb64b-153">Yes</span></span>      | <span data-ttu-id="cb64b-154">Een teken reeks-id waarmee de apparaat-batch wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="cb64b-154">A string identifier that identifies the device batch.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="cb64b-155">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="cb64b-155">Request headers</span></span>

<span data-ttu-id="cb64b-156">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="cb64b-156">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="cb64b-157">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="cb64b-157">Request body</span></span>

<span data-ttu-id="cb64b-158">De aanvraag tekst moet een matrix van [apparaatobject](device-deployment-resources.md#device) bevatten.</span><span class="sxs-lookup"><span data-stu-id="cb64b-158">The request body must contain an array of [Device](device-deployment-resources.md#device) objects.</span></span> <span data-ttu-id="cb64b-159">De volgende combi Naties van velden voor het identificeren van een apparaat worden geaccepteerd:</span><span class="sxs-lookup"><span data-stu-id="cb64b-159">The following combinations of fields for identifying a device are accepted:</span></span>

- <span data-ttu-id="cb64b-160">hardwareHash + productKey.</span><span class="sxs-lookup"><span data-stu-id="cb64b-160">hardwareHash + productKey.</span></span>
- <span data-ttu-id="cb64b-161">hardwareHash + serialNumber.</span><span class="sxs-lookup"><span data-stu-id="cb64b-161">hardwareHash + serialNumber.</span></span>
- <span data-ttu-id="cb64b-162">hardwareHash + productKey + serialNumber.</span><span class="sxs-lookup"><span data-stu-id="cb64b-162">hardwareHash + productKey + serialNumber.</span></span>
- <span data-ttu-id="cb64b-163">alleen hardwareHash.</span><span class="sxs-lookup"><span data-stu-id="cb64b-163">hardwareHash only.</span></span>
- <span data-ttu-id="cb64b-164">alleen productKey.</span><span class="sxs-lookup"><span data-stu-id="cb64b-164">productKey only.</span></span>
- <span data-ttu-id="cb64b-165">serialNumber + oemManufacturerName + modelnaam.</span><span class="sxs-lookup"><span data-stu-id="cb64b-165">serialNumber + oemManufacturerName + modelName.</span></span>

### <a name="request-example"></a><span data-ttu-id="cb64b-166">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="cb64b-166">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="cb64b-167">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="cb64b-167">REST response</span></span>

<span data-ttu-id="cb64b-168">Als dit is gelukt, bevat het antwoord een **locatie** header met een URI die kan worden gebruikt om de upload status van het apparaat op te halen.</span><span class="sxs-lookup"><span data-stu-id="cb64b-168">If successful, the response contains a **Location** header that has a URI that can be used to retrieve device upload status.</span></span> <span data-ttu-id="cb64b-169">Sla deze URI op voor gebruik met andere verwante REST Api's.</span><span class="sxs-lookup"><span data-stu-id="cb64b-169">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="cb64b-170">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="cb64b-170">Response success and error codes</span></span>

<span data-ttu-id="cb64b-171">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="cb64b-171">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="cb64b-172">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="cb64b-172">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="cb64b-173">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="cb64b-173">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="cb64b-174">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="cb64b-174">Response example</span></span>

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
