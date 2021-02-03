---
title: Een klant order maken voor een indirecte wederverkoper
description: Meer informatie over het gebruik van partner Center-Api's voor het maken van een bestelling voor een klant van een indirecte wederverkoper. Artikel bevat vereisten, stappen en exmaples.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f72ecec8d82e6b8a1bc53c277206cafd7d8a4e03
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767644"
---
# <a name="create-an-order-for-a-customer-of-an-indirect-reseller"></a><span data-ttu-id="4138f-104">Een bestelling maken voor een klant van een indirecte reseller</span><span class="sxs-lookup"><span data-stu-id="4138f-104">Create an order for a customer of an indirect reseller</span></span>

<span data-ttu-id="4138f-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="4138f-105">**Applies to:**</span></span>

- <span data-ttu-id="4138f-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="4138f-106">Partner Center</span></span>

<span data-ttu-id="4138f-107">Hoe u een bestelling maakt voor een klant van een indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="4138f-107">How to create an order for a customer of an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4138f-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4138f-108">Prerequisites</span></span>

- <span data-ttu-id="4138f-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4138f-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4138f-110">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="4138f-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="4138f-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4138f-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4138f-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="4138f-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4138f-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="4138f-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4138f-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="4138f-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4138f-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="4138f-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4138f-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4138f-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="4138f-117">De aanbiedings-id van het item dat moet worden gekocht.</span><span class="sxs-lookup"><span data-stu-id="4138f-117">The offer identifier of the item to purchase.</span></span>

- <span data-ttu-id="4138f-118">De Tenant-id van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="4138f-118">The tenant identifier of the indirect reseller.</span></span>

## <a name="c"></a><span data-ttu-id="4138f-119">C\#</span><span class="sxs-lookup"><span data-stu-id="4138f-119">C\#</span></span>

<span data-ttu-id="4138f-120">Voor het maken van een bestelling voor een klant van een indirecte wederverkoper:</span><span class="sxs-lookup"><span data-stu-id="4138f-120">To create an order for a customer of an indirect reseller:</span></span>

1. <span data-ttu-id="4138f-121">Een verzameling van de indirecte wederverkopers ophalen die een relatie hebben met de aangemelde partner.</span><span class="sxs-lookup"><span data-stu-id="4138f-121">Get a collection of the indirect resellers that have a relationship with the signed-in partner.</span></span>

2. <span data-ttu-id="4138f-122">Een lokale variabele ophalen voor het item in de verzameling dat overeenkomt met de ID van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="4138f-122">Get a local variable to the item in the collection that matches the indirect reseller ID.</span></span> <span data-ttu-id="4138f-123">Deze stap helpt u bij het openen van de [**MpnId**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationship.mpnid) -eigenschap van de wederverkoper wanneer u de order maakt.</span><span class="sxs-lookup"><span data-stu-id="4138f-123">This step helps you access the reseller's [**MpnId**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationship.mpnid) property when you create the order.</span></span>

