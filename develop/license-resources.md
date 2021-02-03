---
title: Licentie bronnen
description: Beschrijft bronnen die betrekking hebben op licenties.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 681f53ec73122a4861e6f1a2f96560336481a068
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767423"
---
# <a name="license-resources"></a>Licentie bronnen

**Van toepassing op**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Beschrijft bronnen die betrekking hebben op licenties.

## <a name="license"></a>Licentie

Beschrijft een gebruikers licentie.

>[!NOTE]
>Niet ondersteund in een partner centrum dat wordt beheerd door 21Vianet.

| Eigenschap     | Type                                                           | Description                                                    |
|--------------|----------------------------------------------------------------|----------------------------------------------------------------|
| servicePlans | matrix van ServicePlan-resources                                 | De verzameling service plannen die overeenkomen met de licentie |
| productSKU   | ProductSku                                                     | De SKU van het product dat overeenkomt met de licentie.        |
| kenmerken   | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met de licentie.          |

## <a name="licenseupdate"></a>LicenseUpdate

Bevat informatie die wordt gebruikt voor het toewijzen of verwijderen van licenties van een gebruiker.

| Eigenschap         | Type                                                           | Description                                               |
|------------------|----------------------------------------------------------------|-----------------------------------------------------------|
| licensestoAssign | matrix van objecten                                               | Matrix van [LicenseAssignment](#licenseassignment) -objecten. |
| licensesToRemove | tekenreeksmatrix                                               | De product-SKU-id's van de licenties die moeten worden verwijderd.    |
| licenseWarnings  | matrix van objecten                                               | Matrix van [LicenseWarning](#licensewarning) -objecten.       |
| kenmerken       | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.                                  |

## <a name="licenseassignment"></a>LicenseAssignment

Bevat informatie die nodig is voor de bewerking van een licentie-update.

| Eigenschap      | Type             | Description                                                                |
|---------------|------------------|----------------------------------------------------------------------------|
| excludedPlans | tekenreeksmatrix | De service plan-id's die moeten worden uitgesloten van de beschik baarheid van de gebruiker. |
| skuId         | tekenreeks           | De product-SKU-id voor de licentie.                                |

## <a name="licensewarning"></a>LicenseWarning

Bevat informatie over waarschuwingen die zijn opgetreden tijdens een licentie-update bewerking.

| Eigenschap     | Type             | Description                                         |
|--------------|------------------|-----------------------------------------------------|
| code         | tekenreeks           | De waarschuwings code.                                   |
| message      | tekenreeks           | Het waarschuwings bericht.                                |
| servicePlans | tekenreeksmatrix | De namen van de service plannen die aan de waarschuwing zijn gekoppeld. |

## <a name="productsku"></a>ProductSku

Beschrijft product gegevens.

| Eigenschap       | Type             | Beschrijving                                         |
|----------------|------------------|-----------------------------------------------------|
| id             | tekenreeks           | De product-id.                             |
| naam           | tekenreeks           | De principal-id van de gebruiker.                      |
| skuPartNumber  | tekenreeks           | De nummer naam van het SKU-onderdeel voor het product. Voor Office 365-abonnement E3 is deze waarde bijvoorbeeld `EnterprisePack` . Deze eigenschap kan worden gebruikt in plaats van id als de id niet beschikbaar is.                |
| Target     | tekenreeks           | Het doel type van het product. Deze eigenschap geeft aan of het product van toepassing is op een `User` of een `Tenant` .                                                                    |
| licenseGroupId | tekenreeks           | Identificeert via een groeps-id van de instantie of service die de productSku-licentie beheert. Producten worden gescheiden onder licentie groepen voor betere beheer baarheid.<br/><br/>                                                                                     `group1` -Alle producten waarvan de licenties kunnen worden beheerd door Azure Active Directory (AAD).<br/><br/>                                            `group2` -Minecraft product licenties.                                         |

## <a name="serviceplan"></a>ServicePlan

Identificeert een Implementeer bare service binnen een product-SKU. Een product kan veel service abonnementen hebben.

| Eigenschap         | Type   | Beschrijving                                                                                                       |
|------------------|--------|-------------------------------------------------------------------------------------------------------------------|
| id               | tekenreeks | De id van het service abonnement.                                                                                      |
| displayName      | tekenreeks | De gelokaliseerde weergave naam voor het service plan.                                                                  |
| serviceName      | tekenreeks | De naam van de service.                                                                                                 |
| capabilityStatus | tekenreeks | De status van het service plan van het service plan.                                                                      |
| Target       | tekenreeks | Het doel type van het service plan. Deze eigenschap geeft aan of het product van toepassing is op een gebruiker of een Tenant. |

## <a name="subscribedsku"></a>SubscribedSku

Beschrijft een geabonneerd product dat eigendom is van een Tenant.

| Eigenschap         | Type                                                           | Description                                                                                       |
|------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| availableUnits   | geheel getal                                                        | Het aantal eenheden dat beschikbaar is voor toewijzing. Deze waarde wordt berekend als totaal aantal eenheden-verbruikte eenheden. |
| activeUnits      | geheel getal                                                        | Het aantal eenheden dat actief is voor toewijzing.                                                        |
| consumedUnits    | geheel getal                                                        | Het aantal verbruikte eenheden.                                                                     |
| suspendedUnits   | geheel getal                                                        | Het aantal onderbroken eenheden.                                                                    |
| totalUnits       | geheel getal                                                        | Het totale aantal eenheden. Deze waarde wordt berekend als de som van de actieve en waarschuwings eenheden.         |
| warningUnits     | geheel getal                                                        | Het aantal waarschuwings eenheden.                                                                      |
| productSku       | ProductSku                                                     | De product-SKU.                                                                                  |
| servicePlans     | matrix van ServicePlan-resources                                 | De verzameling van service plannen van een product.                                                     |
| capabilityStatus | tekenreeks                                                         | De SKU-status van een product.                                                                      |
| kenmerken       | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met de resource.                                            |
