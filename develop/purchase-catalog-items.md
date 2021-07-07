---
title: Catalogusitems kopen
description: Catalogusitems kopen met behulp van Partner Center API.
ms.date: 07/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d3e0deedff194b1c836d9266c2201a2b3a52cc1b
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445354"
---
# <a name="purchase-catalog-items"></a><span data-ttu-id="0fe1b-103">Catalogusitems kopen</span><span class="sxs-lookup"><span data-stu-id="0fe1b-103">Purchase catalog items</span></span>

<span data-ttu-id="0fe1b-104">In het volgende scenario wordt het algemene proces gedemonstreerd voor het kopen van items uit de catalogus met behulp van Partner Center API.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-104">The following scenario demonstrates the generic process for purchasing items from the catalog by using the Partner Center API.</span></span>

## <a name="discovery"></a><span data-ttu-id="0fe1b-105">Detectie</span><span class="sxs-lookup"><span data-stu-id="0fe1b-105">Discovery</span></span>

<span data-ttu-id="0fe1b-106">Selecteer producten en SKU's (Stock Keeping Units) en controleer de beschikbaarheid ervan met behulp van de Partner Center API-modellen:</span><span class="sxs-lookup"><span data-stu-id="0fe1b-106">Select products and Stock Keeping Units (SKUs) and check their availability using the following Partner Center API models:</span></span>

