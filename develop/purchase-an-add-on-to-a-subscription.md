---
title: Een invoegtoepassing voor een abonnement kopen
description: Een invoeg toepassing aanschaffen bij een bestaand abonnement.
ms.date: 11/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 975a2516bccdc6274bfec5d6a3286a649fc4f808
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767480"
---
# <a name="purchase-an-add-on-to-a-subscription"></a><span data-ttu-id="aec81-103">Een invoegtoepassing voor een abonnement kopen</span><span class="sxs-lookup"><span data-stu-id="aec81-103">Purchase an add-on to a subscription</span></span>

<span data-ttu-id="aec81-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="aec81-104">**Applies To**</span></span>

- <span data-ttu-id="aec81-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="aec81-105">Partner Center</span></span>
- <span data-ttu-id="aec81-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="aec81-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="aec81-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="aec81-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="aec81-108">Een invoeg toepassing aanschaffen bij een bestaand abonnement.</span><span class="sxs-lookup"><span data-stu-id="aec81-108">How to purchase an add-on to an existing subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aec81-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="aec81-109">Prerequisites</span></span>

- <span data-ttu-id="aec81-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="aec81-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="aec81-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="aec81-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="aec81-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="aec81-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="aec81-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="aec81-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="aec81-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="aec81-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="aec81-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="aec81-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="aec81-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="aec81-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="aec81-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="aec81-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="aec81-118">Een abonnements-ID.</span><span class="sxs-lookup"><span data-stu-id="aec81-118">A subscription ID.</span></span> <span data-ttu-id="aec81-119">Dit is het bestaande abonnement waarvoor u een add-on-aanbieding wilt aanschaffen.</span><span class="sxs-lookup"><span data-stu-id="aec81-119">This is the existing subscription for which to purchase an add-on offer.</span></span>

- <span data-ttu-id="aec81-120">Een aanbiedings-ID waarmee de aanbieding van de invoeg toepassing wordt geïdentificeerd om te worden gekocht.</span><span class="sxs-lookup"><span data-stu-id="aec81-120">An offer ID that identifies the add-on offer to purchase.</span></span>

## <a name="purchasing-an-add-on-through-code"></a><span data-ttu-id="aec81-121">Een invoeg toepassing kopen via code</span><span class="sxs-lookup"><span data-stu-id="aec81-121">Purchasing an add-on through code</span></span>

<span data-ttu-id="aec81-122">Wanneer u een invoeg toepassing aan een abonnement aanschaft, werkt u de oorspronkelijke abonnements volgorde bij met de volg orde voor de invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="aec81-122">When you purchase an add-on to a subscription you are updating the original subscription order with the order for the add-on.</span></span> <span data-ttu-id="aec81-123">In het volgende het veld customerId is de klant-ID, subscriptionId de abonnements-ID is en addOnOfferId is de aanbiedings-ID voor de invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="aec81-123">In the following, customerId is the customer ID, subscriptionId is the subscription ID, and addOnOfferId is the offer ID for the add-on.</span></span>

<span data-ttu-id="aec81-124">Dit zijn de stappen:</span><span class="sxs-lookup"><span data-stu-id="aec81-124">Here are the steps:</span></span>

1.  <span data-ttu-id="aec81-125">Een interface ophalen voor de bewerkingen voor het abonnement.</span><span class="sxs-lookup"><span data-stu-id="aec81-125">Get an interface to the operations for the subscription.</span></span>

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2.  <span data-ttu-id="aec81-126">Deze interface gebruiken om een abonnements object te instantiëren.</span><span class="sxs-lookup"><span data-stu-id="aec81-126">Use that interface to instantiate a subscription object.</span></span> <span data-ttu-id="aec81-127">Hiermee krijgt u de details van het bovenliggende abonnement, inclusief de order-id.</span><span class="sxs-lookup"><span data-stu-id="aec81-127">This gets you the parent subscription details, including the order id.</span></span>

    ``` csharp
    var parentSubscription = subscriptionOperations.Get();
    ```

