---
title: Een winkelwagen bijwerken
description: Hoe u een bestelling voor een klant in een winkel wagen bijwerkt.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7c0806ccc87281b9b34005f22cd8d6ad57fb5de5
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767241"
---
# <a name="update-a-cart"></a><span data-ttu-id="b5eba-103">Een winkelwagen bijwerken</span><span class="sxs-lookup"><span data-stu-id="b5eba-103">Update a cart</span></span>

<span data-ttu-id="b5eba-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="b5eba-104">**Applies To**</span></span>

- <span data-ttu-id="b5eba-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="b5eba-105">Partner Center</span></span>

<span data-ttu-id="b5eba-106">Hoe u een bestelling voor een klant in een winkel wagen bijwerkt.</span><span class="sxs-lookup"><span data-stu-id="b5eba-106">How to update an order for a customer in a cart.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b5eba-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b5eba-107">Prerequisites</span></span>

- <span data-ttu-id="b5eba-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b5eba-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b5eba-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="b5eba-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="b5eba-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b5eba-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="b5eba-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="b5eba-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="b5eba-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="b5eba-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="b5eba-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="b5eba-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="b5eba-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="b5eba-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="b5eba-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b5eba-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="b5eba-116">Een winkel wagen-ID voor een bestaande winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="b5eba-116">A Cart ID for an existing cart.</span></span>

## <a name="c"></a><span data-ttu-id="b5eba-117">C\#</span><span class="sxs-lookup"><span data-stu-id="b5eba-117">C\#</span></span>

<span data-ttu-id="b5eba-118">Als u een bestelling voor een klant wilt bijwerken, haalt u de winkel wagen op met de methode **Get ()** door de id van de klant en de winkel wagen te geven met behulp van de functie **ById ()** .</span><span class="sxs-lookup"><span data-stu-id="b5eba-118">To update an order for a customer, get the cart using the **Get()** method by passing the customer and cart ID's using the **ById()** function.</span></span> <span data-ttu-id="b5eba-119">Breng de benodigde wijzigingen aan in de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="b5eba-119">Make the necessary changes to the cart.</span></span> <span data-ttu-id="b5eba-120">Roep nu de **put** -methode aan met behulp van de methode **ById ()** .</span><span class="sxs-lookup"><span data-stu-id="b5eba-120">Now call the **Put** method by using customer and cart ID's using the **ById()** method.</span></span>

<span data-ttu-id="b5eba-121">Roep ten slotte de methode **put ()** of **PutAsync ()** aan om de volg orde te maken.</span><span class="sxs-lookup"><span data-stu-id="b5eba-121">Finally, call the **Put()** or **PutAsync()** method to create the order.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string cartId;

var cart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Get();

cart.LineItems.ToArray()[0].Quantity++;

