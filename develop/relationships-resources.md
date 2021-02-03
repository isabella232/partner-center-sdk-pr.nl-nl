---
title: Relaties resources
description: Hierin worden de resources met betrekking tot relaties beschreven.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c5701414bd704b375dc23859b920609d5a975d9f
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767220"
---
# <a name="relationships-resources"></a>Relaties resources

**Van toepassing op**

- Partnercentrum

Hierin worden de resources met betrekking tot relaties beschreven.

## <a name="partnerrelationship"></a>PartnerRelationship

Vertegenwoordigt een relatie tussen twee partners.

| Eigenschap         | Type                                                           | Beschrijving                                                                                                                                    |
|------------------|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| id               | tekenreeks                                                         | De partner-id. De partner-id geeft de Tenant-id van de partner op die zich in de ontvanger (aan) zijde van de relatie bevindt. |
| location         | tekenreeks                                                         | De locatie van de partner.                                                                                                                   |
| mpnId            | tekenreeks                                                         | De Microsoft Partner Network-ID (MPN) van de partner.                                                                                 |
| naam             | tekenreeks                                                         | De naam van de partner.                                                                                                                       |
| relationshipType | tekenreeks                                                         | Het type relatie.                                                                                                                      |
| staat            | tekenreeks                                                         | De status van de relatie (bijvoorbeeld `active` ).                                                                                                 |
| kenmerken       | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.                                                                                                                       |

## <a name="relationshiprequest"></a>RelationshipRequest

Biedt de URL waarmee een klant een relatie met een partner kan maken.

| Eigenschap   | Type                                                           | Description                   |
|------------|----------------------------------------------------------------|-------------------------------|
| url        | tekenreeks                                                         | De relatie aanvraag-URL. |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.      |
