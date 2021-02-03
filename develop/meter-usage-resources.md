---
title: Bron voor gebruik van meter gegevens
description: U kunt de MeterUsageRecord-Resource gebruiken om de geschatte monetaire kosten van het gebruik van het meet niveau van een abonnement in de huidige facturerings cyclus te beschrijven.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8c02c859d1d8ba3edd236d83d3056cb82533f7e8
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767213"
---
# <a name="meter-usage-record-resource"></a>Bron voor gebruik van meter gegevens

**Van toepassing op:**

- Partnercentrum

U kunt de **MeterUsageRecord** -Resource gebruiken om de geschatte monetaire kosten van het gebruik van het meet niveau van een abonnement in de huidige facturerings cyclus te beschrijven.

## <a name="meterusagerecord"></a>MeterUsageRecord

| Eigenschap         | Type               | Description                                                                                   |
|------------------|--------------------|-----------------------------------------------------------------------------------------------|
| SubscriptionId           | tekenreeks             | Een GUID die overeenkomt met de id van een partner centrum- [abonnements resource](subscription-resources.md#subscription), die een Microsoft Azure (MS-AZR-0145P) of een Azure-abonnement vertegenwoordigt. Voor Microsoft Azure (MS-AZR-0145P)-abonnementen is deze waarde de commerce-abonnements-id. Voor Azure-plannen voor abonnements abonnementen is deze waarde de Azure plan-id.                  |
| MeterId  | tekenreeks             | Hiermee wordt de meter-id opgehaald of ingesteld.                                                        |
| MeterName          | tekenreeks             | Hiermee wordt de naam van de meter opgehaald of ingesteld.                                       |
| Categorie               | tekenreeks             | Hiermee wordt de Azure-resource categorie opgehaald of ingesteld.                                                 |
| Subcategorie             | tekenreeks             |  Hiermee wordt de subcategorie van Azure-resource opgehaald of ingesteld.                                                     |
| QuantityUsed        | decimal             | Hiermee wordt de hoeveelheid van de gebruikte Azure-resource opgehaald of ingesteld.   |
| Eenheid   | tekenreeks             | Hiermee wordt de maat eenheid voor de Azure-resource opgehaald of ingesteld. |
| Totale   | decimal             | Hiermee worden de geschatte totale kosten van het gebruik opgehaald of ingesteld. |
| CurrencyLocale   | tekenreeks             | De land instelling waarin het abonnement is gebruikt. Deze eigenschap bepaalt de valuta die op de factuur wordt gebruikt. Deze eigenschap is beschikbaar voor de Microsoft Azure-abonnementen (MS-AZR-0145P). |
| CurrencyCode   | tekenreeks             | Hiermee wordt de valuta code opgehaald of ingesteld. Deze eigenschap is beschikbaar voor Azure-abonnementen.                                         |
| USDTotalCost   | decimal             | Hiermee worden de geschatte totale kosten in USD opgehaald of ingesteld. Deze eigenschap is beschikbaar voor Azure-abonnementen.                                         |
| LastModifiedDate | tekenreeks             | De dag (in datum-tijd notatie) waarop deze record voor het laatst is gewijzigd.                             |
| Kenmerken       | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de resource.                                        |                                           |