3. <span data-ttu-id="4138f-124">Maak een exemplaar van een object [**order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) en stel de eigenschap [**ReferenceCustomerID**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.referencecustomerid) in op de klant-id om de klant op te nemen.</span><span class="sxs-lookup"><span data-stu-id="4138f-124">Instantiate an [**Order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object and set the [**ReferenceCustomerID**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.referencecustomerid) property to the customer identifier in order to record the customer.</span></span>

4. <span data-ttu-id="4138f-125">Maak een lijst met [**OrderLineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) -objecten en wijs de lijst toe aan de eigenschap [**regel items**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.lineitems) van de order.</span><span class="sxs-lookup"><span data-stu-id="4138f-125">Create a list of [**OrderLineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) objects, and assign the list to the order's [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.lineitems) property.</span></span> <span data-ttu-id="4138f-126">Elk order regel item bevat de inkoop gegevens voor één aanbieding.</span><span class="sxs-lookup"><span data-stu-id="4138f-126">Each order line item contains the purchase information for one offer.</span></span> <span data-ttu-id="4138f-127">Zorg ervoor dat u de eigenschap [**PartnerIdOnRecord**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem.partneridonrecord) in elk regel item vult met de MPN-id van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="4138f-127">Be sure to populate the [**PartnerIdOnRecord**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem.partneridonrecord) property in each line item with the MPN ID of the indirect reseller.</span></span> <span data-ttu-id="4138f-128">U moet ten minste één order regel item hebben.</span><span class="sxs-lookup"><span data-stu-id="4138f-128">You must have at least one order line item.</span></span>

5. <span data-ttu-id="4138f-129">Schaf een interface aan om bewerkingen uit te best Ellen door de [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met de klant-id om de klant te identificeren en haal vervolgens de interface op uit de eigenschap [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) .</span><span class="sxs-lookup"><span data-stu-id="4138f-129">Obtain an interface to order operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and then retrieve the interface from the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property.</span></span>

6. <span data-ttu-id="4138f-130">Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) aan om de order te maken.</span><span class="sxs-lookup"><span data-stu-id="4138f-130">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) method to create the order.</span></span>

### <a name="c-example"></a><span data-ttu-id="4138f-131">C- \# voor beeld</span><span class="sxs-lookup"><span data-stu-id="4138f-131">C\# example</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string offerId;
// string indirectResellerId;

// Get the indirect resellers with a relationship to the signed-in partner.
var indirectResellers = partnerOperations.Relationships.Get(PartnerRelationshipType.IsIndirectCloudSolutionProviderOf);

// Find the matching reseller in the collection.
var selectedIndirectReseller = (indirectResellers != null && indirectResellers.Items.Any()) ?
    indirectResellers.Items.FirstOrDefault(reseller => reseller.Id.Equals(indirectResellerId, StringComparison.OrdinalIgnoreCase)) :
    null;

// Prepare the order and populate the PartnerIdOnRecord with the reseller&#39;s Microsoft Partner Network Id.
var order = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            OfferId = offerId,
            FriendlyName = "New offer purchase.",
            Quantity = 5,
            PartnerIdOnRecord = selectedIndirectReseller != null ? selectedIndirectReseller.MpnId : null
        }
    }
};

