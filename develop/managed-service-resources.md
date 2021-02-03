---
title: Beheerde service resources
description: Beheerde services zijn services waaraan een partner beheerders bevoegdheden heeft gedelegeerd. Partners kunnen ondersteuning bieden voor en bestands service aanvragen namens hun beheerde services.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ef644ac4d8ae9660cffc9558af33cc27832556c7
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767215"
---
# <a name="managed-service-resources"></a><span data-ttu-id="4a02c-104">Beheerde service resources</span><span class="sxs-lookup"><span data-stu-id="4a02c-104">Managed service resources</span></span>

<span data-ttu-id="4a02c-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="4a02c-105">**Applies To**</span></span>

- <span data-ttu-id="4a02c-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="4a02c-106">Partner Center</span></span>
- <span data-ttu-id="4a02c-107">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="4a02c-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="4a02c-108">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="4a02c-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="4a02c-109">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="4a02c-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="4a02c-110">Beheerde services zijn services waaraan een partner beheerders bevoegdheden heeft gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="4a02c-110">Managed services are services to which a partner has delegated admin privileges.</span></span> <span data-ttu-id="4a02c-111">Partners kunnen ondersteuning bieden voor en bestands service aanvragen namens hun beheerde services.</span><span class="sxs-lookup"><span data-stu-id="4a02c-111">Partners can provide support for and file service requests on the behalf of their managed services.</span></span>

## <a name="managedservice"></a><span data-ttu-id="4a02c-112">ManagedService</span><span class="sxs-lookup"><span data-stu-id="4a02c-112">ManagedService</span></span>

<span data-ttu-id="4a02c-113">Hierin wordt een beheerde service beschreven.</span><span class="sxs-lookup"><span data-stu-id="4a02c-113">Describes a managed service.</span></span>

| <span data-ttu-id="4a02c-114">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="4a02c-114">Property</span></span>   | <span data-ttu-id="4a02c-115">Type</span><span class="sxs-lookup"><span data-stu-id="4a02c-115">Type</span></span>                | <span data-ttu-id="4a02c-116">Description</span><span class="sxs-lookup"><span data-stu-id="4a02c-116">Description</span></span>                                              |
|------------|---------------------|----------------------------------------------------------|
| <span data-ttu-id="4a02c-117">Id</span><span class="sxs-lookup"><span data-stu-id="4a02c-117">Id</span></span>         | <span data-ttu-id="4a02c-118">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4a02c-118">string</span></span>              | <span data-ttu-id="4a02c-119">De beheerde service-id.</span><span class="sxs-lookup"><span data-stu-id="4a02c-119">The managed service id.</span></span>                                  |
| <span data-ttu-id="4a02c-120">Name</span><span class="sxs-lookup"><span data-stu-id="4a02c-120">Name</span></span>       | <span data-ttu-id="4a02c-121">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4a02c-121">string</span></span>              | <span data-ttu-id="4a02c-122">De naam van de beheerde service.</span><span class="sxs-lookup"><span data-stu-id="4a02c-122">The name of the managed service.</span></span>                         |
| <span data-ttu-id="4a02c-123">GroupName</span><span class="sxs-lookup"><span data-stu-id="4a02c-123">GroupName</span></span>  | <span data-ttu-id="4a02c-124">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4a02c-124">string</span></span>              | <span data-ttu-id="4a02c-125">De naam van de groep waartoe de service behoort.</span><span class="sxs-lookup"><span data-stu-id="4a02c-125">The name of the group to which the service belongs.</span></span>      |
| <span data-ttu-id="4a02c-126">Koppelingen</span><span class="sxs-lookup"><span data-stu-id="4a02c-126">Links</span></span>      | <span data-ttu-id="4a02c-127">ManagedServiceLinks</span><span class="sxs-lookup"><span data-stu-id="4a02c-127">ManagedServiceLinks</span></span> | <span data-ttu-id="4a02c-128">De resource koppelingen die overeenkomen met de beheerde service.</span><span class="sxs-lookup"><span data-stu-id="4a02c-128">The resource links corresponding to the managed service.</span></span> |
| <span data-ttu-id="4a02c-129">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="4a02c-129">Attributes</span></span> | <span data-ttu-id="4a02c-130">ResourceAttributes</span><span class="sxs-lookup"><span data-stu-id="4a02c-130">ResourceAttributes</span></span>  | <span data-ttu-id="4a02c-131">De meta gegevens kenmerken die overeenkomen met de overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="4a02c-131">The metadata attributes corresponding to the agreement.</span></span>  |

