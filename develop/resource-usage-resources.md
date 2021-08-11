---
title: Resourcegebruikrecordresources
description: U kunt de resource ResourceUsageRecord gebruiken om de geschatte monetaire kosten van het resourceniveaugebruik van een abonnement in de huidige factureringscyclus te beschrijven.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b330c49518bc12a63f2be731eef5c57884f5b15b706ce4007bbdf1a7bb8fab0e
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996934"
---
# <a name="resource-usage-record-resources"></a>Resourcegebruikrecordresources

U kunt de **resource ResourceUsageRecord gebruiken** om de geschatte monetaire kosten van het resourceniveaugebruik van een abonnement in de huidige factureringscyclus te beschrijven.

## <a name="resourceusagerecord"></a>ResourceUsageRecord

| Eigenschap          | Type               | Description                                                                                                                                                                                                |
|-------------------|--------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| SubscriptionId    | tekenreeks             | Hiermee haalt u de abonnements-id op of stelt u deze in. Voor Microsoft Azure (MS-AZR-0145P) is deze waarde de commerce-abonnements-id. Voor Azure-abonnementen is deze waarde de id van het Azure-plan). |
| ResourceUri       | tekenreeks             | Haalt de resource-URI op of stelt deze in.                                                                                                                                                                            |
| ResourceType      | tekenreeks             | Hiermee haalt u het resourcetype op of stelt u dit in.                                                                                                                                                                            |
| EntitlementId     | tekenreeks             | Hiermee haalt u de rechten-id (de Azure-abonnements-id) op of stelt u deze in.                                                                                                                               |
| EntitlementName   | tekenreeks             | Hiermee haalt u de rechtennaam op of stelt u deze in.                                                                                                                                                                         |
| ResourceGroupName | double             | Hiermee haalt u de naam van de resourcegroep op of stelt u deze in.                                                                                                                                                                      |
| Name              | tekenreeks             | De naam van de resource.                                                                                                                                                                                  |
| ResourceName      | tekenreeks             | Hiermee haalt u de naam van de resource op of stelt u deze in.                                                                                                                                                                     |
| TotalCost         | decimal            | Hiermee haalt u het geschatte totale kostengebruik op of stelt u dit in.                                                                                                                                                               |
| CurrencyCode      | tekenreeks             | Haalt de valutacode op of stelt deze in.                                                                                                                                                                            |
| USDTotalCost      | decimal            | Haalt de geschatte totale kosten in USD op of stelt deze in.                                                                                                                                                              |
| LastModifiedDate  | tekenreeks             | De dag (in datum/tijd-indeling) waarop deze record voor het laatst is gewijzigd.                                                                                                                                          |
| Kenmerken        | ResourceAttributes | De metagegevenskenmerken die overeenkomen met de resource.                                                                                                                                                     |
