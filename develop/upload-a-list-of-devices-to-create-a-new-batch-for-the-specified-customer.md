---
title: Een lijst met apparaten uploaden om een nieuwe batch te maken voor de opgegeven klant
description: Een lijst met informatie over apparaten uploaden om een nieuwe batch te maken voor de opgegeven klant. Hiermee maakt u een apparaatbatch voor inschrijving in zero-touch-implementatie en koppelt u de apparaten en de apparaatbatch aan de opgegeven klant.
ms.date: 08/08/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 285af12034562262c99b2aa3b139e948b0fdd462
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529729"
---
# <a name="upload-a-list-of-devices-to-create-a-new-batch-for-the-specified-customer"></a><span data-ttu-id="04a11-104">Een lijst met apparaten uploaden om een nieuwe batch te maken voor de opgegeven klant</span><span class="sxs-lookup"><span data-stu-id="04a11-104">Upload a list of devices to create a new batch for the specified customer</span></span>

<span data-ttu-id="04a11-105">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="04a11-105">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="04a11-106">Een lijst met informatie over apparaten uploaden om een nieuwe batch te maken voor de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="04a11-106">How to upload a list of information about devices to create a new batch for the specified customer.</span></span> <span data-ttu-id="04a11-107">Hiermee maakt u een apparaatbatch voor inschrijving in zero-touch-implementatie en koppelt u de apparaten en de apparaatbatch aan de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="04a11-107">This creates a device batch for enrollment in zero-touch deployment, and associates the devices and the device batch with the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04a11-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="04a11-108">Prerequisites</span></span>

- <span data-ttu-id="04a11-109">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="04a11-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="04a11-110">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="04a11-110">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="04a11-111">Volg het [model voor beveiligde apps bij](enable-secure-app-model.md) het gebruik van App+User-verificatie met Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="04a11-111">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="04a11-112">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="04a11-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="04a11-113">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="04a11-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="04a11-114">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="04a11-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="04a11-115">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="04a11-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="04a11-116">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="04a11-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="04a11-117">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="04a11-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="04a11-118">De lijst met apparaatbronnen die de informatie over de afzonderlijke apparaten bevatten.</span><span class="sxs-lookup"><span data-stu-id="04a11-118">The list of device resources that provide the information about the individual devices.</span></span>

## <a name="c"></a><span data-ttu-id="04a11-119">C\#</span><span class="sxs-lookup"><span data-stu-id="04a11-119">C\#</span></span>

<span data-ttu-id="04a11-120">Een lijst met apparaten uploaden om een nieuwe apparaatbatch te maken:</span><span class="sxs-lookup"><span data-stu-id="04a11-120">To upload a list of devices to create a new device batch:</span></span>

