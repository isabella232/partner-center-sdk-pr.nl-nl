---
title: Mogelijkheden van indirecte CSP-provider in de sandbox
description: Indirecte providers kunnen indirecte resellers in de sandbox maken voor testdoeleinden.
ms.date: 05/20/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vinayks-ms
ms.author: vinayks
ms.openlocfilehash: bd0f38103e6b6f93ab5da386042b00801b683ccd
ms.sourcegitcommit: 1aeaa12705a5945b8aab6bca254fedebd9c8bc4e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/21/2021
ms.locfileid: "110244603"
---
# <a name="csp-indirect-provider-sandbox-capabilities-for-creating-indirect-reseller-accounts"></a><span data-ttu-id="d174a-103">Sandbox-mogelijkheden van indirecte CSP-provider voor het maken van indirecte reselleraccounts</span><span class="sxs-lookup"><span data-stu-id="d174a-103">CSP Indirect provider sandbox capabilities for creating Indirect reseller accounts</span></span> 

<span data-ttu-id="d174a-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="d174a-104">**Applies to**</span></span>

- <span data-ttu-id="d174a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d174a-105">Partner Center</span></span>

<span data-ttu-id="d174a-106">**Juiste rollen**</span><span class="sxs-lookup"><span data-stu-id="d174a-106">**Appropriate roles**</span></span>

- <span data-ttu-id="d174a-107">Indirecte provider</span><span class="sxs-lookup"><span data-stu-id="d174a-107">Indirect provider</span></span>

<span data-ttu-id="d174a-108">Indirecte CSP-providers kunnen een CSP Indirect Reseller Sandbox-account maken via hun eigen Sandbox-account op laag 2 in Partner Center portal.</span><span class="sxs-lookup"><span data-stu-id="d174a-108">CSP Indirect Providers can create a CSP Indirect Reseller Sandbox account via through their own Tier 2 Sandbox account in Partner Center portal.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="d174a-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d174a-109">Prerequisites</span></span> 

<span data-ttu-id="d174a-110">Partner Center sandboxreferenties voor indirecte provider (laag 2).</span><span class="sxs-lookup"><span data-stu-id="d174a-110">Partner Center Indirect Provider (Tier 2) sandbox credentials.</span></span> <span data-ttu-id="d174a-111">Het sandboxscenario ondersteunt verificatie met zowel de zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="d174a-111">The sandbox scenario supports authentication with both the standalone App and App+User credentials.</span></span> 
 

## <a name="sandbox-indirect-provider--create-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a><span data-ttu-id="d174a-112">Indirecte sandboxprovider: indirecte sandbox-reseller maken met behulp van Partner Center gebruikersinterface</span><span class="sxs-lookup"><span data-stu-id="d174a-112">Sandbox Indirect Provider – Create Sandbox Indirect Reseller using the Partner Center user interface</span></span> 

 <span data-ttu-id="d174a-113">Dit is een sandbox- alleen functie waarmee indirecte sandboxproviders via de portal van de sandbox een indirect Reseller-account Partner Center sandbox.</span><span class="sxs-lookup"><span data-stu-id="d174a-113">This is a Sandbox- only feature that allows Sandbox Indirect Providers the ability to create Sandbox Indirect Reseller account through the Partner Center portal.</span></span>

<span data-ttu-id="d174a-114">De volgende scenario's zijn wat indirecte providers kunnen doen voor indirecte resellers in Sandbox via Partner Center gebruikersinterface:</span><span class="sxs-lookup"><span data-stu-id="d174a-114">The following scenarios are what Indirect providers can do for indirect resellers in Sandbox through the Partner Center user interface:</span></span> 

1. <span data-ttu-id="d174a-115">Indirecte CSP-providers kunnen een CSP Indirect Reseller Sandbox-account maken via hun eigen Sandbox-account op laag 2 in Partner Center portal.</span><span class="sxs-lookup"><span data-stu-id="d174a-115">CSP Indirect Providers can create a CSP Indirect Reseller Sandbox account through their own Tier 2 Sandbox account in Partner Center portal.</span></span>
2. <span data-ttu-id="d174a-116">Indirecte CSP-resellers kunnen klanten weergeven op indirecte providers.</span><span class="sxs-lookup"><span data-stu-id="d174a-116">CSP Indirect Resellers can view customer by Indirect Providers.</span></span> 

1. <span data-ttu-id="d174a-117">Indirecte CSP-resellers kunnen het klantaccount beheren met gedelegeerde beheerdersmachtigingen.</span><span class="sxs-lookup"><span data-stu-id="d174a-117">CSP Indirect Resellers  can manage the customer account using delegated admin permissions.</span></span>

