---
title: Rechtenbronnen
description: Beschrijft resources met betrekking tot rechten.
ms.date: 01/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 929004fff804675218e267bb928b432f7b1209bf
ms.sourcegitcommit: 84a6f701190f46d2adcf6edcaeaafa32d58fbaba
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2021
ms.locfileid: "113510105"
---
# <a name="entitlement-resources"></a>Rechtenbronnen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

## <a name="entitlement"></a>Recht

Deze resource vertegenwoordigt de producten waarvoor de klant het recht heeft om te gebruiken vanwege partneraankopen voor items uit de catalogus.

| Eigenschap | Type | Beschrijving |
|----------|------|-------------|
| referenceOrder | [ReferenceOrder](#referenceorder) | De orderverwijzing die heeft geleid tot het recht. |
| productId | tekenreeks | De id van het product. |
| skuID | tekenreeks | De id van de SKU. |
| quantity | int | De hoeveelheid rechten (exclusief niet-geleverde/overgemaakte rechten). |
| quantityDetails | IEnumerable<[QuantityDetail](#quantitydetail)> | De lijst met details van de hoeveelheid rechten (het aantal items en de status van elke hoeveelheid). |
| entitlementType | tekenreeks | Het type rechten. (Bijgewerkt naar tekenreeks van [EntitlementType](#entitlementtype) in SDK 1.8.) |
| entitledArtifacts | IEnumerable<[Artifact](#artifact)> | De lijst met artefacten die zijn gekoppeld aan het recht. |
| IncludedEntitlements | IEnumerable<[Rechten](#artifact)> | De lijst met rechten, die impliciet zijn opgenomen als gevolg van de product-/SkuId-aankoop uit de catalogus. |
| ExpiryDate | tekenreeks in UTC-datum/tijd-indeling  | De vervaldatum van het recht (indien van toepassing). |

## <a name="referenceorder"></a>ReferenceOrder

De verwijzing naar de volgorde van een recht.

| Eigenschap | Type | Beschrijving |
|----------|------|-------------|
| id | tekenreeks | De id van de bestelling waarnaar wordt verwezen. |
| lineItemId | tekenreeks | De id van het orderregelitem waarnaar wordt verwezen. |
| alternateId | tekenreeks | De alternatieve id van het orderregelitem waarnaar wordt verwezen. |

## <a name="quantitydetail"></a>QuantityDetail

Vertegenwoordigt de details van een aantal rechten.

| Eigenschap | Type | Beschrijving |
|----------|------|-------------|
| quantity | int | Het aantal items. |
| status | tekenreeks | De status van de hoeveelheid. |

## <a name="entitlementtype"></a>EntitlementType

> [!IMPORTANT]
> Afgeschaft in SDK v1.9

Een [enum](/dotnet/api/system.enum) met waarden die het type rechten aangeven.

| Waarde | Beschrijving |
|-------|-------------|
| Software | Geeft het rechtentype aan dat is gerelateerd aan software. |
| VirtualMachineReservedInstance | Geeft het rechtentype aan dat is Azure Reserved Virtual Machine Instances. |

## <a name="artifact"></a>Artefact

Het artefact dat is gekoppeld aan het recht.

| Eigenschap | Type | Beschrijving |
|----------|------|-------------|
| artifactType | tekenreeks | Het type artefact. (Bijgewerkt naar tekenreeks van [ArtifactType](#artifacttype) in SDK V1.8) |
| dynamicAttributes | &lt;Woordenlijstreeks, object&gt; | Dynamische kenmerken die specifieke waarden voor artifacttype bevatten. Als bijvoorbeeld artifactType = "reservedinstance" wordt gebruikt, bevat deze eigenschap "reservationType" = "virtualmachines" of "reservationType" = "sqldatabases" die de gereserveerde instantie van de virtuele machine of de gereserveerde instantie van Azure SQL aantekent. (Beschikbaar vanaf SDK v1.9) |

## <a name="artifacttype"></a>ArtifactType

> [!IMPORTANT]
> Afgeschaft in SDK v1.9

Een [enum met](/dotnet/api/system.enum) waarden die het type rechtenartefact aangeven.

| Waarde                          | Beschrijving                                                                             |
|--------------------------------| ----------------------------------------------------------------------------------------|
| VirtualMachineReservedInstance | Geeft aan dat het artefact helpt bij het ophalen van Azure Reserved Virtual Machine Instances. |

## <a name="reservedinstanceartifact"></a>ReservedInstanceArtifact

Het artefact dat is gekoppeld aan het recht van een gereserveerde Azure-instantie. Deze neemt over van de [klasse Artifact.](#artifact)

| Eigenschap   | Type                           | Beschrijving                                        |
|------------|--------------------------------|----------------------------------------------------|
| koppelen       | [Koppeling](./utility-resources.md#link) | De koppeling om alle bijbehorende artefactgegevens op te halen.   |
| Resourceid | tekenreeks                         | De id van de Azure-reserveringsorder of -resource. |

## <a name="reservedinstanceartifactdetails"></a>ReservedInstanceArtifactDetails

Vertegenwoordigt de entiteit die wordt geretourneerd bij het aanroepen van de azure Reserved Instance artifact-koppeling.

|   Eigenschap   |           Type           |                          Beschrijving                          |
|--------------|--------------------------|---------------------------------------------------------------|
|     type     |          tekenreeks          |                     Het type artefact.                     |
| Reserveringen | `IEnumerable<Reservation>` | Geeft de Azure-resource of reserveringsorder-id aan. |

## <a name="reservation"></a>Reservering

Vertegenwoordigt een afzonderlijke reservering.

| Eigenschap          | Type                           | Beschrijving                                                        |
|-------------------|--------------------------------|--------------------------------------------------------------------|
| reservationId     | tekenreeks                         | De id van de reservering.                                         |
| scopeType         | tekenreeks                         | Het type bereik dat is gekoppeld aan de reservering van de virtuele machine. |
| displayName       | tekenreeks                         | De weergavenaam van de reservering.                               |
| appliedScopes     | IEnumerable                    | De lijst met toegepaste scopes die zijn gekoppeld aan de reservering. (Alleen beschikbaar wanneer scopeType niet wordt gedeeld.) |
| quantity          | int                            | Het aantal virtuele machines in de reservering.                 |
| expiryDateTime    | tekenreeks in UTC-datum/tijd-indeling | De vervaldatum van de reservering.                                |
| effectiveDateTime | tekenreeks in UTC-datum/tijd-indeling | De ingangsdatum van de reservering.                             |
| provisioningState | tekenreeks                         | De inrichtingstoestand van de reservering.                         |

## <a name="virtualmachinereservedinstanceartifact"></a>VirtualMachineReservedInstanceArtifact

> [!IMPORTANT]
> Afgeschaft in SDK v1.9

Het artefact dat is gekoppeld aan een Azure Reserved Virtual Machine Instance-rechten. Deze neemt over van de [klasse Artifact.](#artifact)

| Eigenschap   | Type                              | Beschrijving                                        |
|------------|-----------------------------------|----------------------------------------------------|
| koppelen       | [Koppeling](utility-resources.md#link) | De koppeling om alle bijbehorende artefactgegevens op te halen.   |
| Resourceid | tekenreeks                            | De id van de Azure-reserveringsorder of -resource. |

## <a name="virtualmachinereservedinstanceartifactdetails"></a>VirtualMachineReservedInstanceArtifactDetails

> [!IMPORTANT]
> Afgeschaft in SDK v1.9

Vertegenwoordigt de entiteit die wordt geretourneerd bij het aanroepen van de artefactkoppeling Azure Reserved Virtual Machine Instance.

| Eigenschap                    | Type                                                                 | Beschrijving           |
|-----------------------------|----------------------------------------------------------------------|-----------------------|
| type                        | [ArtifactType](#artifacttype)                                        | Het type artefact. |
| virtualMachineReservations  | IEnumerable<[VirtualMachineReservation](#virtualmachinereservation)> | Geeft de Azure-resource of reserveringsorder-id aan. |

## <a name="virtualmachinereservation"></a>VirtualMachineReservation

> [!IMPORTANT]
> Afgeschaft in SDK v1.9

Vertegenwoordigt een afzonderlijke virtuele-machinereservering.

|     Eigenschap      |              Type              |                                                Beschrijving                                                 |
|-------------------|--------------------------------|------------------------------------------------------------------------------------------------------------|
|   reservationId   |             tekenreeks             |                                         De id van de reservering.                                         |
|     scopeType     |             tekenreeks             |                     Het type bereik dat is gekoppeld aan de reservering van de virtuele machine.                     |
|    displayName    |             tekenreeks             |                                    De weergavenaam van de reservering.                                    |
|   appliedScopes   |      `IEnumerable<string>`       | De lijst met toegepaste scopes die zijn gekoppeld aan de reservering. (Alleen beschikbaar wanneer scopeType niet wordt gedeeld.) |
|     quantity      |              int               |                             Het aantal virtuele machines in de reservering.                             |
|  expiryDateTime   | tekenreeks in UTC-datum/tijd-indeling |                                    De vervaldatum van de reservering.                                     |
| effectiveDateTime | tekenreeks in UTC-datum/tijd-indeling |                                   De ingangsdatum van de reservering.                                   |
| provisioningState |             tekenreeks             |                                 De inrichtingstoestand van de reservering.                                 |
