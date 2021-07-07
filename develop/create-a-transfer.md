---
title: Een overdracht maken
description: Een overdracht van abonnementen voor een klant maken.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d459a0a96912ab27f312bc73af16af2d4fdb518c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973703"
---
# <a name="create-a-transfer"></a><span data-ttu-id="e8328-103">Een overdracht maken</span><span class="sxs-lookup"><span data-stu-id="e8328-103">Create a transfer</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e8328-104">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e8328-104">Prerequisites</span></span>

- <span data-ttu-id="e8328-105">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e8328-105">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e8328-106">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e8328-106">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="e8328-107">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e8328-107">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="e8328-108">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="e8328-108">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="e8328-109">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="e8328-109">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="e8328-110">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="e8328-110">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="e8328-111">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="e8328-111">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="e8328-112">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="e8328-112">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="rest-request"></a><span data-ttu-id="e8328-113">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e8328-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e8328-114">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e8328-114">Request syntax</span></span>

| <span data-ttu-id="e8328-115">Methode</span><span class="sxs-lookup"><span data-stu-id="e8328-115">Method</span></span>   | <span data-ttu-id="e8328-116">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e8328-116">Request URI</span></span>                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e8328-117">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="e8328-117">**POST**</span></span> | <span data-ttu-id="e8328-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e8328-118">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers HTTP/1.1</span></span>                    |

### <a name="uri-parameter"></a><span data-ttu-id="e8328-119">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="e8328-119">URI parameter</span></span>

<span data-ttu-id="e8328-120">Gebruik de volgende padparameter om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="e8328-120">Use the following path parameter to identify the customer.</span></span>

| <span data-ttu-id="e8328-121">Naam</span><span class="sxs-lookup"><span data-stu-id="e8328-121">Name</span></span>            | <span data-ttu-id="e8328-122">Type</span><span class="sxs-lookup"><span data-stu-id="e8328-122">Type</span></span>     | <span data-ttu-id="e8328-123">Vereist</span><span class="sxs-lookup"><span data-stu-id="e8328-123">Required</span></span> | <span data-ttu-id="e8328-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e8328-124">Description</span></span>                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="e8328-125">**customer-id**</span><span class="sxs-lookup"><span data-stu-id="e8328-125">**customer-id**</span></span> | <span data-ttu-id="e8328-126">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-126">string</span></span>   | <span data-ttu-id="e8328-127">Ja</span><span class="sxs-lookup"><span data-stu-id="e8328-127">Yes</span></span>      | <span data-ttu-id="e8328-128">Een met GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="e8328-128">A GUID formatted customer-id that identifies the customer.</span></span>             |

### <a name="request-headers"></a><span data-ttu-id="e8328-129">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e8328-129">Request headers</span></span>

<span data-ttu-id="e8328-130">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e8328-130">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e8328-131">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e8328-131">Request body</span></span>

<span data-ttu-id="e8328-132">In deze tabel worden de [Eigenschappen van TransferEntity](transfer-entity-resources.md) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="e8328-132">This table describes the [TransferEntity](transfer-entity-resources.md) properties in the request body.</span></span>

