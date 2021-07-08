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
# <a name="get-a-list-of-devices-for-the-specified-batch-and-customer"></a>Een lijst met de apparaten voor de opgegeven batch en klant ophalen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland

In dit artikel wordt beschreven hoe u een verzameling apparaten in een opgegeven apparaatbatch ophaalt voor een opgegeven klant. Elke apparaatresource bevat details over het apparaat.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een batch-id van een apparaat.

## <a name="c"></a>C\#

Een verzameling van de apparaten in een opgegeven apparaatbatch ophalen voor de opgegeven klant:

1. Roep de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.

2. Roep de [**methode DeviceBatches.ById aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) om een interface op te halen voor batchverzamelingsbewerkingen van apparaten voor de opgegeven batch.

3. Haal de [**eigenschap Apparaten**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatch.devices) op om een interface op te halen voor bewerkingen voor het verzamelen van apparaten voor de batch.

4. Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.getasync) om de verzameling apparaten op te halen.

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;

var devices =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.Get();
```

Zie voor een voorbeeld het volgende:

- Voorbeeld: [Consoletest-app](console-test-app.md)
- Project: **Partnercentrum-SDK Voorbeelden**
- Klasse: **GetDevices.cs**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                            |
|---------|------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende padparameters bij het maken van de aanvraag.

| Naam           | Type   | Vereist | Beschrijving                                           |
|----------------|--------|----------|-------------------------------------------------------|
| customer-id    | tekenreeks | Ja      | Een tekenreeks in GUID-indeling die de klant identificeert. |
| devicebatch-id | tekenreeks | Ja      | Een tekenreeks-id die de apparaatbatch identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

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

Als dit lukt, bevat de antwoord-hoofdverzameling een verzameling [apparaatresources met pagina's.](device-deployment-resources.md#device) De verzameling bevat 100 apparaten op een pagina. Als u de volgende pagina van 100 apparaten wilt ophalen, moet het continuationToken in de hoofdtekst van het antwoord worden opgenomen in de volgende aanvraag als een MS-ContinuationToken header.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center een volledige lijst.](error-codes.md)

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
