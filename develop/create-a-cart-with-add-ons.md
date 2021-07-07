---
title: Een winkelwagen maken met invoegtoepassingen
description: Meer informatie over het gebruik Partner Center API's om een klantorder met invoegtoepassingen toe te voegen via een winkelwagen. In het artikel worden de vereisten en stappen voor het maken van een winkelwagen met invoegtoepassingen gedeeld.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 513a9607b9194c36253630c91de9622325317c3a
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973754"
---
# <a name="create-a-cart-with-add-ons-to-a-customer-order"></a><span data-ttu-id="ce5e5-104">Een winkelwagen maken met invoegtoepassingen voor een klantorder</span><span class="sxs-lookup"><span data-stu-id="ce5e5-104">Create a cart with add-ons to a customer order</span></span>

<span data-ttu-id="ce5e5-105">U kunt invoegtoepassingen aanschaffen via een winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-105">You can purchase add-ons through a cart.</span></span> <span data-ttu-id="ce5e5-106">Zie Partneraanbiedingen in het Cloud Solution Provider programma voor meer informatie over [wat momenteel beschikbaar is om Cloud Solution Provider verkopen.](/partner-center/csp-offers)</span><span class="sxs-lookup"><span data-stu-id="ce5e5-106">For more information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ce5e5-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ce5e5-107">Prerequisites</span></span>

- <span data-ttu-id="ce5e5-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ce5e5-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ce5e5-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="ce5e5-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ce5e5-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="ce5e5-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="ce5e5-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="ce5e5-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="ce5e5-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="ce5e5-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="ce5e5-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="ce5e5-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ce5e5-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="ce5e5-116">C\#</span><span class="sxs-lookup"><span data-stu-id="ce5e5-116">C\#</span></span>

<span data-ttu-id="ce5e5-117">Met een winkelwagen kunnen een basisaanbieding en de bijbehorende invoegtoepassingen worden gekocht.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-117">A cart enables the purchase of a base offer and its corresponding add-ons.</span></span> <span data-ttu-id="ce5e5-118">Volg deze stappen om een winkelwagen te maken:</span><span class="sxs-lookup"><span data-stu-id="ce5e5-118">Follow these steps to create a cart:</span></span>

1. <span data-ttu-id="ce5e5-119">Een [**winkelwagenobject instanteren.**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart)</span><span class="sxs-lookup"><span data-stu-id="ce5e5-119">Instantiate a [**Cart**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart) object.</span></span>

