---
title: Azure-uitgaven-API-resources
description: Meer informatie over hoe CSP-partners Partner Center API's kunnen gebruiken om Azure-uitgaven en -gebruik van partners en klanten te bekijken en beheren op basis van hun budget.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 472554de1c354559d5bc4b21959c109467891806
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974315"
---
# <a name="azure-spending-api-resources-to-manage-partner-or-customer-spending-and-usage-against-a-budget"></a>Azure-uitgaven-API-resources voor het beheren van partner- of klantuitgaven en -gebruik ten opzichte van een budget 

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Cloud Solution Provider (CSP)-partners kunnen hun Azure-uitgaven bekijken en beheren via Partner Center API's. Ze kunnen ook programmatisch de uitgaven van hun klanten bekijken ten opzichte van een Azure-uitgavenbudget.

Zie scenario's waarin CSP-partners de api's van Partner Center gebruiken voor het beheren van klant- en [partneraccounts en -orders voor meer informatie.](scenarios.md)

## <a name="partner-usage-management"></a>Partnergebruiksbeheer

- [Een samenvatting van het gebruik van partners krijgen](get-a-partner-usage-summary.md) met behulp van de resource **PartnerUsageSummary**
- [Gebruiksrecords voor alle klanten op halen](get-a-customer-s-usage-records.md) met behulp van de resource **CustomerMonthlyUsageRecord**

## <a name="customer-usage-management"></a>Beheer van klantgebruik

- [Het gebruiksoverzicht van een klant op halen](get-a-customer-usage-summary.md) met behulp van de resource **CustomerUsageSummary**
- [Alle abonnementsgebruiksrecords voor een klant op te](get-a-customer-subscription-s-usage-records.md) halen met behulp van de resource **SubscriptionMonthlyUsageRecord**

## <a name="subscription-usage-management"></a>Abonnementsgebruiksbeheer

- [Een overzicht van het gebruik van een abonnement](get-a-customer-subscription-usage-summary.md) krijgen met behulp van de resource **SubscriptionUsageSummary**
- [Alle maandelijkse gebruiksrecords voor een abonnement op halen met](get-all-monthly-usage-records-for-a-subscription.md) behulp van de resource **AzureResourceMonthlyUsageRecord**
- [Gebruiksgegevens voor een abonnement per resource op halen met](get-a-customer-subscription-resource-usage-records.md) behulp van de resource **ResourceUsageRecord**
- [Gebruiksgegevens voor een abonnement per meter op halen met](get-a-customer-subscription-meter-usage-records.md) behulp van de **MeterUsageRecord-resource**

## <a name="azure-spending-budget-management"></a>Azure-uitgavenbudgetbeheer

- [Het gebruiksbudget van een klant op halen](get-a-customer-s-usage-spending-budget.md) met behulp van de resource **CustomerUsageSummary**
- [Het gebruiksbudget van een klant bijwerken](update-a-customer-s-usage-spending-budget.md) met behulp van de resource **CustomerUsageSummary**
