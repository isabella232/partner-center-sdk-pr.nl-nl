---
title: Sandbox-mogelijkheden voor partners die reseller-relatie ondersteunen
description: Partner sandbox biedt de mogelijkheid om relaties tussen de partner en de klant te ondersteunen
ms.date: 11/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: af46811b3615e1f904a9619de85b0aca7622490b
ms.sourcegitcommit: 717e483a6eec23607b4e31ddfaa3e2691f3043e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104711862"
---
# <a name="partner-sandbox-capabilities-that-support-reseller-relationship"></a><span data-ttu-id="abf8d-103">Sandbox-mogelijkheden voor partners die reseller-relatie ondersteunen</span><span class="sxs-lookup"><span data-stu-id="abf8d-103">Partner sandbox capabilities that support reseller relationship</span></span>

<span data-ttu-id="abf8d-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="abf8d-104">**Applies to:**</span></span>

- <span data-ttu-id="abf8d-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="abf8d-105">Partner Center</span></span>
- <span data-ttu-id="abf8d-106">Partnercentrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="abf8d-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="abf8d-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="abf8d-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="abf8d-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="abf8d-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="abf8d-109">In dit artikel wordt uitgelegd wat wordt ondersteund in de sandbox voor wederverkoper relaties tussen de partner en de klant.</span><span class="sxs-lookup"><span data-stu-id="abf8d-109">This article explains what is supported in the Sandbox for reseller relationships between the partner and the customer.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="abf8d-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="abf8d-110">Prerequisites</span></span>

- <span data-ttu-id="abf8d-111">Referenties van het partner centrum-account.</span><span class="sxs-lookup"><span data-stu-id="abf8d-111">Partner Center account credentials.</span></span> <span data-ttu-id="abf8d-112">Het sandbox-scenario ondersteunt verificatie met zowel de zelfstandige app als de app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="abf8d-112">The sandbox scenario supports authentication with both the standalone App and App+User credentials.</span></span>
- <span data-ttu-id="abf8d-113">Een klant-ID (klant-Tenant-id).</span><span class="sxs-lookup"><span data-stu-id="abf8d-113">A customer ID (customer-tenant-id).</span></span> <span data-ttu-id="abf8d-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard/home)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="abf8d-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard/home).</span></span> <span data-ttu-id="abf8d-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="abf8d-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="abf8d-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="abf8d-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="abf8d-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="abf8d-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="abf8d-118">De micro soft-ID is gelijk aan de klant-ID (klant-Tenant-id).</span><span class="sxs-lookup"><span data-stu-id="abf8d-118">The Microsoft ID is the same as the customer ID (customer-tenant-id).</span></span>
- <span data-ttu-id="abf8d-119">Alle Azure Reserved Virtual Machine Instances-en software-aankoop orders moeten worden geannuleerd voordat een klant uit de tip Integration sandbox kan worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="abf8d-119">All Azure Reserved Virtual Machine Instances and software purchase orders must be canceled before deleting a customer from the Tip integration sandbox.</span></span>

## <a name="scenarios-supporting-reseller-relationship"></a><span data-ttu-id="abf8d-120">Scenario's die reseller Relationship ondersteunen</span><span class="sxs-lookup"><span data-stu-id="abf8d-120">Scenarios Supporting Reseller Relationship</span></span>

1.  <span data-ttu-id="abf8d-121">Sandbox direct-factuur partners en indirecte providers kunnen relatie maken met de klant in de sandbox.</span><span class="sxs-lookup"><span data-stu-id="abf8d-121">Sandbox Direct Bill Partners and Indirect Providers can create relationships with the Sandbox customer.</span></span> 
2.  <span data-ttu-id="abf8d-122">Sandbox direct-factuur partners en indirecte providers kunnen sandbox-klanten niet uitnodigen.</span><span class="sxs-lookup"><span data-stu-id="abf8d-122">Sandbox Direct Bill Partners and Indirect Providers cannot invite Sandbox customers.</span></span>



