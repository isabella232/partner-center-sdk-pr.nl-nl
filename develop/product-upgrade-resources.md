---
title: Bronnen voor product-upgrades
description: U kunt meerdere resources gebruiken die betrekking hebben op Partner Center productupgrades naar een Azure-plan. Deze omvatten ProductUpgradeRequest, ProductUpgradesEligibility, ProductUpgradesStatus, UpgradesLineItem, UpgradeProduct en ErrorDetails.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a251168dbe1e153365beec212feca6fafddaef1700ad8651ec9d459aebf24600
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997393"
---
# <a name="product-upgrade-resources"></a>Bronnen voor product-upgrades

U kunt de volgende resources gebruiken voor informatie over Partner Center productupgrades van een Microsoft Azure-abonnement (MS-AZR-0145P) naar een Azure-abonnement.

## <a name="productupgraderequest"></a>ProductUpgradeRequest

De **resource ProductUpgradesRequest bevat** informatie over het aanvraagobject voor productupgrades.

| Eigenschap      | Type                                                          | Description                                                |
|---------------|---------------------------------------------------------------|------------------------------------------------------------|
| customerId    | tekenreeks                                                        | Een tekenreeks in GUID-indeling die de klant identificeert.      |
| productFamily | tekenreeks                                                        | De productfamilie waarvoor de upgrade is aangevraagd. |
| kenmerken    | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                                   |

## <a name="productupgradeseligibility"></a>ProductUpgradesEligibility

De **resource ProductUpgradesEligibility** biedt informatie over de geschiktheid van de klant voor het upgraden van een product.

| Eigenschap      | Type                                                          | Description                                                                      |
|---------------|---------------------------------------------------------------|----------------------------------------------------------------------------------|
| customerId    | tekenreeks                                                        | Een tekenreeks in GUID-indeling die de klant identificeert.                            |
| productFamily | tekenreeks                                                        | De productfamilie waarvoor de upgrade is aangevraagd.                       |
| isEligible    | booleaans                                                          | De waarde van hetool geeft aan of de klant in aanmerking komt voor de aangevraagde upgrade. |
| upgradeId     | tekenreeks                                                        | De upgrade-id als er al een productupgrade voor een bepaalde familie is uitgevoerd.        |
| reason        | tekenreeks                                                        | De reden waarom de klant niet in aanmerking komt voor productupgrade.                |
| productFamily | tekenreeks                                                        | De productfamilie waarvoor de upgrade is aangevraagd.                       |
| kenmerken    | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                                                         |

## <a name="productupgradesstatus"></a>ProductUpgradesStatus

De **resource ProductUpgradesStatus** bevat informatie over de status van een productupgrade.

| Eigenschap | Type   | Description                                          |
|----------|--------|------------------------------------------------------|
| Id       | tekenreeks | Een tekenreeks met GUID-indeling die de upgrade identificeert. |
| productFamily       | tekenreeks                                                         | De productfamilie waarvoor de upgrade is aangevraagd.
| status              | tekenreeks                                                         | De status van de productupgrade.
| lineItems           | matrix van [UpgradesLineItem-resources](#upgradeslineitem)       | Een matrix met objecten die informatie biedt over de upgradedetails voor elk regelitem dat deel uitmaakte van de aanvraag body.
| errorDetails        | [ErrorDetails-resource](#errordetails)                         | De foutdetails voor de aangevraagde upgrade.
| kenmerken          | [ResourceAttributes](utility-resources.md#resourceattributes)  | De metagegevenskenmerken. |

## <a name="upgradeslineitem"></a>UpgradesLineItem

De **resource UpgradesLineItem** beschrijft de status van de details van de productupgrade voor elk regelitem van de aanvraag.

| Eigenschap      | Type                                                          | Description                                       |
|---------------|---------------------------------------------------------------|---------------------------------------------------|
| sourceProduct | [UpgradeProduct-object](#upgradeproduct)                      | Informatie over het bronproduct dat wordt bijgewerkt. |
| targetProduct | [UpgradeProduct-object](#upgradeproduct)                      | Informatie over het doelproduct na de upgrade.   |
| upgradedDate  | tekenreeks in UTC-datum/tijd-indeling                                | De datum waarop het abonnement is bijgewerkt.           |
| status        | tekenreeks                                                        | De status van de productupgrade.                |
| errorDetails  | [ErrorDetails-resource](#errordetails)                        | De foutdetails voor de aangevraagde upgrade.          |
| kenmerken    | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                          |

## <a name="upgradeproduct"></a>UpgradeProduct

De **Resource UpgradeProduct** bevat informatie over het product dat wordt bijgewerkt.

| Eigenschap   | Type                                                          | Beschrijving                                          |
|------------|---------------------------------------------------------------|------------------------------------------------------|
| id         | tekenreeks                                                        | Een tekenreeks in GUID-indeling die het product identificeert. |
| naam       | tekenreeks                                                        | De gebruiksvriendelijke naam van het product dat wordt bijgewerkt.         |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                             |

## <a name="errordetails"></a>ErrorDetails

De **resource ErrorDetails** biedt details over fouten tijdens het upgradeproces.

| Eigenschap   | Type                                                          | Description                                       |
|------------|---------------------------------------------------------------|---------------------------------------------------|
| code       | tekenreeks                                                        | Een foutcode wanneer de productupgrade mislukt.      |
| message    | tekenreeks                                                        | Het foutbericht wanneer de productupgrade mislukt. |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                          |
