---
title: Catalogusitems kopen
description: Catalogus items aanschaffen met de API van partner Center.
ms.date: 07/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f2b3a34cdb6b29cb7eaaf5d977e4588f538fff09
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767222"
---
# <a name="purchase-catalog-items"></a><span data-ttu-id="14f48-103">Catalogusitems kopen</span><span class="sxs-lookup"><span data-stu-id="14f48-103">Purchase catalog items</span></span>

<span data-ttu-id="14f48-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="14f48-104">**Applies To**</span></span>

- <span data-ttu-id="14f48-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="14f48-105">Partner Center</span></span>

<span data-ttu-id="14f48-106">In het volgende scenario wordt het algemene proces voor het kopen van items uit de catalogus gedemonstreerd met behulp van de Partner Center-API.</span><span class="sxs-lookup"><span data-stu-id="14f48-106">The following scenario demonstrates the generic process for purchasing items from the catalog by using the Partner Center API.</span></span>

## <a name="discovery"></a><span data-ttu-id="14f48-107">Detectie</span><span class="sxs-lookup"><span data-stu-id="14f48-107">Discovery</span></span>

<span data-ttu-id="14f48-108">Selecteer producten en Sku's en controleer hun Beschik baarheid met behulp van de volgende partner Center API-modellen:</span><span class="sxs-lookup"><span data-stu-id="14f48-108">Select products and SKUs and check their availability using the following Partner Center API models:</span></span>

