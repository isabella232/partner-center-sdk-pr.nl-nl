---
title: Resources voor self-servebeleid
description: Een partner stelt beleid voor self-service in voor een klant.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ffca78481572e201d3ef9f488e7d594a9c1176249b4415a347b488f4b9b81c51
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996764"
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

| Eigenschap             | Type|Description|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| SelfServeEntityType  | tekenreeks                           | De entiteit die toegang krijgt, geaccepteerde waarden: Klant.                                 |
| TenantID             | tekenreeks                           | De tenant-id van de entiteit die toegang krijgt.                                   |

## <a name="grantor"></a>Grantor

Vertegenwoordigt de grantor die de machtigingen verleent.

| Eigenschap             | Type|Description|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| GrantorType          | tekenreeks                           | De grantor die toegang verleent, geaccepteerde waarden: BillToPartner.                               |
| TenantID             | tekenreeks                           | De tenant-id van de entiteit die toegang verleent.                                       |


## <a name="permission"></a>Machtiging

Vertegenwoordigt een machtiging in het beleid voor self-serve.

| Eigenschap             | Type|Description|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| Resource             | tekenreeks                           | De toegang tot de resource wordt ook verleend: AzureReservedInstances.                          |
| Actie               | tekenreeks                           | Er wordt toegang verleend tot de actie voor: Aankoop                                           |
