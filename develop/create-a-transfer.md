---
title: Een overdracht maken
description: Een overdracht van abonnementen voor een klant maken.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d5e70cc5b7ce4fcfa715f581a2151f0b8d1922b0
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767204"
---
# <a name="create-a-transfer"></a><span data-ttu-id="fb44a-103">Een overdracht maken</span><span class="sxs-lookup"><span data-stu-id="fb44a-103">Create a transfer</span></span>

<span data-ttu-id="fb44a-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="fb44a-104">**Applies to:**</span></span>

- <span data-ttu-id="fb44a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="fb44a-105">Partner Center</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fb44a-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fb44a-106">Prerequisites</span></span>

- <span data-ttu-id="fb44a-107">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fb44a-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fb44a-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="fb44a-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="fb44a-109">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fb44a-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="fb44a-110">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="fb44a-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="fb44a-111">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="fb44a-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="fb44a-112">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="fb44a-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="fb44a-113">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="fb44a-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="fb44a-114">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fb44a-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="fb44a-115">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fb44a-115">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fb44a-116">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fb44a-116">Request syntax</span></span>

| <span data-ttu-id="fb44a-117">Methode</span><span class="sxs-lookup"><span data-stu-id="fb44a-117">Method</span></span>   | <span data-ttu-id="fb44a-118">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fb44a-118">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fb44a-119">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="fb44a-119">**POST**</span></span> | <span data-ttu-id="fb44a-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/transfers http/1.1</span><span class="sxs-lookup"><span data-stu-id="fb44a-120">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="fb44a-121">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="fb44a-121">URI parameter</span></span>

<span data-ttu-id="fb44a-122">Gebruik de volgende para meter voor het identificeren van de klant.</span><span class="sxs-lookup"><span data-stu-id="fb44a-122">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="fb44a-123">Naam</span><span class="sxs-lookup"><span data-stu-id="fb44a-123">Name</span></span>            | <span data-ttu-id="fb44a-124">Type</span><span class="sxs-lookup"><span data-stu-id="fb44a-124">Type</span></span>     | <span data-ttu-id="fb44a-125">Vereist</span><span class="sxs-lookup"><span data-stu-id="fb44a-125">Required</span></span> | <span data-ttu-id="fb44a-126">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fb44a-126">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="fb44a-127">**klant-id**</span><span class="sxs-lookup"><span data-stu-id="fb44a-127">**customer-id**</span></span> | <span data-ttu-id="fb44a-128">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-128">string</span></span>   | <span data-ttu-id="fb44a-129">Yes</span><span class="sxs-lookup"><span data-stu-id="fb44a-129">Yes</span></span>      | <span data-ttu-id="fb44a-130">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="fb44a-130">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="fb44a-131">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fb44a-131">Request headers</span></span>

<span data-ttu-id="fb44a-132">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="fb44a-132">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fb44a-133">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fb44a-133">Request body</span></span>

