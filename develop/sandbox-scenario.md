---
title: Sandbox-mogelijkheden voor partners die reseller-relatie ondersteunen
description: Partner sandbox biedt de mogelijkheid om relaties tussen de partner en de klant te ondersteunen
ms.date: 11/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e01dd1a83ca459cbdf12b8e564b43a2d18f5595b
ms.sourcegitcommit: f69ceae441bbb2ddba96e878a1ec8c1a499a4879
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 01/13/2021
ms.locfileid: "98180728"
---
# <a name="partner-sandbox-capabilities-that-support-reseller-relationship"></a><span data-ttu-id="1b18c-103">Sandbox-mogelijkheden voor partners die reseller-relatie ondersteunen</span><span class="sxs-lookup"><span data-stu-id="1b18c-103">Partner sandbox capabilities that support reseller relationship</span></span>

<span data-ttu-id="1b18c-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="1b18c-104">**Applies to:**</span></span>

- <span data-ttu-id="1b18c-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="1b18c-105">Partner Center</span></span>
- <span data-ttu-id="1b18c-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="1b18c-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="1b18c-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="1b18c-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="1b18c-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1b18c-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1b18c-109">In dit artikel wordt uitgelegd wat wordt ondersteund in de sandbox voor wederverkoper relaties tussen de partner en de klant.</span><span class="sxs-lookup"><span data-stu-id="1b18c-109">This article explains what is supported in the Sandbox for reseller relationships between the partner and the customer.</span></span> 

## <a name="prerequisites"></a><span data-ttu-id="1b18c-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1b18c-110">Prerequisites</span></span>

- <span data-ttu-id="1b18c-111">Referenties van het partner centrum-account.</span><span class="sxs-lookup"><span data-stu-id="1b18c-111">Partner Center account credentials.</span></span> <span data-ttu-id="1b18c-112">Het sandbox-scenario ondersteunt verificatie met zowel de zelfstandige app als de app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="1b18c-112">The sandbox scenario supports authentication with both the standalone App and App+User credentials.</span></span>
- <span data-ttu-id="1b18c-113">Een klant-ID (klant-Tenant-id).</span><span class="sxs-lookup"><span data-stu-id="1b18c-113">A customer ID (customer-tenant-id).</span></span> <span data-ttu-id="1b18c-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard/home)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="1b18c-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard/home).</span></span> <span data-ttu-id="1b18c-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="1b18c-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="1b18c-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="1b18c-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="1b18c-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="1b18c-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="1b18c-118">De micro soft-ID is gelijk aan de klant-ID (klant-Tenant-id).</span><span class="sxs-lookup"><span data-stu-id="1b18c-118">The Microsoft ID is the same as the customer ID (customer-tenant-id).</span></span>
- <span data-ttu-id="1b18c-119">Alle Azure Reserved Virtual Machine Instances-en software-aankoop orders moeten worden geannuleerd voordat een klant uit de tip Integration sandbox kan worden verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1b18c-119">All Azure Reserved Virtual Machine Instances and software purchase orders must be canceled before deleting a customer from the Tip integration sandbox.</span></span>

## <a name="scenarios-supporting-reseller-relationship"></a><span data-ttu-id="1b18c-120">Scenario's die reseller Relationship ondersteunen</span><span class="sxs-lookup"><span data-stu-id="1b18c-120">Scenarios Supporting Reseller Relationship</span></span>

1.  <span data-ttu-id="1b18c-121">Sandbox direct-factuur partners en indirecte providers kunnen relatie maken met de klant in de sandbox.</span><span class="sxs-lookup"><span data-stu-id="1b18c-121">Sandbox Direct Bill Partners and Indirect Providers can create relationships with the Sandbox customer.</span></span> 
2.  <span data-ttu-id="1b18c-122">Sandbox direct-factuur partners en indirecte providers kunnen sandbox-klanten niet uitnodigen.</span><span class="sxs-lookup"><span data-stu-id="1b18c-122">Sandbox Direct Bill Partners and Indirect Providers cannot invite Sandbox customers.</span></span>



