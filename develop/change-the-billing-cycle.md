---
title: De factureringscyclus wijzigen
description: Meer informatie over hoe u een klant abonnement bijwerkt naar een maandelijks of jaarlijks factuurt met behulp van partner Center-Api's. U kunt dit ook doen via het dash board van de partner centrum.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: 8a2879db061ced799e29d84e71be5b1259b07689
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767624"
---
# <a name="change-a-customer-subscription-billing-cycle"></a><span data-ttu-id="2df37-104">Een facturerings cyclus voor een klant abonnement wijzigen</span><span class="sxs-lookup"><span data-stu-id="2df37-104">Change a customer subscription billing cycle</span></span>

<span data-ttu-id="2df37-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="2df37-105">**Applies to:**</span></span>

- <span data-ttu-id="2df37-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="2df37-106">Partner Center</span></span>
- <span data-ttu-id="2df37-107">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="2df37-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="2df37-108">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="2df37-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="2df37-109">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2df37-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2df37-110">Hiermee wordt een [bestelling](order-resources.md) bijgewerkt van maandelijks naar jaar facturering of van jaarlijkse naar maandelijkse facturering.</span><span class="sxs-lookup"><span data-stu-id="2df37-110">Updates an [Order](order-resources.md) from monthly to annual billing or from annual to monthly billing.</span></span>

<span data-ttu-id="2df37-111">In het dash board van de partner centrum kan deze bewerking worden uitgevoerd door te navigeren naar de pagina met abonnements gegevens van een klant.</span><span class="sxs-lookup"><span data-stu-id="2df37-111">In the Partner Center dashboard, this operation can be performed by navigating to a customer's subscription details page.</span></span> <span data-ttu-id="2df37-112">Zodra dit het geval is, ziet u een optie voor het definiëren van de huidige facturerings cyclus voor het abonnement, met de mogelijkheid om deze te wijzigen en in te dienen.</span><span class="sxs-lookup"><span data-stu-id="2df37-112">Once there, you will see an option defining the current billing cycle for the subscription with the ability to change and submit it.</span></span>

<span data-ttu-id="2df37-113">**Buiten het bereik** van dit artikel:</span><span class="sxs-lookup"><span data-stu-id="2df37-113">**Out of scope** for this article:</span></span>

- <span data-ttu-id="2df37-114">De facturerings cyclus voor experimenten wijzigen</span><span class="sxs-lookup"><span data-stu-id="2df37-114">Changing the billing cycle for trials</span></span>
- <span data-ttu-id="2df37-115">Het wijzigen van de facturerings cycli voor aanbiedingen die geen jaar zijn (maandelijks, 6 jaar) & Azure-abonnementen</span><span class="sxs-lookup"><span data-stu-id="2df37-115">Changing the billing cycles for any non-annual term offers (monthly, 6-year) & Azure subscriptions</span></span>
- <span data-ttu-id="2df37-116">De facturerings cycli voor inactieve abonnementen wijzigen</span><span class="sxs-lookup"><span data-stu-id="2df37-116">Changing the billing cycles for inactive subscriptions</span></span>
- <span data-ttu-id="2df37-117">Facturerings cycli voor micro soft onlineservices op licenties gebaseerde abonnementen wijzigen</span><span class="sxs-lookup"><span data-stu-id="2df37-117">Changing billing cycles for Microsoft online services license-based subscriptions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2df37-118">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2df37-118">Prerequisites</span></span>

- <span data-ttu-id="2df37-119">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2df37-119">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2df37-120">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="2df37-120">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="2df37-121">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2df37-121">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="2df37-122">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="2df37-122">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="2df37-123">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="2df37-123">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="2df37-124">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="2df37-124">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="2df37-125">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="2df37-125">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="2df37-126">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="2df37-126">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="2df37-127">Een order-ID.</span><span class="sxs-lookup"><span data-stu-id="2df37-127">An order ID.</span></span>

## <a name="c"></a><span data-ttu-id="2df37-128">C\#</span><span class="sxs-lookup"><span data-stu-id="2df37-128">C\#</span></span>

