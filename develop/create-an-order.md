---
title: Een klant order maken
description: Meer informatie over het gebruik van partner Center-Api's voor het maken van een bestelling voor een klant. Artikel bevat vereisten, stappen en voor beelden.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ce176909a1f9c350f1c16615171de57a7beb888d
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767636"
---
# <a name="create-an-order-for-a-customer-using-partner-center-apis"></a><span data-ttu-id="72a9f-104">Een bestelling maken voor een klant die partner Center-Api's gebruikt</span><span class="sxs-lookup"><span data-stu-id="72a9f-104">Create an order for a customer using Partner Center APIs</span></span>

<span data-ttu-id="72a9f-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="72a9f-105">**Applies to:**</span></span>

- <span data-ttu-id="72a9f-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="72a9f-106">Partner Center</span></span>
- <span data-ttu-id="72a9f-107">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="72a9f-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="72a9f-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="72a9f-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="72a9f-109">Het maken van een **order voor voor Azure gereserveerde VM-instantie producten** is *alleen* van toepassing op:</span><span class="sxs-lookup"><span data-stu-id="72a9f-109">Creating an **order for Azure reserved VM instance products** applies *only* to:</span></span>

- <span data-ttu-id="72a9f-110">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="72a9f-110">Partner Center</span></span>

<span data-ttu-id="72a9f-111">Zie [partner aanbiedingen in het Cloud Solution Provider-programma](/partner-center/csp-offers)voor meer informatie over wat momenteel beschikbaar is om te verkopen.</span><span class="sxs-lookup"><span data-stu-id="72a9f-111">For information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72a9f-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="72a9f-112">Prerequisites</span></span>

- <span data-ttu-id="72a9f-113">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="72a9f-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="72a9f-114">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="72a9f-114">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="72a9f-115">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="72a9f-115">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="72a9f-116">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="72a9f-116">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="72a9f-117">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="72a9f-117">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="72a9f-118">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="72a9f-118">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="72a9f-119">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="72a9f-119">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="72a9f-120">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="72a9f-120">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="72a9f-121">Een aanbiedings-id.</span><span class="sxs-lookup"><span data-stu-id="72a9f-121">An offer identifier.</span></span>

## <a name="c"></a><span data-ttu-id="72a9f-122">C\#</span><span class="sxs-lookup"><span data-stu-id="72a9f-122">C\#</span></span>

<span data-ttu-id="72a9f-123">Voor het maken van een bestelling voor een klant:</span><span class="sxs-lookup"><span data-stu-id="72a9f-123">To create an order for a customer:</span></span>

1. <span data-ttu-id="72a9f-124">Maak een exemplaar van een object [**order**](order-resources.md) en stel de eigenschap **ReferenceCustomerID** in op de klant-id voor het registreren van de klant.</span><span class="sxs-lookup"><span data-stu-id="72a9f-124">Instantiate an [**Order**](order-resources.md) object and set the **ReferenceCustomerID** property to the customer ID to record the customer.</span></span>

2. <span data-ttu-id="72a9f-125">Maak een lijst met [**OrderLineItem**](order-resources.md#orderlineitem) -objecten en wijs de lijst toe aan de eigenschap **regel items** van de order.</span><span class="sxs-lookup"><span data-stu-id="72a9f-125">Create a list of [**OrderLineItem**](order-resources.md#orderlineitem) objects, and assign the list to the order's **LineItems** property.</span></span> <span data-ttu-id="72a9f-126">Elk order regel item bevat de inkoop gegevens voor één aanbieding.</span><span class="sxs-lookup"><span data-stu-id="72a9f-126">Each order line item contains the purchase information for one offer.</span></span> <span data-ttu-id="72a9f-127">U moet ten minste één order regel item hebben.</span><span class="sxs-lookup"><span data-stu-id="72a9f-127">You must have at least one order line item.</span></span>

3. <span data-ttu-id="72a9f-128">Een interface voor het best Ellen van bewerkingen verkrijgen.</span><span class="sxs-lookup"><span data-stu-id="72a9f-128">Obtain an interface to order operations.</span></span> <span data-ttu-id="72a9f-129">Roep eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="72a9f-129">First, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="72a9f-130">Haal vervolgens de interface op uit de eigenschap [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) .</span><span class="sxs-lookup"><span data-stu-id="72a9f-130">Next, retrieve the interface from the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property.</span></span>

4. <span data-ttu-id="72a9f-131">Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) aan en geef het [**volg orde**](order-resources.md) -object door.</span><span class="sxs-lookup"><span data-stu-id="72a9f-131">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) method and pass in the [**Order**](order-resources.md) object.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string offerId;

