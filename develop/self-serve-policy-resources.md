---
title: Resources voor self-servebeleid
description: Een partner stelt beleid voor self-service in voor een klant.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e44581b805e076132984b67280699314e274ca94
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446714"
---
# <a name="selfservepolicy-resource"></a><span data-ttu-id="2487b-103">SelfServePolicy-resource</span><span class="sxs-lookup"><span data-stu-id="2487b-103">SelfServePolicy resource</span></span>

<span data-ttu-id="2487b-104">Een partner stelt beleid voor self-service in voor een klant.</span><span class="sxs-lookup"><span data-stu-id="2487b-104">A partner sets self serve policies for a customer.</span></span>

## <a name="selfservepolicy"></a><span data-ttu-id="2487b-105">SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="2487b-105">SelfServePolicy</span></span>

<span data-ttu-id="2487b-106">Beschrijft een winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="2487b-106">Describes a cart.</span></span>

| <span data-ttu-id="2487b-107">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2487b-107">Property</span></span>              | <span data-ttu-id="2487b-108">Type</span><span class="sxs-lookup"><span data-stu-id="2487b-108">Type</span></span>             | <span data-ttu-id="2487b-109">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2487b-109">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2487b-110">id</span><span class="sxs-lookup"><span data-stu-id="2487b-110">id</span></span>                    | <span data-ttu-id="2487b-111">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2487b-111">string</span></span>           | <span data-ttu-id="2487b-112">Een self-serve beleids-id die wordt opgegeven wanneer het self-serve-beleid is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="2487b-112">A self-serve policy identifier that is supplied upon successful creation of the self serve policy.</span></span>     |
| <span data-ttu-id="2487b-113">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="2487b-113">SelfServeEntity</span></span>       | <span data-ttu-id="2487b-114">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="2487b-114">SelfServeEntity</span></span>  | <span data-ttu-id="2487b-115">De zelfhulpentiteit die toegang krijgt.</span><span class="sxs-lookup"><span data-stu-id="2487b-115">The self serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="2487b-116">Grantor</span><span class="sxs-lookup"><span data-stu-id="2487b-116">Grantor</span></span>               | <span data-ttu-id="2487b-117">Grantor</span><span class="sxs-lookup"><span data-stu-id="2487b-117">Grantor</span></span>          | <span data-ttu-id="2487b-118">De grantor die toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="2487b-118">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="2487b-119">Machtigingen</span><span class="sxs-lookup"><span data-stu-id="2487b-119">Permissions</span></span>           | <span data-ttu-id="2487b-120">Matrix van machtigingen</span><span class="sxs-lookup"><span data-stu-id="2487b-120">Array of Permission</span></span>| <span data-ttu-id="2487b-121">Een matrix met [machtigingsbronnen.](#permission)</span><span class="sxs-lookup"><span data-stu-id="2487b-121">An Array of [Permission](#permission) resources.</span></span>                                                                     |

## <a name="selfserveentity"></a><span data-ttu-id="2487b-122">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="2487b-122">SelfServeEntity</span></span>

<span data-ttu-id="2487b-123">Vertegenwoordigt de entiteit die machtigingen krijgt.</span><span class="sxs-lookup"><span data-stu-id="2487b-123">Represents the entity being granted permissions.</span></span>

| <span data-ttu-id="2487b-124">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2487b-124">Property</span></span>             | <span data-ttu-id="2487b-125">Type</span><span class="sxs-lookup"><span data-stu-id="2487b-125">Type</span></span>|<span data-ttu-id="2487b-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2487b-126">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="2487b-127">SelfServeEntityType</span><span class="sxs-lookup"><span data-stu-id="2487b-127">SelfServeEntityType</span></span>  | <span data-ttu-id="2487b-128">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2487b-128">string</span></span>                           | <span data-ttu-id="2487b-129">De entiteit die toegang krijgt, geaccepteerde waarden: Klant.</span><span class="sxs-lookup"><span data-stu-id="2487b-129">The entity being granted access, accepted values: Customer.</span></span>                                 |
| <span data-ttu-id="2487b-130">TenantID</span><span class="sxs-lookup"><span data-stu-id="2487b-130">TenantID</span></span>             | <span data-ttu-id="2487b-131">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2487b-131">string</span></span>                           | <span data-ttu-id="2487b-132">De tenant-id van de entiteit die toegang krijgt.</span><span class="sxs-lookup"><span data-stu-id="2487b-132">The tenant identifier of the entity being granted access.</span></span>                                   |

## <a name="grantor"></a><span data-ttu-id="2487b-133">Grantor</span><span class="sxs-lookup"><span data-stu-id="2487b-133">Grantor</span></span>

<span data-ttu-id="2487b-134">Vertegenwoordigt de grantor die de machtigingen verleent.</span><span class="sxs-lookup"><span data-stu-id="2487b-134">Represents the grantor granting the permissions.</span></span>

| <span data-ttu-id="2487b-135">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2487b-135">Property</span></span>             | <span data-ttu-id="2487b-136">Type</span><span class="sxs-lookup"><span data-stu-id="2487b-136">Type</span></span>|<span data-ttu-id="2487b-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2487b-137">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="2487b-138">GrantorType</span><span class="sxs-lookup"><span data-stu-id="2487b-138">GrantorType</span></span>          | <span data-ttu-id="2487b-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2487b-139">string</span></span>                           | <span data-ttu-id="2487b-140">De grantor die toegang verleent, geaccepteerde waarden: BillToPartner.</span><span class="sxs-lookup"><span data-stu-id="2487b-140">The grantor granting access, accepted values: BillToPartner.</span></span>                               |
| <span data-ttu-id="2487b-141">TenantID</span><span class="sxs-lookup"><span data-stu-id="2487b-141">TenantID</span></span>             | <span data-ttu-id="2487b-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2487b-142">string</span></span>                           | <span data-ttu-id="2487b-143">De tenant-id van de entiteit die toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="2487b-143">The tenant identifier of the entity granting access.</span></span>                                       |


## <a name="permission"></a><span data-ttu-id="2487b-144">Machtiging</span><span class="sxs-lookup"><span data-stu-id="2487b-144">Permission</span></span>

<span data-ttu-id="2487b-145">Vertegenwoordigt een machtiging in het beleid voor self-serve.</span><span class="sxs-lookup"><span data-stu-id="2487b-145">Represents a permission in the self serve policy.</span></span>

| <span data-ttu-id="2487b-146">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2487b-146">Property</span></span>             | <span data-ttu-id="2487b-147">Type</span><span class="sxs-lookup"><span data-stu-id="2487b-147">Type</span></span>|<span data-ttu-id="2487b-148">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2487b-148">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="2487b-149">Resource</span><span class="sxs-lookup"><span data-stu-id="2487b-149">Resource</span></span>             | <span data-ttu-id="2487b-150">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2487b-150">string</span></span>                           | <span data-ttu-id="2487b-151">De toegang tot de resource wordt ook verleend: AzureReservedInstances.</span><span class="sxs-lookup"><span data-stu-id="2487b-151">The resource access is being granted too: AzureReservedInstances.</span></span>                          |
| <span data-ttu-id="2487b-152">Bewerking</span><span class="sxs-lookup"><span data-stu-id="2487b-152">Action</span></span>               | <span data-ttu-id="2487b-153">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2487b-153">string</span></span>                           | <span data-ttu-id="2487b-154">Er wordt toegang verleend tot de actie voor: Aankoop</span><span class="sxs-lookup"><span data-stu-id="2487b-154">The action access is being granted for: Purchase</span></span>                                           |
