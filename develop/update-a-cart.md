---
title: Een winkelwagen bijwerken
description: Een order voor een klant in een winkelwagen bijwerken.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8954d4dad39f9b1a1b9a2f213e0231f01856fcd2
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446680"
---
# <a name="update-a-cart"></a><span data-ttu-id="757d3-103">Een winkelwagen bijwerken</span><span class="sxs-lookup"><span data-stu-id="757d3-103">Update a cart</span></span>

<span data-ttu-id="757d3-104">Een order voor een klant in een winkelwagen bijwerken.</span><span class="sxs-lookup"><span data-stu-id="757d3-104">How to update an order for a customer in a cart.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="757d3-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="757d3-105">Prerequisites</span></span>

- <span data-ttu-id="757d3-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="757d3-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="757d3-107">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="757d3-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="757d3-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="757d3-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="757d3-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="757d3-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="757d3-110">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="757d3-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="757d3-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="757d3-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="757d3-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="757d3-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="757d3-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="757d3-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="757d3-114">Een winkelwagen-id voor een bestaande winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="757d3-114">A Cart ID for an existing cart.</span></span>

## <a name="c"></a><span data-ttu-id="757d3-115">C\#</span><span class="sxs-lookup"><span data-stu-id="757d3-115">C\#</span></span>

<span data-ttu-id="757d3-116">Als u een order voor een klant wilt bijwerken, moet u de winkelwagen op halen met behulp van de **methode Get()** door de klant- en winkelwagen-ID's door te geven met behulp van de **functie ById().**</span><span class="sxs-lookup"><span data-stu-id="757d3-116">To update an order for a customer, get the cart using the **Get()** method by passing the customer and cart IDs using the **ById()** function.</span></span> <span data-ttu-id="757d3-117">Wijzig de benodigde wijzigingen in de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="757d3-117">Make the necessary changes to the cart.</span></span> <span data-ttu-id="757d3-118">Roep nu de **methode Put aan** met behulp van klant- en winkelwagen-ID's met behulp van de methode **ById().**</span><span class="sxs-lookup"><span data-stu-id="757d3-118">Now call the **Put** method by using customer and cart IDs using the **ById()** method.</span></span>

<span data-ttu-id="757d3-119">Roep ten slotte de **methode Put()** of **PutAsync()** aan om de bestelling te maken.</span><span class="sxs-lookup"><span data-stu-id="757d3-119">Finally, call the **Put()** or **PutAsync()** method to create the order.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string cartId;

var cart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Get();

cart.LineItems.ToArray()[0].Quantity++;