var order = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            OfferId = offerId,
            FriendlyName = "new offer purchase",
            Quantity = 1,
            ProvisioningContext = new Dictionary<string, string>
            {
                { "subscriptionId", "5198C069-3DAA-403A-8660-5BE11BFD12EE" },
                { "scope", "shared" },
                { "duration", "3Years" }
            }
        }
    }
};

var createdOrder = partnerOperations.Customers.ById(customerId).Orders.Create(order);
```

<span data-ttu-id="72a9f-132">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="72a9f-132">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="72a9f-133">**Project**: Partner Center SDK-voor beelden **klasse**: CreateOrder.cs</span><span class="sxs-lookup"><span data-stu-id="72a9f-133">**Project**: Partner Center SDK Samples **Class**: CreateOrder.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="72a9f-134">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="72a9f-134">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="72a9f-135">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="72a9f-135">Request syntax</span></span>

| <span data-ttu-id="72a9f-136">Methode</span><span class="sxs-lookup"><span data-stu-id="72a9f-136">Method</span></span>   | <span data-ttu-id="72a9f-137">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="72a9f-137">Request URI</span></span>                                                                            |
|----------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="72a9f-138">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="72a9f-138">**POST**</span></span> | <span data-ttu-id="72a9f-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/orders http/1.1</span><span class="sxs-lookup"><span data-stu-id="72a9f-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="72a9f-140">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="72a9f-140">URI parameters</span></span>

<span data-ttu-id="72a9f-141">Gebruik de volgende para meter voor het identificeren van de klant.</span><span class="sxs-lookup"><span data-stu-id="72a9f-141">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="72a9f-142">Naam</span><span class="sxs-lookup"><span data-stu-id="72a9f-142">Name</span></span>        | <span data-ttu-id="72a9f-143">Type</span><span class="sxs-lookup"><span data-stu-id="72a9f-143">Type</span></span>   | <span data-ttu-id="72a9f-144">Vereist</span><span class="sxs-lookup"><span data-stu-id="72a9f-144">Required</span></span> | <span data-ttu-id="72a9f-145">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="72a9f-145">Description</span></span>                                                |
|-------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="72a9f-146">klant-id</span><span class="sxs-lookup"><span data-stu-id="72a9f-146">customer-id</span></span> | <span data-ttu-id="72a9f-147">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-147">string</span></span> | <span data-ttu-id="72a9f-148">Yes</span><span class="sxs-lookup"><span data-stu-id="72a9f-148">Yes</span></span>      | <span data-ttu-id="72a9f-149">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="72a9f-149">A GUID formatted customer-id that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="72a9f-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="72a9f-150">Request headers</span></span>

<span data-ttu-id="72a9f-151">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="72a9f-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="72a9f-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="72a9f-152">Request body</span></span>

#### <a name="order"></a><span data-ttu-id="72a9f-153">Volgorde</span><span class="sxs-lookup"><span data-stu-id="72a9f-153">Order</span></span>

<span data-ttu-id="72a9f-154">In deze tabel worden de eigenschappen van de [bestelling](order-resources.md) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="72a9f-154">This table describes the [Order](order-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="72a9f-155">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="72a9f-155">Property</span></span>             | <span data-ttu-id="72a9f-156">Type</span><span class="sxs-lookup"><span data-stu-id="72a9f-156">Type</span></span>                        | <span data-ttu-id="72a9f-157">Vereist</span><span class="sxs-lookup"><span data-stu-id="72a9f-157">Required</span></span>                        | <span data-ttu-id="72a9f-158">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="72a9f-158">Description</span></span>                                                                   |
|----------------------|-----------------------------|---------------------------------|-------------------------------------------------------------------------------|
| <span data-ttu-id="72a9f-159">id</span><span class="sxs-lookup"><span data-stu-id="72a9f-159">id</span></span>                   | <span data-ttu-id="72a9f-160">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-160">string</span></span>                      | <span data-ttu-id="72a9f-161">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-161">No</span></span>                              | <span data-ttu-id="72a9f-162">Een order-id die wordt geleverd bij het maken van de order.</span><span class="sxs-lookup"><span data-stu-id="72a9f-162">An order identifier that is supplied upon successful creation of the order.</span></span>   |
| <span data-ttu-id="72a9f-163">referenceCustomerId</span><span class="sxs-lookup"><span data-stu-id="72a9f-163">referenceCustomerId</span></span>  | <span data-ttu-id="72a9f-164">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-164">string</span></span>                      | <span data-ttu-id="72a9f-165">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-165">No</span></span>                              | <span data-ttu-id="72a9f-166">De klant-id.</span><span class="sxs-lookup"><span data-stu-id="72a9f-166">The customer identifier.</span></span> |
| <span data-ttu-id="72a9f-167">billingCycle</span><span class="sxs-lookup"><span data-stu-id="72a9f-167">billingCycle</span></span>         | <span data-ttu-id="72a9f-168">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-168">string</span></span>                      | <span data-ttu-id="72a9f-169">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-169">No</span></span>                              | <span data-ttu-id="72a9f-170">Hiermee wordt de frequentie aangegeven waarmee de partner voor deze order wordt gefactureerd.</span><span class="sxs-lookup"><span data-stu-id="72a9f-170">Indicates the frequency with which the partner is billed for this order.</span></span> <span data-ttu-id="72a9f-171">Ondersteunde waarden zijn de lidnamen in [BillingCycleType](product-resources.md#billingcycletype).</span><span class="sxs-lookup"><span data-stu-id="72a9f-171">Supported values are the member names found in [BillingCycleType](product-resources.md#billingcycletype).</span></span> <span data-ttu-id="72a9f-172">De standaard waarde is ' maandelijks ' of ' eenmalige ' bij het maken van de order.</span><span class="sxs-lookup"><span data-stu-id="72a9f-172">The default is "Monthly" or "OneTime" at order creation.</span></span> <span data-ttu-id="72a9f-173">Dit veld wordt toegepast bij het maken van de order.</span><span class="sxs-lookup"><span data-stu-id="72a9f-173">This field is applied upon successful creation of the order.</span></span> |
| <span data-ttu-id="72a9f-174">Regel items</span><span class="sxs-lookup"><span data-stu-id="72a9f-174">lineItems</span></span>            | <span data-ttu-id="72a9f-175">matrix van [OrderLineItem](order-resources.md#orderlineitem) -resources</span><span class="sxs-lookup"><span data-stu-id="72a9f-175">array of [OrderLineItem](order-resources.md#orderlineitem) resources</span></span> | <span data-ttu-id="72a9f-176">Yes</span><span class="sxs-lookup"><span data-stu-id="72a9f-176">Yes</span></span>      | <span data-ttu-id="72a9f-177">Een gespecificeerde lijst met de aanbiedingen die de klant koopt, met inbegrip van de hoeveelheid.</span><span class="sxs-lookup"><span data-stu-id="72a9f-177">An itemized list of the offers the customer is purchasing including the quantity.</span></span>        |
| <span data-ttu-id="72a9f-178">currencyCode</span><span class="sxs-lookup"><span data-stu-id="72a9f-178">currencyCode</span></span>         | <span data-ttu-id="72a9f-179">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-179">string</span></span>                      | <span data-ttu-id="72a9f-180">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-180">No</span></span>                              | <span data-ttu-id="72a9f-181">Alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="72a9f-181">Read-only.</span></span> <span data-ttu-id="72a9f-182">De valuta die wordt gebruikt bij het plaatsen van de order.</span><span class="sxs-lookup"><span data-stu-id="72a9f-182">The currency used when placing the order.</span></span> <span data-ttu-id="72a9f-183">Wordt toegepast bij het maken van de order.</span><span class="sxs-lookup"><span data-stu-id="72a9f-183">Applied upon successful creation of the order.</span></span>           |
| <span data-ttu-id="72a9f-184">creationDate</span><span class="sxs-lookup"><span data-stu-id="72a9f-184">creationDate</span></span>         | <span data-ttu-id="72a9f-185">datum/tijd</span><span class="sxs-lookup"><span data-stu-id="72a9f-185">datetime</span></span>                    | <span data-ttu-id="72a9f-186">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-186">No</span></span>                              | <span data-ttu-id="72a9f-187">Alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="72a9f-187">Read-only.</span></span> <span data-ttu-id="72a9f-188">De datum waarop de order is gemaakt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="72a9f-188">The date the order was created, in date-time format.</span></span> <span data-ttu-id="72a9f-189">Wordt toegepast bij het maken van de order.</span><span class="sxs-lookup"><span data-stu-id="72a9f-189">Applied upon successful creation of the order.</span></span>                                   |
| <span data-ttu-id="72a9f-190">status</span><span class="sxs-lookup"><span data-stu-id="72a9f-190">status</span></span>               | <span data-ttu-id="72a9f-191">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-191">string</span></span>                      | <span data-ttu-id="72a9f-192">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-192">No</span></span>                              | <span data-ttu-id="72a9f-193">Alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="72a9f-193">Read-only.</span></span> <span data-ttu-id="72a9f-194">De status van de order.</span><span class="sxs-lookup"><span data-stu-id="72a9f-194">The status of the order.</span></span>  <span data-ttu-id="72a9f-195">Ondersteunde waarden zijn de lidnamen in [OrderStatus](order-resources.md#orderstatus).</span><span class="sxs-lookup"><span data-stu-id="72a9f-195">Supported values are the member names found in [OrderStatus](order-resources.md#orderstatus).</span></span>        |
| <span data-ttu-id="72a9f-196">koppelen</span><span class="sxs-lookup"><span data-stu-id="72a9f-196">links</span></span>                | [<span data-ttu-id="72a9f-197">OrderLinks</span><span class="sxs-lookup"><span data-stu-id="72a9f-197">OrderLinks</span></span>](utility-resources.md#resourcelinks)              | <span data-ttu-id="72a9f-198">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-198">No</span></span>                              | <span data-ttu-id="72a9f-199">De resource koppelingen die overeenkomen met de volg orde.</span><span class="sxs-lookup"><span data-stu-id="72a9f-199">The resource links corresponding to the Order.</span></span> |
| <span data-ttu-id="72a9f-200">kenmerken</span><span class="sxs-lookup"><span data-stu-id="72a9f-200">attributes</span></span>           | [<span data-ttu-id="72a9f-201">ResourceAttributes</span><span class="sxs-lookup"><span data-stu-id="72a9f-201">ResourceAttributes</span></span>](utility-resources.md#resourceattributes) | <span data-ttu-id="72a9f-202">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-202">No</span></span>                              | <span data-ttu-id="72a9f-203">De meta gegevens kenmerken die overeenkomen met de volg orde.</span><span class="sxs-lookup"><span data-stu-id="72a9f-203">The metadata attributes corresponding to the Order.</span></span> |

#### <a name="orderlineitem"></a><span data-ttu-id="72a9f-204">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="72a9f-204">OrderLineItem</span></span>

<span data-ttu-id="72a9f-205">In deze tabel worden de eigenschappen van [OrderLineItem](order-resources.md#orderlineitem) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="72a9f-205">This table describes the [OrderLineItem](order-resources.md#orderlineitem) properties in the request body.</span></span>

>[!NOTE]
><span data-ttu-id="72a9f-206">De partnerIdOnRecord mag alleen worden gegeven wanneer een indirecte provider een bestelling namens een indirecte wederverkoper plaatst.</span><span class="sxs-lookup"><span data-stu-id="72a9f-206">The partnerIdOnRecord should only be provided when an indirect provider places an order on behalf of an indirect reseller.</span></span> <span data-ttu-id="72a9f-207">Het wordt gebruikt voor het opslaan van de Microsoft Partner Network ID alleen van de indirecte wederverkoper (nooit de ID van de indirecte provider).</span><span class="sxs-lookup"><span data-stu-id="72a9f-207">It's used to store the Microsoft Partner Network ID of the indirect reseller only (never the ID of the indirect provider).</span></span>

| <span data-ttu-id="72a9f-208">Naam</span><span class="sxs-lookup"><span data-stu-id="72a9f-208">Name</span></span>                 | <span data-ttu-id="72a9f-209">Type</span><span class="sxs-lookup"><span data-stu-id="72a9f-209">Type</span></span>   | <span data-ttu-id="72a9f-210">Vereist</span><span class="sxs-lookup"><span data-stu-id="72a9f-210">Required</span></span> | <span data-ttu-id="72a9f-211">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="72a9f-211">Description</span></span>                                                                                                                                                                                                                                |
|----------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="72a9f-212">lineItemNumber</span><span class="sxs-lookup"><span data-stu-id="72a9f-212">lineItemNumber</span></span>       | <span data-ttu-id="72a9f-213">int</span><span class="sxs-lookup"><span data-stu-id="72a9f-213">int</span></span>    | <span data-ttu-id="72a9f-214">Ja</span><span class="sxs-lookup"><span data-stu-id="72a9f-214">Yes</span></span>      | <span data-ttu-id="72a9f-215">Elk regel item in de verzameling krijgt een uniek regel nummer, geteld van 0 tot aantal-1.</span><span class="sxs-lookup"><span data-stu-id="72a9f-215">Each line item in the collection gets a unique line number, counting up from 0 to count-1.</span></span>                                                                                                                                                 |
| <span data-ttu-id="72a9f-216">offerId</span><span class="sxs-lookup"><span data-stu-id="72a9f-216">offerId</span></span>              | <span data-ttu-id="72a9f-217">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-217">string</span></span> | <span data-ttu-id="72a9f-218">Yes</span><span class="sxs-lookup"><span data-stu-id="72a9f-218">Yes</span></span>      | <span data-ttu-id="72a9f-219">De aanbiedings-id.</span><span class="sxs-lookup"><span data-stu-id="72a9f-219">The offer identifier.</span></span>                                                                                                                                                                                                                      |
| <span data-ttu-id="72a9f-220">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="72a9f-220">subscriptionId</span></span>       | <span data-ttu-id="72a9f-221">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-221">string</span></span> | <span data-ttu-id="72a9f-222">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-222">No</span></span>       | <span data-ttu-id="72a9f-223">De abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="72a9f-223">The subscription identifier.</span></span>                                                                                                                                                                                                               |
| <span data-ttu-id="72a9f-224">parentSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="72a9f-224">parentSubscriptionId</span></span> | <span data-ttu-id="72a9f-225">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-225">string</span></span> | <span data-ttu-id="72a9f-226">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-226">No</span></span>       | <span data-ttu-id="72a9f-227">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="72a9f-227">Optional.</span></span> <span data-ttu-id="72a9f-228">De ID van het bovenliggende abonnement in een invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="72a9f-228">The ID of the parent subscription in an add-on offer.</span></span> <span data-ttu-id="72a9f-229">Is alleen van toepassing op PATCH.</span><span class="sxs-lookup"><span data-stu-id="72a9f-229">Applies to PATCH only.</span></span>                                                                                                                                                     |
| <span data-ttu-id="72a9f-230">friendlyName</span><span class="sxs-lookup"><span data-stu-id="72a9f-230">friendlyName</span></span>         | <span data-ttu-id="72a9f-231">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-231">string</span></span> | <span data-ttu-id="72a9f-232">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-232">No</span></span>       | <span data-ttu-id="72a9f-233">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="72a9f-233">Optional.</span></span> <span data-ttu-id="72a9f-234">De beschrijvende naam voor het abonnement dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.</span><span class="sxs-lookup"><span data-stu-id="72a9f-234">The friendly name for the subscription defined by the partner to help disambiguate.</span></span>                                                                                                                                              |
| <span data-ttu-id="72a9f-235">quantity</span><span class="sxs-lookup"><span data-stu-id="72a9f-235">quantity</span></span>             | <span data-ttu-id="72a9f-236">int</span><span class="sxs-lookup"><span data-stu-id="72a9f-236">int</span></span>    | <span data-ttu-id="72a9f-237">Ja</span><span class="sxs-lookup"><span data-stu-id="72a9f-237">Yes</span></span>      | <span data-ttu-id="72a9f-238">Het aantal licenties voor een abonnement op basis van licenties.</span><span class="sxs-lookup"><span data-stu-id="72a9f-238">The number of licenses for a license-based subscription.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="72a9f-239">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="72a9f-239">partnerIdOnRecord</span></span>    | <span data-ttu-id="72a9f-240">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-240">string</span></span> | <span data-ttu-id="72a9f-241">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-241">No</span></span>       | <span data-ttu-id="72a9f-242">Wanneer een indirecte provider een bestelling namens een indirecte wederverkoper plaatst, vult u dit veld alleen met de MPN-ID van de **indirecte wederverkoper** (nooit de id van de indirecte provider).</span><span class="sxs-lookup"><span data-stu-id="72a9f-242">When an indirect provider places an order on behalf of an indirect reseller, populate this field with the MPN ID of the **indirect reseller only** (never the ID of the indirect provider).</span></span> <span data-ttu-id="72a9f-243">Dit zorgt voor een goede administratieve verwerking van prikkels.</span><span class="sxs-lookup"><span data-stu-id="72a9f-243">This ensures proper accounting for incentives.</span></span> |
| <span data-ttu-id="72a9f-244">provisioningContext</span><span class="sxs-lookup"><span data-stu-id="72a9f-244">provisioningContext</span></span>  | <span data-ttu-id="72a9f-245">Dictionary<teken reeks, teken reeks></span><span class="sxs-lookup"><span data-stu-id="72a9f-245">Dictionary<string, string></span></span>                | <span data-ttu-id="72a9f-246">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-246">No</span></span>       |  <span data-ttu-id="72a9f-247">Informatie die is vereist voor het inrichten van sommige items in de catalogus.</span><span class="sxs-lookup"><span data-stu-id="72a9f-247">Information required for provisioning for some items in the catalog.</span></span> <span data-ttu-id="72a9f-248">De eigenschap provisioningVariables in een SKU geeft aan welke eigenschappen vereist zijn voor specifieke items in de catalogus.</span><span class="sxs-lookup"><span data-stu-id="72a9f-248">The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog.</span></span>                  |
| <span data-ttu-id="72a9f-249">koppelen</span><span class="sxs-lookup"><span data-stu-id="72a9f-249">links</span></span>                | [<span data-ttu-id="72a9f-250">OrderLineItemLinks</span><span class="sxs-lookup"><span data-stu-id="72a9f-250">OrderLineItemLinks</span></span>](order-resources.md#orderlineitemlinks) | <span data-ttu-id="72a9f-251">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-251">No</span></span>       |  <span data-ttu-id="72a9f-252">Alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="72a9f-252">Read-only.</span></span> <span data-ttu-id="72a9f-253">De resource koppelingen die overeenkomen met het order regel item.</span><span class="sxs-lookup"><span data-stu-id="72a9f-253">The resource links corresponding to the Order line item.</span></span>  |
| <span data-ttu-id="72a9f-254">kenmerken</span><span class="sxs-lookup"><span data-stu-id="72a9f-254">attributes</span></span>           | [<span data-ttu-id="72a9f-255">ResourceAttributes</span><span class="sxs-lookup"><span data-stu-id="72a9f-255">ResourceAttributes</span></span>](utility-resources.md#resourceattributes) | <span data-ttu-id="72a9f-256">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-256">No</span></span>       | <span data-ttu-id="72a9f-257">De meta gegevens kenmerken die overeenkomen met de OrderLineItem.</span><span class="sxs-lookup"><span data-stu-id="72a9f-257">The metadata attributes corresponding to the OrderLineItem.</span></span> |
| <span data-ttu-id="72a9f-258">renewsTo</span><span class="sxs-lookup"><span data-stu-id="72a9f-258">renewsTo</span></span>             | <span data-ttu-id="72a9f-259">Matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="72a9f-259">Array of objects</span></span>                          | <span data-ttu-id="72a9f-260">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-260">No</span></span>    |<span data-ttu-id="72a9f-261">Een matrix met [RenewsTo](order-resources.md#renewsto) -resources.</span><span class="sxs-lookup"><span data-stu-id="72a9f-261">An array of [RenewsTo](order-resources.md#renewsto) resources.</span></span>                                                                            |

##### <a name="renewsto"></a><span data-ttu-id="72a9f-262">RenewsTo</span><span class="sxs-lookup"><span data-stu-id="72a9f-262">RenewsTo</span></span>

<span data-ttu-id="72a9f-263">In deze tabel worden de eigenschappen van [RenewsTo](order-resources.md#renewsto) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="72a9f-263">This table describes the [RenewsTo](order-resources.md#renewsto) properties in the request body.</span></span>

| <span data-ttu-id="72a9f-264">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="72a9f-264">Property</span></span>              | <span data-ttu-id="72a9f-265">Type</span><span class="sxs-lookup"><span data-stu-id="72a9f-265">Type</span></span>             | <span data-ttu-id="72a9f-266">Vereist</span><span class="sxs-lookup"><span data-stu-id="72a9f-266">Required</span></span>        | <span data-ttu-id="72a9f-267">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="72a9f-267">Description</span></span> |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="72a9f-268">termDuration</span><span class="sxs-lookup"><span data-stu-id="72a9f-268">termDuration</span></span>          | <span data-ttu-id="72a9f-269">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72a9f-269">string</span></span>           | <span data-ttu-id="72a9f-270">No</span><span class="sxs-lookup"><span data-stu-id="72a9f-270">No</span></span>              | <span data-ttu-id="72a9f-271">Een ISO 8601-representatie van de duur van de verlengings termijn.</span><span class="sxs-lookup"><span data-stu-id="72a9f-271">An ISO 8601 representation of the renewal term's duration.</span></span> <span data-ttu-id="72a9f-272">De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar).</span><span class="sxs-lookup"><span data-stu-id="72a9f-272">The current supported values are **P1M** (1 month) and **P1Y** (1 year).</span></span> |

### <a name="request-example"></a><span data-ttu-id="72a9f-273">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="72a9f-273">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders HTTP/1.1
Authorization: Bearer <token>
Host: api.partnercenter.microsoft.com
Content-Length: 691
Content-Type: application/json

{
  "BillingCycle": "one_time",
  "CurrencyCode": "USD",
  "LineItems": [
    {
      "LineItemNumber": 0,
      "ProvisioningContext": {
        "subscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
        "scope": "shared",
        "duration": "1Year"
      },
      "OfferId": "DZH318Z0BQ4B:0047:DZH318Z0DSM8",
      "FriendlyName": "A_sample_Azure_RI",
      "Quantity": 1
    }
  ]
}
```

