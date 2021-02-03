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
# <a name="get-a-list-of-devices-for-the-specified-batch-and-customer"></a>Een lijst met de apparaten voor de opgegeven batch en klant ophalen

**Van toepassing op:**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland

In dit artikel wordt beschreven hoe u een verzameling apparaten kunt ophalen in een opgegeven batch voor een opgegeven klant. Elke bron van het apparaat bevat details over het apparaat.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een batch-id voor het apparaat.

## <a name="c"></a>C\#

Ophalen van een verzameling van de apparaten in een opgegeven batch voor de opgegeven klant:

1. Roep de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.

2. Roep de methode [**DeviceBatches. ById**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) aan om een interface te verkrijgen voor het verzamelen van batch-bewerkingen voor het apparaat voor de opgegeven batch.

3. Haal de eigenschap [**apparaten**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatch.devices) op om een interface voor het verzamelen van apparaten op te halen voor de batch.

4. Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.getasync) aan om de verzameling van apparaten op te halen.

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;

var devices =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.Get();
```

Voor een voor beeld ziet u het volgende:

- Voor beeld: [console test-app](console-test-app.md)
- Project: **Partner Center SDK** -voor beelden
- Klasse: **GetDevices.cs**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/deviceBatches/{devicebatch-ID}/devices http/1.1 |

#### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende Path-para meters bij het maken van de aanvraag.

| Naam           | Type   | Vereist | Beschrijving                                           |
|----------------|--------|----------|-------------------------------------------------------|
| klant-id    | tekenreeks | Yes      | Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd. |
| devicebatch-id | tekenreeks | Yes      | Een teken reeks-id waarmee de apparaat-batch wordt geïdentificeerd. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches/testbatch/devices HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord tekst een wissel bare verzameling van bronnen voor [apparaten](device-deployment-resources.md#device) . De verzameling bevat 100-apparaten op een pagina. Als u de volgende pagina van 100 apparaten wilt ophalen, moet de continuationToken in de antwoord tekst worden opgenomen in de volgende aanvraag als MS-ContinuationToken-header.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie voor een volledige lijst de [rest-fout codes van het partner centrum](error-codes.md).

### <a name="response-example"></a>Voorbeeld van antwoord

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
