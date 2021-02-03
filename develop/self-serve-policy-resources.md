---
title: Zelf beleids resources beheren
description: Een partner stelt zelf het beleid voor een klant in.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 04daf6aaeb69153c4139941188f53dbab8979969
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767245"
---
# <a name="selfservepolicy-resource"></a>SelfServePolicy-resource

**Van toepassing op:**

- Partnercentrum

Een partner stelt zelf het beleid voor een klant in.

## <a name="selfservepolicy"></a>SelfServePolicy

Hierin wordt een winkel wagen beschreven.

| Eigenschap              | Type             | Beschrijving                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | Een selfservice beleids-id die wordt geleverd bij het maken van het beleid voor eigen beheer.     |
| SelfServeEntity       | SelfServeEntity  | De selfservice-entiteit waaraan toegang wordt verleend.                                                     |
| Verlener               | Verlener          | De subsidie die toegang verleent.                                                                    |
| Machtigingen           | Matrix van machtigingen| Een matrix met [machtigings](#permission) bronnen.                                                                     |

## <a name="selfserveentity"></a>SelfServeEntity

Vertegenwoordigt de entiteit waaraan machtigingen worden verleend.

| Eigenschap             | Type|Description|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| SelfServeEntityType  | tekenreeks                           | De entiteit waaraan toegang is verleend, geaccepteerde waarden: klant.                                 |
| TenantID             | tekenreeks                           | De Tenant-id van de entiteit waaraan toegang wordt verleend.                                   |

## <a name="grantor"></a>Verlener

Hiermee wordt de verlener aangeduid die de machtigingen verleent.

| Eigenschap             | Type|Description|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| GrantorType          | tekenreeks                           | De granting verleent toegang, geaccepteerde waarden: BillToPartner.                               |
| TenantID             | tekenreeks                           | De Tenant-id van de entiteit die toegang verleent.                                       |


## <a name="permission"></a>Machtiging

Hiermee wordt een machtiging in het beleid voor zelf beheer aangeduid.

| Eigenschap             | Type|Description|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| Resource             | tekenreeks                           | De toegang tot de resource is te klein: AzureReservedInstances.                          |
| Bewerking               | tekenreeks                           | De actie toegang wordt verleend voor: aankoop                                           |
