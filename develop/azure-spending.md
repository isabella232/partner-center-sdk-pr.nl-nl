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
# <a name="azure-spending-api-resources-to-manage-partner-or-customer-spending-and-usage-against-a-budget"></a><span data-ttu-id="f4ef9-103">Azure-uitgaven-API-resources voor het beheren van partner- of klantuitgaven en -gebruik ten opzichte van een budget</span><span class="sxs-lookup"><span data-stu-id="f4ef9-103">Azure spending API resources to manage partner or customer spending and usage against a budget</span></span> 

<span data-ttu-id="f4ef9-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="f4ef9-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="f4ef9-105">Cloud Solution Provider (CSP)-partners kunnen hun Azure-uitgaven bekijken en beheren via Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="f4ef9-105">Cloud Solution Provider (CSP) partners can view and manage their Azure spending through Partner Center APIs.</span></span> <span data-ttu-id="f4ef9-106">Ze kunnen ook programmatisch de uitgaven van hun klanten bekijken ten opzichte van een Azure-uitgavenbudget.</span><span class="sxs-lookup"><span data-stu-id="f4ef9-106">They can also programmatically view their customers' spending against an Azure spending budget.</span></span>

<span data-ttu-id="f4ef9-107">Zie scenario's waarin CSP-partners de api's van Partner Center gebruiken voor het beheren van klant- en [partneraccounts en -orders voor meer informatie.](scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="f4ef9-107">For more information, see [scenarios in which CSP partners can use the Partner Center APIs to manage customer and partner accounts and orders](scenarios.md).</span></span>

## <a name="partner-usage-management"></a><span data-ttu-id="f4ef9-108">Partnergebruiksbeheer</span><span class="sxs-lookup"><span data-stu-id="f4ef9-108">Partner usage management</span></span>

- <span data-ttu-id="f4ef9-109">[Een samenvatting van het gebruik van partners krijgen](get-a-partner-usage-summary.md) met behulp van de resource **PartnerUsageSummary**</span><span class="sxs-lookup"><span data-stu-id="f4ef9-109">[Get a partner usage summary](get-a-partner-usage-summary.md) using the **PartnerUsageSummary** resource</span></span>
- <span data-ttu-id="f4ef9-110">[Gebruiksrecords voor alle klanten op halen](get-a-customer-s-usage-records.md) met behulp van de resource **CustomerMonthlyUsageRecord**</span><span class="sxs-lookup"><span data-stu-id="f4ef9-110">[Get usage records for all customers](get-a-customer-s-usage-records.md) using the **CustomerMonthlyUsageRecord** resource</span></span>

## <a name="customer-usage-management"></a><span data-ttu-id="f4ef9-111">Beheer van klantgebruik</span><span class="sxs-lookup"><span data-stu-id="f4ef9-111">Customer usage management</span></span>

- <span data-ttu-id="f4ef9-112">[Het gebruiksoverzicht van een klant op halen](get-a-customer-usage-summary.md) met behulp van de resource **CustomerUsageSummary**</span><span class="sxs-lookup"><span data-stu-id="f4ef9-112">[Get a customer's usage summary](get-a-customer-usage-summary.md) using the **CustomerUsageSummary** resource</span></span>
- <span data-ttu-id="f4ef9-113">[Alle abonnementsgebruiksrecords voor een klant op te](get-a-customer-subscription-s-usage-records.md) halen met behulp van de resource **SubscriptionMonthlyUsageRecord**</span><span class="sxs-lookup"><span data-stu-id="f4ef9-113">[Get all subscription usage records for a customer](get-a-customer-subscription-s-usage-records.md) using the **SubscriptionMonthlyUsageRecord** resource</span></span>

## <a name="subscription-usage-management"></a><span data-ttu-id="f4ef9-114">Abonnementsgebruiksbeheer</span><span class="sxs-lookup"><span data-stu-id="f4ef9-114">Subscription usage management</span></span>

- <span data-ttu-id="f4ef9-115">[Een overzicht van het gebruik van een abonnement](get-a-customer-subscription-usage-summary.md) krijgen met behulp van de resource **SubscriptionUsageSummary**</span><span class="sxs-lookup"><span data-stu-id="f4ef9-115">[Get a subscription usage summary](get-a-customer-subscription-usage-summary.md) using the **SubscriptionUsageSummary** resource</span></span>
- <span data-ttu-id="f4ef9-116">[Alle maandelijkse gebruiksrecords voor een abonnement op halen met](get-all-monthly-usage-records-for-a-subscription.md) behulp van de resource **AzureResourceMonthlyUsageRecord**</span><span class="sxs-lookup"><span data-stu-id="f4ef9-116">[Get all monthly usage records for a subscription](get-all-monthly-usage-records-for-a-subscription.md) using the **AzureResourceMonthlyUsageRecord** resource</span></span>
- <span data-ttu-id="f4ef9-117">[Gebruiksgegevens voor een abonnement per resource op halen met](get-a-customer-subscription-resource-usage-records.md) behulp van de resource **ResourceUsageRecord**</span><span class="sxs-lookup"><span data-stu-id="f4ef9-117">[Get usage data for a subscription by resource](get-a-customer-subscription-resource-usage-records.md) using the **ResourceUsageRecord** resource</span></span>
- <span data-ttu-id="f4ef9-118">[Gebruiksgegevens voor een abonnement per meter op halen met](get-a-customer-subscription-meter-usage-records.md) behulp van de **MeterUsageRecord-resource**</span><span class="sxs-lookup"><span data-stu-id="f4ef9-118">[Get usage data for a subscription by meter](get-a-customer-subscription-meter-usage-records.md) using the **MeterUsageRecord** resource</span></span>

## <a name="azure-spending-budget-management"></a><span data-ttu-id="f4ef9-119">Azure-uitgavenbudgetbeheer</span><span class="sxs-lookup"><span data-stu-id="f4ef9-119">Azure spending budget management</span></span>

- <span data-ttu-id="f4ef9-120">[Het gebruiksbudget van een klant op halen](get-a-customer-s-usage-spending-budget.md) met behulp van de resource **CustomerUsageSummary**</span><span class="sxs-lookup"><span data-stu-id="f4ef9-120">[Get a customer's usage budget](get-a-customer-s-usage-spending-budget.md) using the **CustomerUsageSummary** resource</span></span>
- <span data-ttu-id="f4ef9-121">[Het gebruiksbudget van een klant bijwerken](update-a-customer-s-usage-spending-budget.md) met behulp van de resource **CustomerUsageSummary**</span><span class="sxs-lookup"><span data-stu-id="f4ef9-121">[Update a customer's usage budget](update-a-customer-s-usage-spending-budget.md) using the **CustomerUsageSummary** resource</span></span>
