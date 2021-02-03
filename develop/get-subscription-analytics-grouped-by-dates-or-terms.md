---
title: Abonnements analyse gegroepeerd op datum of voor waarden ophalen
description: Informatie over abonnements analyse weer geven gegroepeerd op datum of voor waarden.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4a9946027fa89f5a93fff5eede86e36a6be5b721
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767278"
---
# <a name="get-subscription-analytics-grouped-by-dates-or-terms"></a><span data-ttu-id="90ec2-103">Abonnements analyse gegroepeerd op datum of voor waarden ophalen</span><span class="sxs-lookup"><span data-stu-id="90ec2-103">Get subscription analytics grouped by dates or terms</span></span>

<span data-ttu-id="90ec2-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="90ec2-104">**Applies To**</span></span>

- <span data-ttu-id="90ec2-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="90ec2-105">Partner Center</span></span>
- <span data-ttu-id="90ec2-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="90ec2-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="90ec2-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="90ec2-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="90ec2-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="90ec2-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="90ec2-109">Informatie over abonnements analyse ophalen voor uw klanten, gegroepeerd op datum of voor waarden.</span><span class="sxs-lookup"><span data-stu-id="90ec2-109">How to get subscription analytics information for your customers grouped by dates or terms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="90ec2-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="90ec2-110">Prerequisites</span></span>

- <span data-ttu-id="90ec2-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="90ec2-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="90ec2-112">Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="90ec2-112">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="90ec2-113">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="90ec2-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="90ec2-114">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="90ec2-114">Request syntax</span></span>

| <span data-ttu-id="90ec2-115">Methode</span><span class="sxs-lookup"><span data-stu-id="90ec2-115">Method</span></span> | <span data-ttu-id="90ec2-116">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="90ec2-116">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="90ec2-117">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="90ec2-117">**GET**</span></span> | <span data-ttu-id="90ec2-118">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/Subscriptions? GroupBy = {groupby_queries}</span><span class="sxs-lookup"><span data-stu-id="90ec2-118">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?groupby={groupby_queries}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="90ec2-119">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="90ec2-119">URI parameters</span></span>

<span data-ttu-id="90ec2-120">Gebruik de volgende vereiste para meters voor het identificeren van uw organisatie en het groeperen van de resultaten.</span><span class="sxs-lookup"><span data-stu-id="90ec2-120">Use the following required path parameters to identify your organization and to group the results.</span></span>

| <span data-ttu-id="90ec2-121">Naam</span><span class="sxs-lookup"><span data-stu-id="90ec2-121">Name</span></span> | <span data-ttu-id="90ec2-122">Type</span><span class="sxs-lookup"><span data-stu-id="90ec2-122">Type</span></span> | <span data-ttu-id="90ec2-123">Vereist</span><span class="sxs-lookup"><span data-stu-id="90ec2-123">Required</span></span> | <span data-ttu-id="90ec2-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="90ec2-124">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="90ec2-125">groupby_queries</span><span class="sxs-lookup"><span data-stu-id="90ec2-125">groupby_queries</span></span> | <span data-ttu-id="90ec2-126">paren teken reeksen en datum/tijd</span><span class="sxs-lookup"><span data-stu-id="90ec2-126">pairs of strings and dateTime</span></span> | <span data-ttu-id="90ec2-127">Yes</span><span class="sxs-lookup"><span data-stu-id="90ec2-127">Yes</span></span> | <span data-ttu-id="90ec2-128">De voor waarden en datums waarop het resultaat moet worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="90ec2-128">The terms and dates to filter the result.</span></span> |

### <a name="groupby-syntax"></a><span data-ttu-id="90ec2-129">De syntaxis GroupBy</span><span class="sxs-lookup"><span data-stu-id="90ec2-129">GroupBy syntax</span></span>

<span data-ttu-id="90ec2-130">De Group by-para meter moet zijn samengesteld als een reeks door komma's gescheiden, veld waarden.</span><span class="sxs-lookup"><span data-stu-id="90ec2-130">The group by parameter must be composed as a series of comma separated, field values.</span></span>