### <a name="in-the-sandbox"></a><span data-ttu-id="1b18c-123">In de sandbox</span><span class="sxs-lookup"><span data-stu-id="1b18c-123">In the Sandbox</span></span>

<span data-ttu-id="1b18c-124">**Directe factuur partners**:</span><span class="sxs-lookup"><span data-stu-id="1b18c-124">**Direct bill partners**:</span></span>

<span data-ttu-id="1b18c-125">• Kan bestaande klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="1b18c-125">•   Can add existing customers</span></span>

<span data-ttu-id="1b18c-126">• Kan geen relaties aanvragen met nieuwe klanten</span><span class="sxs-lookup"><span data-stu-id="1b18c-126">•   Cannot request relationships with new customers</span></span>

<span data-ttu-id="1b18c-127">**Indirecte providers**:</span><span class="sxs-lookup"><span data-stu-id="1b18c-127">**Indirect providers**:</span></span>

<span data-ttu-id="1b18c-128">• Kan bestaande klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="1b18c-128">•   Can add existing customers</span></span>

<span data-ttu-id="1b18c-129">• Kan geen relaties aanvragen met nieuwe klanten</span><span class="sxs-lookup"><span data-stu-id="1b18c-129">•   Cannot request relationships with new customers</span></span>

<span data-ttu-id="1b18c-130">• Kan geen relatie hebben met een indirecte wederverkoper</span><span class="sxs-lookup"><span data-stu-id="1b18c-130">•   Cannot have a relationship with an Indirect reseller</span></span>

<span data-ttu-id="1b18c-131">**Indirecte wederverkoper**: (binnenkort beschikbaar)</span><span class="sxs-lookup"><span data-stu-id="1b18c-131">**Indirect reseller**: (coming soon)</span></span>

<span data-ttu-id="1b18c-132">• Kan een relatie met bestaande klanten hebben</span><span class="sxs-lookup"><span data-stu-id="1b18c-132">•   Can have a relationships with existing customers</span></span>

<span data-ttu-id="1b18c-133">• Kan geen nieuwe relaties aanvragen of nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="1b18c-133">•   Cannot request new relationships or add new customers</span></span>

### <a name="in-partner-center"></a><span data-ttu-id="1b18c-134">In partner centrum</span><span class="sxs-lookup"><span data-stu-id="1b18c-134">In Partner Center</span></span>

<span data-ttu-id="1b18c-135">**Directe factuur partners**:</span><span class="sxs-lookup"><span data-stu-id="1b18c-135">**Direct bill partners**:</span></span>

<span data-ttu-id="1b18c-136">• Kan nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="1b18c-136">•   Can add new customers</span></span>

<span data-ttu-id="1b18c-137">• Kan relaties aanvragen met nieuwe klanten</span><span class="sxs-lookup"><span data-stu-id="1b18c-137">•   Can request relationships with new customers</span></span>

<span data-ttu-id="1b18c-138">**Indirecte providers**:</span><span class="sxs-lookup"><span data-stu-id="1b18c-138">**Indirect providers**:</span></span>

<span data-ttu-id="1b18c-139">• Kan nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="1b18c-139">•   Can add new customers</span></span>

<span data-ttu-id="1b18c-140">• Kan relaties aanvragen met nieuwe klanten</span><span class="sxs-lookup"><span data-stu-id="1b18c-140">•   Can request relationships with new customers</span></span>

<span data-ttu-id="1b18c-141">• Kan relaties hebben met indirecte wederverkopers</span><span class="sxs-lookup"><span data-stu-id="1b18c-141">•   Can have relationships with indirect resellers</span></span>

<span data-ttu-id="1b18c-142">**Indirecte wederverkopers**:</span><span class="sxs-lookup"><span data-stu-id="1b18c-142">**Indirect resellers**:</span></span>

<span data-ttu-id="1b18c-143">• Kan geen nieuwe klanten toevoegen</span><span class="sxs-lookup"><span data-stu-id="1b18c-143">•   Can’t add new customers</span></span>

<span data-ttu-id="1b18c-144">• Kan relaties aanvragen met nieuwe klanten</span><span class="sxs-lookup"><span data-stu-id="1b18c-144">•   Can request relationships with new customers</span></span>