### <a name="in-the-sandbox"></a><span data-ttu-id="abf8d-123">In de sandbox</span><span class="sxs-lookup"><span data-stu-id="abf8d-123">In the Sandbox</span></span>

<span data-ttu-id="abf8d-124">**Directe factuur partners**:</span><span class="sxs-lookup"><span data-stu-id="abf8d-124">**Direct bill partners**:</span></span>

<span data-ttu-id="abf8d-125">• Kan bestaande klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="abf8d-125">•   Can add existing customers</span></span>

<span data-ttu-id="abf8d-126">• Kan geen relaties aanvragen met nieuwe klanten</span><span class="sxs-lookup"><span data-stu-id="abf8d-126">•   Cannot request relationships with new customers</span></span>

<span data-ttu-id="abf8d-127">**Indirecte providers**:</span><span class="sxs-lookup"><span data-stu-id="abf8d-127">**Indirect providers**:</span></span>

<span data-ttu-id="abf8d-128">• Kan bestaande klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="abf8d-128">•   Can add existing customers</span></span>

<span data-ttu-id="abf8d-129">• Kan geen relaties aanvragen met nieuwe klanten</span><span class="sxs-lookup"><span data-stu-id="abf8d-129">•   Cannot request relationships with new customers</span></span>

<span data-ttu-id="abf8d-130">• Kan geen relatie hebben met een indirecte wederverkoper</span><span class="sxs-lookup"><span data-stu-id="abf8d-130">•   Cannot have a relationship with an Indirect reseller</span></span>

<span data-ttu-id="abf8d-131">**Indirecte wederverkoper**: (binnenkort beschikbaar)</span><span class="sxs-lookup"><span data-stu-id="abf8d-131">**Indirect reseller**: (coming soon)</span></span>

<span data-ttu-id="abf8d-132">• Kan een relatie met bestaande klanten hebben</span><span class="sxs-lookup"><span data-stu-id="abf8d-132">•   Can have a relationships with existing customers</span></span>

<span data-ttu-id="abf8d-133">• Kan geen nieuwe relaties aanvragen of nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="abf8d-133">•   Cannot request new relationships or add new customers</span></span>

### <a name="in-partner-center"></a><span data-ttu-id="abf8d-134">In partner centrum</span><span class="sxs-lookup"><span data-stu-id="abf8d-134">In Partner Center</span></span>

<span data-ttu-id="abf8d-135">**Directe factuur partners**:</span><span class="sxs-lookup"><span data-stu-id="abf8d-135">**Direct bill partners**:</span></span>

<span data-ttu-id="abf8d-136">• Kan nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="abf8d-136">•   Can add new customers</span></span>

<span data-ttu-id="abf8d-137">• Kan relaties aanvragen met nieuwe klanten</span><span class="sxs-lookup"><span data-stu-id="abf8d-137">•   Can request relationships with new customers</span></span>

<span data-ttu-id="abf8d-138">**Indirecte providers**:</span><span class="sxs-lookup"><span data-stu-id="abf8d-138">**Indirect providers**:</span></span>

<span data-ttu-id="abf8d-139">• Kan nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="abf8d-139">•   Can add new customers</span></span>

<span data-ttu-id="abf8d-140">• Kan relaties aanvragen met nieuwe klanten</span><span class="sxs-lookup"><span data-stu-id="abf8d-140">•   Can request relationships with new customers</span></span>

<span data-ttu-id="abf8d-141">• Kan relaties hebben met indirecte wederverkopers</span><span class="sxs-lookup"><span data-stu-id="abf8d-141">•   Can have relationships with indirect resellers</span></span>

<span data-ttu-id="abf8d-142">**Indirecte wederverkopers**:</span><span class="sxs-lookup"><span data-stu-id="abf8d-142">**Indirect resellers**:</span></span>

<span data-ttu-id="abf8d-143">• Kan geen nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="abf8d-143">•   Can’t add new customers</span></span>

