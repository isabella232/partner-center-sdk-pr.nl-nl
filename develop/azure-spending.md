---
title: Azure bestedings-API-resources
description: Ontdek hoe CSP-partners Partner Center-Api's kunnen gebruiken om de uitgaven en het gebruik van Azure-partners en klanten te bekijken en te beheren op basis van hun budget.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 02a2995a06473cc6990d1234acd522a3b38a03d3
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767593"
---
# <a name="azure-spending-api-resources-to-manage-partner-or-customer-spending-and-usage-against-a-budget"></a>Azure bestedings-API-resources voor het beheren van de partner-of klant uitgaven en het gebruik van een budget 

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Cloud Solution Provider (CSP)-partners kunnen hun Azure-uitgaven bekijken en beheren via partner Center-Api's. Ze kunnen ook programmatisch de uitgaven van hun klanten bekijken op basis van een Azure-uitgaven budget.

Zie [scenario's waarin CSP-partners de partner centrum-api's kunnen gebruiken voor het beheren van klant-en partner accounts en-orders](scenarios.md)voor meer informatie.

## <a name="partner-usage-management"></a>Beheer van partner gebruik

- [Een samen vatting van de partner gebruik ophalen](get-a-partner-usage-summary.md) met behulp van de **PartnerUsageSummary** -resource
- [Gebruiks records voor alle klanten ophalen](get-a-customer-s-usage-records.md) met behulp van de **CustomerMonthlyUsageRecord** -resource

## <a name="customer-usage-management"></a>Beheer van klant gebruik

- Het [gebruiks overzicht van een klant ophalen](get-a-customer-usage-summary.md) met behulp van de **CustomerUsageSummary** -resource
- [Alle gebruiks records voor een klant ophalen](get-a-customer-subscription-s-usage-records.md) met behulp van de **SubscriptionMonthlyUsageRecord** -resource

## <a name="subscription-usage-management"></a>Beheer van abonnements gebruik

- [Een overzicht van het gebruik van een abonnement ophalen](get-a-customer-subscription-usage-summary.md) met behulp van de **SubscriptionUsageSummary** -resource
- [Alle maandelijkse gebruiks records voor een abonnement ophalen](get-all-monthly-usage-records-for-a-subscription.md) met behulp van de **AzureResourceMonthlyUsageRecord** -resource
- [Gebruiks gegevens ophalen voor een abonnement per resource](get-a-customer-subscription-resource-usage-records.md) met behulp van de **ResourceUsageRecord** -resource
- [Gebruiks gegevens ophalen voor een abonnement per meter](get-a-customer-subscription-meter-usage-records.md) met behulp van de **MeterUsageRecord** -resource

## <a name="azure-spending-budget-management"></a>Beheer van uitgaven budget van Azure

- Het [gebruiks budget van een klant ophalen](get-a-customer-s-usage-spending-budget.md) met behulp van de **CustomerUsageSummary** -resource
- Het [gebruiks budget van een klant bijwerken](update-a-customer-s-usage-spending-budget.md) met behulp van de **CustomerUsageSummary** -resource
