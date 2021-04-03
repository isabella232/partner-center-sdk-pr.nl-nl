---
title: Resource gebruik-record resources
description: U kunt de ResourceUsageRecord-Resource gebruiken om de geschatte monetaire kosten te beschrijven van het resource niveau gebruik van een abonnement in de huidige facturerings cyclus.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b0a28620eec86e86630aef93b13f26c9dd675a5d
ms.sourcegitcommit: faea78fe3264cbafc2b02c04d98d5ce30e992124
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2021
ms.locfileid: "106274560"
---
# <a name="resource-usage-record-resources"></a>Resource gebruik-record resources

**Van toepassing op:**

- Partnercentrum

U kunt de **ResourceUsageRecord** -Resource gebruiken om de geschatte monetaire kosten te beschrijven van het resource niveau gebruik van een abonnement in de huidige facturerings cyclus.

## <a name="resourceusagerecord"></a>ResourceUsageRecord

| Eigenschap          | Type               | Beschrijving                                                                                                                                                                                                |
|-------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SubscriptionId    | tekenreeks             | Hiermee wordt de abonnements-id opgehaald of ingesteld. Voor Microsoft Azure-abonnementen (MS-AZR-0145P) is deze waarde de commerce-abonnements-id. Voor Azure-abonnementen is deze waarde de Azure plan-id). |
| ResourceUri       | tekenreeks             | Hiermee wordt de resource-URI opgehaald of ingesteld.                                                                                                                                                                            |
| ResourceType      | tekenreeks             | Hiermee wordt het bron type opgehaald of ingesteld.                                                                                                                                                                            |
| EntitlementId     | tekenreeks             | Hiermee wordt de recht-id (de Azure-abonnement-id) opgehaald of ingesteld.                                                                                                                               |
| Rechtnaam   | tekenreeks             | Hiermee wordt de naam van de rechten opgehaald of ingesteld.                                                                                                                                                                         |
| ResourceGroupName | double             | Hiermee wordt de naam van de resource groep opgehaald of ingesteld.                                                                                                                                                                      |
| Name              | tekenreeks             | De naam van de resource.                                                                                                                                                                                  |
| ResourceName      | tekenreeks             | Hiermee wordt de naam van de resource opgehaald of ingesteld.                                                                                                                                                                     |
| Totale         | decimal            | Hiermee wordt het geschatte totale kosten gebruik opgehaald of ingesteld.                                                                                                                                                               |
| CurrencyCode      | tekenreeks             | Hiermee wordt de valuta code opgehaald of ingesteld.                                                                                                                                                                            |
| USDTotalCost      | decimal            | Hiermee worden de geschatte totale kosten in USD opgehaald of ingesteld.                                                                                                                                                              |
| LastModifiedDate  | tekenreeks             | De dag (in datum-tijd notatie) waarop deze record voor het laatst is gewijzigd.                                                                                                                                          |
| Kenmerken        | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de resource.                                                                                                                                                     |
