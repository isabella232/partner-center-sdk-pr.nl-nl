---
title: Een lijst met apparaten uploaden om een nieuwe batch te maken voor de opgegeven klant
description: Een lijst met informatie over apparaten uploaden om een nieuwe batch voor de opgegeven klant te maken. Hiermee maakt u een apparaat batch voor inschrijving in een Zero-touch-implementatie, en koppelt u de apparaten en de apparaat batch aan de opgegeven klant.
ms.date: 08/08/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0b48971b862418136c42e78ae973a5aea27404a1
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767507"
---
# <a name="upload-a-list-of-devices-to-create-a-new-batch-for-the-specified-customer"></a><span data-ttu-id="e87ac-104">Een lijst met apparaten uploaden om een nieuwe batch te maken voor de opgegeven klant</span><span class="sxs-lookup"><span data-stu-id="e87ac-104">Upload a list of devices to create a new batch for the specified customer</span></span>

<span data-ttu-id="e87ac-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="e87ac-105">**Applies to:**</span></span>

- <span data-ttu-id="e87ac-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e87ac-106">Partner Center</span></span>
- <span data-ttu-id="e87ac-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="e87ac-107">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="e87ac-108">Een lijst met informatie over apparaten uploaden om een nieuwe batch voor de opgegeven klant te maken.</span><span class="sxs-lookup"><span data-stu-id="e87ac-108">How to upload a list of information about devices to create a new batch for the specified customer.</span></span> <span data-ttu-id="e87ac-109">Hiermee maakt u een apparaat batch voor inschrijving in een Zero-touch-implementatie, en koppelt u de apparaten en de apparaat batch aan de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="e87ac-109">This creates a device batch for enrollment in zero-touch deployment, and associates the devices and the device batch with the specified customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e87ac-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e87ac-110">Prerequisites</span></span>

- <span data-ttu-id="e87ac-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e87ac-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e87ac-112">Dit scenario ondersteunt verificatie met app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="e87ac-112">This scenario supports authentication with App+User credentials.</span></span> <span data-ttu-id="e87ac-113">Volg het [model voor beveiligde apps](enable-secure-app-model.md) wanneer u app + gebruikers authenticatie met partner Center api's gebruikt.</span><span class="sxs-lookup"><span data-stu-id="e87ac-113">Follow the [secure app model](enable-secure-app-model.md) when using App+User authentication with Partner Center APIs.</span></span>

- <span data-ttu-id="e87ac-114">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e87ac-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e87ac-115">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="e87ac-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e87ac-116">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="e87ac-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e87ac-117">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="e87ac-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e87ac-118">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="e87ac-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e87ac-119">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e87ac-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="e87ac-120">De lijst met apparaten die de informatie over de afzonderlijke apparaten bieden.</span><span class="sxs-lookup"><span data-stu-id="e87ac-120">The list of device resources that provide the information about the individual devices.</span></span>

## <a name="c"></a><span data-ttu-id="e87ac-121">C\#</span><span class="sxs-lookup"><span data-stu-id="e87ac-121">C\#</span></span>

<span data-ttu-id="e87ac-122">Een lijst met apparaten uploaden om een nieuwe apparaat batch te maken:</span><span class="sxs-lookup"><span data-stu-id="e87ac-122">To upload a list of devices to create a new device batch:</span></span>