3.  <span data-ttu-id="aec81-128">Een nieuw [**order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object instantiëren.</span><span class="sxs-lookup"><span data-stu-id="aec81-128">Instantiate a new [**Order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object.</span></span> <span data-ttu-id="aec81-129">Deze order instantie wordt gebruikt om de oorspronkelijke volg orde bij te werken die wordt gebruikt om het abonnement aan te schaffen.</span><span class="sxs-lookup"><span data-stu-id="aec81-129">This order instance is used to update the original order used to purchase the subscription.</span></span> <span data-ttu-id="aec81-130">Voeg één regel item toe aan de volg orde waarin de invoeg toepassing wordt vertegenwoordigd.</span><span class="sxs-lookup"><span data-stu-id="aec81-130">Add a single line item to the order that represents the add-on.</span></span>
    ``` csharp
    var orderToUpdate = new Order()
    {
        ReferenceCustomerId = customerId,
        LineItems = new List<OrderLineItem>()
        {
            new OrderLineItem()
            {
                LineItemNumber = 0,
                OfferId = addOnOfferId,
                FriendlyName = "Some friendly name",
                Quantity = 2,
                ParentSubscriptionId = subscriptionId
            }
        }
    };
    ```

4.  <span data-ttu-id="aec81-131">Werk de oorspronkelijke volg orde voor het abonnement bij met de nieuwe volg orde voor de invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="aec81-131">Update the original order for the subscription with the new order for the add-on.</span></span>
    ``` csharp
    Order updatedOrder = partnerOperations.Customers.ById(customerId).Orders.ById(parentSubscription.OrderId).Patch(orderToUpdate);
    ```

## <a name="c"></a><span data-ttu-id="aec81-132">C\#</span><span class="sxs-lookup"><span data-stu-id="aec81-132">C\#</span></span>

<span data-ttu-id="aec81-133">Als u een invoeg toepassing wilt kopen, moet u eerst een interface aan de abonnements bewerkingen verkrijgen door de [**IAggregatePartner. Customers. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met de klant-id om de klant te identificeren, en de methode [**abonnementen. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om het abonnement te identificeren dat de invoeg toepassing biedt.</span><span class="sxs-lookup"><span data-stu-id="aec81-133">To purchase an add-on, begin by obtaining an interface to the subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the subscription that has the add-on offer.</span></span> <span data-ttu-id="aec81-134">Gebruik die [**Interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) om de abonnements gegevens op te halen door [**Get aan**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get)te roepen.</span><span class="sxs-lookup"><span data-stu-id="aec81-134">Use that [**interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) to retrieve the subscription details by calling [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get).</span></span> <span data-ttu-id="aec81-135">Waarom hebt u de abonnements gegevens nodig?</span><span class="sxs-lookup"><span data-stu-id="aec81-135">Why do you need the subscription details?</span></span> <span data-ttu-id="aec81-136">Omdat u de order-id van de abonnements order nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="aec81-136">Because you need the order id of the subscription order.</span></span> <span data-ttu-id="aec81-137">Dat is de volg orde waarin de invoeg toepassing moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="aec81-137">That's the order to be updated with the add-on.</span></span>

<span data-ttu-id="aec81-138">Vervolgens moet u een nieuw [**order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object instantiëren en dit vullen met een enkel [**LineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) -exemplaar dat de informatie bevat om de invoeg toepassing te identificeren, zoals wordt weer gegeven in het volgende code fragment.</span><span class="sxs-lookup"><span data-stu-id="aec81-138">Next, instantiate a new [**Order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object and populate it with a single [**LineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) instance that contains the information to identify the add-on, as shown in the following code snippet.</span></span> <span data-ttu-id="aec81-139">U gebruikt dit nieuwe object om de abonnements volgorde bij te werken met de invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="aec81-139">You'll use this new object to update the subscription order with the add-on.</span></span> <span data-ttu-id="aec81-140">Ten slotte roept u de [**patch**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.patch) -methode aan om de abonnements volgorde bij te werken, nadat u de klant eerst hebt geïdentificeerd met [**IAggregatePartner. klanten. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) en de order met [**Orders. ById**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid).</span><span class="sxs-lookup"><span data-stu-id="aec81-140">Finally, call the [**Patch**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.patch) method to update the subscription order, after first identifying the customer with [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) and the order with [**Orders.ById**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;
// string addOnOfferId;

// Get an interface to the operations for the subscription.
var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);

// Get the parent subscription details.
var parentSubscription = subscriptionOperations.Get();

// In order to buy an add-on subscription for this offer, we need to patch/update the order through which the base offer was purchased
// by creating an order object with a single line item which represents the add-on offer purchase.
var orderToUpdate = new Order()
{
    ReferenceCustomerId = customerId,
    LineItems = new List<OrderLineItem>()
    {
        new OrderLineItem()
        {
            LineItemNumber = 0,
            OfferId = addOnOfferId,
            FriendlyName = "Some friendly name",
            Quantity = 2,
            ParentSubscriptionId = subscriptionId
        }
    }
};

// Update the order to apply the add on purchase.
Order updatedOrder = partnerOperations.Customers.ById(customerId).Orders.ById(parentSubscription.OrderId).Patch(orderToUpdate);
```

<span data-ttu-id="aec81-141">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="aec81-141">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="aec81-142">**Project**: Partner Center SDK-voor beelden **klasse**: AddSubscriptionAddOn.cs</span><span class="sxs-lookup"><span data-stu-id="aec81-142">**Project**: Partner Center SDK Samples **Class**: AddSubscriptionAddOn.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="aec81-143">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="aec81-143">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="aec81-144">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="aec81-144">Request syntax</span></span>

| <span data-ttu-id="aec81-145">Methode</span><span class="sxs-lookup"><span data-stu-id="aec81-145">Method</span></span>    | <span data-ttu-id="aec81-146">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="aec81-146">Request URI</span></span>                                                                                              |
|-----------|----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="aec81-147">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="aec81-147">**PATCH**</span></span> | <span data-ttu-id="aec81-148">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/orders/{order-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="aec81-148">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="aec81-149">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="aec81-149">URI parameters</span></span>

<span data-ttu-id="aec81-150">Gebruik de volgende para meters om de klant en order te identificeren.</span><span class="sxs-lookup"><span data-stu-id="aec81-150">Use the following parameters to identify the customer and order.</span></span>

| <span data-ttu-id="aec81-151">Naam</span><span class="sxs-lookup"><span data-stu-id="aec81-151">Name</span></span>                   | <span data-ttu-id="aec81-152">Type</span><span class="sxs-lookup"><span data-stu-id="aec81-152">Type</span></span>     | <span data-ttu-id="aec81-153">Vereist</span><span class="sxs-lookup"><span data-stu-id="aec81-153">Required</span></span> | <span data-ttu-id="aec81-154">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="aec81-154">Description</span></span>                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="aec81-155">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="aec81-155">**customer-tenant-id**</span></span> | <span data-ttu-id="aec81-156">**guid**</span><span class="sxs-lookup"><span data-stu-id="aec81-156">**guid**</span></span> | <span data-ttu-id="aec81-157">J</span><span class="sxs-lookup"><span data-stu-id="aec81-157">Y</span></span>        | <span data-ttu-id="aec81-158">De waarde is een **klant-Tenant-id** die de klant aanduidt.</span><span class="sxs-lookup"><span data-stu-id="aec81-158">The value is a GUID formatted **customer-tenant-id** that identifies the customer.</span></span> |
| <span data-ttu-id="aec81-159">**order-id**</span><span class="sxs-lookup"><span data-stu-id="aec81-159">**order-id**</span></span>           | <span data-ttu-id="aec81-160">**guid**</span><span class="sxs-lookup"><span data-stu-id="aec81-160">**guid**</span></span> | <span data-ttu-id="aec81-161">J</span><span class="sxs-lookup"><span data-stu-id="aec81-161">Y</span></span>        | <span data-ttu-id="aec81-162">De order-id.</span><span class="sxs-lookup"><span data-stu-id="aec81-162">The order identifier.</span></span>                                                              |

### <a name="request-headers"></a><span data-ttu-id="aec81-163">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="aec81-163">Request headers</span></span>

<span data-ttu-id="aec81-164">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="aec81-164">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="aec81-165">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="aec81-165">Request body</span></span>

<span data-ttu-id="aec81-166">In de volgende tabellen worden de eigenschappen in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="aec81-166">The following tables describe the properties in the request body.</span></span>

## <a name="order"></a><span data-ttu-id="aec81-167">Volgorde</span><span class="sxs-lookup"><span data-stu-id="aec81-167">Order</span></span>

| <span data-ttu-id="aec81-168">Naam</span><span class="sxs-lookup"><span data-stu-id="aec81-168">Name</span></span>                | <span data-ttu-id="aec81-169">Type</span><span class="sxs-lookup"><span data-stu-id="aec81-169">Type</span></span>             | <span data-ttu-id="aec81-170">Vereist</span><span class="sxs-lookup"><span data-stu-id="aec81-170">Required</span></span> | <span data-ttu-id="aec81-171">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="aec81-171">Description</span></span>                                          |
|---------------------|------------------|----------|------------------------------------------------------|
| <span data-ttu-id="aec81-172">Id</span><span class="sxs-lookup"><span data-stu-id="aec81-172">Id</span></span>                  | <span data-ttu-id="aec81-173">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="aec81-173">string</span></span>           | <span data-ttu-id="aec81-174">N</span><span class="sxs-lookup"><span data-stu-id="aec81-174">N</span></span>        | <span data-ttu-id="aec81-175">De order-ID.</span><span class="sxs-lookup"><span data-stu-id="aec81-175">The order ID.</span></span>                                        |
| <span data-ttu-id="aec81-176">ReferenceCustomerId</span><span class="sxs-lookup"><span data-stu-id="aec81-176">ReferenceCustomerId</span></span> | <span data-ttu-id="aec81-177">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="aec81-177">string</span></span>           | <span data-ttu-id="aec81-178">J</span><span class="sxs-lookup"><span data-stu-id="aec81-178">Y</span></span>        | <span data-ttu-id="aec81-179">De klant-ID.</span><span class="sxs-lookup"><span data-stu-id="aec81-179">The customer ID.</span></span>                                     |
| <span data-ttu-id="aec81-180">Regel items</span><span class="sxs-lookup"><span data-stu-id="aec81-180">LineItems</span></span>           | <span data-ttu-id="aec81-181">matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="aec81-181">array of objects</span></span> | <span data-ttu-id="aec81-182">J</span><span class="sxs-lookup"><span data-stu-id="aec81-182">Y</span></span>        | <span data-ttu-id="aec81-183">Een matrix met [OrderLineItem](#orderlineitem) -objecten.</span><span class="sxs-lookup"><span data-stu-id="aec81-183">An array of [OrderLineItem](#orderlineitem) objects.</span></span> |
| <span data-ttu-id="aec81-184">CreationDate</span><span class="sxs-lookup"><span data-stu-id="aec81-184">CreationDate</span></span>        | <span data-ttu-id="aec81-185">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="aec81-185">string</span></span>           | <span data-ttu-id="aec81-186">N</span><span class="sxs-lookup"><span data-stu-id="aec81-186">N</span></span>        | <span data-ttu-id="aec81-187">De datum waarop de order is gemaakt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="aec81-187">The date the order was created, in date-time format.</span></span> |
| <span data-ttu-id="aec81-188">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="aec81-188">Attributes</span></span>          | <span data-ttu-id="aec81-189">object</span><span class="sxs-lookup"><span data-stu-id="aec81-189">object</span></span>           | <span data-ttu-id="aec81-190">N</span><span class="sxs-lookup"><span data-stu-id="aec81-190">N</span></span>        | <span data-ttu-id="aec81-191">Bevat "object type": "order".</span><span class="sxs-lookup"><span data-stu-id="aec81-191">Contains "ObjectType": "Order".</span></span>                      |

## <a name="orderlineitem"></a><span data-ttu-id="aec81-192">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="aec81-192">OrderLineItem</span></span>

| <span data-ttu-id="aec81-193">Naam</span><span class="sxs-lookup"><span data-stu-id="aec81-193">Name</span></span>                 | <span data-ttu-id="aec81-194">Type</span><span class="sxs-lookup"><span data-stu-id="aec81-194">Type</span></span>   | <span data-ttu-id="aec81-195">Vereist</span><span class="sxs-lookup"><span data-stu-id="aec81-195">Required</span></span> | <span data-ttu-id="aec81-196">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="aec81-196">Description</span></span>                                                  |
|----------------------|--------|----------|--------------------------------------------------------------|
| <span data-ttu-id="aec81-197">LineItemNumber</span><span class="sxs-lookup"><span data-stu-id="aec81-197">LineItemNumber</span></span>       | <span data-ttu-id="aec81-198">getal</span><span class="sxs-lookup"><span data-stu-id="aec81-198">number</span></span> | <span data-ttu-id="aec81-199">J</span><span class="sxs-lookup"><span data-stu-id="aec81-199">Y</span></span>        | <span data-ttu-id="aec81-200">Het nummer van het regel item, te beginnen met 0.</span><span class="sxs-lookup"><span data-stu-id="aec81-200">The line item number, starting with 0.</span></span>                       |
| <span data-ttu-id="aec81-201">OfferId</span><span class="sxs-lookup"><span data-stu-id="aec81-201">OfferId</span></span>              | <span data-ttu-id="aec81-202">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="aec81-202">string</span></span> | <span data-ttu-id="aec81-203">J</span><span class="sxs-lookup"><span data-stu-id="aec81-203">Y</span></span>        | <span data-ttu-id="aec81-204">De aanbiedings-ID van de invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="aec81-204">The offer ID of the add-on.</span></span>                                  |
| <span data-ttu-id="aec81-205">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="aec81-205">SubscriptionId</span></span>       | <span data-ttu-id="aec81-206">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="aec81-206">string</span></span> | <span data-ttu-id="aec81-207">N</span><span class="sxs-lookup"><span data-stu-id="aec81-207">N</span></span>        | <span data-ttu-id="aec81-208">De ID van het gekochte abonnement voor de invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="aec81-208">The ID of the add-on subscription purchased.</span></span>                 |
| <span data-ttu-id="aec81-209">ParentSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="aec81-209">ParentSubscriptionId</span></span> | <span data-ttu-id="aec81-210">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="aec81-210">string</span></span> | <span data-ttu-id="aec81-211">J</span><span class="sxs-lookup"><span data-stu-id="aec81-211">Y</span></span>        | <span data-ttu-id="aec81-212">De ID van het bovenliggende abonnement met de invoeg toepassing.</span><span class="sxs-lookup"><span data-stu-id="aec81-212">The ID of the parent subscription that has the add-on offer.</span></span> |
| <span data-ttu-id="aec81-213">FriendlyName</span><span class="sxs-lookup"><span data-stu-id="aec81-213">FriendlyName</span></span>         | <span data-ttu-id="aec81-214">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="aec81-214">string</span></span> | <span data-ttu-id="aec81-215">N</span><span class="sxs-lookup"><span data-stu-id="aec81-215">N</span></span>        | <span data-ttu-id="aec81-216">De beschrijvende naam voor dit regel item.</span><span class="sxs-lookup"><span data-stu-id="aec81-216">The friendly name for this line item.</span></span>                        |
| <span data-ttu-id="aec81-217">Aantal</span><span class="sxs-lookup"><span data-stu-id="aec81-217">Quantity</span></span>             | <span data-ttu-id="aec81-218">getal</span><span class="sxs-lookup"><span data-stu-id="aec81-218">number</span></span> | <span data-ttu-id="aec81-219">J</span><span class="sxs-lookup"><span data-stu-id="aec81-219">Y</span></span>        | <span data-ttu-id="aec81-220">Het aantal licenties.</span><span class="sxs-lookup"><span data-stu-id="aec81-220">The number of licenses.</span></span>                                      |
| <span data-ttu-id="aec81-221">PartnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="aec81-221">PartnerIdOnRecord</span></span>    | <span data-ttu-id="aec81-222">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="aec81-222">string</span></span> | <span data-ttu-id="aec81-223">N</span><span class="sxs-lookup"><span data-stu-id="aec81-223">N</span></span>        | <span data-ttu-id="aec81-224">De MPN-ID van de partner van de record.</span><span class="sxs-lookup"><span data-stu-id="aec81-224">The MPN ID of the partner of record.</span></span>                         |
| <span data-ttu-id="aec81-225">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="aec81-225">Attributes</span></span>           | <span data-ttu-id="aec81-226">object</span><span class="sxs-lookup"><span data-stu-id="aec81-226">object</span></span> | <span data-ttu-id="aec81-227">N</span><span class="sxs-lookup"><span data-stu-id="aec81-227">N</span></span>        | <span data-ttu-id="aec81-228">Bevat "object type": "OrderLineItem".</span><span class="sxs-lookup"><span data-stu-id="aec81-228">Contains "ObjectType": "OrderLineItem".</span></span>                      |

### <a name="request-example"></a><span data-ttu-id="aec81-229">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="aec81-229">Request example</span></span>

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
    "LineItems": [{
            "LineItemNumber": 0,
            "OfferId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "SubscriptionId": null,
            "ParentSubscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
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

## <a name="rest-response"></a><span data-ttu-id="aec81-230">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="aec81-230">REST response</span></span>

<span data-ttu-id="aec81-231">Als dit lukt, retourneert deze methode de bijgewerkte abonnements volgorde in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="aec81-231">If successful, this method returns the updated subscription order in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="aec81-232">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="aec81-232">Response success and error codes</span></span>

<span data-ttu-id="aec81-233">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="aec81-233">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="aec81-234">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="aec81-234">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="aec81-235">Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="aec81-235">For the full list, see [Partner Center Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="aec81-236">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="aec81-236">Response example</span></span>

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
    "billingCycle": "none",
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
        }, {
            "lineItemNumber": 1,
            "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
            "subscriptionId": "968BA1CF-C146-4ADF-A300-308DCF718EEE",
            "friendlyName": "Some friendly name",
            "quantity": 2,
            "links": {
                "subscription": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/968BA1CF-C146-4ADF-A300-308DCF718EEE",
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
