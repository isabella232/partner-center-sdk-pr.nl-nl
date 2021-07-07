---
title: Een invoegtoepassing voor een abonnement kopen
description: Een invoegaanvoeging aanschaffen voor een bestaand abonnement.
ms.date: 11/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d8b700a2ad41a37ca0ad745f3e7767449974b18a
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547679"
---
# <a name="purchase-an-add-on-to-a-subscription"></a><span data-ttu-id="1aef0-103">Een invoegtoepassing voor een abonnement kopen</span><span class="sxs-lookup"><span data-stu-id="1aef0-103">Purchase an add-on to a subscription</span></span>

<span data-ttu-id="1aef0-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="1aef0-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="1aef0-105">Een invoegaanvoeging aanschaffen voor een bestaand abonnement.</span><span class="sxs-lookup"><span data-stu-id="1aef0-105">How to purchase an add-on to an existing subscription.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1aef0-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1aef0-106">Prerequisites</span></span>

- <span data-ttu-id="1aef0-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1aef0-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1aef0-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="1aef0-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="1aef0-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1aef0-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="1aef0-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="1aef0-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="1aef0-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="1aef0-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="1aef0-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="1aef0-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="1aef0-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="1aef0-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="1aef0-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1aef0-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="1aef0-115">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="1aef0-115">A subscription ID.</span></span> <span data-ttu-id="1aef0-116">Dit is het bestaande abonnement waarvoor een invoegaanbieding moet worden gekocht.</span><span class="sxs-lookup"><span data-stu-id="1aef0-116">This is the existing subscription for which to purchase an add-on offer.</span></span>

- <span data-ttu-id="1aef0-117">Een aanbiedings-id die de invoegaanbieding identificeert die moet worden gekocht.</span><span class="sxs-lookup"><span data-stu-id="1aef0-117">An offer ID that identifies the add-on offer to purchase.</span></span>

## <a name="purchasing-an-add-on-through-code"></a><span data-ttu-id="1aef0-118">Een invoegproces aanschaffen via code</span><span class="sxs-lookup"><span data-stu-id="1aef0-118">Purchasing an add-on through code</span></span>

<span data-ttu-id="1aef0-119">Wanneer u een invoegaanvoeging voor een abonnement aanschaft, wordt de oorspronkelijke abonnementsorder bijgewerkt met de bestelling voor de invoeg-app.</span><span class="sxs-lookup"><span data-stu-id="1aef0-119">When you purchase an add-on to a subscription, you are updating the original subscription order with the order for the add-on.</span></span> <span data-ttu-id="1aef0-120">In het volgende is customerId de klant-id, subscriptionId de abonnements-id en addOnOfferId de aanbiedings-id voor de invoeg-on.</span><span class="sxs-lookup"><span data-stu-id="1aef0-120">In the following, customerId is the customer ID, subscriptionId is the subscription ID, and addOnOfferId is the offer ID for the add-on.</span></span>

<span data-ttu-id="1aef0-121">Dit zijn de stappen:</span><span class="sxs-lookup"><span data-stu-id="1aef0-121">Here are the steps:</span></span>

1.  <span data-ttu-id="1aef0-122">Haal een interface op voor de bewerkingen voor het abonnement.</span><span class="sxs-lookup"><span data-stu-id="1aef0-122">Get an interface to the operations for the subscription.</span></span>

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2.  <span data-ttu-id="1aef0-123">Gebruik deze interface om een abonnementsobject te instanteren.</span><span class="sxs-lookup"><span data-stu-id="1aef0-123">Use that interface to instantiate a subscription object.</span></span> <span data-ttu-id="1aef0-124">Hiermee haalt u de details van het bovenliggende abonnement op, inclusief de order-id.</span><span class="sxs-lookup"><span data-stu-id="1aef0-124">This gets you the parent subscription details, including the order ID.</span></span>

    ``` csharp
    var parentSubscription = subscriptionOperations.Get();
    ```