1. <span data-ttu-id="e87ac-123">Exemplaar een nieuwe [list/DotNet/API/System. Collections. generic. List -1) van het type [**apparaat**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) en vul de lijst in met de apparaten.</span><span class="sxs-lookup"><span data-stu-id="e87ac-123">Instantiate a new [List/dotnet/api/system.collections.generic.list-1) of type [**Device**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) and populate the list with the devices.</span></span> <span data-ttu-id="e87ac-124">De volgende combi Naties van gevulde eigenschappen zijn vereist ten minste voor het identificeren van elk apparaat:</span><span class="sxs-lookup"><span data-stu-id="e87ac-124">The following combinations of populated properties are required at a minimum for identifying each device:</span></span>

   - <span data-ttu-id="e87ac-125">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span><span class="sxs-lookup"><span data-stu-id="e87ac-125">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).</span></span>
   - <span data-ttu-id="e87ac-126">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**Serialnumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="e87ac-126">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>
   - <span data-ttu-id="e87ac-127">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)  +  [**Serialnumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span><span class="sxs-lookup"><span data-stu-id="e87ac-127">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) + [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) + [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).</span></span>
   - <span data-ttu-id="e87ac-128">Alleen [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) .</span><span class="sxs-lookup"><span data-stu-id="e87ac-128">[**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash) only.</span></span>
   - <span data-ttu-id="e87ac-129">Alleen [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) .</span><span class="sxs-lookup"><span data-stu-id="e87ac-129">[**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey) only.</span></span>
   - <span data-ttu-id="e87ac-130">[**Serialnumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber)  +  [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername)  +  [**Modelnaam**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span><span class="sxs-lookup"><span data-stu-id="e87ac-130">[**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber) + [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername) + [**ModelName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).</span></span>

2. <span data-ttu-id="e87ac-131">Maak een exemplaar van een [**DeviceBatchCreationRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest) -object en stel de eigenschap [**BatchId**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.batchid) in op een unieke naam van uw keuze en de eigenschap [**devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) voor de lijst met apparaten die moeten worden geüpload.</span><span class="sxs-lookup"><span data-stu-id="e87ac-131">Instantiate a [**DeviceBatchCreationRequest**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest) object and set the [**BatchId**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.batchid) property to a unique name of your choosing, and the [**Devices**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.devicebatchcreationrequest.devices) property to the list of devices to upload.</span></span>

3. <span data-ttu-id="e87ac-132">De aanvraag voor het maken van een apparaat batch verwerken door de [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="e87ac-132">Process the device batch creation request by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to retrieve an interface to operations on the specified customer.</span></span>

4. <span data-ttu-id="e87ac-133">Roep de [**DeviceBatches. Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) -of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) -methode aan met de aanvraag voor het maken van een batch voor het aanmaken van de batch.</span><span class="sxs-lookup"><span data-stu-id="e87ac-133">Call the [**DeviceBatches.Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection) method with the device batch creation request to create the batch.</span></span>

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

<span data-ttu-id="e87ac-134">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e87ac-134">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e87ac-135">**Project**: Partner Center SDK-voor beelden **klasse**: CreateDeviceBatch.cs</span><span class="sxs-lookup"><span data-stu-id="e87ac-135">**Project**: Partner Center SDK Samples **Class**: CreateDeviceBatch.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e87ac-136">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e87ac-136">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e87ac-137">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e87ac-137">Request syntax</span></span>

| <span data-ttu-id="e87ac-138">Methode</span><span class="sxs-lookup"><span data-stu-id="e87ac-138">Method</span></span>   | <span data-ttu-id="e87ac-139">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e87ac-139">Request URI</span></span>                                                                                   |
|----------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="e87ac-140">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="e87ac-140">**POST**</span></span> | <span data-ttu-id="e87ac-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/deviceBatches http/1.1</span><span class="sxs-lookup"><span data-stu-id="e87ac-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="e87ac-142">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="e87ac-142">URI parameter</span></span>

<span data-ttu-id="e87ac-143">Gebruik de volgende Path-para meters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="e87ac-143">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="e87ac-144">Naam</span><span class="sxs-lookup"><span data-stu-id="e87ac-144">Name</span></span>        | <span data-ttu-id="e87ac-145">Type</span><span class="sxs-lookup"><span data-stu-id="e87ac-145">Type</span></span>   | <span data-ttu-id="e87ac-146">Vereist</span><span class="sxs-lookup"><span data-stu-id="e87ac-146">Required</span></span> | <span data-ttu-id="e87ac-147">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e87ac-147">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="e87ac-148">klant-id</span><span class="sxs-lookup"><span data-stu-id="e87ac-148">customer-id</span></span> | <span data-ttu-id="e87ac-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e87ac-149">string</span></span> | <span data-ttu-id="e87ac-150">Yes</span><span class="sxs-lookup"><span data-stu-id="e87ac-150">Yes</span></span>      | <span data-ttu-id="e87ac-151">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="e87ac-151">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e87ac-152">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e87ac-152">Request headers</span></span>

<span data-ttu-id="e87ac-153">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e87ac-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e87ac-154">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e87ac-154">Request body</span></span>

<span data-ttu-id="e87ac-155">De aanvraag tekst moet een [DeviceBatchCreationRequest](device-deployment-resources.md#devicebatchcreationrequest) -resource bevatten.</span><span class="sxs-lookup"><span data-stu-id="e87ac-155">The request body must contain a [DeviceBatchCreationRequest](device-deployment-resources.md#devicebatchcreationrequest) resource.</span></span>

### <a name="request-example"></a><span data-ttu-id="e87ac-156">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e87ac-156">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e87ac-157">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e87ac-157">REST response</span></span>

<span data-ttu-id="e87ac-158">Als dit is gelukt, bevat het antwoord een **locatie** header met een URI die kan worden gebruikt om de upload status van het apparaat op te halen.</span><span class="sxs-lookup"><span data-stu-id="e87ac-158">If successful, the response contains a **Location** header that has a URI that can be used to retrieve device upload status.</span></span> <span data-ttu-id="e87ac-159">Sla deze URI op voor gebruik met andere verwante REST Api's.</span><span class="sxs-lookup"><span data-stu-id="e87ac-159">Save this URI for use with other related REST APIs.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e87ac-160">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="e87ac-160">Response success and error codes</span></span>

<span data-ttu-id="e87ac-161">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e87ac-161">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e87ac-162">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e87ac-162">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e87ac-163">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="e87ac-163">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

#### <a name="response-example"></a><span data-ttu-id="e87ac-164">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e87ac-164">Response example</span></span>

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