<span data-ttu-id="fb44a-134">In deze tabel worden de eigenschappen van [TransferEntity](transfer-entity-resources.md) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="fb44a-134">This table describes the [TransferEntity](transfer-entity-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="fb44a-135">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fb44a-135">Property</span></span>              | <span data-ttu-id="fb44a-136">Type</span><span class="sxs-lookup"><span data-stu-id="fb44a-136">Type</span></span>          | <span data-ttu-id="fb44a-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="fb44a-137">Required</span></span>  | <span data-ttu-id="fb44a-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fb44a-138">Description</span></span>                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="fb44a-139">id</span><span class="sxs-lookup"><span data-stu-id="fb44a-139">id</span></span>                    | <span data-ttu-id="fb44a-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-140">string</span></span>        | <span data-ttu-id="fb44a-141">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-141">No</span></span>    | <span data-ttu-id="fb44a-142">Een transferEntity-id die wordt geleverd bij het maken van de transferEntity.</span><span class="sxs-lookup"><span data-stu-id="fb44a-142">A transferEntity identifier that is supplied upon successful creation of the transferEntity.</span></span>                               |
| <span data-ttu-id="fb44a-143">createdTime</span><span class="sxs-lookup"><span data-stu-id="fb44a-143">createdTime</span></span>           | <span data-ttu-id="fb44a-144">DateTime</span><span class="sxs-lookup"><span data-stu-id="fb44a-144">DateTime</span></span>      | <span data-ttu-id="fb44a-145">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-145">No</span></span>    | <span data-ttu-id="fb44a-146">De datum waarop de transferEntity is gemaakt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="fb44a-146">The date the transferEntity was created, in date-time format.</span></span> <span data-ttu-id="fb44a-147">Wordt toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fb44a-147">Applied upon successful creation of the transferEntity.</span></span>      |
| <span data-ttu-id="fb44a-148">lastModifiedTime</span><span class="sxs-lookup"><span data-stu-id="fb44a-148">lastModifiedTime</span></span>      | <span data-ttu-id="fb44a-149">DateTime</span><span class="sxs-lookup"><span data-stu-id="fb44a-149">DateTime</span></span>      | <span data-ttu-id="fb44a-150">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-150">No</span></span>    | <span data-ttu-id="fb44a-151">De datum waarop de transferEntity voor het laatst is bijgewerkt, in datum-tijd notatie.</span><span class="sxs-lookup"><span data-stu-id="fb44a-151">The date the transferEntity was last updated, in date-time format.</span></span> <span data-ttu-id="fb44a-152">Wordt toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fb44a-152">Applied upon successful creation of the transferEntity.</span></span> |
| <span data-ttu-id="fb44a-153">lastModifiedUser</span><span class="sxs-lookup"><span data-stu-id="fb44a-153">lastModifiedUser</span></span>      | <span data-ttu-id="fb44a-154">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-154">string</span></span>        | <span data-ttu-id="fb44a-155">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-155">No</span></span>    | <span data-ttu-id="fb44a-156">De gebruiker die de transferEntity voor het laatst heeft bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="fb44a-156">The user who last updated the transferEntity.</span></span> <span data-ttu-id="fb44a-157">Toegepast bij het maken van transferEntity.</span><span class="sxs-lookup"><span data-stu-id="fb44a-157">Applied upon successful creation of transferEntity.</span></span>                          |
| <span data-ttu-id="fb44a-158">customerName</span><span class="sxs-lookup"><span data-stu-id="fb44a-158">customerName</span></span>          | <span data-ttu-id="fb44a-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-159">string</span></span>        | <span data-ttu-id="fb44a-160">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-160">No</span></span>    | <span data-ttu-id="fb44a-161">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="fb44a-161">Optional.</span></span> <span data-ttu-id="fb44a-162">De naam van de klant wiens abonnementen worden overgedragen.</span><span class="sxs-lookup"><span data-stu-id="fb44a-162">The name of the customer whose subscriptions are being transferred.</span></span>                                              |
| <span data-ttu-id="fb44a-163">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="fb44a-163">customerTenantId</span></span>      | <span data-ttu-id="fb44a-164">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-164">string</span></span>        | <span data-ttu-id="fb44a-165">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-165">No</span></span>    | <span data-ttu-id="fb44a-166">Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="fb44a-166">A GUID formatted customer-id that identifies the customer.</span></span> <span data-ttu-id="fb44a-167">Wordt toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fb44a-167">Applied upon successful creation of the transferEntity.</span></span>         |
| <span data-ttu-id="fb44a-168">partnertenantid</span><span class="sxs-lookup"><span data-stu-id="fb44a-168">partnertenantid</span></span>       | <span data-ttu-id="fb44a-169">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-169">string</span></span>        | <span data-ttu-id="fb44a-170">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-170">No</span></span>    | <span data-ttu-id="fb44a-171">Een door de GUID opgemaakte partner-id waarmee de partner wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="fb44a-171">A GUID formatted partner-id that identifies the partner.</span></span>                                                                   |
| <span data-ttu-id="fb44a-172">sourcePartnerName</span><span class="sxs-lookup"><span data-stu-id="fb44a-172">sourcePartnerName</span></span>     | <span data-ttu-id="fb44a-173">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-173">string</span></span>        | <span data-ttu-id="fb44a-174">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-174">No</span></span>    | <span data-ttu-id="fb44a-175">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="fb44a-175">Optional.</span></span> <span data-ttu-id="fb44a-176">De naam van de organisatie van de partner die de overdracht initieert.</span><span class="sxs-lookup"><span data-stu-id="fb44a-176">The name of the partner's organization who is initiating the transfer.</span></span>                                           |
| <span data-ttu-id="fb44a-177">sourcePartnerTenantId</span><span class="sxs-lookup"><span data-stu-id="fb44a-177">sourcePartnerTenantId</span></span> | <span data-ttu-id="fb44a-178">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-178">string</span></span>        | <span data-ttu-id="fb44a-179">Yes</span><span class="sxs-lookup"><span data-stu-id="fb44a-179">Yes</span></span>   | <span data-ttu-id="fb44a-180">Een door de GUID opgemaakte partner-id waarmee de partner wordt geïdentificeerd die de overdracht initieert.</span><span class="sxs-lookup"><span data-stu-id="fb44a-180">A GUID formatted partner-id that identifies the partner initiating the transfer.</span></span>                                           |
| <span data-ttu-id="fb44a-181">targetPartnerName</span><span class="sxs-lookup"><span data-stu-id="fb44a-181">targetPartnerName</span></span>     | <span data-ttu-id="fb44a-182">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-182">string</span></span>        | <span data-ttu-id="fb44a-183">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-183">No</span></span>    | <span data-ttu-id="fb44a-184">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="fb44a-184">Optional.</span></span> <span data-ttu-id="fb44a-185">De naam van de organisatie van de partner waarop de overdracht is gericht.</span><span class="sxs-lookup"><span data-stu-id="fb44a-185">The name of the partner's organization to whom the transfer is targeted.</span></span>                                         |
| <span data-ttu-id="fb44a-186">targetPartnerTenantId</span><span class="sxs-lookup"><span data-stu-id="fb44a-186">targetPartnerTenantId</span></span> | <span data-ttu-id="fb44a-187">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-187">string</span></span>        | <span data-ttu-id="fb44a-188">Yes</span><span class="sxs-lookup"><span data-stu-id="fb44a-188">Yes</span></span>   | <span data-ttu-id="fb44a-189">Een door de GUID opgemaakte partner-id waarmee de partner wordt geïdentificeerd voor wie de overdracht is gericht.</span><span class="sxs-lookup"><span data-stu-id="fb44a-189">A GUID formatted partner-id that identifies the partner to whom the transfer is targeted.</span></span>                                  |
| <span data-ttu-id="fb44a-190">Regel items</span><span class="sxs-lookup"><span data-stu-id="fb44a-190">lineItems</span></span>             | <span data-ttu-id="fb44a-191">Matrix van objecten</span><span class="sxs-lookup"><span data-stu-id="fb44a-191">Array of objects</span></span> | <span data-ttu-id="fb44a-192">Yes</span><span class="sxs-lookup"><span data-stu-id="fb44a-192">Yes</span></span>| <span data-ttu-id="fb44a-193">Een matrix met [TransferLineItem](transfer-entity-resources.md#transferlineitem) -resources.</span><span class="sxs-lookup"><span data-stu-id="fb44a-193">An Array of [TransferLineItem](transfer-entity-resources.md#transferlineitem) resources.</span></span>                                   |
| <span data-ttu-id="fb44a-194">status</span><span class="sxs-lookup"><span data-stu-id="fb44a-194">status</span></span>                | <span data-ttu-id="fb44a-195">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-195">string</span></span>        | <span data-ttu-id="fb44a-196">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-196">No</span></span>    | <span data-ttu-id="fb44a-197">De status van de transferEntity.</span><span class="sxs-lookup"><span data-stu-id="fb44a-197">The status of the transferEntity.</span></span> <span data-ttu-id="fb44a-198">Mogelijke waarden zijn ' Active ' (kunnen worden verwijderd/verzonden) en ' voltooid ' (is al voltooid).</span><span class="sxs-lookup"><span data-stu-id="fb44a-198">Possible values are "Active" (can be deleted/submitted) and "Completed" (has already been completed).</span></span> <span data-ttu-id="fb44a-199">Wordt toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fb44a-199">Applied upon successful creation of the transferEntity.</span></span>|

<span data-ttu-id="fb44a-200">In deze tabel worden de eigenschappen van [TransferLineItem](transfer-entity-resources.md#transferlineitem) in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="fb44a-200">This table describes the [TransferLineItem](transfer-entity-resources.md#transferlineitem) properties in the request body.</span></span>

|      <span data-ttu-id="fb44a-201">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="fb44a-201">Property</span></span>       |            <span data-ttu-id="fb44a-202">Type</span><span class="sxs-lookup"><span data-stu-id="fb44a-202">Type</span></span>             | <span data-ttu-id="fb44a-203">Vereist</span><span class="sxs-lookup"><span data-stu-id="fb44a-203">Required</span></span> | <span data-ttu-id="fb44a-204">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fb44a-204">Description</span></span>                                                                                     |
|---------------------|-----------------------------|----------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="fb44a-205">id</span><span class="sxs-lookup"><span data-stu-id="fb44a-205">id</span></span>                   | <span data-ttu-id="fb44a-206">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-206">string</span></span>                     | <span data-ttu-id="fb44a-207">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-207">No</span></span>       | <span data-ttu-id="fb44a-208">Een unieke id voor een regel item voor de overdracht.</span><span class="sxs-lookup"><span data-stu-id="fb44a-208">A unique identifier for a transfer line item.</span></span> <span data-ttu-id="fb44a-209">Wordt toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fb44a-209">Applied upon successful creation of the transferEntity.</span></span>|
| <span data-ttu-id="fb44a-210">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="fb44a-210">subscriptionId</span></span>       | <span data-ttu-id="fb44a-211">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-211">string</span></span>                     | <span data-ttu-id="fb44a-212">Yes</span><span class="sxs-lookup"><span data-stu-id="fb44a-212">Yes</span></span>      | <span data-ttu-id="fb44a-213">De abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="fb44a-213">The subscription identifier.</span></span>                                                                         |
| <span data-ttu-id="fb44a-214">quantity</span><span class="sxs-lookup"><span data-stu-id="fb44a-214">quantity</span></span>             | <span data-ttu-id="fb44a-215">int</span><span class="sxs-lookup"><span data-stu-id="fb44a-215">int</span></span>                        | <span data-ttu-id="fb44a-216">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-216">No</span></span>       | <span data-ttu-id="fb44a-217">Het aantal licenties of exemplaren.</span><span class="sxs-lookup"><span data-stu-id="fb44a-217">The number of licenses or instances.</span></span>                                                                 |
| <span data-ttu-id="fb44a-218">billingCycle</span><span class="sxs-lookup"><span data-stu-id="fb44a-218">billingCycle</span></span>         | <span data-ttu-id="fb44a-219">Object</span><span class="sxs-lookup"><span data-stu-id="fb44a-219">Object</span></span>                     | <span data-ttu-id="fb44a-220">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-220">No</span></span>       | <span data-ttu-id="fb44a-221">Het type facturerings cyclus dat voor de huidige periode is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="fb44a-221">The type of billing cycle set for the current period.</span></span>                                                |
| <span data-ttu-id="fb44a-222">friendlyName</span><span class="sxs-lookup"><span data-stu-id="fb44a-222">friendlyName</span></span>         | <span data-ttu-id="fb44a-223">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-223">string</span></span>                     | <span data-ttu-id="fb44a-224">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-224">No</span></span>       | <span data-ttu-id="fb44a-225">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="fb44a-225">Optional.</span></span> <span data-ttu-id="fb44a-226">De beschrijvende naam voor het item dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.</span><span class="sxs-lookup"><span data-stu-id="fb44a-226">The friendly name for the item defined by the partner to help disambiguate.</span></span>                |
| <span data-ttu-id="fb44a-227">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="fb44a-227">partnerIdOnRecord</span></span>    | <span data-ttu-id="fb44a-228">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-228">string</span></span>                     | <span data-ttu-id="fb44a-229">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-229">No</span></span>       | <span data-ttu-id="fb44a-230">Partner on record (MPNID) voor de aankoop die plaatsvindt wanneer de overdracht wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="fb44a-230">PartnerId on Record (MPNID) on the purchase that happens when the transfer is accepted.</span></span>              |
| <span data-ttu-id="fb44a-231">offerId</span><span class="sxs-lookup"><span data-stu-id="fb44a-231">offerId</span></span>              | <span data-ttu-id="fb44a-232">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-232">string</span></span>                     | <span data-ttu-id="fb44a-233">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-233">No</span></span>       | <span data-ttu-id="fb44a-234">De aanbiedings-id.</span><span class="sxs-lookup"><span data-stu-id="fb44a-234">The offer identifier.</span></span>                                                                                |
| <span data-ttu-id="fb44a-235">addonItems</span><span class="sxs-lookup"><span data-stu-id="fb44a-235">addonItems</span></span>           | <span data-ttu-id="fb44a-236">Lijst met **TransferLineItem** -objecten</span><span class="sxs-lookup"><span data-stu-id="fb44a-236">List of **TransferLineItem** objects</span></span> | <span data-ttu-id="fb44a-237">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-237">No</span></span> | <span data-ttu-id="fb44a-238">Een verzameling transferEntity-regel items voor addons die worden overgedragen samen met het basis abonnement dat wordt overgedragen.</span><span class="sxs-lookup"><span data-stu-id="fb44a-238">A collection of transferEntity line items for addons that will be transferred along with the base subscription that is being transferred.</span></span> <span data-ttu-id="fb44a-239">Wordt toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="fb44a-239">Applied upon successful creation of the transferEntity.</span></span>|
| <span data-ttu-id="fb44a-240">transferError</span><span class="sxs-lookup"><span data-stu-id="fb44a-240">transferError</span></span>        | <span data-ttu-id="fb44a-241">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-241">string</span></span>                     | <span data-ttu-id="fb44a-242">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-242">No</span></span>       | <span data-ttu-id="fb44a-243">Wordt toegepast nadat transferEntity is geaccepteerd in het geval van een fout.</span><span class="sxs-lookup"><span data-stu-id="fb44a-243">Applied after transferEntity is accepted in case of an error.</span></span>                                        |
| <span data-ttu-id="fb44a-244">status</span><span class="sxs-lookup"><span data-stu-id="fb44a-244">status</span></span>               | <span data-ttu-id="fb44a-245">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fb44a-245">string</span></span>                     | <span data-ttu-id="fb44a-246">No</span><span class="sxs-lookup"><span data-stu-id="fb44a-246">No</span></span>       | <span data-ttu-id="fb44a-247">De status van de lineitem in de transferEntity.</span><span class="sxs-lookup"><span data-stu-id="fb44a-247">The status of the lineitem in the transferEntity.</span></span>                                                    |

### <a name="request-example"></a><span data-ttu-id="fb44a-248">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fb44a-248">Request example</span></span>

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/transfers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-7294a10ae1cf
MS-CorrelationId: 0e93c70c-977c-4a88-9580-7cf084c73286
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Expect: 100-continue

{
    "sourcePartnerTenantId": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "targetPartnerTenantId": "656218b1-80c9-40b2-83ae-3a2703b55271",
    "lineItems": [
        {
            "subscriptionId": "7291BFBF-1772-4C5B-A624-18B6152CD8CB",
            "partnerIdOnRecord": "517285"
        },
        {
            "subscriptionId": "6C0B221B-8DF9-4F4A-A5BB-4C9CBB7B27B0",
            "partnerIdOnRecord": "517285"
        }
    ]
}
```

## <a name="rest-response"></a><span data-ttu-id="fb44a-249">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fb44a-249">REST response</span></span>

<span data-ttu-id="fb44a-250">Als dit lukt, retourneert deze methode de gevulde [TransferEnity](transfer-entity-resources.md) -resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="fb44a-250">If successful, this method returns the populated [TransferEnity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fb44a-251">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="fb44a-251">Response success and error codes</span></span>

<span data-ttu-id="fb44a-252">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="fb44a-252">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fb44a-253">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fb44a-253">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fb44a-254">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="fb44a-254">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fb44a-255">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fb44a-255">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 138
Content-Type: application/json; charset=utf-8
MS-RequestId: 4fa6dad6-a89f-4875-8247-7294a10ae1cf
MS-CorrelationId: 0e93c70c-977c-4a88-9580-7cf084c73286
X-Locale: en-US,en-US
{
    "id": "67c5b05b-09b5-47ba-9047-5056fe2afa4f",
    "status": "Active",
    "createdTime": "2020-03-24T20:44:14.9602781Z",
    "lastModifiedTime": "2020-03-24T20:44:15Z",
    "customerTenantId": "823c6c3f-9259-4d51-bae2-5dd06743177f",
    "partnertenantid": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "sourcePartnerTenantId": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "targetPartnerTenantId": "656218b1-80c9-40b2-83ae-3a2703b55271",
    "lastModifiedUser": "d0648481-b615-45c9-8cd1-ff87940dbdc4",
    "lineItems": [
        {
            "id": 0,
            "subscriptionId": "7291BFBF-1772-4C5B-A624-18B6152CD8CB",
            "offerId": "50E9A47A-7B4D-4970-9D90-CAE927F53753",
            "billingCycle": "annual",
            "friendlyName": "Dynamics 365 for Sales Enterprise Attach to Qualifying Dynamics 365 Base Offer",
            "quantity": 1,
            "addonItems": [
                {
                    "id": 0,
                    "subscriptionId": "D738C6C9-DDBD-46E9-B316-65F9D9B3ECB4",
                    "offerId": "2BCF9FE8-8B65-4FCF-9240-419203FB8CF4",
                    "billingCycle": "annual",
                    "friendlyName": "Dynamics 365 - Additional Production Instance (Qualified Offer)",
                    "quantity": 4
                }
            ]
        },
        {
            "id": 0,
            "subscriptionId": "6C0B221B-8DF9-4F4A-A5BB-4C9CBB7B27B0",
            "offerId": "455DDD41-32ED-4E2D-B3A2-BBCB22CAA467",
            "billingCycle": "annual",
            "friendlyName": "Dynamics 365 Customer Engagement Plan Patch",
            "quantity": 8,
            "addonItems": []
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/823c6c3f-9259-4d51-bae2-5dd06743177f/transfers/67c5b05b-09b5-47ba-9047-5056fe2afa4f",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "TransferEntity"
    }
}
```