3.  <span data-ttu-id="1aef0-125">Een nieuw [**orderobject**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) maken.</span><span class="sxs-lookup"><span data-stu-id="1aef0-125">Instantiate a new [**Order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object.</span></span> <span data-ttu-id="1aef0-126">Dit order-exemplaar wordt gebruikt om de oorspronkelijke bestelling bij te werken die is gebruikt om het abonnement aan te schaffen.</span><span class="sxs-lookup"><span data-stu-id="1aef0-126">This order instance is used to update the original order used to purchase the subscription.</span></span> <span data-ttu-id="1aef0-127">Voeg een item met één regel toe aan de volgorde die de invoeg-opvoeging vertegenwoordigt.</span><span class="sxs-lookup"><span data-stu-id="1aef0-127">Add a single-line item to the order that represents the add-on.</span></span>
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

4.  <span data-ttu-id="1aef0-128">Werk de oorspronkelijke order voor het abonnement bij met de nieuwe order voor de invoegvoeging.</span><span class="sxs-lookup"><span data-stu-id="1aef0-128">Update the original order for the subscription with the new order for the add-on.</span></span>
    ``` csharp
    Order updatedOrder = partnerOperations.Customers.ById(customerId).Orders.ById(parentSubscription.OrderId).Patch(orderToUpdate);
    ```

## <a name="c"></a><span data-ttu-id="1aef0-129">C\#</span><span class="sxs-lookup"><span data-stu-id="1aef0-129">C\#</span></span>

<span data-ttu-id="1aef0-130">Als u een invoegbewerking wilt aanschaffen, begint u met het verkrijgen van een interface voor de abonnementsbewerkingen door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om de klant te identificeren en de methode [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om het abonnement te identificeren dat de invoeg-aanbieding heeft.</span><span class="sxs-lookup"><span data-stu-id="1aef0-130">To purchase an add-on, begin by obtaining an interface to the subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the subscription that has the add-on offer.</span></span> <span data-ttu-id="1aef0-131">Gebruik deze [**interface om de**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) abonnementsgegevens op te halen door Ophalen aan te [**roepen.**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get)</span><span class="sxs-lookup"><span data-stu-id="1aef0-131">Use that [**interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) to retrieve the subscription details by calling [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get).</span></span> <span data-ttu-id="1aef0-132">De abonnementsgegevens bevatten de order-id van de abonnementsorder. Dit is de order die moet worden bijgewerkt met de invoegvoeging.</span><span class="sxs-lookup"><span data-stu-id="1aef0-132">The subscription details contain the order ID of the subscription order, which is the order to be updated with the add-on.</span></span>

<span data-ttu-id="1aef0-133">Instantieer vervolgens een nieuw [**Order-object**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) en vul dit met één [**LineItem-exemplaar**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) dat de informatie bevat voor het identificeren van de invoegsel, zoals wordt weergegeven in het volgende codefragment.</span><span class="sxs-lookup"><span data-stu-id="1aef0-133">Next, instantiate a new [**Order**](/dotnet/api/microsoft.store.partnercenter.models.orders.order) object and populate it with a single [**LineItem**](/dotnet/api/microsoft.store.partnercenter.models.orders.orderlineitem) instance that contains the information to identify the add-on, as shown in the following code snippet.</span></span> <span data-ttu-id="1aef0-134">U gebruikt dit nieuwe object om de abonnementsorder bij te werken met de invoeg-on.</span><span class="sxs-lookup"><span data-stu-id="1aef0-134">You'll use this new object to update the subscription order with the add-on.</span></span> <span data-ttu-id="1aef0-135">Roep ten slotte de [**patchmethode aan**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.patch) om de abonnementsorder bij te werken, nadat u eerst de klant hebt identificeert met [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) en de order met [**Orders.ById.**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="1aef0-135">Finally, call the [**Patch**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.patch) method to update the subscription order, after first identifying the customer with [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) and the order with [**Orders.ById**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid).</span></span>

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

<span data-ttu-id="1aef0-136">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="1aef0-136">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="1aef0-137">**Project:** Partnercentrum-SDK Klasse **Samples:** AddSubscriptionAddOn.cs</span><span class="sxs-lookup"><span data-stu-id="1aef0-137">**Project**: Partner Center SDK Samples **Class**: AddSubscriptionAddOn.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="1aef0-138">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="1aef0-138">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1aef0-139">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="1aef0-139">Request syntax</span></span>

| <span data-ttu-id="1aef0-140">Methode</span><span class="sxs-lookup"><span data-stu-id="1aef0-140">Method</span></span>    | <span data-ttu-id="1aef0-141">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="1aef0-141">Request URI</span></span>                                                                                              |
|-----------|----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1aef0-142">**Patch**</span><span class="sxs-lookup"><span data-stu-id="1aef0-142">**PATCH**</span></span> | <span data-ttu-id="1aef0-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="1aef0-143">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{order-id} HTTP/1.1</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="1aef0-144">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="1aef0-144">URI parameters</span></span>

<span data-ttu-id="1aef0-145">Gebruik de volgende parameters om de klant en bestelling te identificeren.</span><span class="sxs-lookup"><span data-stu-id="1aef0-145">Use the following parameters to identify the customer and order.</span></span>

| <span data-ttu-id="1aef0-146">Naam</span><span class="sxs-lookup"><span data-stu-id="1aef0-146">Name</span></span>                   | <span data-ttu-id="1aef0-147">Type</span><span class="sxs-lookup"><span data-stu-id="1aef0-147">Type</span></span>     | <span data-ttu-id="1aef0-148">Vereist</span><span class="sxs-lookup"><span data-stu-id="1aef0-148">Required</span></span> | <span data-ttu-id="1aef0-149">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1aef0-149">Description</span></span>                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="1aef0-150">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="1aef0-150">**customer-tenant-id**</span></span> | <span data-ttu-id="1aef0-151">**guid**</span><span class="sxs-lookup"><span data-stu-id="1aef0-151">**guid**</span></span> | <span data-ttu-id="1aef0-152">J</span><span class="sxs-lookup"><span data-stu-id="1aef0-152">Y</span></span>        | <span data-ttu-id="1aef0-153">De waarde is een in GUID **opgemaakte klant-tenant-id** die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="1aef0-153">The value is a GUID formatted **customer-tenant-id** that identifies the customer.</span></span> |
| <span data-ttu-id="1aef0-154">**order-id**</span><span class="sxs-lookup"><span data-stu-id="1aef0-154">**order-id**</span></span>           | <span data-ttu-id="1aef0-155">**guid**</span><span class="sxs-lookup"><span data-stu-id="1aef0-155">**guid**</span></span> | <span data-ttu-id="1aef0-156">J</span><span class="sxs-lookup"><span data-stu-id="1aef0-156">Y</span></span>        | <span data-ttu-id="1aef0-157">De order-id.</span><span class="sxs-lookup"><span data-stu-id="1aef0-157">The order identifier.</span></span>                                                              |

### <a name="request-headers"></a><span data-ttu-id="1aef0-158">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="1aef0-158">Request headers</span></span>

<span data-ttu-id="1aef0-159">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="1aef0-159">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1aef0-160">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="1aef0-160">Request body</span></span>

<span data-ttu-id="1aef0-161">In de volgende tabellen worden de eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="1aef0-161">The following tables describe the properties in the request body.</span></span>

## <a name="order"></a><span data-ttu-id="1aef0-162">Volgorde</span><span class="sxs-lookup"><span data-stu-id="1aef0-162">Order</span></span>

| <span data-ttu-id="1aef0-163">Naam</span><span class="sxs-lookup"><span data-stu-id="1aef0-163">Name</span></span>                | <span data-ttu-id="1aef0-164">Type</span><span class="sxs-lookup"><span data-stu-id="1aef0-164">Type</span></span>             | <span data-ttu-id="1aef0-165">Vereist</span><span class="sxs-lookup"><span data-stu-id="1aef0-165">Required</span></span> | <span data-ttu-id="1aef0-166">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1aef0-166">Description</span></span>                                          |
|---------------------|------------------|----------|------------------------------------------------------|
| <span data-ttu-id="1aef0-167">Id</span><span class="sxs-lookup"><span data-stu-id="1aef0-167">Id</span></span>                  | <span data-ttu-id="1aef0-168">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1aef0-168">string</span></span>           | <span data-ttu-id="1aef0-169">N</span><span class="sxs-lookup"><span data-stu-id="1aef0-169">N</span></span>        | <span data-ttu-id="1aef0-170">De order-id.</span><span class="sxs-lookup"><span data-stu-id="1aef0-170">The order ID.</span></span>                                        |
| <span data-ttu-id="1aef0-171">ReferenceCustomerId</span><span class="sxs-lookup"><span data-stu-id="1aef0-171">ReferenceCustomerId</span></span> | <span data-ttu-id="1aef0-172">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1aef0-172">string</span></span>           | <span data-ttu-id="1aef0-173">J</span><span class="sxs-lookup"><span data-stu-id="1aef0-173">Y</span></span>        | <span data-ttu-id="1aef0-174">De klant-id.</span><span class="sxs-lookup"><span data-stu-id="1aef0-174">The customer ID.</span></span>                                     |
| <span data-ttu-id="1aef0-175">Regelitems</span><span class="sxs-lookup"><span data-stu-id="1aef0-175">LineItems</span></span>           | <span data-ttu-id="1aef0-176">matrix met objecten</span><span class="sxs-lookup"><span data-stu-id="1aef0-176">array of objects</span></span> | <span data-ttu-id="1aef0-177">J</span><span class="sxs-lookup"><span data-stu-id="1aef0-177">Y</span></span>        | <span data-ttu-id="1aef0-178">Een matrix met [OrderLineItem-objecten.](#orderlineitem)</span><span class="sxs-lookup"><span data-stu-id="1aef0-178">An array of [OrderLineItem](#orderlineitem) objects.</span></span> |
| <span data-ttu-id="1aef0-179">CreationDate</span><span class="sxs-lookup"><span data-stu-id="1aef0-179">CreationDate</span></span>        | <span data-ttu-id="1aef0-180">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1aef0-180">string</span></span>           | <span data-ttu-id="1aef0-181">N</span><span class="sxs-lookup"><span data-stu-id="1aef0-181">N</span></span>        | <span data-ttu-id="1aef0-182">De datum waarop de order is gemaakt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="1aef0-182">The date the order was created, in date-time format.</span></span> |
| <span data-ttu-id="1aef0-183">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1aef0-183">Attributes</span></span>          | <span data-ttu-id="1aef0-184">object</span><span class="sxs-lookup"><span data-stu-id="1aef0-184">object</span></span>           | <span data-ttu-id="1aef0-185">N</span><span class="sxs-lookup"><span data-stu-id="1aef0-185">N</span></span>        | <span data-ttu-id="1aef0-186">Bevat "ObjectType": "Order".</span><span class="sxs-lookup"><span data-stu-id="1aef0-186">Contains "ObjectType": "Order".</span></span>                      |

## <a name="orderlineitem"></a><span data-ttu-id="1aef0-187">OrderLineItem</span><span class="sxs-lookup"><span data-stu-id="1aef0-187">OrderLineItem</span></span>

| <span data-ttu-id="1aef0-188">Naam</span><span class="sxs-lookup"><span data-stu-id="1aef0-188">Name</span></span>                 | <span data-ttu-id="1aef0-189">Type</span><span class="sxs-lookup"><span data-stu-id="1aef0-189">Type</span></span>   | <span data-ttu-id="1aef0-190">Vereist</span><span class="sxs-lookup"><span data-stu-id="1aef0-190">Required</span></span> | <span data-ttu-id="1aef0-191">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1aef0-191">Description</span></span>                                                  |
|----------------------|--------|----------|--------------------------------------------------------------|
| <span data-ttu-id="1aef0-192">LineItemNumber</span><span class="sxs-lookup"><span data-stu-id="1aef0-192">LineItemNumber</span></span>       | <span data-ttu-id="1aef0-193">getal</span><span class="sxs-lookup"><span data-stu-id="1aef0-193">number</span></span> | <span data-ttu-id="1aef0-194">J</span><span class="sxs-lookup"><span data-stu-id="1aef0-194">Y</span></span>        | <span data-ttu-id="1aef0-195">Het regelitemnummer, beginnend met 0.</span><span class="sxs-lookup"><span data-stu-id="1aef0-195">The line item number, starting with 0.</span></span>                       |
| <span data-ttu-id="1aef0-196">OfferId</span><span class="sxs-lookup"><span data-stu-id="1aef0-196">OfferId</span></span>              | <span data-ttu-id="1aef0-197">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1aef0-197">string</span></span> | <span data-ttu-id="1aef0-198">J</span><span class="sxs-lookup"><span data-stu-id="1aef0-198">Y</span></span>        | <span data-ttu-id="1aef0-199">De aanbiedings-id van de invoeg-on.</span><span class="sxs-lookup"><span data-stu-id="1aef0-199">The offer ID of the add-on.</span></span>                                  |
| <span data-ttu-id="1aef0-200">SubscriptionId</span><span class="sxs-lookup"><span data-stu-id="1aef0-200">SubscriptionId</span></span>       | <span data-ttu-id="1aef0-201">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1aef0-201">string</span></span> | <span data-ttu-id="1aef0-202">N</span><span class="sxs-lookup"><span data-stu-id="1aef0-202">N</span></span>        | <span data-ttu-id="1aef0-203">De id van het aangeschafte invoegabonnement.</span><span class="sxs-lookup"><span data-stu-id="1aef0-203">The ID of the add-on subscription purchased.</span></span>                 |
| <span data-ttu-id="1aef0-204">ParentSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="1aef0-204">ParentSubscriptionId</span></span> | <span data-ttu-id="1aef0-205">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1aef0-205">string</span></span> | <span data-ttu-id="1aef0-206">J</span><span class="sxs-lookup"><span data-stu-id="1aef0-206">Y</span></span>        | <span data-ttu-id="1aef0-207">De id van het bovenliggende abonnement met de invoeg-aanbieding.</span><span class="sxs-lookup"><span data-stu-id="1aef0-207">The ID of the parent subscription that has the add-on offer.</span></span> |
| <span data-ttu-id="1aef0-208">FriendlyName</span><span class="sxs-lookup"><span data-stu-id="1aef0-208">FriendlyName</span></span>         | <span data-ttu-id="1aef0-209">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1aef0-209">string</span></span> | <span data-ttu-id="1aef0-210">N</span><span class="sxs-lookup"><span data-stu-id="1aef0-210">N</span></span>        | <span data-ttu-id="1aef0-211">De gebruiksvriendelijke naam voor dit regelitem.</span><span class="sxs-lookup"><span data-stu-id="1aef0-211">The friendly name for this line item.</span></span>                        |
| <span data-ttu-id="1aef0-212">Aantal</span><span class="sxs-lookup"><span data-stu-id="1aef0-212">Quantity</span></span>             | <span data-ttu-id="1aef0-213">getal</span><span class="sxs-lookup"><span data-stu-id="1aef0-213">number</span></span> | <span data-ttu-id="1aef0-214">J</span><span class="sxs-lookup"><span data-stu-id="1aef0-214">Y</span></span>        | <span data-ttu-id="1aef0-215">Het aantal licenties.</span><span class="sxs-lookup"><span data-stu-id="1aef0-215">The number of licenses.</span></span>                                      |
| <span data-ttu-id="1aef0-216">PartnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="1aef0-216">PartnerIdOnRecord</span></span>    | <span data-ttu-id="1aef0-217">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1aef0-217">string</span></span> | <span data-ttu-id="1aef0-218">N</span><span class="sxs-lookup"><span data-stu-id="1aef0-218">N</span></span>        | <span data-ttu-id="1aef0-219">De MPN-id van de recordpartner.</span><span class="sxs-lookup"><span data-stu-id="1aef0-219">The MPN ID of the partner of record.</span></span>                         |
| <span data-ttu-id="1aef0-220">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1aef0-220">Attributes</span></span>           | <span data-ttu-id="1aef0-221">object</span><span class="sxs-lookup"><span data-stu-id="1aef0-221">object</span></span> | <span data-ttu-id="1aef0-222">N</span><span class="sxs-lookup"><span data-stu-id="1aef0-222">N</span></span>        | <span data-ttu-id="1aef0-223">Bevat "ObjectType": "OrderLineItem".</span><span class="sxs-lookup"><span data-stu-id="1aef0-223">Contains "ObjectType": "OrderLineItem".</span></span>                      |

### <a name="request-example"></a><span data-ttu-id="1aef0-224">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1aef0-224">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="1aef0-225">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="1aef0-225">REST response</span></span>

<span data-ttu-id="1aef0-226">Als dit lukt, retourneert deze methode de bijgewerkte abonnementsorder in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="1aef0-226">If successful, this method returns the updated subscription order in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1aef0-227">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="1aef0-227">Response success and error codes</span></span>

<span data-ttu-id="1aef0-228">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="1aef0-228">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1aef0-229">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1aef0-229">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1aef0-230">Zie foutcodes voor de [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="1aef0-230">For the full list, see [Partner Center Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1aef0-231">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="1aef0-231">Response example</span></span>

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
