---
title: Mogelijkheden van indirecte CSP-provider in de sandbox
description: Indirecte providers kunnen indirecte resellers in de sandbox maken voor testdoeleinden.
ms.date: 05/20/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vinayks-ms
ms.author: vinayks
ms.openlocfilehash: da35dadd4e13247e923259a1cf3a67852f4b9e00
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445898"
---
# <a name="csp-indirect-provider-sandbox-capabilities-for-creating-indirect-reseller-accounts"></a><span data-ttu-id="d5042-103">Sandbox-mogelijkheden van indirecte CSP-provider voor het maken van indirecte reselleraccounts</span><span class="sxs-lookup"><span data-stu-id="d5042-103">CSP Indirect provider sandbox capabilities for creating Indirect reseller accounts</span></span> 

<span data-ttu-id="d5042-104">**Juiste rollen:** Indirecte provider</span><span class="sxs-lookup"><span data-stu-id="d5042-104">**Appropriate roles**: Indirect provider</span></span>

<span data-ttu-id="d5042-105">Indirecte CSP-providers kunnen een CSP Indirect Reseller Sandbox-account maken via hun eigen Sandbox-account op laag 2 in Partner Center portal.</span><span class="sxs-lookup"><span data-stu-id="d5042-105">CSP Indirect Providers can create a CSP Indirect Reseller Sandbox account via through their own Tier 2 Sandbox account in Partner Center portal.</span></span>


## <a name="prerequisites"></a><span data-ttu-id="d5042-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d5042-106">Prerequisites</span></span> 

<span data-ttu-id="d5042-107">Partner Center sandboxreferenties voor indirecte provider (laag 2).</span><span class="sxs-lookup"><span data-stu-id="d5042-107">Partner Center Indirect Provider (Tier 2) sandbox credentials.</span></span> <span data-ttu-id="d5042-108">Het sandboxscenario ondersteunt verificatie met zowel de zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="d5042-108">The sandbox scenario supports authentication with both the standalone App and App+User credentials.</span></span> 
 

## <a name="sandbox-indirect-provider--create-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a><span data-ttu-id="d5042-109">Indirecte sandboxprovider: indirecte sandbox-reseller maken met behulp van Partner Center gebruikersinterface</span><span class="sxs-lookup"><span data-stu-id="d5042-109">Sandbox Indirect Provider – Create Sandbox Indirect Reseller using the Partner Center user interface</span></span> 

 <span data-ttu-id="d5042-110">Dit is een sandbox-functie waarmee indirecte sandboxproviders via de portal een sandbox-account voor indirecte resellers Partner Center maken.</span><span class="sxs-lookup"><span data-stu-id="d5042-110">This is a Sandbox-only feature that allows Sandbox Indirect Providers the ability to create a Sandbox Indirect Reseller account through the Partner Center portal.</span></span>

<span data-ttu-id="d5042-111">De volgende scenario's zijn wat indirecte providers kunnen doen voor indirecte resellers in Sandbox via Partner Center gebruikersinterface:</span><span class="sxs-lookup"><span data-stu-id="d5042-111">The following scenarios are what Indirect providers can do for indirect resellers in Sandbox through the Partner Center user interface:</span></span> 

1. <span data-ttu-id="d5042-112">Indirecte CSP-providers kunnen een CSP Indirect Reseller Sandbox-account maken via hun eigen Sandbox-account op laag 2 in Partner Center portal.</span><span class="sxs-lookup"><span data-stu-id="d5042-112">CSP Indirect Providers can create a CSP Indirect Reseller Sandbox account through their own Tier 2 Sandbox account in Partner Center portal.</span></span>
2. <span data-ttu-id="d5042-113">Indirecte CSP-resellers kunnen klanten weergeven op indirecte providers.</span><span class="sxs-lookup"><span data-stu-id="d5042-113">CSP Indirect Resellers can view customer by Indirect Providers.</span></span> 

1. <span data-ttu-id="d5042-114">Indirecte CSP-resellers kunnen het klantaccount beheren met gedelegeerde beheerdersmachtigingen.</span><span class="sxs-lookup"><span data-stu-id="d5042-114">CSP Indirect Resellers can manage the customer account using delegated admin permissions.</span></span>

1. <span data-ttu-id="d5042-115">Indirecte CSP-providers kunnen indirecte CSP-resellers uitnodigen.</span><span class="sxs-lookup"><span data-stu-id="d5042-115">CSP Indirect Providers can invite CSP Indirect Resellers.</span></span>
 
