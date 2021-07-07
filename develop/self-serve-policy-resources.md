---
title: Resources voor self-servebeleid
description: Een partner stelt beleid voor self-service in voor een klant.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e44581b805e076132984b67280699314e274ca94
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446714"
---
# <a name="selfservepolicy-resource"></a>SelfServePolicy-resource

Een partner stelt beleid voor self-service in voor een klant.

## <a name="selfservepolicy"></a>SelfServePolicy

Beschrijft een winkelwagen.

| Eigenschap              | Type             | Beschrijving                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | Een self-serve beleids-id die wordt opgegeven wanneer het self-serve-beleid is gemaakt.     |
| SelfServeEntity       | SelfServeEntity  | De zelfhulpentiteit die toegang krijgt.                                                     |
| Grantor               | Grantor          | De grantor die toegang verleent.                                                                    |
| Machtigingen           | Matrix van machtigingen| Een matrix met [machtigingsbronnen.](#permission)                                                                     |

## <a name="selfserveentity"></a>SelfServeEntity

Vertegenwoordigt de entiteit die machtigingen krijgt.

| Eigenschap             | Type|Beschrijving|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| SelfServeEntityType  | tekenreeks                           | De entiteit die toegang krijgt, geaccepteerde waarden: Klant.                                 |
| TenantID             | tekenreeks                           | De tenant-id van de entiteit die toegang krijgt.                                   |

## <a name="grantor"></a>Grantor

Vertegenwoordigt de grantor die de machtigingen verleent.

| Eigenschap             | Type|Beschrijving|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| GrantorType          | tekenreeks                           | De grantor die toegang verleent, geaccepteerde waarden: BillToPartner.                               |
| TenantID             | tekenreeks                           | De tenant-id van de entiteit die toegang verleent.                                       |


## <a name="permission"></a>Machtiging

Vertegenwoordigt een machtiging in het beleid voor self-serve.

| Eigenschap             | Type|Beschrijving|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| Resource             | tekenreeks                           | De toegang tot de resource wordt ook verleend: AzureReservedInstances.                          |
| Bewerking               | tekenreeks                           | Er wordt toegang verleend tot de actie voor: Aankoop                                           |
