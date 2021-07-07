---
title: Een klantorder maken
description: Meer informatie over het gebruik Partner Center API's om een order voor een klant te maken. Het artikel bevat vereisten, stappen en voorbeelden.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c3a86a99f43bdeec5e4c560ab59e1924b76c0636
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973539"
---
# <a name="create-an-order-for-a-customer-using-partner-center-apis"></a><span data-ttu-id="312d6-104">Een order voor een klant maken met behulp van Partner Center API's</span><span class="sxs-lookup"><span data-stu-id="312d6-104">Create an order for a customer using Partner Center APIs</span></span>

<span data-ttu-id="312d6-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="312d6-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="312d6-106">Het maken van **een bestelling voor azure-producten voor gereserveerde VM-instanties is** alleen van toepassing *op:*</span><span class="sxs-lookup"><span data-stu-id="312d6-106">Creating an **order for Azure reserved VM instance products** applies *only* to:</span></span>

- <span data-ttu-id="312d6-107">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="312d6-107">Partner Center</span></span>

<span data-ttu-id="312d6-108">Zie Partneraanbiedingen in het Cloud Solution Provider voor meer informatie over [wat momenteel beschikbaar is om te verkopen.](/partner-center/csp-offers)</span><span class="sxs-lookup"><span data-stu-id="312d6-108">For information about what is currently available to sell, see [Partner offers in the Cloud Solution Provider program](/partner-center/csp-offers).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="312d6-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="312d6-109">Prerequisites</span></span>

- <span data-ttu-id="312d6-110">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="312d6-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="312d6-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="312d6-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="312d6-112">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="312d6-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="312d6-113">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="312d6-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="312d6-114">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="312d6-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="312d6-115">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="312d6-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="312d6-116">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="312d6-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="312d6-117">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="312d6-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="312d6-118">Een aanbiedings-id.</span><span class="sxs-lookup"><span data-stu-id="312d6-118">An offer identifier.</span></span>

## <a name="c"></a><span data-ttu-id="312d6-119">C\#</span><span class="sxs-lookup"><span data-stu-id="312d6-119">C\#</span></span>

<span data-ttu-id="312d6-120">Een order voor een klant maken:</span><span class="sxs-lookup"><span data-stu-id="312d6-120">To create an order for a customer:</span></span>

1. <span data-ttu-id="312d6-121">Instantieer een [**Order-object**](order-resources.md) en stel de **eigenschap ReferenceCustomerID** in op de klant-id om de klant vast te stellen.</span><span class="sxs-lookup"><span data-stu-id="312d6-121">Instantiate an [**Order**](order-resources.md) object and set the **ReferenceCustomerID** property to the customer ID to record the customer.</span></span>

2. <span data-ttu-id="312d6-122">Maak een lijst met [**OrderLineItem-objecten**](order-resources.md#orderlineitem) en wijs de lijst toe aan de eigenschap **LineItems van de** order.</span><span class="sxs-lookup"><span data-stu-id="312d6-122">Create a list of [**OrderLineItem**](order-resources.md#orderlineitem) objects, and assign the list to the order's **LineItems** property.</span></span> <span data-ttu-id="312d6-123">Elk orderregelitem bevat de aankoopgegevens voor één aanbieding.</span><span class="sxs-lookup"><span data-stu-id="312d6-123">Each order line item contains the purchase information for one offer.</span></span> <span data-ttu-id="312d6-124">U moet ten minste één orderregelitem hebben.</span><span class="sxs-lookup"><span data-stu-id="312d6-124">You must have at least one order line item.</span></span>

3. <span data-ttu-id="312d6-125">Een interface verkrijgen voor het orden van bewerkingen.</span><span class="sxs-lookup"><span data-stu-id="312d6-125">Obtain an interface to order operations.</span></span> <span data-ttu-id="312d6-126">Roep eerst de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="312d6-126">First, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="312d6-127">Haal vervolgens de interface op uit de [**eigenschap Orders.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders)</span><span class="sxs-lookup"><span data-stu-id="312d6-127">Next, retrieve the interface from the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property.</span></span>

4. <span data-ttu-id="312d6-128">Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) en geef het [**orderobject**](order-resources.md) door.</span><span class="sxs-lookup"><span data-stu-id="312d6-128">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.createasync) method and pass in the [**Order**](order-resources.md) object.</span></span>

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

