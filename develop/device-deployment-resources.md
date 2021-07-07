---
title: Resources voor apparaatimplementatie
description: Resources met betrekking tot Partner Center implementatie van apparaten.
ms.date: 06/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c85f0bd6a633ac18aa8e56e5a89bfc5c8f0398cc
ms.sourcegitcommit: d20e7d572fee09a83a4b23a92da7ff09cfebe75a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111906504"
---
# <a name="device-deployment-resources"></a>Resources voor apparaatimplementatie

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland

De volgende resources zijn gerelateerd aan de implementatie van apparaten.

## <a name="configurationpolicy"></a>ConfigurationPolicy

**ConfigurationPolicy** biedt informatie over een configuratiebeleid.

| Eigenschap             | Type                                                           | Beschrijving                                                        |
|----------------------|----------------------------------------------|--------------------------------------------------------------------------------------|
| id                   | tekenreeks                                       | Een tekenreeks met GUID-indeling die het beleid identificeert.                                  |
| naam                 | tekenreeks                                       | De gebruiksvriendelijke naam voor het beleid.                                                    |
| category             | tekenreeks                                       | De categorie.                                                                        |
| beschrijving          | tekenreeks                                       | De beschrijving van het beleid.                                                              |
| devicesAssignedCount | getal                                       | Het aantal apparaten dat aan dit beleid is toegewezen.                                       |
| policySettings       | tekenreeksmatrix                             | De beleidsinstellingen: "none","remove \_ oem \_ preinstalls","oobe \_ user not local \_ \_ \_ admin","skip \_ express \_ settings","skip \_ oem \_ registration", \_ "skip eula".    |
| createdDate          | tekenreeks in UTC-datum/tijd-indeling               | De datum en tijd waarop het beleid is gemaakt.                                            |
| lastModifiedDate     | tekenreeks in UTC-datum/tijd-indeling               | De datum en tijd waarop het beleid voor het laatst is gewijzigd.                                      |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                                            |

## <a name="device"></a>Apparaat

**Het** apparaat biedt informatie over een apparaat.