var updatedCart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Put(cart);
```

## <a name="rest-request"></a><span data-ttu-id="757d3-120">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="757d3-120">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="757d3-121">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="757d3-121">Request syntax</span></span>

| <span data-ttu-id="757d3-122">Methode</span><span class="sxs-lookup"><span data-stu-id="757d3-122">Method</span></span>  | <span data-ttu-id="757d3-123">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="757d3-123">Request URI</span></span>                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="757d3-124">**PUT**</span><span class="sxs-lookup"><span data-stu-id="757d3-124">**PUT**</span></span> | <span data-ttu-id="757d3-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts/{cart-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="757d3-125">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts/{cart-id} HTTP/1.1</span></span>              |

### <a name="uri-parameters"></a><span data-ttu-id="757d3-126">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="757d3-126">URI parameters</span></span>

<span data-ttu-id="757d3-127">Gebruik de volgende padparameters om de klant te identificeren en geef de winkelwagen op die moet worden bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="757d3-127">Use the following path parameters to identify the customer, and specify the cart to be updated.</span></span>

| <span data-ttu-id="757d3-128">Naam</span><span class="sxs-lookup"><span data-stu-id="757d3-128">Name</span></span>            | <span data-ttu-id="757d3-129">Type</span><span class="sxs-lookup"><span data-stu-id="757d3-129">Type</span></span>     | <span data-ttu-id="757d3-130">Vereist</span><span class="sxs-lookup"><span data-stu-id="757d3-130">Required</span></span> | <span data-ttu-id="757d3-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="757d3-131">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="757d3-132">**customer-id**</span><span class="sxs-lookup"><span data-stu-id="757d3-132">**customer-id**</span></span> | <span data-ttu-id="757d3-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="757d3-133">string</span></span>   | <span data-ttu-id="757d3-134">Ja</span><span class="sxs-lookup"><span data-stu-id="757d3-134">Yes</span></span>      | <span data-ttu-id="757d3-135">Een in GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="757d3-135">A GUID formatted customer-id that identifies the customer.</span></span>             |
| <span data-ttu-id="757d3-136">**cart-id**</span><span class="sxs-lookup"><span data-stu-id="757d3-136">**cart-id**</span></span>     | <span data-ttu-id="757d3-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="757d3-137">string</span></span>   | <span data-ttu-id="757d3-138">Ja</span><span class="sxs-lookup"><span data-stu-id="757d3-138">Yes</span></span>      | <span data-ttu-id="757d3-139">Een met GUID opgemaakte cart-id die de winkelwagen identificeert.</span><span class="sxs-lookup"><span data-stu-id="757d3-139">A GUID formatted cart-id that identifies the cart.</span></span>                     |

### <a name="request-headers"></a><span data-ttu-id="757d3-140">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="757d3-140">Request headers</span></span>

<span data-ttu-id="757d3-141">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="757d3-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="757d3-142">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="757d3-142">Request body</span></span>

<span data-ttu-id="757d3-143">In deze tabel worden de eigenschappen [van de winkelwagen](cart-resources.md) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="757d3-143">This table describes the [Cart](cart-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="757d3-144">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="757d3-144">Property</span></span>              | <span data-ttu-id="757d3-145">Type</span><span class="sxs-lookup"><span data-stu-id="757d3-145">Type</span></span>             | <span data-ttu-id="757d3-146">Vereist</span><span class="sxs-lookup"><span data-stu-id="757d3-146">Required</span></span>        | <span data-ttu-id="757d3-147">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="757d3-147">Description</span></span>                                                                                               |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="757d3-148">id</span><span class="sxs-lookup"><span data-stu-id="757d3-148">id</span></span>                    | <span data-ttu-id="757d3-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="757d3-149">string</span></span>           | <span data-ttu-id="757d3-150">No</span><span class="sxs-lookup"><span data-stu-id="757d3-150">No</span></span>              | <span data-ttu-id="757d3-151">Een winkelwagen-id die wordt opgegeven wanneer de winkelwagen is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="757d3-151">A cart identifier that is supplied upon successful creation of the cart.</span></span>                                  |
| <span data-ttu-id="757d3-152">creationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="757d3-152">creationTimeStamp</span></span>     | <span data-ttu-id="757d3-153">DateTime</span><span class="sxs-lookup"><span data-stu-id="757d3-153">DateTime</span></span>         | <span data-ttu-id="757d3-154">Nee</span><span class="sxs-lookup"><span data-stu-id="757d3-154">No</span></span>              | <span data-ttu-id="757d3-155">De datum waarop de winkelwagen is gemaakt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="757d3-155">The date the cart was created, in date-time format.</span></span> <span data-ttu-id="757d3-156">Toegepast wanneer de winkelwagen is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="757d3-156">Applied upon successful creation of the cart.</span></span>        |
| <span data-ttu-id="757d3-157">lastModifiedTimeStamp</span><span class="sxs-lookup"><span data-stu-id="757d3-157">lastModifiedTimeStamp</span></span> | <span data-ttu-id="757d3-158">DateTime</span><span class="sxs-lookup"><span data-stu-id="757d3-158">DateTime</span></span>         | <span data-ttu-id="757d3-159">Nee</span><span class="sxs-lookup"><span data-stu-id="757d3-159">No</span></span>              | <span data-ttu-id="757d3-160">De datum waarop de winkelwagen voor het laatst is bijgewerkt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="757d3-160">The date the cart was last updated, in date-time format.</span></span> <span data-ttu-id="757d3-161">Toegepast wanneer de winkelwagen is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="757d3-161">Applied upon successful creation of the cart.</span></span>    |
| <span data-ttu-id="757d3-162">expirationTimeStamp</span><span class="sxs-lookup"><span data-stu-id="757d3-162">expirationTimeStamp</span></span>   | <span data-ttu-id="757d3-163">DateTime</span><span class="sxs-lookup"><span data-stu-id="757d3-163">DateTime</span></span>         | <span data-ttu-id="757d3-164">Nee</span><span class="sxs-lookup"><span data-stu-id="757d3-164">No</span></span>              | <span data-ttu-id="757d3-165">De datum waarop de winkelwagen verloopt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="757d3-165">The date the cart will expire, in date-time format.</span></span>  <span data-ttu-id="757d3-166">Toegepast bij het maken van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="757d3-166">Applied upon successful creation of cart.</span></span>            |
| <span data-ttu-id="757d3-167">lastModifiedUser</span><span class="sxs-lookup"><span data-stu-id="757d3-167">lastModifiedUser</span></span>      | <span data-ttu-id="757d3-168">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="757d3-168">string</span></span>           | <span data-ttu-id="757d3-169">No</span><span class="sxs-lookup"><span data-stu-id="757d3-169">No</span></span>              | <span data-ttu-id="757d3-170">De gebruiker die de winkelwagen voor het laatst heeft bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="757d3-170">The user who last updated the cart.</span></span> <span data-ttu-id="757d3-171">Toegepast bij het maken van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="757d3-171">Applied upon successful creation of cart.</span></span>                             |
| <span data-ttu-id="757d3-172">lineItems</span><span class="sxs-lookup"><span data-stu-id="757d3-172">lineItems</span></span>             | <span data-ttu-id="757d3-173">Matrix met objecten</span><span class="sxs-lookup"><span data-stu-id="757d3-173">Array of objects</span></span> | <span data-ttu-id="757d3-174">Ja</span><span class="sxs-lookup"><span data-stu-id="757d3-174">Yes</span></span>             | <span data-ttu-id="757d3-175">Een matrix van [CartLineItem-resources.](cart-resources.md#cartlineitem)</span><span class="sxs-lookup"><span data-stu-id="757d3-175">An Array of [CartLineItem](cart-resources.md#cartlineitem) resources.</span></span>                                               |

<span data-ttu-id="757d3-176">In deze tabel worden de [eigenschappen van CartLineItem](cart-resources.md#cartlineitem) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="757d3-176">This table describes the [CartLineItem](cart-resources.md#cartlineitem) properties in the request body.</span></span>

| <span data-ttu-id="757d3-177">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="757d3-177">Property</span></span>             | <span data-ttu-id="757d3-178">Type</span><span class="sxs-lookup"><span data-stu-id="757d3-178">Type</span></span>                        | <span data-ttu-id="757d3-179">Vereist</span><span class="sxs-lookup"><span data-stu-id="757d3-179">Required</span></span>     | <span data-ttu-id="757d3-180">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="757d3-180">Description</span></span>                                                                                        |
|----------------------|-----------------------------|--------------|----------------------------------------------------------------------------------------------------|
| <span data-ttu-id="757d3-181">id</span><span class="sxs-lookup"><span data-stu-id="757d3-181">id</span></span>                   | <span data-ttu-id="757d3-182">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="757d3-182">string</span></span>                      | <span data-ttu-id="757d3-183">No</span><span class="sxs-lookup"><span data-stu-id="757d3-183">No</span></span>           | <span data-ttu-id="757d3-184">Een unieke id voor een winkelwagenregelitem.</span><span class="sxs-lookup"><span data-stu-id="757d3-184">A Unique identifier for a cart line item.</span></span> <span data-ttu-id="757d3-185">Toegepast bij het maken van de winkelwagen.</span><span class="sxs-lookup"><span data-stu-id="757d3-185">Applied upon successful creation of cart.</span></span>                |
| <span data-ttu-id="757d3-186">catalogId</span><span class="sxs-lookup"><span data-stu-id="757d3-186">catalogId</span></span>            | <span data-ttu-id="757d3-187">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="757d3-187">string</span></span>                      | <span data-ttu-id="757d3-188">Ja</span><span class="sxs-lookup"><span data-stu-id="757d3-188">Yes</span></span>          | <span data-ttu-id="757d3-189">De id van het catalogusitem.</span><span class="sxs-lookup"><span data-stu-id="757d3-189">The catalog item identifier.</span></span>                                                                       |
| <span data-ttu-id="757d3-190">Friendlyname</span><span class="sxs-lookup"><span data-stu-id="757d3-190">friendlyName</span></span>         | <span data-ttu-id="757d3-191">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="757d3-191">string</span></span>                      | <span data-ttu-id="757d3-192">No</span><span class="sxs-lookup"><span data-stu-id="757d3-192">No</span></span>           | <span data-ttu-id="757d3-193">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="757d3-193">Optional.</span></span> <span data-ttu-id="757d3-194">De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het opsysen van ambiguïteit.</span><span class="sxs-lookup"><span data-stu-id="757d3-194">The friendly name for the item defined by the partner to help disambiguate.</span></span>              |
| <span data-ttu-id="757d3-195">quantity</span><span class="sxs-lookup"><span data-stu-id="757d3-195">quantity</span></span>             | <span data-ttu-id="757d3-196">int</span><span class="sxs-lookup"><span data-stu-id="757d3-196">int</span></span>                         | <span data-ttu-id="757d3-197">Ja</span><span class="sxs-lookup"><span data-stu-id="757d3-197">Yes</span></span>          | <span data-ttu-id="757d3-198">Het aantal licenties of instanties.</span><span class="sxs-lookup"><span data-stu-id="757d3-198">The number of licenses or instances.</span></span>     |
| <span data-ttu-id="757d3-199">currencyCode</span><span class="sxs-lookup"><span data-stu-id="757d3-199">currencyCode</span></span>         | <span data-ttu-id="757d3-200">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="757d3-200">string</span></span>                      | <span data-ttu-id="757d3-201">No</span><span class="sxs-lookup"><span data-stu-id="757d3-201">No</span></span>           | <span data-ttu-id="757d3-202">De valutacode.</span><span class="sxs-lookup"><span data-stu-id="757d3-202">The currency code.</span></span>                                                                                 |
| <span data-ttu-id="757d3-203">billingCycle</span><span class="sxs-lookup"><span data-stu-id="757d3-203">billingCycle</span></span>         | <span data-ttu-id="757d3-204">Object</span><span class="sxs-lookup"><span data-stu-id="757d3-204">Object</span></span>                      | <span data-ttu-id="757d3-205">Ja</span><span class="sxs-lookup"><span data-stu-id="757d3-205">Yes</span></span>          | <span data-ttu-id="757d3-206">Het type factureringscyclus dat is ingesteld voor de huidige periode.</span><span class="sxs-lookup"><span data-stu-id="757d3-206">The type of billing cycle set for the current period.</span></span>                                              |
| <span data-ttu-id="757d3-207">deelnemers</span><span class="sxs-lookup"><span data-stu-id="757d3-207">participants</span></span>         | <span data-ttu-id="757d3-208">Lijst met objectreeksparen</span><span class="sxs-lookup"><span data-stu-id="757d3-208">List of Object String pairs</span></span> | <span data-ttu-id="757d3-209">Nee</span><span class="sxs-lookup"><span data-stu-id="757d3-209">No</span></span>           | <span data-ttu-id="757d3-210">Een verzameling deelnemers aan de aankoop.</span><span class="sxs-lookup"><span data-stu-id="757d3-210">A collection of participants on the purchase.</span></span>                                                      |
| <span data-ttu-id="757d3-211">provisioningContext</span><span class="sxs-lookup"><span data-stu-id="757d3-211">provisioningContext</span></span>  | <span data-ttu-id="757d3-212">Woordenlijst<tekenreeks, tekenreeks></span><span class="sxs-lookup"><span data-stu-id="757d3-212">Dictionary<string, string></span></span>  | <span data-ttu-id="757d3-213">Nee</span><span class="sxs-lookup"><span data-stu-id="757d3-213">No</span></span>           | <span data-ttu-id="757d3-214">Een context die wordt gebruikt voor het inrichten van de aanbieding.</span><span class="sxs-lookup"><span data-stu-id="757d3-214">A context used for provisioning of offer.</span></span>                                                          |
| <span data-ttu-id="757d3-215">orderGroup</span><span class="sxs-lookup"><span data-stu-id="757d3-215">orderGroup</span></span>           | <span data-ttu-id="757d3-216">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="757d3-216">string</span></span>                      | <span data-ttu-id="757d3-217">No</span><span class="sxs-lookup"><span data-stu-id="757d3-217">No</span></span>           | <span data-ttu-id="757d3-218">Een groep om aan te geven welke items samen kunnen worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="757d3-218">A group to indicate which items can be placed together.</span></span>                                            |
| <span data-ttu-id="757d3-219">fout</span><span class="sxs-lookup"><span data-stu-id="757d3-219">error</span></span>                | <span data-ttu-id="757d3-220">Object</span><span class="sxs-lookup"><span data-stu-id="757d3-220">Object</span></span>                      | <span data-ttu-id="757d3-221">Nee</span><span class="sxs-lookup"><span data-stu-id="757d3-221">No</span></span>           | <span data-ttu-id="757d3-222">Toegepast nadat de winkelwagen is gemaakt in het geval van een fout.</span><span class="sxs-lookup"><span data-stu-id="757d3-222">Applied after cart is created in case of an error.</span></span>                                                 |

### <a name="request-example"></a><span data-ttu-id="757d3-223">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="757d3-223">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="757d3-224">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="757d3-224">REST response</span></span>

<span data-ttu-id="757d3-225">Als dit lukt, retourneert deze methode de ingevulde [winkelwagenresource](cart-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="757d3-225">If successful, this method returns the populated [Cart](cart-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="757d3-226">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="757d3-226">Response success and error codes</span></span>

<span data-ttu-id="757d3-227">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="757d3-227">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="757d3-228">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="757d3-228">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="757d3-229">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="757d3-229">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="757d3-230">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="757d3-230">Response example</span></span>

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