<span data-ttu-id="312d6-129">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="312d6-129">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="312d6-130">**Project:** Partnercentrum-SDK Samples **Class**: CreateOrder.cs</span><span class="sxs-lookup"><span data-stu-id="312d6-130">**Project**: Partner Center SDK Samples **Class**: CreateOrder.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="312d6-131">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="312d6-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="312d6-132">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="312d6-132">Request syntax</span></span>

| <span data-ttu-id="312d6-133">Methode</span><span class="sxs-lookup"><span data-stu-id="312d6-133">Method</span></span>   | <span data-ttu-id="312d6-134">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="312d6-134">Request URI</span></span>                                                                            |
|----------|----------------------------------------------------------------------------------------|
| <span data-ttu-id="312d6-135">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="312d6-135">**POST**</span></span> | <span data-ttu-id="312d6-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="312d6-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/orders HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="312d6-137">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="312d6-137">URI parameters</span></span>

<span data-ttu-id="312d6-138">Gebruik de volgende padparameter om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="312d6-138">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="312d6-139">Naam</span><span class="sxs-lookup"><span data-stu-id="312d6-139">Name</span></span>        | <span data-ttu-id="312d6-140">Type</span><span class="sxs-lookup"><span data-stu-id="312d6-140">Type</span></span>   | <span data-ttu-id="312d6-141">Vereist</span><span class="sxs-lookup"><span data-stu-id="312d6-141">Required</span></span> | <span data-ttu-id="312d6-142">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="312d6-142">Description</span></span>                                                |
|-------------|--------|----------|------------------------------------------------------------|
| <span data-ttu-id="312d6-143">customer-id</span><span class="sxs-lookup"><span data-stu-id="312d6-143">customer-id</span></span> | <span data-ttu-id="312d6-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-144">string</span></span> | <span data-ttu-id="312d6-145">Ja</span><span class="sxs-lookup"><span data-stu-id="312d6-145">Yes</span></span>      | <span data-ttu-id="312d6-146">Een met GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="312d6-146">A GUID formatted customer-id that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="312d6-147">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="312d6-147">Request headers</span></span>

<span data-ttu-id="312d6-148">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="312d6-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="312d6-149">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="312d6-149">Request body</span></span>

#### <a name="order"></a><span data-ttu-id="312d6-150">Volgorde</span><span class="sxs-lookup"><span data-stu-id="312d6-150">Order</span></span>

