---
title: Resources voor klantgebruik
description: Resources voor klanten met op gebruik gebaseerde abonnementen en maandelijkse gebruiksbudgetten (waaronder CustomerMonthlyUsageRecord, CustomerUsageSummary, PartnerUsageSummary en SpendingBudget).
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 066fd84f872365b419796f00125c097c685f4579731aaacd67e826bf671bd789
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115995149"
---
# <a name="customer-usage-resources"></a>Resources voor klantgebruik

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Klanten met op gebruik gebaseerde abonnementen hebben mogelijk een maandelijks gebruiksbudget. Dit budget stelt een limiet in voor het maximale gebruik van de klant en stelt de partner in staat om het gebruik in de tijd bij te houden.

> [!NOTE]
> Klantgebruiksnummers zijn schattingen (geen eindwaarden), die niet moeten worden gebruikt voor factureringsdoeleinden.

## <a name="customermonthlyusagerecord"></a>CustomerMonthlyUsageRecord

**CustomerMonthlyUsageRecord vertegenwoordigt** de geschatte monetaire kosten van het gebruik van een klant in de huidige maand.

| Eigenschap         | Type               | Description                                                              |
|------------------|--------------------|--------------------------------------------------------------------------|
| Budget           | UitgavenBudget     | Het bestedingsbudget dat aan de klant is toegewezen.                          |
| PercentUsed      | decimal             | Het percentage dat buiten het toegewezen budget wordt gebruikt.                        |
| ResourceId       | tekenreeks             | De unieke id van de resource.                                   |
| ResourceName     | tekenreeks             | De naam van de resource.                                                |
| TotalCost        | decimal             | De geschatte totale gebruikskosten voor de resources in het abonnement.|
| CurrencyLocale   | tekenreeks             | De valutavaluta van de klant. Beschikbaar voor Microsoft Azure (MS-AZR-0145P) abonnementen.            |
| CurrencyCode     | tekenreeks             | Hiermee haalt u de valutacode op of stelt u deze in. Beschikbaar voor Azure-abonnementen.           |
| USDTotalCost     | decimal             | Haalt de geschatte totale kosten op in USD of stelt deze in. Beschikbaar voor Azure-abonnementen.                                         |
| IsUpgraded       | booleaans             | Hiermee haalt u een waarde op of stelt u in of geeft u aan of het Azure-abonnement van de klant is bijgewerkt. De waarde **true vertegenwoordigt** klanten die een Azure-plan hebben.                         |
| LastModifiedDate | date               | De datum waarop de gebruiksgegevens het laatst zijn gewijzigd.                               |
| Kenmerken       | ResourceAttributes | De metagegevenskenmerken die overeenkomen met de gebruiksrecord.               |

## <a name="customerusagesummary"></a>CustomerUsageSummary

**CustomerUsageSummary** vertegenwoordigt een overzicht van het gebruik van de klant voor een hele factureringsperiode.

| Eigenschap         | Type               | Description                                                                                                      |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------|
| Budget           | UitgavenBudget     | Het bestedingsbudget dat aan de klant is toegewezen.                                                                  |
| ResourceId       | tekenreeks             | De unieke id van de resource. In de context van CustomerMonthlyUsageRecord is deze id de klant-id. |
| ResourceName     | tekenreeks             | De naam van de resource. In de context van CustomerMonthlyUsageRecord is dit de naam van de klant.               |
| BillingStartDate | date               | De begindatum van de huidige factureringsperiode.                                                                    |
| BillingEndDate   | date               | De einddatum van de huidige factureringsperiode.                                                                      |
| TotalCost        | decimal             | De geschatte totale gebruikskosten voor de resources in het abonnement.                                         |
| CurrencyLocale   | tekenreeks             | De valutavaluta van de klant. Beschikbaar voor Microsoft Azure (MS-AZR-0145P) abonnementen.                                         |
| CurrencyCode     | tekenreeks             | Hiermee haalt u de valutacode op of stelt u deze in. Beschikbaar voor Azure-abonnementen.                                         |
| USDTotalCost     | decimal             | Haalt de geschatte totale kosten op in USD of stelt deze in. Beschikbaar voor azure-abonnementsbronnen.                                         |
| LastModifiedDate | date               | De datum waarop de gebruiksgegevens het laatst zijn gewijzigd.                                                                       |
| Koppelingen            | ResourceLinks      | De resourcekoppelingen die overeenkomen met het gebruiksoverzicht.                                                           |
| Kenmerken       | ResourceAttributes | De metagegevenskenmerken die overeenkomen met het gebruiksoverzicht.                                                      |

## <a name="partnerusagesummary"></a>PartnerUsageSummary

**PartnerUsageSummary** vertegenwoordigt een samenvatting op partnerniveau van het gebruiksbudget voor alle klanten.

| Eigenschap         | Type               | Description                                                                                                      |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------|
| EmailsToNotify   | tekenreeksmatrix   | De lijst met e-mailadressen voor meldingen.                                                                   |
| CustomerOverBudget | geheel getal          | Het aantal klanten dat boven budget is.                                                                    |
| CustomersTrendingOver | geheel getal       | Het aantal klanten dat het budget bijna heeft overgenomen.                                                     |
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

**SpendingBudget** vertegenwoordigt het budget dat aan deze klant is toegewezen voor abonnementen op basis van gebruik.

| Eigenschap   | Type               | Description                                                                                         |
|------------|--------------------|-----------------------------------------------------------------------------------------------------|
| Bedrag     | decimal             | Het toegewezen budget. Als de waarde null is, wordt er geen uitgavenbudget toegewezen aan deze klant. |
| Kenmerken | ResourceAttributes | De metagegevenskenmerken die overeenkomen met het budget.                                                |