var updatedCart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Put(cart);
```

## <a name="rest-request"></a><span data-ttu-id="b5eba-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="b5eba-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b5eba-123">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b5eba-123">Request syntax</span></span>

| <span data-ttu-id="b5eba-124">Methode</span><span class="sxs-lookup"><span data-stu-id="b5eba-124">Method</span></span>  | <span data-ttu-id="b5eba-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="b5eba-125">Request URI</span></span>                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b5eba-126">**PUT**</span><span class="sxs-lookup"><span data-stu-id="b5eba-126">**PUT**</span></span> | <span data-ttu-id="b5eba-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Carts/{Cart-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="b5eba-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts/{cart-id} HTTP/1.1</span></span>              |

### <a name="uri-parameters"></a><span data-ttu-id="b5eba-128">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="b5eba-128">URI parameters</span></span>

<span data-ttu-id="b5eba-129">Gebruik de volgende pad-para meters om de klant te identificeren en geef op welke winkel wagen moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="b5eba-129">Use the following path parameters to identify the customer, and specify the cart to be updated.</span></span>

| <span data-ttu-id="b5eba-130">Naam</span><span class="sxs-lookup"><span data-stu-id="b5eba-130">Name</span></span>            | <span data-ttu-id="b5eba-131">Type</span><span class="sxs-lookup"><span data-stu-id="b5eba-131">Type</span></span>     | <span data-ttu-id="b5eba-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="b5eba-132">Required</span></span> | <span data-ttu-id="b5eba-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b5eba-133">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="b5eba-134">**klant-id**</span><span class="sxs-lookup"><span data-stu-id="b5eba-134">**customer-id**</span></span> | <span data-ttu-id="b5eba-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b5eba-135">string</span></span>   | <span data-ttu-id="b5eba-136">Yes</span><span class="sxs-lookup"><span data-stu-id="b5eba-136">Yes</span></span>      | <span data-ttu-id="b5eba-137">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="b5eba-137">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="b5eba-138">**Winkel wagen-id**</span><span class="sxs-lookup"><span data-stu-id="b5eba-138">**cart-id**</span></span>     | <span data-ttu-id="b5eba-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b5eba-139">string</span></span>   | <span data-ttu-id="b5eba-140">Yes</span><span class="sxs-lookup"><span data-stu-id="b5eba-140">Yes</span></span>      | <span data-ttu-id="b5eba-141">Een door de GUID ingedeelde winkel wagen-id waarmee de winkel wagen wordt aangeduid.</span><span class="sxs-lookup"><span data-stu-id="b5eba-141">A GUID formatted cart-id that identifies the cart.</span></span>                     |

### <a name="request-headers"></a><span data-ttu-id="b5eba-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="b5eba-142">Request headers</span></span>

<span data-ttu-id="b5eba-143">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="b5eba-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b5eba-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="b5eba-144">Request body</span></span>

<span data-ttu-id="b5eba-145">In deze tabel worden de eigenschappen van de [winkel wagen](cart-resources.md) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="b5eba-145">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="b5eba-146">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="b5eba-146">Property</span></span>              | <span data-ttu-id="b5eba-147">Type</span><span class="sxs-lookup"><span data-stu-id="b5eba-147">Type</span></span>             | <span data-ttu-id="b5eba-148">Vereist</span><span class="sxs-lookup"><span data-stu-id="b5eba-148">Required</span></span>        | <span data-ttu-id="b5eba-149">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b5eba-149">Description</span></span>                                                                                               |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b5eba-150">id</span><span class="sxs-lookup"><span data-stu-id="b5eba-150">id</span></span>                    | <span data-ttu-id="b5eba-151">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b5eba-151">string</span></span>           | <span data-ttu-id="b5eba-152">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-152">No</span></span>              | <span data-ttu-id="b5eba-153">Een winkel wagen-id die is opgegeven bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="b5eba-153">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="b5eba-154">creationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="b5eba-154">creationTimeStamp</span></span>     | <span data-ttu-id="b5eba-155">DateTime</span><span class="sxs-lookup"><span data-stu-id="b5eba-155">DateTime</span></span>         | <span data-ttu-id="b5eba-156">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-156">No</span></span>              | <span data-ttu-id="b5eba-157">De datum waarop de winkel wagen is gemaakt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="b5eba-157">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="b5eba-158">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="b5eba-158">Applied upon successful creation of the cart.</span></span>        |
| <span data-ttu-id="b5eba-159">lastModifiedTimeStamp</span><span class="sxs-lookup"><span data-stu-id="b5eba-159">lastModifiedTimeStamp</span></span> | <span data-ttu-id="b5eba-160">DateTime</span><span class="sxs-lookup"><span data-stu-id="b5eba-160">DateTime</span></span>         | <span data-ttu-id="b5eba-161">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-161">No</span></span>              | <span data-ttu-id="b5eba-162">De datum waarop de winkel wagen voor het laatst is bijgewerkt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="b5eba-162">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="b5eba-163">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="b5eba-163">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="b5eba-164">expirationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="b5eba-164">expirationTimeStamp</span></span>   | <span data-ttu-id="b5eba-165">DateTime</span><span class="sxs-lookup"><span data-stu-id="b5eba-165">DateTime</span></span>         | <span data-ttu-id="b5eba-166">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-166">No</span></span>              | <span data-ttu-id="b5eba-167">De datum waarop de winkel wagen verloopt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="b5eba-167">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="b5eba-168">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="b5eba-168">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="b5eba-169">lastModifiedUser</span><span class="sxs-lookup"><span data-stu-id="b5eba-169">lastModifiedUser</span></span>      | <span data-ttu-id="b5eba-170">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b5eba-170">string</span></span>           | <span data-ttu-id="b5eba-171">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-171">No</span></span>              | <span data-ttu-id="b5eba-172">De gebruiker die de winkel wagen het laatst heeft bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="b5eba-172">The user who last updated the cart.</span></span> <span data-ttu-id="b5eba-173">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="b5eba-173">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="b5eba-174">Regel items</span><span class="sxs-lookup"><span data-stu-id="b5eba-174">lineItems</span></span>             | <span data-ttu-id="b5eba-175">Matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="b5eba-175">Array of objects</span></span> | <span data-ttu-id="b5eba-176">Yes</span><span class="sxs-lookup"><span data-stu-id="b5eba-176">Yes</span></span>             | <span data-ttu-id="b5eba-177">Een matrix met [CartLineItem](cart-resources.md#cartlineitem) -resources.</span><span class="sxs-lookup"><span data-stu-id="b5eba-177">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                               |

<span data-ttu-id="b5eba-178">In deze tabel worden de eigenschappen van [CartLineItem](cart-resources.md#cartlineitem) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="b5eba-178">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

| <span data-ttu-id="b5eba-179">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="b5eba-179">Property</span></span>             | <span data-ttu-id="b5eba-180">Type</span><span class="sxs-lookup"><span data-stu-id="b5eba-180">Type</span></span>                        | <span data-ttu-id="b5eba-181">Vereist</span><span class="sxs-lookup"><span data-stu-id="b5eba-181">Required</span></span>     | <span data-ttu-id="b5eba-182">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b5eba-182">Description</span></span>                                                                                        |
|----------------------|-----------------------------|--------------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b5eba-183">id</span><span class="sxs-lookup"><span data-stu-id="b5eba-183">id</span></span>                   | <span data-ttu-id="b5eba-184">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b5eba-184">string</span></span>                      | <span data-ttu-id="b5eba-185">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-185">No</span></span>           | <span data-ttu-id="b5eba-186">Een unieke id voor een winkelwagen regel item.</span><span class="sxs-lookup"><span data-stu-id="b5eba-186">A Unique identifier for a cart line item.</span></span> <span data-ttu-id="b5eba-187">Wordt toegepast bij het maken van de winkel wagen.</span><span class="sxs-lookup"><span data-stu-id="b5eba-187">Applied upon successful creation of cart.</span></span>                |
| <span data-ttu-id="b5eba-188">catalogId</span><span class="sxs-lookup"><span data-stu-id="b5eba-188">catalogId</span></span>            | <span data-ttu-id="b5eba-189">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b5eba-189">string</span></span>                      | <span data-ttu-id="b5eba-190">Yes</span><span class="sxs-lookup"><span data-stu-id="b5eba-190">Yes</span></span>          | <span data-ttu-id="b5eba-191">De id van het catalogus item.</span><span class="sxs-lookup"><span data-stu-id="b5eba-191">The catalog item identifier.</span></span>                                                                       |
| <span data-ttu-id="b5eba-192">friendlyName</span><span class="sxs-lookup"><span data-stu-id="b5eba-192">friendlyName</span></span>         | <span data-ttu-id="b5eba-193">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b5eba-193">string</span></span>                      | <span data-ttu-id="b5eba-194">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-194">No</span></span>           | <span data-ttu-id="b5eba-195">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="b5eba-195">Optional.</span></span> <span data-ttu-id="b5eba-196">De beschrijvende naam voor het item dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.</span><span class="sxs-lookup"><span data-stu-id="b5eba-196">The friendly name for the item defined by the partner to help disambiguate.</span></span>              |
| <span data-ttu-id="b5eba-197">quantity</span><span class="sxs-lookup"><span data-stu-id="b5eba-197">quantity</span></span>             | <span data-ttu-id="b5eba-198">int</span><span class="sxs-lookup"><span data-stu-id="b5eba-198">int</span></span>                         | <span data-ttu-id="b5eba-199">Ja</span><span class="sxs-lookup"><span data-stu-id="b5eba-199">Yes</span></span>          | <span data-ttu-id="b5eba-200">Het aantal licenties of exemplaren.</span><span class="sxs-lookup"><span data-stu-id="b5eba-200">The number of licenses or instances.</span></span>     |
| <span data-ttu-id="b5eba-201">currencyCode</span><span class="sxs-lookup"><span data-stu-id="b5eba-201">currencyCode</span></span>         | <span data-ttu-id="b5eba-202">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b5eba-202">string</span></span>                      | <span data-ttu-id="b5eba-203">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-203">No</span></span>           | <span data-ttu-id="b5eba-204">De valuta code.</span><span class="sxs-lookup"><span data-stu-id="b5eba-204">The currency code.</span></span>                                                                                 |
| <span data-ttu-id="b5eba-205">billingCycle</span><span class="sxs-lookup"><span data-stu-id="b5eba-205">billingCycle</span></span>         | <span data-ttu-id="b5eba-206">Object</span><span class="sxs-lookup"><span data-stu-id="b5eba-206">Object</span></span>                      | <span data-ttu-id="b5eba-207">Ja</span><span class="sxs-lookup"><span data-stu-id="b5eba-207">Yes</span></span>          | <span data-ttu-id="b5eba-208">Het type facturerings cyclus dat voor de huidige periode is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="b5eba-208">The type of billing cycle set for the current period.</span></span>                                              |
| <span data-ttu-id="b5eba-209">deelnemers</span><span class="sxs-lookup"><span data-stu-id="b5eba-209">participants</span></span>         | <span data-ttu-id="b5eba-210">Lijst met object teken reeks paren</span><span class="sxs-lookup"><span data-stu-id="b5eba-210">List of Object String pairs</span></span> | <span data-ttu-id="b5eba-211">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-211">No</span></span>           | <span data-ttu-id="b5eba-212">Een verzameling deel nemers aan de aankoop.</span><span class="sxs-lookup"><span data-stu-id="b5eba-212">A collection of participants on the purchase.</span></span>                                                      |
| <span data-ttu-id="b5eba-213">provisioningContext</span><span class="sxs-lookup"><span data-stu-id="b5eba-213">provisioningContext</span></span>  | <span data-ttu-id="b5eba-214">Dictionary<teken reeks, teken reeks></span><span class="sxs-lookup"><span data-stu-id="b5eba-214">Dictionary<string, string></span></span>  | <span data-ttu-id="b5eba-215">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-215">No</span></span>           | <span data-ttu-id="b5eba-216">Een context die wordt gebruikt voor het inrichten van de aanbieding.</span><span class="sxs-lookup"><span data-stu-id="b5eba-216">A context used for provisioning of offer.</span></span>                                                          |
| <span data-ttu-id="b5eba-217">orderGroup</span><span class="sxs-lookup"><span data-stu-id="b5eba-217">orderGroup</span></span>           | <span data-ttu-id="b5eba-218">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="b5eba-218">string</span></span>                      | <span data-ttu-id="b5eba-219">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-219">No</span></span>           | <span data-ttu-id="b5eba-220">Een groep om aan te geven welke items bij elkaar kunnen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="b5eba-220">A group to indicate which items can be placed together.</span></span>                                            |
| <span data-ttu-id="b5eba-221">fout</span><span class="sxs-lookup"><span data-stu-id="b5eba-221">error</span></span>                | <span data-ttu-id="b5eba-222">Object</span><span class="sxs-lookup"><span data-stu-id="b5eba-222">Object</span></span>                      | <span data-ttu-id="b5eba-223">No</span><span class="sxs-lookup"><span data-stu-id="b5eba-223">No</span></span>           | <span data-ttu-id="b5eba-224">Wordt toegepast nadat de winkel wagen is gemaakt in het geval van een fout.</span><span class="sxs-lookup"><span data-stu-id="b5eba-224">Applied after cart is created in case of an error.</span></span>                                                 |

### <a name="request-example"></a><span data-ttu-id="b5eba-225">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b5eba-225">Request example</span></span>

```http
PUT /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts/65faf57b-0205-47ee-92b3-08dcf233ea73/ HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 496
Expect: 100-continue

