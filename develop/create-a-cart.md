---
title: Een winkelwagen maken
description: Meer informatie over het gebruik van partner Center-Api's voor het toevoegen van een bestelling voor een klant in een winkel wagen. Onderwerp bevat informatie over het maken van een winkel wagen en eventuele vereisten.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: a1c559b415a7d42af4e904e09795f92aed7f125f
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767637"
---
# <a name="create-a-cart-with-a-customer-order"></a><span data-ttu-id="3b3c1-104">Een winkel wagen maken met een klant order</span><span class="sxs-lookup"><span data-stu-id="3b3c1-104">Create a cart with a customer order</span></span>

<span data-ttu-id="3b3c1-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="3b3c1-105">**Applies to:**</span></span>

- <span data-ttu-id="3b3c1-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="3b3c1-106">Partner Center</span></span>
- <span data-ttu-id="3b3c1-107">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="3b3c1-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="3b3c1-108">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="3b3c1-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="3b3c1-109">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="3b3c1-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="3b3c1-110">U kunt een bestelling voor een klant in een winkel wagen toevoegen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-110">You can add an order for a customer in a cart.</span></span> <span data-ttu-id="3b3c1-111">Zie [partner aanbiedingen in het Cloud Solution Provider-programma](/partner-center/csp-offers)voor meer informatie over wat momenteel beschikbaar is om te verkopen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-111">For more information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="3b3c1-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="3b3c1-112">Prerequisites</span></span>

- <span data-ttu-id="3b3c1-113">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="3b3c1-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="3b3c1-114">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-114">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="3b3c1-115">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3b3c1-115">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="3b3c1-116">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-116">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="3b3c1-117">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-117">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="3b3c1-118">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-118">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="3b3c1-119">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="3b3c1-119">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="3b3c1-120">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="3b3c1-120">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="3b3c1-121">C\#</span><span class="sxs-lookup"><span data-stu-id="3b3c1-121">C\#</span></span>

<span data-ttu-id="3b3c1-122">Voor het maken van een bestelling voor een klant:</span><span class="sxs-lookup"><span data-stu-id="3b3c1-122">To create an order for a customer:</span></span>

1. <span data-ttu-id="3b3c1-123">Een object voor een winkel wagen instantiëren.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-123">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="3b3c1-124">Maak een lijst met **CartLineItem** -objecten en wijs de lijst toe aan de eigenschap regel items van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-124">Create a list of **CartLineItem** objects, and assign the list to the cart's LineItems property.</span></span> <span data-ttu-id="3b3c1-125">Elk winkelwagen regel item bevat de aankoop gegevens voor één product.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-125">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="3b3c1-126">U moet ten minste één winkelwagen regel item hebben.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-126">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="3b3c1-127">Verkrijg een interface voor winkelwagen bewerkingen door de **IAggregatePartner. Customs. ById** -methode aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de eigenschap **winkel wagen** .</span><span class="sxs-lookup"><span data-stu-id="3b3c1-127">Obtain an interface to cart operations by calling the **IAggregatePartner.Customers.ById** method with the customer ID to identify the customer, and then retrieving the interface from the **Cart** property.</span></span>

4. <span data-ttu-id="3b3c1-128">Roep de methode **Create** of **CreateAsync** aan om de winkel wagen te maken.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-128">Call the **Create** or **CreateAsync** method to create the cart.</span></span>

### <a name="c-example"></a><span data-ttu-id="3b3c1-129">C- \# voor beeld</span><span class="sxs-lookup"><span data-stu-id="3b3c1-129">C\# example</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

