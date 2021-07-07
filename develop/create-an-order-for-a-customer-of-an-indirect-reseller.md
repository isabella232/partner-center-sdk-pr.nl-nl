---
title: Klantorder voor indirecte reseller maken
description: Meer informatie over het gebruik Partner Center API's om een order te maken voor een klant van een indirecte reseller. Het artikel bevat vereisten, stappen en voorbeelden.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6253ba2289ea1f58e7d8eaa960d7d0daaa887f0d
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973537"
---
# <a name="create-an-order-for-a-customer-of-an-indirect-reseller"></a><span data-ttu-id="e996a-104">Een bestelling maken voor een klant van een indirecte reseller</span><span class="sxs-lookup"><span data-stu-id="e996a-104">Create an order for a customer of an indirect reseller</span></span>

<span data-ttu-id="e996a-105">Een order maken voor een klant van een indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="e996a-105">How to create an order for a customer of an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e996a-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e996a-106">Prerequisites</span></span>

- <span data-ttu-id="e996a-107">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="e996a-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e996a-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e996a-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e996a-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e996a-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e996a-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="e996a-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e996a-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="e996a-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e996a-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="e996a-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e996a-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="e996a-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e996a-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e996a-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="e996a-115">De aanbiedings-id van het item dat moet worden gekocht.</span><span class="sxs-lookup"><span data-stu-id="e996a-115">The offer identifier of the item to purchase.</span></span>

- <span data-ttu-id="e996a-116">De tenant-id van de indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="e996a-116">The tenant identifier of the indirect reseller.</span></span>

## <a name="c"></a><span data-ttu-id="e996a-117">C\#</span><span class="sxs-lookup"><span data-stu-id="e996a-117">C\#</span></span>

<span data-ttu-id="e996a-118">Een order maken voor een klant van een indirecte reseller:</span><span class="sxs-lookup"><span data-stu-id="e996a-118">To create an order for a customer of an indirect reseller:</span></span>

1. <span data-ttu-id="e996a-119">Haal een verzameling van de indirecte resellers op die een relatie hebben met de aangemelde partner.</span><span class="sxs-lookup"><span data-stu-id="e996a-119">Get a collection of the indirect resellers that have a relationship with the signed-in partner.</span></span>

2. <span data-ttu-id="e996a-120">Haal een lokale variabele op voor het item in de verzameling dat overeenkomt met de indirecte reseller-id.</span><span class="sxs-lookup"><span data-stu-id="e996a-120">Get a local variable to the item in the collection that matches the indirect reseller ID.</span></span> <span data-ttu-id="e996a-121">Met deze stap krijgt u toegang tot de [**mpnId-eigenschap**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationship.mpnid) van de reseller wanneer u de order maakt.</span><span class="sxs-lookup"><span data-stu-id="e996a-121">This step helps you access the reseller's [**MpnId**](/dotnet/api/microsoft.store.partnercenter.models.relationships.partnerrelationship.mpnid) property when you create the order.</span></span>

3. <span data-ttu-id="e996a-122">Instantieer een [**Order-object**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) en stel de eigenschap [**ReferenceCustomerID**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.referencecustomerid) in op de klant-id om de klant vast te stellen.</span><span class="sxs-lookup"><span data-stu-id="e996a-122">Instantiate an [**Order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object and set the [**ReferenceCustomerID**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.referencecustomerid) property to the customer identifier in order to record the customer.</span></span>

4. <span data-ttu-id="e996a-123">Maak een lijst met [**OrderLineItem-objecten**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) en wijs de lijst toe aan de eigenschap [**LineItems van de**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.lineitems) order.</span><span class="sxs-lookup"><span data-stu-id="e996a-123">Create a list of [**OrderLineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) objects, and assign the list to the order's [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.lineitems) property.</span></span> <span data-ttu-id="e996a-124">Elk orderregelitem bevat de aankoopgegevens voor één aanbieding.</span><span class="sxs-lookup"><span data-stu-id="e996a-124">Each order line item contains the purchase information for one offer.</span></span> <span data-ttu-id="e996a-125">Zorg ervoor dat u de [**eigenschap PartnerIdOnRecord**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem.partneridonrecord) in elk regelitem vult met de MPN-id van de indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="e996a-125">Be sure to populate the [**PartnerIdOnRecord**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem.partneridonrecord) property in each line item with the MPN ID of the indirect reseller.</span></span> <span data-ttu-id="e996a-126">U moet ten minste één orderregelitem hebben.</span><span class="sxs-lookup"><span data-stu-id="e996a-126">You must have at least one order line item.</span></span>

5. <span data-ttu-id="e996a-127">Verkrijg een interface voor orderbewerkingen door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de [**eigenschap Orders.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders)</span><span class="sxs-lookup"><span data-stu-id="e996a-127">Obtain an interface to order operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and then retrieve the interface from the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property.</span></span>

6. <span data-ttu-id="e996a-128">Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) om de order te maken.</span><span class="sxs-lookup"><span data-stu-id="e996a-128">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) method to create the order.</span></span>

