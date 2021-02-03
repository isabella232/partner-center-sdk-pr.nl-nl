---
title: Implementatie bronnen voor apparaten
description: Resources met betrekking tot de implementatie van het partner centrum-apparaat.
ms.date: 06/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a464cdad3979c305df16a3bdc9133ce70a7ac688
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767189"
---
# <a name="device-deployment-resources"></a>Implementatie bronnen voor apparaten

**Van toepassing op:**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland

De volgende bronnen zijn gerelateerd aan de implementatie van het apparaat.

## <a name="configurationpolicy"></a>ConfigurationPolicy

**ConfigurationPolicy** biedt informatie over een configuratie beleid.

| Eigenschap             | Type                                                           | Beschrijving                                                        |
|----------------------|----------------------------------------------|--------------------------------------------------------------------------------------|
| id                   | tekenreeks                                       | Een teken reeks met een GUID-indeling waarmee het beleid wordt geïdentificeerd.                                  |
| naam                 | tekenreeks                                       | De beschrijvende naam voor het beleid.                                                    |
| category             | tekenreeks                                       | De categorie.                                                                        |
| beschrijving          | tekenreeks                                       | De beschrijving van het beleid.                                                              |
| devicesAssignedCount | getal                                       | Het aantal apparaten dat aan dit beleid is toegewezen.                                       |
| policySettings       | tekenreeksmatrix                             | De beleids instellingen: ' geen ', ' \_ OEM- \_ voor installatie verwijderen ', ' OOBE- \_ gebruiker \_ niet \_ lokale \_ beheerder ', ' overs laan van \_ snelle instellingen ', ' overs laan van OEM- \_ \_ \_ registratie ', ' \_ gebruiksrecht overeenkomst overs Laan '.    |
| createdDate          | teken reeks in UTC-datum-tijd notatie               | De datum en tijd waarop het beleid is gemaakt.                                            |
| lastModifiedDate     | teken reeks in UTC-datum-tijd notatie               | De datum en tijd waarop het beleid voor het laatst is gewijzigd.                                      |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.                                            |

## <a name="device"></a>Apparaat

**Apparaat** biedt informatie over een apparaat.