var cart = new Cart()
{
    LineItems = new List<CartLineItem>()
    {
        new CartLineItem()
        {
      /* Microsoft Azure Subscription */
            Id = 0,
            CatalogItemId = "MS-AZR-0145P",
            Quantity = 1,
            BillingCycle = BillingCycleType.Monthly,
            TermDuration = "P1Y"
        },
        new CartLineItem()
        {
      /* Azure Reserved Instance */
            Id = 1,
            CatalogItemId = "DZH318Z0BQ36:004G:DZH318Z08C0S",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime,
            TermDuration = "P1Y",
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", subscriptionId },
                { "scope", "shared" }
            }
        },
        new CartLineItem()
        {
      /* Azure Reserved Instance */
            Id = 2,
            CatalogItemId = "DZH318Z0BQ36:004J:DZH318Z08B8X",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime,
            TermDuration = "P3Y",
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", subscriptionId },
                { "scope", "shared" }
            }
        },
        new CartLineItem()
        {
      /* Perpetual Software */
            Id = 3,
            CatalogItemId = "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
            Quantity = 1,
            BillingCycle = BillingCycleType.OneTime
        },
        new CartLineItem()
        {
      /* SaaS */
            Id = 4,
            CatalogItemId = "DZH318Z0BXWC:0002:DZH318Z0BMRV",
            Quantity = 1,
            BillingCycle = BillingCycleType.Monthly,
            TermDuration = "P1M"
        },
        new CartLineItem()
        {
      /* SaaS Free Trial */
            Id = 5,
            CatalogItemId = "DZH318Z0C0WF:0001:DZH318Z0BP69",
            Quantity = 10,
            BillingCycle = BillingCycleType.None,
            TermDuration = "P1M",
            RenewsTo = new RenewsTo
            {
                TermDuration = "P1Y"
            }
        }
    }
};

cart = partnerOperations.Customers.ById(customerId).Carts.Create(cart);
```

## <a name="java"></a><span data-ttu-id="3b3c1-130">Java</span><span class="sxs-lookup"><span data-stu-id="3b3c1-130">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="3b3c1-131">Voor het maken van een bestelling voor een klant:</span><span class="sxs-lookup"><span data-stu-id="3b3c1-131">To create an order for a customer:</span></span>

1. <span data-ttu-id="3b3c1-132">Een object voor een winkel wagen instantiëren.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-132">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="3b3c1-133">Maak een lijst met **CartLineItem** -objecten en wijs de lijst toe aan de regel items van de wagen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-133">Create a list of **CartLineItem** objects, and assign the list to the cart's line items.</span></span> <span data-ttu-id="3b3c1-134">Elk winkelwagen regel item bevat de aankoop gegevens voor één product.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-134">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="3b3c1-135">U moet ten minste één winkelwagen regel item hebben.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-135">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="3b3c1-136">Verkrijg een interface voor winkelwagen bewerkingen door de functie **IAggregatePartner. getCustomers (). byId** aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de functie **getCart** .</span><span class="sxs-lookup"><span data-stu-id="3b3c1-136">Obtain an interface to cart operations by calling the **IAggregatePartner.getCustomers().byId** function with the customer ID to identify the customer, and then retrieving the interface from the **getCart** function.</span></span>

4. <span data-ttu-id="3b3c1-137">Roep de functie **Create** aan om de winkel wagen te maken.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-137">Call the **create** function to create the cart.</span></span>

## <a name="java-example"></a><span data-ttu-id="3b3c1-138">Java-voor beeld</span><span class="sxs-lookup"><span data-stu-id="3b3c1-138">Java example</span></span>

```java
// IAggregatePartner partnerOperations;
// String customerId;
// String subscriptionId;
// String catalogItemId;

CartLineItem lineItem = new CartLineItem();

lineItem.setBillingCycle(BillingCycleType.OneTime);
lineItem.setCatalogItemId(catalogItemId);
lineItem.setFriendlyName("Sample RI Purchase");
lineItem.setQuantity(1);

Map<String, String> provisioningContext = new HashMap<String,String>();

provisioningContext.put("duration", "3Years");
provisioningContext.put("scope", "shared");
provisioningContext.put("subscriptionId", subscriptionId);

lineItem.setProvisioningContext(provisioningContext);

List<CartLineItem> lineItemList = new ArrayList<CartLineItem>();
lineItemList.add(lineItem);

Cart cart = new Cart();
cart.setLineItems(lineItemList);