1. <span data-ttu-id="d5042-116">Indirecte CSP-providers kunnen een CSP Indirect Reseller Sandbox-account verwijderen via hun eigen Sandbox-account op laag 2 in Partner Center portal.</span><span class="sxs-lookup"><span data-stu-id="d5042-116">CSP Indirect Providers can delete a CSP Indirect Reseller Sandbox account through their own Tier 2 Sandbox account in Partner Center portal.</span></span>

    <span data-ttu-id="d5042-117">a.</span><span class="sxs-lookup"><span data-stu-id="d5042-117">a.</span></span>  <span data-ttu-id="d5042-118">Wanneer de indirecte sandboxprovider de relatie met de indirecte sandbox-reseller verwijdert, controleert u of de indirecte reseller een andere relatie heeft met andere providers.</span><span class="sxs-lookup"><span data-stu-id="d5042-118">When Sandbox Indirect Provider deletes the relationship with Sandbox Indirect Reseller, check if the Indirect Reseller has any other relationship with other providers.</span></span> <span data-ttu-id="d5042-119">Als dat het zo is, wordt alleen de relatie met die specifieke indirecte provider verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d5042-119">If so, only the relationship with that specific Indirect provider will be removed.</span></span>

    <span data-ttu-id="d5042-120">c.</span><span class="sxs-lookup"><span data-stu-id="d5042-120">c.</span></span> <span data-ttu-id="d5042-121">Als dit de enige relatie voor de indirecte reseller is, wordt de indirecte reseller verwijderd.</span><span class="sxs-lookup"><span data-stu-id="d5042-121">If that is the only relationship for the Indirect Reseller, then the Indirect Reseller will be deleted.</span></span>

1. <span data-ttu-id="d5042-122">Indirecte CSP-providers kunnen een CSP Indirect Reseller.</span><span class="sxs-lookup"><span data-stu-id="d5042-122">CSP Indirect Providers can delete a CSP Indirect Reseller.</span></span>

    <span data-ttu-id="d5042-123">a.</span><span class="sxs-lookup"><span data-stu-id="d5042-123">a.</span></span> <span data-ttu-id="d5042-124">Dit is een functie alleen voor sandboxs waarmee indirecte sandboxproviders sandbox-indirecte resellers kunnen verwijderen.</span><span class="sxs-lookup"><span data-stu-id="d5042-124">This is a Sandbox-only feature that allows Sandbox Indirect Providers the ability to delete Sandbox Indirect Resellers.</span></span>
     
1. <span data-ttu-id="d5042-125">Vereisten voor het verwijderen van een indirecte sandbox-reseller:</span><span class="sxs-lookup"><span data-stu-id="d5042-125">Pre-requisites for deleting a Sandbox Indirect Reseller:</span></span>

    1. <span data-ttu-id="d5042-126">De abonnementen voor elke klant van de indirecte sandbox-reseller opschorten.</span><span class="sxs-lookup"><span data-stu-id="d5042-126">Suspend the subscriptions for each customer of Sandbox Indirect Reseller.</span></span>

    1. <span data-ttu-id="d5042-127">Verwijder alle klanten van indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="d5042-127">Delete all customers of Indirect Reseller.</span></span>

1. <span data-ttu-id="d5042-128">Limiet van vijf indirecte sandbox-resellers die zijn toegestaan per indirecte sandboxprovider.</span><span class="sxs-lookup"><span data-stu-id="d5042-128">Limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider.</span></span> <span data-ttu-id="d5042-129">Zodra de indirecte sandbox-reseller is verwijderd, wordt het quotum opnieuw ingesteld.</span><span class="sxs-lookup"><span data-stu-id="d5042-129">Once the Sandbox Indirect reseller is deleted, the quota will be reset.</span></span>

### <a name="pre-requisites"></a><span data-ttu-id="d5042-130">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d5042-130">Pre-requisites</span></span>

- <span data-ttu-id="d5042-131">Limiet van vijf indirecte sandbox-resellers die zijn toegestaan per indirecte sandboxprovider.</span><span class="sxs-lookup"><span data-stu-id="d5042-131">Limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider.</span></span> 

