---
title: Een winkelwagen maken
description: Meer informatie over het gebruik Partner Center API's om een order voor een klant in een winkelwagen toe te voegen. Onderwerp bevat informatie over het maken van een winkelwagen en eventuele vereisten.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: dba54d4f6b97f3d0a51e2f87b32edca686466b89
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973771"
---
# <a name="create-a-cart-with-a-customer-order"></a><span data-ttu-id="216e4-104">Een winkelwagen maken met een klantorder</span><span class="sxs-lookup"><span data-stu-id="216e4-104">Create a cart with a customer order</span></span>

<span data-ttu-id="216e4-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="216e4-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="216e4-106">U kunt een order voor een klant toevoegen in een winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="216e4-106">You can add an order for a customer in a cart.</span></span> <span data-ttu-id="216e4-107">Zie Partneraanbiedingen in het Cloud Solution Provider programma voor meer informatie over [wat momenteel beschikbaar is om Cloud Solution Provider verkopen.](/partner-center/csp-offers)</span><span class="sxs-lookup"><span data-stu-id="216e4-107">For more information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="216e4-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="216e4-108">Prerequisites</span></span>

- <span data-ttu-id="216e4-109">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="216e4-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="216e4-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="216e4-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="216e4-111">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="216e4-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="216e4-112">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="216e4-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="216e4-113">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="216e4-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="216e4-114">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="216e4-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="216e4-115">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="216e4-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="216e4-116">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="216e4-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="216e4-117">C\#</span><span class="sxs-lookup"><span data-stu-id="216e4-117">C\#</span></span>

<span data-ttu-id="216e4-118">Een order voor een klant maken:</span><span class="sxs-lookup"><span data-stu-id="216e4-118">To create an order for a customer:</span></span>

1. <span data-ttu-id="216e4-119">Een winkelwagenobject instanteren.</span><span class="sxs-lookup"><span data-stu-id="216e4-119">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="216e4-120">Maak een lijst met **CartLineItem-objecten** en wijs de lijst toe aan de eigenschap LineItems van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="216e4-120">Create a list of **CartLineItem** objects, and assign the list to the cart's LineItems property.</span></span> <span data-ttu-id="216e4-121">Elk winkelwagenregelitem bevat de aankoopgegevens voor één product.</span><span class="sxs-lookup"><span data-stu-id="216e4-121">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="216e4-122">U moet ten minste één winkelwagenregelitem hebben.</span><span class="sxs-lookup"><span data-stu-id="216e4-122">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="216e4-123">Verkrijg een interface voor winkelwagenbewerkingen door de methode **IAggregatePartner.Customers.ById** aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de eigenschap **Winkelwagen.**</span><span class="sxs-lookup"><span data-stu-id="216e4-123">Obtain an interface to cart operations by calling the **IAggregatePartner.Customers.ById** method with the customer ID to identify the customer, and then retrieving the interface from the **Cart** property.</span></span>

4. <span data-ttu-id="216e4-124">Roep de **methode Create** of **CreateAsync aan** om de winkelwagen te maken.</span><span class="sxs-lookup"><span data-stu-id="216e4-124">Call the **Create** or **CreateAsync** method to create the cart.</span></span>

### <a name="c-example"></a><span data-ttu-id="216e4-125">\#C-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="216e4-125">C\# example</span></span>

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

## <a name="java"></a><span data-ttu-id="216e4-126">Java</span><span class="sxs-lookup"><span data-stu-id="216e4-126">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="216e4-127">Een order voor een klant maken:</span><span class="sxs-lookup"><span data-stu-id="216e4-127">To create an order for a customer:</span></span>

1. <span data-ttu-id="216e4-128">Een winkelwagenobject instanteren.</span><span class="sxs-lookup"><span data-stu-id="216e4-128">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="216e4-129">Maak een lijst met **CartLineItem-objecten** en wijs de lijst toe aan de regelitems van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="216e4-129">Create a list of **CartLineItem** objects, and assign the list to the cart's line items.</span></span> <span data-ttu-id="216e4-130">Elk winkelwagenregelitem bevat de aankoopgegevens voor één product.</span><span class="sxs-lookup"><span data-stu-id="216e4-130">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="216e4-131">U moet ten minste één winkelwagenregelitem hebben.</span><span class="sxs-lookup"><span data-stu-id="216e4-131">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="216e4-132">Verkrijg een interface voor winkelwagenbewerkingen door de functie **IAggregatePartner.getCustomers().byId** aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de **functie getCart.**</span><span class="sxs-lookup"><span data-stu-id="216e4-132">Obtain an interface to cart operations by calling the **IAggregatePartner.getCustomers().byId** function with the customer ID to identify the customer, and then retrieving the interface from the **getCart** function.</span></span>

