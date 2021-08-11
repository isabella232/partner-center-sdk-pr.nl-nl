---
title: Relaties van resources
description: Beschrijft resources die betrekking hebben op relaties.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bbbc973679ae80c3ad6b9d67945c6fbcb087789484939b67f8d8a6b538ce7d37
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997087"
---
# <a name="relationships-resources"></a>Relaties van resources

Beschrijft resources die betrekking hebben op relaties.

## <a name="partnerrelationship"></a>PartnerRelationship

Vertegenwoordigt een relatie tussen twee partners.

| Eigenschap         | Type                                                           | Beschrijving                                                                                                                                    |
|------------------|----------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------|
| id               | tekenreeks                                                         | De partner-id. De partner-id geeft de tenant-id op van de partner die zich aan de ontvangerszijde (van) de relatie heeft. |
| location         | tekenreeks                                                         | De locatie van de partner.                                                                                                                   |
| mpnId            | tekenreeks                                                         | De Microsoft Partner Network (MPN) van de partner.                                                                                 |
| naam             | tekenreeks                                                         | De naam van de partner.                                                                                                                       |
| relationshipType | tekenreeks                                                         | Het type relatie.                                                                                                                      |
| staat            | tekenreeks                                                         | De status van de relatie (bijvoorbeeld `active` ).                                                                                                 |
| kenmerken       | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                                                                                                                       |

## <a name="relationshiprequest"></a>RelationshipRequest

Biedt de URL waarmee een klant een relatie met een partner kan opzetten.

| Eigenschap   | Type                                                           | Description                   |
|------------|----------------------------------------------------------------|-------------------------------|
| url        | tekenreeks                                                         | De URL van de relatieaanvraag. |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.      |