<span data-ttu-id="90ec2-131">Een niet-gecodeerd voor beeld ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="90ec2-131">An unencoded example looks like this:</span></span>

```http
?groupby=termField1,dateField1,termField2
```

<span data-ttu-id="90ec2-132">In de volgende tabel ziet u een lijst met de ondersteunde velden voor Group by.</span><span class="sxs-lookup"><span data-stu-id="90ec2-132">The following table shows a list of the supported fields for group by.</span></span>

| <span data-ttu-id="90ec2-133">Veld</span><span class="sxs-lookup"><span data-stu-id="90ec2-133">Field</span></span> | <span data-ttu-id="90ec2-134">Type</span><span class="sxs-lookup"><span data-stu-id="90ec2-134">Type</span></span> | <span data-ttu-id="90ec2-135">Description</span><span class="sxs-lookup"><span data-stu-id="90ec2-135">Description</span></span> |
|-------|------|-------------|
| <span data-ttu-id="90ec2-136">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="90ec2-136">customerTenantId</span></span> | <span data-ttu-id="90ec2-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-137">string</span></span> | <span data-ttu-id="90ec2-138">Een teken reeks met een GUID-indeling die de Tenant van de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="90ec2-138">A GUID-formatted string that identifies the customer tenant.</span></span> |
| <span data-ttu-id="90ec2-139">customerName</span><span class="sxs-lookup"><span data-stu-id="90ec2-139">customerName</span></span> | <span data-ttu-id="90ec2-140">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-140">string</span></span> | <span data-ttu-id="90ec2-141">De naam van de klant.</span><span class="sxs-lookup"><span data-stu-id="90ec2-141">The name of the customer.</span></span> |
| <span data-ttu-id="90ec2-142">customerMarket</span><span class="sxs-lookup"><span data-stu-id="90ec2-142">customerMarket</span></span> | <span data-ttu-id="90ec2-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-143">string</span></span> | <span data-ttu-id="90ec2-144">Het land/de regio waarin de klant zaken doet.</span><span class="sxs-lookup"><span data-stu-id="90ec2-144">The country/region that the customer does business in.</span></span> |
| <span data-ttu-id="90ec2-145">id</span><span class="sxs-lookup"><span data-stu-id="90ec2-145">id</span></span> | <span data-ttu-id="90ec2-146">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-146">string</span></span> | <span data-ttu-id="90ec2-147">Een teken reeks met een GUID-indeling waarmee het abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="90ec2-147">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="90ec2-148">status</span><span class="sxs-lookup"><span data-stu-id="90ec2-148">status</span></span> | <span data-ttu-id="90ec2-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-149">string</span></span> | <span data-ttu-id="90ec2-150">De abonnements status.</span><span class="sxs-lookup"><span data-stu-id="90ec2-150">The subscription status.</span></span> <span data-ttu-id="90ec2-151">Ondersteunde waarden zijn: ' Active ', ' Suspended ' of ' provisioned '.</span><span class="sxs-lookup"><span data-stu-id="90ec2-151">Supported values are: "ACTIVE", "SUSPENDED", or "DEPROVISIONED".</span></span> |
| <span data-ttu-id="90ec2-152">Product</span><span class="sxs-lookup"><span data-stu-id="90ec2-152">productName</span></span> | <span data-ttu-id="90ec2-153">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-153">string</span></span> | <span data-ttu-id="90ec2-154">De naam van het product.</span><span class="sxs-lookup"><span data-stu-id="90ec2-154">The name of the product.</span></span> |
| <span data-ttu-id="90ec2-155">subscriptionType</span><span class="sxs-lookup"><span data-stu-id="90ec2-155">subscriptionType</span></span> | <span data-ttu-id="90ec2-156">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-156">string</span></span> | <span data-ttu-id="90ec2-157">Het type abonnement.</span><span class="sxs-lookup"><span data-stu-id="90ec2-157">The subscription type.</span></span> <span data-ttu-id="90ec2-158">Opmerking: dit veld is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="90ec2-158">Note: This field is case sensitive.</span></span> <span data-ttu-id="90ec2-159">Ondersteunde waarden zijn: ' Office ', ' Azure ', ' Microsoft365 ', ' Dynamics ', ' EMS '.</span><span class="sxs-lookup"><span data-stu-id="90ec2-159">Supported values are: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span></span> |
| <span data-ttu-id="90ec2-160">autoRenewEnabled</span><span class="sxs-lookup"><span data-stu-id="90ec2-160">autoRenewEnabled</span></span> | <span data-ttu-id="90ec2-161">Booleaans</span><span class="sxs-lookup"><span data-stu-id="90ec2-161">Boolean</span></span> | <span data-ttu-id="90ec2-162">Een waarde die aangeeft of het abonnement automatisch wordt vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="90ec2-162">A value indicating whether the subscription is renewed automatically.</span></span> |
| <span data-ttu-id="90ec2-163">Partner</span><span class="sxs-lookup"><span data-stu-id="90ec2-163">partnerId</span></span>  | <span data-ttu-id="90ec2-164">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-164">string</span></span> | <span data-ttu-id="90ec2-165">De MPN-ID.</span><span class="sxs-lookup"><span data-stu-id="90ec2-165">The MPN ID.</span></span> <span data-ttu-id="90ec2-166">Voor een rechtstreekse wederverkoper is deze para meter de MPN-ID van de partner.</span><span class="sxs-lookup"><span data-stu-id="90ec2-166">For a direct reseller, this parameter will be the MPN ID of the partner.</span></span> <span data-ttu-id="90ec2-167">Voor een indirecte wederverkoper is deze para meter de MPN-ID van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="90ec2-167">For an indirect reseller, this parameter will be the MPN ID of the indirect reseller.</span></span> |
| <span data-ttu-id="90ec2-168">friendlyName</span><span class="sxs-lookup"><span data-stu-id="90ec2-168">friendlyName</span></span> | <span data-ttu-id="90ec2-169">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-169">string</span></span> | <span data-ttu-id="90ec2-170">De naam van het abonnement.</span><span class="sxs-lookup"><span data-stu-id="90ec2-170">The name of the subscription.</span></span> |
| <span data-ttu-id="90ec2-171">partnerName</span><span class="sxs-lookup"><span data-stu-id="90ec2-171">partnerName</span></span> | <span data-ttu-id="90ec2-172">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-172">string</span></span> | <span data-ttu-id="90ec2-173">De naam van de partner voor wie het abonnement is aangeschaft</span><span class="sxs-lookup"><span data-stu-id="90ec2-173">Name of the partner for whom the subscription was purchased</span></span> |
| <span data-ttu-id="90ec2-174">providerName</span><span class="sxs-lookup"><span data-stu-id="90ec2-174">providerName</span></span> | <span data-ttu-id="90ec2-175">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-175">string</span></span> | <span data-ttu-id="90ec2-176">Wanneer abonnements transactie voor de indirecte wederverkoper is, is de naam van de provider de indirecte provider die het abonnement heeft gekocht.</span><span class="sxs-lookup"><span data-stu-id="90ec2-176">When subscription transaction is for the indirect reseller, provider name is the indirect provider who bought the subscription.</span></span>
| <span data-ttu-id="90ec2-177">creationDate</span><span class="sxs-lookup"><span data-stu-id="90ec2-177">creationDate</span></span> | <span data-ttu-id="90ec2-178">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="90ec2-178">string in UTC date time format</span></span> | <span data-ttu-id="90ec2-179">De datum waarop het abonnement is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="90ec2-179">The date the subscription was created.</span></span> |
| <span data-ttu-id="90ec2-180">effectiveStartDate</span><span class="sxs-lookup"><span data-stu-id="90ec2-180">effectiveStartDate</span></span> | <span data-ttu-id="90ec2-181">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="90ec2-181">string in UTC date time format</span></span> | <span data-ttu-id="90ec2-182">De datum waarop het abonnement wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="90ec2-182">The date the subscription starts.</span></span> |
| <span data-ttu-id="90ec2-183">commitmentEndDate</span><span class="sxs-lookup"><span data-stu-id="90ec2-183">commitmentEndDate</span></span> | <span data-ttu-id="90ec2-184">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="90ec2-184">string in UTC date time format</span></span> | <span data-ttu-id="90ec2-185">De datum waarop het abonnement eindigt.</span><span class="sxs-lookup"><span data-stu-id="90ec2-185">The date the subscription ends.</span></span> |
| <span data-ttu-id="90ec2-186">currentStateEndDate</span><span class="sxs-lookup"><span data-stu-id="90ec2-186">currentStateEndDate</span></span> | <span data-ttu-id="90ec2-187">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="90ec2-187">string in UTC date time format</span></span> | <span data-ttu-id="90ec2-188">De datum waarop de huidige status van het abonnement wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="90ec2-188">The date that the current status of the subscription will change.</span></span> |
| <span data-ttu-id="90ec2-189">trialToPaidConversionDate</span><span class="sxs-lookup"><span data-stu-id="90ec2-189">trialToPaidConversionDate</span></span> | <span data-ttu-id="90ec2-190">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="90ec2-190">string in UTC date time format</span></span> | <span data-ttu-id="90ec2-191">De datum waarop het abonnement wordt geconverteerd van een proef versie naar betaald.</span><span class="sxs-lookup"><span data-stu-id="90ec2-191">The date that the subscription converts from trial to paid.</span></span> <span data-ttu-id="90ec2-192">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="90ec2-192">The default value is null.</span></span> |
| <span data-ttu-id="90ec2-193">trialStartDate</span><span class="sxs-lookup"><span data-stu-id="90ec2-193">trialStartDate</span></span> | <span data-ttu-id="90ec2-194">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="90ec2-194">string in UTC date time format</span></span> | <span data-ttu-id="90ec2-195">De datum waarop de proef periode voor het abonnement is gestart.</span><span class="sxs-lookup"><span data-stu-id="90ec2-195">The date that the trial period for the subscription started.</span></span> <span data-ttu-id="90ec2-196">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="90ec2-196">The default value is null.</span></span> |
| <span data-ttu-id="90ec2-197">lastUsageDate</span><span class="sxs-lookup"><span data-stu-id="90ec2-197">lastUsageDate</span></span> | <span data-ttu-id="90ec2-198">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="90ec2-198">string in UTC date time format</span></span> | <span data-ttu-id="90ec2-199">De datum waarop het abonnement voor het laatst is gebruikt.</span><span class="sxs-lookup"><span data-stu-id="90ec2-199">The date that the subscription was last used.</span></span> <span data-ttu-id="90ec2-200">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="90ec2-200">The default value is null.</span></span> |
| <span data-ttu-id="90ec2-201">deprovisionedDate</span><span class="sxs-lookup"><span data-stu-id="90ec2-201">deprovisionedDate</span></span> | <span data-ttu-id="90ec2-202">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="90ec2-202">string in UTC date time format</span></span> | <span data-ttu-id="90ec2-203">De datum waarop het abonnement is ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="90ec2-203">The date that the subscription was deprovisioned.</span></span> <span data-ttu-id="90ec2-204">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="90ec2-204">The default value is null.</span></span> |
| <span data-ttu-id="90ec2-205">lastRenewalDate</span><span class="sxs-lookup"><span data-stu-id="90ec2-205">lastRenewalDate</span></span> | <span data-ttu-id="90ec2-206">teken reeks in UTC-datum tijd notatie</span><span class="sxs-lookup"><span data-stu-id="90ec2-206">string in UTC date time format</span></span> | <span data-ttu-id="90ec2-207">De datum waarop het abonnement voor het laatst is vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="90ec2-207">The date that the subscription was last renewed.</span></span> <span data-ttu-id="90ec2-208">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="90ec2-208">The default value is null.</span></span> |