<span data-ttu-id="2df37-129">Als u de frequentie van de facturerings cyclus wilt wijzigen, werkt u de eigenschap [**order. BillingCycle**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.billingcycle#Microsoft_Store_PartnerCenter_Models_Orders_Order_BillingCycle) bij.</span><span class="sxs-lookup"><span data-stu-id="2df37-129">To change the frequency of the billing cycle, update the [**Order.BillingCycle**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.billingcycle#Microsoft_Store_PartnerCenter_Models_Orders_Order_BillingCycle) property.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string offerId;
// string orderId;

var order = new Order()
{
    ReferenceCustomerId = customerId,
    BillingCycle = BillingCycleType.Annual,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            LineItemNumber = 0,
            OfferId = offerId,
            SubscriptionId = "69829602-C219-40FD-A3D5-4150FCA41A19",
            Quantity = 1
        }
    }
};

var createdOrder = partnerOperations.Customers.ById(customerId).Orders.ById(orderId).Patch(order);
```

## <a name="rest-request"></a><span data-ttu-id="2df37-130">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="2df37-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2df37-131">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2df37-131">Request syntax</span></span>

| <span data-ttu-id="2df37-132">Methode</span><span class="sxs-lookup"><span data-stu-id="2df37-132">Method</span></span>    | <span data-ttu-id="2df37-133">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="2df37-133">Request URI</span></span>                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="2df37-134">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="2df37-134">**PATCH**</span></span> | <span data-ttu-id="2df37-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/orders/{order-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="2df37-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="2df37-136">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="2df37-136">URI parameter</span></span>

<span data-ttu-id="2df37-137">Deze tabel bevat de vereiste query parameter voor het wijzigen van de hoeveelheid van het abonnement.</span><span class="sxs-lookup"><span data-stu-id="2df37-137">This table lists the required query parameter to change the quantity of the subscription.</span></span>

| <span data-ttu-id="2df37-138">Naam</span><span class="sxs-lookup"><span data-stu-id="2df37-138">Name</span></span>                   | <span data-ttu-id="2df37-139">Type</span><span class="sxs-lookup"><span data-stu-id="2df37-139">Type</span></span> | <span data-ttu-id="2df37-140">Vereist</span><span class="sxs-lookup"><span data-stu-id="2df37-140">Required</span></span> | <span data-ttu-id="2df37-141">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2df37-141">Description</span></span>                                                          |
|------------------------|------|----------|----------------------------------------------------------------------|
| <span data-ttu-id="2df37-142">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="2df37-142">**customer-tenant-id**</span></span> | <span data-ttu-id="2df37-143">GUID</span><span class="sxs-lookup"><span data-stu-id="2df37-143">GUID</span></span> |    <span data-ttu-id="2df37-144">J</span><span class="sxs-lookup"><span data-stu-id="2df37-144">Y</span></span>     | <span data-ttu-id="2df37-145">Een in de GUID ingedeelde **klant-Tenant-id** waarmee de klant wordt geïdentificeerd</span><span class="sxs-lookup"><span data-stu-id="2df37-145">A GUID formatted **customer-tenant-id** that identifies the customer</span></span> |
| <span data-ttu-id="2df37-146">**order-id**</span><span class="sxs-lookup"><span data-stu-id="2df37-146">**order-id**</span></span>           | <span data-ttu-id="2df37-147">GUID</span><span class="sxs-lookup"><span data-stu-id="2df37-147">GUID</span></span> |    <span data-ttu-id="2df37-148">J</span><span class="sxs-lookup"><span data-stu-id="2df37-148">Y</span></span>     | <span data-ttu-id="2df37-149">De order-id</span><span class="sxs-lookup"><span data-stu-id="2df37-149">The order identifier</span></span>                                                 |

### <a name="request-headers"></a><span data-ttu-id="2df37-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="2df37-150">Request headers</span></span>

<span data-ttu-id="2df37-151">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="2df37-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2df37-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="2df37-152">Request body</span></span>

<span data-ttu-id="2df37-153">In de volgende tabellen worden de eigenschappen in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="2df37-153">The following tables describe the properties in the request body.</span></span>

### <a name="order"></a><span data-ttu-id="2df37-154">Volgorde</span><span class="sxs-lookup"><span data-stu-id="2df37-154">Order</span></span>

| <span data-ttu-id="2df37-155">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2df37-155">Property</span></span>           | <span data-ttu-id="2df37-156">Type</span><span class="sxs-lookup"><span data-stu-id="2df37-156">Type</span></span>             | <span data-ttu-id="2df37-157">Vereist</span><span class="sxs-lookup"><span data-stu-id="2df37-157">Required</span></span> | <span data-ttu-id="2df37-158">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2df37-158">Description</span></span>                                                                |
|--------------------|------------------|----------|----------------------------------------------------------------------------|
| <span data-ttu-id="2df37-159">Id</span><span class="sxs-lookup"><span data-stu-id="2df37-159">Id</span></span>                 | <span data-ttu-id="2df37-160">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2df37-160">string</span></span>           |    <span data-ttu-id="2df37-161">N</span><span class="sxs-lookup"><span data-stu-id="2df37-161">N</span></span>     | <span data-ttu-id="2df37-162">Een order-id die is opgegeven bij het maken van de order</span><span class="sxs-lookup"><span data-stu-id="2df37-162">An order identifier that is supplied upon successful creation of the order</span></span> |
|<span data-ttu-id="2df37-163">ReferenceCustomerId</span><span class="sxs-lookup"><span data-stu-id="2df37-163">ReferenceCustomerId</span></span> | <span data-ttu-id="2df37-164">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2df37-164">string</span></span>           |    <span data-ttu-id="2df37-165">J</span><span class="sxs-lookup"><span data-stu-id="2df37-165">Y</span></span>     | <span data-ttu-id="2df37-166">De klant-id</span><span class="sxs-lookup"><span data-stu-id="2df37-166">The customer identifier</span></span>                                                    |
| <span data-ttu-id="2df37-167">BillingCycle</span><span class="sxs-lookup"><span data-stu-id="2df37-167">BillingCycle</span></span>       | <span data-ttu-id="2df37-168">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2df37-168">string</span></span>           |    <span data-ttu-id="2df37-169">J</span><span class="sxs-lookup"><span data-stu-id="2df37-169">Y</span></span>     | <span data-ttu-id="2df37-170">Hiermee wordt de frequentie aangegeven waarmee de partner voor deze order wordt gefactureerd.</span><span class="sxs-lookup"><span data-stu-id="2df37-170">Indicates the frequency with which the partner is billed for this order.</span></span> <span data-ttu-id="2df37-171">Ondersteunde waarden zijn de lidnamen in [BillingCycleType](product-resources.md#billingcycletype).</span><span class="sxs-lookup"><span data-stu-id="2df37-171">Supported values are the member names found in [BillingCycleType](product-resources.md#billingcycletype).</span></span> |
| <span data-ttu-id="2df37-172">Regel items</span><span class="sxs-lookup"><span data-stu-id="2df37-172">LineItems</span></span>          | <span data-ttu-id="2df37-173">matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="2df37-173">array of objects</span></span> |    <span data-ttu-id="2df37-174">J</span><span class="sxs-lookup"><span data-stu-id="2df37-174">Y</span></span>     | <span data-ttu-id="2df37-175">Een matrix met [OrderLineItem](#orderlineitem) -resources</span><span class="sxs-lookup"><span data-stu-id="2df37-175">An array of [OrderLineItem](#orderlineitem) resources</span></span>                      |
| <span data-ttu-id="2df37-176">CreationDate</span><span class="sxs-lookup"><span data-stu-id="2df37-176">CreationDate</span></span>       | <span data-ttu-id="2df37-177">datum/tijd</span><span class="sxs-lookup"><span data-stu-id="2df37-177">datetime</span></span>         |    <span data-ttu-id="2df37-178">N</span><span class="sxs-lookup"><span data-stu-id="2df37-178">N</span></span>     | <span data-ttu-id="2df37-179">De datum waarop de order is gemaakt, in datum-tijd notatie</span><span class="sxs-lookup"><span data-stu-id="2df37-179">The date the order was created, in date-time format</span></span>                        |
| <span data-ttu-id="2df37-180">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2df37-180">Attributes</span></span>         | <span data-ttu-id="2df37-181">Object</span><span class="sxs-lookup"><span data-stu-id="2df37-181">Object</span></span>           |    <span data-ttu-id="2df37-182">N</span><span class="sxs-lookup"><span data-stu-id="2df37-182">N</span></span>     | <span data-ttu-id="2df37-183">Bevat "object type": "OrderLineItem"</span><span class="sxs-lookup"><span data-stu-id="2df37-183">Contains "ObjectType": "OrderLineItem"</span></span>                                     |

### <a name="orderlineitem"></a><span data-ttu-id="2df37-184">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="2df37-184">OrderLineItem</span></span>

| <span data-ttu-id="2df37-185">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="2df37-185">Property</span></span>             | <span data-ttu-id="2df37-186">Type</span><span class="sxs-lookup"><span data-stu-id="2df37-186">Type</span></span>   | <span data-ttu-id="2df37-187">Vereist</span><span class="sxs-lookup"><span data-stu-id="2df37-187">Required</span></span> | <span data-ttu-id="2df37-188">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2df37-188">Description</span></span>                                                                        |
|----------------------|--------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="2df37-189">LineItemNumber</span><span class="sxs-lookup"><span data-stu-id="2df37-189">LineItemNumber</span></span>       | <span data-ttu-id="2df37-190">getal</span><span class="sxs-lookup"><span data-stu-id="2df37-190">number</span></span> |    <span data-ttu-id="2df37-191">J</span><span class="sxs-lookup"><span data-stu-id="2df37-191">Y</span></span>     | <span data-ttu-id="2df37-192">Het nummer van het regel item, te beginnen met 0</span><span class="sxs-lookup"><span data-stu-id="2df37-192">The line item number, starting with 0</span></span>                                              |
| <span data-ttu-id="2df37-193">OfferId</span><span class="sxs-lookup"><span data-stu-id="2df37-193">OfferId</span></span>              | <span data-ttu-id="2df37-194">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2df37-194">string</span></span> |    <span data-ttu-id="2df37-195">J</span><span class="sxs-lookup"><span data-stu-id="2df37-195">Y</span></span>     | <span data-ttu-id="2df37-196">De ID van de aanbieding</span><span class="sxs-lookup"><span data-stu-id="2df37-196">The ID of the offer</span></span>                                                                |
| <span data-ttu-id="2df37-197">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="2df37-197">SubscriptionId</span></span>       | <span data-ttu-id="2df37-198">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2df37-198">string</span></span> |    <span data-ttu-id="2df37-199">J</span><span class="sxs-lookup"><span data-stu-id="2df37-199">Y</span></span>     | <span data-ttu-id="2df37-200">De ID van het abonnement</span><span class="sxs-lookup"><span data-stu-id="2df37-200">The ID of the subscription</span></span>                                                         |
| <span data-ttu-id="2df37-201">FriendlyName</span><span class="sxs-lookup"><span data-stu-id="2df37-201">FriendlyName</span></span>         | <span data-ttu-id="2df37-202">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2df37-202">string</span></span> |    <span data-ttu-id="2df37-203">N</span><span class="sxs-lookup"><span data-stu-id="2df37-203">N</span></span>     | <span data-ttu-id="2df37-204">De beschrijvende naam voor het abonnement dat is gedefinieerd door de partner om dubbel zinnigheid te helpen</span><span class="sxs-lookup"><span data-stu-id="2df37-204">The friendly name for the subscription defined by the partner to help disambiguate</span></span> |
| <span data-ttu-id="2df37-205">Aantal</span><span class="sxs-lookup"><span data-stu-id="2df37-205">Quantity</span></span>             | <span data-ttu-id="2df37-206">getal</span><span class="sxs-lookup"><span data-stu-id="2df37-206">number</span></span> |    <span data-ttu-id="2df37-207">J</span><span class="sxs-lookup"><span data-stu-id="2df37-207">Y</span></span>     | <span data-ttu-id="2df37-208">Het aantal licenties of exemplaren</span><span class="sxs-lookup"><span data-stu-id="2df37-208">The number of licenses or instances</span></span>                                                |
| <span data-ttu-id="2df37-209">PartnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="2df37-209">PartnerIdOnRecord</span></span>    | <span data-ttu-id="2df37-210">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2df37-210">string</span></span> |    <span data-ttu-id="2df37-211">N</span><span class="sxs-lookup"><span data-stu-id="2df37-211">N</span></span>     | <span data-ttu-id="2df37-212">De MPN-ID van de partner van de record</span><span class="sxs-lookup"><span data-stu-id="2df37-212">The MPN ID of the partner of record</span></span>                                                |
| <span data-ttu-id="2df37-213">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="2df37-213">Attributes</span></span>           | <span data-ttu-id="2df37-214">Object</span><span class="sxs-lookup"><span data-stu-id="2df37-214">Object</span></span> |    <span data-ttu-id="2df37-215">N</span><span class="sxs-lookup"><span data-stu-id="2df37-215">N</span></span>     | <span data-ttu-id="2df37-216">Bevat "object type": "OrderLineItem"</span><span class="sxs-lookup"><span data-stu-id="2df37-216">Contains "ObjectType": "OrderLineItem"</span></span>                                             |

### <a name="request-example"></a><span data-ttu-id="2df37-217">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2df37-217">Request example</span></span>

<span data-ttu-id="2df37-218">Bijwerken naar jaarlijkse facturering</span><span class="sxs-lookup"><span data-stu-id="2df37-218">Update to annual billing</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/orders/CF3B0E37-BE0B-4CDD-B584-D1A97D98A922 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 17a2658e-d2cc-439b-a2f0-2aefd9344fbc
MS-CorrelationId: 60efdd24-17ef-4080-9b02-4fc315f916ff
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 414
Expect: 100-continue

{
    "Id": null,
    "ReferenceCustomerId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "BillingCycle" : "Annual",
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "SubscriptionId": "69829602-C219-40FD-A3D5-4150FCA41A19",
            "FriendlyName": "Some friendly name",
            "Quantity": 2,
            "PartnerIdOnRecord": null,
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

## <a name="rest-response"></a><span data-ttu-id="2df37-219">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="2df37-219">REST response</span></span>

<span data-ttu-id="2df37-220">Als dit lukt, retourneert deze methode de bijgewerkte abonnements volgorde in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="2df37-220">If successful, this method returns the updated subscription order in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2df37-221">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="2df37-221">Response success and error codes</span></span>

<span data-ttu-id="2df37-222">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="2df37-222">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2df37-223">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="2df37-223">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2df37-224">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="2df37-224">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2df37-225">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="2df37-225">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1135
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 60efdd24-17ef-4080-9b02-4fc315f916ff
MS-RequestId: 17a2658e-d2cc-439b-a2f0-2aefd9344fbc
MS-CV: WtFy3zI8V0u2lnT9.0
MS-ServerId: 020021921
Date: Wed, 25 Jan 2017 23:01:08 GMT

{
    "id": "cf3b0e37-be0b-4cdd-b584-d1a97d98a922",
    "referenceCustomerId": "4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04",
    "billingCycle": "Annual",
    "lineItems": [{
            "lineItemNumber": 0,
            "offerId": "195416C1-3447-423A-B37B-EE59A99A19C4",
            "subscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
            "friendlyName": "new offer purchase",
            "quantity": 5,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        {
            "lineItemNumber": 1,
            "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "subscriptionId": "69829602-C219-40FD-A3D5-4150FCA41A19",
            "friendlyName": "Some friendly name",
            "quantity": 2,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/69829602-C219-40FD-A3D5-4150FCA41A19",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2017-01-25T14:53:12.093-08:00",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/orders/cf3b0e37-be0b-4cdd-b584-d1a97d98a922",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "etag": "eyJpZCI6ImNmM2IwZTM3LWJlMGItNGNkZC1iNTg0LWQxYTk3ZDk4YTkyMiIsInZlcnNpb24iOjJ9",
        "objectType": "Order"
    }
}
```