Cart cartCreated = partnerOperations.getCustomers().byId(customerId).getCarts().create(cart);
```

## <a name="powershell"></a><span data-ttu-id="3b3c1-139">PowerShell</span><span class="sxs-lookup"><span data-stu-id="3b3c1-139">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="3b3c1-140">Voor het maken van een bestelling voor een klant:</span><span class="sxs-lookup"><span data-stu-id="3b3c1-140">To create an order for a customer:</span></span>

1. <span data-ttu-id="3b3c1-141">Een object voor een winkel wagen instantiëren.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-141">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="3b3c1-142">Maak een lijst met **CartLineItem** -objecten en wijs de lijst toe aan de regel items van de wagen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-142">Create a list of **CartLineItem** objects, and assign the list to the cart's line items.</span></span> <span data-ttu-id="3b3c1-143">Elk winkelwagen regel item bevat de aankoop gegevens voor één product.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-143">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="3b3c1-144">U moet ten minste één winkelwagen regel item hebben.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-144">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="3b3c1-145">Voer de opdracht [**New-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) uit om de winkel wagen te maken.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-145">Execute the [**New-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) command to create the cart.</span></span>

```powershell
# $customerId
# $subscriptionId
# $catalogItemId

$lineItem = New-Object -TypeName Microsoft.Store.PartnerCenter.PowerShell.Models.Carts.PSCartLineItem

$lineItem.BillingCycle = 'OneTime'
$lineItem.CatalogItemId = $catalogItemId
$lineItem.FriendlyName = 'Sample RI Purchase'
$lineItem.ProvisioningContext.Add('duration', '1Year')
$lineItem.ProvisioningContext.Add('scope', 'shared')
$lineItem.ProvisioningContext.Add('subscriptionId', $subsciptionId)
$lineItem.Quantity = 10

