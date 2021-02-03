---
title: Zelf beleids resources beheren
description: Een partner stelt zelf het beleid voor een klant in.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 04daf6aaeb69153c4139941188f53dbab8979969
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767245"
---
# <a name="selfservepolicy-resource"></a><span data-ttu-id="50616-103">SelfServePolicy-resource</span><span class="sxs-lookup"><span data-stu-id="50616-103">SelfServePolicy resource</span></span>

<span data-ttu-id="50616-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="50616-104">**Applies to:**</span></span>

- <span data-ttu-id="50616-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="50616-105">Partner Center</span></span>

<span data-ttu-id="50616-106">Een partner stelt zelf het beleid voor een klant in.</span><span class="sxs-lookup"><span data-stu-id="50616-106">A partner sets self serve policies for a customer.</span></span>

## <a name="selfservepolicy"></a><span data-ttu-id="50616-107">SelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="50616-107">SelfServePolicy</span></span>

<span data-ttu-id="50616-108">Hierin wordt een winkel wagen beschreven.</span><span class="sxs-lookup"><span data-stu-id="50616-108">Describes a cart.</span></span>

| <span data-ttu-id="50616-109">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="50616-109">Property</span></span>              | <span data-ttu-id="50616-110">Type</span><span class="sxs-lookup"><span data-stu-id="50616-110">Type</span></span>             | <span data-ttu-id="50616-111">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="50616-111">Description</span></span>                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="50616-112">id</span><span class="sxs-lookup"><span data-stu-id="50616-112">id</span></span>                    | <span data-ttu-id="50616-113">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="50616-113">string</span></span>           | <span data-ttu-id="50616-114">Een selfservice beleids-id die wordt geleverd bij het maken van het beleid voor eigen beheer.</span><span class="sxs-lookup"><span data-stu-id="50616-114">A self serve policy identifier that is supplied upon successful creation of the self serve policy.</span></span>     |
| <span data-ttu-id="50616-115">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="50616-115">SelfServeEntity</span></span>       | <span data-ttu-id="50616-116">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="50616-116">SelfServeEntity</span></span>  | <span data-ttu-id="50616-117">De selfservice-entiteit waaraan toegang wordt verleend.</span><span class="sxs-lookup"><span data-stu-id="50616-117">The self serve entity that is being granted access.</span></span>                                                     |
| <span data-ttu-id="50616-118">Verlener</span><span class="sxs-lookup"><span data-stu-id="50616-118">Grantor</span></span>               | <span data-ttu-id="50616-119">Verlener</span><span class="sxs-lookup"><span data-stu-id="50616-119">Grantor</span></span>          | <span data-ttu-id="50616-120">De subsidie die toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="50616-120">The grantor that is granting access.</span></span>                                                                    |
| <span data-ttu-id="50616-121">Machtigingen</span><span class="sxs-lookup"><span data-stu-id="50616-121">Permissions</span></span>           | <span data-ttu-id="50616-122">Matrix van machtigingen</span><span class="sxs-lookup"><span data-stu-id="50616-122">Array of Permission</span></span>| <span data-ttu-id="50616-123">Een matrix met [machtigings](#permission) bronnen.</span><span class="sxs-lookup"><span data-stu-id="50616-123">An Array of [Permission](#permission) resources.</span></span>                                                                     |

## <a name="selfserveentity"></a><span data-ttu-id="50616-124">SelfServeEntity</span><span class="sxs-lookup"><span data-stu-id="50616-124">SelfServeEntity</span></span>

<span data-ttu-id="50616-125">Vertegenwoordigt de entiteit waaraan machtigingen worden verleend.</span><span class="sxs-lookup"><span data-stu-id="50616-125">Represents the entity being granted permissions.</span></span>

| <span data-ttu-id="50616-126">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="50616-126">Property</span></span>             | <span data-ttu-id="50616-127">Type</span><span class="sxs-lookup"><span data-stu-id="50616-127">Type</span></span>|<span data-ttu-id="50616-128">Description</span><span class="sxs-lookup"><span data-stu-id="50616-128">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="50616-129">SelfServeEntityType</span><span class="sxs-lookup"><span data-stu-id="50616-129">SelfServeEntityType</span></span>  | <span data-ttu-id="50616-130">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="50616-130">string</span></span>                           | <span data-ttu-id="50616-131">De entiteit waaraan toegang is verleend, geaccepteerde waarden: klant.</span><span class="sxs-lookup"><span data-stu-id="50616-131">The entity being granted access, accepted values: Customer.</span></span>                                 |
| <span data-ttu-id="50616-132">TenantID</span><span class="sxs-lookup"><span data-stu-id="50616-132">TenantID</span></span>             | <span data-ttu-id="50616-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="50616-133">string</span></span>                           | <span data-ttu-id="50616-134">De Tenant-id van de entiteit waaraan toegang wordt verleend.</span><span class="sxs-lookup"><span data-stu-id="50616-134">The tenant identifier of the entity being granted access.</span></span>                                   |

## <a name="grantor"></a><span data-ttu-id="50616-135">Verlener</span><span class="sxs-lookup"><span data-stu-id="50616-135">Grantor</span></span>

<span data-ttu-id="50616-136">Hiermee wordt de verlener aangeduid die de machtigingen verleent.</span><span class="sxs-lookup"><span data-stu-id="50616-136">Represents the grantor granting the permissions.</span></span>

| <span data-ttu-id="50616-137">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="50616-137">Property</span></span>             | <span data-ttu-id="50616-138">Type</span><span class="sxs-lookup"><span data-stu-id="50616-138">Type</span></span>|<span data-ttu-id="50616-139">Description</span><span class="sxs-lookup"><span data-stu-id="50616-139">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="50616-140">GrantorType</span><span class="sxs-lookup"><span data-stu-id="50616-140">GrantorType</span></span>          | <span data-ttu-id="50616-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="50616-141">string</span></span>                           | <span data-ttu-id="50616-142">De granting verleent toegang, geaccepteerde waarden: BillToPartner.</span><span class="sxs-lookup"><span data-stu-id="50616-142">The grantor granting access, accepted values: BillToPartner.</span></span>                               |
| <span data-ttu-id="50616-143">TenantID</span><span class="sxs-lookup"><span data-stu-id="50616-143">TenantID</span></span>             | <span data-ttu-id="50616-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="50616-144">string</span></span>                           | <span data-ttu-id="50616-145">De Tenant-id van de entiteit die toegang verleent.</span><span class="sxs-lookup"><span data-stu-id="50616-145">The tenant identifier of the entity granting access.</span></span>                                       |


## <a name="permission"></a><span data-ttu-id="50616-146">Machtiging</span><span class="sxs-lookup"><span data-stu-id="50616-146">Permission</span></span>

<span data-ttu-id="50616-147">Hiermee wordt een machtiging in het beleid voor zelf beheer aangeduid.</span><span class="sxs-lookup"><span data-stu-id="50616-147">Represents a permission in the self serve policy.</span></span>

| <span data-ttu-id="50616-148">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="50616-148">Property</span></span>             | <span data-ttu-id="50616-149">Type</span><span class="sxs-lookup"><span data-stu-id="50616-149">Type</span></span>|<span data-ttu-id="50616-150">Description</span><span class="sxs-lookup"><span data-stu-id="50616-150">Description</span></span>|
|----------------------|----------------------------------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="50616-151">Resource</span><span class="sxs-lookup"><span data-stu-id="50616-151">Resource</span></span>             | <span data-ttu-id="50616-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="50616-152">string</span></span>                           | <span data-ttu-id="50616-153">De toegang tot de resource is te klein: AzureReservedInstances.</span><span class="sxs-lookup"><span data-stu-id="50616-153">The resource access is being granted too: AzureReservedInstances.</span></span>                          |
| <span data-ttu-id="50616-154">Bewerking</span><span class="sxs-lookup"><span data-stu-id="50616-154">Action</span></span>               | <span data-ttu-id="50616-155">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="50616-155">string</span></span>                           | <span data-ttu-id="50616-156">De actie toegang wordt verleend voor: aankoop</span><span class="sxs-lookup"><span data-stu-id="50616-156">The action access is being granted for: Purchase</span></span>                                           |