| <span data-ttu-id="e8328-133">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="e8328-133">Property</span></span>              | <span data-ttu-id="e8328-134">Type</span><span class="sxs-lookup"><span data-stu-id="e8328-134">Type</span></span>          | <span data-ttu-id="e8328-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="e8328-135">Required</span></span>  | <span data-ttu-id="e8328-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e8328-136">Description</span></span>                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| <span data-ttu-id="e8328-137">id</span><span class="sxs-lookup"><span data-stu-id="e8328-137">id</span></span>                    | <span data-ttu-id="e8328-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-138">string</span></span>        | <span data-ttu-id="e8328-139">No</span><span class="sxs-lookup"><span data-stu-id="e8328-139">No</span></span>    | <span data-ttu-id="e8328-140">Een transferEntity-id die wordt opgegeven wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e8328-140">A transferEntity identifier that is supplied upon successful creation of the transferEntity.</span></span>                               |
| <span data-ttu-id="e8328-141">createdTime</span><span class="sxs-lookup"><span data-stu-id="e8328-141">createdTime</span></span>           | <span data-ttu-id="e8328-142">DateTime</span><span class="sxs-lookup"><span data-stu-id="e8328-142">DateTime</span></span>      | <span data-ttu-id="e8328-143">Nee</span><span class="sxs-lookup"><span data-stu-id="e8328-143">No</span></span>    | <span data-ttu-id="e8328-144">De datum waarop de transferEntity is gemaakt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="e8328-144">The date the transferEntity was created, in date-time format.</span></span> <span data-ttu-id="e8328-145">Toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e8328-145">Applied upon successful creation of the transferEntity.</span></span>      |
| <span data-ttu-id="e8328-146">lastModifiedTime</span><span class="sxs-lookup"><span data-stu-id="e8328-146">lastModifiedTime</span></span>      | <span data-ttu-id="e8328-147">DateTime</span><span class="sxs-lookup"><span data-stu-id="e8328-147">DateTime</span></span>      | <span data-ttu-id="e8328-148">Nee</span><span class="sxs-lookup"><span data-stu-id="e8328-148">No</span></span>    | <span data-ttu-id="e8328-149">De datum waarop de transferEntity voor het laatst is bijgewerkt, in datum/tijd-indeling.</span><span class="sxs-lookup"><span data-stu-id="e8328-149">The date the transferEntity was last updated, in date-time format.</span></span> <span data-ttu-id="e8328-150">Toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e8328-150">Applied upon successful creation of the transferEntity.</span></span> |
| <span data-ttu-id="e8328-151">lastModifiedUser</span><span class="sxs-lookup"><span data-stu-id="e8328-151">lastModifiedUser</span></span>      | <span data-ttu-id="e8328-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-152">string</span></span>        | <span data-ttu-id="e8328-153">No</span><span class="sxs-lookup"><span data-stu-id="e8328-153">No</span></span>    | <span data-ttu-id="e8328-154">De gebruiker die voor het laatst de transferEntity heeft bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="e8328-154">The user who last updated the transferEntity.</span></span> <span data-ttu-id="e8328-155">Toegepast bij het maken van transferEntity.</span><span class="sxs-lookup"><span data-stu-id="e8328-155">Applied upon successful creation of transferEntity.</span></span>                          |
| <span data-ttu-id="e8328-156">customerName</span><span class="sxs-lookup"><span data-stu-id="e8328-156">customerName</span></span>          | <span data-ttu-id="e8328-157">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-157">string</span></span>        | <span data-ttu-id="e8328-158">No</span><span class="sxs-lookup"><span data-stu-id="e8328-158">No</span></span>    | <span data-ttu-id="e8328-159">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="e8328-159">Optional.</span></span> <span data-ttu-id="e8328-160">De naam van de klant van wie de abonnementen worden overgedragen.</span><span class="sxs-lookup"><span data-stu-id="e8328-160">The name of the customer whose subscriptions are being transferred.</span></span>                                              |
| <span data-ttu-id="e8328-161">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="e8328-161">customerTenantId</span></span>      | <span data-ttu-id="e8328-162">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-162">string</span></span>        | <span data-ttu-id="e8328-163">No</span><span class="sxs-lookup"><span data-stu-id="e8328-163">No</span></span>    | <span data-ttu-id="e8328-164">Een met GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="e8328-164">A GUID formatted customer-id that identifies the customer.</span></span> <span data-ttu-id="e8328-165">Toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e8328-165">Applied upon successful creation of the transferEntity.</span></span>         |
| <span data-ttu-id="e8328-166">partnertenantid</span><span class="sxs-lookup"><span data-stu-id="e8328-166">partnertenantid</span></span>       | <span data-ttu-id="e8328-167">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-167">string</span></span>        | <span data-ttu-id="e8328-168">No</span><span class="sxs-lookup"><span data-stu-id="e8328-168">No</span></span>    | <span data-ttu-id="e8328-169">Een partner-id met GUID-indeling die de partner identificeert.</span><span class="sxs-lookup"><span data-stu-id="e8328-169">A GUID formatted partner-id that identifies the partner.</span></span>                                                                   |
| <span data-ttu-id="e8328-170">sourcePartnerName</span><span class="sxs-lookup"><span data-stu-id="e8328-170">sourcePartnerName</span></span>     | <span data-ttu-id="e8328-171">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-171">string</span></span>        | <span data-ttu-id="e8328-172">No</span><span class="sxs-lookup"><span data-stu-id="e8328-172">No</span></span>    | <span data-ttu-id="e8328-173">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="e8328-173">Optional.</span></span> <span data-ttu-id="e8328-174">De naam van de organisatie van de partner die de overdracht start.</span><span class="sxs-lookup"><span data-stu-id="e8328-174">The name of the partner's organization who is initiating the transfer.</span></span>                                           |
| <span data-ttu-id="e8328-175">sourcePartnerTenantId</span><span class="sxs-lookup"><span data-stu-id="e8328-175">sourcePartnerTenantId</span></span> | <span data-ttu-id="e8328-176">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-176">string</span></span>        | <span data-ttu-id="e8328-177">Ja</span><span class="sxs-lookup"><span data-stu-id="e8328-177">Yes</span></span>   | <span data-ttu-id="e8328-178">Een partner-id met GUID-indeling die de partner identificeert die de overdracht start.</span><span class="sxs-lookup"><span data-stu-id="e8328-178">A GUID formatted partner-id that identifies the partner initiating the transfer.</span></span>                                           |
| <span data-ttu-id="e8328-179">targetPartnerName</span><span class="sxs-lookup"><span data-stu-id="e8328-179">targetPartnerName</span></span>     | <span data-ttu-id="e8328-180">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-180">string</span></span>        | <span data-ttu-id="e8328-181">No</span><span class="sxs-lookup"><span data-stu-id="e8328-181">No</span></span>    | <span data-ttu-id="e8328-182">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="e8328-182">Optional.</span></span> <span data-ttu-id="e8328-183">De naam van de organisatie van de partner waarop de overdracht is gericht.</span><span class="sxs-lookup"><span data-stu-id="e8328-183">The name of the partner's organization to whom the transfer is targeted.</span></span>                                         |
| <span data-ttu-id="e8328-184">targetPartnerTenantId</span><span class="sxs-lookup"><span data-stu-id="e8328-184">targetPartnerTenantId</span></span> | <span data-ttu-id="e8328-185">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-185">string</span></span>        | <span data-ttu-id="e8328-186">Ja</span><span class="sxs-lookup"><span data-stu-id="e8328-186">Yes</span></span>   | <span data-ttu-id="e8328-187">Een partner-id met GUID-indeling die de partner identificeert waarop de overdracht is gericht.</span><span class="sxs-lookup"><span data-stu-id="e8328-187">A GUID formatted partner-id that identifies the partner to whom the transfer is targeted.</span></span>                                  |
| <span data-ttu-id="e8328-188">lineItems</span><span class="sxs-lookup"><span data-stu-id="e8328-188">lineItems</span></span>             | <span data-ttu-id="e8328-189">Matrix met objecten</span><span class="sxs-lookup"><span data-stu-id="e8328-189">Array of objects</span></span> | <span data-ttu-id="e8328-190">Ja</span><span class="sxs-lookup"><span data-stu-id="e8328-190">Yes</span></span>| <span data-ttu-id="e8328-191">Een matrix van [TransferLineItem-resources.](transfer-entity-resources.md#transferlineitem)</span><span class="sxs-lookup"><span data-stu-id="e8328-191">An Array of [TransferLineItem](transfer-entity-resources.md#transferlineitem) resources.</span></span>                                   |
| <span data-ttu-id="e8328-192">status</span><span class="sxs-lookup"><span data-stu-id="e8328-192">status</span></span>                | <span data-ttu-id="e8328-193">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-193">string</span></span>        | <span data-ttu-id="e8328-194">No</span><span class="sxs-lookup"><span data-stu-id="e8328-194">No</span></span>    | <span data-ttu-id="e8328-195">De status van de transferEntity.</span><span class="sxs-lookup"><span data-stu-id="e8328-195">The status of the transferEntity.</span></span> <span data-ttu-id="e8328-196">Mogelijke waarden zijn 'Actief' (kan worden verwijderd/verzonden) en 'Voltooid' (is al voltooid).</span><span class="sxs-lookup"><span data-stu-id="e8328-196">Possible values are "Active" (can be deleted/submitted) and "Completed" (has already been completed).</span></span> <span data-ttu-id="e8328-197">Toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e8328-197">Applied upon successful creation of the transferEntity.</span></span>|

<span data-ttu-id="e8328-198">In deze tabel worden de [eigenschappen van TransferLineItem](transfer-entity-resources.md#transferlineitem) in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="e8328-198">This table describes the [TransferLineItem](transfer-entity-resources.md#transferlineitem) properties in the request body.</span></span>

|      <span data-ttu-id="e8328-199">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="e8328-199">Property</span></span>       |            <span data-ttu-id="e8328-200">Type</span><span class="sxs-lookup"><span data-stu-id="e8328-200">Type</span></span>             | <span data-ttu-id="e8328-201">Vereist</span><span class="sxs-lookup"><span data-stu-id="e8328-201">Required</span></span> | <span data-ttu-id="e8328-202">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e8328-202">Description</span></span>                                                                                     |
|---------------------|-----------------------------|----------|-------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e8328-203">id</span><span class="sxs-lookup"><span data-stu-id="e8328-203">id</span></span>                   | <span data-ttu-id="e8328-204">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-204">string</span></span>                     | <span data-ttu-id="e8328-205">No</span><span class="sxs-lookup"><span data-stu-id="e8328-205">No</span></span>       | <span data-ttu-id="e8328-206">Een unieke id voor een overdrachtsregelitem.</span><span class="sxs-lookup"><span data-stu-id="e8328-206">A unique identifier for a transfer line item.</span></span> <span data-ttu-id="e8328-207">Toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e8328-207">Applied upon successful creation of the transferEntity.</span></span>|
| <span data-ttu-id="e8328-208">subscriptionId</span><span class="sxs-lookup"><span data-stu-id="e8328-208">subscriptionId</span></span>       | <span data-ttu-id="e8328-209">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-209">string</span></span>                     | <span data-ttu-id="e8328-210">Ja</span><span class="sxs-lookup"><span data-stu-id="e8328-210">Yes</span></span>      | <span data-ttu-id="e8328-211">De abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="e8328-211">The subscription identifier.</span></span>                                                                         |
| <span data-ttu-id="e8328-212">quantity</span><span class="sxs-lookup"><span data-stu-id="e8328-212">quantity</span></span>             | <span data-ttu-id="e8328-213">int</span><span class="sxs-lookup"><span data-stu-id="e8328-213">int</span></span>                        | <span data-ttu-id="e8328-214">Nee</span><span class="sxs-lookup"><span data-stu-id="e8328-214">No</span></span>       | <span data-ttu-id="e8328-215">Het aantal licenties of exemplaren.</span><span class="sxs-lookup"><span data-stu-id="e8328-215">The number of licenses or instances.</span></span>                                                                 |
| <span data-ttu-id="e8328-216">billingCycle</span><span class="sxs-lookup"><span data-stu-id="e8328-216">billingCycle</span></span>         | <span data-ttu-id="e8328-217">Object</span><span class="sxs-lookup"><span data-stu-id="e8328-217">Object</span></span>                     | <span data-ttu-id="e8328-218">Nee</span><span class="sxs-lookup"><span data-stu-id="e8328-218">No</span></span>       | <span data-ttu-id="e8328-219">Het type factureringscyclus dat is ingesteld voor de huidige periode.</span><span class="sxs-lookup"><span data-stu-id="e8328-219">The type of billing cycle set for the current period.</span></span>                                                |
| <span data-ttu-id="e8328-220">Friendlyname</span><span class="sxs-lookup"><span data-stu-id="e8328-220">friendlyName</span></span>         | <span data-ttu-id="e8328-221">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-221">string</span></span>                     | <span data-ttu-id="e8328-222">No</span><span class="sxs-lookup"><span data-stu-id="e8328-222">No</span></span>       | <span data-ttu-id="e8328-223">Optioneel.</span><span class="sxs-lookup"><span data-stu-id="e8328-223">Optional.</span></span> <span data-ttu-id="e8328-224">De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.</span><span class="sxs-lookup"><span data-stu-id="e8328-224">The friendly name for the item defined by the partner to help disambiguate.</span></span>                |
| <span data-ttu-id="e8328-225">partnerIdOnRecord</span><span class="sxs-lookup"><span data-stu-id="e8328-225">partnerIdOnRecord</span></span>    | <span data-ttu-id="e8328-226">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-226">string</span></span>                     | <span data-ttu-id="e8328-227">No</span><span class="sxs-lookup"><span data-stu-id="e8328-227">No</span></span>       | <span data-ttu-id="e8328-228">PartnerId on Record (MPN-id) voor de aankoop die wordt gedaan wanneer de overdracht wordt geaccepteerd.</span><span class="sxs-lookup"><span data-stu-id="e8328-228">PartnerId on Record (MPN ID) on the purchase that happens when the transfer is accepted.</span></span>              |
| <span data-ttu-id="e8328-229">offerId</span><span class="sxs-lookup"><span data-stu-id="e8328-229">offerId</span></span>              | <span data-ttu-id="e8328-230">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-230">string</span></span>                     | <span data-ttu-id="e8328-231">No</span><span class="sxs-lookup"><span data-stu-id="e8328-231">No</span></span>       | <span data-ttu-id="e8328-232">De aanbiedings-id.</span><span class="sxs-lookup"><span data-stu-id="e8328-232">The offer identifier.</span></span>                                                                                |
| <span data-ttu-id="e8328-233">addonItems</span><span class="sxs-lookup"><span data-stu-id="e8328-233">addonItems</span></span>           | <span data-ttu-id="e8328-234">Lijst met **TransferLineItem-objecten**</span><span class="sxs-lookup"><span data-stu-id="e8328-234">List of **TransferLineItem** objects</span></span> | <span data-ttu-id="e8328-235">Nee</span><span class="sxs-lookup"><span data-stu-id="e8328-235">No</span></span> | <span data-ttu-id="e8328-236">Een verzameling transferEntity-regelitems voor addons die samen met het basisabonnement dat wordt overgedragen, worden overgedragen.</span><span class="sxs-lookup"><span data-stu-id="e8328-236">A collection of transferEntity line items for addons that will be transferred along with the base subscription that is being transferred.</span></span> <span data-ttu-id="e8328-237">Toegepast wanneer de transferEntity is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="e8328-237">Applied upon successful creation of the transferEntity.</span></span>|
| <span data-ttu-id="e8328-238">transferError</span><span class="sxs-lookup"><span data-stu-id="e8328-238">transferError</span></span>        | <span data-ttu-id="e8328-239">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-239">string</span></span>                     | <span data-ttu-id="e8328-240">No</span><span class="sxs-lookup"><span data-stu-id="e8328-240">No</span></span>       | <span data-ttu-id="e8328-241">Toegepast nadat transferEntity is geaccepteerd als er een fout is opgetreden.</span><span class="sxs-lookup"><span data-stu-id="e8328-241">Applied after transferEntity is accepted if there is an error.</span></span>                                        |
| <span data-ttu-id="e8328-242">status</span><span class="sxs-lookup"><span data-stu-id="e8328-242">status</span></span>               | <span data-ttu-id="e8328-243">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8328-243">string</span></span>                     | <span data-ttu-id="e8328-244">No</span><span class="sxs-lookup"><span data-stu-id="e8328-244">No</span></span>       | <span data-ttu-id="e8328-245">De status van het regelitem in de transferEntity.</span><span class="sxs-lookup"><span data-stu-id="e8328-245">The status of the lineitem in the transferEntity.</span></span>                                                    |

### <a name="request-example"></a><span data-ttu-id="e8328-246">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e8328-246">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e8328-247">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e8328-247">REST response</span></span>

<span data-ttu-id="e8328-248">Als dit lukt, retourneert deze methode de ingevulde [TransferEnity-resource](transfer-entity-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="e8328-248">If successful, this method returns the populated [TransferEnity](transfer-entity-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e8328-249">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e8328-249">Response success and error codes</span></span>

<span data-ttu-id="e8328-250">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e8328-250">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e8328-251">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e8328-251">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e8328-252">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e8328-252">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e8328-253">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e8328-253">Response example</span></span>

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