### <a name="c-example"></a><span data-ttu-id="e996a-129">\#C-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e996a-129">C\# example</span></span>

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

<span data-ttu-id="e996a-130">**Voorbeeld:** [Consoletest-app](console-test-app.md)**Project**: Partnercentrum-SDK **Samples Class**: PlaceOrderForCustomer.cs</span><span class="sxs-lookup"><span data-stu-id="e996a-130">**Sample**: [Console test app](console-test-app.md)**Project**: Partner Center SDK Samples **Class**: PlaceOrderForCustomer.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e996a-131">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e996a-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e996a-132">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e996a-132">Request syntax</span></span>

| <span data-ttu-id="e996a-133">Methode</span><span class="sxs-lookup"><span data-stu-id="e996a-133">Method</span></span>   | <span data-ttu-id="e996a-134">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e996a-134">Request URI</span></span>                                                                            |
|----------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="e996a-135">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="e996a-135">**POST**</span></span> | <span data-ttu-id="e996a-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e996a-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="e996a-137">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="e996a-137">URI parameters</span></span>

<span data-ttu-id="e996a-138">Gebruik de volgende padparameter om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="e996a-138">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="e996a-139">Naam</span><span class="sxs-lookup"><span data-stu-id="e996a-139">Name</span></span>        | <span data-ttu-id="e996a-140">Type</span><span class="sxs-lookup"><span data-stu-id="e996a-140">Type</span></span>   | <span data-ttu-id="e996a-141">Vereist</span><span class="sxs-lookup"><span data-stu-id="e996a-141">Required</span></span> | <span data-ttu-id="e996a-142">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e996a-142">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="e996a-143">customer-id</span><span class="sxs-lookup"><span data-stu-id="e996a-143">customer-id</span></span> | <span data-ttu-id="e996a-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e996a-144">string</span></span> | <span data-ttu-id="e996a-145">Ja</span><span class="sxs-lookup"><span data-stu-id="e996a-145">Yes</span></span>      | <span data-ttu-id="e996a-146">Een tekenreeks met GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="e996a-146">A GUID formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e996a-147">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e996a-147">Request headers</span></span>

<span data-ttu-id="e996a-148">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e996a-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e996a-149">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e996a-149">Request body</span></span>

#### <a name="order"></a><span data-ttu-id="e996a-150">Volgorde</span><span class="sxs-lookup"><span data-stu-id="e996a-150">Order</span></span>

<span data-ttu-id="e996a-151">In deze tabel worden de **ordereigenschappen** in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="e996a-151">This table describes the **Order** properties in the request body.</span></span>