1. <span data-ttu-id="d174a-118">Indirecte CSP-providers kunnen indirecte CSP-resellers uitnodigen.</span><span class="sxs-lookup"><span data-stu-id="d174a-118">CSP Indirect Providers can invite CSP Indirect Resellers.</span></span>
 
1. <span data-ttu-id="d174a-119">Indirecte CSP-providers kunnen een CSP Indirect Reseller Sandbox-account verwijderen via hun eigen Sandbox-account op laag 2 in Partner Center portal.</span><span class="sxs-lookup"><span data-stu-id="d174a-119">CSP Indirect Providers can delete a CSP Indirect Reseller Sandbox account through their own Tier 2 Sandbox account in Partner Center portal.</span></span>

    <span data-ttu-id="d174a-120">a.</span><span class="sxs-lookup"><span data-stu-id="d174a-120">a.</span></span>  <span data-ttu-id="d174a-121">Wanneer de indirecte sandboxprovider de relatie met de indirecte sandbox-reseller verwijdert.</span><span class="sxs-lookup"><span data-stu-id="d174a-121">When Sandbox Indirect Provider deletes relationship with Sandbox Indirect Reseller.</span></span>

    <span data-ttu-id="d174a-122">b.</span><span class="sxs-lookup"><span data-stu-id="d174a-122">b.</span></span>  <span data-ttu-id="d174a-123">Controleer of de indirecte reseller een andere relatie heeft met andere providers.</span><span class="sxs-lookup"><span data-stu-id="d174a-123">Check if the Indirect Reseller has any other relationship with other providers.</span></span> <span data-ttu-id="d174a-124">Als dat het zo is, wordt alleen de relatie met die specifieke indirecte provider verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d174a-124">If so, only the relationship with that specific Indirect provider will be removed.</span></span>

    <span data-ttu-id="d174a-125">c.</span><span class="sxs-lookup"><span data-stu-id="d174a-125">c.</span></span> <span data-ttu-id="d174a-126">Als dit de enige relatie voor de IR is, wordt de IR verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d174a-126">If that is the only relationship for the IR, then the IR will be deleted.</span></span>

1. <span data-ttu-id="d174a-127">CSP Indirect Provider kunt een CSP Indirect Reseller.</span><span class="sxs-lookup"><span data-stu-id="d174a-127">CSP Indirect Provider can delete a CSP Indirect Reseller.</span></span>

    <span data-ttu-id="d174a-128">a.</span><span class="sxs-lookup"><span data-stu-id="d174a-128">a.</span></span> <span data-ttu-id="d174a-129">Dit is een functie voor alleen sandboxs waarmee indirecte Sandbox-providers indirecte resellers kunnen verwijderen.</span><span class="sxs-lookup"><span data-stu-id="d174a-129">This is a Sandbox-only feature that allows Sandbox Indirect Providers the ability to delete Sandbox Indirect Resellers.</span></span>
     
1. <span data-ttu-id="d174a-130">Vereisten voor het verwijderen van een indirecte sandbox-reseller:</span><span class="sxs-lookup"><span data-stu-id="d174a-130">Pre-requisites for deleting a Sandbox Indirect Reseller:</span></span>

    1. <span data-ttu-id="d174a-131">De abonnementen voor elke klant van de indirecte sandbox-reseller opschorten.</span><span class="sxs-lookup"><span data-stu-id="d174a-131">Suspend the subscriptions for each customer of Sandbox Indirect Reseller.</span></span>

    1. <span data-ttu-id="d174a-132">Verwijder alle klanten van indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="d174a-132">Delete all customers of Indirect Reseller.</span></span>

1. <span data-ttu-id="d174a-133">Limiet van 5 indirecte sandbox-resellers die zijn toegestaan per indirecte sandboxprovider.</span><span class="sxs-lookup"><span data-stu-id="d174a-133">Limit of 5 Sandbox Indirect Resellers allowed per Sandbox Indirect Provider.</span></span> <span data-ttu-id="d174a-134">Zodra de indirecte sandbox-reseller is verwijderd, wordt het quotum opnieuw ingesteld.</span><span class="sxs-lookup"><span data-stu-id="d174a-134">Once the Sandbox Indirect reseller is deleted, the quota will be reset.</span></span>

### <a name="pre-requisites"></a><span data-ttu-id="d174a-135">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d174a-135">Pre-requisites</span></span>

- <span data-ttu-id="d174a-136">Limiet van 5 indirecte sandbox-resellers die zijn toegestaan per indirecte sandboxprovider.</span><span class="sxs-lookup"><span data-stu-id="d174a-136">Limit of 5 Sandbox Indirect Resellers allowed per Sandbox Indirect Provider.</span></span> 