- <span data-ttu-id="d5042-132">Dezelfde MPN-id kan worden gebruikt om meerdere Sandbox-accounts voor indirecte resellers te maken als het land van de MPN-id en het land van de sandbox voor indirecte resellers hetzelfde zijn.</span><span class="sxs-lookup"><span data-stu-id="d5042-132">Same MPN ID can be used to create multiple Indirect Reseller Sandbox accounts if MPN ID country and Indirect Reseller Sandbox country are same.</span></span> <span data-ttu-id="d5042-133">Als u een MPN-test-id beschikbaar hebt, kunt u deze gebruiken of een lijst met MPN-id's krijgen via ons [Yammer kanaal]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 ).</span><span class="sxs-lookup"><span data-stu-id="d5042-133">If you have a test MPN ID available, you can use it, or you can get a list of MPN IDs through our [Yammer channel]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 ).</span></span> <span data-ttu-id="d5042-134">Als u geen toegang hebt tot Yammer, Yammer u om toegang aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="d5042-134">If you don’t have access to Yammer, Yammer will ask you to request access.</span></span>
 
- <span data-ttu-id="d5042-135">Slechts 75 klanten zijn toegestaan per indirecte sandboxprovider</span><span class="sxs-lookup"><span data-stu-id="d5042-135">Only 75 customers are allowed per Sandbox Indirect Provider</span></span>

## <a name="create-csp-indirect-reseller-sandbox-account"></a><span data-ttu-id="d5042-136">Een sandbox CSP Indirect Reseller account maken</span><span class="sxs-lookup"><span data-stu-id="d5042-136">Create CSP Indirect Reseller Sandbox account</span></span>

1. <span data-ttu-id="d5042-137">Meld u aan Partner Center via uw Sandbox-account op laag 2.</span><span class="sxs-lookup"><span data-stu-id="d5042-137">Sign into Partner Center via your Tier 2 Sandbox account.</span></span> 

2. <span data-ttu-id="d5042-138">Navigeer in het linkermenu naar Indirecte resellers.</span><span class="sxs-lookup"><span data-stu-id="d5042-138">Navigate to Indirect Resellers from the left menu.</span></span> 

3. <span data-ttu-id="d5042-139">Selecteer de **knop Sandbox voor reseller** toevoegen.</span><span class="sxs-lookup"><span data-stu-id="d5042-139">Select the **Add Reseller Sandbox** button.</span></span> 

4. <span data-ttu-id="d5042-140">Vul het formulier voor accountinschrijving in.</span><span class="sxs-lookup"><span data-stu-id="d5042-140">Fill the account enrollment form.</span></span> <span data-ttu-id="d5042-141">Het spreekt voor zich, maar vergeet niet dat u een Sandbox-account maakt voor een indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="d5042-141">It's self-explanatory but remember you are creating a Sandbox account for an Indirect Reseller.</span></span> <span data-ttu-id="d5042-142">Dit account wordt niet gekeurd en wordt geactiveerd zodra u de accountinschrijving hebt voltooien.</span><span class="sxs-lookup"><span data-stu-id="d5042-142">This account won't undergo vetting and will be activated as soon as you finish the account enrollment.</span></span>  

5. <span data-ttu-id="d5042-143">Zodra het account is gemaakt, krijgt u de globale beheerdersreferenties voor het sandbox-account voor indirecte resellers in de portal.</span><span class="sxs-lookup"><span data-stu-id="d5042-143">Once the account is created, you will get the Global Admin credentials for the Indirect Reseller sandbox account on the portal.</span></span> <span data-ttu-id="d5042-144">Vergeet niet om het onmiddellijk op te slaan, anders kunt u zich niet aanmelden als een sandbox voor indirecte resellers.</span><span class="sxs-lookup"><span data-stu-id="d5042-144">Remember to save it immediately,  otherwise, you won't be able to sign in as an Indirect Reseller Sandbox.</span></span> 

