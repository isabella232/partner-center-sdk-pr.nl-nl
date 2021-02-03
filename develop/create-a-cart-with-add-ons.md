---
title: Een winkelwagen maken met invoegtoepassingen
description: Meer informatie over het gebruik van partner Center-Api's voor het toevoegen van een klant order met invoeg toepassingen via een winkel wagen. Artikel deelt vereisten en stappen voor het maken van een winkel wagen met invoeg toepassingen.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 81c41405a2f56eb4d1d3447d14b93e05d550cc70
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767638"
---
# <a name="create-a-cart-with-add-ons-to-a-customer-order"></a><span data-ttu-id="43990-104">Een winkel wagen maken met invoeg toepassingen voor een klant order</span><span class="sxs-lookup"><span data-stu-id="43990-104">Create a cart with add-ons to a customer order</span></span>

<span data-ttu-id="43990-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="43990-105">**Applies to:**</span></span>

- <span data-ttu-id="43990-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="43990-106">Partner Center</span></span>

<span data-ttu-id="43990-107">U kunt invoeg toepassingen kopen via een winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="43990-107">You can purchase add-ons through a cart.</span></span> <span data-ttu-id="43990-108">Zie [partner aanbiedingen in het Cloud Solution Provider-programma](/partner-center/csp-offers)voor meer informatie over wat momenteel beschikbaar is om te verkopen.</span><span class="sxs-lookup"><span data-stu-id="43990-108">For more information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="43990-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="43990-109">Prerequisites</span></span>

- <span data-ttu-id="43990-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="43990-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="43990-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="43990-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="43990-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="43990-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="43990-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="43990-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="43990-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="43990-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="43990-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="43990-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="43990-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="43990-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="43990-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="43990-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="43990-118">C\#</span><span class="sxs-lookup"><span data-stu-id="43990-118">C\#</span></span>

<span data-ttu-id="43990-119">Een winkel wagen maakt het mogelijk om een basis aanbod en de bijbehorende invoeg toepassingen aan te schaffen.</span><span class="sxs-lookup"><span data-stu-id="43990-119">A cart enables the purchase of a base offer and its corresponding add-ons.</span></span> <span data-ttu-id="43990-120">Volg deze stappen om een winkel wagen te maken:</span><span class="sxs-lookup"><span data-stu-id="43990-120">Follow these steps to create a cart:</span></span>

1. <span data-ttu-id="43990-121">Een object voor een [**winkel wagen**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart) instantiëren.</span><span class="sxs-lookup"><span data-stu-id="43990-121">Instantiate a [**Cart**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart) object.</span></span>