## <a name="managedservicelinks"></a><span data-ttu-id="4a02c-132">ManagedServiceLinks</span><span class="sxs-lookup"><span data-stu-id="4a02c-132">ManagedServiceLinks</span></span>

<span data-ttu-id="4a02c-133">Bevat de koppelingen waarmee de partner met gedelegeerde beheerders machtigingen toegang biedt voor de service.</span><span class="sxs-lookup"><span data-stu-id="4a02c-133">Contains the links that allow the partner with delegated admin permissions to provide support for the service.</span></span>

| <span data-ttu-id="4a02c-134">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="4a02c-134">Property</span></span>      | <span data-ttu-id="4a02c-135">Type</span><span class="sxs-lookup"><span data-stu-id="4a02c-135">Type</span></span> | <span data-ttu-id="4a02c-136">Description</span><span class="sxs-lookup"><span data-stu-id="4a02c-136">Description</span></span>                 |
|---------------|------|-----------------------------|
| <span data-ttu-id="4a02c-137">AdminService</span><span class="sxs-lookup"><span data-stu-id="4a02c-137">AdminService</span></span>  | <span data-ttu-id="4a02c-138">Koppeling</span><span class="sxs-lookup"><span data-stu-id="4a02c-138">Link</span></span> | <span data-ttu-id="4a02c-139">De URI van de beheer service.</span><span class="sxs-lookup"><span data-stu-id="4a02c-139">The admin service URI.</span></span>      |
| <span data-ttu-id="4a02c-140">ServiceHealth</span><span class="sxs-lookup"><span data-stu-id="4a02c-140">ServiceHealth</span></span> | <span data-ttu-id="4a02c-141">Koppeling</span><span class="sxs-lookup"><span data-stu-id="4a02c-141">Link</span></span> | <span data-ttu-id="4a02c-142">De URI van de service status.</span><span class="sxs-lookup"><span data-stu-id="4a02c-142">The service health URI.</span></span>     |
| <span data-ttu-id="4a02c-143">ServiceTicket</span><span class="sxs-lookup"><span data-stu-id="4a02c-143">ServiceTicket</span></span> | <span data-ttu-id="4a02c-144">Koppeling</span><span class="sxs-lookup"><span data-stu-id="4a02c-144">Link</span></span> | <span data-ttu-id="4a02c-145">De URI van het service ticket.</span><span class="sxs-lookup"><span data-stu-id="4a02c-145">The service ticket URI.</span></span>     |
| <span data-ttu-id="4a02c-146">Zelf</span><span class="sxs-lookup"><span data-stu-id="4a02c-146">Self</span></span>          | <span data-ttu-id="4a02c-147">Koppeling</span><span class="sxs-lookup"><span data-stu-id="4a02c-147">Link</span></span> | <span data-ttu-id="4a02c-148">De zelf-URI.</span><span class="sxs-lookup"><span data-stu-id="4a02c-148">The self URI.</span></span>               |
| <span data-ttu-id="4a02c-149">Volgende</span><span class="sxs-lookup"><span data-stu-id="4a02c-149">Next</span></span>          | <span data-ttu-id="4a02c-150">Koppeling</span><span class="sxs-lookup"><span data-stu-id="4a02c-150">Link</span></span> | <span data-ttu-id="4a02c-151">De volgende pagina met items.</span><span class="sxs-lookup"><span data-stu-id="4a02c-151">The next page of items.</span></span>     |
| <span data-ttu-id="4a02c-152">Vorige</span><span class="sxs-lookup"><span data-stu-id="4a02c-152">Previous</span></span>      | <span data-ttu-id="4a02c-153">Koppeling</span><span class="sxs-lookup"><span data-stu-id="4a02c-153">Link</span></span> | <span data-ttu-id="4a02c-154">De vorige pagina met items.</span><span class="sxs-lookup"><span data-stu-id="4a02c-154">The previous page of items.</span></span> |