### <a name="filter-fields"></a><span data-ttu-id="90ec2-209">Filter velden</span><span class="sxs-lookup"><span data-stu-id="90ec2-209">Filter fields</span></span>

<span data-ttu-id="90ec2-210">De volgende tabel bevat de optionele filter velden en de bijbehorende beschrijvingen:</span><span class="sxs-lookup"><span data-stu-id="90ec2-210">The following table lists optional filter fields and their descriptions:</span></span>

| <span data-ttu-id="90ec2-211">Veld</span><span class="sxs-lookup"><span data-stu-id="90ec2-211">Field</span></span> | <span data-ttu-id="90ec2-212">Type</span><span class="sxs-lookup"><span data-stu-id="90ec2-212">Type</span></span> |  <span data-ttu-id="90ec2-213">Description</span><span class="sxs-lookup"><span data-stu-id="90ec2-213">Description</span></span> |
|-------|------|--------------|
| <span data-ttu-id="90ec2-214">top</span><span class="sxs-lookup"><span data-stu-id="90ec2-214">top</span></span> | <span data-ttu-id="90ec2-215">int</span><span class="sxs-lookup"><span data-stu-id="90ec2-215">int</span></span> | <span data-ttu-id="90ec2-216">Het aantal rijen met gegevens dat in de aanvraag moet worden geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="90ec2-216">The number of rows of data to return in the request.</span></span> <span data-ttu-id="90ec2-217">Als de waarde niet is opgegeven, zijn de maximum waarde en de standaard waarde 10000.</span><span class="sxs-lookup"><span data-stu-id="90ec2-217">If the value isn't specified, the maximum value and the default value are 10000.</span></span> <span data-ttu-id="90ec2-218">Als er meer rijen in de query staan, bevat de antwoord tekst een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="90ec2-218">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |
| <span data-ttu-id="90ec2-219">skip</span><span class="sxs-lookup"><span data-stu-id="90ec2-219">skip</span></span> | <span data-ttu-id="90ec2-220">int</span><span class="sxs-lookup"><span data-stu-id="90ec2-220">int</span></span> | <span data-ttu-id="90ec2-221">Het aantal rijen dat in de query moet worden overgeslagen.</span><span class="sxs-lookup"><span data-stu-id="90ec2-221">The number of rows to skip in the query.</span></span> <span data-ttu-id="90ec2-222">Gebruik deze para meter om door grote gegevens sets te bladeren.</span><span class="sxs-lookup"><span data-stu-id="90ec2-222">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="90ec2-223">Bijvoorbeeld Top = 10000 en skip = 0 haalt de eerste 10000 rijen met gegevens op, Top = 10000 en skip = 10000 de volgende 10000 rijen met gegevens ophalen.</span><span class="sxs-lookup"><span data-stu-id="90ec2-223">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data.</span></span> |
| <span data-ttu-id="90ec2-224">filter</span><span class="sxs-lookup"><span data-stu-id="90ec2-224">filter</span></span> | <span data-ttu-id="90ec2-225">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-225">string</span></span> | <span data-ttu-id="90ec2-226">Een of meer instructies waarmee de rijen in het antwoord worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="90ec2-226">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="90ec2-227">Elke filter instructie bevat een veld naam uit de hoofd tekst van het antwoord en een waarde die is gekoppeld aan de **`eq`** , **`ne`** , of voor bepaalde velden, de **`contains`** operator.</span><span class="sxs-lookup"><span data-stu-id="90ec2-227">Each filter statement contains a field name from the response body and a value that are associated with the **`eq`**, **`ne`**, or for certain fields, the **`contains`** operator.</span></span> <span data-ttu-id="90ec2-228">Instructies kunnen worden gecombineerd met **`and`** of **`or`** .</span><span class="sxs-lookup"><span data-stu-id="90ec2-228">Statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="90ec2-229">Teken reeks waarden moeten tussen enkele aanhalings tekens in de filter parameter worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="90ec2-229">String values must be surrounded by single quotes in the filter parameter.</span></span> <span data-ttu-id="90ec2-230">Zie de volgende sectie voor een lijst met velden die kunnen worden gefilterd en de Opera tors die worden ondersteund door deze velden.</span><span class="sxs-lookup"><span data-stu-id="90ec2-230">See the following section for a list of fields that can be filtered and the operators that are supported with those fields.</span></span> |
| <span data-ttu-id="90ec2-231">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="90ec2-231">aggregationLevel</span></span> | <span data-ttu-id="90ec2-232">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-232">string</span></span> | <span data-ttu-id="90ec2-233">Hiermee geeft u het tijds bereik op waarvoor u de samengevoegde gegevens wilt ophalen.</span><span class="sxs-lookup"><span data-stu-id="90ec2-233">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="90ec2-234">Dit kan een van de volgende teken reeksen zijn: **dag**, **week** of **maand**.</span><span class="sxs-lookup"><span data-stu-id="90ec2-234">Can be one of the following strings: **day**, **week**, or **month**.</span></span> <span data-ttu-id="90ec2-235">Als de waarde niet is opgegeven, is de standaard instelling **dateRange**.</span><span class="sxs-lookup"><span data-stu-id="90ec2-235">If the value isn't specified, the default is **dateRange**.</span></span> <span data-ttu-id="90ec2-236">**Opmerking**: deze para meter is alleen van toepassing wanneer een datum veld wordt door gegeven als onderdeel van de para meter groupBy.</span><span class="sxs-lookup"><span data-stu-id="90ec2-236">**Note**: This parameter applies only when a date field is passed as part of the groupBy parameter.</span></span> |
| <span data-ttu-id="90ec2-237">groupBy</span><span class="sxs-lookup"><span data-stu-id="90ec2-237">groupBy</span></span> | <span data-ttu-id="90ec2-238">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="90ec2-238">string</span></span> | <span data-ttu-id="90ec2-239">Een instructie die alleen gegevens aggregatie toepast op de opgegeven velden.</span><span class="sxs-lookup"><span data-stu-id="90ec2-239">A statement that applies data aggregation only to the specified fields.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="90ec2-240">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="90ec2-240">Request headers</span></span>