4. <span data-ttu-id="216e4-133">Roep de **functie create aan** om de winkelwagen te maken.</span><span class="sxs-lookup"><span data-stu-id="216e4-133">Call the **create** function to create the cart.</span></span>

## <a name="java-example"></a><span data-ttu-id="216e4-134">Java-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="216e4-134">Java example</span></span>

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

## <a name="powershell"></a><span data-ttu-id="216e4-135">PowerShell</span><span class="sxs-lookup"><span data-stu-id="216e4-135">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="216e4-136">Een order voor een klant maken:</span><span class="sxs-lookup"><span data-stu-id="216e4-136">To create an order for a customer:</span></span>

1. <span data-ttu-id="216e4-137">Een winkelwagenobject instanteren.</span><span class="sxs-lookup"><span data-stu-id="216e4-137">Instantiate a Cart object.</span></span>

2. <span data-ttu-id="216e4-138">Maak een lijst met **CartLineItem-objecten** en wijs de lijst toe aan de regelitems van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="216e4-138">Create a list of **CartLineItem** objects, and assign the list to the cart's line items.</span></span> <span data-ttu-id="216e4-139">Elk winkelwagenregelitem bevat de aankoopgegevens voor één product.</span><span class="sxs-lookup"><span data-stu-id="216e4-139">Each cart line item contains the purchase information for one product.</span></span> <span data-ttu-id="216e4-140">U moet ten minste één winkelwagenregelitem hebben.</span><span class="sxs-lookup"><span data-stu-id="216e4-140">You must have at least one cart line item.</span></span>

3. <span data-ttu-id="216e4-141">Voer de [**opdracht New-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) uit om de winkelwagen te maken.</span><span class="sxs-lookup"><span data-stu-id="216e4-141">Execute the [**New-PartnerCustomerCart**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomerCart.md) command to create the cart.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="216e4-142">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="216e4-142">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="216e4-143">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="216e4-143">Request syntax</span></span>

| <span data-ttu-id="216e4-144">Methode</span><span class="sxs-lookup"><span data-stu-id="216e4-144">Method</span></span>   | <span data-ttu-id="216e4-145">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="216e4-145">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="216e4-146">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="216e4-146">**POST**</span></span> | <span data-ttu-id="216e4-147">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="216e4-147">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1</span></span>                        |

### <a name="uri-parameter"></a><span data-ttu-id="216e4-148">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="216e4-148">URI parameter</span></span>

<span data-ttu-id="216e4-149">Gebruik de volgende padparameter om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="216e4-149">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="216e4-150">Naam</span><span class="sxs-lookup"><span data-stu-id="216e4-150">Name</span></span>            | <span data-ttu-id="216e4-151">Type</span><span class="sxs-lookup"><span data-stu-id="216e4-151">Type</span></span>     | <span data-ttu-id="216e4-152">Vereist</span><span class="sxs-lookup"><span data-stu-id="216e4-152">Required</span></span> | <span data-ttu-id="216e4-153">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="216e4-153">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="216e4-154">**customer-id**</span><span class="sxs-lookup"><span data-stu-id="216e4-154">**customer-id**</span></span> | <span data-ttu-id="216e4-155">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="216e4-155">string</span></span>   | <span data-ttu-id="216e4-156">Ja</span><span class="sxs-lookup"><span data-stu-id="216e4-156">Yes</span></span>      | <span data-ttu-id="216e4-157">Een met GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="216e4-157">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="216e4-158">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="216e4-158">Request headers</span></span>

<span data-ttu-id="216e4-159">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="216e4-159">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="216e4-160">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="216e4-160">Request body</span></span>

