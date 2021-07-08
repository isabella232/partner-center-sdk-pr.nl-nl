---
title: Beheerde servicebronnen
description: Beheerde services zijn services waaraan een partner beheerdersbevoegdheden heeft gedelegeerd. Partners kunnen ondersteuning bieden voor en serviceaanvragen indienen namens hun beheerde services.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 582efe75fd18a9174dd5dc173c290bee25443ee9
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548121"
---
# <a name="managed-service-resources"></a><span data-ttu-id="0e803-104">Beheerde servicebronnen</span><span class="sxs-lookup"><span data-stu-id="0e803-104">Managed service resources</span></span>

<span data-ttu-id="0e803-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0e803-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0e803-106">Beheerde services zijn services waaraan een partner beheerdersbevoegdheden heeft gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="0e803-106">Managed services are services to which a partner has delegated admin privileges.</span></span> <span data-ttu-id="0e803-107">Partners kunnen ondersteuning bieden voor en serviceaanvragen indienen namens hun beheerde services.</span><span class="sxs-lookup"><span data-stu-id="0e803-107">Partners can provide support for and file service requests on the behalf of their managed services.</span></span>

## <a name="managedservice"></a><span data-ttu-id="0e803-108">ManagedService</span><span class="sxs-lookup"><span data-stu-id="0e803-108">ManagedService</span></span>

<span data-ttu-id="0e803-109">Beschrijft een beheerde service.</span><span class="sxs-lookup"><span data-stu-id="0e803-109">Describes a managed service.</span></span>

| <span data-ttu-id="0e803-110">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="0e803-110">Property</span></span>   | <span data-ttu-id="0e803-111">Type</span><span class="sxs-lookup"><span data-stu-id="0e803-111">Type</span></span>                | <span data-ttu-id="0e803-112">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0e803-112">Description</span></span>                                              |
|------------|---------------------|----------------------------------------------------------|
| <span data-ttu-id="0e803-113">Id</span><span class="sxs-lookup"><span data-stu-id="0e803-113">Id</span></span>         | <span data-ttu-id="0e803-114">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="0e803-114">string</span></span>              | <span data-ttu-id="0e803-115">De id van de beheerde service.</span><span class="sxs-lookup"><span data-stu-id="0e803-115">The managed service ID.</span></span>                                  |
| <span data-ttu-id="0e803-116">Name</span><span class="sxs-lookup"><span data-stu-id="0e803-116">Name</span></span>       | <span data-ttu-id="0e803-117">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="0e803-117">string</span></span>              | <span data-ttu-id="0e803-118">De naam van de beheerde service.</span><span class="sxs-lookup"><span data-stu-id="0e803-118">The name of the managed service.</span></span>                         |
| <span data-ttu-id="0e803-119">Groupname</span><span class="sxs-lookup"><span data-stu-id="0e803-119">GroupName</span></span>  | <span data-ttu-id="0e803-120">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="0e803-120">string</span></span>              | <span data-ttu-id="0e803-121">De naam van de groep waar de service bij hoort.</span><span class="sxs-lookup"><span data-stu-id="0e803-121">The name of the group to which the service belongs.</span></span>      |
| <span data-ttu-id="0e803-122">Koppelingen</span><span class="sxs-lookup"><span data-stu-id="0e803-122">Links</span></span>      | <span data-ttu-id="0e803-123">ManagedServiceLinks</span><span class="sxs-lookup"><span data-stu-id="0e803-123">ManagedServiceLinks</span></span> | <span data-ttu-id="0e803-124">De resourcekoppelingen die overeenkomen met de beheerde service.</span><span class="sxs-lookup"><span data-stu-id="0e803-124">The resource links corresponding to the managed service.</span></span> |
| <span data-ttu-id="0e803-125">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="0e803-125">Attributes</span></span> | <span data-ttu-id="0e803-126">ResourceAttributes</span><span class="sxs-lookup"><span data-stu-id="0e803-126">ResourceAttributes</span></span>  | <span data-ttu-id="0e803-127">De metagegevenskenmerken die overeenkomen met de overeenkomst.</span><span class="sxs-lookup"><span data-stu-id="0e803-127">The metadata attributes corresponding to the agreement.</span></span>  |

