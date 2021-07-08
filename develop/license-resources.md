---
title: Licentiebronnen
description: Beschrijft resources met betrekking tot licenties.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 27d44f89ac89f365e77e073c425ca45ab3638c68
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548393"
---
# <a name="license-resources"></a>Licentiebronnen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Beschrijft resources met betrekking tot licenties.

## <a name="license"></a>Licentie

Beschrijft een gebruikerslicentie.

>[!NOTE]
>Niet ondersteund op Partner Center beheerd door 21Vianet.

| Eigenschap     | Type                                                           | Beschrijving                                                    |
|--------------|----------------------------------------------------------------|----------------------------------------------------------------|
| servicePlans | matrix van ServicePlan-resources                                 | De verzameling serviceplannen die overeenkomen met de licentie |
| productSKU   | ProductSku                                                     | De SKU van het product dat overeenkomt met de licentie.        |
| kenmerken   | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met de licentie.          |

## <a name="licenseupdate"></a>LicenseUpdate

Bevat informatie die wordt gebruikt voor het toewijzen of verwijderen van licenties aan een gebruiker.

| Eigenschap         | Type                                                           | Beschrijving                                               |
|------------------|----------------------------------------------------------------|-----------------------------------------------------------|
| licensestoAssign | matrix van objecten                                               | Matrix van [LicenseAssignment-objecten.](#licenseassignment) |
| licensesToRemove | tekenreeksmatrix                                               | De product-SKU-id's van de licenties die moeten worden verwijderd.    |
| licenseWarnings  | matrix van objecten                                               | Matrix van [LicenseWarning-objecten.](#licensewarning)       |
| kenmerken       | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                                  |

## <a name="licenseassignment"></a>LicenseAssignment

Bevat informatie die nodig is voor een licentie-updatebewerking.

| Eigenschap      | Type             | Beschrijving                                                                |
|---------------|------------------|----------------------------------------------------------------------------|
| excludedPlans | tekenreeksmatrix | De serviceplan-id's die moeten worden uitgesloten van beschikbaarheid voor de gebruiker. |
| skuId         | tekenreeks           | De product-SKU-id voor de licentie.                                |

## <a name="licensewarning"></a>LicentieWarning

Bevat waarschuwingsinformatie die is opgetreden tijdens een licentie-updatebewerking.

| Eigenschap     | Type             | Beschrijving                                         |
|--------------|------------------|-----------------------------------------------------|
| code         | tekenreeks           | De waarschuwingscode.                                   |
| message      | tekenreeks           | Het waarschuwingsbericht.                                |
| servicePlans | tekenreeksmatrix | De namen van het serviceplan die aan de waarschuwing zijn gekoppeld. |

## <a name="productsku"></a>ProductSku

Beschrijft productdetails.

| Eigenschap       | Type             | Beschrijving                                         |
|----------------|------------------|-----------------------------------------------------|
| id             | tekenreeks           | De product-id.                             |
| naam           | tekenreeks           | De principal-id van de gebruiker.                      |
| skuPartNumber  | tekenreeks           | De nummernaam van het SKU-onderdeel voor het product. Voor een abonnement Office 365 E3 is deze waarde `EnterprisePack` bijvoorbeeld . Deze eigenschap kan worden gebruikt in plaats van id als de id niet beschikbaar is.                |
| targetType     | tekenreeks           | Het doeltype van het product. Deze eigenschap geeft aan of het product van toepassing is op een `User` of een `Tenant` .                                                                    |
| licenseGroupId | tekenreeks           | Identificeert via een groeps-id de instantie of service die de productSku-licentie beheert. Producten worden gescheiden onder licentiegroepen voor betere beheerbaarheid.<br/><br/>                                                                                     `group1`- Alle producten waarvan de licenties kunnen worden beheerd door Azure Active Directory (AAD).<br/><br/>                                            `group2`- Minecraft productlicenties.                                         |

## <a name="serviceplan"></a>ServicePlan

Identificeert een implementeerbare service binnen een product-SKU. Een product kan veel serviceplannen hebben.

| Eigenschap         | Type   | Beschrijving                                                                                                       |
|------------------|--------|-------------------------------------------------------------------------------------------------------------------|
| id               | tekenreeks | De id van het serviceplan.                                                                                      |
| displayName      | tekenreeks | De gelokaliseerde weergavenaam voor het serviceplan.                                                                  |
| Servicenaam      | tekenreeks | De servicenaam.                                                                                                 |
| capabilityStatus | tekenreeks | De status van het serviceplan van het serviceplan.                                                                      |
| targetType       | tekenreeks | Het doeltype van het serviceplan. Deze eigenschap geeft aan of het product van toepassing is op een 'Gebruiker' of 'Tenant'. |

## <a name="subscribedsku"></a>SubscribedSku

Beschrijft een geabonneerd product dat eigendom is van een tenant.

| Eigenschap         | Type                                                           | Beschrijving                                                                                       |
|------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| availableUnits   | geheel getal                                                        | Het aantal eenheden dat beschikbaar is voor toewijzing. Deze waarde wordt berekend als totaal aantal eenheden - verbruikte eenheden. |
| activeUnits      | geheel getal                                                        | Het aantal eenheden dat actief is voor toewijzing.                                                        |
| consumedUnits    | geheel getal                                                        | Het aantal verbruikte eenheden.                                                                     |
| suspendedUnits   | geheel getal                                                        | Het aantal eenheden dat is opgeschort.                                                                    |
| totalUnits       | geheel getal                                                        | Het totale aantal eenheden. Deze waarde wordt berekend als de som van de actieve en waarschuwingseenheden.         |
| warningUnits     | geheel getal                                                        | Het aantal waarschuwingseenheden.                                                                      |
| productSku       | ProductSku                                                     | De product-SKU.                                                                                  |
| servicePlans     | matrix van ServicePlan-resources                                 | De verzameling serviceplannen van een product.                                                     |
| capabilityStatus | tekenreeks                                                         | De SKU-status van een product.                                                                      |
| kenmerken       | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met de resource.                                            |