New-PartnerCustomerCart -CustomerId $customerId -LineItems $lineItem
```

## <a name="rest-request"></a><span data-ttu-id="3b3c1-146">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="3b3c1-146">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="3b3c1-147">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3b3c1-147">Request syntax</span></span>

| <span data-ttu-id="3b3c1-148">Methode</span><span class="sxs-lookup"><span data-stu-id="3b3c1-148">Method</span></span>   | <span data-ttu-id="3b3c1-149">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="3b3c1-149">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3b3c1-150">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="3b3c1-150">**POST**</span></span> | <span data-ttu-id="3b3c1-151">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Carts http/1.1</span><span class="sxs-lookup"><span data-stu-id="3b3c1-151">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1</span></span>                        |

### <a name="uri-parameter"></a><span data-ttu-id="3b3c1-152">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="3b3c1-152">URI parameter</span></span>

<span data-ttu-id="3b3c1-153">Gebruik de volgende para meter voor het identificeren van de klant.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-153">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="3b3c1-154">Naam</span><span class="sxs-lookup"><span data-stu-id="3b3c1-154">Name</span></span>            | <span data-ttu-id="3b3c1-155">Type</span><span class="sxs-lookup"><span data-stu-id="3b3c1-155">Type</span></span>     | <span data-ttu-id="3b3c1-156">Vereist</span><span class="sxs-lookup"><span data-stu-id="3b3c1-156">Required</span></span> | <span data-ttu-id="3b3c1-157">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3b3c1-157">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="3b3c1-158">**klant-id**</span><span class="sxs-lookup"><span data-stu-id="3b3c1-158">**customer-id**</span></span> | <span data-ttu-id="3b3c1-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b3c1-159">string</span></span>   | <span data-ttu-id="3b3c1-160">Yes</span><span class="sxs-lookup"><span data-stu-id="3b3c1-160">Yes</span></span>      | <span data-ttu-id="3b3c1-161">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-161">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="3b3c1-162">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="3b3c1-162">Request headers</span></span>

<span data-ttu-id="3b3c1-163">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="3b3c1-163">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="3b3c1-164">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="3b3c1-164">Request body</span></span>

<span data-ttu-id="3b3c1-165">In deze tabel worden de eigenschappen van de [winkel wagen](cart-resources.md) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-165">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="3b3c1-166">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="3b3c1-166">Property</span></span>              | <span data-ttu-id="3b3c1-167">Type</span><span class="sxs-lookup"><span data-stu-id="3b3c1-167">Type</span></span>             | <span data-ttu-id="3b3c1-168">Vereist</span><span class="sxs-lookup"><span data-stu-id="3b3c1-168">Required</span></span>        | <span data-ttu-id="3b3c1-169">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3b3c1-169">Description</span></span> |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3b3c1-170">id</span><span class="sxs-lookup"><span data-stu-id="3b3c1-170">id</span></span>                    | <span data-ttu-id="3b3c1-171">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b3c1-171">string</span></span>           | <span data-ttu-id="3b3c1-172">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-172">No</span></span>              | <span data-ttu-id="3b3c1-173">Een winkel wagen-id die is opgegeven bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-173">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="3b3c1-174">creationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="3b3c1-174">creationTimeStamp</span></span>     | <span data-ttu-id="3b3c1-175">DateTime</span><span class="sxs-lookup"><span data-stu-id="3b3c1-175">DateTime</span></span>         | <span data-ttu-id="3b3c1-176">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-176">No</span></span>              | <span data-ttu-id="3b3c1-177">De datum waarop de winkel wagen is gemaakt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-177">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="3b3c1-178">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-178">Applied upon successful creation of the cart.</span></span>         |
| <span data-ttu-id="3b3c1-179">lastModifiedTimeStamp</span><span class="sxs-lookup"><span data-stu-id="3b3c1-179">lastModifiedTimeStamp</span></span> | <span data-ttu-id="3b3c1-180">DateTime</span><span class="sxs-lookup"><span data-stu-id="3b3c1-180">DateTime</span></span>         | <span data-ttu-id="3b3c1-181">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-181">No</span></span>              | <span data-ttu-id="3b3c1-182">De datum waarop de winkel wagen voor het laatst is bijgewerkt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-182">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="3b3c1-183">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-183">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="3b3c1-184">expirationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="3b3c1-184">expirationTimeStamp</span></span>   | <span data-ttu-id="3b3c1-185">DateTime</span><span class="sxs-lookup"><span data-stu-id="3b3c1-185">DateTime</span></span>         | <span data-ttu-id="3b3c1-186">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-186">No</span></span>              | <span data-ttu-id="3b3c1-187">De datum waarop de winkel wagen verloopt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-187">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="3b3c1-188">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-188">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="3b3c1-189">lastModifiedUser</span><span class="sxs-lookup"><span data-stu-id="3b3c1-189">lastModifiedUser</span></span>      | <span data-ttu-id="3b3c1-190">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b3c1-190">string</span></span>           | <span data-ttu-id="3b3c1-191">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-191">No</span></span>              | <span data-ttu-id="3b3c1-192">De gebruiker die de winkel wagen het laatst heeft bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-192">The user who last updated the cart.</span></span> <span data-ttu-id="3b3c1-193">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-193">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="3b3c1-194">Regel items</span><span class="sxs-lookup"><span data-stu-id="3b3c1-194">lineItems</span></span>             | <span data-ttu-id="3b3c1-195">Matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="3b3c1-195">Array of objects</span></span> | <span data-ttu-id="3b3c1-196">Yes</span><span class="sxs-lookup"><span data-stu-id="3b3c1-196">Yes</span></span>             | <span data-ttu-id="3b3c1-197">Een matrix met [CartLineItem](cart-resources.md#cartlineitem) -resources.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-197">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                     |

<span data-ttu-id="3b3c1-198">In deze tabel worden de eigenschappen van [CartLineItem](cart-resources.md#cartlineitem) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-198">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

|      <span data-ttu-id="3b3c1-199">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="3b3c1-199">Property</span></span>       |            <span data-ttu-id="3b3c1-200">Type</span><span class="sxs-lookup"><span data-stu-id="3b3c1-200">Type</span></span>             | <span data-ttu-id="3b3c1-201">Vereist</span><span class="sxs-lookup"><span data-stu-id="3b3c1-201">Required</span></span> |                                                                                         <span data-ttu-id="3b3c1-202">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3b3c1-202">Description</span></span>                                                                                         |
|---------------------|-----------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         <span data-ttu-id="3b3c1-203">id</span><span class="sxs-lookup"><span data-stu-id="3b3c1-203">id</span></span>          |           <span data-ttu-id="3b3c1-204">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b3c1-204">string</span></span>            |    <span data-ttu-id="3b3c1-205">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-205">No</span></span>    |                                                     <span data-ttu-id="3b3c1-206">Een unieke id voor een winkelwagen regel item.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-206">A Unique identifier for a cart line item.</span></span> <span data-ttu-id="3b3c1-207">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-207">Applied upon successful creation of cart.</span></span>                                                     |
|      <span data-ttu-id="3b3c1-208">catalogId</span><span class="sxs-lookup"><span data-stu-id="3b3c1-208">catalogId</span></span>      |           <span data-ttu-id="3b3c1-209">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b3c1-209">string</span></span>            |   <span data-ttu-id="3b3c1-210">Yes</span><span class="sxs-lookup"><span data-stu-id="3b3c1-210">Yes</span></span>    |                                                                                <span data-ttu-id="3b3c1-211">De id van het catalogus item.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-211">The catalog item identifier.</span></span>                                                                                 |
|    <span data-ttu-id="3b3c1-212">friendlyName</span><span class="sxs-lookup"><span data-stu-id="3b3c1-212">friendlyName</span></span>     |           <span data-ttu-id="3b3c1-213">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b3c1-213">string</span></span>            |    <span data-ttu-id="3b3c1-214">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-214">No</span></span>    |                                                    <span data-ttu-id="3b3c1-215">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-215">Optional.</span></span> <span data-ttu-id="3b3c1-216">De beschrijvende naam voor het item dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-216">The friendly name for the item defined by the partner to help disambiguate.</span></span>                                                    |
|      <span data-ttu-id="3b3c1-217">quantity</span><span class="sxs-lookup"><span data-stu-id="3b3c1-217">quantity</span></span>       |             <span data-ttu-id="3b3c1-218">int</span><span class="sxs-lookup"><span data-stu-id="3b3c1-218">int</span></span>             |   <span data-ttu-id="3b3c1-219">Ja</span><span class="sxs-lookup"><span data-stu-id="3b3c1-219">Yes</span></span>    |                                                                            <span data-ttu-id="3b3c1-220">Het aantal licenties of exemplaren.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-220">The number of licenses or instances.</span></span>                                                                             |
|    <span data-ttu-id="3b3c1-221">currencyCode</span><span class="sxs-lookup"><span data-stu-id="3b3c1-221">currencyCode</span></span>     |           <span data-ttu-id="3b3c1-222">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b3c1-222">string</span></span>            |    <span data-ttu-id="3b3c1-223">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-223">No</span></span>    |                                                                                     <span data-ttu-id="3b3c1-224">De valuta code.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-224">The currency code.</span></span>                                                                                      |
|    <span data-ttu-id="3b3c1-225">billingCycle</span><span class="sxs-lookup"><span data-stu-id="3b3c1-225">billingCycle</span></span>     |           <span data-ttu-id="3b3c1-226">Object</span><span class="sxs-lookup"><span data-stu-id="3b3c1-226">Object</span></span>            |   <span data-ttu-id="3b3c1-227">Ja</span><span class="sxs-lookup"><span data-stu-id="3b3c1-227">Yes</span></span>    |                                                                    <span data-ttu-id="3b3c1-228">Het type facturerings cyclus dat voor de huidige periode is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-228">The type of billing cycle set for the current period.</span></span>                                                                    |
|    <span data-ttu-id="3b3c1-229">deelnemers</span><span class="sxs-lookup"><span data-stu-id="3b3c1-229">participants</span></span>     | <span data-ttu-id="3b3c1-230">Lijst met object teken reeks paren</span><span class="sxs-lookup"><span data-stu-id="3b3c1-230">List of Object String pairs</span></span> |    <span data-ttu-id="3b3c1-231">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-231">No</span></span>    |                                                                <span data-ttu-id="3b3c1-232">Een verzameling partner on record (MPNID) voor de aankoop.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-232">A collection of PartnerId on Record (MPNID) on the purchase.</span></span>                                                                 |
| <span data-ttu-id="3b3c1-233">provisioningContext</span><span class="sxs-lookup"><span data-stu-id="3b3c1-233">provisioningContext</span></span> | <span data-ttu-id="3b3c1-234">Dictionary<teken reeks, teken reeks></span><span class="sxs-lookup"><span data-stu-id="3b3c1-234">Dictionary<string, string></span></span>  |    <span data-ttu-id="3b3c1-235">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-235">No</span></span>    | <span data-ttu-id="3b3c1-236">Informatie die is vereist voor het inrichten van sommige items in de catalogus.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-236">Information required for provisioning for some items in the catalog.</span></span> <span data-ttu-id="3b3c1-237">De eigenschap provisioningVariables in een SKU geeft aan welke eigenschappen vereist zijn voor specifieke items in de catalogus.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-237">The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog.</span></span> |
|     <span data-ttu-id="3b3c1-238">orderGroup</span><span class="sxs-lookup"><span data-stu-id="3b3c1-238">orderGroup</span></span>      |           <span data-ttu-id="3b3c1-239">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b3c1-239">string</span></span>            |    <span data-ttu-id="3b3c1-240">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-240">No</span></span>    |                                                                   <span data-ttu-id="3b3c1-241">Een groep om aan te geven welke items bij elkaar kunnen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-241">A group to indicate which items can be placed together.</span></span>                                                                   |
|        <span data-ttu-id="3b3c1-242">fout</span><span class="sxs-lookup"><span data-stu-id="3b3c1-242">error</span></span>        |           <span data-ttu-id="3b3c1-243">Object</span><span class="sxs-lookup"><span data-stu-id="3b3c1-243">Object</span></span>            |    <span data-ttu-id="3b3c1-244">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-244">No</span></span>    |                                                                     <span data-ttu-id="3b3c1-245">Wordt toegepast nadat de winkel wagen is gemaakt in het geval van een fout.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-245">Applied after cart is created in case of an error.</span></span>                                                                      |
|     <span data-ttu-id="3b3c1-246">renewsTo</span><span class="sxs-lookup"><span data-stu-id="3b3c1-246">renewsTo</span></span>        | <span data-ttu-id="3b3c1-247">Matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="3b3c1-247">Array of objects</span></span>            |    <span data-ttu-id="3b3c1-248">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-248">No</span></span>    |                                                    <span data-ttu-id="3b3c1-249">Een matrix met [RenewsTo](cart-resources.md#renewsto) -resources.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-249">An array of [RenewsTo](cart-resources.md#renewsto) resources.</span></span>                                                                            |

<span data-ttu-id="3b3c1-250">In deze tabel worden de eigenschappen van [RenewsTo](cart-resources.md#renewsto) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-250">This table describes the [RenewsTo](cart-resources.md#renewsto) properties in the request body.</span></span>

| <span data-ttu-id="3b3c1-251">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="3b3c1-251">Property</span></span>              | <span data-ttu-id="3b3c1-252">Type</span><span class="sxs-lookup"><span data-stu-id="3b3c1-252">Type</span></span>             | <span data-ttu-id="3b3c1-253">Vereist</span><span class="sxs-lookup"><span data-stu-id="3b3c1-253">Required</span></span>        | <span data-ttu-id="3b3c1-254">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="3b3c1-254">Description</span></span> |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="3b3c1-255">termDuration</span><span class="sxs-lookup"><span data-stu-id="3b3c1-255">termDuration</span></span>          | <span data-ttu-id="3b3c1-256">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="3b3c1-256">string</span></span>           | <span data-ttu-id="3b3c1-257">No</span><span class="sxs-lookup"><span data-stu-id="3b3c1-257">No</span></span>              | <span data-ttu-id="3b3c1-258">Een ISO 8601-representatie van de duur van de verlengings termijn.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-258">An ISO 8601 representation of the renewal term's duration.</span></span> <span data-ttu-id="3b3c1-259">De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar).</span><span class="sxs-lookup"><span data-stu-id="3b3c1-259">The current supported values are **P1M** (1 month) and **P1Y** (1 year).</span></span> |

### <a name="request-example"></a><span data-ttu-id="3b3c1-260">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="3b3c1-260">Request example</span></span>

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 496
Expect: 100-continue

{
  "lineItems": [
    {
    /* Microsoft Azure Subscription */
      "id": 0,
      "catalogItemId": "MS-AZR-0145P",
      "quantity": 1,
      "billingCycle": "monthly",
      "termDuration": "P1Y"
    },
    {
    /* Azure Reserved Instance */
      "id": 1,
      "catalogItemId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
      "quantity": 1,
      "billingCycle": "one_time",
      "termDuration": "P1Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      }
    },
    {
    /* Azure Reserved Instance */
      "id": 2,
      "catalogItemId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
      "quantity": 1,
      "billingCycle": "one_time",
      "termDuration": "P3Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "single"
      }
    },
    {
    /* Perpetual Software */
      "id": 3,
      "catalogItemId": "DG7GMGF0DWTL:0001:DG7GMGF0DSFM",
      "quantity": 1,
      "billingCycle": "one_time"
    },
    {
    /* SaaS */
      "id": 4,
      "catalogItemId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
      "quantity": 1,
      "billingCycle": "monthly",
      "termDuration": "P1M"
    },
  {
    /* SaaS Free Trial */
       "id": 5,
       "catalogItemId": "DZH318Z0C0WF:0001:DZH318Z0BP69",
       "quantity": 10,
       "billingCycle": "none",
       "termDuration": "P1M",
       "renewsTo": {
         "termDuration": "P1Y"
       }
    }
  ]
}
```

