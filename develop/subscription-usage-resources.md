---
title: Gebruiks resources voor abonnementen
description: Met resources voor abonnements gebruik worden abonnementen beschreven met facturering op basis van gebruik. Deze abonnementen hebben dagelijkse en maandelijkse gebruiks records, samen met een samen vatting van gebruik voor elke salaris periode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8e23287d80f19084860f4597754448e81c01049f
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767242"
---
# <a name="subscription-usage-resources"></a>Gebruiks resources voor abonnementen

**Van toepassing op:**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

U kunt de volgende bronnen gebruiken om gebruiks gegevens te verkrijgen voor een specifiek abonnement met facturering op basis van gebruik. Deze abonnementen hebben dagelijkse en maandelijkse gebruiks records, samen met een samen vatting van gebruik voor elke salaris periode.

## <a name="subscriptiondailyusagerecord"></a>SubscriptionDailyUsageRecord

*De **SubscriptionDailyUsageRecord** -resource is verouderd en kan onnauwkeurige resultaten opleveren. We raden u aan uw toepassingen bij te werken voor het gebruik van de Api's die worden beschreven in de [gebruiks gegevens van een klant ophalen voor Azure](get-a-customer-s-utilization-record-for-azure.md) en in plaats daarvan [prijzen voor Microsoft Azure krijgen](get-prices-for-microsoft-azure.md) .*

De **SubscriptionDailyUsageRecord** -resource beschrijft hoeveel een abonnement op één dag wordt gebruikt.

| Eigenschap         | Type               | Description                                                                                   |
|------------------|--------------------|-----------------------------------------------------------------------------------------------|
| DateUsed         | tekenreeks             | De dag, in datum-tijd notatie, waarmee het abonnement is gebruikt.                                 |
| ResourceId       | tekenreeks             | GPT. De unieke ID van de resource.                                                          |
| ResourceName     | tekenreeks             | De naam van de resource.                                                                     |
| Totale        | decimal             | De geschatte totale kosten voor het gebruik van de resources in het abonnement op de opgegeven dag.     |
| CurrencyLocale   | tekenreeks             | De land instelling waarin het abonnement is gebruikt, bepaalt de valuta die op de factuur moet worden gebruikt. |
| LastModifiedDate | tekenreeks             | De dag, in datum-tijd notatie, waarop deze record voor het laatst is gewijzigd.                             |
| Kenmerken       | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de resource.                                        |

## <a name="subscriptionmonthlyusagerecord"></a>SubscriptionMonthlyUsageRecord

De **SubscriptionMonthlyUsageRecord** -resource beschrijft hoeveel een abonnement wordt gebruikt in één maand.

| Eigenschap         | Type               | Beschrijving                                                                                   |
|------------------|--------------------|-----------------------------------------------------------------------------------------------|
| Status           | tekenreeks             | De status van het abonnement: ' none ', ' Active ', ' Suspended ' of ' deleted '.                  |
| PartnerOnRecord  | tekenreeks             | "De MPN-ID van de partner op record."                                                        |
| OfferId          | tekenreeks             | GPT. De id van de aanbieding met betrekking tot dit abonnement.                                       |
| Id               | tekenreeks             | GPT. De id van het abonnement of de resource.                                                 |
| Name             | tekenreeks             | De naam van het abonnement of de resource.                                                     |
| Totale        | decimal             | De geschatte totale kosten voor het gebruik van de resources in het abonnement in de opgegeven maand.   |
| CurrencyLocale   | tekenreeks             | De land instelling waarin het abonnement is gebruikt, bepaalt de valuta die op de factuur moet worden gebruikt. Beschikbaar voor Microsoft Azure-abonnementen (MS-AZR-0145P). |
| CurrencyCode     | tekenreeks             | Hiermee wordt de valuta code opgehaald of ingesteld. Beschikbaar voor Azure Plan-resources voor abonnementen.                                         |
| USDTotalCost     | decimal             | Hiermee worden de geschatte totale kosten in USD opgehaald of ingesteld. Beschikbaar voor Azure-abonnementen.                                         |
| LastModifiedDate | tekenreeks             | De dag, in datum-tijd notatie, waarop deze record voor het laatst is gewijzigd.                             |
| Kenmerken       | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de resource.                                        |

## <a name="subscriptionusagesummary"></a>SubscriptionUsageSummary

De **SubscriptionUsageSummary** -resource beschrijft hoeveel een specifiek abonnement is gebruikt in de huidige facturerings periode.

| Eigenschap         | Type               | Description                                                                                                            |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------------|
| ResourceId       | tekenreeks             | GPT. De id van het abonnement of de resource. In de context van CustomerMonthlyUsageRecord is deze id de klant-id. |
| ResourceName     | tekenreeks             | De naam van het abonnement of de resource. In de context van CustomerMonthlyUsageRecord is deze naam de naam van de klant. |
| BillingStartDate | date               | De begin datum van de huidige facturerings periode, in datum-tijd notatie.                                                     |
| BillingEndDate   | date               | De eind datum van de huidige facturerings periode, in datum-tijd notatie.                                                       |
| Totale        | double             | De geschatte totale kosten voor het gebruik van de resources in het abonnement tijdens de opgegeven facturerings periode.               |
| CurrencyLocale   | tekenreeks             | De land instelling waarin het abonnement is gebruikt, bepaalt de valuta die op de factuur moet worden gebruikt. Beschikbaar voor Microsoft Azure-abonnementen (MS-AZR-0145P). |
| CurrencyCode   | tekenreeks             | Hiermee wordt de valuta code opgehaald of ingesteld. Beschikbaar voor Azure-abonnementen.                                         |
| USDTotalCost   | decimal             | Hiermee worden de geschatte totale kosten in USD opgehaald of ingesteld. Beschikbaar voor Azure Plan-resources voor abonnementen.                                         |
| LastModifiedDate | tekenreeks             | De dag, in datum-tijd notatie, waarop deze record voor het laatst is gewijzigd.                                                      |
| Koppelingen            | ResourceLinks      | De resource koppelingen die overeenkomen met de SubscriptionUsageSummary.                                                      |
| Kenmerken       | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de SubscriptionUsageSummary.                                                 |
