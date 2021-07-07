---
title: Sandbox-mogelijkheden voor reseller-relatie
description: Partner-sandbox biedt de mogelijkheid om relaties tussen de partner en de klant te ondersteunen
ms.date: 05/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: aa6c4fb9ef71bacfad7e0f1510fec15f6af60a05
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547390"
---
# <a name="sandbox-capabilities-for-reseller-relationship"></a><span data-ttu-id="74af2-103">Sandbox-mogelijkheden voor reseller-relatie</span><span class="sxs-lookup"><span data-stu-id="74af2-103">Sandbox capabilities for Reseller relationship</span></span>

<span data-ttu-id="74af2-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="74af2-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="74af2-105">In dit artikel wordt uitgelegd wat er wordt ondersteund in de Sandbox voor resellerrelaties tussen de partner en de klant.</span><span class="sxs-lookup"><span data-stu-id="74af2-105">This article explains what is supported in the Sandbox for reseller relationships between the partner and the customer.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="74af2-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="74af2-106">Prerequisites</span></span>

- <span data-ttu-id="74af2-107">Partner Center accountreferenties.</span><span class="sxs-lookup"><span data-stu-id="74af2-107">Partner Center account credentials.</span></span> <span data-ttu-id="74af2-108">Het sandboxscenario ondersteunt verificatie met zowel de zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="74af2-108">The sandbox scenario supports authentication with both the standalone App and App+User credentials.</span></span>
- <span data-ttu-id="74af2-109">Een klant-id (klant-tenant-id).</span><span class="sxs-lookup"><span data-stu-id="74af2-109">A customer ID (customer-tenant-id).</span></span> <span data-ttu-id="74af2-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard/home).</span><span class="sxs-lookup"><span data-stu-id="74af2-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard/home).</span></span> <span data-ttu-id="74af2-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="74af2-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="74af2-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="74af2-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="74af2-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="74af2-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="74af2-114">De Microsoft-id is hetzelfde als de klant-id (klant-tenant-id).</span><span class="sxs-lookup"><span data-stu-id="74af2-114">The Microsoft ID is the same as the customer ID (customer-tenant-id).</span></span>
- <span data-ttu-id="74af2-115">Alle Azure Reserved Virtual Machine Instances en software-aankooporders moeten worden geannuleerd voordat u een klant uit de Sandbox voor tipintegratie kunt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="74af2-115">All Azure Reserved Virtual Machine Instances and software purchase orders must be canceled before deleting a customer from the Tip integration sandbox.</span></span>

## <a name="scenarios-supporting-reseller-relationship"></a><span data-ttu-id="74af2-116">Scenario's die een resellerrelatie ondersteunen</span><span class="sxs-lookup"><span data-stu-id="74af2-116">Scenarios Supporting Reseller Relationship</span></span>

1.  <span data-ttu-id="74af2-117">Sandbox-partners voor directe factuur en indirecte providers kunnen relaties met de Sandbox-klant maken.</span><span class="sxs-lookup"><span data-stu-id="74af2-117">Sandbox Direct Bill Partners and Indirect Providers can create relationships with the Sandbox customer.</span></span> 
2.  <span data-ttu-id="74af2-118">Sandbox Directe factuurpartners en indirecte providers kunnen sandbox-klanten niet uitnodigen.</span><span class="sxs-lookup"><span data-stu-id="74af2-118">Sandbox Direct Bill Partners and Indirect Providers cannot invite Sandbox customers.</span></span>

3. <span data-ttu-id="74af2-119">Sandbox Direct Bill Partner en indirecte providers kunnen de resellerrelatie verwijderen uit Partner Center gebruikersinterface en API.</span><span class="sxs-lookup"><span data-stu-id="74af2-119">Sandbox Direct Bill Partner and Indirect Providers are able to remove reseller relationship from Partner Center UI and API.</span></span>

