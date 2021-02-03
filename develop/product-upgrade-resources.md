---
title: Bronnen voor product-upgrades
description: U kunt meerdere resources met betrekking tot partner Center-product upgrades gebruiken voor een Azure-abonnement. Dit zijn onder andere ProductUpgradeRequest, ProductUpgradesEligibility, ProductUpgradesStatus, UpgradesLineItem, UpgradeProduct en error Details.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c0245141dc99832f47bff9b68741724d5d313ab8
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767223"
---
# <a name="product-upgrade-resources"></a>Bronnen voor product-upgrades

**Van toepassing op:**

- Partnercentrum

U kunt de volgende bronnen gebruiken voor informatie over het upgraden van een partner Center-product van een Microsoft Azure (MS-AZR-0145P) naar een Azure-abonnement.

## <a name="productupgraderequest"></a>ProductUpgradeRequest

De **ProductUpgradesRequest** -resource bevat informatie over het aanvraag object voor product upgrades.

| Eigenschap | Type | Description |
|----------------------|----------------------------------------------|----------------------------------------------------------------|
| customerId           | tekenreeks                                       | Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd. |
| productFamily        | tekenreeks                                       | De product familie waarvoor de upgrade is aangevraagd. |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken. |

## <a name="productupgradeseligibility"></a>ProductUpgradesEligibility

De **ProductUpgradesEligibility** -resource biedt informatie over de geschiktheid van de klant voor het upgraden van een product.

| Eigenschap | Type | Description |
|----------------------|--------------------------------------------- |----------------------------------------------------------------|
| customerId           | tekenreeks                                       | Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd. |          | productFamily        | tekenreeks                                       | De product familie waarvoor de upgrade is aangevraagd. |
| isEligible           | booleaans                                         | De Boole-waarde geeft aan of de klant in aanmerking komt voor de aangevraagde upgrade. |
| upgradeId            | tekenreeks                                       | De upgrade-ID als er al een product upgrade voor de betreffende familie is. |
| reason               | tekenreeks                                       | De reden waarom de klant niet in aanmerking komt voor product upgrade. |
| productFamily        | tekenreeks                                       | De product familie waarvoor de upgrade is aangevraagd. |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.

## <a name="productupgradesstatus"></a>ProductUpgradesStatus

De **ProductUpgradesStatus** -resource bevat informatie over de status van een product upgrade.

| Eigenschap | Type | Description |
|---------------------|----------------------------------------------------------------|-----------------------------------------------|
| Id                  | tekenreeks                                                         | Een teken reeks met een GUID-indeling waarmee de upgrade wordt geïdentificeerd. |
| productFamily       | tekenreeks                                                         | De product familie waarvoor de upgrade is aangevraagd.
| status              | tekenreeks                                                         | De status van de product upgrade.
| Regel items           | matrix van [UpgradesLineItem](#upgradeslineitem) -resources       | Een matrix met objecten die informatie bevatten over de upgrade Details voor elk regel item dat deel uitmaakt van de aanvraag tekst.
| Error Details        | [Error Details](#errordetails) -resource                         | De fout Details voor de aangevraagde upgrade.
| kenmerken          | [ResourceAttributes](utility-resources.md#resourceattributes)  | De meta gegevens kenmerken. |

## <a name="upgradeslineitem"></a>UpgradesLineItem

De **UpgradesLineItem** -resource beschrijft de status van product upgrade Details voor elk regel item van de aanvraag.

| Eigenschap | Type | Description |
|-----------------|-----------------------------------------------------|--------------------------------------------------------------|
| sourceProduct   | [UpgradeProduct](#upgradeproduct) -object            | Gegevens van het bron product dat wordt geüpgraded. |
| targetProduct   | [UpgradeProduct](#upgradeproduct) -object            | Informatie over de product post-upgrade voor het doel. |
| upgradedDate    | teken reeks in UTC-datum-tijd notatie                      | De datum waarop het abonnement is bijgewerkt. |
| status          | tekenreeks                                              | De status van de product upgrade. |
| Error Details    | [Error Details](#errordetails) -resource              | De fout Details voor de aangevraagde upgrade. |
| kenmerken      | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.  |

## <a name="upgradeproduct"></a>UpgradeProduct

De **UpgradeProduct** -resource bevat informatie over het product dat wordt geüpgraded.

| Eigenschap | Type |Beschrijving |
|----------------------|----------------------------------------------|----------------------------------------------------------------|
| id                   | tekenreeks                                       | Een teken reeks met een GUID-indeling waarmee het product wordt geïdentificeerd. |
| naam                 | tekenreeks                                       | De beschrijvende naam van het product dat wordt geüpgraded. |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken. |

## <a name="errordetails"></a>ErrorDetails

De **Error Details** -resource biedt Details over fouten tijdens het upgrade proces.

| Eigenschap | Type | Description |
|-------------------------|----------------------------------------------|-------------------------------------------------------------|
| code                    | tekenreeks                                       | Een fout code wanneer het bijwerken van het product mislukt. |
| message                 | tekenreeks                                       | Het fout bericht wanneer het bijwerken van het product mislukt. |
| kenmerken              | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken. |
