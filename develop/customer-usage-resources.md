---
title: Resources voor klant gebruik
description: Resources voor klanten met op gebruik gebaseerde abonnementen en maandelijks gebruik van budgetten (waaronder CustomerMonthlyUsageRecord, CustomerUsageSummary, PartnerUsageSummary en SpendingBudget).
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ec82fcfe6c08a8ad55dd1fb48984859b954dd3c8
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767192"
---
# <a name="customer-usage-resources"></a>Resources voor klant gebruik

**Van toepassing op:**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Klanten met op gebruik gebaseerde abonnementen kunnen een maandelijks budget gebruiken. In deze begroting wordt een limiet ingesteld voor het maximale gebruik van de klant en kan de partner het gebruik gedurende een periode bijhouden.

> [!NOTE]
> Gebruiks nummers van klanten zijn schattingen (niet de uiteindelijke waarden), die niet mogen worden gebruikt voor facturerings doeleinden.

## <a name="customermonthlyusagerecord"></a>CustomerMonthlyUsageRecord

**CustomerMonthlyUsageRecord** vertegenwoordigt de geschatte monetaire kosten van het gebruik van een klant in de huidige maand.

| Eigenschap         | Type               | Description                                                              |
|------------------|--------------------|--------------------------------------------------------------------------|
| Budget           | SpendingBudget     | Het bestedings budget dat voor de klant is toegewezen.                          |
| PercentUsed      | decimal             | Het percentage dat uit het toegewezen budget wordt gebruikt.                        |
| ResourceId       | tekenreeks             | De unieke id van de resource.                                   |
| ResourceName     | tekenreeks             | De naam van de resource.                                                |
| Totale        | decimal             | De geschatte totale kosten voor het gebruik van de resources in het abonnement.|
| CurrencyLocale   | tekenreeks             | De valuta-land instelling van de klant. Beschikbaar voor Microsoft Azure-abonnementen (MS-AZR-0145P).            |
| CurrencyCode     | tekenreeks             | Hiermee wordt de valuta code opgehaald of ingesteld. Beschikbaar voor Azure-abonnementen.           |
| USDTotalCost     | decimal             | Hiermee worden de geschatte totale kosten in USD opgehaald of ingesteld. Beschikbaar voor Azure-abonnementen.                                         |
| IsUpgraded       | booleaans             | Hiermee wordt een waarde opgehaald of ingesteld waarmee wordt aangegeven of het Azure-abonnement van de klant wordt bijgewerkt. De waarde **True** vertegenwoordigt klanten die een Azure-abonnement hebben.                         |
| LastModifiedDate | date               | De datum waarop de gebruiks gegevens voor het laatst zijn gewijzigd.                               |
| Kenmerken       | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de gebruiks record.               |

## <a name="customerusagesummary"></a>CustomerUsageSummary

**CustomerUsageSummary** vertegenwoordigt een samen vatting van het gebruik van de klant voor een volledige facturerings periode.

| Eigenschap         | Type               | Description                                                                                                      |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------|
| Budget           | SpendingBudget     | Het bestedings budget dat voor de klant is toegewezen.                                                                  |
| ResourceId       | tekenreeks             | De unieke id van de resource. In de context van CustomerMonthlyUsageRecord is deze id de klant-id. |
| ResourceName     | tekenreeks             | De naam van de resource. In de context van CustomerMonthlyUsageRecord is dit de naam van de klant.               |
| BillingStartDate | date               | De begin datum van de huidige facturerings periode.                                                                    |
| BillingEndDate   | date               | De eind datum van de huidige facturerings periode.                                                                      |
| Totale        | decimal             | De geschatte totale kosten voor het gebruik van de resources in het abonnement.                                         |
| CurrencyLocale   | tekenreeks             | De valuta-land instelling van de klant. Beschikbaar voor Microsoft Azure-abonnementen (MS-AZR-0145P).                                         |
| CurrencyCode     | tekenreeks             | Hiermee wordt de valuta code opgehaald of ingesteld. Beschikbaar voor Azure-abonnementen.                                         |
| USDTotalCost     | decimal             | Hiermee worden de geschatte totale kosten in USD opgehaald of ingesteld. Beschikbaar voor Azure Plan-resources voor abonnementen.                                         |
| LastModifiedDate | date               | De datum waarop de gebruiks gegevens voor het laatst zijn gewijzigd.                                                                       |
| Koppelingen            | ResourceLinks      | De resource koppelingen die overeenkomen met de samen vatting van het gebruik.                                                           |
| Kenmerken       | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de samen vatting van het gebruik.                                                      |

## <a name="partnerusagesummary"></a>PartnerUsageSummary

**PartnerUsageSummary** vertegenwoordigt een samen vatting van het gebruik van budget tering op partner niveau voor alle klanten.

| Eigenschap         | Type               | Description                                                                                                      |
|------------------|--------------------|------------------------------------------------------------------------------------------------------------------|
| EmailsToNotify   | tekenreeksmatrix   | De lijst met e-mail adressen voor meldingen.                                                                   |
| CustomerOverBudget | geheel getal          | Het aantal klanten dat het budget overschrijdt.                                                                    |
| CustomersTrendingOver | geheel getal       | Het aantal klanten dat bijna het budget gaat overschrijden.                                                     |
| CustomersWithUsageBasedSubscriptions  | geheel getal | Het aantal klanten met een abonnement op basis van gebruik.                                               |
| ResourceId       | tekenreeks             | De unieke id van de resource. In de context van CustomerMonthlyUsageRecord is deze id de klant-id. |
| ResourceName     | tekenreeks             | De naam van de resource. In de context van CustomerMonthlyUsageRecord is dit de naam van de klant.               |
| BillingStartDate | date               | De begin datum van de huidige facturerings periode.                                                                    |
| BillingEndDate   | date               | De eind datum van de huidige facturerings periode.                                                                      |
| Totale        | decimal             | De geschatte totale kosten van het gebruik van alle klanten op basis van het huidige gebruik vanaf het begin van de facturerings periode.      |
| CurrencyLocale   | tekenreeks             | De valuta-land instelling.                                                                                             |
| LastModifiedDate | date               | De datum waarop de gebruiks gegevens voor het laatst zijn gewijzigd.                                                                       |
| Koppelingen            | ResourceLinks      | De resource koppelingen die overeenkomen met de samen vatting van het gebruik.                                                           |
| Kenmerken       | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de samen vatting van het gebruik.                                                      |

## <a name="spendingbudget"></a>SpendingBudget

**SpendingBudget** vertegenwoordigt het budget dat aan deze klant wordt toegewezen voor op gebruik gebaseerde abonnementen.

| Eigenschap   | Type               | Description                                                                                         |
|------------|--------------------|-----------------------------------------------------------------------------------------------------|
| Bedrag     | decimal             | Het toegewezen budget. Als de waarde Null is, wordt er geen bestedings budget aan deze klant toegewezen. |
| Kenmerken | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met het budget.                                                |