// Place the order.
var createdOrder = partnerOperations.Customers.ById(customerId).Orders.Create(order);
```

<span data-ttu-id="4138f-132">Voor **beeld**: [console test app](console-test-app.md)**project**: Partner Center SDK samples **klasse**: PlaceOrderForCustomer.cs</span><span class="sxs-lookup"><span data-stu-id="4138f-132">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: PlaceOrderForCustomer.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="4138f-133">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4138f-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4138f-134">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4138f-134">Request syntax</span></span>

| <span data-ttu-id="4138f-135">Methode</span><span class="sxs-lookup"><span data-stu-id="4138f-135">Method</span></span>   | <span data-ttu-id="4138f-136">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4138f-136">Request URI</span></span>                                                                            |
|----------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="4138f-137">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="4138f-137">**POST**</span></span> | <span data-ttu-id="4138f-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/orders http/1.1</span><span class="sxs-lookup"><span data-stu-id="4138f-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="4138f-139">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="4138f-139">URI parameters</span></span>

<span data-ttu-id="4138f-140">Gebruik de volgende para meter voor het identificeren van de klant.</span><span class="sxs-lookup"><span data-stu-id="4138f-140">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="4138f-141">Naam</span><span class="sxs-lookup"><span data-stu-id="4138f-141">Name</span></span>        | <span data-ttu-id="4138f-142">Type</span><span class="sxs-lookup"><span data-stu-id="4138f-142">Type</span></span>   | <span data-ttu-id="4138f-143">Vereist</span><span class="sxs-lookup"><span data-stu-id="4138f-143">Required</span></span> | <span data-ttu-id="4138f-144">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4138f-144">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="4138f-145">klant-id</span><span class="sxs-lookup"><span data-stu-id="4138f-145">customer-id</span></span> | <span data-ttu-id="4138f-146">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4138f-146">string</span></span> | <span data-ttu-id="4138f-147">Yes</span><span class="sxs-lookup"><span data-stu-id="4138f-147">Yes</span></span>      | <span data-ttu-id="4138f-148">Een teken reeks met een GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="4138f-148">A GUID formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4138f-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4138f-149">Request headers</span></span>

<span data-ttu-id="4138f-150">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4138f-150">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4138f-151">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4138f-151">Request body</span></span>

#### <a name="order"></a><span data-ttu-id="4138f-152">Volgorde</span><span class="sxs-lookup"><span data-stu-id="4138f-152">Order</span></span>

<span data-ttu-id="4138f-153">In deze tabel worden de eigenschappen van de **bestelling** in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="4138f-153">This table describes the **Order** properties in the request body.</span></span>

| <span data-ttu-id="4138f-154">Naam</span><span class="sxs-lookup"><span data-stu-id="4138f-154">Name</span></span> | <span data-ttu-id="4138f-155">Type</span><span class="sxs-lookup"><span data-stu-id="4138f-155">Type</span></span> | <span data-ttu-id="4138f-156">Vereist</span><span class="sxs-lookup"><span data-stu-id="4138f-156">Required</span></span> | <span data-ttu-id="4138f-157">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4138f-157">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="4138f-158">id</span><span class="sxs-lookup"><span data-stu-id="4138f-158">id</span></span> | <span data-ttu-id="4138f-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4138f-159">string</span></span> | <span data-ttu-id="4138f-160">No</span><span class="sxs-lookup"><span data-stu-id="4138f-160">No</span></span> | <span data-ttu-id="4138f-161">Een order-id die wordt geleverd bij het maken van de order.</span><span class="sxs-lookup"><span data-stu-id="4138f-161">An order identifier that is supplied upon successful creation of the order.</span></span> |
| <span data-ttu-id="4138f-162">referenceCustomerId</span><span class="sxs-lookup"><span data-stu-id="4138f-162">referenceCustomerId</span></span> | <span data-ttu-id="4138f-163">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4138f-163">string</span></span> | <span data-ttu-id="4138f-164">Yes</span><span class="sxs-lookup"><span data-stu-id="4138f-164">Yes</span></span> | <span data-ttu-id="4138f-165">De klant-id.</span><span class="sxs-lookup"><span data-stu-id="4138f-165">The customer identifier.</span></span> |
| <span data-ttu-id="4138f-166">billingCycle</span><span class="sxs-lookup"><span data-stu-id="4138f-166">billingCycle</span></span> | <span data-ttu-id="4138f-167">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4138f-167">string</span></span> | <span data-ttu-id="4138f-168">No</span><span class="sxs-lookup"><span data-stu-id="4138f-168">No</span></span> | <span data-ttu-id="4138f-169">De frequentie waarmee de partner voor deze order wordt gefactureerd.</span><span class="sxs-lookup"><span data-stu-id="4138f-169">The frequency with which the partner is billed for this order.</span></span> <span data-ttu-id="4138f-170">De standaard waarde is &quot; maandelijks &quot; en wordt toegepast bij het maken van de order.</span><span class="sxs-lookup"><span data-stu-id="4138f-170">The default is &quot;Monthly&quot; and is applied upon successful creation of the order.</span></span> <span data-ttu-id="4138f-171">Ondersteunde waarden zijn de lidnamen in [**BillingCycleType**](/dotnet/api/microsoft.store.partnercenter.models.offers.billingcycletype).</span><span class="sxs-lookup"><span data-stu-id="4138f-171">Supported values are the member names found in [**BillingCycleType**](/dotnet/api/microsoft.store.partnercenter.models.offers.billingcycletype).</span></span> <span data-ttu-id="4138f-172">Opmerking: de jaarlijkse facturerings functie is nog niet algemeen beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="4138f-172">Note: the annual billing feature isn't yet generally available.</span></span> <span data-ttu-id="4138f-173">De ondersteuning voor jaarlijkse facturering is binnenkort beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="4138f-173">Support for annual billing is coming soon.</span></span> |
| <span data-ttu-id="4138f-174">Regel items</span><span class="sxs-lookup"><span data-stu-id="4138f-174">lineItems</span></span> | <span data-ttu-id="4138f-175">matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="4138f-175">array of objects</span></span> | <span data-ttu-id="4138f-176">Yes</span><span class="sxs-lookup"><span data-stu-id="4138f-176">Yes</span></span> | <span data-ttu-id="4138f-177">Een matrix met [**OrderLineItem**](#orderlineitem) -resources.</span><span class="sxs-lookup"><span data-stu-id="4138f-177">An array of [**OrderLineItem**](#orderlineitem) resources.</span></span> |
| <span data-ttu-id="4138f-178">creationDate</span><span class="sxs-lookup"><span data-stu-id="4138f-178">creationDate</span></span> | <span data-ttu-id="4138f-179">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4138f-179">string</span></span> | <span data-ttu-id="4138f-180">No</span><span class="sxs-lookup"><span data-stu-id="4138f-180">No</span></span> | <span data-ttu-id="4138f-181">De datum waarop de order is gemaakt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="4138f-181">The date the order was created, in date-time format.</span></span> <span data-ttu-id="4138f-182">Wordt toegepast bij het maken van de order.</span><span class="sxs-lookup"><span data-stu-id="4138f-182">Applied upon successful creation of the order.</span></span> |
| <span data-ttu-id="4138f-183">kenmerken</span><span class="sxs-lookup"><span data-stu-id="4138f-183">attributes</span></span> | <span data-ttu-id="4138f-184">object</span><span class="sxs-lookup"><span data-stu-id="4138f-184">object</span></span> | <span data-ttu-id="4138f-185">No</span><span class="sxs-lookup"><span data-stu-id="4138f-185">No</span></span> | <span data-ttu-id="4138f-186">Bevat "object type": "order".</span><span class="sxs-lookup"><span data-stu-id="4138f-186">Contains "ObjectType": "Order".</span></span> |

#### <a name="orderlineitem"></a><span data-ttu-id="4138f-187">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="4138f-187">OrderLineItem</span></span>

<span data-ttu-id="4138f-188">In deze tabel worden de eigenschappen van **OrderLineItem** in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="4138f-188">This table describes the **OrderLineItem** properties in the request body.</span></span>

| <span data-ttu-id="4138f-189">Naam</span><span class="sxs-lookup"><span data-stu-id="4138f-189">Name</span></span> | <span data-ttu-id="4138f-190">Type</span><span class="sxs-lookup"><span data-stu-id="4138f-190">Type</span></span> | <span data-ttu-id="4138f-191">Vereist</span><span class="sxs-lookup"><span data-stu-id="4138f-191">Required</span></span> | <span data-ttu-id="4138f-192">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4138f-192">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="4138f-193">lineItemNumber</span><span class="sxs-lookup"><span data-stu-id="4138f-193">lineItemNumber</span></span> | <span data-ttu-id="4138f-194">int</span><span class="sxs-lookup"><span data-stu-id="4138f-194">int</span></span> | <span data-ttu-id="4138f-195">Ja</span><span class="sxs-lookup"><span data-stu-id="4138f-195">Yes</span></span> | <span data-ttu-id="4138f-196">Elk regel item in de verzameling krijgt een uniek regel nummer, geteld van 0 tot aantal-1.</span><span class="sxs-lookup"><span data-stu-id="4138f-196">Each line item in the collection gets a unique line number, counting up from 0 to count-1.</span></span> |
| <span data-ttu-id="4138f-197">offerId</span><span class="sxs-lookup"><span data-stu-id="4138f-197">offerId</span></span> | <span data-ttu-id="4138f-198">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4138f-198">string</span></span> | <span data-ttu-id="4138f-199">Yes</span><span class="sxs-lookup"><span data-stu-id="4138f-199">Yes</span></span> | <span data-ttu-id="4138f-200">De aanbiedings-id.</span><span class="sxs-lookup"><span data-stu-id="4138f-200">The offer identifier.</span></span> |
| <span data-ttu-id="4138f-201">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="4138f-201">subscriptionId</span></span> | <span data-ttu-id="4138f-202">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4138f-202">string</span></span> | <span data-ttu-id="4138f-203">No</span><span class="sxs-lookup"><span data-stu-id="4138f-203">No</span></span> | <span data-ttu-id="4138f-204">De abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="4138f-204">The subscription identifier.</span></span> |
| <span data-ttu-id="4138f-205">parentSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="4138f-205">parentSubscriptionId</span></span> | <span data-ttu-id="4138f-206">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4138f-206">string</span></span> | <span data-ttu-id="4138f-207">No</span><span class="sxs-lookup"><span data-stu-id="4138f-207">No</span></span> | <span data-ttu-id="4138f-208">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="4138f-208">Optional.</span></span> <span data-ttu-id="4138f-209">De ID van het bovenliggende abonnement in een invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="4138f-209">The ID of the parent subscription in an add-on offer.</span></span> <span data-ttu-id="4138f-210">Is alleen van toepassing op PATCH.</span><span class="sxs-lookup"><span data-stu-id="4138f-210">Applies to PATCH only.</span></span> |
| <span data-ttu-id="4138f-211">friendlyName</span><span class="sxs-lookup"><span data-stu-id="4138f-211">friendlyName</span></span> | <span data-ttu-id="4138f-212">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4138f-212">string</span></span> | <span data-ttu-id="4138f-213">No</span><span class="sxs-lookup"><span data-stu-id="4138f-213">No</span></span> | <span data-ttu-id="4138f-214">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="4138f-214">Optional.</span></span> <span data-ttu-id="4138f-215">De beschrijvende naam voor het abonnement dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.</span><span class="sxs-lookup"><span data-stu-id="4138f-215">The friendly name for the subscription defined by the partner to help disambiguate.</span></span> |
| <span data-ttu-id="4138f-216">quantity</span><span class="sxs-lookup"><span data-stu-id="4138f-216">quantity</span></span> | <span data-ttu-id="4138f-217">int</span><span class="sxs-lookup"><span data-stu-id="4138f-217">int</span></span> | <span data-ttu-id="4138f-218">Ja</span><span class="sxs-lookup"><span data-stu-id="4138f-218">Yes</span></span> | <span data-ttu-id="4138f-219">Het aantal licenties voor een abonnement op basis van licenties.</span><span class="sxs-lookup"><span data-stu-id="4138f-219">The number of licenses for a license-based subscription.</span></span> |
| <span data-ttu-id="4138f-220">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="4138f-220">partnerIdOnRecord</span></span> | <span data-ttu-id="4138f-221">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4138f-221">string</span></span> | <span data-ttu-id="4138f-222">No</span><span class="sxs-lookup"><span data-stu-id="4138f-222">No</span></span> | <span data-ttu-id="4138f-223">Wanneer een indirecte provider een bestelling namens een indirecte wederverkoper plaatst, vult u dit veld alleen met de MPN-ID van de **indirecte wederverkoper** (nooit de id van de indirecte provider).</span><span class="sxs-lookup"><span data-stu-id="4138f-223">When an indirect provider places an order on behalf of an indirect reseller, populate this field with the MPN ID of the **indirect reseller only** (never the ID of the indirect provider).</span></span> <span data-ttu-id="4138f-224">Dit zorgt voor een goede administratieve verwerking van prikkels.</span><span class="sxs-lookup"><span data-stu-id="4138f-224">This ensures proper accounting for incentives.</span></span> <span data-ttu-id="4138f-225">**Als de wederverkoper MPN-ID niet kan worden verstrekt, mislukt de order niet. De wederverkoper wordt echter niet geregistreerd en als gevolg hiervan kan de verkoop niet worden inbegrepen.**</span><span class="sxs-lookup"><span data-stu-id="4138f-225">**Failure to provide the reseller MPN ID does not cause the order to fail. However, the reseller isn't recorded and as a consequence incentive calculations may not include the sale.**</span></span> |
| <span data-ttu-id="4138f-226">kenmerken</span><span class="sxs-lookup"><span data-stu-id="4138f-226">attributes</span></span> | <span data-ttu-id="4138f-227">object</span><span class="sxs-lookup"><span data-stu-id="4138f-227">object</span></span> | <span data-ttu-id="4138f-228">No</span><span class="sxs-lookup"><span data-stu-id="4138f-228">No</span></span> | <span data-ttu-id="4138f-229">Bevat "object type": "OrderLineItem".</span><span class="sxs-lookup"><span data-stu-id="4138f-229">Contains "ObjectType":"OrderLineItem".</span></span> |

### <a name="request-example"></a><span data-ttu-id="4138f-230">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4138f-230">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/orders HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 02109f46-3ff2-4be4-9f37-b2eb6d58d542
MS-CorrelationId: 85195ae6-3de5-4978-abd4-7be2fbfe4c84
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 410
Expect: 100-continue

{
    "Id": null,
    "ReferenceCustomerId": "c501c3c4-d776-40ef-9ecf-9cefb59442c1",
    "BillingCycle": "unknown",
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "DB2E705F-B82A-4024-A3D5-D88E12F2DB35",
            "SubscriptionId": null,
            "ParentSubscriptionId": null,
            "FriendlyName": "New offer purchase.",
            "Quantity": 5,
            "PartnerIdOnRecord": "4847383",
            "Attributes": {
                "ObjectType": "OrderLineItem"
            }
        }
    ],
    "CreationDate": null,
    "Attributes": {
        "ObjectType": "Order"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="4138f-231">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4138f-231">REST response</span></span>

<span data-ttu-id="4138f-232">Als dit lukt, bevat de antwoord tekst de ingevulde [order](order-resources.md) resource.</span><span class="sxs-lookup"><span data-stu-id="4138f-232">If successful, the response body contains the populated [Order](order-resources.md) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4138f-233">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="4138f-233">Response success and error codes</span></span>

<span data-ttu-id="4138f-234">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="4138f-234">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4138f-235">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4138f-235">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4138f-236">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="4138f-236">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4138f-237">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="4138f-237">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 831
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 85195ae6-3de5-4978-abd4-7be2fbfe4c84
MS-RequestId: 02109f46-3ff2-4be4-9f37-b2eb6d58d542
MS-CV: Nd3Oum/L5EywtKQK.0
MS-ServerId: 020021921
Date: Mon, 10 Apr 2017 23:02:24 GMT

{
    "id": "3eddcac6-63b2-4c40-b0b6-f47e18301492",
    "referenceCustomerId": "c501c3c4-d776-40ef-9ecf-9cefb59442c1",
    "billingCycle": "monthly",
    "lineItems": [{
            "lineItemNumber": 0,
            "offerId": "DB2E705F-B82A-4024-A3D5-D88E12F2DB35",
            "subscriptionId": "42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
            "friendlyName": "New offer purchase.",
            "quantity": 5,
            "partnerIdOnRecord": "4847383",
            "links": {
                "subscription": {
                    "uri": "/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/subscriptions/42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2017-04-10T16:02:25.983-07:00",
    "links": {
        "self": {
            "uri": "/customers/c501c3c4-d776-40ef-9ecf-9cefb59442c1/orders/3eddcac6-63b2-4c40-b0b6-f47e18301492",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "etag": "eyJpZCI6IjNlZGRjYWM2LTYzYjItNGM0MC1iMGI2LWY0N2UxODMwMTQ5MiIsInZlcnNpb24iOjF9",
        "objectType": "Order"
    }
}
```
