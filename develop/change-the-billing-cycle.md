---
title: De factureringscyclus wijzigen
description: Meer informatie over het bijwerken van een klantabonnement naar maandelijkse of jaarlijkse facturering met behulp Partner Center API's. U kunt dit ook doen vanuit het Partner Center dashboard.
ms.date: 05/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: sourishdeb
ms.author: sodeb
ms.openlocfilehash: 435309229e2cb038c936028943f4c2cf27b032a7
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974111"
---
# <a name="change-a-customer-subscription-billing-cycle"></a><span data-ttu-id="8be6c-104">Factureringscyclus van een klantabonnement wijzigen</span><span class="sxs-lookup"><span data-stu-id="8be6c-104">Change a customer subscription billing cycle</span></span>

<span data-ttu-id="8be6c-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="8be6c-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="8be6c-106">Werkt een [order bij](order-resources.md) van maandelijkse naar jaarlijkse facturering of van jaarlijkse naar maandelijkse facturering.</span><span class="sxs-lookup"><span data-stu-id="8be6c-106">Updates an [Order](order-resources.md) from monthly to annual billing or from annual to monthly billing.</span></span>

<span data-ttu-id="8be6c-107">In het Partner Center dashboard kunt u deze bewerking uitvoeren door te navigeren naar de pagina met abonnementsgegevens van een klant.</span><span class="sxs-lookup"><span data-stu-id="8be6c-107">In the Partner Center dashboard, this operation can be performed by navigating to a customer's subscription details page.</span></span> <span data-ttu-id="8be6c-108">Daar ziet u een optie voor het definiëren van de huidige factureringscyclus voor het abonnement met de mogelijkheid om deze te wijzigen en te verzenden.</span><span class="sxs-lookup"><span data-stu-id="8be6c-108">Once there, you will see an option defining the current billing cycle for the subscription with the ability to change and submit it.</span></span>

<span data-ttu-id="8be6c-109">**Buiten het bereik** van dit artikel:</span><span class="sxs-lookup"><span data-stu-id="8be6c-109">**Out of scope** for this article:</span></span>

- <span data-ttu-id="8be6c-110">De factureringscyclus voor proefversies wijzigen</span><span class="sxs-lookup"><span data-stu-id="8be6c-110">Changing the billing cycle for trials</span></span>
- <span data-ttu-id="8be6c-111">De factureringscycli wijzigen voor niet-jaarlijkse termijnaanbiedingen (maandelijks, zes jaar) & Azure-abonnementen</span><span class="sxs-lookup"><span data-stu-id="8be6c-111">Changing the billing cycles for any non-annual term offers (monthly, six-year) & Azure subscriptions</span></span>
- <span data-ttu-id="8be6c-112">De factureringscycli voor inactieve abonnementen wijzigen</span><span class="sxs-lookup"><span data-stu-id="8be6c-112">Changing the billing cycles for inactive subscriptions</span></span>
- <span data-ttu-id="8be6c-113">Factureringscycli wijzigen voor Microsoft onlineservices op licenties gebaseerde abonnementen</span><span class="sxs-lookup"><span data-stu-id="8be6c-113">Changing billing cycles for Microsoft online services license-based subscriptions</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8be6c-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8be6c-114">Prerequisites</span></span>

- <span data-ttu-id="8be6c-115">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8be6c-115">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8be6c-116">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="8be6c-116">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="8be6c-117">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8be6c-117">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8be6c-118">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="8be6c-118">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8be6c-119">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="8be6c-119">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8be6c-120">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="8be6c-120">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8be6c-121">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="8be6c-121">On the customer's Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8be6c-122">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8be6c-122">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="8be6c-123">Een order-id.</span><span class="sxs-lookup"><span data-stu-id="8be6c-123">An order ID.</span></span>

## <a name="c"></a><span data-ttu-id="8be6c-124">C\#</span><span class="sxs-lookup"><span data-stu-id="8be6c-124">C\#</span></span>