6. <span data-ttu-id="d5042-145">Meld u af en meld u opnieuw aan Partner Center met de nieuwe referenties voor de Sandbox voor indirecte resellers.</span><span class="sxs-lookup"><span data-stu-id="d5042-145">Sign out and sign in again to Partner Center using the new credentials for Indirect Reseller Sandbox.</span></span> <span data-ttu-id="d5042-146">Verken de mogelijkheden die u als indirecte reseller kunt doen.</span><span class="sxs-lookup"><span data-stu-id="d5042-146">Explore the capabilities you can do as an Indirect Reseller.</span></span> <span data-ttu-id="d5042-147">Dit zijn enkele dingen:</span><span class="sxs-lookup"><span data-stu-id="d5042-147">Some things are:</span></span>  

    - <span data-ttu-id="d5042-148">Profielen beheren</span><span class="sxs-lookup"><span data-stu-id="d5042-148">Manage profiles</span></span>  

    - <span data-ttu-id="d5042-149">Gebruikers en rollen beheren</span><span class="sxs-lookup"><span data-stu-id="d5042-149">Manage users and roles</span></span> 

    - <span data-ttu-id="d5042-150">Indirecte providers beheren</span><span class="sxs-lookup"><span data-stu-id="d5042-150">Manage Indirect Providers</span></span> 

    - <span data-ttu-id="d5042-151">CSP Sandbox-klanten beheren</span><span class="sxs-lookup"><span data-stu-id="d5042-151">Manage CSP Sandbox customers</span></span> 

    - <span data-ttu-id="d5042-152">Relaties beheren</span><span class="sxs-lookup"><span data-stu-id="d5042-152">Manage relationships</span></span>
    
     
## <a name="sandbox-indirect-provider--delete-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a><span data-ttu-id="d5042-153">Indirecte sandboxprovider: indirecte sandbox-reseller verwijderen met behulp van Partner Center gebruikersinterface</span><span class="sxs-lookup"><span data-stu-id="d5042-153">Sandbox Indirect Provider – Delete Sandbox Indirect Reseller using the Partner Center user interface</span></span>

 <span data-ttu-id="d5042-154">Dit is een sandbox-functie waarmee indirecte sandboxproviders een bestaand sandbox-account voor indirecte resellers kunnen verwijderen via Partner Center portal.</span><span class="sxs-lookup"><span data-stu-id="d5042-154">This is a Sandbox only feature that allows Sandbox Indirect Providers an ability to delete an existing Sandbox Indirect Reseller account via Partner Center portal.</span></span> 

### <a name="pre-requisites-to-delete-sandbox-indirect-reseller"></a><span data-ttu-id="d5042-155">Vereisten voor het verwijderen van indirecte sandbox-reseller:</span><span class="sxs-lookup"><span data-stu-id="d5042-155">Pre-requisites to delete sandbox Indirect reseller:</span></span>

<span data-ttu-id="d5042-156">Een bestaand CSP Indirect Reseller Sandbox-account dat is gekoppeld aan uw CSP Indirect Provider Sandbox-account op laag 2.</span><span class="sxs-lookup"><span data-stu-id="d5042-156">An existing CSP Indirect Reseller Sandbox account associated with your own CSP Indirect Provider Tier-2 Sandbox account.</span></span>  
 

## <a name="delete-csp-indirect-reseller-sandbox-account"></a><span data-ttu-id="d5042-157">Een sandbox CSP Indirect Reseller account verwijderen</span><span class="sxs-lookup"><span data-stu-id="d5042-157">Delete CSP Indirect Reseller Sandbox account</span></span>

1. <span data-ttu-id="d5042-158">Meld u Partner Center aan met uw Sandbox-account op laag 2.</span><span class="sxs-lookup"><span data-stu-id="d5042-158">Sign into Partner Center using your Tier 2 Sandbox account.</span></span> 

2. <span data-ttu-id="d5042-159">Navigeer in het linkermenu naar Indirecte resellers.</span><span class="sxs-lookup"><span data-stu-id="d5042-159">Navigate to Indirect Resellers from the left menu.</span></span> 

3. <span data-ttu-id="d5042-160">Selecteer de **koppeling Sandbox voor reseller** verwijderen naast het Sandbox-account voor indirecte resellers dat u wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="d5042-160">Select the **Delete Reseller Sandbox** link next to the Indirect Reseller Sandbox account you want to delete.</span></span> <span data-ttu-id="d5042-161">Het Sandbox-account voor indirecte resellers wordt permanent verwijderd en kan niet worden hersteld.</span><span class="sxs-lookup"><span data-stu-id="d5042-161">The Indirect Reseller Sandbox account will be permanently deleted and cannot be recovered.</span></span> 

## <a name="api-references"></a><span data-ttu-id="d5042-162">API-referenties</span><span class="sxs-lookup"><span data-stu-id="d5042-162">API references</span></span>

- <span data-ttu-id="d5042-163">Indirecte reseller maken</span><span class="sxs-lookup"><span data-stu-id="d5042-163">Create Indirect Reseller</span></span> 
- <span data-ttu-id="d5042-164">Indirecte reseller verwijderen</span><span class="sxs-lookup"><span data-stu-id="d5042-164">Delete Indirect Reseller</span></span> 

 

 