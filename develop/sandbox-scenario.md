---
title: Sandbox-mogelijkheden voor reseller-relatie
description: Partner-sandbox biedt de mogelijkheid om relaties tussen de partner en de klant te ondersteunen
ms.date: 05/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9bef4a15685ebbdc2212988f5ac5724b946cfd54
ms.sourcegitcommit: 1aeaa12705a5945b8aab6bca254fedebd9c8bc4e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/21/2021
ms.locfileid: "110243381"
---
# <a name="sandbox-capabilities-for-reseller-relationship"></a><span data-ttu-id="9a067-103">Sandbox-mogelijkheden voor reseller-relatie</span><span class="sxs-lookup"><span data-stu-id="9a067-103">Sandbox capabilities for Reseller relationship</span></span>

<span data-ttu-id="9a067-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="9a067-104">**Applies to:**</span></span>

- <span data-ttu-id="9a067-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="9a067-105">Partner Center</span></span>
- <span data-ttu-id="9a067-106">Partnercentrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="9a067-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="9a067-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="9a067-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="9a067-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9a067-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="9a067-109">In dit artikel wordt uitgelegd wat er wordt ondersteund in de Sandbox voor resellerrelaties tussen de partner en de klant.</span><span class="sxs-lookup"><span data-stu-id="9a067-109">This article explains what is supported in the Sandbox for reseller relationships between the partner and the customer.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="9a067-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9a067-110">Prerequisites</span></span>

- <span data-ttu-id="9a067-111">Partner Center accountreferenties.</span><span class="sxs-lookup"><span data-stu-id="9a067-111">Partner Center account credentials.</span></span> <span data-ttu-id="9a067-112">Het sandboxscenario ondersteunt verificatie met zowel de zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="9a067-112">The sandbox scenario supports authentication with both the standalone App and App+User credentials.</span></span>
- <span data-ttu-id="9a067-113">Een klant-id (klant-tenant-id).</span><span class="sxs-lookup"><span data-stu-id="9a067-113">A customer ID (customer-tenant-id).</span></span> <span data-ttu-id="9a067-114">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard/home).</span><span class="sxs-lookup"><span data-stu-id="9a067-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard/home).</span></span> <span data-ttu-id="9a067-115">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="9a067-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="9a067-116">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="9a067-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="9a067-117">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="9a067-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="9a067-118">De Microsoft-id is hetzelfde als de klant-id (klant-tenant-id).</span><span class="sxs-lookup"><span data-stu-id="9a067-118">The Microsoft ID is the same as the customer ID (customer-tenant-id).</span></span>
- <span data-ttu-id="9a067-119">Alle Azure Reserved Virtual Machine Instances en software-aankooporders moeten worden geannuleerd voordat u een klant uit de Sandbox voor tipintegratie kunt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="9a067-119">All Azure Reserved Virtual Machine Instances and software purchase orders must be canceled before deleting a customer from the Tip integration sandbox.</span></span>

## <a name="scenarios-supporting-reseller-relationship"></a><span data-ttu-id="9a067-120">Scenario's die een resellerrelatie ondersteunen</span><span class="sxs-lookup"><span data-stu-id="9a067-120">Scenarios Supporting Reseller Relationship</span></span>

1.  <span data-ttu-id="9a067-121">Sandbox-partners voor directe factuur en indirecte providers kunnen relaties met de Sandbox-klant maken.</span><span class="sxs-lookup"><span data-stu-id="9a067-121">Sandbox Direct Bill Partners and Indirect Providers can create relationships with the Sandbox customer.</span></span> 
2.  <span data-ttu-id="9a067-122">Sandbox Directe factuurpartners en indirecte providers kunnen sandbox-klanten niet uitnodigen.</span><span class="sxs-lookup"><span data-stu-id="9a067-122">Sandbox Direct Bill Partners and Indirect Providers cannot invite Sandbox customers.</span></span>

3. <span data-ttu-id="9a067-123">Sandbox Direct Bill Partner en indirecte providers kunnen de resellerrelatie verwijderen uit Partner Center gebruikersinterface en API.</span><span class="sxs-lookup"><span data-stu-id="9a067-123">Sandbox Direct Bill Partner and Indirect Providers are able to remove reseller relationship from Partner Center UI and API.</span></span>

