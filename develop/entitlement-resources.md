---
title: Rechten resources
description: Beschrijft bronnen die betrekking hebben op recht.
ms.date: 01/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 428ac6f8b4d67894092119a6246279045a04dac0
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767361"
---
# <a name="entitlement-resources"></a>Rechten resources

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

## <a name="entitlement"></a>Recht

Deze resource bevat de producten waarvoor de klant recht heeft om te worden gebruikt vanwege een partner aankoop voor items uit de catalogus.

| Eigenschap | Type | Description |
|----------|------|-------------|
| referenceOrder | [ReferenceOrder](#referenceorder) | De verwijzing naar de order die heeft geresulteerd in het recht. |
| productId | tekenreeks | De id van het product. |
| skuID | tekenreeks | De ID van de SKU. |
| quantity | int | Het aantal rechten (exclusief niet-afgehandelde/overgedragen rechten). |
| quantityDetails | IEnumerable<[QuantityDetail](#quantitydetail)> | De lijst met details van de rechten hoeveelheid (het aantal items en de status van elk aantal). |
| entitlementType | tekenreeks | Het type recht. (Bijgewerkt naar een teken reeks van [EntitlementType](#entitlementtype) in SDK 1,8.) |
| entitledArtifacts | IEnumerable<- [artefact](#artifact)> | De lijst met artefacten die zijn gekoppeld aan het recht. |
| IncludedEntitlements | IEnumerable<[recht](#artifact)> | De lijst met rechten die impliciet zijn opgenomen als resultaat van de aankoop van de SkuId van de catalogus. |
| ExpiryDate | teken reeks in UTC-datum-tijd notatie  | De verval datum van de rechten (indien van toepassing). |

## <a name="referenceorder"></a>ReferenceOrder

De volg orde van de verwijzing van een recht.

| Eigenschap | Type | Beschrijving |
|----------|------|-------------|
| id | tekenreeks | De ID van de order waarnaar wordt verwezen. |
| lineItemId | tekenreeks | De ID van het order regel item waarnaar wordt verwezen. |
| alternateId | tekenreeks | De alternatieve ID van het order regel item waarnaar wordt verwezen. |

## <a name="quantitydetail"></a>QuantityDetail

Hiermee worden de details van een rechtse hoeveelheid aangegeven.

| Eigenschap | Type | Description |
|----------|------|-------------|
| quantity | int | Het aantal items. |
| status | tekenreeks | De status van de hoeveelheid. |

## <a name="entitlementtype"></a>EntitlementType

> [!IMPORTANT]
> Afgeschaft in SDK v 1,9

Een [Enum](/dotnet/api/system.enum) met waarden die het type recht aangeven.

| Waarde | Beschrijving |
|-------|-------------|
| Software | Hiermee wordt het type recht aangegeven dat is gerelateerd aan software. |
| VirtualMachineReservedInstance | Hiermee wordt het type recht aangegeven dat is gerelateerd aan Azure Reserved Virtual Machine Instances. |

## <a name="artifact"></a>Artefact

Het artefact dat is gekoppeld aan het recht.

| Eigenschap | Type | Description |
|----------|------|-------------|
| artifactType | tekenreeks | Het type artefact. (Bijgewerkt met een teken reeks van [ArtifactType](#artifacttype) in SDK v 1.8) |
| dynamicAttributes | Woordenboek &lt; teken reeks, object&gt; | Dynamische kenmerken met artifacttype-specifieke waarden. Als bijvoorbeeld artifactType = "reservedinstance" is, bevat deze eigenschap "reservationType" = "informatie" of "reservationType" = "sqldatabases" die het gereserveerde exemplaar van een virtuele machine of een gereserveerd Azure SQL-exemplaar aangeeft. (Beschikbaar vanaf SDK v 1,9) |

## <a name="artifacttype"></a>ArtifactType

> [!IMPORTANT]
> Afgeschaft in SDK v 1,9

Een [Enum](/dotnet/api/system.enum) met waarden die het type van het rechten artefact aangeven.

| Waarde                          | Beschrijving                                                                             |
|--------------------------------| ----------------------------------------------------------------------------------------|
| VirtualMachineReservedInstance | Hiermee worden de hulp middelen voor artefacten aangegeven bij het ophalen van Azure Reserved Virtual Machine Instances. |

## <a name="reservedinstanceartifact"></a>ReservedInstanceArtifact

Het artefact dat is gekoppeld aan een door Azure gereserveerde instantie-recht. Deze wordt overgenomen van de klasse [artefacten](#artifact) .

| Eigenschap   | Type                           | Description                                        |
|------------|--------------------------------|----------------------------------------------------|
| koppelen       | [Koppeling](./utility-resources.md#link) | De koppeling om alle gekoppelde artefact gegevens op te halen.   |
| resourceID | tekenreeks                         | De ID van de Azure-reserverings order of-resource. |

## <a name="reservedinstanceartifactdetails"></a>ReservedInstanceArtifactDetails

Vertegenwoordigt de entiteit die wordt geretourneerd bij het aanroepen van de koppeling naar de gereserveerde instantie artefact van Azure.

|   Eigenschap   |           Type           |                          Beschrijving                          |
|--------------|--------------------------|---------------------------------------------------------------|
|     type     |          tekenreeks          |                     Het type artefact.                     |
| ringen | IEnumerable<Reservation> | Hiermee wordt de Azure resource-of reserverings order-id aangegeven. |

## <a name="reservation"></a>Reservering

Vertegenwoordigt een afzonderlijke reserve ring.

| Eigenschap          | Type                           | Description                                                        |
|-------------------|--------------------------------|--------------------------------------------------------------------|
| reservationId     | tekenreeks                         | De ID van de reserve ring.                                         |
| scopeType         | tekenreeks                         | Het type bereik dat is gekoppeld aan de reserve ring van de virtuele machine. |
| displayName       | tekenreeks                         | De weergave naam van de reserve ring.                               |
| appliedScopes     | IEnumerable                    | De lijst met toegepaste bereiken die zijn gekoppeld aan de reserve ring. (Alleen beschikbaar als scopeType niet wordt gedeeld.) |
| quantity          | int                            | Het aantal virtuele machines in de reserve ring.                 |
| expiryDateTime    | teken reeks in UTC-datum-tijd notatie | De verval datum van de reserve ring.                                |
| effectiveDateTime | teken reeks in UTC-datum-tijd notatie | De ingangs datum van de reserve ring.                             |
| provisioningState | tekenreeks                         | De inrichtings status van de reserve ring.                         |

## <a name="virtualmachinereservedinstanceartifact"></a>VirtualMachineReservedInstanceArtifact

> [!IMPORTANT]
> Afgeschaft in SDK v 1,9

Het artefact dat is gekoppeld aan een voor Azure gereserveerde instantie van een virtuele machine. Deze wordt overgenomen van de klasse [artefacten](#artifact) .

| Eigenschap   | Type                              | Description                                        |
|------------|-----------------------------------|----------------------------------------------------|
| koppelen       | [Koppeling](utility-resources.md#link) | De koppeling om alle gekoppelde artefact gegevens op te halen.   |
| resourceID | tekenreeks                            | De ID van de Azure-reserverings order of-resource. |

## <a name="virtualmachinereservedinstanceartifactdetails"></a>VirtualMachineReservedInstanceArtifactDetails

> [!IMPORTANT]
> Afgeschaft in SDK v 1,9

Vertegenwoordigt de entiteit die wordt geretourneerd bij het aanroepen van de koppeling van de Azure reserved virtual machine-instantie artefact.

| Eigenschap                    | Type                                                                 | Beschrijving           |
|-----------------------------|----------------------------------------------------------------------|-----------------------|
| type                        | [ArtifactType](#artifacttype)                                        | Het type artefact. |
| virtualMachineReservations  | IEnumerable<[VirtualMachineReservation](#virtualmachinereservation)> | Hiermee wordt de Azure resource-of reserverings order-id aangegeven. |

## <a name="virtualmachinereservation"></a>VirtualMachineReservation

> [!IMPORTANT]
> Afgeschaft in SDK v 1,9

Vertegenwoordigt een afzonderlijke reserve ring van virtuele machines.

|     Eigenschap      |              Type              |                                                Description                                                 |
|-------------------|--------------------------------|------------------------------------------------------------------------------------------------------------|
|   reservationId   |             tekenreeks             |                                         De ID van de reserve ring.                                         |
|     scopeType     |             tekenreeks             |                     Het type bereik dat is gekoppeld aan de reserve ring van de virtuele machine.                     |
|    displayName    |             tekenreeks             |                                    De weergave naam van de reserve ring.                                    |
|   appliedScopes   |      IEnumerable<string>       | De lijst met toegepaste bereiken die zijn gekoppeld aan de reserve ring. (Alleen beschikbaar als scopeType niet wordt gedeeld.) |
|     quantity      |              int               |                             Het aantal virtuele machines in de reserve ring.                             |
|  expiryDateTime   | teken reeks in UTC-datum-tijd notatie |                                    De verval datum van de reserve ring.                                     |
| effectiveDateTime | teken reeks in UTC-datum-tijd notatie |                                   De ingangs datum van de reserve ring.                                   |
| provisioningState |             tekenreeks             |                                 De inrichtings status van de reserve ring.                                 |
