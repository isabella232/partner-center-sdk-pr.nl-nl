---
title: Een abonnement voor commerciële Marketplace-producten maken
description: Ontwikkel aars kunnen een abonnement voor commerciële Marketplace-producten maken en beheren met behulp van partner Center-Api's.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: df2a3707e00ba36a11c404b102304c08d105244e
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767198"
---
# <a name="create-a-subscription-for-commercial-marketplace-products"></a><span data-ttu-id="b17ed-103">Een abonnement voor commerciële Marketplace-producten maken</span><span class="sxs-lookup"><span data-stu-id="b17ed-103">Create a subscription for commercial marketplace products</span></span>

<span data-ttu-id="b17ed-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="b17ed-104">**Applies to:**</span></span>

* <span data-ttu-id="b17ed-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="b17ed-105">Partner Center</span></span>

<span data-ttu-id="b17ed-106">U kunt een abonnement voor commerciële Marketplace-producten maken met behulp van partner Center-Api's.</span><span class="sxs-lookup"><span data-stu-id="b17ed-106">You can create a subscription for commercial marketplace products using Partner Center APIs.</span></span> <span data-ttu-id="b17ed-107">U moet [een lijst met aanbiedingen voor een markt verkrijgen](#get-a-list-of-offers-for-a-market), een bestelling voor een abonnement op commerciële Marketplace [maken en verzenden en](#create-and-submit-an-order) vervolgens [een activerings koppeling ophalen](#get-activation-link).</span><span class="sxs-lookup"><span data-stu-id="b17ed-107">You must [get a list of offers for a market](#get-a-list-of-offers-for-a-market), [create and submit an order](#create-and-submit-an-order) for a commercial marketplace subscription, then [retrieve an activation link](#get-activation-link).</span></span>

