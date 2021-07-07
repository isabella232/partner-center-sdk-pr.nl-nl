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
# <a name="upload-a-list-of-devices-to-an-existing-batch-for-the-specified-customer"></a>Een lijst met apparaten uploaden naar een bestaande batch voor de opgegeven klant

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland

Een lijst met informatie over apparaten uploaden naar een bestaande batch voor de opgegeven klant. Hiermee koppelt u de apparaten aan een apparaatbatch die al is gemaakt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- De batch-id van het apparaat.

- De lijst met apparaatbronnen die de informatie over de afzonderlijke apparaten bevatten.

## <a name="c"></a>C\#

Als u een lijst met apparaten wilt uploaden naar een bestaande apparaatbatch, instantieer dan eerst een nieuw [List/dotnet/api/system.collections.generic.list-1) van het type [**Apparaat**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device) en vul de lijst met de apparaten in. De volgende combinaties van ingevulde eigenschappen zijn minimaal vereist voor het identificeren van elk apparaat:

- [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey).

- [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).

- [**HardwareHash**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)  +  [**ProductKey**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)  +  [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber).

- [**Alleen HardwareHash.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.hardwarehash)

- [**Alleen ProductKey.**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.productkey)

- [**SerialNumber**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.serialnumber)  +  [**OemManufacturerName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.oemmanufacturername)  +  [**ModelName**](/dotnet/api/microsoft.store.partnercenter.models.devicesdeployment.device.modelname).

Roep vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant. Roep vervolgens de [**methode DeviceBatches.ById aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) met de batch-id van het apparaat om een interface op te halen voor bewerkingen voor de opgegeven batch. Roep ten slotte de [**methode Devices.Create**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.createasync) aan met de lijst met apparaten om de apparaten toe te voegen aan de apparaatbatch.

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

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: CreateDevices.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                            |
|----------|------------------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik het volgende pad en de queryparameters bij het maken van de aanvraag.

| Naam           | Type   | Vereist | Beschrijving                                           |
|----------------|--------|----------|-------------------------------------------------------|
| customer-id    | tekenreeks | Ja      | Een tekenreeks in GUID-indeling die de klant identificeert. |
| devicebatch-id | tekenreeks | Ja      | Een tekenreeks-id die de apparaatbatch identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

De aanvraag body moet een matrix van [apparaatobjecten](device-deployment-resources.md#device) bevatten. De volgende combinaties van velden voor het identificeren van een apparaat worden geaccepteerd:

- hardwareHash + productKey.
- hardwareHash + serialNumber.
- hardwareHash + productKey + serialNumber.
- alleen hardwareHash.
- alleen productKey.
- serialNumber + oemManufacturerName + modelName.

### <a name="request-example"></a>Voorbeeld van aanvraag

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

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat het antwoord een **Location-header** met een URI die kan worden gebruikt om de uploadstatus van het apparaat op te halen. Sla deze URI op voor gebruik met andere gerelateerde REST API's.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

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