<span data-ttu-id="abf8d-144">• Kan relaties aanvragen met nieuwe klanten</span><span class="sxs-lookup"><span data-stu-id="abf8d-144">•   Can request relationships with new customers</span></span>

3. <span data-ttu-id="abf8d-145">Sandbox direct Bill-partner en indirecte providers kunnen wederverkoper-relaties verwijderen uit de gebruikers interface en API van partner Center.</span><span class="sxs-lookup"><span data-stu-id="abf8d-145">Sandbox Direct Bill Partner and Indirect Providers are able to remove reseller relationship from Partner Center UI and API.</span></span>

4. <span data-ttu-id="abf8d-146">Met de sandbox-relatie verwijderen wordt het verwijderen van de klant-AP aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="abf8d-146">Sandbox Remove Reseller Relationship will call Delete customer AP.</span></span> <span data-ttu-id="abf8d-147">Hiermee wordt de relatie verwijderd en wordt de Tenant van de klant verwijderd.</span><span class="sxs-lookup"><span data-stu-id="abf8d-147">This will remove the relationship as well as delete the customer tenant.</span></span> <span data-ttu-id="abf8d-148">{baseURL}/v1/Customers/{customer-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="abf8d-148">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span>

<span data-ttu-id="abf8d-149">Volg de [wederverkoper-relatie verwijderen](remove-a-reseller-relationship-with-a-customer.md) voor de klant voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="abf8d-149">Follow the [Remove Reseller Relationship](remove-a-reseller-relationship-with-a-customer.md) for the customer for details.</span></span> <span data-ttu-id="abf8d-150">Er zijn echter enkele verschillen tussen de mogelijkheden van het product en de sandbox.</span><span class="sxs-lookup"><span data-stu-id="abf8d-150">However, there are some differences between the Product and Sandbox capabilities.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="abf8d-151">SYNTAXIS VAN AANVRAAG</span><span class="sxs-lookup"><span data-stu-id="abf8d-151">REQUEST SYNTAX</span></span>

|<span data-ttu-id="abf8d-152">**Methode**</span><span class="sxs-lookup"><span data-stu-id="abf8d-152">**Method**</span></span>|<span data-ttu-id="abf8d-153">**Verwijderen**</span><span class="sxs-lookup"><span data-stu-id="abf8d-153">**Delete**</span></span>|
|-------------|------------|
|<span data-ttu-id="abf8d-154">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="abf8d-154">Delete</span></span>|<span data-ttu-id="abf8d-155">{baseURL}/v1/Customers/{customer-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="abf8d-155">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span> |

<span data-ttu-id="abf8d-156">Hoofd tekst van aanvraag geen</span><span class="sxs-lookup"><span data-stu-id="abf8d-156">Request body None</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="abf8d-157">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="abf8d-157">Response success and error codes</span></span>

<span data-ttu-id="abf8d-158">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="abf8d-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="abf8d-159">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="abf8d-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="abf8d-160">Zie [rest-fout codes van het partner centrum](./error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="abf8d-160">For the full list, see [Partner Center REST error codes](./error-codes.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="abf8d-161">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="abf8d-161">Next steps</span></span>

- [<span data-ttu-id="abf8d-162">Sandbox-abonnementen voor Azure Marketplace-producten activeren</span><span class="sxs-lookup"><span data-stu-id="abf8d-162">Activate Sandbox subscriptions for Azure Marketplace products</span></span>](activate-sandbox-subscription-azure-marketplace-products.md)

- [<span data-ttu-id="abf8d-163">Een order annuleren vanuit sandbox</span><span class="sxs-lookup"><span data-stu-id="abf8d-163">Cancel an order from Sandbox</span></span>](cancel-an-order-from-the-integration-sandbox.md)

- [<span data-ttu-id="abf8d-164">Testen en fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="abf8d-164">Test and debug</span></span>](test-and-debug.md)