<span data-ttu-id="312d6-151">In deze tabel worden de [ordereigenschappen](order-resources.md) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="312d6-151">This table describes the [Order](order-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="312d6-152">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="312d6-152">Property</span></span>             | <span data-ttu-id="312d6-153">Type</span><span class="sxs-lookup"><span data-stu-id="312d6-153">Type</span></span>                        | <span data-ttu-id="312d6-154">Vereist</span><span class="sxs-lookup"><span data-stu-id="312d6-154">Required</span></span>                        | <span data-ttu-id="312d6-155">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="312d6-155">Description</span></span>                                                                   |
|----------------------|-----------------------------|---------------------------------|-------------------------------------------------------------------------------|
| <span data-ttu-id="312d6-156">id</span><span class="sxs-lookup"><span data-stu-id="312d6-156">id</span></span>                   | <span data-ttu-id="312d6-157">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-157">string</span></span>                      | <span data-ttu-id="312d6-158">No</span><span class="sxs-lookup"><span data-stu-id="312d6-158">No</span></span>                              | <span data-ttu-id="312d6-159">Een order-id die wordt opgegeven wanneer de order is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="312d6-159">An order identifier that is supplied upon successful creation of the order.</span></span>   |
| <span data-ttu-id="312d6-160">referenceCustomerId</span><span class="sxs-lookup"><span data-stu-id="312d6-160">referenceCustomerId</span></span>  | <span data-ttu-id="312d6-161">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-161">string</span></span>                      | <span data-ttu-id="312d6-162">No</span><span class="sxs-lookup"><span data-stu-id="312d6-162">No</span></span>                              | <span data-ttu-id="312d6-163">De klant-id.</span><span class="sxs-lookup"><span data-stu-id="312d6-163">The customer identifier.</span></span> |
| <span data-ttu-id="312d6-164">billingCycle</span><span class="sxs-lookup"><span data-stu-id="312d6-164">billingCycle</span></span>         | <span data-ttu-id="312d6-165">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-165">string</span></span>                      | <span data-ttu-id="312d6-166">No</span><span class="sxs-lookup"><span data-stu-id="312d6-166">No</span></span>                              | <span data-ttu-id="312d6-167">Geeft de frequentie aan waarmee de partner wordt gefactureerd voor deze bestelling.</span><span class="sxs-lookup"><span data-stu-id="312d6-167">Indicates the frequency with which the partner is billed for this order.</span></span> <span data-ttu-id="312d6-168">Ondersteunde waarden zijn de namen van leden in [BillingCycleType.](product-resources.md#billingcycletype)</span><span class="sxs-lookup"><span data-stu-id="312d6-168">Supported values are the member names found in [BillingCycleType](product-resources.md#billingcycletype).</span></span> <span data-ttu-id="312d6-169">De standaardwaarde is 'Maandelijks' of 'OneTime' bij het maken van de order.</span><span class="sxs-lookup"><span data-stu-id="312d6-169">The default is "Monthly" or "OneTime" at order creation.</span></span> <span data-ttu-id="312d6-170">Dit veld wordt toegepast wanneer de order is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="312d6-170">This field is applied upon successful creation of the order.</span></span> |
| <span data-ttu-id="312d6-171">lineItems</span><span class="sxs-lookup"><span data-stu-id="312d6-171">lineItems</span></span>            | <span data-ttu-id="312d6-172">matrix van [OrderLineItem-resources](order-resources.md#orderlineitem)</span><span class="sxs-lookup"><span data-stu-id="312d6-172">array of [OrderLineItem](order-resources.md#orderlineitem) resources</span></span> | <span data-ttu-id="312d6-173">Ja</span><span class="sxs-lookup"><span data-stu-id="312d6-173">Yes</span></span>      | <span data-ttu-id="312d6-174">Een gespecificeerde lijst met aanbiedingen die de klant aanschaft, inclusief de hoeveelheid.</span><span class="sxs-lookup"><span data-stu-id="312d6-174">An itemized list of the offers the customer is purchasing including the quantity.</span></span>        |
| <span data-ttu-id="312d6-175">currencyCode</span><span class="sxs-lookup"><span data-stu-id="312d6-175">currencyCode</span></span>         | <span data-ttu-id="312d6-176">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-176">string</span></span>                      | <span data-ttu-id="312d6-177">No</span><span class="sxs-lookup"><span data-stu-id="312d6-177">No</span></span>                              | <span data-ttu-id="312d6-178">Alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="312d6-178">Read-only.</span></span> <span data-ttu-id="312d6-179">De valuta die wordt gebruikt bij het plaatsen van de order.</span><span class="sxs-lookup"><span data-stu-id="312d6-179">The currency used when placing the order.</span></span> <span data-ttu-id="312d6-180">Toegepast wanneer de order is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="312d6-180">Applied upon successful creation of the order.</span></span>           |
| <span data-ttu-id="312d6-181">creationDate</span><span class="sxs-lookup"><span data-stu-id="312d6-181">creationDate</span></span>         | <span data-ttu-id="312d6-182">datum/tijd</span><span class="sxs-lookup"><span data-stu-id="312d6-182">datetime</span></span>                    | <span data-ttu-id="312d6-183">Nee</span><span class="sxs-lookup"><span data-stu-id="312d6-183">No</span></span>                              | <span data-ttu-id="312d6-184">Alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="312d6-184">Read-only.</span></span> <span data-ttu-id="312d6-185">De datum waarop de order is gemaakt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="312d6-185">The date the order was created, in date-time format.</span></span> <span data-ttu-id="312d6-186">Toegepast wanneer de order is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="312d6-186">Applied upon successful creation of the order.</span></span>                                   |
| <span data-ttu-id="312d6-187">status</span><span class="sxs-lookup"><span data-stu-id="312d6-187">status</span></span>               | <span data-ttu-id="312d6-188">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-188">string</span></span>                      | <span data-ttu-id="312d6-189">No</span><span class="sxs-lookup"><span data-stu-id="312d6-189">No</span></span>                              | <span data-ttu-id="312d6-190">Alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="312d6-190">Read-only.</span></span> <span data-ttu-id="312d6-191">De status van de bestelling.</span><span class="sxs-lookup"><span data-stu-id="312d6-191">The status of the order.</span></span>  <span data-ttu-id="312d6-192">Ondersteunde waarden zijn de ledennamen in [OrderStatus](order-resources.md#orderstatus).</span><span class="sxs-lookup"><span data-stu-id="312d6-192">Supported values are the member names found in [OrderStatus](order-resources.md#orderstatus).</span></span>        |
| <span data-ttu-id="312d6-193">Verwijzigingen</span><span class="sxs-lookup"><span data-stu-id="312d6-193">links</span></span>                | [<span data-ttu-id="312d6-194">OrderLinks</span><span class="sxs-lookup"><span data-stu-id="312d6-194">OrderLinks</span></span>](utility-resources.md#resourcelinks)              | <span data-ttu-id="312d6-195">Nee</span><span class="sxs-lookup"><span data-stu-id="312d6-195">No</span></span>                              | <span data-ttu-id="312d6-196">De resourcekoppelingen die overeenkomen met de Order.</span><span class="sxs-lookup"><span data-stu-id="312d6-196">The resource links corresponding to the Order.</span></span> |
| <span data-ttu-id="312d6-197">kenmerken</span><span class="sxs-lookup"><span data-stu-id="312d6-197">attributes</span></span>           | [<span data-ttu-id="312d6-198">ResourceAttributes</span><span class="sxs-lookup"><span data-stu-id="312d6-198">ResourceAttributes</span></span>](utility-resources.md#resourceattributes) | <span data-ttu-id="312d6-199">Nee</span><span class="sxs-lookup"><span data-stu-id="312d6-199">No</span></span>                              | <span data-ttu-id="312d6-200">De metagegevenskenmerken die overeenkomen met de volgorde.</span><span class="sxs-lookup"><span data-stu-id="312d6-200">The metadata attributes corresponding to the Order.</span></span> |

#### <a name="orderlineitem"></a><span data-ttu-id="312d6-201">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="312d6-201">OrderLineItem</span></span>

<span data-ttu-id="312d6-202">In deze tabel worden de [eigenschappen van OrderLineItem](order-resources.md#orderlineitem) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="312d6-202">This table describes the [OrderLineItem](order-resources.md#orderlineitem) properties in the request body.</span></span>

>[!NOTE]
><span data-ttu-id="312d6-203">De partnerIdOnRecord mag alleen worden opgegeven wanneer een indirecte provider een bestelling plaatst namens een indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="312d6-203">The partnerIdOnRecord should only be provided when an indirect provider places an order on behalf of an indirect reseller.</span></span> <span data-ttu-id="312d6-204">Deze wordt gebruikt voor het opslaan van Microsoft Partner Network id van de indirecte reseller (nooit de id van de indirecte provider).</span><span class="sxs-lookup"><span data-stu-id="312d6-204">It's used to store the Microsoft Partner Network ID of the indirect reseller only (never the ID of the indirect provider).</span></span>

| <span data-ttu-id="312d6-205">Naam</span><span class="sxs-lookup"><span data-stu-id="312d6-205">Name</span></span>                 | <span data-ttu-id="312d6-206">Type</span><span class="sxs-lookup"><span data-stu-id="312d6-206">Type</span></span>   | <span data-ttu-id="312d6-207">Vereist</span><span class="sxs-lookup"><span data-stu-id="312d6-207">Required</span></span> | <span data-ttu-id="312d6-208">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="312d6-208">Description</span></span>                                                                                                                                                                                                                                |
|----------------------|--------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="312d6-209">lineItemNumber</span><span class="sxs-lookup"><span data-stu-id="312d6-209">lineItemNumber</span></span>       | <span data-ttu-id="312d6-210">int</span><span class="sxs-lookup"><span data-stu-id="312d6-210">int</span></span>    | <span data-ttu-id="312d6-211">Ja</span><span class="sxs-lookup"><span data-stu-id="312d6-211">Yes</span></span>      | <span data-ttu-id="312d6-212">Elk regelitem in de verzameling krijgt een uniek regelnummer, dat wordt geteld van 0 tot count-1.</span><span class="sxs-lookup"><span data-stu-id="312d6-212">Each line item in the collection gets a unique line number, counting up from 0 to count-1.</span></span>                                                                                                                                                 |
| <span data-ttu-id="312d6-213">offerId</span><span class="sxs-lookup"><span data-stu-id="312d6-213">offerId</span></span>              | <span data-ttu-id="312d6-214">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-214">string</span></span> | <span data-ttu-id="312d6-215">Ja</span><span class="sxs-lookup"><span data-stu-id="312d6-215">Yes</span></span>      | <span data-ttu-id="312d6-216">De aanbiedings-id.</span><span class="sxs-lookup"><span data-stu-id="312d6-216">The offer identifier.</span></span>                                                                                                                                                                                                                      |
| <span data-ttu-id="312d6-217">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="312d6-217">subscriptionId</span></span>       | <span data-ttu-id="312d6-218">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-218">string</span></span> | <span data-ttu-id="312d6-219">No</span><span class="sxs-lookup"><span data-stu-id="312d6-219">No</span></span>       | <span data-ttu-id="312d6-220">De abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="312d6-220">The subscription identifier.</span></span>                                                                                                                                                                                                               |
| <span data-ttu-id="312d6-221">parentSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="312d6-221">parentSubscriptionId</span></span> | <span data-ttu-id="312d6-222">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-222">string</span></span> | <span data-ttu-id="312d6-223">No</span><span class="sxs-lookup"><span data-stu-id="312d6-223">No</span></span>       | <span data-ttu-id="312d6-224">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="312d6-224">Optional.</span></span> <span data-ttu-id="312d6-225">De id van het bovenliggende abonnement in een invoegaanbieding.</span><span class="sxs-lookup"><span data-stu-id="312d6-225">The ID of the parent subscription in an add-on offer.</span></span> <span data-ttu-id="312d6-226">Alleen van toepassing op PATCH.</span><span class="sxs-lookup"><span data-stu-id="312d6-226">Applies to PATCH only.</span></span>                                                                                                                                                     |
| <span data-ttu-id="312d6-227">Friendlyname</span><span class="sxs-lookup"><span data-stu-id="312d6-227">friendlyName</span></span>         | <span data-ttu-id="312d6-228">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-228">string</span></span> | <span data-ttu-id="312d6-229">No</span><span class="sxs-lookup"><span data-stu-id="312d6-229">No</span></span>       | <span data-ttu-id="312d6-230">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="312d6-230">Optional.</span></span> <span data-ttu-id="312d6-231">De gebruiksvriendelijke naam voor het abonnement dat is gedefinieerd door de partner om ondubbelzinnig te maken.</span><span class="sxs-lookup"><span data-stu-id="312d6-231">The friendly name for the subscription defined by the partner to help disambiguate.</span></span>                                                                                                                                              |
| <span data-ttu-id="312d6-232">quantity</span><span class="sxs-lookup"><span data-stu-id="312d6-232">quantity</span></span>             | <span data-ttu-id="312d6-233">int</span><span class="sxs-lookup"><span data-stu-id="312d6-233">int</span></span>    | <span data-ttu-id="312d6-234">Ja</span><span class="sxs-lookup"><span data-stu-id="312d6-234">Yes</span></span>      | <span data-ttu-id="312d6-235">Het aantal licenties voor een abonnement op basis van een licentie.</span><span class="sxs-lookup"><span data-stu-id="312d6-235">The number of licenses for a license-based subscription.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="312d6-236">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="312d6-236">partnerIdOnRecord</span></span>    | <span data-ttu-id="312d6-237">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-237">string</span></span> | <span data-ttu-id="312d6-238">No</span><span class="sxs-lookup"><span data-stu-id="312d6-238">No</span></span>       | <span data-ttu-id="312d6-239">Wanneer een indirecte provider een bestelling plaatst namens een indirecte reseller, vult u dit veld in met de MPN-id van de **indirecte reseller** (nooit de id van de indirecte provider).</span><span class="sxs-lookup"><span data-stu-id="312d6-239">When an indirect provider places an order on behalf of an indirect reseller, populate this field with the MPN ID of the **indirect reseller only** (never the ID of the indirect provider).</span></span> <span data-ttu-id="312d6-240">Dit zorgt voor de juiste boekhouding voor incentives.</span><span class="sxs-lookup"><span data-stu-id="312d6-240">This ensures proper accounting for incentives.</span></span> |
| <span data-ttu-id="312d6-241">provisioningContext</span><span class="sxs-lookup"><span data-stu-id="312d6-241">provisioningContext</span></span>  | <span data-ttu-id="312d6-242">Woordenlijst<tekenreeks, tekenreeks></span><span class="sxs-lookup"><span data-stu-id="312d6-242">Dictionary<string, string></span></span>                | <span data-ttu-id="312d6-243">Nee</span><span class="sxs-lookup"><span data-stu-id="312d6-243">No</span></span>       |  <span data-ttu-id="312d6-244">Informatie die vereist is voor het inrichten van sommige items in de catalogus.</span><span class="sxs-lookup"><span data-stu-id="312d6-244">Information required for provisioning for some items in the catalog.</span></span> <span data-ttu-id="312d6-245">De eigenschap provisioningVariables in een SKU geeft aan welke eigenschappen vereist zijn voor specifieke items in de catalogus.</span><span class="sxs-lookup"><span data-stu-id="312d6-245">The provisioningVariables property in a SKU indicates which properties are required for specific items in the catalog.</span></span>                  |
| <span data-ttu-id="312d6-246">Verwijzigingen</span><span class="sxs-lookup"><span data-stu-id="312d6-246">links</span></span>                | [<span data-ttu-id="312d6-247">OrderLineItemLinks</span><span class="sxs-lookup"><span data-stu-id="312d6-247">OrderLineItemLinks</span></span>](order-resources.md#orderlineitemlinks) | <span data-ttu-id="312d6-248">Nee</span><span class="sxs-lookup"><span data-stu-id="312d6-248">No</span></span>       |  <span data-ttu-id="312d6-249">Alleen-lezen.</span><span class="sxs-lookup"><span data-stu-id="312d6-249">Read-only.</span></span> <span data-ttu-id="312d6-250">De resourcekoppelingen die overeenkomen met het regelitem Order.</span><span class="sxs-lookup"><span data-stu-id="312d6-250">The resource links corresponding to the Order line item.</span></span>  |
| <span data-ttu-id="312d6-251">kenmerken</span><span class="sxs-lookup"><span data-stu-id="312d6-251">attributes</span></span>           | [<span data-ttu-id="312d6-252">ResourceAttributes</span><span class="sxs-lookup"><span data-stu-id="312d6-252">ResourceAttributes</span></span>](utility-resources.md#resourceattributes) | <span data-ttu-id="312d6-253">Nee</span><span class="sxs-lookup"><span data-stu-id="312d6-253">No</span></span>       | <span data-ttu-id="312d6-254">De metagegevenskenmerken die overeenkomen met de OrderLineItem.</span><span class="sxs-lookup"><span data-stu-id="312d6-254">The metadata attributes corresponding to the OrderLineItem.</span></span> |
| <span data-ttu-id="312d6-255">renewsTo</span><span class="sxs-lookup"><span data-stu-id="312d6-255">renewsTo</span></span>             | <span data-ttu-id="312d6-256">Matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="312d6-256">Array of objects</span></span>                          | <span data-ttu-id="312d6-257">Nee</span><span class="sxs-lookup"><span data-stu-id="312d6-257">No</span></span>    |<span data-ttu-id="312d6-258">Een matrix van [RenewsTo-resources.](order-resources.md#renewsto)</span><span class="sxs-lookup"><span data-stu-id="312d6-258">An array of [RenewsTo](order-resources.md#renewsto) resources.</span></span>                                                                            |

##### <a name="renewsto"></a><span data-ttu-id="312d6-259">RenewsTo</span><span class="sxs-lookup"><span data-stu-id="312d6-259">RenewsTo</span></span>

<span data-ttu-id="312d6-260">In deze tabel worden de [renewsTo-eigenschappen](order-resources.md#renewsto) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="312d6-260">This table describes the [RenewsTo](order-resources.md#renewsto) properties in the request body.</span></span>

| <span data-ttu-id="312d6-261">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="312d6-261">Property</span></span>              | <span data-ttu-id="312d6-262">Type</span><span class="sxs-lookup"><span data-stu-id="312d6-262">Type</span></span>             | <span data-ttu-id="312d6-263">Vereist</span><span class="sxs-lookup"><span data-stu-id="312d6-263">Required</span></span>        | <span data-ttu-id="312d6-264">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="312d6-264">Description</span></span> |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="312d6-265">termDuration</span><span class="sxs-lookup"><span data-stu-id="312d6-265">termDuration</span></span>          | <span data-ttu-id="312d6-266">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="312d6-266">string</span></span>           | <span data-ttu-id="312d6-267">No</span><span class="sxs-lookup"><span data-stu-id="312d6-267">No</span></span>              | <span data-ttu-id="312d6-268">Een ISO 8601-weergave van de duur van de verlengingsperiode.</span><span class="sxs-lookup"><span data-stu-id="312d6-268">An ISO 8601 representation of the renewal term's duration.</span></span> <span data-ttu-id="312d6-269">De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar).</span><span class="sxs-lookup"><span data-stu-id="312d6-269">The current supported values are **P1M** (1 month) and **P1Y** (1 year).</span></span> |

### <a name="request-example"></a><span data-ttu-id="312d6-270">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="312d6-270">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="312d6-271">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="312d6-271">REST response</span></span>

<span data-ttu-id="312d6-272">Als dit lukt, retourneert de methode een [Order-resource](order-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="312d6-272">If successful, the method returns an [Order](order-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="312d6-273">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="312d6-273">Response success and error codes</span></span>

<span data-ttu-id="312d6-274">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="312d6-274">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="312d6-275">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="312d6-275">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="312d6-276">Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="312d6-276">For the full list, see [Partner Center error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="312d6-277">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="312d6-277">Response example</span></span>

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