- <span data-ttu-id="14f48-109">[Product](product-resources.md#product) : een groeperings constructie voor tevens-goederen of-services.</span><span class="sxs-lookup"><span data-stu-id="14f48-109">[Product](product-resources.md#product) - A grouping construct for purchasable goods or services.</span></span> <span data-ttu-id="14f48-110">Een product zelf is geen tevens-item.</span><span class="sxs-lookup"><span data-stu-id="14f48-110">A product by itself isn't a purchasable item.</span></span>
- <span data-ttu-id="14f48-111">[SKU](product-resources.md#sku) : een SKU (tevens Stock Keeping Unit) onder een product.</span><span class="sxs-lookup"><span data-stu-id="14f48-111">[SKU](product-resources.md#sku) - A purchasable Stock Keeping Unit (SKU) under a product.</span></span> <span data-ttu-id="14f48-112">Deze vertegenwoordigen de verschillende vormen van het product.</span><span class="sxs-lookup"><span data-stu-id="14f48-112">These represent the different shapes of the product.</span></span>
- <span data-ttu-id="14f48-113">[Beschik baarheid](product-resources.md#availability) : een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land-, valuta-en sector segment).</span><span class="sxs-lookup"><span data-stu-id="14f48-113">[Availability](product-resources.md#availability) - A configuration in which a SKU is available for purchase (such as country, currency and industry segment).</span></span>

<span data-ttu-id="14f48-114">Voer de volgende stappen uit om een item te kopen vanuit de catalogus:</span><span class="sxs-lookup"><span data-stu-id="14f48-114">To purchase an item from the catalog, complete the following steps:</span></span>

1. <span data-ttu-id="14f48-115">Identificeer en haal het product en de SKU op die u wilt kopen.</span><span class="sxs-lookup"><span data-stu-id="14f48-115">Identify and retrieve the Product and SKU that you want to purchase.</span></span>

   - [<span data-ttu-id="14f48-116">Een lijst met producten ophalen</span><span class="sxs-lookup"><span data-stu-id="14f48-116">Get a list of products</span></span>](get-a-list-of-products.md)
   - [<span data-ttu-id="14f48-117">Een product ophalen met de product-ID</span><span class="sxs-lookup"><span data-stu-id="14f48-117">Get a product using the product ID</span></span>](get-a-product-by-id.md)
   - [<span data-ttu-id="14f48-118">Een lijst met Sku's voor een product ophalen</span><span class="sxs-lookup"><span data-stu-id="14f48-118">Get a list of SKUs for a product</span></span>](get-a-list-of-skus-for-a-product.md)
   - [<span data-ttu-id="14f48-119">Een SKU ophalen met behulp van de SKU-ID</span><span class="sxs-lookup"><span data-stu-id="14f48-119">Get a SKU using the SKU ID</span></span>](get-a-sku-by-id.md)

2. <span data-ttu-id="14f48-120">Controleer de inventarisatie van een SKU.</span><span class="sxs-lookup"><span data-stu-id="14f48-120">Check the inventory for a SKU.</span></span> <span data-ttu-id="14f48-121">Deze stap is alleen nodig voor Sku's die zijn gelabeld met een **InventoryCheck** -waarde in de eigenschap [purchasePrerequisites](product-resources.md#sku) .</span><span class="sxs-lookup"><span data-stu-id="14f48-121">This step is only needed for SKUs that are tagged with an **InventoryCheck** value in the [purchasePrerequisites](product-resources.md#sku) property.</span></span>

   - [<span data-ttu-id="14f48-122">Voorraad controleren</span><span class="sxs-lookup"><span data-stu-id="14f48-122">Check Inventory</span></span>](check-inventory.md)

3. <span data-ttu-id="14f48-123">De [Beschik baarheid](product-resources.md#availability) voor de [SKU](product-resources.md#sku)ophalen.</span><span class="sxs-lookup"><span data-stu-id="14f48-123">Retrieve the [availability](product-resources.md#availability) for the [SKU](product-resources.md#sku).</span></span> <span data-ttu-id="14f48-124">U hebt de **CatalogItemId** van de beschik baarheid nodig wanneer u de order plaatst.</span><span class="sxs-lookup"><span data-stu-id="14f48-124">You will need the **CatalogItemId** of the availability when placing the order.</span></span> <span data-ttu-id="14f48-125">Gebruik een van de volgende Api's om deze waarde op te halen:</span><span class="sxs-lookup"><span data-stu-id="14f48-125">To get this value, use one of the following APIs:</span></span>

   - [<span data-ttu-id="14f48-126">Een lijst met Beschik baarheid voor een SKU ophalen</span><span class="sxs-lookup"><span data-stu-id="14f48-126">Get a list of availabilities for a SKU</span></span>](get-a-list-of-availabilities-for-a-sku.md)
   - [<span data-ttu-id="14f48-127">Krijg een Beschik baarheid met behulp van de beschikbaarheids-ID</span><span class="sxs-lookup"><span data-stu-id="14f48-127">Get an availability using the availability ID</span></span>](get-an-availability-by-id.md)

## <a name="order-submission"></a><span data-ttu-id="14f48-128">Verzen ding best Ellen</span><span class="sxs-lookup"><span data-stu-id="14f48-128">Order submission</span></span>

<span data-ttu-id="14f48-129">Ga als volgt te werk om de volg orde van uw catalogus items te verzenden:</span><span class="sxs-lookup"><span data-stu-id="14f48-129">To submit your catalog item order, do the following:</span></span>

1. <span data-ttu-id="14f48-130">Maak een [mandje](cart-resources.md) om de verzameling catalogus items te bewaren die u wilt kopen.</span><span class="sxs-lookup"><span data-stu-id="14f48-130">Create a [Cart](cart-resources.md) to hold the collection of catalog items that you intend to buy.</span></span> <span data-ttu-id="14f48-131">Wanneer u een winkel wagen maakt, worden de [Winkelwagen regel items](cart-resources.md#cartlineitem) automatisch gegroepeerd op basis van wat er in dezelfde [volg orde](order-resources.md)kan worden aangeschaft.</span><span class="sxs-lookup"><span data-stu-id="14f48-131">When you create a cart, the [cart line items](cart-resources.md#cartlineitem) are automatically grouped based on what can be purchased together in the same [Order](order-resources.md).</span></span>

   - [<span data-ttu-id="14f48-132">Een winkel wagen maken</span><span class="sxs-lookup"><span data-stu-id="14f48-132">Create a shopping cart</span></span>](create-a-cart.md)
   - [<span data-ttu-id="14f48-133">Een winkel wagen bijwerken</span><span class="sxs-lookup"><span data-stu-id="14f48-133">Update a shopping cart</span></span>](update-a-cart.md)

2. <span data-ttu-id="14f48-134">Bekijk de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="14f48-134">Check out the cart.</span></span> <span data-ttu-id="14f48-135">Het uitchecken van een winkel wagen resulteert in het maken van een [order](order-resources.md).</span><span class="sxs-lookup"><span data-stu-id="14f48-135">Checking out a cart results in the creation of an [Order](order-resources.md).</span></span>

   - [<span data-ttu-id="14f48-136">De winkel wagen afhandelen</span><span class="sxs-lookup"><span data-stu-id="14f48-136">Checkout the cart</span></span>](checkout-a-cart.md)

## <a name="get-order-details"></a><span data-ttu-id="14f48-137">Bestellingsgegevens ophalen</span><span class="sxs-lookup"><span data-stu-id="14f48-137">Get order details</span></span>

<span data-ttu-id="14f48-138">U kunt de details van een afzonderlijke order ophalen met behulp van de order-ID of een lijst met orders voor een klant ophalen.</span><span class="sxs-lookup"><span data-stu-id="14f48-138">You can retrieve the details of an individual order using the order ID, or get a list of orders for a customer.</span></span> <span data-ttu-id="14f48-139">Er is een vertraging van Maxi maal 15 minuten tussen de tijd dat een bestelling wordt verzonden en wanneer deze wordt weer gegeven in een lijst met de orders van een klant.</span><span class="sxs-lookup"><span data-stu-id="14f48-139">There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a list of a customer's orders.</span></span>

- <span data-ttu-id="14f48-140">Zie [een order op basis van id ophalen](get-an-order-by-id.md) om de details van een afzonderlijke order op te halen met behulp van de order-id's.</span><span class="sxs-lookup"><span data-stu-id="14f48-140">See [Get an order by ID](get-an-order-by-id.md) to get the details of an individual order using the order IDs.</span></span>

- <span data-ttu-id="14f48-141">Zie [alle orders van een klant ophalen](get-all-of-a-customer-s-orders.md) voor een lijst met orders voor een klant met behulp van de klant-id.</span><span class="sxs-lookup"><span data-stu-id="14f48-141">See [Get all of a customer's orders](get-all-of-a-customer-s-orders.md) to get a list of orders for a customer using the customer ID.</span></span>

- <span data-ttu-id="14f48-142">Zie [een lijst met orders ophalen per klant en facturerings cyclus type](get-a-list-of-orders-by-customer-and-billing-cycle-type.md) voor een lijst met orders voor een klant per [facturerings cyclus type](product-resources.md#billingcycletype) , zodat u orders voor catalogus items (eenmalige kosten) en jaarlijks of maandelijks gefactureerde orders afzonderlijk kunt weer geven.</span><span class="sxs-lookup"><span data-stu-id="14f48-142">See [Get a list of orders by customer and billing cycle type](get-a-list-of-orders-by-customer-and-billing-cycle-type.md) to get a list of orders for a customer by [billing cycle type](product-resources.md#billingcycletype) allowing you to list catalog item orders (one-time charges) and annual or monthly billed orders separately.</span></span>

## <a name="lifecycle-management"></a><span data-ttu-id="14f48-143">Levenscyclus beheer</span><span class="sxs-lookup"><span data-stu-id="14f48-143">Lifecycle management</span></span>

<span data-ttu-id="14f48-144">Als onderdeel van het beheer van de levens cyclus van uw catalogus items in het partner centrum, kunt u informatie ophalen over de [rechten](entitlement-resources.md)van uw catalogus item en reserverings Details ophalen met behulp van de reserverings order-id.</span><span class="sxs-lookup"><span data-stu-id="14f48-144">As part of managing the lifecycle of your catalog items in Partner Center, you can retrieve information about your catalog item [Entitlements](entitlement-resources.md), and get reservation details using the reservation order ID.</span></span> <span data-ttu-id="14f48-145">Zie [rechten ophalen](get-a-collection-of-entitlements.md)voor voor beelden van hoe u dit doet.</span><span class="sxs-lookup"><span data-stu-id="14f48-145">For examples of how to do this, see [Get entitlements](get-a-collection-of-entitlements.md).</span></span>   

## <a name="invoice-and-reconciliation"></a><span data-ttu-id="14f48-146">Factuur en reconciliatie</span><span class="sxs-lookup"><span data-stu-id="14f48-146">Invoice and reconciliation</span></span>

<span data-ttu-id="14f48-147">In de volgende scenario's ziet u hoe u de [facturen](invoice-resources.md)van uw klant programmatisch kunt bekijken en hoe u uw account saldi en samen vattingen kunt ophalen die eenmalige kosten voor catalogus items bevatten.</span><span class="sxs-lookup"><span data-stu-id="14f48-147">The following scenarios show you how to programmatically view your customer's [invoices](invoice-resources.md), and get your account balances and summaries that include one-time charges for catalog items.</span></span>

### <a name="balance-and-payment"></a><span data-ttu-id="14f48-148">Saldo en betaling</span><span class="sxs-lookup"><span data-stu-id="14f48-148">Balance and payment</span></span>

<span data-ttu-id="14f48-149">Als u het huidige account saldo wilt ophalen in het standaard valuta type dat een saldo van de kosten voor terugkerend en eenmalig (catalogus item) is, raadpleegt u [uw huidige account saldo ophalen](get-the-reseller-s-current-account-balance.md).</span><span class="sxs-lookup"><span data-stu-id="14f48-149">To get current account balance in your default currency type that is a balance of both recurring and one-time (catalog item) charges, see [Get your current account balance](get-the-reseller-s-current-account-balance.md).</span></span>

### <a name="multi-currency-balance-and-payment"></a><span data-ttu-id="14f48-150">Saldo en betaling in meerdere valuta</span><span class="sxs-lookup"><span data-stu-id="14f48-150">Multi-currency balance and payment</span></span>

<span data-ttu-id="14f48-151">Zie [factuur overzichten ophalen](get-invoice-summaries.md)voor een overzicht van uw huidige account saldo en een verzameling van factuur overzichten met een factuur samenvatting met zowel periodieke als eenmalige kosten voor elk van de valuta typen van uw klant.</span><span class="sxs-lookup"><span data-stu-id="14f48-151">To get your current account balance and a collection of invoice summaries containing an invoice summary with both recurring and one-time charges for each of your customer's currency types, see [Get invoice summaries](get-invoice-summaries.md).</span></span>

### <a name="invoices"></a><span data-ttu-id="14f48-152">Facturen</span><span class="sxs-lookup"><span data-stu-id="14f48-152">Invoices</span></span>

<span data-ttu-id="14f48-153">Zie [een verzameling facturen ophalen](get-a-collection-of-invoices.md)voor een verzameling facturen waarin zowel terugkerende als eenmalige kosten worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="14f48-153">To get a collection of invoices that show both recurring and one-time charges, see [Get a collection of invoices](get-a-collection-of-invoices.md).</span></span> 

### <a name="single-invoice"></a><span data-ttu-id="14f48-154">Eén factuur</span><span class="sxs-lookup"><span data-stu-id="14f48-154">Single Invoice</span></span>

<span data-ttu-id="14f48-155">Als u een specifieke factuur wilt ophalen met behulp van de factuur-ID, raadpleegt u [een factuur op id ophalen](get-invoice-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="14f48-155">To retrieve a specific invoice using the invoice ID, see [Get an invoice by ID](get-invoice-by-id.md).</span></span>  

### <a name="reconciliation"></a><span data-ttu-id="14f48-156">Afstemming</span><span class="sxs-lookup"><span data-stu-id="14f48-156">Reconciliation</span></span>

<span data-ttu-id="14f48-157">Zie [factuur regel items ophalen](get-invoiceline-items.md)voor een verzameling van gegevens over het factuur regel item (reconciliatie regel items) voor een specifieke factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="14f48-157">To get a collection of invoice line item details (Reconciliation line items) for a specific invoice ID, see [Get invoice line items](get-invoiceline-items.md).</span></span>  

### <a name="download-an-invoice-as-a-pdf"></a><span data-ttu-id="14f48-158">Een factuur als PDF-bestand downloaden</span><span class="sxs-lookup"><span data-stu-id="14f48-158">Download an invoice as a PDF</span></span>

<span data-ttu-id="14f48-159">Zie [een factuur overzicht ophalen](get-invoice-statement.md)als u een factuur overzicht wilt ophalen in een PDF-formulier met een factuur-ID.</span><span class="sxs-lookup"><span data-stu-id="14f48-159">To retrieve an invoice statement in PDF form using an invoice ID, see [Get an invoice statement](get-invoice-statement.md).</span></span>
