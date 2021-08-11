---
title: Een apparaat voor de opgegeven klant verwijderen
description: Een apparaat verwijderen dat bij een opgegeven klant hoort.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f44c94ff35ecdb709b44ba6eebc17ae37e513313d464a28378ce22ceb0097ee3
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115995064"
---
# <a name="delete-a-device-for-the-specified-customer"></a>Een apparaat voor de opgegeven klant verwijderen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland

In dit artikel wordt uitgelegd hoe u een apparaat verwijdert dat bij een opgegeven klant hoort.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- De batch-id van het apparaat.

- De apparaat-id.

## <a name="c"></a>C\#

Een apparaat voor de opgegeven klant verwijderen:

1. Roep de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de klant.

2. Roep de [**methode DeviceBatches.ById aan met**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.byid) de batch-id van het apparaat om een interface op te halen voor bewerkingen voor de opgegeven batch.

3. Roep de [**methode Devices.ById aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicecollection.byid) om een interface op te halen voor bewerking op het opgegeven apparaat.

4. Roep de [**methode Delete**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.delete) of [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevice.deleteasync) aan om het apparaat uit de batch te verwijderen.

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;
string selectedDeviceBatchId;
string selectedDeviceId;

partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.ById(selectedDeviceBatchId).Devices.ById(selectedDeviceId).Delete();
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project:** Partnercentrum-SDK Klasse **Samples:** DeleteDevice.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode     | Aanvraag-URI                                                                                                                        |
|------------|------------------------------------------------------------------------------------------------------------------------------------|
| DELETE     | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches/{devicebatch-id}/devices/{device-id} HTTP/1.1  |

#### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende padparameters bij het maken van de aanvraag.

| Naam           | Type   | Vereist | Beschrijving                                                        |
|----------------|--------|----------|--------------------------------------------------------------------|
| customer-id    | tekenreeks | Yes      | Een tekenreeks in GUID-indeling die de klant identificeert.              |
| devicebatch-id | tekenreeks | Yes      | De batch-id van het apparaat van de batch die het apparaat bevat. |
| device-id      | tekenreeks | Yes      | De apparaat-id.                                             |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

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

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert het antwoord **de statuscode 204 Geen** inhoud.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 394d96d0-05b2-4b02-b907-0697632ee3bb
MS-RequestId: 8b3e6f78-220b-4177-861b-33d6f38f7b97
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:58:53 GMT
```