2. <span data-ttu-id="43990-122">Maak een lijst met [**CartLineItem**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) -objecten die de basis aanbod (en) vertegenwoordigen, en wijs de lijst toe aan de eigenschap [**regel items**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="43990-122">Create a list of [**CartLineItem**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) objects which represent the base offer(s), and assign the list to the cart's [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) property.</span></span>

3. <span data-ttu-id="43990-123">Vul onder elke basis lijn van de winkel wagen de lijst met **AddOnItems** in met andere **CartLineItem** -objecten die elk een invoeg toepassing vertegenwoordigen die wordt aangeschaft voor die basis aanbieding.</span><span class="sxs-lookup"><span data-stu-id="43990-123">Under each base offer's cart line item, populate the list of **AddOnItems** with other **CartLineItem** objects that each represent an add-on that will be purchased against that base offer.</span></span>

4. <span data-ttu-id="43990-124">Verkrijg een interface voor winkelwagen bewerkingen door gebruik te maken van [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) om de [**ICustomerCollection. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de eigenschap **winkel wagen** .</span><span class="sxs-lookup"><span data-stu-id="43990-124">Obtain an interface to cart operations by using [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) to call the [**ICustomerCollection.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and then retrieving the interface from the **Cart** property.</span></span>

5. <span data-ttu-id="43990-125">Roep tot slot de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) aan om de winkel wagen te maken.</span><span class="sxs-lookup"><span data-stu-id="43990-125">Finally, call the [**Create**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) method to create the cart.</span></span>

### <a name="c-example"></a><span data-ttu-id="43990-126">C- \# voor beeld</span><span class="sxs-lookup"><span data-stu-id="43990-126">C\# example</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string customerId;

var cart = new Cart()
    {
        LineItems = new List<CartLineItem>()
        {
            new CartLineItem()
            {
                Id = 0,
                CatalogItemId = "A_base_offer_ID",
                FriendlyName = "Myofferpurchase",
                Quantity = 3,
                BillingCycle = BillingCycleType.Monthly,
                AddonItems = new List<CartLineItem>
                {
                    new CartLineItem
                    {
                        Id = 1,
                        CatalogItemId = "An_addon_item_ID",
                        BillingCycle = BillingCycleType.Monthly,
                        Quantity = 2,
                    },
                    new CartLineItem
                    {
                        Id = 2,
                        CatalogItemId = "Another_addon_item_ID",
                        BillingCycle = BillingCycleType.Monthly,
                        Quantity = 3
                    }
                }
            }
        }
    };

var createdCart = partnerOperations.Customers.ById(customerId).Carts.Create(cart);
```

<span data-ttu-id="43990-127">Volg deze stappen voor het maken van een winkel wagen waarmee de aankoop van invoeg toepassingen voor bestaande basis abonnementen wordt ingeschakeld:</span><span class="sxs-lookup"><span data-stu-id="43990-127">Follow these steps to create a cart which will enable the purchase of add-on(s) against existing base subscription(s):</span></span>

1. <span data-ttu-id="43990-128">Maak een **mandje** met een nieuwe **CartLineItem** met de abonnements-id in de eigenschap **ProvisioningContext** met de sleutel ParentSubscriptionId.</span><span class="sxs-lookup"><span data-stu-id="43990-128">Create a **Cart** with a new **CartLineItem** containing the subscription ID in the **ProvisioningContext** property with key "ParentSubscriptionId".</span></span>

2. <span data-ttu-id="43990-129">Roep de methode **Create** of **CreateAsync** aan.</span><span class="sxs-lookup"><span data-stu-id="43990-129">Call the **Create** or **CreateAsync** method.</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var cart = new Cart()
    {
        LineItems = new List<CartLineItem>()
        {
            new CartLineItem()
            {
                Id = 0,
                CatalogItemId = "An_addon_item_ID",
                ProvisioningContext = new Dictionary<string, string>
                {
                    {
                        "ParentSubscriptionId", "An_existing_subscription_Id"
                    }
                },
                Quantity = 1,
                BillingCycle = BillingCycleType.Annual,
            }
        }
    };

var createdCart = partnerOperations.Customers.ById(selectedCustomerId).Carts.Create(cart);
```

## <a name="rest-request"></a><span data-ttu-id="43990-130">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="43990-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="43990-131">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="43990-131">Request syntax</span></span>

| <span data-ttu-id="43990-132">Methode</span><span class="sxs-lookup"><span data-stu-id="43990-132">Method</span></span>   | <span data-ttu-id="43990-133">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="43990-133">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="43990-134">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="43990-134">**POST**</span></span> | <span data-ttu-id="43990-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Carts http/1.1</span><span class="sxs-lookup"><span data-stu-id="43990-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1</span></span>                        |

#### <a name="uri-parameter"></a><span data-ttu-id="43990-136">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="43990-136">URI parameter</span></span>

<span data-ttu-id="43990-137">Gebruik de volgende para meter voor het identificeren van de klant.</span><span class="sxs-lookup"><span data-stu-id="43990-137">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="43990-138">Naam</span><span class="sxs-lookup"><span data-stu-id="43990-138">Name</span></span>            | <span data-ttu-id="43990-139">Type</span><span class="sxs-lookup"><span data-stu-id="43990-139">Type</span></span>     | <span data-ttu-id="43990-140">Vereist</span><span class="sxs-lookup"><span data-stu-id="43990-140">Required</span></span> | <span data-ttu-id="43990-141">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="43990-141">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="43990-142">**klant-id**</span><span class="sxs-lookup"><span data-stu-id="43990-142">**customer-id**</span></span> | <span data-ttu-id="43990-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="43990-143">string</span></span>   | <span data-ttu-id="43990-144">Yes</span><span class="sxs-lookup"><span data-stu-id="43990-144">Yes</span></span>      | <span data-ttu-id="43990-145">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="43990-145">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="43990-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="43990-146">Request headers</span></span>

<span data-ttu-id="43990-147">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="43990-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="43990-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="43990-148">Request body</span></span>

<span data-ttu-id="43990-149">In deze tabel worden de eigenschappen van de [winkel wagen](cart-resources.md) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="43990-149">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="43990-150">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="43990-150">Property</span></span>              | <span data-ttu-id="43990-151">Type</span><span class="sxs-lookup"><span data-stu-id="43990-151">Type</span></span>             | <span data-ttu-id="43990-152">Vereist</span><span class="sxs-lookup"><span data-stu-id="43990-152">Required</span></span>        | <span data-ttu-id="43990-153">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="43990-153">Description</span></span> |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="43990-154">id</span><span class="sxs-lookup"><span data-stu-id="43990-154">id</span></span>                    | <span data-ttu-id="43990-155">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="43990-155">string</span></span>           | <span data-ttu-id="43990-156">No</span><span class="sxs-lookup"><span data-stu-id="43990-156">No</span></span>              | <span data-ttu-id="43990-157">Een winkel wagen-id die is opgegeven bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="43990-157">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="43990-158">creationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="43990-158">creationTimeStamp</span></span>     | <span data-ttu-id="43990-159">DateTime</span><span class="sxs-lookup"><span data-stu-id="43990-159">DateTime</span></span>         | <span data-ttu-id="43990-160">No</span><span class="sxs-lookup"><span data-stu-id="43990-160">No</span></span>              | <span data-ttu-id="43990-161">De datum waarop de winkel wagen is gemaakt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="43990-161">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="43990-162">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="43990-162">Applied upon successful creation of the cart.</span></span>         |
| <span data-ttu-id="43990-163">lastModifiedTimeStamp</span><span class="sxs-lookup"><span data-stu-id="43990-163">lastModifiedTimeStamp</span></span> | <span data-ttu-id="43990-164">DateTime</span><span class="sxs-lookup"><span data-stu-id="43990-164">DateTime</span></span>         | <span data-ttu-id="43990-165">No</span><span class="sxs-lookup"><span data-stu-id="43990-165">No</span></span>              | <span data-ttu-id="43990-166">De datum waarop de winkel wagen voor het laatst is bijgewerkt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="43990-166">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="43990-167">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="43990-167">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="43990-168">expirationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="43990-168">expirationTimeStamp</span></span>   | <span data-ttu-id="43990-169">DateTime</span><span class="sxs-lookup"><span data-stu-id="43990-169">DateTime</span></span>         | <span data-ttu-id="43990-170">No</span><span class="sxs-lookup"><span data-stu-id="43990-170">No</span></span>              | <span data-ttu-id="43990-171">De datum waarop de winkel wagen verloopt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="43990-171">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="43990-172">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="43990-172">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="43990-173">lastModifiedUser</span><span class="sxs-lookup"><span data-stu-id="43990-173">lastModifiedUser</span></span>      | <span data-ttu-id="43990-174">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="43990-174">string</span></span>           | <span data-ttu-id="43990-175">No</span><span class="sxs-lookup"><span data-stu-id="43990-175">No</span></span>              | <span data-ttu-id="43990-176">De gebruiker die de winkel wagen het laatst heeft bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="43990-176">The user who last updated the cart.</span></span> <span data-ttu-id="43990-177">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="43990-177">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="43990-178">Regel items</span><span class="sxs-lookup"><span data-stu-id="43990-178">lineItems</span></span>             | <span data-ttu-id="43990-179">Matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="43990-179">Array of objects</span></span> | <span data-ttu-id="43990-180">Yes</span><span class="sxs-lookup"><span data-stu-id="43990-180">Yes</span></span>             | <span data-ttu-id="43990-181">Een matrix met [CartLineItem](cart-resources.md#cartlineitem) -resources.</span><span class="sxs-lookup"><span data-stu-id="43990-181">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                             |

<span data-ttu-id="43990-182">In deze tabel worden de eigenschappen van [CartLineItem](cart-resources.md#cartlineitem) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="43990-182">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

| <span data-ttu-id="43990-183">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="43990-183">Property</span></span>             | <span data-ttu-id="43990-184">Type</span><span class="sxs-lookup"><span data-stu-id="43990-184">Type</span></span>                             | <span data-ttu-id="43990-185">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="43990-185">Description</span></span>                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="43990-186">id</span><span class="sxs-lookup"><span data-stu-id="43990-186">id</span></span>                   | <span data-ttu-id="43990-187">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="43990-187">string</span></span>                           | <span data-ttu-id="43990-188">Een unieke id voor een winkelwagen regel item.</span><span class="sxs-lookup"><span data-stu-id="43990-188">A unique identifier for a cart line item.</span></span> <span data-ttu-id="43990-189">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="43990-189">Applied upon successful creation of cart.</span></span>                                                                   |
| <span data-ttu-id="43990-190">catalogId</span><span class="sxs-lookup"><span data-stu-id="43990-190">catalogId</span></span>            | <span data-ttu-id="43990-191">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="43990-191">string</span></span>                           | <span data-ttu-id="43990-192">De id van het catalogus item.</span><span class="sxs-lookup"><span data-stu-id="43990-192">The catalog item identifier.</span></span>                                                                                                                          |
| <span data-ttu-id="43990-193">friendlyName</span><span class="sxs-lookup"><span data-stu-id="43990-193">friendlyName</span></span>         | <span data-ttu-id="43990-194">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="43990-194">string</span></span>                           | <span data-ttu-id="43990-195">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="43990-195">Optional.</span></span> <span data-ttu-id="43990-196">De beschrijvende naam voor het item dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.</span><span class="sxs-lookup"><span data-stu-id="43990-196">The friendly name for the item defined by the partner to help disambiguate.</span></span>                                                                 |
| <span data-ttu-id="43990-197">quantity</span><span class="sxs-lookup"><span data-stu-id="43990-197">quantity</span></span>             | <span data-ttu-id="43990-198">int</span><span class="sxs-lookup"><span data-stu-id="43990-198">int</span></span>                              | <span data-ttu-id="43990-199">Het aantal licenties of exemplaren.</span><span class="sxs-lookup"><span data-stu-id="43990-199">The number of licenses or instances.</span></span>                                                                                                                  |
| <span data-ttu-id="43990-200">currencyCode</span><span class="sxs-lookup"><span data-stu-id="43990-200">currencyCode</span></span>         | <span data-ttu-id="43990-201">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="43990-201">string</span></span>                           | <span data-ttu-id="43990-202">De valuta code.</span><span class="sxs-lookup"><span data-stu-id="43990-202">The currency code.</span></span>                                                                                                                                    |
| <span data-ttu-id="43990-203">billingCycle</span><span class="sxs-lookup"><span data-stu-id="43990-203">billingCycle</span></span>         | <span data-ttu-id="43990-204">Object</span><span class="sxs-lookup"><span data-stu-id="43990-204">Object</span></span>                           | <span data-ttu-id="43990-205">Het type facturerings cyclus dat voor de huidige periode is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="43990-205">The type of billing cycle set for the current period.</span></span>                                                                                                 |
| <span data-ttu-id="43990-206">deelnemers</span><span class="sxs-lookup"><span data-stu-id="43990-206">participants</span></span>         | <span data-ttu-id="43990-207">Lijst met object teken reeks paren</span><span class="sxs-lookup"><span data-stu-id="43990-207">List of Object String pairs</span></span>      | <span data-ttu-id="43990-208">Een verzameling partner on record (MPNID) voor de aankoop.</span><span class="sxs-lookup"><span data-stu-id="43990-208">A collection of PartnerId on Record (MPNID) on the purchase.</span></span>                                                                                          |
| <span data-ttu-id="43990-209">provisioningContext</span><span class="sxs-lookup"><span data-stu-id="43990-209">provisioningContext</span></span>  | <span data-ttu-id="43990-210">Dictionary<teken reeks, teken reeks></span><span class="sxs-lookup"><span data-stu-id="43990-210">Dictionary<string, string></span></span>       | <span data-ttu-id="43990-211">Een context die wordt gebruikt voor het inrichten van de aanbieding.</span><span class="sxs-lookup"><span data-stu-id="43990-211">A context used for provisioning of offer.</span></span>                                                                                                             |
| <span data-ttu-id="43990-212">orderGroup</span><span class="sxs-lookup"><span data-stu-id="43990-212">orderGroup</span></span>           | <span data-ttu-id="43990-213">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="43990-213">string</span></span>                           | <span data-ttu-id="43990-214">Een groep om aan te geven welke items bij elkaar kunnen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="43990-214">A group to indicate which items can be placed together.</span></span>                                                                                               |
| <span data-ttu-id="43990-215">addonItems</span><span class="sxs-lookup"><span data-stu-id="43990-215">addonItems</span></span>           | <span data-ttu-id="43990-216">Lijst met **CartLineItem** -objecten</span><span class="sxs-lookup"><span data-stu-id="43990-216">List of **CartLineItem** objects</span></span> | <span data-ttu-id="43990-217">Een verzameling winkelwagen regel items voor invoeg toepassingen die worden aangeschaft bij het basis abonnement dat resulteert van de aankoop van het bovenliggende winkelwagen regel item.</span><span class="sxs-lookup"><span data-stu-id="43990-217">A collection of cart line items for add-ons that will be purchased towards the base subscription that results from the parent cart line item's purchase.</span></span> |
| <span data-ttu-id="43990-218">fout</span><span class="sxs-lookup"><span data-stu-id="43990-218">error</span></span>                | <span data-ttu-id="43990-219">Object</span><span class="sxs-lookup"><span data-stu-id="43990-219">Object</span></span>                           | <span data-ttu-id="43990-220">Wordt toegepast nadat de winkel wagen is gemaakt in het geval van een fout.</span><span class="sxs-lookup"><span data-stu-id="43990-220">Applied after cart is created in case of an error.</span></span>                                                                                                    |

### <a name="request-example-new-base-subscription"></a><span data-ttu-id="43990-221">Voor beeld van aanvraag (nieuw basis abonnement)</span><span class="sxs-lookup"><span data-stu-id="43990-221">Request example (new base subscription)</span></span>

<span data-ttu-id="43990-222">In het volgende REST-voor beeld ziet u hoe u een mandje maakt met invoeg toepassings items voor een nieuw basis abonnement.</span><span class="sxs-lookup"><span data-stu-id="43990-222">The following REST example shows how to create a cart with add-on items for a new base subscription.</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f931348a-6312-47d0-a8dd-31a386dedb8f
MS-CorrelationId: f73baf70-bbc3-43d0-8b29-dffa08ff9511

{
    "LineItems": [
        {
            "Id":0,
            "CatalogItemId":"91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "FriendlyName":"Myofferpurchase",
            "Quantity":3,
            "BillingCycle":"monthly",
            "AddonItems": [
                {
                    "Id":1,
                    "CatalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
                    "Quantity":2,
                    "BillingCycle":"monthly"
                },
                {
                    "Id":2,
                    "CatalogItemId":"43FCE491-76D1-4BCC-B709-8A288786DBAE",
                    "Quantity":3,
                    "BillingCycle":"monthly"
                }
            ]
        }
    ]
}
```

#### <a name="request-example-existing-base-subscription"></a><span data-ttu-id="43990-223">Voor beeld van aanvraag (bestaand basis abonnement)</span><span class="sxs-lookup"><span data-stu-id="43990-223">Request example (existing base subscription)</span></span>

<span data-ttu-id="43990-224">In het volgende REST-voor beeld ziet u hoe u invoeg toepassingen toevoegt aan een bestaand basis abonnement.</span><span class="sxs-lookup"><span data-stu-id="43990-224">The following REST example show how to append add-ons to an existing base subscription.</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 512a777a-5427-452d-9637-18421387e435
MS-CorrelationId: 182474ba-7303-4d0f-870a-8c7fba5ccc4b

{
    "LineItems": [
        {
            "Id":0,
            "CatalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
            "Quantity":1,
            "BillingCycle":"annual",
            "ProvisioningContext":{"ParentSubscriptionId":"97555B61-7461-477A-A98C-9C76148783E4"}
        }
    ]
}
```

## <a name="rest-response"></a><span data-ttu-id="43990-225">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="43990-225">REST response</span></span>

<span data-ttu-id="43990-226">Als dit lukt, retourneert deze methode de gevulde [Winkelwagen](cart-resources.md) resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="43990-226">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

#### <a name="response-success-and-error-codes"></a><span data-ttu-id="43990-227">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="43990-227">Response success and error codes</span></span>

<span data-ttu-id="43990-228">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="43990-228">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="43990-229">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="43990-229">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="43990-230">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="43990-230">For the full list, see [Error Codes](error-codes.md).</span></span>

#### <a name="response-example-new-base-subscription"></a><span data-ttu-id="43990-231">Antwoord voorbeeld (nieuw basis abonnement)</span><span class="sxs-lookup"><span data-stu-id="43990-231">Response example (new base subscription)</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 958
Content-Type: application/json
MS-CorrelationId: f73baf70-bbc3-43d0-8b29-dffa08ff9511
MS-RequestId: f931348a-6312-47d0-a8dd-31a386dedb8f
X-Locale: en-US,en-US
Date: Thu, 01 Nov 2018 22:29:05 GMT

{
    "id":"dbe2f8d4-f21d-43e2-9356-cff6387c4ba1",
    "creationTimestamp":"2018-11-01T22:29:03.6900182Z",
    "lastModifiedTimestamp":"2018-11-01T22:29:03.6900182Z",
    "expirationTimestamp":"2018-11-01T22:44:05.0025799Z",
    "lastModifiedUser":"1824b7fc-2fac-4478-b177-66823c40ab75",
    "status":"Active",
    "lineItems": [
        {
            "id":0,
            "catalogItemId":"91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "friendlyName":"Myofferpurchase",
            "quantity":3,
            "currencyCode":"USD",
            "billingCycle":"monthly",
            "orderGroup":"OMS-0",
            "addonItems": [
                {
                    "id":1,
                    "catalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
                    "quantity":2,
                    "currencyCode":"USD",
                    "billingCycle":"monthly",
                    "orderGroup":"OMS-0"
                },
                {
                    "id":2,
                    "catalogItemId":"43FCE491-76D1-4BCC-B709-8A288786DBAE",
                    "quantity":3,
                    "currencyCode":"USD",
                    "billingCycle":"monthly",
                    "orderGroup":"OMS-0"
                }
            ]
        }
],
    "links": {
        "self": {
            "uri":"/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts/dbe2f8d4-f21d-43e2-9356-cff6387c4ba1",
            "method":"GET",
            "headers":[
            ]
        }
    },
    "attributes": {
        "objectType":"Cart"
    }
}
```

#### <a name="response-example-existing-base-subscription"></a><span data-ttu-id="43990-232">Antwoord voorbeeld (bestaand basis abonnement)</span><span class="sxs-lookup"><span data-stu-id="43990-232">Response example (existing base subscription)</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 707
Content-Type: application/json
MS-CorrelationId: 182474ba-7303-4d0f-870a-8c7fba5ccc4b
MS-RequestId: 512a777a-5427-452d-9637-18421387e435
X-Locale: en-US,en-US
Date: Thu, 01 Nov 2018 22:46:18 GMT

{
    "id":"4d927e27-93d1-448b-abe5-819b66ecca22",
    "creationTimestamp":"2018-11-01T22:46:16.2996364Z",
    "lastModifiedTimestamp":"2018-11-01T22:46:16.2996364Z",
    "expirationTimestamp":"2018-11-01T23:01:18.7543264Z",
    "lastModifiedUser":"1824b7fc-2fac-4478-b177-66823c40ab75",
    "status":"Active",
    "lineItems": [
        {
            "id":0,
            "catalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
            "quantity":1,
            "currencyCode":"USD",
            "billingCycle":"annual",
            "provisioningContext": {
                "parentSubscriptionId":"97555B61-7461-477A-A98C-9C76148783E4"
            },
            "orderGroup":"OMS-0"
        }
    ],
    "links": {
        "self": {
            "uri":"/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts/4d927e27-93d1-448b-abe5-819b66ecca22",
            "method":"GET",
            "headers":[
            ]
        }
    },
    "attributes": {
        "objectType":"Cart"
    }
}
```