| Eigenschap            | Type                                                           | Beschrijving                                                              |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------|
| id                  | tekenreeks                                                         | Een tekenreeks met GUID-indeling die het apparaat identificeert.                      |
| serialNumber        | tekenreeks                                                         | Het serienummer dat uniek is gekoppeld aan het apparaat.                   |
| productKey          | tekenreeks                                                         | De productcode die uniek is gekoppeld aan het apparaat.                     |
| hardwareHash        | tekenreeks                                                         | De hardware-hash die uniek is gekoppeld aan het apparaat.                   |
| modelName           | tekenreeks                                                         | De modelnaam die aan het apparaat is gekoppeld.                               |
| oemManufacturerName | tekenreeks                                                         | De naam van de OEM-fabrikant die aan het apparaat is gekoppeld.             |
| policies            | matrix van objecten                                               | De lijst met beleidsregels die zijn toegewezen aan het apparaat.                             |
| uploadedDate        | tekenreeks in UTC-datum/tijd-indeling                                 | De datum en tijd waarop de apparaatdetails zijn geüpload.                      |
| allowedOperations   | tekenreeksmatrix                                               | De lijst met HTTP-methoden die zijn toegestaan op een apparaatsynchronisatie, zoals GET, PATCH, DELETE. |
| kenmerken          | [ResourceAttributes](utility-resources.md#resourceattributes)  | De metagegevenskenmerken.                                                 |

## <a name="batchuploaddetails"></a>BatchUploadDetails

**BatchUploadDetails beschrijft** de status van een apparaat batchupload van informatie over elk apparaat in een lijst met apparaten.

| Eigenschap        | Type     | Beschrijving                                                                  |
|-----------------|----------|------------------------------------------------------------------------------|
| batchTrackingId | tekenreeks   | Een tekenreeks met GUID-indeling die is gekoppeld aan de batch met geüploade apparaten. |
| status          | tekenreeks   | De status van de batchupload: 'onbekend', 'in de wachtrij geplaatst', 'verwerking', 'voltooid', 'voltooid \_ met \_ fouten'. |
| startedTime     | tekenreeks in UTC-datum/tijd-indeling | De datum en tijd waarop het batchuploadproces is gestart.   |
| completedTime   | tekenreeks in UTC-datum/tijd-indeling  | De datum en tijd waarop het batchuploadproces is voltooid.   |
| devicesStatus   | matrix van [DeviceUploadDetails-resources](#deviceuploaddetails) | Een matrix met objecten die de status van elke upload van apparaatgegevens specificeert. |
| kenmerken      | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.  |

## <a name="deviceuploaddetails"></a>DeviceUploadDetails

**DeviceUploadDetails** beschrijft de status van een upload van informatie over een apparaat.

| Eigenschap         | Type                    | Beschrijving                                 |
|------------------|-------------------------|---------------------------------------------|
| deviceId         | tekenreeks                  | Een tekenreeks met GUID-indeling die is gekoppeld aan het apparaat. |
| serialNumber     | tekenreeks                  | Het serienummer dat uniek is gekoppeld aan het apparaat. |
| productKey       | tekenreeks                  | De productcode die uniek is gekoppeld aan het apparaat. |
| status           | tekenreeks                  | De status van de upload van de apparaatgegevens: 'wordt uitgevoerd', 'voltooid', 'voltooid \_ met \_ fouten'. |
| errorCode        | tekenreeks                  | De HTTP-statusfoutcode die wordt geretourneerd als het uploaden van het apparaat mislukt. |
| errorDescription | tekenreeks                  | De beschrijving van de HTTP-fout als het uploaden van het apparaat mislukt. |
| kenmerken       | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.   |

## <a name="devicebatch"></a>DeviceBatch

**DeviceBatch** vertegenwoordigt een verzameling apparaten.

| Eigenschap     | Type                                                           | Beschrijving                                                           |
|--------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| id           | tekenreeks                                                         | Een tekenreeks in GUID-indeling die is gekoppeld aan de batch apparaten. |
| Createdby    | tekenreeks                                                         | De naam van de tenant die de verzameling heeft gemaakt.                   |
| creationDate | tekenreeks in UTC-datum/tijd-indeling                                 | De gegevens en tijd dat de verzameling is gemaakt.                    |
| deviceCount  | getal                                                         | Het aantal apparaten in de verzameling.                              |
| devicesLink  | [Koppeling](utility-resources.md#link)                              | Een koppeling naar de apparaten in deze batch.                        |
| kenmerken   | [ResourceAttributes](utility-resources.md#resourceattributes)  | De metagegevenskenmerken.                                              |

## <a name="devicebatchcreationrequest"></a>DeviceBatchCreationRequest

**DeviceBatchCreationRequest biedt** de informatie die nodig is om een apparaatbatch te maken en vult deze met apparaten.

| Eigenschap     | Type                                                           | Beschrijving                                                           |
|--------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| batchId      | tekenreeks                                                         | Een tekenreeks in GUID-indeling die is gekoppeld aan de batch apparaten. |
| devices      | matrix van [apparaatobjecten](#device)                             | Elk object geeft een apparaat aan. De volgende combinaties van velden voor het identificeren van een apparaat worden geaccepteerd: hardwareHash + productKey, hardwareHash + serialNumber, hardwareHash + productKey + serialNumber, hardwareHash only, productKey only, serialNumber + oemManufacturerName + modelName. |
| kenmerken   | [ResourceAttributes](utility-resources.md#resourceattributes)  | De metagegevenskenmerken.                                              |

## <a name="devicepolicyupdaterequest"></a>DevicePolicyUpdateRequest

**DevicePolicyUpdateRequest bevat** de informatie die nodig is voor het bijwerken van een lijst met apparaten met een beleid.

| Eigenschap     | Type                                                           | Beschrijving                                                           |
|--------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| devices      | matrix van [apparaatobjecten](#device)                             | Elk object geeft een apparaat aan. De volgende eigenschappen zijn vereist: Id, Beleid. |
| kenmerken   | [ResourceAttributes](utility-resources.md#resourceattributes)  | De metagegevenskenmerken.                                              |