- <span data-ttu-id="d174a-137">Dezelfde MPN-id kan worden gebruikt om meerdere Sandbox-accounts voor indirecte resellers te maken als het land van de MPN-id en het land van de sandbox voor indirecte resellers hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="d174a-137">Same MPN ID can be used to create multiple Indirect Reseller Sandbox accounts if MPN ID country and Indirect Reseller Sandbox country are same.</span></span> <span data-ttu-id="d174a-138">Als u een MPN-test-id beschikbaar hebt, kunt u deze gebruiken of kunt u een lijst met MPN-id's krijgen via ons [Yammer-kanaal]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 ).</span><span class="sxs-lookup"><span data-stu-id="d174a-138">If you have a test MPN ID available, you can use it, or you can get a list of MPN IDs through our [Yammer channel]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 ).</span></span> <span data-ttu-id="d174a-139">Als u geen toegang hebt tot Yammer, vraagt Yammer u om toegang aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="d174a-139">If you don’t have access to Yammer, Yammer will ask you to request access.</span></span>
 
- <span data-ttu-id="d174a-140">Slechts 75 klanten zijn toegestaan per indirecte sandboxprovider</span><span class="sxs-lookup"><span data-stu-id="d174a-140">Only 75 customers are allowed per Sandbox Indirect Provider</span></span>

## <a name="create-csp-indirect-reseller-sandbox-account"></a><span data-ttu-id="d174a-141">Een sandbox CSP Indirect Reseller account maken</span><span class="sxs-lookup"><span data-stu-id="d174a-141">Create CSP Indirect Reseller Sandbox account</span></span>

1. <span data-ttu-id="d174a-142">Meld u Partner Center via uw Sandbox-account op laag 2.</span><span class="sxs-lookup"><span data-stu-id="d174a-142">Sign into Partner Center via your Tier 2 Sandbox account.</span></span> 

2. <span data-ttu-id="d174a-143">Navigeer in het linkermenu naar Indirecte resellers.</span><span class="sxs-lookup"><span data-stu-id="d174a-143">Navigate to Indirect Resellers from the left menu.</span></span> 

3. <span data-ttu-id="d174a-144">Klik op de knop Sandbox voor reseller toevoegen.</span><span class="sxs-lookup"><span data-stu-id="d174a-144">Click on “Add Reseller Sandbox” button.</span></span> 

4. <span data-ttu-id="d174a-145">Vul het formulier voor accountinschrijving in.</span><span class="sxs-lookup"><span data-stu-id="d174a-145">Fill the account enrollment form.</span></span> <span data-ttu-id="d174a-146">Dit staat voor zichzelf, maar vergeet niet dat u een Sandbox-account maakt voor een indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="d174a-146">It's self-explanatory but remember you are creating a Sandbox account for an Indirect Reseller.</span></span> <span data-ttu-id="d174a-147">Dit account wordt niet gekeurd en wordt geactiveerd zodra u de accountinschrijving hebt voltooien.</span><span class="sxs-lookup"><span data-stu-id="d174a-147">This account won't undergo vetting and will be activated as soon as you finish the account enrollment.</span></span>  

5. <span data-ttu-id="d174a-148">Zodra het account is gemaakt, krijgt u de referenties van de globale beheerder voor het sandbox-account van de indirecte reseller in de portal.</span><span class="sxs-lookup"><span data-stu-id="d174a-148">Once the account is created, you will get the Global Admin credentials for the Indirect Reseller sandbox account on the portal.</span></span> <span data-ttu-id="d174a-149">Vergeet niet om het onmiddellijk op te slaan, anders kunt u zich niet aanmelden als een sandbox voor indirecte resellers.</span><span class="sxs-lookup"><span data-stu-id="d174a-149">Remember to save it immediately,  otherwise, you won't be able to sign in as an Indirect Reseller Sandbox.</span></span> 

