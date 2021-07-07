---
title: Resources voor klantgebruik
description: Resources voor klanten met abonnementen op basis van gebruik en budgetten voor maandelijks gebruik (waaronder CustomerMonthlyUsageRecord, CustomerUsageSummary, PartnerUsageSummary en SpendingBudget).
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: eae516e2f759dfc2e8f80e946a835d70760c5c9e
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973040"
---
# <a name="customer-usage-resources"></a>Resources voor klantgebruik

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Klanten met een abonnement op basis van gebruik hebben mogelijk een maandelijks gebruiksbudget. Met dit budget stelt u een limiet in voor het maximumgebruik van de klant en kan de partner het gebruik in de tijd bijhouden.

> [!NOTE]
> Klantgebruiksnummers zijn schattingen (geen eindwaarden), die niet mogen worden gebruikt voor factureringsdoeleinden.

## <a name="customermonthlyusagerecord"></a>CustomerMonthlyUsageRecord

**CustomerMonthlyUsageRecord vertegenwoordigt** de geschatte monetaire kosten van het gebruik van een klant in de huidige maand.

| Eigenschap         | Type               | Beschrijving                                                              |
|------------------|--------------------|--------------------------------------------------------------------------|
| Budget           | UitgavenBudget     | Het bestedingsbudget dat aan de klant is toegewezen.                          |
| PercentUsed      | decimal             | Het percentage dat is gebruikt buiten het toegewezen budget.                        |
| ResourceId       | tekenreeks             | De unieke id van de resource.                                   |
| ResourceName     | tekenreeks             | De naam van de resource.                                                |
| TotalCost        | decimal             | De geschatte totale gebruikskosten voor de resources in het abonnement.|
| CurrencyLocale   | tekenreeks             | De valutavaluta van de klant. Beschikbaar voor Microsoft Azure (MS-AZR-0145P) abonnementen.            |
| CurrencyCode     | tekenreeks             | Hiermee haalt u de valutacode op of stelt u deze in. Beschikbaar voor Azure-abonnementen.           |
| USDTotalCost     | decimal             | Haalt de geschatte totale kosten in USD op of stelt deze in. Beschikbaar voor Azure-abonnementen.                                         |
| IsUpgraded       | booleaans             | Hiermee haalt u een waarde op of stelt u in die aangeeft of het Azure-abonnement van de klant is bijgewerkt. De waarde **true vertegenwoordigt** klanten die een Azure-plan hebben.                         |
| LastModifiedDate | date               | De datum waarop de gebruiksgegevens het laatst zijn gewijzigd.                               |
| Kenmerken       | ResourceAttributes | De metagegevenskenmerken die overeenkomen met de gebruiksrecord.               |

## <a name="customerusagesummary"></a>CustomerUsageSummary

**CustomerUsageSummary** vertegenwoordigt een samenvatting van het gebruik van de klant voor een hele factureringsperiode.

| Eigenschap         | Type               | Beschrijving                                                                                                      |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------|
| Budget           | UitgavenBudget     | Het bestedingsbudget dat aan de klant is toegewezen.                                                                  |
| ResourceId       | tekenreeks             | De unieke id van de resource. In de context van CustomerMonthlyUsageRecord is deze id de klant-id. |
| ResourceName     | tekenreeks             | De naam van de resource. In de context van CustomerMonthlyUsageRecord is dit de naam van de klant.               |
| BillingStartDate | date               | De begindatum van de huidige factureringsperiode.                                                                    |
| BillingEndDate   | date               | De einddatum van de huidige factureringsperiode.                                                                      |
| TotalCost        | decimal             | De geschatte totale gebruikskosten voor de resources in het abonnement.                                         |
| CurrencyLocale   | tekenreeks             | De valutavaluta van de klant. Beschikbaar voor Microsoft Azure (MS-AZR-0145P) abonnementen.                                         |
| CurrencyCode     | tekenreeks             | Hiermee haalt u de valutacode op of stelt u deze in. Beschikbaar voor Azure-abonnementen.                                         |
| USDTotalCost     | decimal             | Haalt de geschatte totale kosten in USD op of stelt deze in. Beschikbaar voor azure-abonnementsbronnen.                                         |
| LastModifiedDate | date               | De datum waarop de gebruiksgegevens het laatst zijn gewijzigd.                                                                       |
| Koppelingen            | ResourceLinks      | De resourcekoppelingen die overeenkomen met het gebruiksoverzicht.                                                           |
| Kenmerken       | ResourceAttributes | De metagegevenskenmerken die overeenkomen met het gebruiksoverzicht.                                                      |

## <a name="partnerusagesummary"></a>PartnerUsageSummary

**PartnerUsageSummary** vertegenwoordigt een samenvatting op partnerniveau van gebruiksbudgetten voor alle klanten.

| Eigenschap         | Type               | Beschrijving                                                                                                      |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------|
| EmailsToNotify   | tekenreeksmatrix   | De lijst met e-mailadressen voor meldingen.                                                                   |
| CustomerOverBudget | geheel getal          | Het aantal klanten dat boven budget is.                                                                    |
| CustomersTrendingOver | geheel getal       | Het aantal klanten dat bijna boven het budget uit komt.                                                     |
| CustomersWithUsageBasedSubscriptions  | geheel getal | Het aantal klanten met een abonnement op basis van gebruik.                                               |
| ResourceId       | tekenreeks             | De unieke id van de resource. In de context van CustomerMonthlyUsageRecord is deze id de klant-id. |
| ResourceName     | tekenreeks             | De naam van de resource. In de context van CustomerMonthlyUsageRecord is dit de naam van de klant.               |
| BillingStartDate | date               | De begindatum van de huidige factureringsperiode.                                                                    |
| BillingEndDate   | date               | De einddatum van de huidige factureringsperiode.                                                                      |
| TotalCost        | decimal             | De geschatte totale kosten van al het klantgebruik op basis van het huidige gebruik vanaf het begin van de factureringsperiode.      |
| CurrencyLocale   | tekenreeks             | De valuta-locale.                                                                                             |
| LastModifiedDate | date               | De datum waarop de gebruiksgegevens het laatst zijn gewijzigd.                                                                       |
| Koppelingen            | ResourceLinks      | De resourcekoppelingen die overeenkomen met het gebruiksoverzicht.                                                           |
| Kenmerken       | ResourceAttributes | De metagegevenskenmerken die overeenkomen met het gebruiksoverzicht.                                                      |

## <a name="spendingbudget"></a>UitgavenBudget

**UitgavenBudget** vertegenwoordigt het budget dat aan deze klant is toegewezen voor abonnementen op basis van gebruik.

| Eigenschap   | Type               | Beschrijving                                                                                         |
|------------|--------------------|-----------------------------------------------------------------------------------------------------|
| Bedrag     | decimal             | Het toegewezen budget. Als de waarde null is, wordt er geen bestedingsbudget toegewezen aan deze klant. |
| Kenmerken | ResourceAttributes | De metagegevenskenmerken die overeenkomen met het budget.                                                |