- <span data-ttu-id="0fe1b-107">[Product:](product-resources.md#product) een groeperingsconsistente voor opschatbare goederen of services.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-107">[Product](product-resources.md#product) - A grouping construct for purchasable goods or services.</span></span> <span data-ttu-id="0fe1b-108">Een product op zichzelf is geen opschatbaar item.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-108">A product by itself isn't a purchasable item.</span></span>
- <span data-ttu-id="0fe1b-109">[SKU:](product-resources.md#sku) een opschatbare SKU onder een product.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-109">[SKU](product-resources.md#sku) - A purchasable SKU under a product.</span></span> <span data-ttu-id="0fe1b-110">Deze vertegenwoordigen de verschillende vormen van het product.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-110">These represent the different shapes of the product.</span></span>
- <span data-ttu-id="0fe1b-111">[Beschikbaarheid:](product-resources.md#availability) een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land, valuta en branchesegment).</span><span class="sxs-lookup"><span data-stu-id="0fe1b-111">[Availability](product-resources.md#availability) - A configuration in which a SKU is available for purchase (such as country, currency, and industry segment).</span></span>

<span data-ttu-id="0fe1b-112">Als u een item uit de catalogus wilt kopen, moet u de volgende stappen voltooien:</span><span class="sxs-lookup"><span data-stu-id="0fe1b-112">To purchase an item from the catalog, complete the following steps:</span></span>

1. <span data-ttu-id="0fe1b-113">Identificeer en haal het product en de SKU op die u wilt kopen.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-113">Identify and retrieve the Product and SKU that you want to purchase.</span></span>

   - [<span data-ttu-id="0fe1b-114">Een lijst met producten op halen</span><span class="sxs-lookup"><span data-stu-id="0fe1b-114">Get a list of products</span></span>](get-a-list-of-products.md)
   - [<span data-ttu-id="0fe1b-115">Een product op halen met behulp van de product-id</span><span class="sxs-lookup"><span data-stu-id="0fe1b-115">Get a product using the product ID</span></span>](get-a-product-by-id.md)
   - [<span data-ttu-id="0fe1b-116">Een lijst met SKU's voor een product op halen</span><span class="sxs-lookup"><span data-stu-id="0fe1b-116">Get a list of SKUs for a product</span></span>](get-a-list-of-skus-for-a-product.md)
   - [<span data-ttu-id="0fe1b-117">Een SKU op halen met behulp van de SKU-id</span><span class="sxs-lookup"><span data-stu-id="0fe1b-117">Get a SKU using the SKU ID</span></span>](get-a-sku-by-id.md)

2. <span data-ttu-id="0fe1b-118">Controleer de inventaris voor een SKU.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-118">Check the inventory for a SKU.</span></span> <span data-ttu-id="0fe1b-119">Deze stap is alleen nodig voor SKU's die zijn gelabeld met de waarde **InventoryCheck** in de eigenschap [purchasePrerequisites.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="0fe1b-119">This step is only needed for SKUs that are tagged with an **InventoryCheck** value in the [purchasePrerequisites](product-resources.md#sku) property.</span></span>

   - [<span data-ttu-id="0fe1b-120">Voorraad controleren</span><span class="sxs-lookup"><span data-stu-id="0fe1b-120">Check Inventory</span></span>](check-inventory.md)

3. <span data-ttu-id="0fe1b-121">Haal de [beschikbaarheid voor](product-resources.md#availability) de [SKU op.](product-resources.md#sku)</span><span class="sxs-lookup"><span data-stu-id="0fe1b-121">Retrieve the [availability](product-resources.md#availability) for the [SKU](product-resources.md#sku).</span></span> <span data-ttu-id="0fe1b-122">U hebt de **CatalogItemId van de** beschikbaarheid nodig bij het plaatsen van de order.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-122">You will need the **CatalogItemId** of the availability when placing the order.</span></span> <span data-ttu-id="0fe1b-123">Gebruik een van de volgende API's om deze waarde op te halen:</span><span class="sxs-lookup"><span data-stu-id="0fe1b-123">To get this value, use one of the following APIs:</span></span>

   - [<span data-ttu-id="0fe1b-124">Een lijst met beschikbaarheid voor een SKU op halen</span><span class="sxs-lookup"><span data-stu-id="0fe1b-124">Get a list of availabilities for a SKU</span></span>](get-a-list-of-availabilities-for-a-sku.md)
   - [<span data-ttu-id="0fe1b-125">Een beschikbaarheid krijgen met behulp van de beschikbaarheids-id</span><span class="sxs-lookup"><span data-stu-id="0fe1b-125">Get an availability using the availability ID</span></span>](get-an-availability-by-id.md)

## <a name="order-submission"></a><span data-ttu-id="0fe1b-126">Verzending van order</span><span class="sxs-lookup"><span data-stu-id="0fe1b-126">Order submission</span></span>

<span data-ttu-id="0fe1b-127">Ga als volgt te werk om uw catalogusitemvolgorde in te dienen:</span><span class="sxs-lookup"><span data-stu-id="0fe1b-127">To submit your catalog item order, do the following:</span></span>

1. <span data-ttu-id="0fe1b-128">Maak een [winkelwagen](cart-resources.md) voor de verzameling catalogusitems die u wilt kopen.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-128">Create a [Cart](cart-resources.md) to hold the collection of catalog items that you intend to buy.</span></span> <span data-ttu-id="0fe1b-129">Wanneer u een winkelwagen maakt, worden de [regelitems](cart-resources.md#cartlineitem) van de winkelwagen automatisch gegroepeerd op basis van wat samen in dezelfde order kan worden [gekocht.](order-resources.md)</span><span class="sxs-lookup"><span data-stu-id="0fe1b-129">When you create a cart, the [cart line items](cart-resources.md#cartlineitem) are automatically grouped based on what can be purchased together in the same [Order](order-resources.md).</span></span>

   - [<span data-ttu-id="0fe1b-130">Een winkelwagen maken</span><span class="sxs-lookup"><span data-stu-id="0fe1b-130">Create a shopping cart</span></span>](create-a-cart.md)
   - [<span data-ttu-id="0fe1b-131">Een winkelwagen bijwerken</span><span class="sxs-lookup"><span data-stu-id="0fe1b-131">Update a shopping cart</span></span>](update-a-cart.md)

2. <span data-ttu-id="0fe1b-132">Bekijk de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-132">Check out the cart.</span></span> <span data-ttu-id="0fe1b-133">Als u een winkelwagen bekijkt, wordt er een order [gemaakt.](order-resources.md)</span><span class="sxs-lookup"><span data-stu-id="0fe1b-133">Checking out a cart results in the creation of an [Order](order-resources.md).</span></span>

   - [<span data-ttu-id="0fe1b-134">De winkelwagen uitchecken</span><span class="sxs-lookup"><span data-stu-id="0fe1b-134">Checkout the cart</span></span>](checkout-a-cart.md)

## <a name="get-order-details"></a><span data-ttu-id="0fe1b-135">Orderdetails op halen</span><span class="sxs-lookup"><span data-stu-id="0fe1b-135">Get order details</span></span>

<span data-ttu-id="0fe1b-136">U kunt de details van een afzonderlijke order ophalen met behulp van de order-id of een lijst met orders voor een klant ophalen.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-136">You can retrieve the details of an individual order using the order ID, or get a list of orders for a customer.</span></span> <span data-ttu-id="0fe1b-137">Er is een vertraging van maximaal 15 minuten tussen het moment waarop een order wordt verzonden en wanneer deze wordt weergegeven in een lijst met orders van een klant.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-137">There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a list of a customer's orders.</span></span>

- <span data-ttu-id="0fe1b-138">Zie [Een order op id krijgen](get-an-order-by-id.md) om de details van een afzonderlijke order op te halen met behulp van de order-id's.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-138">See [Get an order by ID](get-an-order-by-id.md) to get the details of an individual order using the order IDs.</span></span>

- <span data-ttu-id="0fe1b-139">Zie [Get all of a customer's orders (Alle orders van een klant op halen)](get-all-of-a-customer-s-orders.md) voor een lijst met orders voor een klant met behulp van de klant-id.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-139">See [Get all of a customer's orders](get-all-of-a-customer-s-orders.md) to get a list of orders for a customer using the customer ID.</span></span>

- <span data-ttu-id="0fe1b-140">Zie Get [a list of orders by customer](get-a-list-of-orders-by-customer-and-billing-cycle-type.md) and billing cycle [](product-resources.md#billingcycletype) type (Een lijst met orders per klant en type factureringscyclus) voor een lijst met orders voor een klant per type factureringscyclus, zodat u catalogusitemorders (een keer kosten) en jaarlijkse of maandelijks gefactureerde orders afzonderlijk kunt bekijken.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-140">See [Get a list of orders by customer and billing cycle type](get-a-list-of-orders-by-customer-and-billing-cycle-type.md) to get a list of orders for a customer by [billing cycle type](product-resources.md#billingcycletype) allowing you to list catalog item orders (one-time charges) and annual or monthly billed orders separately.</span></span>

## <a name="lifecycle-management"></a><span data-ttu-id="0fe1b-141">Levenscyclusbeheer</span><span class="sxs-lookup"><span data-stu-id="0fe1b-141">Lifecycle management</span></span>

<span data-ttu-id="0fe1b-142">Als onderdeel van het beheren van de levenscyclus van uw catalogusitems in Partner Center, kunt u informatie ophalen over uw catalogusitem Rechten en [reserveringsgegevens](entitlement-resources.md)ophalen met behulp van de reserveringsorder-id.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-142">As part of managing the lifecycle of your catalog items in Partner Center, you can retrieve information about your catalog item [Entitlements](entitlement-resources.md), and get reservation details using the reservation order ID.</span></span> <span data-ttu-id="0fe1b-143">Zie Rechten krijgen voor voorbeelden van [hoe u dit doet.](get-a-collection-of-entitlements.md)</span><span class="sxs-lookup"><span data-stu-id="0fe1b-143">For examples of how to do this, see [Get entitlements](get-a-collection-of-entitlements.md).</span></span>   

## <a name="invoice-and-reconciliation"></a><span data-ttu-id="0fe1b-144">Factuur en afstemming</span><span class="sxs-lookup"><span data-stu-id="0fe1b-144">Invoice and reconciliation</span></span>

<span data-ttu-id="0fe1b-145">In de volgende scenario's ziet u hoe [](invoice-resources.md)u de facturen van uw klant programmatisch kunt weergeven en de saldo's en samenvattingen van uw account kunt opmaken die een een time-kosten voor catalogusitems bevatten.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-145">The following scenarios show you how to programmatically view your customer's [invoices](invoice-resources.md), and get your account balances and summaries that include one-time charges for catalog items.</span></span>

### <a name="balance-and-payment"></a><span data-ttu-id="0fe1b-146">Saldo en betaling</span><span class="sxs-lookup"><span data-stu-id="0fe1b-146">Balance and payment</span></span>

<span data-ttu-id="0fe1b-147">Zie Uw huidige rekeningsaldo opmaken om het huidige rekeningsaldo op te halen in uw standaardvalutatype dat een saldo is van zowel terugkerende als eenmalige kosten [(catalogusitem).](get-the-reseller-s-current-account-balance.md)</span><span class="sxs-lookup"><span data-stu-id="0fe1b-147">To get current account balance in your default currency type that is a balance of both recurring and one-time (catalog item) charges, see [Get your current account balance](get-the-reseller-s-current-account-balance.md).</span></span>

### <a name="multi-currency-balance-and-payment"></a><span data-ttu-id="0fe1b-148">Saldo en betaling met meerdere valuta</span><span class="sxs-lookup"><span data-stu-id="0fe1b-148">Multi-currency balance and payment</span></span>

<span data-ttu-id="0fe1b-149">Zie [Factuuroverzichten](get-invoice-summaries.md)ophalen voor het saldo van uw huidige rekening en een verzameling factuuroverzichten met zowel terugkerende als eenmalige kosten voor elk van de valutatypen van uw klant.</span><span class="sxs-lookup"><span data-stu-id="0fe1b-149">To get your current account balance and a collection of invoice summaries containing an invoice summary with both recurring and one-time charges for each of your customer's currency types, see [Get invoice summaries](get-invoice-summaries.md).</span></span>

### <a name="invoices"></a><span data-ttu-id="0fe1b-150">Facturen</span><span class="sxs-lookup"><span data-stu-id="0fe1b-150">Invoices</span></span>

<span data-ttu-id="0fe1b-151">Zie Een verzameling facturen ophalen voor een verzameling facturen met zowel terugkerende als eenmalige [kosten.](get-a-collection-of-invoices.md)</span><span class="sxs-lookup"><span data-stu-id="0fe1b-151">To get a collection of invoices that show both recurring and one-time charges, see [Get a collection of invoices](get-a-collection-of-invoices.md).</span></span> 

### <a name="single-invoice"></a><span data-ttu-id="0fe1b-152">Eén factuur</span><span class="sxs-lookup"><span data-stu-id="0fe1b-152">Single Invoice</span></span>

<span data-ttu-id="0fe1b-153">Zie Een factuur ophalen op id als u een specifieke factuur wilt ophalen met behulp van de [factuur-id.](get-invoice-by-id.md)</span><span class="sxs-lookup"><span data-stu-id="0fe1b-153">To retrieve a specific invoice using the invoice ID, see [Get an invoice by ID](get-invoice-by-id.md).</span></span>  

### <a name="reconciliation"></a><span data-ttu-id="0fe1b-154">Verzoening</span><span class="sxs-lookup"><span data-stu-id="0fe1b-154">Reconciliation</span></span>

<span data-ttu-id="0fe1b-155">Zie Factuurregelitems ophalen voor een verzameling factuurregelitems (afstemmingsregelitems) voor een specifieke [factuur-id.](get-invoiceline-items.md)</span><span class="sxs-lookup"><span data-stu-id="0fe1b-155">To get a collection of invoice line item details (Reconciliation line items) for a specific invoice ID, see [Get invoice line items](get-invoiceline-items.md).</span></span>  

### <a name="download-an-invoice-as-a-pdf"></a><span data-ttu-id="0fe1b-156">Een factuur downloaden als PDF</span><span class="sxs-lookup"><span data-stu-id="0fe1b-156">Download an invoice as a PDF</span></span>

<span data-ttu-id="0fe1b-157">Zie Een factuuroverzicht ophalen als u een factuuroverzicht in PDF-vorm wilt ophalen met behulp van een [factuur-id.](get-invoice-statement.md)</span><span class="sxs-lookup"><span data-stu-id="0fe1b-157">To retrieve an invoice statement in PDF form using an invoice ID, see [Get an invoice statement](get-invoice-statement.md).</span></span>