<span data-ttu-id="90ec2-241">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="90ec2-241">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="90ec2-242">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="90ec2-242">Request body</span></span>

<span data-ttu-id="90ec2-243">Geen.</span><span class="sxs-lookup"><span data-stu-id="90ec2-243">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="90ec2-244">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="90ec2-244">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?groupBy=subscriptionType
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="90ec2-245">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="90ec2-245">REST response</span></span>

<span data-ttu-id="90ec2-246">Als dit lukt, bevat de antwoord tekst een verzameling [abonnements](partner-center-analytics-resources.md#subscription-resource) resources gegroepeerd op basis van de opgegeven voor waarden en datums.</span><span class="sxs-lookup"><span data-stu-id="90ec2-246">If successful, the response body contains a collection of [Subscription](partner-center-analytics-resources.md#subscription-resource) resources grouped by the specified terms and dates.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="90ec2-247">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="90ec2-247">Response success and error codes</span></span>

<span data-ttu-id="90ec2-248">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="90ec2-248">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="90ec2-249">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="90ec2-249">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="90ec2-250">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="90ec2-250">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="90ec2-251">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="90ec2-251">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
{
  "Value": [
    {
      "subscriptionType": "Azure",
      "subscriptionCount": "63",
      "licenseCount": "0"
    },
    {
      "subscriptionType": "Dynamics",
      "subscriptionCount": "62",
      "licenseCount": "405"
    },
    {
      "subscriptionType": "EMS",
      "subscriptionCount": "39",
      "licenseCount": "193"
    },
    {
      "subscriptionType": "M365",
      "subscriptionCount": "2",
      "licenseCount": "5"
    },
    {
      "subscriptionType": "Office",
      "subscriptionCount": "906",
      "licenseCount": "7485"
    },
    {
      "subscriptionType": "UNKNOWN",
      "subscriptionCount": "104",
      "licenseCount": "439"
    },
    {
      "subscriptionType": "Windows",
      "subscriptionCount": "2",
      "licenseCount": "2"
    }
  ],
  "@nextLink": null,
  "TotalCount": 7
}
```

## <a name="see-also"></a><span data-ttu-id="90ec2-252">Zie ook</span><span class="sxs-lookup"><span data-stu-id="90ec2-252">See also</span></span>

[<span data-ttu-id="90ec2-253">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="90ec2-253">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