## <a name="rest-response"></a><span data-ttu-id="3b3c1-261">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="3b3c1-261">REST response</span></span>

<span data-ttu-id="3b3c1-262">Als dit lukt, retourneert deze methode de gevulde [Winkelwagen](cart-resources.md) resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-262">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="3b3c1-263">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="3b3c1-263">Response success and error codes</span></span>

<span data-ttu-id="3b3c1-264">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-264">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="3b3c1-265">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-265">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="3b3c1-266">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-266">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="3b3c1-267">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="3b3c1-267">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 764
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
X-Locale: en-US,en-US
MS-CV: sF/wRa2ih0CzbABc.0
MS-ServerId: 000001
Date: Thu, 15 Mar 2018 17:15:01 GMT
{
  "id": "3655b1a0-b1c9-4268-9824-577fdbc4d0be",
  "creationTimestamp": "2019-01-16T00:45:41.6062996Z",
  "lastModifiedTimestamp": "2019-01-16T00:45:41.6062996Z",
  "expirationTimestamp": "2019-01-16T01:00:54.4188497Z",
  "lastModifiedUser": "1824b7fc-2fac-4478-b177-66823c40ab75",
  "status": "Active",
  "lineItems": [
    {
      "id": 0,
      "catalogItemId": "MS-AZR-0145P",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "monthly",
      "termDuration": "P1Y",
      "orderGroup": "OMS-0"
    },
    {
      "id": 1,
      "catalogItemId": "DZH318Z0BQ36:004G:DZH318Z08C0S",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "termDuration": "P1Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      },
      "orderGroup": "0"
    },
    {
      "id": 2,
      "catalogItemId": "DZH318Z0BQ36:004J:DZH318Z08B8X",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "termDuration": "P3Y",
      "provisioningContext": {
        "subscriptionId": "1C461A25-F729-4FA5-AADB-280947DD05E8",
        "scope": "shared"
      },
      "orderGroup": "0"
    },
    {
      "id": 3,
      "catalogItemId": "DG7GMGF0DWM3:0002:DG7GMGF0DT1M",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "one_time",
      "orderGroup": "0"
    },
    {
      "id": 4,
      "catalogItemId": "DZH318Z0BXWC:0002:DZH318Z0BMRV",
      "quantity": 1,
      "currencyCode": "USD",
      "billingCycle": "monthly",
      "termDuration": "P1M",
      "orderGroup": "1"
    },
  {
      "id": 5,
      "catalogItemId": "DZH318Z0C0WF:0001:DZH318Z0BP69",
      "quantity": 10,
      "currencyCode": "USD",
      "billingCycle": "none",
      "termDuration": "P1M",
      "renewsTo": {
  "termDuration": "P1Y"
      },
    "orderGroup": "2"
    }
  ],
  "links": {
    "self": {
      "uri": "/customers/28045616-f6b9-462f-9701-0d89b5e65c44/carts/3655b1a0-b1c9-4268-9824-577fdbc4d0be",
      "method": "GET",
      "headers": []
    }
  },
  "attributes": {
    "objectType": "Cart"
  }
}
```