1. <span data-ttu-id="04a11-121">Instantieer een nieuw [List/dotnet/api/system.collections.generic.list-1) van het type [**Apparaat**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) en vul de lijst met de apparaten.</span><span class="sxs-lookup"><span data-stu-id="04a11-121">Instantiate a new [List/dotnet/api/system.collections.generic.list-1) of type [**Device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) and populate the list with the devices.</span></span> <span data-ttu-id="04a11-122">De volgende combinaties van ingevulde eigenschappen zijn minimaal vereist voor het identificeren van elk apparaat:</span><span class="sxs-lookup"><span data-stu-id="04a11-122">The following combinations of populated properties are required at a minimum for identifying each device:</span></span>

   - <span data-ttu-id="04a11-123">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span><span class="sxs-lookup"><span data-stu-id="04a11-123">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span></span>
   - <span data-ttu-id="04a11-124">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="04a11-124">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>
   - <span data-ttu-id="04a11-125">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)  +  [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="04a11-125">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>
   - <span data-ttu-id="04a11-126">[**Alleen HardwareHash.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)</span><span class="sxs-lookup"><span data-stu-id="04a11-126">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) only.</span></span>
   - <span data-ttu-id="04a11-127">[**Alleen ProductKey.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)</span><span class="sxs-lookup"><span data-stu-id="04a11-127">[**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) only.</span></span>
   - <span data-ttu-id="04a11-128">[**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber)  +  [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername)  +  [**ModelName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span><span class="sxs-lookup"><span data-stu-id="04a11-128">[**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber) + [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername) + [**ModelName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span></span>

2. <span data-ttu-id="04a11-129">Instantieer een [**DeviceBatchCreationRequest-object**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest) en stel de eigenschap [**BatchId**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.batchid) in op een unieke naam van uw keuze en de eigenschap [**Devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) op de lijst met apparaten die u wilt uploaden.</span><span class="sxs-lookup"><span data-stu-id="04a11-129">Instantiate a [**DeviceBatchCreationRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest) object and set the [**BatchId**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.batchid) property to a unique name of your choosing, and the [**Devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) property to the list of devices to upload.</span></span>

3. <span data-ttu-id="04a11-130">Verwerken van de aanvraag voor het maken van een apparaatbatch door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="04a11-130">Process the device batch creation request by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the specified customer.</span></span>

4. <span data-ttu-id="04a11-131">Roep de [**methode DeviceBatches.Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) met de aanvraag voor het maken van de apparaatbatches om de batch te maken.</span><span class="sxs-lookup"><span data-stu-id="04a11-131">Call the [**DeviceBatches.Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) method with the device batch creation request to create the batch.</span></span>

```csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;

List<Device> devicesToBeUploaded = new List<Device>
{
    new Device
    {
        HardwareHash = "DummyHash123",
        ProductKey = "00329-00000-0003-AA606",
        SerialNumber = "1R9-ZNP67"
    }
};

DeviceBatchCreationRequest
    newDeviceBatch = new DeviceBatchCreationRequest
{
    BatchId = "SDKTestDeviceBatch",
    Devices = devicesToBeUploaded
};

var trackingLocation =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.Create(newDeviceBatch);
```

<span data-ttu-id="04a11-132">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="04a11-132">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="04a11-133">**Project:** Partnercentrum-SDK Klasse **Samples:** CreateDeviceBatch.cs</span><span class="sxs-lookup"><span data-stu-id="04a11-133">**Project**: Partner Center SDK Samples **Class**: CreateDeviceBatch.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="04a11-134">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="04a11-134">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="04a11-135">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="04a11-135">Request syntax</span></span>

| <span data-ttu-id="04a11-136">Methode</span><span class="sxs-lookup"><span data-stu-id="04a11-136">Method</span></span>   | <span data-ttu-id="04a11-137">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="04a11-137">Request URI</span></span>                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="04a11-138">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="04a11-138">**POST**</span></span> | <span data-ttu-id="04a11-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="04a11-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="04a11-140">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="04a11-140">URI parameter</span></span>

<span data-ttu-id="04a11-141">Gebruik de volgende padparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="04a11-141">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="04a11-142">Naam</span><span class="sxs-lookup"><span data-stu-id="04a11-142">Name</span></span>        | <span data-ttu-id="04a11-143">Type</span><span class="sxs-lookup"><span data-stu-id="04a11-143">Type</span></span>   | <span data-ttu-id="04a11-144">Vereist</span><span class="sxs-lookup"><span data-stu-id="04a11-144">Required</span></span> | <span data-ttu-id="04a11-145">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="04a11-145">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="04a11-146">customer-id</span><span class="sxs-lookup"><span data-stu-id="04a11-146">customer-id</span></span> | <span data-ttu-id="04a11-147">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="04a11-147">string</span></span> | <span data-ttu-id="04a11-148">Ja</span><span class="sxs-lookup"><span data-stu-id="04a11-148">Yes</span></span>      | <span data-ttu-id="04a11-149">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="04a11-149">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="04a11-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="04a11-150">Request headers</span></span>

<span data-ttu-id="04a11-151">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="04a11-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="04a11-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="04a11-152">Request body</span></span>

<span data-ttu-id="04a11-153">De aanvraag moet een [DeviceBatchCreationRequest-resource](device-deployment-resources.md#devicebatchcreationrequest) bevatten.</span><span class="sxs-lookup"><span data-stu-id="04a11-153">The request body must contain a [DeviceBatchCreationRequest](device-deployment-resources.md#devicebatchcreationrequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="04a11-154">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="04a11-154">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/deviceBatches HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c245d5f2-1de3-4ae0-9e42-95e38e3cb8ff
MS-CorrelationId: e3f26e6a-044f-4371-ad52-0d91ce4200be
X-Locale: en-US
MS-PartnerCenter-Application: Partner Center .NET SDK Samples
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 340
Expect: 100-continue
Connection: Keep-Alive
{
    "BatchId": "SDKTestDeviceBatch",
    "Devices": [{
            "Id": null,
            "SerialNumber": "1R9-ZNP67",
            "ProductKey": "00329-00000-0003-AA606",
            "HardwareHash": "DummyHash123",
            "Policies": null,
            "CreatedBy": null,
            "UploadedDate": "0001-01-01T00:00:00",
            "AllowedOperations": null,
            "Attributes": {
                "ObjectType": "Device"
            }
        }
    ],
    "Attributes": {
        "ObjectType": "DeviceBatchCreationRequest"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="04a11-155">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="04a11-155">REST response</span></span>

<span data-ttu-id="04a11-156">Als dit lukt, bevat het antwoord een **Location-header** met een URI die kan worden gebruikt om de uploadstatus van het apparaat op te halen.</span><span class="sxs-lookup"><span data-stu-id="04a11-156">If successful, the response contains a **Location** header that has a URI that can be used to retrieve device upload status.</span></span> <span data-ttu-id="04a11-157">Sla deze URI op voor gebruik met andere gerelateerde REST API's.</span><span class="sxs-lookup"><span data-stu-id="04a11-157">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="04a11-158">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="04a11-158">Response success and error codes</span></span>

<span data-ttu-id="04a11-159">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="04a11-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="04a11-160">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="04a11-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="04a11-161">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="04a11-161">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="04a11-162">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="04a11-162">Response example</span></span>

```http
HTTP/1.1 202 Accepted
Content-Length: 0
Location: /customers/c7f3c849-129f-4b85-a96d-4f8e88b315a3/batchJobStatus/beba2053-5401-46ff-9223-7e841ed78fbf
MS-CorrelationId: 772871a9-399b-4f3b-b8c7-38f550e4f22a
MS-RequestId: cb82f7d6-f0d9-44d4-82f9-f6eee6e68390
MS-CV: iqOqN0FnaE2y0HcD.0
MS-ServerId: 030020525
Date: Thu, 28 Sep 2017 20:35:35 GMT
```