{
    {
        "Id":"b4c8fdea-cbe4-4d17-9576-13fcacbf9605",
        "CreationTimestamp":"2018-03-15T17:15:02.3840528Z",
        "LastModifiedTimestamp":"2018-03-15T17:15:02.3840528Z",
        "ExpirationTimestamp":"0001-01-01T00:00:00",
        "LastModifiedUser":"2713ccd7-ea3b-470a-9cfb-451d5d0482cc",
        "LineItems":[
            {
                "Id":0,
                "CatalogItemId":"DG7GMGF0DWTL:0001:DG7GMGF0DSJB",
                "FriendlyName":"A_sample_Azure_RI",
                "Quantity":2,
                "BillingCycle":"one_time",
                "ProvisioningContext": {
                    "SubscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
                    "Scope": "shared",
                    "Duration": "1Year"
                }
            }
        ],
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="b5eba-226">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="b5eba-226">REST response</span></span>

<span data-ttu-id="b5eba-227">Als dit lukt, retourneert deze methode de gevulde [Winkelwagen](cart-resources.md) resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="b5eba-227">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b5eba-228">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="b5eba-228">Response success and error codes</span></span>

<span data-ttu-id="b5eba-229">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="b5eba-229">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b5eba-230">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="b5eba-230">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b5eba-231">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="b5eba-231">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b5eba-232">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b5eba-232">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 764
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
X-Locale: en-US,en-US
MS-CV: sF/wRa2ih0CzbABc.0
MS-ServerId: 000001
Date: Thu, 15 Mar 2018 17:15:01 GMT
{
    "id": "b4c8fdea-cbe4-4d17-9576-13fcacbf9605",
    "creationTimestamp": "2018-03-15T17:15:02.3840528Z",
    "lastModifiedTimestamp": "2018-03-15T17:15:02.3840528Z",
    "lastModifiedUser": "2713ccd7-ea3b-470a-9cfb-451d5d0482cc",
    "lineItems": [
        {
            "id": 0,
            "catalogItemId": "DG7GMGF0DWTL:0001:DG7GMGF0DSJB",
            "friendlyName": "A_sample_Azure_RI",
            "quantity": 2,
            "currencyCode": "USD",
            "billingCycle": "one_time",
            "ProvisioningContext": {
                "subscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
                "scope": "shared",
                "duration": "1Year"
            }
            "orderGroup": "0"
        }
    ],
    "links": {
        "self": {
            "uri": "/v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts/b4c8fdea-cbe4-4d17-9576-13fcacbf9605/",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Cart"
    }
}
```