| <span data-ttu-id="e996a-152">Naam</span><span class="sxs-lookup"><span data-stu-id="e996a-152">Name</span></span> | <span data-ttu-id="e996a-153">Type</span><span class="sxs-lookup"><span data-stu-id="e996a-153">Type</span></span> | <span data-ttu-id="e996a-154">Vereist</span><span class="sxs-lookup"><span data-stu-id="e996a-154">Required</span></span> | <span data-ttu-id="e996a-155">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e996a-155">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="e996a-156">id</span><span class="sxs-lookup"><span data-stu-id="e996a-156">id</span></span> | <span data-ttu-id="e996a-157">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e996a-157">string</span></span> | <span data-ttu-id="e996a-158">No</span><span class="sxs-lookup"><span data-stu-id="e996a-158">No</span></span> | <span data-ttu-id="e996a-159">Een order-id die wordt opgegeven wanneer de order is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e996a-159">An order identifier that is supplied upon successful creation of the order.</span></span> |
| <span data-ttu-id="e996a-160">referenceCustomerId</span><span class="sxs-lookup"><span data-stu-id="e996a-160">referenceCustomerId</span></span> | <span data-ttu-id="e996a-161">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e996a-161">string</span></span> | <span data-ttu-id="e996a-162">Ja</span><span class="sxs-lookup"><span data-stu-id="e996a-162">Yes</span></span> | <span data-ttu-id="e996a-163">De klant-id.</span><span class="sxs-lookup"><span data-stu-id="e996a-163">The customer identifier.</span></span> |
| <span data-ttu-id="e996a-164">billingCycle</span><span class="sxs-lookup"><span data-stu-id="e996a-164">billingCycle</span></span> | <span data-ttu-id="e996a-165">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e996a-165">string</span></span> | <span data-ttu-id="e996a-166">No</span><span class="sxs-lookup"><span data-stu-id="e996a-166">No</span></span> | <span data-ttu-id="e996a-167">De frequentie waarmee de partner wordt gefactureerd voor deze bestelling.</span><span class="sxs-lookup"><span data-stu-id="e996a-167">The frequency with which the partner is billed for this order.</span></span> <span data-ttu-id="e996a-168">De standaardwaarde is &quot; Maandelijks en wordt toegepast wanneer de order is &quot; gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e996a-168">The default is &quot;Monthly&quot; and is applied upon successful creation of the order.</span></span> <span data-ttu-id="e996a-169">Ondersteunde waarden zijn de namen van leden in [**BillingCycleType.**](/dotnet/api/microsoft.store.partnercenter.models.offers.billingcycletype)</span><span class="sxs-lookup"><span data-stu-id="e996a-169">Supported values are the member names found in [**BillingCycleType**](/dotnet/api/microsoft.store.partnercenter.models.offers.billingcycletype).</span></span> <span data-ttu-id="e996a-170">Opmerking: de jaarlijkse factureringsfunctie is nog niet algemeen beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="e996a-170">Note: the annual billing feature isn't yet generally available.</span></span> <span data-ttu-id="e996a-171">Ondersteuning voor jaarlijkse facturering is binnenkort beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="e996a-171">Support for annual billing is coming soon.</span></span> |
| <span data-ttu-id="e996a-172">lineItems</span><span class="sxs-lookup"><span data-stu-id="e996a-172">lineItems</span></span> | <span data-ttu-id="e996a-173">matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="e996a-173">array of objects</span></span> | <span data-ttu-id="e996a-174">Ja</span><span class="sxs-lookup"><span data-stu-id="e996a-174">Yes</span></span> | <span data-ttu-id="e996a-175">Een matrix met [**OrderLineItem-resources.**](#orderlineitem)</span><span class="sxs-lookup"><span data-stu-id="e996a-175">An array of [**OrderLineItem**](#orderlineitem) resources.</span></span> |
| <span data-ttu-id="e996a-176">creationDate</span><span class="sxs-lookup"><span data-stu-id="e996a-176">creationDate</span></span> | <span data-ttu-id="e996a-177">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e996a-177">string</span></span> | <span data-ttu-id="e996a-178">No</span><span class="sxs-lookup"><span data-stu-id="e996a-178">No</span></span> | <span data-ttu-id="e996a-179">De datum waarop de order is gemaakt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="e996a-179">The date the order was created, in date-time format.</span></span> <span data-ttu-id="e996a-180">Toegepast wanneer de order is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e996a-180">Applied upon successful creation of the order.</span></span> |
| <span data-ttu-id="e996a-181">kenmerken</span><span class="sxs-lookup"><span data-stu-id="e996a-181">attributes</span></span> | <span data-ttu-id="e996a-182">object</span><span class="sxs-lookup"><span data-stu-id="e996a-182">object</span></span> | <span data-ttu-id="e996a-183">Nee</span><span class="sxs-lookup"><span data-stu-id="e996a-183">No</span></span> | <span data-ttu-id="e996a-184">Bevat 'ObjectType': 'Order'.</span><span class="sxs-lookup"><span data-stu-id="e996a-184">Contains "ObjectType": "Order".</span></span> |

#### <a name="orderlineitem"></a><span data-ttu-id="e996a-185">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="e996a-185">OrderLineItem</span></span>

<span data-ttu-id="e996a-186">In deze tabel worden de **eigenschappen van OrderLineItem** in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="e996a-186">This table describes the **OrderLineItem** properties in the request body.</span></span>

| <span data-ttu-id="e996a-187">Naam</span><span class="sxs-lookup"><span data-stu-id="e996a-187">Name</span></span> | <span data-ttu-id="e996a-188">Type</span><span class="sxs-lookup"><span data-stu-id="e996a-188">Type</span></span> | <span data-ttu-id="e996a-189">Vereist</span><span class="sxs-lookup"><span data-stu-id="e996a-189">Required</span></span> | <span data-ttu-id="e996a-190">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e996a-190">Description</span></span> |
| ---- | ---- | -------- | ----------- |
| <span data-ttu-id="e996a-191">lineItemNumber</span><span class="sxs-lookup"><span data-stu-id="e996a-191">lineItemNumber</span></span> | <span data-ttu-id="e996a-192">int</span><span class="sxs-lookup"><span data-stu-id="e996a-192">int</span></span> | <span data-ttu-id="e996a-193">Ja</span><span class="sxs-lookup"><span data-stu-id="e996a-193">Yes</span></span> | <span data-ttu-id="e996a-194">Elk regelitem in de verzameling krijgt een uniek regelnummer, dat wordt geteld van 0 tot count-1.</span><span class="sxs-lookup"><span data-stu-id="e996a-194">Each line item in the collection gets a unique line number, counting up from 0 to count-1.</span></span> |
| <span data-ttu-id="e996a-195">offerId</span><span class="sxs-lookup"><span data-stu-id="e996a-195">offerId</span></span> | <span data-ttu-id="e996a-196">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e996a-196">string</span></span> | <span data-ttu-id="e996a-197">Ja</span><span class="sxs-lookup"><span data-stu-id="e996a-197">Yes</span></span> | <span data-ttu-id="e996a-198">De aanbiedings-id.</span><span class="sxs-lookup"><span data-stu-id="e996a-198">The offer identifier.</span></span> |
| <span data-ttu-id="e996a-199">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="e996a-199">subscriptionId</span></span> | <span data-ttu-id="e996a-200">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e996a-200">string</span></span> | <span data-ttu-id="e996a-201">No</span><span class="sxs-lookup"><span data-stu-id="e996a-201">No</span></span> | <span data-ttu-id="e996a-202">De abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="e996a-202">The subscription identifier.</span></span> |
| <span data-ttu-id="e996a-203">parentSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="e996a-203">parentSubscriptionId</span></span> | <span data-ttu-id="e996a-204">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e996a-204">string</span></span> | <span data-ttu-id="e996a-205">No</span><span class="sxs-lookup"><span data-stu-id="e996a-205">No</span></span> | <span data-ttu-id="e996a-206">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="e996a-206">Optional.</span></span> <span data-ttu-id="e996a-207">De id van het bovenliggende abonnement in een invoegaanbieding.</span><span class="sxs-lookup"><span data-stu-id="e996a-207">The ID of the parent subscription in an add-on offer.</span></span> <span data-ttu-id="e996a-208">Alleen van toepassing op PATCH.</span><span class="sxs-lookup"><span data-stu-id="e996a-208">Applies to PATCH only.</span></span> |
| <span data-ttu-id="e996a-209">Friendlyname</span><span class="sxs-lookup"><span data-stu-id="e996a-209">friendlyName</span></span> | <span data-ttu-id="e996a-210">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e996a-210">string</span></span> | <span data-ttu-id="e996a-211">No</span><span class="sxs-lookup"><span data-stu-id="e996a-211">No</span></span> | <span data-ttu-id="e996a-212">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="e996a-212">Optional.</span></span> <span data-ttu-id="e996a-213">De gebruiksvriendelijke naam voor het abonnement dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.</span><span class="sxs-lookup"><span data-stu-id="e996a-213">The friendly name for the subscription defined by the partner to help disambiguate.</span></span> |
| <span data-ttu-id="e996a-214">quantity</span><span class="sxs-lookup"><span data-stu-id="e996a-214">quantity</span></span> | <span data-ttu-id="e996a-215">int</span><span class="sxs-lookup"><span data-stu-id="e996a-215">int</span></span> | <span data-ttu-id="e996a-216">Ja</span><span class="sxs-lookup"><span data-stu-id="e996a-216">Yes</span></span> | <span data-ttu-id="e996a-217">Het aantal licenties voor een abonnement op basis van een licentie.</span><span class="sxs-lookup"><span data-stu-id="e996a-217">The number of licenses for a license-based subscription.</span></span> |
| <span data-ttu-id="e996a-218">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="e996a-218">partnerIdOnRecord</span></span> | <span data-ttu-id="e996a-219">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e996a-219">string</span></span> | <span data-ttu-id="e996a-220">No</span><span class="sxs-lookup"><span data-stu-id="e996a-220">No</span></span> | <span data-ttu-id="e996a-221">Wanneer een indirecte provider een order plaatst namens een indirecte reseller, vult u dit veld in met de MPN-id van alleen de **indirecte reseller** (nooit de id van de indirecte provider).</span><span class="sxs-lookup"><span data-stu-id="e996a-221">When an indirect provider places an order on behalf of an indirect reseller, populate this field with the MPN ID of the **indirect reseller only** (never the ID of the indirect provider).</span></span> <span data-ttu-id="e996a-222">Dit zorgt voor een juiste boekhouding voor incentives.</span><span class="sxs-lookup"><span data-stu-id="e996a-222">This ensures proper accounting for incentives.</span></span> <span data-ttu-id="e996a-223">**Als de MPN-id van de reseller niet wordt verstrekt, mislukt de order niet. De reseller wordt echter niet vastgelegd en als gevolg hiervan zijn de incentive-berekeningen mogelijk niet opgenomen in de verkoop.**</span><span class="sxs-lookup"><span data-stu-id="e996a-223">**Failure to provide the reseller MPN ID does not cause the order to fail. However, the reseller isn't recorded and as a consequence incentive calculations may not include the sale.**</span></span> |
| <span data-ttu-id="e996a-224">kenmerken</span><span class="sxs-lookup"><span data-stu-id="e996a-224">attributes</span></span> | <span data-ttu-id="e996a-225">object</span><span class="sxs-lookup"><span data-stu-id="e996a-225">object</span></span> | <span data-ttu-id="e996a-226">Nee</span><span class="sxs-lookup"><span data-stu-id="e996a-226">No</span></span> | <span data-ttu-id="e996a-227">Bevat "ObjectType":"OrderLineItem".</span><span class="sxs-lookup"><span data-stu-id="e996a-227">Contains "ObjectType":"OrderLineItem".</span></span> |

### <a name="request-example"></a><span data-ttu-id="e996a-228">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e996a-228">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e996a-229">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e996a-229">REST response</span></span>

<span data-ttu-id="e996a-230">Als dit lukt, bevat de antwoord-body de ingevulde [resource Order.](order-resources.md)</span><span class="sxs-lookup"><span data-stu-id="e996a-230">If successful, the response body contains the populated [Order](order-resources.md) resource.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e996a-231">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e996a-231">Response success and error codes</span></span>

<span data-ttu-id="e996a-232">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e996a-232">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e996a-233">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e996a-233">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e996a-234">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="e996a-234">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e996a-235">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e996a-235">Response example</span></span>

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