## <a name="managedservicelinks"></a><span data-ttu-id="0e803-128">ManagedServiceLinks</span><span class="sxs-lookup"><span data-stu-id="0e803-128">ManagedServiceLinks</span></span>

<span data-ttu-id="0e803-129">Bevat de koppelingen waarmee de partner met gedelegeerde beheerdersmachtigingen ondersteuning kan bieden voor de service.</span><span class="sxs-lookup"><span data-stu-id="0e803-129">Contains the links that allow the partner with delegated admin permissions to provide support for the service.</span></span>

| <span data-ttu-id="0e803-130">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="0e803-130">Property</span></span>      | <span data-ttu-id="0e803-131">Type</span><span class="sxs-lookup"><span data-stu-id="0e803-131">Type</span></span> | <span data-ttu-id="0e803-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0e803-132">Description</span></span>                 |
|---------------|------|-----------------------------|
| <span data-ttu-id="0e803-133">AdminService</span><span class="sxs-lookup"><span data-stu-id="0e803-133">AdminService</span></span>  | <span data-ttu-id="0e803-134">Koppeling</span><span class="sxs-lookup"><span data-stu-id="0e803-134">Link</span></span> | <span data-ttu-id="0e803-135">De URI van de beheerservice.</span><span class="sxs-lookup"><span data-stu-id="0e803-135">The admin service URI.</span></span>      |
| <span data-ttu-id="0e803-136">ServiceHealth</span><span class="sxs-lookup"><span data-stu-id="0e803-136">ServiceHealth</span></span> | <span data-ttu-id="0e803-137">Koppeling</span><span class="sxs-lookup"><span data-stu-id="0e803-137">Link</span></span> | <span data-ttu-id="0e803-138">De URI voor service health.</span><span class="sxs-lookup"><span data-stu-id="0e803-138">The service health URI.</span></span>     |
| <span data-ttu-id="0e803-139">ServiceTicket</span><span class="sxs-lookup"><span data-stu-id="0e803-139">ServiceTicket</span></span> | <span data-ttu-id="0e803-140">Koppeling</span><span class="sxs-lookup"><span data-stu-id="0e803-140">Link</span></span> | <span data-ttu-id="0e803-141">De serviceticket-URI.</span><span class="sxs-lookup"><span data-stu-id="0e803-141">The service ticket URI.</span></span>     |
| <span data-ttu-id="0e803-142">Zelf</span><span class="sxs-lookup"><span data-stu-id="0e803-142">Self</span></span>          | <span data-ttu-id="0e803-143">Koppeling</span><span class="sxs-lookup"><span data-stu-id="0e803-143">Link</span></span> | <span data-ttu-id="0e803-144">De zelf-URI.</span><span class="sxs-lookup"><span data-stu-id="0e803-144">The self-URI.</span></span>               |
| <span data-ttu-id="0e803-145">Volgende</span><span class="sxs-lookup"><span data-stu-id="0e803-145">Next</span></span>          | <span data-ttu-id="0e803-146">Koppeling</span><span class="sxs-lookup"><span data-stu-id="0e803-146">Link</span></span> | <span data-ttu-id="0e803-147">De volgende pagina met items.</span><span class="sxs-lookup"><span data-stu-id="0e803-147">The next page of items.</span></span>     |
| <span data-ttu-id="0e803-148">Vorige</span><span class="sxs-lookup"><span data-stu-id="0e803-148">Previous</span></span>      | <span data-ttu-id="0e803-149">Koppeling</span><span class="sxs-lookup"><span data-stu-id="0e803-149">Link</span></span> | <span data-ttu-id="0e803-150">De vorige pagina met items.</span><span class="sxs-lookup"><span data-stu-id="0e803-150">The previous page of items.</span></span> |

