---
title: Resources voor abonnementsgebruik
description: Resources voor abonnementsgebruik beschrijven abonnementen met facturering op basis van gebruik. Deze abonnementen hebben dagelijkse en maandelijkse gebruiksrecords, samen met een gebruiksoverzicht voor elke betaalperiode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: dcb24dcf5ca8165ec23c4b187def38d05772e1de
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547373"
---
# <a name="subscription-usage-resources"></a>Resources voor abonnementsgebruik

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

U kunt de volgende resources voor abonnementsgebruik gebruiken om gebruiksgegevens op te halen voor een specifiek abonnement met facturering op basis van gebruik. Deze abonnementen hebben dagelijkse en maandelijkse gebruiksrecords, samen met een gebruiksoverzicht voor elke betaalperiode.

## <a name="subscriptiondailyusagerecord"></a>SubscriptionDailyUsageRecord

*De **resource SubscriptionDailyUsageRecord** is verouderd en kan onnauwkeurige resultaten opleveren. U wordt aangeraden uw toepassingen bij te werken voor het gebruik van de [API's](get-a-customer-s-utilization-record-for-azure.md) die worden beschreven in Gebruiksrecords van een klant voor Azure downloaden en prijzen voor [Microsoft Azure.](get-prices-for-microsoft-azure.md)*

In **de resource SubscriptionDailyUsageRecord** wordt beschreven hoeveel een abonnement op één dag wordt gebruikt.

| Eigenschap         | Type               | Beschrijving                                                                                   |
|------------------|--------------------|-----------------------------------------------------------------------------------------------|
| DateUsed         | tekenreeks             | De dag, in datum/tijd-indeling, waarop het abonnement is gebruikt.                                 |
| ResourceId       | tekenreeks             | Guid. De unieke id van de resource.                                                          |
| ResourceName     | tekenreeks             | De naam van de resource.                                                                     |
| TotalCost        | decimal             | De geschatte totale kosten voor het gebruik van de resources in het abonnement op de opgegeven dag.     |
| CurrencyLocale   | tekenreeks             | De lokatie waarin het abonnement is gebruikt, bepaalt de valuta die op de factuur moet worden gebruikt. |
| LastModifiedDate | tekenreeks             | De dag, in datum/tijd-indeling, waarop deze record voor het laatst is gewijzigd.                             |
| Kenmerken       | ResourceAttributes | De metagegevenskenmerken die overeenkomen met de resource.                                        |

## <a name="subscriptionmonthlyusagerecord"></a>SubscriptionMonthlyUsageRecord

De **resource SubscriptionMonthlyUsageRecord** beschrijft hoeveel een abonnement in één maand wordt gebruikt.

| Eigenschap         | Type               | Beschrijving                                                                                   |
|------------------|--------------------|-----------------------------------------------------------------------------------------------|
| Status           | tekenreeks             | De status van het abonnement: 'none', 'active', 'suspended' of 'deleted'.                  |
| PartnerOnRecord  | tekenreeks             | De MPN-id van de partner in record.                                                        |
| OfferId          | tekenreeks             | Guid. De id van de aanbieding die is gerelateerd aan dit abonnement.                                       |
| Id               | tekenreeks             | Guid. De id van het abonnement of de resource.                                                 |
| Name             | tekenreeks             | De naam van het abonnement of de resource.                                                     |
| TotalCost        | decimal             | De geschatte totale kosten voor het gebruik van de resources in het abonnement in de opgegeven maand.   |
| CurrencyLocale   | tekenreeks             | De lokatie waarin het abonnement is gebruikt, bepaalt de valuta die op de factuur moet worden gebruikt. Beschikbaar voor Microsoft Azure (MS-AZR-0145P) abonnementen. |
| CurrencyCode     | tekenreeks             | Haalt de valutacode op of stelt deze in. Beschikbaar voor azure-abonnementsbronnen.                                         |
| USDTotalCost     | decimal             | Haalt de geschatte totale kosten in USD op of stelt deze in. Beschikbaar voor Azure-abonnementen.                                         |
| LastModifiedDate | tekenreeks             | De dag, in datum/tijd-indeling, waarop deze record voor het laatst is gewijzigd.                             |
| Kenmerken       | ResourceAttributes | De metagegevenskenmerken die overeenkomen met de resource.                                        |

## <a name="subscriptionusagesummary"></a>SubscriptionUsageSummary

De **resource SubscriptionUsageSummary** beschrijft hoeveel een specifiek abonnement is gebruikt in de huidige factureringsperiode.

| Eigenschap         | Type               | Beschrijving                                                                                                            |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------------|
| ResourceId       | tekenreeks             | Guid. De id van het abonnement of de resource. In de context van CustomerMonthlyUsageRecord is deze id de klant-id. |
| ResourceName     | tekenreeks             | De naam van het abonnement of de resource. In de context van CustomerMonthlyUsageRecord is deze naam de naam van de klant. |
| BillingStartDate | date               | De begindatum van de huidige factureringsperiode, in datum/tijd-indeling.                                                     |
| BillingEndDate   | date               | De einddatum van de huidige factureringsperiode, in datum/tijd-indeling.                                                       |
| TotalCost        | double             | De geschatte totale kosten voor het gebruik van de resources in het abonnement tijdens de opgegeven factureringsperiode.               |
| CurrencyLocale   | tekenreeks             | De lokatie waarin het abonnement is gebruikt, bepaalt de valuta die op de factuur moet worden gebruikt. Beschikbaar voor Microsoft Azure (MS-AZR-0145P) abonnementen. |
| CurrencyCode   | tekenreeks             | Hiermee haalt u de valutacode op of stelt u deze in. Beschikbaar voor Azure-abonnementen.                                         |
| USDTotalCost   | decimal             | Haalt de geschatte totale kosten op in USD of stelt deze in. Beschikbaar voor azure-abonnementsbronnen.                                         |
| LastModifiedDate | tekenreeks             | De dag, in datum/tijd-indeling, waarop deze record het laatst is gewijzigd.                                                      |
| Koppelingen            | ResourceLinks      | De resourcekoppelingen die overeenkomen met subscriptionUsageSummary.                                                      |
| Kenmerken       | ResourceAttributes | De metagegevenskenmerken die overeenkomen met subscriptionUsageSummary.                                                 |