| Eigenschap            | Type                                                           | Beschrijving                                                              |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------|
| id                  | tekenreeks                                                         | Een teken reeks met een GUID-indeling waarmee het apparaat wordt geïdentificeerd.                      |
| serialNumber        | tekenreeks                                                         | Het serie nummer dat uniek is gekoppeld aan het apparaat.                   |
| productKey          | tekenreeks                                                         | De product code die uniek is gekoppeld aan het apparaat.                     |
| hardwareHash        | tekenreeks                                                         | De hardware-hash die uniek is gekoppeld aan het apparaat.                   |
| modelName           | tekenreeks                                                         | De naam van het model dat aan het apparaat is gekoppeld.                               |
| oemManufacturerName | tekenreeks                                                         | De naam van de OEM-fabrikant die aan het apparaat is gekoppeld.             |
| policies            | matrix van objecten                                               | De lijst met beleids regels die zijn toegewezen aan het apparaat.                             |
| uploadedDate        | teken reeks in UTC-datum-tijd notatie                                 | De datum en tijd waarop de details van het apparaat zijn geüpload.                      |
| allowedOperations   | tekenreeksmatrix                                               | De lijst met HTTP-methoden die zijn toegestaan op een apparaat synchroniseren als GET, PATCH, verwijderen. |
| kenmerken          | [ResourceAttributes](utility-resources.md#resourceattributes)  | De meta gegevens kenmerken.                                                 |

## <a name="batchuploaddetails"></a>BatchUploadDetails

**BatchUploadDetails** beschrijft de status van een apparaat batch upload van informatie over elk apparaat in een lijst met apparaten.

| Eigenschap        | Type     | Description                                                                  |
|-----------------|----------|------------------------------------------------------------------------------|
| batchTrackingId | tekenreeks   | Een teken reeks die is ingedeeld in de GUID die is gekoppeld aan de batch apparaten die zijn geüpload. |
| status          | tekenreeks   | De status van de batch upload: ' onbekend ', ' in wachtrij ', ' verwerking ', ' voltooid ', \_ met fouten voltooid \_ . |
| startedTime     | teken reeks in UTC-datum-tijd notatie | De datum en tijd waarop het batch-upload proces is gestart.   |
| completedTime   | teken reeks in UTC-datum-tijd notatie  | De datum en tijd waarop het batch-upload proces is voltooid.   |
| devicesStatus   | matrix van [DeviceUploadDetails](#deviceuploaddetails) -resources | Een matrix met objecten waarmee de status van elke apparaatgegevens worden geüpload. |
| kenmerken      | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.  |

## <a name="deviceuploaddetails"></a>DeviceUploadDetails

**DeviceUploadDetails** beschrijft de status van het uploaden van gegevens over een apparaat.

| Eigenschap         | Type                    | Description                                 |
|------------------|-------------------------|---------------------------------------------|
| deviceId         | tekenreeks                  | Een teken reeks met een GUID-indeling die aan het apparaat is gekoppeld. |
| serialNumber     | tekenreeks                  | Het serie nummer dat uniek is gekoppeld aan het apparaat. |
| productKey       | tekenreeks                  | De product code die uniek is gekoppeld aan het apparaat. |
| status           | tekenreeks                  | De status van de apparaatgegevens uploaden: ' in uitvoering ', ' voltooid ', \_ met \_ fouten voltooid. |
| errorCode        | tekenreeks                  | De fout code van de HTTP-status die wordt geretourneerd als het uploaden van het apparaat mislukt. |
| errorDescription | tekenreeks                  | De HTTP-fout beschrijving als het uploaden van het apparaat mislukt. |
| kenmerken       | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.   |

## <a name="devicebatch"></a>DeviceBatch

**DeviceBatch** vertegenwoordigt een verzameling apparaten.

| Eigenschap     | Type                                                           | Beschrijving                                                           |
|--------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| id           | tekenreeks                                                         | Een teken reeks met een GUID-indeling die is gekoppeld aan de batch apparaten. |
| Type CreatedBy    | tekenreeks                                                         | De naam van de Tenant die de verzameling heeft gemaakt.                   |
| creationDate | teken reeks in UTC-datum-tijd notatie                                 | De gegevens en het tijdstip waarop de verzameling is gemaakt.                    |
| deviceCount  | getal                                                         | Het aantal apparaten in de verzameling.                              |
| devicesLink  | [Koppeling](utility-resources.md#link)                              | Een koppeling naar de apparaten die zijn opgenomen in deze batch.                        |
| kenmerken   | [ResourceAttributes](utility-resources.md#resourceattributes)  | De meta gegevens kenmerken.                                              |

## <a name="devicebatchcreationrequest"></a>DeviceBatchCreationRequest

**DeviceBatchCreationRequest** biedt de vereiste informatie voor het maken van een apparaat batch en vult deze met apparaten.

| Eigenschap     | Type                                                           | Description                                                           |
|--------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| batchId      | tekenreeks                                                         | Een teken reeks met een GUID-indeling die is gekoppeld aan de batch apparaten. |
| devices      | matrix van [apparaatobject](#device)                             | Met elk object wordt een apparaat opgegeven. De volgende combi Naties van velden voor het identificeren van een apparaat worden geaccepteerd: hardwareHash + productKey, hardwareHash + serialNumber, hardwareHash + productKey + serialNumber, hardwareHash alleen, productKey, serialNumber + oemManufacturerName + modelnaam. |
| kenmerken   | [ResourceAttributes](utility-resources.md#resourceattributes)  | De meta gegevens kenmerken.                                              |

## <a name="devicepolicyupdaterequest"></a>DevicePolicyUpdateRequest

**DevicePolicyUpdateRequest** biedt de vereiste informatie voor het bijwerken van een lijst met apparaten met een beleid.

| Eigenschap     | Type                                                           | Description                                                           |
|--------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| devices      | matrix van [apparaatobject](#device)                             | Met elk object wordt een apparaat opgegeven. De volgende eigenschappen zijn vereist: id, beleids regels. |
| kenmerken   | [ResourceAttributes](utility-resources.md#resourceattributes)  | De meta gegevens kenmerken.                                              |