2. <span data-ttu-id="ce5e5-120">Maak een lijst met [**CartLineItem-objecten**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) die de basisaanbieding(en) vertegenwoordigen en wijs de lijst toe aan de eigenschap [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-120">Create a list of [**CartLineItem**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) objects that represent the base offer(s), and assign the list to the cart's [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) property.</span></span>

3. <span data-ttu-id="ce5e5-121">Vul onder het regelitem van elke basisaanbieding de lijst met **AddOnItems** in met andere **CartLineItem-objecten** die elk een invoeg-on vertegenwoordigen die wordt gekocht op basis van die basisaanbieding.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-121">Under each base offer's cart line item, populate the list of **AddOnItems** with other **CartLineItem** objects that each represent an add-on that will be purchased against that base offer.</span></span>

4. <span data-ttu-id="ce5e5-122">Verkrijg een interface voor winkelwagenbewerkingen door [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) te gebruiken om de methode [**ICustomerCollection.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de eigenschap **Winkelwagen.**</span><span class="sxs-lookup"><span data-stu-id="ce5e5-122">Obtain an interface to cart operations by using [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) to call the [**ICustomerCollection.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and then retrieving the interface from the **Cart** property.</span></span>

5. <span data-ttu-id="ce5e5-123">Roep ten slotte de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) om de winkelwagen te maken.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-123">Finally, call the [**Create**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) method to create the cart.</span></span>

### <a name="c-example"></a><span data-ttu-id="ce5e5-124">\#C-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="ce5e5-124">C\# example</span></span>

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

<span data-ttu-id="ce5e5-125">Volg deze stappen om een winkelwagen te maken waarmee de aankoop van invoeg-on(s) voor bestaande basisabonnementen mogelijk wordt:</span><span class="sxs-lookup"><span data-stu-id="ce5e5-125">Follow these steps to create a cart that will enable the purchase of add-on(s) against existing base subscription(s):</span></span>

1. <span data-ttu-id="ce5e5-126">Maak een **winkelwagen** met een nieuwe **CartLineItem** met de abonnements-id in de **eigenschap ProvisioningContext** met de sleutel ParentSubscriptionId.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-126">Create a **Cart** with a new **CartLineItem** containing the subscription ID in the **ProvisioningContext** property with key "ParentSubscriptionId".</span></span>

2. <span data-ttu-id="ce5e5-127">Roep de **methode Create** of **CreateAsync aan.**</span><span class="sxs-lookup"><span data-stu-id="ce5e5-127">Call the **Create** or **CreateAsync** method.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="ce5e5-128">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ce5e5-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ce5e5-129">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="ce5e5-129">Request syntax</span></span>

| <span data-ttu-id="ce5e5-130">Methode</span><span class="sxs-lookup"><span data-stu-id="ce5e5-130">Method</span></span>   | <span data-ttu-id="ce5e5-131">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ce5e5-131">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ce5e5-132">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="ce5e5-132">**POST**</span></span> | <span data-ttu-id="ce5e5-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ce5e5-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1</span></span>                        |

#### <a name="uri-parameter"></a><span data-ttu-id="ce5e5-134">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="ce5e5-134">URI parameter</span></span>

<span data-ttu-id="ce5e5-135">Gebruik de volgende padparameter om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-135">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="ce5e5-136">Naam</span><span class="sxs-lookup"><span data-stu-id="ce5e5-136">Name</span></span>            | <span data-ttu-id="ce5e5-137">Type</span><span class="sxs-lookup"><span data-stu-id="ce5e5-137">Type</span></span>     | <span data-ttu-id="ce5e5-138">Vereist</span><span class="sxs-lookup"><span data-stu-id="ce5e5-138">Required</span></span> | <span data-ttu-id="ce5e5-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ce5e5-139">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="ce5e5-140">**customer-id**</span><span class="sxs-lookup"><span data-stu-id="ce5e5-140">**customer-id**</span></span> | <span data-ttu-id="ce5e5-141">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ce5e5-141">string</span></span>   | <span data-ttu-id="ce5e5-142">Ja</span><span class="sxs-lookup"><span data-stu-id="ce5e5-142">Yes</span></span>      | <span data-ttu-id="ce5e5-143">Een in GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-143">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="ce5e5-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ce5e5-144">Request headers</span></span>

<span data-ttu-id="ce5e5-145">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="ce5e5-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ce5e5-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ce5e5-146">Request body</span></span>

<span data-ttu-id="ce5e5-147">In deze tabel worden de eigenschappen [van de winkelwagen](cart-resources.md) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-147">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="ce5e5-148">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="ce5e5-148">Property</span></span>              | <span data-ttu-id="ce5e5-149">Type</span><span class="sxs-lookup"><span data-stu-id="ce5e5-149">Type</span></span>             | <span data-ttu-id="ce5e5-150">Vereist</span><span class="sxs-lookup"><span data-stu-id="ce5e5-150">Required</span></span>        | <span data-ttu-id="ce5e5-151">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ce5e5-151">Description</span></span> |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ce5e5-152">id</span><span class="sxs-lookup"><span data-stu-id="ce5e5-152">id</span></span>                    | <span data-ttu-id="ce5e5-153">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ce5e5-153">string</span></span>           | <span data-ttu-id="ce5e5-154">No</span><span class="sxs-lookup"><span data-stu-id="ce5e5-154">No</span></span>              | <span data-ttu-id="ce5e5-155">Een winkelwagen-id die wordt opgegeven wanneer de winkelwagen is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-155">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="ce5e5-156">creationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="ce5e5-156">creationTimeStamp</span></span>     | <span data-ttu-id="ce5e5-157">DateTime</span><span class="sxs-lookup"><span data-stu-id="ce5e5-157">DateTime</span></span>         | <span data-ttu-id="ce5e5-158">Nee</span><span class="sxs-lookup"><span data-stu-id="ce5e5-158">No</span></span>              | <span data-ttu-id="ce5e5-159">De datum waarop de winkelwagen is gemaakt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-159">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="ce5e5-160">Toegepast wanneer de winkelwagen is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-160">Applied upon successful creation of the cart.</span></span>         |
| <span data-ttu-id="ce5e5-161">lastModifiedTimeStamp</span><span class="sxs-lookup"><span data-stu-id="ce5e5-161">lastModifiedTimeStamp</span></span> | <span data-ttu-id="ce5e5-162">DateTime</span><span class="sxs-lookup"><span data-stu-id="ce5e5-162">DateTime</span></span>         | <span data-ttu-id="ce5e5-163">Nee</span><span class="sxs-lookup"><span data-stu-id="ce5e5-163">No</span></span>              | <span data-ttu-id="ce5e5-164">De datum waarop de winkelwagen voor het laatst is bijgewerkt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-164">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="ce5e5-165">Toegepast wanneer de winkelwagen is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-165">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="ce5e5-166">expirationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="ce5e5-166">expirationTimeStamp</span></span>   | <span data-ttu-id="ce5e5-167">DateTime</span><span class="sxs-lookup"><span data-stu-id="ce5e5-167">DateTime</span></span>         | <span data-ttu-id="ce5e5-168">Nee</span><span class="sxs-lookup"><span data-stu-id="ce5e5-168">No</span></span>              | <span data-ttu-id="ce5e5-169">De datum waarop de winkelwagen verloopt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-169">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="ce5e5-170">Toegepast bij het maken van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-170">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="ce5e5-171">lastModifiedUser</span><span class="sxs-lookup"><span data-stu-id="ce5e5-171">lastModifiedUser</span></span>      | <span data-ttu-id="ce5e5-172">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ce5e5-172">string</span></span>           | <span data-ttu-id="ce5e5-173">No</span><span class="sxs-lookup"><span data-stu-id="ce5e5-173">No</span></span>              | <span data-ttu-id="ce5e5-174">De gebruiker die de winkelwagen voor het laatst heeft bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-174">The user who last updated the cart.</span></span> <span data-ttu-id="ce5e5-175">Toegepast bij het maken van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-175">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="ce5e5-176">lineItems</span><span class="sxs-lookup"><span data-stu-id="ce5e5-176">lineItems</span></span>             | <span data-ttu-id="ce5e5-177">Matrix met objecten</span><span class="sxs-lookup"><span data-stu-id="ce5e5-177">Array of objects</span></span> | <span data-ttu-id="ce5e5-178">Ja</span><span class="sxs-lookup"><span data-stu-id="ce5e5-178">Yes</span></span>             | <span data-ttu-id="ce5e5-179">Een matrix van [CartLineItem-resources.](cart-resources.md#cartlineitem)</span><span class="sxs-lookup"><span data-stu-id="ce5e5-179">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                             |

<span data-ttu-id="ce5e5-180">In deze tabel worden de [eigenschappen van CartLineItem](cart-resources.md#cartlineitem) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-180">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

| <span data-ttu-id="ce5e5-181">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="ce5e5-181">Property</span></span>             | <span data-ttu-id="ce5e5-182">Type</span><span class="sxs-lookup"><span data-stu-id="ce5e5-182">Type</span></span>                             | <span data-ttu-id="ce5e5-183">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ce5e5-183">Description</span></span>                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="ce5e5-184">id</span><span class="sxs-lookup"><span data-stu-id="ce5e5-184">id</span></span>                   | <span data-ttu-id="ce5e5-185">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ce5e5-185">string</span></span>                           | <span data-ttu-id="ce5e5-186">Een unieke id voor een winkelwagenregelitem.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-186">A unique identifier for a cart line item.</span></span> <span data-ttu-id="ce5e5-187">Toegepast bij het maken van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-187">Applied upon successful creation of cart.</span></span>                                                                   |
| <span data-ttu-id="ce5e5-188">catalogId</span><span class="sxs-lookup"><span data-stu-id="ce5e5-188">catalogId</span></span>            | <span data-ttu-id="ce5e5-189">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ce5e5-189">string</span></span>                           | <span data-ttu-id="ce5e5-190">De id van het catalogusitem.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-190">The catalog item identifier.</span></span>                                                                                                                          |
| <span data-ttu-id="ce5e5-191">Friendlyname</span><span class="sxs-lookup"><span data-stu-id="ce5e5-191">friendlyName</span></span>         | <span data-ttu-id="ce5e5-192">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ce5e5-192">string</span></span>                           | <span data-ttu-id="ce5e5-193">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-193">Optional.</span></span> <span data-ttu-id="ce5e5-194">De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het opsysen van ambiguïteit.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-194">The friendly name for the item defined by the partner to help disambiguate.</span></span>                                                                 |
| <span data-ttu-id="ce5e5-195">quantity</span><span class="sxs-lookup"><span data-stu-id="ce5e5-195">quantity</span></span>             | <span data-ttu-id="ce5e5-196">int</span><span class="sxs-lookup"><span data-stu-id="ce5e5-196">int</span></span>                              | <span data-ttu-id="ce5e5-197">Het aantal licenties of instanties.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-197">The number of licenses or instances.</span></span>                                                                                                                  |
| <span data-ttu-id="ce5e5-198">currencyCode</span><span class="sxs-lookup"><span data-stu-id="ce5e5-198">currencyCode</span></span>         | <span data-ttu-id="ce5e5-199">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ce5e5-199">string</span></span>                           | <span data-ttu-id="ce5e5-200">De valutacode.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-200">The currency code.</span></span>                                                                                                                                    |
| <span data-ttu-id="ce5e5-201">billingCycle</span><span class="sxs-lookup"><span data-stu-id="ce5e5-201">billingCycle</span></span>         | <span data-ttu-id="ce5e5-202">Object</span><span class="sxs-lookup"><span data-stu-id="ce5e5-202">Object</span></span>                           | <span data-ttu-id="ce5e5-203">Het type factureringscyclus dat is ingesteld voor de huidige periode.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-203">The type of billing cycle set for the current period.</span></span>                                                                                                 |
| <span data-ttu-id="ce5e5-204">deelnemers</span><span class="sxs-lookup"><span data-stu-id="ce5e5-204">participants</span></span>         | <span data-ttu-id="ce5e5-205">Lijst met objectreeksparen</span><span class="sxs-lookup"><span data-stu-id="ce5e5-205">List of Object String pairs</span></span>      | <span data-ttu-id="ce5e5-206">Een verzameling PartnerId on Record (MPN-id) voor de aankoop.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-206">A collection of PartnerId on Record (MPN ID) on the purchase.</span></span>                                                                                          |
| <span data-ttu-id="ce5e5-207">provisioningContext</span><span class="sxs-lookup"><span data-stu-id="ce5e5-207">provisioningContext</span></span>  | <span data-ttu-id="ce5e5-208">Woordenlijst<tekenreeks, tekenreeks></span><span class="sxs-lookup"><span data-stu-id="ce5e5-208">Dictionary<string, string></span></span>       | <span data-ttu-id="ce5e5-209">Een context die wordt gebruikt voor het inrichten van de aanbieding.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-209">A context used for provisioning of offer.</span></span>                                                                                                             |
| <span data-ttu-id="ce5e5-210">orderGroup</span><span class="sxs-lookup"><span data-stu-id="ce5e5-210">orderGroup</span></span>           | <span data-ttu-id="ce5e5-211">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ce5e5-211">string</span></span>                           | <span data-ttu-id="ce5e5-212">Een groep om aan te geven welke items bij elkaar kunnen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-212">A group to indicate which items can be placed together.</span></span>                                                                                               |
| <span data-ttu-id="ce5e5-213">addonItems</span><span class="sxs-lookup"><span data-stu-id="ce5e5-213">addonItems</span></span>           | <span data-ttu-id="ce5e5-214">Lijst met **CartLineItem-objecten**</span><span class="sxs-lookup"><span data-stu-id="ce5e5-214">List of **CartLineItem** objects</span></span> | <span data-ttu-id="ce5e5-215">Een verzameling winkelwagenregelitems voor invoegtoepassingen die worden aangeschaft voor het basisabonnement dat het resultaat is van de aankoop van het bovenliggende winkelwagenlijnitem.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-215">A collection of cart line items for add-ons that will be purchased towards the base subscription that results from the parent cart line item's purchase.</span></span> |
| <span data-ttu-id="ce5e5-216">fout</span><span class="sxs-lookup"><span data-stu-id="ce5e5-216">error</span></span>                | <span data-ttu-id="ce5e5-217">Object</span><span class="sxs-lookup"><span data-stu-id="ce5e5-217">Object</span></span>                           | <span data-ttu-id="ce5e5-218">Toegepast nadat de winkelwagen is gemaakt als er een fout is.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-218">Applied after cart is created if there is an error.</span></span>                                                                                                    |

### <a name="request-example-new-base-subscription"></a><span data-ttu-id="ce5e5-219">Voorbeeld van aanvraag (nieuw basisabonnement)</span><span class="sxs-lookup"><span data-stu-id="ce5e5-219">Request example (new base subscription)</span></span>

<span data-ttu-id="ce5e5-220">In het volgende REST-voorbeeld ziet u hoe u een winkelwagen maakt met invoeg-items voor een nieuw basisabonnement.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-220">The following REST example shows how to create a cart with add-on items for a new base subscription.</span></span>

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

#### <a name="request-example-existing-base-subscription"></a><span data-ttu-id="ce5e5-221">Voorbeeld van aanvraag (bestaand basisabonnement)</span><span class="sxs-lookup"><span data-stu-id="ce5e5-221">Request example (existing base subscription)</span></span>

<span data-ttu-id="ce5e5-222">In het volgende REST-voorbeeld ziet u hoe u invoegtoepassingen toevoegt aan een bestaand basisabonnement.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-222">The following REST example shows how to append add-ons to an existing base subscription.</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="ce5e5-223">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ce5e5-223">REST response</span></span>

<span data-ttu-id="ce5e5-224">Als dit lukt, retourneert deze methode de ingevulde [winkelwagenresource](cart-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-224">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

#### <a name="response-success-and-error-codes"></a><span data-ttu-id="ce5e5-225">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="ce5e5-225">Response success and error codes</span></span>

<span data-ttu-id="ce5e5-226">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-226">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ce5e5-227">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ce5e5-227">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ce5e5-228">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="ce5e5-228">For the full list, see [Error Codes](error-codes.md).</span></span>

#### <a name="response-example-new-base-subscription"></a><span data-ttu-id="ce5e5-229">Voorbeeld van antwoord (nieuw basisabonnement)</span><span class="sxs-lookup"><span data-stu-id="ce5e5-229">Response example (new base subscription)</span></span>

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

#### <a name="response-example-existing-base-subscription"></a><span data-ttu-id="ce5e5-230">Voorbeeld van antwoord (bestaand basisabonnement)</span><span class="sxs-lookup"><span data-stu-id="ce5e5-230">Response example (existing base subscription)</span></span>

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