3. <span data-ttu-id="1b18c-145">Sandbox direct Bill-partner en indirecte providers kunnen wederverkoper-relaties verwijderen uit de gebruikers interface en API van partner Center.</span><span class="sxs-lookup"><span data-stu-id="1b18c-145">Sandbox Direct Bill Partner and Indirect Providers are able to remove reseller relationship from Partner Center UI and API.</span></span>

4. <span data-ttu-id="1b18c-146">Met de sandbox-relatie verwijderen wordt het verwijderen van de klant-AP aangeroepen.</span><span class="sxs-lookup"><span data-stu-id="1b18c-146">Sandbox Remove Reseller Relationship will call Delete customer AP.</span></span> <span data-ttu-id="1b18c-147">Hiermee wordt de relatie verwijderd en wordt de Tenant van de klant verwijderd.</span><span class="sxs-lookup"><span data-stu-id="1b18c-147">This will remove the relationship as well as delete the customer tenant.</span></span> <span data-ttu-id="1b18c-148">{baseURL}/v1/Customers/{customer-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="1b18c-148">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span>

<span data-ttu-id="1b18c-149">Volg de [wederverkoper-relatie verwijderen](remove-a-reseller-relationship-with-a-customer.md) voor de klant voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="1b18c-149">Follow the [Remove Reseller Relationship](remove-a-reseller-relationship-with-a-customer.md) for the customer for details.</span></span> <span data-ttu-id="1b18c-150">Er zijn echter enkele verschillen tussen de mogelijkheden van het product en de sandbox.</span><span class="sxs-lookup"><span data-stu-id="1b18c-150">However, there are some differences between the Product and Sandbox capabilities.</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1b18c-151">SYNTAXIS VAN AANVRAAG</span><span class="sxs-lookup"><span data-stu-id="1b18c-151">REQUEST SYNTAX</span></span>

|<span data-ttu-id="1b18c-152">**Methode**</span><span class="sxs-lookup"><span data-stu-id="1b18c-152">**Method**</span></span>|<span data-ttu-id="1b18c-153">**Verwijderen**</span><span class="sxs-lookup"><span data-stu-id="1b18c-153">**Delete**</span></span>|
|-------------|------------|
|<span data-ttu-id="1b18c-154">Verwijderen</span><span class="sxs-lookup"><span data-stu-id="1b18c-154">Delete</span></span>|<span data-ttu-id="1b18c-155">{baseURL}/v1/Customers/{customer-Tenant-id}</span><span class="sxs-lookup"><span data-stu-id="1b18c-155">{baseURL}/v1/Customers/{customer-Tenant-id}</span></span> |

<span data-ttu-id="1b18c-156">Hoofd tekst van aanvraag geen</span><span class="sxs-lookup"><span data-stu-id="1b18c-156">Request body None</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1b18c-157">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="1b18c-157">Response success and error codes</span></span>

<span data-ttu-id="1b18c-158">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="1b18c-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1b18c-159">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1b18c-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1b18c-160">Zie [rest-fout codes van het partner centrum](https://docs.microsoft.com/partner-center/develop/error-codes)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="1b18c-160">For the full list, see [Partner Center REST error codes](https://docs.microsoft.com/partner-center/develop/error-codes).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1b18c-161">Volgende stappen</span><span class="sxs-lookup"><span data-stu-id="1b18c-161">Next steps</span></span>

- [<span data-ttu-id="1b18c-162">Sandbox-abonnementen voor Azure Marketplace-producten activeren</span><span class="sxs-lookup"><span data-stu-id="1b18c-162">Activate Sandbox subscriptions for Azure Marketplace products</span></span>](activate-sandbox-subscription-azure-marketplace-products.md)

- [<span data-ttu-id="1b18c-163">Een order annuleren vanuit sandbox</span><span class="sxs-lookup"><span data-stu-id="1b18c-163">Cancel an order from Sandbox</span></span>](cancel-an-order-from-the-integration-sandbox.md)

- [<span data-ttu-id="1b18c-164">Testen en fouten opsporen</span><span class="sxs-lookup"><span data-stu-id="1b18c-164">Test and debug</span></span>](test-and-debug.md) 
