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
# <a name="azure-spending-api-resources-to-manage-partner-or-customer-spending-and-usage-against-a-budget"></a><span data-ttu-id="db9c3-103">Azure bestedings-API-resources voor het beheren van de partner-of klant uitgaven en het gebruik van een budget</span><span class="sxs-lookup"><span data-stu-id="db9c3-103">Azure spending API resources to manage partner or customer spending and usage against a budget</span></span> 

<span data-ttu-id="db9c3-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="db9c3-104">**Applies to:**</span></span>

- <span data-ttu-id="db9c3-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="db9c3-105">Partner Center</span></span>
- <span data-ttu-id="db9c3-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="db9c3-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="db9c3-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="db9c3-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="db9c3-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="db9c3-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="db9c3-109">Cloud Solution Provider (CSP)-partners kunnen hun Azure-uitgaven bekijken en beheren via partner Center-Api's.</span><span class="sxs-lookup"><span data-stu-id="db9c3-109">Cloud Solution Provider (CSP) partners can view and manage their Azure spending through Partner Center APIs.</span></span> <span data-ttu-id="db9c3-110">Ze kunnen ook programmatisch de uitgaven van hun klanten bekijken op basis van een Azure-uitgaven budget.</span><span class="sxs-lookup"><span data-stu-id="db9c3-110">They can also programmatically view their customers' spending against an Azure spending budget.</span></span>

<span data-ttu-id="db9c3-111">Zie [scenario's waarin CSP-partners de partner centrum-api's kunnen gebruiken voor het beheren van klant-en partner accounts en-orders](scenarios.md)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="db9c3-111">For more information, see [scenarios in which CSP partners can use the Partner Center APIs to manage customer and partner accounts and orders](scenarios.md).</span></span>

## <a name="partner-usage-management"></a><span data-ttu-id="db9c3-112">Beheer van partner gebruik</span><span class="sxs-lookup"><span data-stu-id="db9c3-112">Partner usage management</span></span>

- <span data-ttu-id="db9c3-113">[Een samen vatting van de partner gebruik ophalen](get-a-partner-usage-summary.md) met behulp van de **PartnerUsageSummary** -resource</span><span class="sxs-lookup"><span data-stu-id="db9c3-113">[Get a partner usage summary](get-a-partner-usage-summary.md) using the **PartnerUsageSummary** resource</span></span>
- <span data-ttu-id="db9c3-114">[Gebruiks records voor alle klanten ophalen](get-a-customer-s-usage-records.md) met behulp van de **CustomerMonthlyUsageRecord** -resource</span><span class="sxs-lookup"><span data-stu-id="db9c3-114">[Get usage records for all customers](get-a-customer-s-usage-records.md) using the **CustomerMonthlyUsageRecord** resource</span></span>

## <a name="customer-usage-management"></a><span data-ttu-id="db9c3-115">Beheer van klant gebruik</span><span class="sxs-lookup"><span data-stu-id="db9c3-115">Customer usage management</span></span>

- <span data-ttu-id="db9c3-116">Het [gebruiks overzicht van een klant ophalen](get-a-customer-usage-summary.md) met behulp van de **CustomerUsageSummary** -resource</span><span class="sxs-lookup"><span data-stu-id="db9c3-116">[Get a customer's usage summary](get-a-customer-usage-summary.md) using the **CustomerUsageSummary** resource</span></span>
- <span data-ttu-id="db9c3-117">[Alle gebruiks records voor een klant ophalen](get-a-customer-subscription-s-usage-records.md) met behulp van de **SubscriptionMonthlyUsageRecord** -resource</span><span class="sxs-lookup"><span data-stu-id="db9c3-117">[Get all subscription usage records for a customer](get-a-customer-subscription-s-usage-records.md) using the **SubscriptionMonthlyUsageRecord** resource</span></span>

## <a name="subscription-usage-management"></a><span data-ttu-id="db9c3-118">Beheer van abonnements gebruik</span><span class="sxs-lookup"><span data-stu-id="db9c3-118">Subscription usage management</span></span>

- <span data-ttu-id="db9c3-119">[Een overzicht van het gebruik van een abonnement ophalen](get-a-customer-subscription-usage-summary.md) met behulp van de **SubscriptionUsageSummary** -resource</span><span class="sxs-lookup"><span data-stu-id="db9c3-119">[Get a subscription usage summary](get-a-customer-subscription-usage-summary.md) using the **SubscriptionUsageSummary** resource</span></span>
- <span data-ttu-id="db9c3-120">[Alle maandelijkse gebruiks records voor een abonnement ophalen](get-all-monthly-usage-records-for-a-subscription.md) met behulp van de **AzureResourceMonthlyUsageRecord** -resource</span><span class="sxs-lookup"><span data-stu-id="db9c3-120">[Get all monthly usage records for a subscription](get-all-monthly-usage-records-for-a-subscription.md) using the **AzureResourceMonthlyUsageRecord** resource</span></span>
- <span data-ttu-id="db9c3-121">[Gebruiks gegevens ophalen voor een abonnement per resource](get-a-customer-subscription-resource-usage-records.md) met behulp van de **ResourceUsageRecord** -resource</span><span class="sxs-lookup"><span data-stu-id="db9c3-121">[Get usage data for a subscription by resource](get-a-customer-subscription-resource-usage-records.md) using the **ResourceUsageRecord** resource</span></span>
- <span data-ttu-id="db9c3-122">[Gebruiks gegevens ophalen voor een abonnement per meter](get-a-customer-subscription-meter-usage-records.md) met behulp van de **MeterUsageRecord** -resource</span><span class="sxs-lookup"><span data-stu-id="db9c3-122">[Get usage data for a subscription by meter](get-a-customer-subscription-meter-usage-records.md) using the **MeterUsageRecord** resource</span></span>

## <a name="azure-spending-budget-management"></a><span data-ttu-id="db9c3-123">Beheer van uitgaven budget van Azure</span><span class="sxs-lookup"><span data-stu-id="db9c3-123">Azure spending budget management</span></span>

- <span data-ttu-id="db9c3-124">Het [gebruiks budget van een klant ophalen](get-a-customer-s-usage-spending-budget.md) met behulp van de **CustomerUsageSummary** -resource</span><span class="sxs-lookup"><span data-stu-id="db9c3-124">[Get a customer's usage budget](get-a-customer-s-usage-spending-budget.md) using the **CustomerUsageSummary** resource</span></span>
- <span data-ttu-id="db9c3-125">Het [gebruiks budget van een klant bijwerken](update-a-customer-s-usage-spending-budget.md) met behulp van de **CustomerUsageSummary** -resource</span><span class="sxs-lookup"><span data-stu-id="db9c3-125">[Update a customer's usage budget](update-a-customer-s-usage-spending-budget.md) using the **CustomerUsageSummary** resource</span></span>
