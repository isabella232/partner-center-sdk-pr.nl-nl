---
title: TransferEligibility-resources
description: Een partner maakt een overdracht wanneer een klant hun abonnement met de partner wil overzetten naar een andere partner.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: dcac5724a1f708bc540a3aac7ce74b2eda60a296
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767248"
---
# <a name="transfereligibility-resources"></a><span data-ttu-id="d418a-103">TransferEligibility-resources</span><span class="sxs-lookup"><span data-stu-id="d418a-103">TransferEligibility resources</span></span>

<span data-ttu-id="d418a-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="d418a-104">**Applies to:**</span></span>

- <span data-ttu-id="d418a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d418a-105">Partner Center</span></span>

<span data-ttu-id="d418a-106">Een partner maakt een overdracht wanneer een klant hun abonnement met de partner wil overzetten naar een andere partner.</span><span class="sxs-lookup"><span data-stu-id="d418a-106">A partner creates a transfer when a customer wants their subscription with the partner to be transferred to another partner.</span></span>

## <a name="transfereligibility"></a><span data-ttu-id="d418a-107">TransferEligibility</span><span class="sxs-lookup"><span data-stu-id="d418a-107">TransferEligibility</span></span>

<span data-ttu-id="d418a-108">Hierin wordt een transferEligibility beschreven.</span><span class="sxs-lookup"><span data-stu-id="d418a-108">Describes a transferEligibility.</span></span>

| <span data-ttu-id="d418a-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="d418a-109">Property</span></span>              | <span data-ttu-id="d418a-110">Type</span><span class="sxs-lookup"><span data-stu-id="d418a-110">Type</span></span>             | <span data-ttu-id="d418a-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d418a-111">Description</span></span>                                                                              |
|-----------------------|------------------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="d418a-112">id</span><span class="sxs-lookup"><span data-stu-id="d418a-112">id</span></span>                    | <span data-ttu-id="d418a-113">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d418a-113">string</span></span>           | <span data-ttu-id="d418a-114">De abonnements-id van de klant.</span><span class="sxs-lookup"><span data-stu-id="d418a-114">The customer's subscription identifier.</span></span>                                                  |
| <span data-ttu-id="d418a-115">isEligible</span><span class="sxs-lookup"><span data-stu-id="d418a-115">isEligible</span></span>            | <span data-ttu-id="d418a-116">booleaans</span><span class="sxs-lookup"><span data-stu-id="d418a-116">bool</span></span>             | <span data-ttu-id="d418a-117">Hiermee wordt aangegeven of het abonnement in aanmerking komt voor de overdracht.</span><span class="sxs-lookup"><span data-stu-id="d418a-117">Indicates whether the subscription is eligible for the transfer.</span></span>                         |
| <span data-ttu-id="d418a-118">Reden</span><span class="sxs-lookup"><span data-stu-id="d418a-118">Reason</span></span>                | <span data-ttu-id="d418a-119">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d418a-119">string</span></span>           | <span data-ttu-id="d418a-120">De eigenschap reason legt uit waarom het abonnement niet in aanmerking komt voor overdracht.</span><span class="sxs-lookup"><span data-stu-id="d418a-120">The reason property explains why the subscription isn't eligible for transfer.</span></span> |