<span data-ttu-id="b17ed-108">U kunt ook [levenscyclus beheer uitvoeren](#lifecycle-management) en [facturen](#invoice-and-reconciliation) voor deze abonnementen beheren.</span><span class="sxs-lookup"><span data-stu-id="b17ed-108">You can also [perform lifecycle management](#lifecycle-management) and [manage invoices](#invoice-and-reconciliation) for these subscriptions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b17ed-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b17ed-109">Prerequisites</span></span>

* <span data-ttu-id="b17ed-110">Verificatie referenties voor het [partner centrum](partner-center-authentication.md) .</span><span class="sxs-lookup"><span data-stu-id="b17ed-110">[Partner Center authentication](partner-center-authentication.md) credentials.</span></span> <span data-ttu-id="b17ed-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="b17ed-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>
* <span data-ttu-id="b17ed-112">De klant-id.</span><span class="sxs-lookup"><span data-stu-id="b17ed-112">The customer identifier.</span></span> <span data-ttu-id="b17ed-113">Als u geen klant-id hebt, volgt u de stappen in [een lijst met klanten ophalen](get-a-list-of-customers.md).</span><span class="sxs-lookup"><span data-stu-id="b17ed-113">If you don't have a customer's identifier, follow the steps in [Get a list of customers](get-a-list-of-customers.md).</span></span> <span data-ttu-id="b17ed-114">U kunt zich ook aanmelden bij het partner centrum, de klant kiezen uit de lijst met klanten, **account** selecteren en vervolgens hun **micro soft-id** opslaan.</span><span class="sxs-lookup"><span data-stu-id="b17ed-114">Alternatively, sign in to Partner Center, choose the customer from the list of customers, select **Account**, then save their **Microsoft ID**.</span></span>

## <a name="get-a-list-of-offers-for-a-market"></a><span data-ttu-id="b17ed-115">Een lijst met aanbiedingen voor een markt ophalen</span><span class="sxs-lookup"><span data-stu-id="b17ed-115">Get a list of offers for a market</span></span>

<span data-ttu-id="b17ed-116">U kunt de beschik bare aanbiedingen voor een markt controleren met behulp van de volgende partner Center API-modellen:</span><span class="sxs-lookup"><span data-stu-id="b17ed-116">You can check the available offers for a market using the following Partner Center API models:</span></span>

* <span data-ttu-id="b17ed-117">**[Product](product-resources.md#product)**: een groeperings constructie voor tevens goederen of-services.</span><span class="sxs-lookup"><span data-stu-id="b17ed-117">**[Product](product-resources.md#product)**: A grouping construct for purchasable goods or services.</span></span> <span data-ttu-id="b17ed-118">Een product zelf is geen tevens-item.</span><span class="sxs-lookup"><span data-stu-id="b17ed-118">A product itself isn't a purchasable item.</span></span>
* <span data-ttu-id="b17ed-119">**[SKU](product-resources.md#sku)**: een SKU (Stock Keeping Unit) onder een product.</span><span class="sxs-lookup"><span data-stu-id="b17ed-119">**[SKU](product-resources.md#sku)**: A purchasable Stock Keeping Unit (SKU) under a product.</span></span> <span data-ttu-id="b17ed-120">Deze vertegenwoordigen de verschillende vormen van het product.</span><span class="sxs-lookup"><span data-stu-id="b17ed-120">These represent the different shapes of the product.</span></span>
* <span data-ttu-id="b17ed-121">**[Beschik baarheid](product-resources.md#availability)**: een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land-, valuta-of sector segment).</span><span class="sxs-lookup"><span data-stu-id="b17ed-121">**[Availability](product-resources.md#availability)**: A configuration in which a SKU is available for purchase (such as country, currency, or industry segment).</span></span>

<span data-ttu-id="b17ed-122">Voordat u een Azure-reserve ring aanschaft, voert u de volgende stappen uit:</span><span class="sxs-lookup"><span data-stu-id="b17ed-122">Before you purchase an Azure reservation, complete the following steps:</span></span>

1. <span data-ttu-id="b17ed-123">Identificeer en haal het product en de SKU op die u wilt kopen.</span><span class="sxs-lookup"><span data-stu-id="b17ed-123">Identify and retrieve the product and SKU that you want to purchase.</span></span> <span data-ttu-id="b17ed-124">Als u de product-ID en SKU-ID al kent, selecteert u deze.</span><span class="sxs-lookup"><span data-stu-id="b17ed-124">If you already know the Product ID and SKU ID, select them.</span></span>

    * [<span data-ttu-id="b17ed-125">Een lijst met producten ophalen</span><span class="sxs-lookup"><span data-stu-id="b17ed-125">Get a list of products</span></span>](get-a-list-of-products.md)
    * [<span data-ttu-id="b17ed-126">Een product ophalen met de product-ID</span><span class="sxs-lookup"><span data-stu-id="b17ed-126">Get a product using the product ID</span></span>](get-a-product-by-id.md)
    * [<span data-ttu-id="b17ed-127">Een lijst met Sku's voor een product ophalen</span><span class="sxs-lookup"><span data-stu-id="b17ed-127">Get a list of SKUs for a product</span></span>](get-a-list-of-skus-for-a-product.md)
    * [<span data-ttu-id="b17ed-128">Een SKU ophalen met behulp van de SKU-ID</span><span class="sxs-lookup"><span data-stu-id="b17ed-128">Get a SKU using the SKU ID</span></span>](get-a-sku-by-id.md)

    > [!NOTE]
    > <span data-ttu-id="b17ed-129">U kunt producten voor commerciële Marketplace identificeren met hun **product type** -eigenschap van **Azure** en hun **subtype** -eigenschap van **SaaS**.</span><span class="sxs-lookup"><span data-stu-id="b17ed-129">You can identify commercial marketplace products by their **ProductType** property of **"Azure"** and their **SubType** property of **"SaaS"**.</span></span>

2. <span data-ttu-id="b17ed-130">Als de Sku's zijn gelabeld met een **InventoryCheck** -vereiste, [controleert u de inventaris van een SKU](check-inventory.md).</span><span class="sxs-lookup"><span data-stu-id="b17ed-130">If the SKUs are tagged with an **InventoryCheck** prerequisite, [check the inventory for a SKU](check-inventory.md).</span></span>

    > [!NOTE]
    > <span data-ttu-id="b17ed-131">Op dit moment zijn er geen commerciële Marketplace-producten die inventaris controle ondersteunen of die zijn gelabeld met een **InventoryCheck** -vereiste.</span><span class="sxs-lookup"><span data-stu-id="b17ed-131">At this time, there are no commercial marketplace products that support inventory check or are tagged with an **InventoryCheck** prerequisite.</span></span>

3. <span data-ttu-id="b17ed-132">De beschik baarheid voor de SKU ophalen.</span><span class="sxs-lookup"><span data-stu-id="b17ed-132">Retrieve the availability for the SKU.</span></span> <span data-ttu-id="b17ed-133">U hebt de **CatalogItemId** van de beschik baarheid nodig bij het plaatsen van de order, die u via de volgende api's kunt ophalen:</span><span class="sxs-lookup"><span data-stu-id="b17ed-133">You will need the **CatalogItemId** of the availability when placing the order, which you can retrieve through the following APIs:</span></span>

    * [<span data-ttu-id="b17ed-134">Een lijst met Beschik baarheid voor een SKU ophalen</span><span class="sxs-lookup"><span data-stu-id="b17ed-134">Get a list of availabilities for a SKU</span></span>](get-a-list-of-availabilities-for-a-sku.md)
    * [<span data-ttu-id="b17ed-135">Krijg een Beschik baarheid met behulp van de beschikbaarheids-ID</span><span class="sxs-lookup"><span data-stu-id="b17ed-135">Get an availability using the availability ID</span></span>](get-an-availability-by-id.md)

## <a name="create-and-submit-an-order"></a><span data-ttu-id="b17ed-136">Een order maken en verzenden</span><span class="sxs-lookup"><span data-stu-id="b17ed-136">Create and submit an order</span></span>

<span data-ttu-id="b17ed-137">Voer de volgende stappen uit om uw Azure-reserverings order in te dienen:</span><span class="sxs-lookup"><span data-stu-id="b17ed-137">To submit your Azure reservation order, follow these steps:</span></span>

1. <span data-ttu-id="b17ed-138">[Maak een mandje](create-a-cart.md) om de verzameling catalogus items te bewaren die u wilt kopen.</span><span class="sxs-lookup"><span data-stu-id="b17ed-138">[Create a cart](create-a-cart.md) to hold the collection of catalog items that you intend to buy.</span></span> <span data-ttu-id="b17ed-139">Wanneer u een [winkel wagen](cart-resources.md#cart)maakt, worden de [Winkelwagen regel items](cart-resources.md#cartlineitem) automatisch gegroepeerd op basis van wat er in dezelfde [volg orde](order-resources.md#order)kan worden aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="b17ed-139">When you create a [cart](cart-resources.md#cart), the [cart line items](cart-resources.md#cartlineitem) are automatically grouped based on what can be purchased together in the same [order](order-resources.md#order).</span></span> <span data-ttu-id="b17ed-140">(U kunt ook [een winkel wagen bijwerken](update-a-cart.md).)</span><span class="sxs-lookup"><span data-stu-id="b17ed-140">(You can also [update a cart](update-a-cart.md).)</span></span>
2. <span data-ttu-id="b17ed-141">[Bekijk de winkel wagen](checkout-a-cart.md), wat resulteert in het maken van een [order](order-resources.md#order).</span><span class="sxs-lookup"><span data-stu-id="b17ed-141">[Check out the cart](checkout-a-cart.md), which results in the creation of an [order](order-resources.md#order).</span></span>

### <a name="get-order-details"></a><span data-ttu-id="b17ed-142">Bestellingsgegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="b17ed-142">Get order details</span></span>

<span data-ttu-id="b17ed-143">U kunt [de details van een afzonderlijke order ophalen met behulp van de order-id](get-an-order-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="b17ed-143">You can [retrieve the details of an individual order using the order ID](get-an-order-by-id.md).</span></span> <span data-ttu-id="b17ed-144">U kunt ook [een lijst met alle orders voor een specifieke klant ophalen](get-all-of-a-customer-s-orders.md).</span><span class="sxs-lookup"><span data-stu-id="b17ed-144">You can also [retrieve a list of all orders for a specific customer](get-all-of-a-customer-s-orders.md).</span></span>

> [!NOTE]
> <span data-ttu-id="b17ed-145">Nadat een order is verzonden, is er een vertraging van Maxi maal 15 minuten voordat de order wordt weer gegeven in de order lijst van die klant.</span><span class="sxs-lookup"><span data-stu-id="b17ed-145">After an order is submitted, there is a delay of up to 15 minutes before the order appears in that customer's order list.</span></span>

## <a name="get-activation-link"></a><span data-ttu-id="b17ed-146">Activerings koppeling ophalen</span><span class="sxs-lookup"><span data-stu-id="b17ed-146">Get activation link</span></span>

<span data-ttu-id="b17ed-147">De partner of klant moet abonnementen activeren voor Azure Marketplace-producten.</span><span class="sxs-lookup"><span data-stu-id="b17ed-147">The partner or customer must activate subscriptions to Azure Marketplace products.</span></span> <span data-ttu-id="b17ed-148">U kunt [een activerings koppeling verkrijgen per order regel item](get-activation-link-by-order-line-item.md).</span><span class="sxs-lookup"><span data-stu-id="b17ed-148">You can [get an activation link by order line item](get-activation-link-by-order-line-item.md).</span></span> <span data-ttu-id="b17ed-149">U kunt ook [een abonnement op id ophalen](get-a-subscription-by-id.md)en vervolgens de eigenschap **links** ervan opsommen om een activerings koppeling te maken.</span><span class="sxs-lookup"><span data-stu-id="b17ed-149">You can also [get a subscription by ID](get-a-subscription-by-id.md), then enumerate its **Links** property to create an activation link.</span></span>

## <a name="lifecycle-management"></a><span data-ttu-id="b17ed-150">Levenscyclus beheer</span><span class="sxs-lookup"><span data-stu-id="b17ed-150">Lifecycle management</span></span>

<span data-ttu-id="b17ed-151">U kunt de levens cyclus van uw abonnementen op commerciële Marketplace-Producten beheren met de volgende methoden:</span><span class="sxs-lookup"><span data-stu-id="b17ed-151">You can manage the lifecycle of your subscriptions to commercial marketplace products using the following methods:</span></span>

* [<span data-ttu-id="b17ed-152">Een abonnement op de commerciële marketplace annuleren</span><span class="sxs-lookup"><span data-stu-id="b17ed-152">Cancel a commercial marketplace subscription</span></span>](cancel-an-azure-marketplace-subscription.md)
* [<span data-ttu-id="b17ed-153">Autoverlengen voor een abonnement op commerciële Marketplace in-of uitschakelen</span><span class="sxs-lookup"><span data-stu-id="b17ed-153">Enable or disable autorenew for a commercial marketplace subscription</span></span>](update-autorenew-for-an-azure-marketplace-subscription.md)

## <a name="quantity-management"></a><span data-ttu-id="b17ed-154">Hoeveelheids beheer</span><span class="sxs-lookup"><span data-stu-id="b17ed-154">Quantity management</span></span>

<span data-ttu-id="b17ed-155">De hoeveelheid van een abonnement op commerciële Marketplace moet binnen de grenzen vallen die door de bijbehorende [SKU](product-resources.md#sku) zijn gedefinieerd (Zie de kenmerken **minimumQuantity** en **maximumQuantity** ).</span><span class="sxs-lookup"><span data-stu-id="b17ed-155">The quantity of a commercial marketplace subscription must be within the limits defined by its associated [SKU](product-resources.md#sku) (see the **minimumQuantity** and **maximumQuantity** attributes).</span></span> <span data-ttu-id="b17ed-156">Als u de hoeveelheid van een abonnement op commerciële Marketplace wilt bijwerken, gebruikt u de volgende methode:</span><span class="sxs-lookup"><span data-stu-id="b17ed-156">To update the quantity of a commercial marketplace subscription, use the following method:</span></span>

* [<span data-ttu-id="b17ed-157">De hoeveelheid van een abonnement wijzigen</span><span class="sxs-lookup"><span data-stu-id="b17ed-157">Change the quantity of a subscription</span></span>](change-the-quantity-of-a-subscription.md)

## <a name="invoice-and-reconciliation"></a><span data-ttu-id="b17ed-158">Factuur en reconciliatie</span><span class="sxs-lookup"><span data-stu-id="b17ed-158">Invoice and reconciliation</span></span>

<span data-ttu-id="b17ed-159">U kunt de volgende methoden gebruiken om klant [facturen](invoice-resources.md) (inclusief kosten voor abonnementen op commerciële Marketplace-Producten) te beheren:</span><span class="sxs-lookup"><span data-stu-id="b17ed-159">You can manage customer [invoices](invoice-resources.md) (including charges for subscriptions to commercial marketplace products) using the following methods:</span></span>

* [<span data-ttu-id="b17ed-160">Gefactureerde commerciële Marketplace voor factuur gebruik ophalen regel items</span><span class="sxs-lookup"><span data-stu-id="b17ed-160">Get invoice billed commercial marketplace consumption line items</span></span>](get-invoice-billed-consumption-lineitems.md)
* [<span data-ttu-id="b17ed-161">Koppelingen voor factuurramingen ophalen</span><span class="sxs-lookup"><span data-stu-id="b17ed-161">Get invoice estimate links</span></span>](get-invoice-estimate-links.md)
* [<span data-ttu-id="b17ed-162">Factuur niet-gefactureerde commerciële Marketplace verbruik regel items ophalen</span><span class="sxs-lookup"><span data-stu-id="b17ed-162">Get invoice unbilled commercial marketplace consumption line items</span></span>](get-invoice-unbilled-consumption-lineitems.md)
* [<span data-ttu-id="b17ed-163">Regel items voor niet-gefactureerde reconciliatie van factuur ophalen</span><span class="sxs-lookup"><span data-stu-id="b17ed-163">Get invoice unbilled reconciliation line items</span></span>](get-invoice-unbilled-recon-lineitems.md)

## <a name="test-using-integration-sandbox-account"></a><span data-ttu-id="b17ed-164">Testen met behulp van een sandbox-account voor integratie</span><span class="sxs-lookup"><span data-stu-id="b17ed-164">Test using integration sandbox account</span></span>

<span data-ttu-id="b17ed-165">Nadat u in productie een abonnement hebt gemaakt op een commerciële Marketplace SaaS-producten, moet u een persoonlijke activerings koppeling ophalen van het partner centrum en de site van de uitgever bezoeken om het installatie proces te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="b17ed-165">In production, after you have created a subscription to commercial marketplace SaaS products, you need to retrieve a personalized activation link from Partner Center and visit the publisher's site to complete the setup process.</span></span> <span data-ttu-id="b17ed-166">De facturering van het abonnement wordt pas gestart nadat de installatie is voltooid.</span><span class="sxs-lookup"><span data-stu-id="b17ed-166">Subscription billing will begin only after setup is complete.</span></span>

<span data-ttu-id="b17ed-167">In de CSP-sandbox-omgeving is er geen integratie met Isv's.</span><span class="sxs-lookup"><span data-stu-id="b17ed-167">In the CSP sandbox environment, there is no integration with ISVs.</span></span> <span data-ttu-id="b17ed-168">Als u probeert een activerings koppeling op te halen van het partner centrum, wordt een dummy-koppeling geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="b17ed-168">If you try to retrieve an activation link from Partner Center, a dummy link will be returned.</span></span> <span data-ttu-id="b17ed-169">U kunt deze dummy koppeling niet gebruiken om het installatie proces te volt ooien op de site van de uitgever.</span><span class="sxs-lookup"><span data-stu-id="b17ed-169">You cannot use this dummy link to complete the setup process at the publisher's site.</span></span> <span data-ttu-id="b17ed-170">Gebruik de volgende methode om het abonnement te activeren als u het sandbox-account voor integratie wilt gebruiken om de facturering te testen voor abonnementen op de SaaS-producten van de commerciële markt plaats.</span><span class="sxs-lookup"><span data-stu-id="b17ed-170">To use the integration sandbox account to test billing for subscriptions to commercial marketplace SaaS products, use the following method to activate the subscription instead.</span></span> <span data-ttu-id="b17ed-171">De facturering van het abonnement wordt gestart nadat de activering is voltooid:</span><span class="sxs-lookup"><span data-stu-id="b17ed-171">Subscription billing will begin after successful activation:</span></span>

* [<span data-ttu-id="b17ed-172">Een sandbox-abonnement voor commerciële Marketplace-producten activeren</span><span class="sxs-lookup"><span data-stu-id="b17ed-172">Activate a sandbox subscription for commercial marketplace products</span></span>](activate-sandbox-subscription-azure-marketplace-products.md)