<span data-ttu-id="216e4-161">In deze tabel worden de eigenschappen [van de winkelwagen](cart-resources.md) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="216e4-161">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="216e4-162">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="216e4-162">Property</span></span>              | <span data-ttu-id="216e4-163">Type</span><span class="sxs-lookup"><span data-stu-id="216e4-163">Type</span></span>             | <span data-ttu-id="216e4-164">Vereist</span><span class="sxs-lookup"><span data-stu-id="216e4-164">Required</span></span>        | <span data-ttu-id="216e4-165">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="216e4-165">Description</span></span> |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="216e4-166">id</span><span class="sxs-lookup"><span data-stu-id="216e4-166">id</span></span>                    | <span data-ttu-id="216e4-167">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="216e4-167">string</span></span>           | <span data-ttu-id="216e4-168">No</span><span class="sxs-lookup"><span data-stu-id="216e4-168">No</span></span>              | <span data-ttu-id="216e4-169">Een winkelwagen-id die wordt opgegeven wanneer de winkelwagen is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="216e4-169">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="216e4-170">creationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="216e4-170">creationTimeStamp</span></span>     | <span data-ttu-id="216e4-171">DateTime</span><span class="sxs-lookup"><span data-stu-id="216e4-171">DateTime</span></span>         | <span data-ttu-id="216e4-172">Nee</span><span class="sxs-lookup"><span data-stu-id="216e4-172">No</span></span>              | <span data-ttu-id="216e4-173">De datum waarop de winkelwagen is gemaakt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="216e4-173">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="216e4-174">Toegepast wanneer de winkelwagen is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="216e4-174">Applied upon successful creation of the cart.</span></span>         |
| <span data-ttu-id="216e4-175">lastModifiedTimeStamp</span><span class="sxs-lookup"><span data-stu-id="216e4-175">lastModifiedTimeStamp</span></span> | <span data-ttu-id="216e4-176">DateTime</span><span class="sxs-lookup"><span data-stu-id="216e4-176">DateTime</span></span>         | <span data-ttu-id="216e4-177">Nee</span><span class="sxs-lookup"><span data-stu-id="216e4-177">No</span></span>              | <span data-ttu-id="216e4-178">De datum waarop de winkelwagen het laatst is bijgewerkt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="216e4-178">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="216e4-179">Toegepast wanneer de winkelwagen is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="216e4-179">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="216e4-180">expirationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="216e4-180">expirationTimeStamp</span></span>   | <span data-ttu-id="216e4-181">DateTime</span><span class="sxs-lookup"><span data-stu-id="216e4-181">DateTime</span></span>         | <span data-ttu-id="216e4-182">Nee</span><span class="sxs-lookup"><span data-stu-id="216e4-182">No</span></span>              | <span data-ttu-id="216e4-183">De datum waarop de winkelwagen verloopt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="216e4-183">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="216e4-184">Toegepast bij het maken van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="216e4-184">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="216e4-185">lastModifiedUser</span><span class="sxs-lookup"><span data-stu-id="216e4-185">lastModifiedUser</span></span>      | <span data-ttu-id="216e4-186">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="216e4-186">string</span></span>           | <span data-ttu-id="216e4-187">No</span><span class="sxs-lookup"><span data-stu-id="216e4-187">No</span></span>              | <span data-ttu-id="216e4-188">De gebruiker die de winkelwagen voor het laatst heeft bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="216e4-188">The user who last updated the cart.</span></span> <span data-ttu-id="216e4-189">Toegepast bij het maken van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="216e4-189">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="216e4-190">lineItems</span><span class="sxs-lookup"><span data-stu-id="216e4-190">lineItems</span></span>             | <span data-ttu-id="216e4-191">Matrix met objecten</span><span class="sxs-lookup"><span data-stu-id="216e4-191">Array of objects</span></span> | <span data-ttu-id="216e4-192">Ja</span><span class="sxs-lookup"><span data-stu-id="216e4-192">Yes</span></span>             | <span data-ttu-id="216e4-193">Een matrix van [CartLineItem-resources.](cart-resources.md#cartlineitem)</span><span class="sxs-lookup"><span data-stu-id="216e4-193">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                     |

<span data-ttu-id="216e4-194">In deze tabel worden de [eigenschappen van CartLineItem](cart-resources.md#cartlineitem) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="216e4-194">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

|      <span data-ttu-id="216e4-195">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="216e4-195">Property</span></span>       |            <span data-ttu-id="216e4-196">Type</span><span class="sxs-lookup"><span data-stu-id="216e4-196">Type</span></span>             | <span data-ttu-id="216e4-197">Vereist</span><span class="sxs-lookup"><span data-stu-id="216e4-197">Required</span></span> |                                                                                         <span data-ttu-id="216e4-198">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="216e4-198">Description</span></span>                                                                                         |
|---------------------|-----------------------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|         <span data-ttu-id="216e4-199">id</span><span class="sxs-lookup"><span data-stu-id="216e4-199">id</span></span>          |           <span data-ttu-id="216e4-200">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="216e4-200">string</span></span>            |    <span data-ttu-id="216e4-201">No</span><span class="sxs-lookup"><span data-stu-id="216e4-201">No</span></span>    |                                                     <span data-ttu-id="216e4-202">Een unieke id voor een winkelwagenregelitem.</span><span class="sxs-lookup"><span data-stu-id="216e4-202">A unique identifier for a cart line item.</span></span> <span data-ttu-id="216e4-203">Toegepast nadat de winkelwagen is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="216e4-203">Applied upon successful creation of cart.</span></span>                                                     |
|      <span data-ttu-id="216e4-204">catalogId</span><span class="sxs-lookup"><span data-stu-id="216e4-204">catalogId</span></span>      |           <span data-ttu-id="216e4-205">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="216e4-205">string</span></span>            |   <span data-ttu-id="216e4-206">Ja</span><span class="sxs-lookup"><span data-stu-id="216e4-206">Yes</span></span>    |                                                                                <span data-ttu-id="216e4-207">De id van het catalogusitem.</span><span class="sxs-lookup"><span data-stu-id="216e4-207">The catalog item identifier.</span></span>                                                                                 |
|    <span data-ttu-id="216e4-208">Friendlyname</span><span class="sxs-lookup"><span data-stu-id="216e4-208">friendlyName</span></span>     |           <span data-ttu-id="216e4-209">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="216e4-209">string</span></span>            |    <span data-ttu-id="216e4-210">No</span><span class="sxs-lookup"><span data-stu-id="216e4-210">No</span></span>    |                                                    <span data-ttu-id="216e4-211">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="216e4-211">Optional.</span></span> <span data-ttu-id="216e4-212">De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.</span><span class="sxs-lookup"><span data-stu-id="216e4-212">The friendly name for the item defined by the partner to help disambiguate.</span></span>                                                    |
|      <span data-ttu-id="216e4-213">quantity</span><span class="sxs-lookup"><span data-stu-id="216e4-213">quantity</span></span>       |             <span data-ttu-id="216e4-214">int</span><span class="sxs-lookup"><span data-stu-id="216e4-214">int</span></span>             |   <span data-ttu-id="216e4-215">Ja</span><span class="sxs-lookup"><span data-stu-id="216e4-215">Yes</span></span>    |                                                                            <span data-ttu-id="216e4-216">Het aantal licenties of exemplaren.</span><span class="sxs-lookup"><span data-stu-id="216e4-216">The number of licenses or instances.</span></span>                                                                             |
|    <span data-ttu-id="216e4-217">currencyCode</span><span class="sxs-lookup"><span data-stu-id="216e4-217">currencyCode</span></span>     |           <span data-ttu-id="216e4-218">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="216e4-218">string</span></span>            |    <span data-ttu-id="216e4-219">No</span><span class="sxs-lookup"><span data-stu-id="216e4-219">No</span></span>    |                                                                                     <span data-ttu-id="216e4-220">De valutacode.</span><span class="sxs-lookup"><span data-stu-id="216e4-220">The currency code.</span></span>                                                                                      |
|    <span data-ttu-id="216e4-221">billingCycle</span><span class="sxs-lookup"><span data-stu-id="216e4-221">billingCycle</span></span>     |           <span data-ttu-id="216e4-222">Object</span><span class="sxs-lookup"><span data-stu-id="216e4-222">Object</span></span>            |   <span data-ttu-id="216e4-223">Ja</span><span class="sxs-lookup"><span data-stu-id="216e4-223">Yes</span></span>    |                                                                    <span data-ttu-id="216e4-224">Het type factureringscyclus dat is ingesteld voor de huidige periode.</span><span class="sxs-lookup"><span data-stu-id="216e4-224">The type of billing cycle set for the current period.</span></span>                                                                    |
|    <span data-ttu-id="216e4-225">deelnemers</span><span class="sxs-lookup"><span data-stu-id="216e4-225">participants</span></span>     | <span data-ttu-id="216e4-226">Lijst met objectreeksparen</span><span class="sxs-lookup"><span data-stu-id="216e4-226">List of Object String pairs</span></span> |    <span data-ttu-id="216e4-227">Nee</span><span class="sxs-lookup"><span data-stu-id="216e4-227">No</span></span>    |                                                                <span data-ttu-id="216e4-228">Een verzameling PartnerId on Record (MPNID) voor de aankoop.</span><span class="sxs-lookup"><span data-stu-id="216e4-228">A collection of PartnerId on Record (MPNID) on the purchase.</span></span>                                                                 |
| <span data-ttu-id="216e4-229">provisioningContext</span><span class="sxs-lookup"><span data-stu-id="216e4-229">provisioningContext</span></span> | <span data-ttu-id="216e4-230">Woordenlijst<tekenreeks, tekenreeks></span><span class="sxs-lookup"><span data-stu-id="216e4-230">Dictionary<string, string></span></span>  |    <span data-ttu-id="216e4-231">Nee</span><span class="sxs-lookup"><span data-stu-id="216e4-231">No</span></span>    | <span data-ttu-id="216e4-232">Informatie die vereist is voor het inrichten van sommige items in de catalogus.</span><span class="sxs-lookup"><span data-stu-id="216e4-232">Information required for provisioning for some items in the catalog.</span></span> <span data-ttu-id="216e4-233">De eigenschap provisioningVariables in een SKU geeft aan welke eigenschappen vereist zijn voor specifieke items in de catalogus.</span><span class="sxs-lookup"><span data-stu-id="216e4-233">The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog.</span></span> |
|     <span data-ttu-id="216e4-234">orderGroup</span><span class="sxs-lookup"><span data-stu-id="216e4-234">orderGroup</span></span>      |           <span data-ttu-id="216e4-235">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="216e4-235">string</span></span>            |    <span data-ttu-id="216e4-236">No</span><span class="sxs-lookup"><span data-stu-id="216e4-236">No</span></span>    |                                                                   <span data-ttu-id="216e4-237">Een groep om aan te geven welke items samen kunnen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="216e4-237">A group to indicate which items can be placed together.</span></span>                                                                   |
|        <span data-ttu-id="216e4-238">fout</span><span class="sxs-lookup"><span data-stu-id="216e4-238">error</span></span>        |           <span data-ttu-id="216e4-239">Object</span><span class="sxs-lookup"><span data-stu-id="216e4-239">Object</span></span>            |    <span data-ttu-id="216e4-240">Nee</span><span class="sxs-lookup"><span data-stu-id="216e4-240">No</span></span>    |                                                                     <span data-ttu-id="216e4-241">Toegepast nadat de winkelwagen is gemaakt als er een fout is opgetreden.</span><span class="sxs-lookup"><span data-stu-id="216e4-241">Applied after cart is created if there is an error.</span></span>                                                                      |
|     <span data-ttu-id="216e4-242">renewsTo</span><span class="sxs-lookup"><span data-stu-id="216e4-242">renewsTo</span></span>        | <span data-ttu-id="216e4-243">Matrix met objecten</span><span class="sxs-lookup"><span data-stu-id="216e4-243">Array of objects</span></span>            |    <span data-ttu-id="216e4-244">Nee</span><span class="sxs-lookup"><span data-stu-id="216e4-244">No</span></span>    |                                                    <span data-ttu-id="216e4-245">Een matrix van [RenewsTo-resources.](cart-resources.md#renewsto)</span><span class="sxs-lookup"><span data-stu-id="216e4-245">An array of [RenewsTo](cart-resources.md#renewsto) resources.</span></span>                                                                            |

<span data-ttu-id="216e4-246">In deze tabel worden de [RenewsTo-eigenschappen](cart-resources.md#renewsto) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="216e4-246">This table describes the [RenewsTo](cart-resources.md#renewsto) properties in the request body.</span></span>

| <span data-ttu-id="216e4-247">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="216e4-247">Property</span></span>              | <span data-ttu-id="216e4-248">Type</span><span class="sxs-lookup"><span data-stu-id="216e4-248">Type</span></span>             | <span data-ttu-id="216e4-249">Vereist</span><span class="sxs-lookup"><span data-stu-id="216e4-249">Required</span></span>        | <span data-ttu-id="216e4-250">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="216e4-250">Description</span></span> |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="216e4-251">termDuration</span><span class="sxs-lookup"><span data-stu-id="216e4-251">termDuration</span></span>          | <span data-ttu-id="216e4-252">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="216e4-252">string</span></span>           | <span data-ttu-id="216e4-253">No</span><span class="sxs-lookup"><span data-stu-id="216e4-253">No</span></span>              | <span data-ttu-id="216e4-254">Een ISO 8601-weergave van de duur van de verlengingstermijn.</span><span class="sxs-lookup"><span data-stu-id="216e4-254">An ISO 8601 representation of the renewal term's duration.</span></span> <span data-ttu-id="216e4-255">De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar).</span><span class="sxs-lookup"><span data-stu-id="216e4-255">The current supported values are **P1M** (1 month) and **P1Y** (1 year).</span></span> |

### <a name="request-example"></a><span data-ttu-id="216e4-256">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="216e4-256">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="216e4-257">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="216e4-257">REST response</span></span>

<span data-ttu-id="216e4-258">Als dit lukt, retourneert deze methode de ingevulde [winkelwagenresource](cart-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="216e4-258">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="216e4-259">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="216e4-259">Response success and error codes</span></span>

<span data-ttu-id="216e4-260">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="216e4-260">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="216e4-261">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="216e4-261">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="216e4-262">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="216e4-262">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="216e4-263">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="216e4-263">Response example</span></span>

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