<span data-ttu-id="8be6c-125">Als u de frequentie van de factureringscyclus wilt wijzigen, werkt u de [**eigenschap Order.BillingCycle**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.billingcycle#Microsoft_Store_PartnerCenter_Models_Orders_Order_BillingCycle) bij.</span><span class="sxs-lookup"><span data-stu-id="8be6c-125">To change the frequency of the billing cycle, update the [**Order.BillingCycle**](/dotnet/api/microsoft.store.partnercenter.models.orders.order.billingcycle#Microsoft_Store_PartnerCenter_Models_Orders_Order_BillingCycle) property.</span></span>

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

## <a name="rest-request"></a><span data-ttu-id="8be6c-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="8be6c-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8be6c-127">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="8be6c-127">Request syntax</span></span>

| <span data-ttu-id="8be6c-128">Methode</span><span class="sxs-lookup"><span data-stu-id="8be6c-128">Method</span></span>    | <span data-ttu-id="8be6c-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="8be6c-129">Request URI</span></span>                                                                                             |
|-----------|---------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8be6c-130">**Patch**</span><span class="sxs-lookup"><span data-stu-id="8be6c-130">**PATCH**</span></span> | <span data-ttu-id="8be6c-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="8be6c-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="8be6c-132">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="8be6c-132">URI parameter</span></span>

<span data-ttu-id="8be6c-133">Deze tabel bevat de vereiste queryparameter om de hoeveelheid van het abonnement te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="8be6c-133">This table lists the required query parameter to change the quantity of the subscription.</span></span>

| <span data-ttu-id="8be6c-134">Naam</span><span class="sxs-lookup"><span data-stu-id="8be6c-134">Name</span></span>                   | <span data-ttu-id="8be6c-135">Type</span><span class="sxs-lookup"><span data-stu-id="8be6c-135">Type</span></span> | <span data-ttu-id="8be6c-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="8be6c-136">Required</span></span> | <span data-ttu-id="8be6c-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8be6c-137">Description</span></span>                                                          |
|------------------------|------|----------|----------------------------------------------------------------------|
| <span data-ttu-id="8be6c-138">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="8be6c-138">**customer-tenant-id**</span></span> | <span data-ttu-id="8be6c-139">GUID</span><span class="sxs-lookup"><span data-stu-id="8be6c-139">GUID</span></span> |    <span data-ttu-id="8be6c-140">J</span><span class="sxs-lookup"><span data-stu-id="8be6c-140">Y</span></span>     | <span data-ttu-id="8be6c-141">Een met GUID **opgemaakte klant-tenant-id** die de klant identificeert</span><span class="sxs-lookup"><span data-stu-id="8be6c-141">A GUID formatted **customer-tenant-id** that identifies the customer</span></span> |
| <span data-ttu-id="8be6c-142">**order-id**</span><span class="sxs-lookup"><span data-stu-id="8be6c-142">**order-id**</span></span>           | <span data-ttu-id="8be6c-143">GUID</span><span class="sxs-lookup"><span data-stu-id="8be6c-143">GUID</span></span> |    <span data-ttu-id="8be6c-144">J</span><span class="sxs-lookup"><span data-stu-id="8be6c-144">Y</span></span>     | <span data-ttu-id="8be6c-145">De order-id</span><span class="sxs-lookup"><span data-stu-id="8be6c-145">The order identifier</span></span>                                                 |

### <a name="request-headers"></a><span data-ttu-id="8be6c-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="8be6c-146">Request headers</span></span>

<span data-ttu-id="8be6c-147">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="8be6c-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8be6c-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="8be6c-148">Request body</span></span>

<span data-ttu-id="8be6c-149">In de volgende tabellen worden de eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="8be6c-149">The following tables describe the properties in the request body.</span></span>

### <a name="order"></a><span data-ttu-id="8be6c-150">Volgorde</span><span class="sxs-lookup"><span data-stu-id="8be6c-150">Order</span></span>

| <span data-ttu-id="8be6c-151">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8be6c-151">Property</span></span>           | <span data-ttu-id="8be6c-152">Type</span><span class="sxs-lookup"><span data-stu-id="8be6c-152">Type</span></span>             | <span data-ttu-id="8be6c-153">Vereist</span><span class="sxs-lookup"><span data-stu-id="8be6c-153">Required</span></span> | <span data-ttu-id="8be6c-154">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8be6c-154">Description</span></span>                                                                |
|--------------------|------------------|----------|----------------------------------------------------------------------------|
| <span data-ttu-id="8be6c-155">Id</span><span class="sxs-lookup"><span data-stu-id="8be6c-155">Id</span></span>                 | <span data-ttu-id="8be6c-156">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="8be6c-156">string</span></span>           |    <span data-ttu-id="8be6c-157">N</span><span class="sxs-lookup"><span data-stu-id="8be6c-157">N</span></span>     | <span data-ttu-id="8be6c-158">Een order-id die wordt opgegeven wanneer de order is gemaakt</span><span class="sxs-lookup"><span data-stu-id="8be6c-158">An order identifier that is supplied upon successful creation of the order</span></span> |
|<span data-ttu-id="8be6c-159">ReferenceCustomerId</span><span class="sxs-lookup"><span data-stu-id="8be6c-159">ReferenceCustomerId</span></span> | <span data-ttu-id="8be6c-160">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="8be6c-160">string</span></span>           |    <span data-ttu-id="8be6c-161">J</span><span class="sxs-lookup"><span data-stu-id="8be6c-161">Y</span></span>     | <span data-ttu-id="8be6c-162">De klant-id</span><span class="sxs-lookup"><span data-stu-id="8be6c-162">The customer identifier</span></span>                                                    |
| <span data-ttu-id="8be6c-163">BillingCycle</span><span class="sxs-lookup"><span data-stu-id="8be6c-163">BillingCycle</span></span>       | <span data-ttu-id="8be6c-164">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="8be6c-164">string</span></span>           |    <span data-ttu-id="8be6c-165">J</span><span class="sxs-lookup"><span data-stu-id="8be6c-165">Y</span></span>     | <span data-ttu-id="8be6c-166">Geeft de frequentie aan waarmee de partner wordt gefactureerd voor deze bestelling.</span><span class="sxs-lookup"><span data-stu-id="8be6c-166">Indicates the frequency with which the partner is billed for this order.</span></span> <span data-ttu-id="8be6c-167">Ondersteunde waarden zijn de ledennamen in [BillingCycleType.](product-resources.md#billingcycletype)</span><span class="sxs-lookup"><span data-stu-id="8be6c-167">Supported values are the member names found in [BillingCycleType](product-resources.md#billingcycletype).</span></span> |
| <span data-ttu-id="8be6c-168">Regelitems</span><span class="sxs-lookup"><span data-stu-id="8be6c-168">LineItems</span></span>          | <span data-ttu-id="8be6c-169">matrix met objecten</span><span class="sxs-lookup"><span data-stu-id="8be6c-169">array of objects</span></span> |    <span data-ttu-id="8be6c-170">J</span><span class="sxs-lookup"><span data-stu-id="8be6c-170">Y</span></span>     | <span data-ttu-id="8be6c-171">Een matrix met [OrderLineItem-resources](#orderlineitem)</span><span class="sxs-lookup"><span data-stu-id="8be6c-171">An array of [OrderLineItem](#orderlineitem) resources</span></span>                      |
| <span data-ttu-id="8be6c-172">CreationDate</span><span class="sxs-lookup"><span data-stu-id="8be6c-172">CreationDate</span></span>       | <span data-ttu-id="8be6c-173">datum/tijd</span><span class="sxs-lookup"><span data-stu-id="8be6c-173">datetime</span></span>         |    <span data-ttu-id="8be6c-174">N</span><span class="sxs-lookup"><span data-stu-id="8be6c-174">N</span></span>     | <span data-ttu-id="8be6c-175">De datum waarop de order is gemaakt, in datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="8be6c-175">The date the order was created, in date-time format</span></span>                        |
| <span data-ttu-id="8be6c-176">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8be6c-176">Attributes</span></span>         | <span data-ttu-id="8be6c-177">Object</span><span class="sxs-lookup"><span data-stu-id="8be6c-177">Object</span></span>           |    <span data-ttu-id="8be6c-178">N</span><span class="sxs-lookup"><span data-stu-id="8be6c-178">N</span></span>     | <span data-ttu-id="8be6c-179">Bevat "ObjectType": "OrderLineItem"</span><span class="sxs-lookup"><span data-stu-id="8be6c-179">Contains "ObjectType": "OrderLineItem"</span></span>                                     |

### <a name="orderlineitem"></a><span data-ttu-id="8be6c-180">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="8be6c-180">OrderLineItem</span></span>

| <span data-ttu-id="8be6c-181">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="8be6c-181">Property</span></span>             | <span data-ttu-id="8be6c-182">Type</span><span class="sxs-lookup"><span data-stu-id="8be6c-182">Type</span></span>   | <span data-ttu-id="8be6c-183">Vereist</span><span class="sxs-lookup"><span data-stu-id="8be6c-183">Required</span></span> | <span data-ttu-id="8be6c-184">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8be6c-184">Description</span></span>                                                                        |
|----------------------|--------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="8be6c-185">LineItemNumber</span><span class="sxs-lookup"><span data-stu-id="8be6c-185">LineItemNumber</span></span>       | <span data-ttu-id="8be6c-186">getal</span><span class="sxs-lookup"><span data-stu-id="8be6c-186">number</span></span> |    <span data-ttu-id="8be6c-187">J</span><span class="sxs-lookup"><span data-stu-id="8be6c-187">Y</span></span>     | <span data-ttu-id="8be6c-188">Het regelitemnummer, beginnend met 0</span><span class="sxs-lookup"><span data-stu-id="8be6c-188">The line item number, starting with 0</span></span>                                              |
| <span data-ttu-id="8be6c-189">OfferId</span><span class="sxs-lookup"><span data-stu-id="8be6c-189">OfferId</span></span>              | <span data-ttu-id="8be6c-190">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="8be6c-190">string</span></span> |    <span data-ttu-id="8be6c-191">J</span><span class="sxs-lookup"><span data-stu-id="8be6c-191">Y</span></span>     | <span data-ttu-id="8be6c-192">De id van de aanbieding</span><span class="sxs-lookup"><span data-stu-id="8be6c-192">The ID of the offer</span></span>                                                                |
| <span data-ttu-id="8be6c-193">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="8be6c-193">SubscriptionId</span></span>       | <span data-ttu-id="8be6c-194">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="8be6c-194">string</span></span> |    <span data-ttu-id="8be6c-195">J</span><span class="sxs-lookup"><span data-stu-id="8be6c-195">Y</span></span>     | <span data-ttu-id="8be6c-196">De id van het abonnement</span><span class="sxs-lookup"><span data-stu-id="8be6c-196">The ID of the subscription</span></span>                                                         |
| <span data-ttu-id="8be6c-197">FriendlyName</span><span class="sxs-lookup"><span data-stu-id="8be6c-197">FriendlyName</span></span>         | <span data-ttu-id="8be6c-198">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="8be6c-198">string</span></span> |    <span data-ttu-id="8be6c-199">N</span><span class="sxs-lookup"><span data-stu-id="8be6c-199">N</span></span>     | <span data-ttu-id="8be6c-200">De gebruiksvriendelijke naam voor het abonnement dat is gedefinieerd door de partner om dubbelzinnigheid te helpen</span><span class="sxs-lookup"><span data-stu-id="8be6c-200">The friendly name for the subscription defined by the partner to help disambiguate</span></span> |
| <span data-ttu-id="8be6c-201">Aantal</span><span class="sxs-lookup"><span data-stu-id="8be6c-201">Quantity</span></span>             | <span data-ttu-id="8be6c-202">getal</span><span class="sxs-lookup"><span data-stu-id="8be6c-202">number</span></span> |    <span data-ttu-id="8be6c-203">J</span><span class="sxs-lookup"><span data-stu-id="8be6c-203">Y</span></span>     | <span data-ttu-id="8be6c-204">Het aantal licenties of exemplaren</span><span class="sxs-lookup"><span data-stu-id="8be6c-204">The number of licenses or instances</span></span>                                                |
| <span data-ttu-id="8be6c-205">PartnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="8be6c-205">PartnerIdOnRecord</span></span>    | <span data-ttu-id="8be6c-206">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="8be6c-206">string</span></span> |    <span data-ttu-id="8be6c-207">N</span><span class="sxs-lookup"><span data-stu-id="8be6c-207">N</span></span>     | <span data-ttu-id="8be6c-208">De MPN-id van de recordpartner</span><span class="sxs-lookup"><span data-stu-id="8be6c-208">The MPN ID of the partner of record</span></span>                                                |
| <span data-ttu-id="8be6c-209">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="8be6c-209">Attributes</span></span>           | <span data-ttu-id="8be6c-210">Object</span><span class="sxs-lookup"><span data-stu-id="8be6c-210">Object</span></span> |    <span data-ttu-id="8be6c-211">N</span><span class="sxs-lookup"><span data-stu-id="8be6c-211">N</span></span>     | <span data-ttu-id="8be6c-212">Bevat "ObjectType": "OrderLineItem"</span><span class="sxs-lookup"><span data-stu-id="8be6c-212">Contains "ObjectType": "OrderLineItem"</span></span>                                             |

### <a name="request-example"></a><span data-ttu-id="8be6c-213">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="8be6c-213">Request example</span></span>

<span data-ttu-id="8be6c-214">Bijwerken naar jaarlijkse facturering</span><span class="sxs-lookup"><span data-stu-id="8be6c-214">Update to annual billing</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="8be6c-215">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="8be6c-215">REST response</span></span>

<span data-ttu-id="8be6c-216">Als dit lukt, retourneert deze methode de bijgewerkte abonnementsorder in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="8be6c-216">If successful, this method returns the updated subscription order in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8be6c-217">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="8be6c-217">Response success and error codes</span></span>

<span data-ttu-id="8be6c-218">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="8be6c-218">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8be6c-219">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="8be6c-219">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8be6c-220">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="8be6c-220">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8be6c-221">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="8be6c-221">Response example</span></span>

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