## <a name="rest-response"></a><span data-ttu-id="72a9f-274">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="72a9f-274">REST response</span></span>

<span data-ttu-id="72a9f-275">Als dit lukt, retourneert de methode een [order](order-resources.md) resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="72a9f-275">If successful, the method returns an [Order](order-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="72a9f-276">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="72a9f-276">Response success and error codes</span></span>

<span data-ttu-id="72a9f-277">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="72a9f-277">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="72a9f-278">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="72a9f-278">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="72a9f-279">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="72a9f-279">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="72a9f-280">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="72a9f-280">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 788
Content-Type: application/json; charset=utf-8
MS-CorrelationId: b593cbb7-b358-4b31-81fc-e60b9c277a7f
MS-RequestId: 025f4c19-217f-49d6-a056-391902c62fb3
Date: Thu, 15 Mar 2018 22:30:02 GMT

{
  "id": "Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1",
  "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
  "billingCycle": "one_time",
  "currencyCode": "USD",
  "lineItems": [
    {
        "lineItemNumber": 0,
        "offerId": "84A03D81-6B37-4D66-8D4A-FAEA24541538",
        "friendlyName": "A_sample_Azure_RI",
        "quantity": 1,
        "links": {
            "sku": {
                "uri": "/products/DZH318Z0BQ4B/skus/0047?country=US",
                "method": "GET",
                "headers": []
            }
        }
    } ],
    "creationDate": "2018-03-15T22:30:02.085152Z",
    "status": "pending",
    "links": {
        "provisioningStatus": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/Cs_jyTxubLpvdJXdo8xcQZN6I2RsLrgZ1",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Order"
    }
}
```