6. <span data-ttu-id="d174a-150">Meld u af en meld u opnieuw aan Partner Center met de nieuwe referenties voor sandbox voor indirecte resellers.</span><span class="sxs-lookup"><span data-stu-id="d174a-150">Sign out and sign in again to Partner Center using the new credentials for Indirect Reseller Sandbox.</span></span> <span data-ttu-id="d174a-151">Verken de mogelijkheden die u als indirecte reseller kunt doen.</span><span class="sxs-lookup"><span data-stu-id="d174a-151">Explore the capabilities you can do as an Indirect Reseller.</span></span> <span data-ttu-id="d174a-152">Enkele dingen zijn:</span><span class="sxs-lookup"><span data-stu-id="d174a-152">Some things are :</span></span>  

    - <span data-ttu-id="d174a-153">Profielen beheren</span><span class="sxs-lookup"><span data-stu-id="d174a-153">Manage profiles</span></span>  

    - <span data-ttu-id="d174a-154">Gebruikers en rollen beheren</span><span class="sxs-lookup"><span data-stu-id="d174a-154">Manage users and roles</span></span> 

    - <span data-ttu-id="d174a-155">Indirecte providers beheren</span><span class="sxs-lookup"><span data-stu-id="d174a-155">Manage Indirect Providers</span></span> 

    - <span data-ttu-id="d174a-156">CSP Sandbox-klanten beheren</span><span class="sxs-lookup"><span data-stu-id="d174a-156">Manage CSP Sandbox customers</span></span> 

    - <span data-ttu-id="d174a-157">Relaties beheren</span><span class="sxs-lookup"><span data-stu-id="d174a-157">Manage relationships</span></span>
    
     
## <a name="sandbox-indirect-provider--delete-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a><span data-ttu-id="d174a-158">Indirecte sandboxprovider: indirecte sandbox-reseller verwijderen met behulp van Partner Center gebruikersinterface</span><span class="sxs-lookup"><span data-stu-id="d174a-158">Sandbox Indirect Provider – Delete Sandbox Indirect Reseller using the Partner Center user interface</span></span>

 <span data-ttu-id="d174a-159">Dit is een sandbox-functie waarmee indirecte sandboxproviders een bestaand sandbox-account voor indirecte resellers kunnen verwijderen via Partner Center portal.</span><span class="sxs-lookup"><span data-stu-id="d174a-159">This is a Sandbox only feature that allows Sandbox Indirect Providers an ability to delete an existing Sandbox Indirect Reseller account via Partner Center portal.</span></span> 

### <a name="pre-requisites-to-delete-sandbox-indirect-reseller"></a><span data-ttu-id="d174a-160">Vereisten voor het verwijderen van indirecte sandbox-reseller:</span><span class="sxs-lookup"><span data-stu-id="d174a-160">Pre-requisites to delete sandbox Indirect reseller:</span></span>

<span data-ttu-id="d174a-161">Een bestaand CSP Indirect Reseller Sandbox-account dat is gekoppeld aan uw CSP Indirect Provider Sandbox-account op laag 2.</span><span class="sxs-lookup"><span data-stu-id="d174a-161">An existing CSP Indirect Reseller Sandbox account associated with your own CSP Indirect Provider Tier-2 Sandbox account.</span></span>  
 

## <a name="delete-csp-indirect-reseller-sandbox-account"></a><span data-ttu-id="d174a-162">Een sandbox CSP Indirect Reseller account verwijderen</span><span class="sxs-lookup"><span data-stu-id="d174a-162">Delete CSP Indirect Reseller Sandbox account</span></span>

1. <span data-ttu-id="d174a-163">Meld u Partner Center aan met uw Sandbox-account op laag 2.</span><span class="sxs-lookup"><span data-stu-id="d174a-163">Sign into Partner Center using your Tier 2 Sandbox account.</span></span> 

2. <span data-ttu-id="d174a-164">Navigeer in het linkermenu naar Indirecte resellers.</span><span class="sxs-lookup"><span data-stu-id="d174a-164">Navigate to Indirect Resellers from the left menu.</span></span> 

3. <span data-ttu-id="d174a-165">Klik op **de koppeling Sandbox voor** reseller verwijderen naast het Sandbox-account voor indirecte resellers dat u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="d174a-165">Click on **Delete Reseller Sandbox** link next to the Indirect Reseller Sandbox account you want to delete.</span></span> <span data-ttu-id="d174a-166">Het Sandbox-account voor indirecte resellers wordt permanent verwijderd en kan niet worden hersteld.</span><span class="sxs-lookup"><span data-stu-id="d174a-166">The Indirect Reseller Sandbox account will be permanently deleted and cannot be recovered.</span></span> 

## <a name="api-references"></a><span data-ttu-id="d174a-167">API-referenties</span><span class="sxs-lookup"><span data-stu-id="d174a-167">API references</span></span>

- <span data-ttu-id="d174a-168">Indirecte reseller maken</span><span class="sxs-lookup"><span data-stu-id="d174a-168">Create Indirect Reseller</span></span> 
- <span data-ttu-id="d174a-169">Indirecte reseller verwijderen</span><span class="sxs-lookup"><span data-stu-id="d174a-169">Delete Indirect Reseller</span></span> 

 

 