4. <span data-ttu-id="74af2-120">Met de Sandbox Remove Reseller-relatie wordt klant-AP verwijderen aanroepen.</span><span class="sxs-lookup"><span data-stu-id="74af2-120">Sandbox Remove Reseller Relationship will call Delete customer AP.</span></span> <span data-ttu-id="74af2-121">Hiermee verwijdert u de relatie en verwijdert u de tenant van de klant.</span><span class="sxs-lookup"><span data-stu-id="74af2-121">This will remove the relationship and delete the customer tenant.</span></span> <span data-ttu-id="74af2-122">{baseURL}/v1/Customers/{customer-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="74af2-122">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span>


    ### <a name="in-the-sandbox"></a><span data-ttu-id="74af2-123">In de sandbox</span><span class="sxs-lookup"><span data-stu-id="74af2-123">In the Sandbox</span></span>

    <span data-ttu-id="74af2-124">**Partners voor directe factuur:**</span><span class="sxs-lookup"><span data-stu-id="74af2-124">**Direct bill partners**:</span></span>

    - <span data-ttu-id="74af2-125">Kan bestaande klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="74af2-125">Can add existing customers</span></span>

    - <span data-ttu-id="74af2-126">Kan geen relaties met nieuwe klanten aanvragen</span><span class="sxs-lookup"><span data-stu-id="74af2-126">Cannot request relationships with new customers</span></span>

    <span data-ttu-id="74af2-127">**Indirecte providers:**</span><span class="sxs-lookup"><span data-stu-id="74af2-127">**Indirect providers**:</span></span>

    - <span data-ttu-id="74af2-128">Kan bestaande klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="74af2-128">Can add existing customers</span></span>

    - <span data-ttu-id="74af2-129">Kan geen relaties met nieuwe klanten aanvragen</span><span class="sxs-lookup"><span data-stu-id="74af2-129">Cannot request relationships with new customers</span></span>

    - <span data-ttu-id="74af2-130">Kan geen relatie hebben met een indirecte reseller</span><span class="sxs-lookup"><span data-stu-id="74af2-130">Cannot have a relationship with an Indirect reseller</span></span>

    <span data-ttu-id="74af2-131">**Indirecte reseller:**</span><span class="sxs-lookup"><span data-stu-id="74af2-131">**Indirect reseller**:</span></span> 

    -   <span data-ttu-id="74af2-132">Kan relaties hebben met bestaande klanten</span><span class="sxs-lookup"><span data-stu-id="74af2-132">Can have relationships with existing customers</span></span>

    -   <span data-ttu-id="74af2-133">Kan geen nieuwe relaties aanvragen of nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="74af2-133">Cannot request new relationships or add new customers</span></span>

    ### <a name="in-partner-center"></a><span data-ttu-id="74af2-134">In Partner Center</span><span class="sxs-lookup"><span data-stu-id="74af2-134">In Partner Center</span></span>

    <span data-ttu-id="74af2-135">**Partners voor directe factuur:**</span><span class="sxs-lookup"><span data-stu-id="74af2-135">**Direct bill partners**:</span></span>

    -   <span data-ttu-id="74af2-136">Kan nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="74af2-136">Can add new customers</span></span>

    -   <span data-ttu-id="74af2-137">Kan relaties met nieuwe klanten aanvragen</span><span class="sxs-lookup"><span data-stu-id="74af2-137">Can request relationships with new customers</span></span>

    <span data-ttu-id="74af2-138">**Indirecte providers:**</span><span class="sxs-lookup"><span data-stu-id="74af2-138">**Indirect providers**:</span></span>

    -   <span data-ttu-id="74af2-139">Kan nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="74af2-139">Can add new customers</span></span>

    -   <span data-ttu-id="74af2-140">Kan relaties met nieuwe klanten aanvragen</span><span class="sxs-lookup"><span data-stu-id="74af2-140">Can request relationships with new customers</span></span>

    -   <span data-ttu-id="74af2-141">Kan relaties hebben met indirecte resellers</span><span class="sxs-lookup"><span data-stu-id="74af2-141">Can have relationships with indirect resellers</span></span>

    <span data-ttu-id="74af2-142">**Indirecte resellers:**</span><span class="sxs-lookup"><span data-stu-id="74af2-142">**Indirect resellers**:</span></span>

    -   <span data-ttu-id="74af2-143">Kan geen nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="74af2-143">Can’t add new customers</span></span>

    -   <span data-ttu-id="74af2-144">Kan relaties met nieuwe klanten aanvragen</span><span class="sxs-lookup"><span data-stu-id="74af2-144">Can request relationships with new customers</span></span>


<span data-ttu-id="74af2-145">Volg de [instructies in Resellerrelatie](remove-a-reseller-relationship-with-a-customer.md) verwijderen voor de klant voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="74af2-145">Follow the [Remove Reseller Relationship](remove-a-reseller-relationship-with-a-customer.md) for the customer for details.</span></span> <span data-ttu-id="74af2-146">Er zijn echter enkele verschillen tussen de product- en sandbox-mogelijkheden.</span><span class="sxs-lookup"><span data-stu-id="74af2-146">However, there are some differences between the Product and Sandbox capabilities.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="74af2-147">AANVRAAGSYNTAXIS</span><span class="sxs-lookup"><span data-stu-id="74af2-147">REQUEST SYNTAX</span></span>

|<span data-ttu-id="74af2-148">**Methode**</span><span class="sxs-lookup"><span data-stu-id="74af2-148">**Method**</span></span>|<span data-ttu-id="74af2-149">**Verwijderen**</span><span class="sxs-lookup"><span data-stu-id="74af2-149">**Delete**</span></span>|
|-------------|------------|
|<span data-ttu-id="74af2-150">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="74af2-150">Delete</span></span>|<span data-ttu-id="74af2-151">{baseURL}/v1/Customers/{customer-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="74af2-151">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span> |

<span data-ttu-id="74af2-152">Aanvraag body None</span><span class="sxs-lookup"><span data-stu-id="74af2-152">Request body None</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="74af2-153">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="74af2-153">Response success and error codes</span></span>

<span data-ttu-id="74af2-154">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="74af2-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="74af2-155">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="74af2-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="74af2-156">Zie REST-foutcodes voor [Partner Center lijst.](./error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="74af2-156">For the full list, see [Partner Center REST error codes](./error-codes.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="74af2-157">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="74af2-157">Next steps</span></span>

- [<span data-ttu-id="74af2-158">Sandbox-abonnementen activeren voor Azure Marketplace producten</span><span class="sxs-lookup"><span data-stu-id="74af2-158">Activate Sandbox subscriptions for Azure Marketplace products</span></span>](activate-sandbox-subscription-azure-marketplace-products.md)

- [<span data-ttu-id="74af2-159">Een bestelling van sandbox annuleren</span><span class="sxs-lookup"><span data-stu-id="74af2-159">Cancel an order from Sandbox</span></span>](cancel-an-order-from-the-integration-sandbox.md)

- [<span data-ttu-id="74af2-160">Testen en fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="74af2-160">Test and debug</span></span>](test-and-debug.md)