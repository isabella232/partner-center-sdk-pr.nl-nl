---
title: TransferEligibility-resources
description: Een partner kan een overdracht maken wanneer een klant een abonnement bij de partner aanvraagt om te worden overgedragen naar een andere partner.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8f121d499abffb4c4dda688c2a91c25f83d2e863
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530205"
---
# <a name="transfereligibility-resources"></a><span data-ttu-id="2452d-103">TransferEligibility-resources</span><span class="sxs-lookup"><span data-stu-id="2452d-103">TransferEligibility resources</span></span>

<span data-ttu-id="2452d-104">Een partner kan een overdracht maken wanneer een klant een abonnement bij de partner aanvraagt om te worden overgedragen naar een andere partner.</span><span class="sxs-lookup"><span data-stu-id="2452d-104">A partner can create a transfer when a customer requests their subscription with the partner to be transferred to another partner.</span></span> <span data-ttu-id="2452d-105">Gebruik TransferEligibility om te controleren of een abonnement in aanmerking komt voor overdracht.</span><span class="sxs-lookup"><span data-stu-id="2452d-105">Use TransferEligibility to check whether a subscription is eligible to be transferred.</span></span>

## <a name="transfereligibility"></a><span data-ttu-id="2452d-106">TransferEligibility</span><span class="sxs-lookup"><span data-stu-id="2452d-106">TransferEligibility</span></span>

<span data-ttu-id="2452d-107">Beschrijft een transferEligibility.</span><span class="sxs-lookup"><span data-stu-id="2452d-107">Describes a transferEligibility.</span></span>

| <span data-ttu-id="2452d-108">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2452d-108">Property</span></span>              | <span data-ttu-id="2452d-109">Type</span><span class="sxs-lookup"><span data-stu-id="2452d-109">Type</span></span>             | <span data-ttu-id="2452d-110">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2452d-110">Description</span></span>                                                                              |
|-----------------------|------------------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="2452d-111">id</span><span class="sxs-lookup"><span data-stu-id="2452d-111">id</span></span>                    | <span data-ttu-id="2452d-112">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2452d-112">string</span></span>           | <span data-ttu-id="2452d-113">De abonnements-id van de klant.</span><span class="sxs-lookup"><span data-stu-id="2452d-113">The customer's subscription identifier.</span></span>                                                  |
| <span data-ttu-id="2452d-114">isEligible</span><span class="sxs-lookup"><span data-stu-id="2452d-114">isEligible</span></span>            | <span data-ttu-id="2452d-115">booleaans</span><span class="sxs-lookup"><span data-stu-id="2452d-115">bool</span></span>             | <span data-ttu-id="2452d-116">Geeft aan of het abonnement in aanmerking komt voor de overdracht.</span><span class="sxs-lookup"><span data-stu-id="2452d-116">Indicates whether the subscription is eligible for the transfer.</span></span>                         |
| <span data-ttu-id="2452d-117">Reden</span><span class="sxs-lookup"><span data-stu-id="2452d-117">Reason</span></span>                | <span data-ttu-id="2452d-118">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2452d-118">string</span></span>           | <span data-ttu-id="2452d-119">De eigenschap reason verklaart waarom het abonnement niet in aanmerking komt voor overdracht.</span><span class="sxs-lookup"><span data-stu-id="2452d-119">The reason property explains why the subscription isn't eligible for transfer.</span></span> |