4. <span data-ttu-id="9a067-124">Met de Sandbox Remove Reseller-relatie wordt klant-AP verwijderen aanroepen.</span><span class="sxs-lookup"><span data-stu-id="9a067-124">Sandbox Remove Reseller Relationship will call Delete customer AP.</span></span> <span data-ttu-id="9a067-125">Hiermee verwijdert u de relatie en verwijdert u de tenant van de klant.</span><span class="sxs-lookup"><span data-stu-id="9a067-125">This will remove the relationship as well as delete the customer tenant.</span></span> <span data-ttu-id="9a067-126">{baseURL}/v1/Customers/{customer-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="9a067-126">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span>


    ### <a name="in-the-sandbox"></a><span data-ttu-id="9a067-127">In de sandbox</span><span class="sxs-lookup"><span data-stu-id="9a067-127">In the Sandbox</span></span>

    <span data-ttu-id="9a067-128">**Partners voor directe factuur:**</span><span class="sxs-lookup"><span data-stu-id="9a067-128">**Direct bill partners**:</span></span>

    - <span data-ttu-id="9a067-129">Kan bestaande klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="9a067-129">Can add existing customers</span></span>

    - <span data-ttu-id="9a067-130">Kan geen relaties met nieuwe klanten aanvragen</span><span class="sxs-lookup"><span data-stu-id="9a067-130">Cannot request relationships with new customers</span></span>

    <span data-ttu-id="9a067-131">**Indirecte providers:**</span><span class="sxs-lookup"><span data-stu-id="9a067-131">**Indirect providers**:</span></span>

    - <span data-ttu-id="9a067-132">Kan bestaande klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="9a067-132">Can add existing customers</span></span>

    - <span data-ttu-id="9a067-133">Kan geen relaties met nieuwe klanten aanvragen</span><span class="sxs-lookup"><span data-stu-id="9a067-133">Cannot request relationships with new customers</span></span>

    - <span data-ttu-id="9a067-134">Kan geen relatie hebben met een indirecte reseller</span><span class="sxs-lookup"><span data-stu-id="9a067-134">Cannot have a relationship with an Indirect reseller</span></span>

    <span data-ttu-id="9a067-135">**Indirecte reseller:**</span><span class="sxs-lookup"><span data-stu-id="9a067-135">**Indirect reseller**:</span></span> 

    -   <span data-ttu-id="9a067-136">Kan relaties hebben met bestaande klanten</span><span class="sxs-lookup"><span data-stu-id="9a067-136">Can have a relationships with existing customers</span></span>

    -   <span data-ttu-id="9a067-137">Kan geen nieuwe relaties aanvragen of nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="9a067-137">Cannot request new relationships or add new customers</span></span>

    ### <a name="in-partner-center"></a><span data-ttu-id="9a067-138">In Partner Center</span><span class="sxs-lookup"><span data-stu-id="9a067-138">In Partner Center</span></span>

    <span data-ttu-id="9a067-139">**Partners voor directe factuur:**</span><span class="sxs-lookup"><span data-stu-id="9a067-139">**Direct bill partners**:</span></span>

    -   <span data-ttu-id="9a067-140">Kan nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="9a067-140">Can add new customers</span></span>

    -   <span data-ttu-id="9a067-141">Kan relaties met nieuwe klanten aanvragen</span><span class="sxs-lookup"><span data-stu-id="9a067-141">Can request relationships with new customers</span></span>

    <span data-ttu-id="9a067-142">**Indirecte providers:**</span><span class="sxs-lookup"><span data-stu-id="9a067-142">**Indirect providers**:</span></span>

    -   <span data-ttu-id="9a067-143">Kan nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="9a067-143">Can add new customers</span></span>

    -   <span data-ttu-id="9a067-144">Kan relaties met nieuwe klanten aanvragen</span><span class="sxs-lookup"><span data-stu-id="9a067-144">Can request relationships with new customers</span></span>

    -   <span data-ttu-id="9a067-145">Kan relaties hebben met indirecte resellers</span><span class="sxs-lookup"><span data-stu-id="9a067-145">Can have relationships with indirect resellers</span></span>

    <span data-ttu-id="9a067-146">**Indirecte resellers:**</span><span class="sxs-lookup"><span data-stu-id="9a067-146">**Indirect resellers**:</span></span>

    -   <span data-ttu-id="9a067-147">Kan geen nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="9a067-147">Can’t add new customers</span></span>

    -   <span data-ttu-id="9a067-148">Kan relaties met nieuwe klanten aanvragen</span><span class="sxs-lookup"><span data-stu-id="9a067-148">Can request relationships with new customers</span></span>


<span data-ttu-id="9a067-149">Volg de [instructies in Resellerrelatie verwijderen](remove-a-reseller-relationship-with-a-customer.md) voor de klant voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="9a067-149">Follow the [Remove Reseller Relationship](remove-a-reseller-relationship-with-a-customer.md) for the customer for details.</span></span> <span data-ttu-id="9a067-150">Er zijn echter enkele verschillen tussen de product- en sandbox-mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="9a067-150">However, there are some differences between the Product and Sandbox capabilities.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9a067-151">AANVRAAGSYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="9a067-151">REQUEST SYNTAX</span></span>

|<span data-ttu-id="9a067-152">**Methode**</span><span class="sxs-lookup"><span data-stu-id="9a067-152">**Method**</span></span>|<span data-ttu-id="9a067-153">**Verwijderen**</span><span class="sxs-lookup"><span data-stu-id="9a067-153">**Delete**</span></span>|
|-------------|------------|
|<span data-ttu-id="9a067-154">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="9a067-154">Delete</span></span>|<span data-ttu-id="9a067-155">{baseURL}/v1/Customers/{customer-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="9a067-155">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span> |

<span data-ttu-id="9a067-156">Aanvraag body None</span><span class="sxs-lookup"><span data-stu-id="9a067-156">Request body None</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9a067-157">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="9a067-157">Response success and error codes</span></span>

<span data-ttu-id="9a067-158">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="9a067-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9a067-159">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9a067-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9a067-160">Zie REST-foutcodes voor [Partner Center lijst.](./error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="9a067-160">For the full list, see [Partner Center REST error codes](./error-codes.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="9a067-161">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="9a067-161">Next steps</span></span>

- [<span data-ttu-id="9a067-162">Sandbox-abonnementen activeren voor Azure Marketplace producten</span><span class="sxs-lookup"><span data-stu-id="9a067-162">Activate Sandbox subscriptions for Azure Marketplace products</span></span>](activate-sandbox-subscription-azure-marketplace-products.md)

- [<span data-ttu-id="9a067-163">Een bestelling van sandbox annuleren</span><span class="sxs-lookup"><span data-stu-id="9a067-163">Cancel an order from Sandbox</span></span>](cancel-an-order-from-the-integration-sandbox.md)

- [<span data-ttu-id="9a067-164">Testen en fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="9a067-164">Test and debug</span></span>](test-and-debug.md)