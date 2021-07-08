---
title: Abonnementsanalyses groeperen op datums of voorwaarden
description: Informatie over abonnementsanalyses groeperen op datums of voorwaarden.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8192a9863d53ec8697a7341cd38c69200614bd4a
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548716"
---
# <a name="get-subscription-analytics-grouped-by-dates-or-terms"></a><span data-ttu-id="7664b-103">Abonnementsanalyses groeperen op datums of voorwaarden</span><span class="sxs-lookup"><span data-stu-id="7664b-103">Get subscription analytics grouped by dates or terms</span></span>

<span data-ttu-id="7664b-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7664b-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7664b-105">Informatie over abonnementsanalyses voor uw klanten, gegroepeerd op datums of voorwaarden.</span><span class="sxs-lookup"><span data-stu-id="7664b-105">How to get subscription analytics information for your customers grouped by dates or terms.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7664b-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7664b-106">Prerequisites</span></span>

- <span data-ttu-id="7664b-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7664b-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7664b-108">Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="7664b-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="7664b-109">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7664b-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7664b-110">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="7664b-110">Request syntax</span></span>

| <span data-ttu-id="7664b-111">Methode</span><span class="sxs-lookup"><span data-stu-id="7664b-111">Method</span></span> | <span data-ttu-id="7664b-112">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7664b-112">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="7664b-113">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7664b-113">**GET**</span></span> | <span data-ttu-id="7664b-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?groupby={groupby_queries}</span><span class="sxs-lookup"><span data-stu-id="7664b-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?groupby={groupby_queries}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="7664b-115">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="7664b-115">URI parameters</span></span>

<span data-ttu-id="7664b-116">Gebruik de volgende vereiste padparameters om uw organisatie te identificeren en de resultaten te groeperen.</span><span class="sxs-lookup"><span data-stu-id="7664b-116">Use the following required path parameters to identify your organization and to group the results.</span></span>

| <span data-ttu-id="7664b-117">Naam</span><span class="sxs-lookup"><span data-stu-id="7664b-117">Name</span></span> | <span data-ttu-id="7664b-118">Type</span><span class="sxs-lookup"><span data-stu-id="7664b-118">Type</span></span> | <span data-ttu-id="7664b-119">Vereist</span><span class="sxs-lookup"><span data-stu-id="7664b-119">Required</span></span> | <span data-ttu-id="7664b-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7664b-120">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="7664b-121">groupby_queries</span><span class="sxs-lookup"><span data-stu-id="7664b-121">groupby_queries</span></span> | <span data-ttu-id="7664b-122">paren van tekenreeksen en datum/tijd</span><span class="sxs-lookup"><span data-stu-id="7664b-122">pairs of strings and dateTime</span></span> | <span data-ttu-id="7664b-123">Ja</span><span class="sxs-lookup"><span data-stu-id="7664b-123">Yes</span></span> | <span data-ttu-id="7664b-124">De voorwaarden en datums waarop het resultaat moet worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="7664b-124">The terms and dates to filter the result.</span></span> |

### <a name="groupby-syntax"></a><span data-ttu-id="7664b-125">GroupBy-syntaxis</span><span class="sxs-lookup"><span data-stu-id="7664b-125">GroupBy syntax</span></span>

<span data-ttu-id="7664b-126">De groep op parameter moet bestaan uit een reeks door komma's gescheiden veldwaarden.</span><span class="sxs-lookup"><span data-stu-id="7664b-126">The group by parameter must be composed as a series of comma separated, field values.</span></span>

<span data-ttu-id="7664b-127">Een niet-gecodeerd voorbeeld ziet er als volgende uit:</span><span class="sxs-lookup"><span data-stu-id="7664b-127">An unencoded example looks like this:</span></span>

```http
?groupby=termField1,dateField1,termField2
```

<span data-ttu-id="7664b-128">In de volgende tabel ziet u een lijst met de ondersteunde velden voor group by.</span><span class="sxs-lookup"><span data-stu-id="7664b-128">The following table shows a list of the supported fields for group by.</span></span>

| <span data-ttu-id="7664b-129">Veld</span><span class="sxs-lookup"><span data-stu-id="7664b-129">Field</span></span> | <span data-ttu-id="7664b-130">Type</span><span class="sxs-lookup"><span data-stu-id="7664b-130">Type</span></span> | <span data-ttu-id="7664b-131">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7664b-131">Description</span></span> |
|-------|------|-------------|
| <span data-ttu-id="7664b-132">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="7664b-132">customerTenantId</span></span> | <span data-ttu-id="7664b-133">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-133">string</span></span> | <span data-ttu-id="7664b-134">Een tekenreeks in GUID-indeling die de tenant van de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="7664b-134">A GUID-formatted string that identifies the customer tenant.</span></span> |
| <span data-ttu-id="7664b-135">customerName</span><span class="sxs-lookup"><span data-stu-id="7664b-135">customerName</span></span> | <span data-ttu-id="7664b-136">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-136">string</span></span> | <span data-ttu-id="7664b-137">De naam van de klant.</span><span class="sxs-lookup"><span data-stu-id="7664b-137">The name of the customer.</span></span> |
| <span data-ttu-id="7664b-138">customerMarket</span><span class="sxs-lookup"><span data-stu-id="7664b-138">customerMarket</span></span> | <span data-ttu-id="7664b-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-139">string</span></span> | <span data-ttu-id="7664b-140">Het land/de regio waarin de klant zaken doet.</span><span class="sxs-lookup"><span data-stu-id="7664b-140">The country/region that the customer does business in.</span></span> |
| <span data-ttu-id="7664b-141">id</span><span class="sxs-lookup"><span data-stu-id="7664b-141">id</span></span> | <span data-ttu-id="7664b-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-142">string</span></span> | <span data-ttu-id="7664b-143">Een tekenreeks in GUID-indeling die het abonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="7664b-143">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="7664b-144">status</span><span class="sxs-lookup"><span data-stu-id="7664b-144">status</span></span> | <span data-ttu-id="7664b-145">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-145">string</span></span> | <span data-ttu-id="7664b-146">De abonnementsstatus.</span><span class="sxs-lookup"><span data-stu-id="7664b-146">The subscription status.</span></span> <span data-ttu-id="7664b-147">Ondersteunde waarden zijn: 'ACTIEF', 'SUSPENDED' of 'DEPROVISIONED'.</span><span class="sxs-lookup"><span data-stu-id="7664b-147">Supported values are: "ACTIVE", "SUSPENDED", or "DEPROVISIONED".</span></span> |
| <span data-ttu-id="7664b-148">Productnaam</span><span class="sxs-lookup"><span data-stu-id="7664b-148">productName</span></span> | <span data-ttu-id="7664b-149">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-149">string</span></span> | <span data-ttu-id="7664b-150">De naam van het product.</span><span class="sxs-lookup"><span data-stu-id="7664b-150">The name of the product.</span></span> |
| <span data-ttu-id="7664b-151">subscriptionType</span><span class="sxs-lookup"><span data-stu-id="7664b-151">subscriptionType</span></span> | <span data-ttu-id="7664b-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-152">string</span></span> | <span data-ttu-id="7664b-153">Het abonnementstype.</span><span class="sxs-lookup"><span data-stu-id="7664b-153">The subscription type.</span></span> <span data-ttu-id="7664b-154">Opmerking: Dit veld is casegevoelig.</span><span class="sxs-lookup"><span data-stu-id="7664b-154">Note: This field is case-sensitive.</span></span> <span data-ttu-id="7664b-155">Ondersteunde waarden zijn: 'Office', 'Azure', 'Microsoft365', 'Dynamics', 'EMS'.</span><span class="sxs-lookup"><span data-stu-id="7664b-155">Supported values are: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span></span> |
| <span data-ttu-id="7664b-156">autoRenewEnabled</span><span class="sxs-lookup"><span data-stu-id="7664b-156">autoRenewEnabled</span></span> | <span data-ttu-id="7664b-157">Booleaans</span><span class="sxs-lookup"><span data-stu-id="7664b-157">Boolean</span></span> | <span data-ttu-id="7664b-158">Een waarde die aangeeft of het abonnement automatisch wordt verlengd.</span><span class="sxs-lookup"><span data-stu-id="7664b-158">A value indicating whether the subscription is renewed automatically.</span></span> |
| <span data-ttu-id="7664b-159">partnerId</span><span class="sxs-lookup"><span data-stu-id="7664b-159">partnerId</span></span>  | <span data-ttu-id="7664b-160">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-160">string</span></span> | <span data-ttu-id="7664b-161">De MPN-id.</span><span class="sxs-lookup"><span data-stu-id="7664b-161">The MPN ID.</span></span> <span data-ttu-id="7664b-162">Voor een directe reseller is deze parameter de MPN-id van de partner.</span><span class="sxs-lookup"><span data-stu-id="7664b-162">For a direct reseller, this parameter will be the MPN ID of the partner.</span></span> <span data-ttu-id="7664b-163">Voor een indirecte reseller is deze parameter de MPN-id van de indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="7664b-163">For an indirect reseller, this parameter will be the MPN ID of the indirect reseller.</span></span> |
| <span data-ttu-id="7664b-164">Friendlyname</span><span class="sxs-lookup"><span data-stu-id="7664b-164">friendlyName</span></span> | <span data-ttu-id="7664b-165">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-165">string</span></span> | <span data-ttu-id="7664b-166">De naam van het abonnement.</span><span class="sxs-lookup"><span data-stu-id="7664b-166">The name of the subscription.</span></span> |
| <span data-ttu-id="7664b-167">partnerName</span><span class="sxs-lookup"><span data-stu-id="7664b-167">partnerName</span></span> | <span data-ttu-id="7664b-168">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-168">string</span></span> | <span data-ttu-id="7664b-169">Naam van de partner voor wie het abonnement is gekocht</span><span class="sxs-lookup"><span data-stu-id="7664b-169">Name of the partner for whom the subscription was purchased</span></span> |
| <span data-ttu-id="7664b-170">providerName</span><span class="sxs-lookup"><span data-stu-id="7664b-170">providerName</span></span> | <span data-ttu-id="7664b-171">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-171">string</span></span> | <span data-ttu-id="7664b-172">Wanneer de abonnementstransactie voor de indirecte reseller is, is de providernaam de indirecte provider die het abonnement heeft gekocht.</span><span class="sxs-lookup"><span data-stu-id="7664b-172">When subscription transaction is for the indirect reseller, provider name is the indirect provider who bought the subscription.</span></span>
| <span data-ttu-id="7664b-173">creationDate</span><span class="sxs-lookup"><span data-stu-id="7664b-173">creationDate</span></span> | <span data-ttu-id="7664b-174">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="7664b-174">string in UTC date time format</span></span> | <span data-ttu-id="7664b-175">De datum waarop het abonnement is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="7664b-175">The date the subscription was created.</span></span> |
| <span data-ttu-id="7664b-176">effectiveStartDate</span><span class="sxs-lookup"><span data-stu-id="7664b-176">effectiveStartDate</span></span> | <span data-ttu-id="7664b-177">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="7664b-177">string in UTC date time format</span></span> | <span data-ttu-id="7664b-178">De datum waarop het abonnement wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="7664b-178">The date the subscription starts.</span></span> |
| <span data-ttu-id="7664b-179">commitmentEndDate</span><span class="sxs-lookup"><span data-stu-id="7664b-179">commitmentEndDate</span></span> | <span data-ttu-id="7664b-180">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="7664b-180">string in UTC date time format</span></span> | <span data-ttu-id="7664b-181">De datum waarop het abonnement eindigt.</span><span class="sxs-lookup"><span data-stu-id="7664b-181">The date the subscription ends.</span></span> |
| <span data-ttu-id="7664b-182">currentStateEndDate</span><span class="sxs-lookup"><span data-stu-id="7664b-182">currentStateEndDate</span></span> | <span data-ttu-id="7664b-183">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="7664b-183">string in UTC date time format</span></span> | <span data-ttu-id="7664b-184">De datum waarop de huidige status van het abonnement wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="7664b-184">The date that the current status of the subscription will change.</span></span> |
| <span data-ttu-id="7664b-185">trialToPaidConversionDate</span><span class="sxs-lookup"><span data-stu-id="7664b-185">trialToPaidConversionDate</span></span> | <span data-ttu-id="7664b-186">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="7664b-186">string in UTC date time format</span></span> | <span data-ttu-id="7664b-187">De datum waarop het abonnement wordt omgezet van proefversie naar betaald.</span><span class="sxs-lookup"><span data-stu-id="7664b-187">The date that the subscription converts from trial to paid.</span></span> <span data-ttu-id="7664b-188">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="7664b-188">The default value is null.</span></span> |
| <span data-ttu-id="7664b-189">trialStartDate</span><span class="sxs-lookup"><span data-stu-id="7664b-189">trialStartDate</span></span> | <span data-ttu-id="7664b-190">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="7664b-190">string in UTC date time format</span></span> | <span data-ttu-id="7664b-191">De datum waarop de proefperiode voor het abonnement is gestart.</span><span class="sxs-lookup"><span data-stu-id="7664b-191">The date that the trial period for the subscription started.</span></span> <span data-ttu-id="7664b-192">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="7664b-192">The default value is null.</span></span> |
| <span data-ttu-id="7664b-193">lastUsageDate</span><span class="sxs-lookup"><span data-stu-id="7664b-193">lastUsageDate</span></span> | <span data-ttu-id="7664b-194">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="7664b-194">string in UTC date time format</span></span> | <span data-ttu-id="7664b-195">De datum waarop het abonnement voor het laatst is gebruikt.</span><span class="sxs-lookup"><span data-stu-id="7664b-195">The date that the subscription was last used.</span></span> <span data-ttu-id="7664b-196">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="7664b-196">The default value is null.</span></span> |
| <span data-ttu-id="7664b-197">deprovisionedDate</span><span class="sxs-lookup"><span data-stu-id="7664b-197">deprovisionedDate</span></span> | <span data-ttu-id="7664b-198">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="7664b-198">string in UTC date time format</span></span> | <span data-ttu-id="7664b-199">De datum waarop het abonnement is verwijderd.</span><span class="sxs-lookup"><span data-stu-id="7664b-199">The date that the subscription was deprovisioned.</span></span> <span data-ttu-id="7664b-200">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="7664b-200">The default value is null.</span></span> |
| <span data-ttu-id="7664b-201">lastRenewalDate</span><span class="sxs-lookup"><span data-stu-id="7664b-201">lastRenewalDate</span></span> | <span data-ttu-id="7664b-202">tekenreeks in UTC-datum/tijd-indeling</span><span class="sxs-lookup"><span data-stu-id="7664b-202">string in UTC date time format</span></span> | <span data-ttu-id="7664b-203">De datum waarop het abonnement voor het laatst is vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="7664b-203">The date that the subscription was last renewed.</span></span> <span data-ttu-id="7664b-204">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="7664b-204">The default value is null.</span></span> |

### <a name="filter-fields"></a><span data-ttu-id="7664b-205">Filtervelden</span><span class="sxs-lookup"><span data-stu-id="7664b-205">Filter fields</span></span>

<span data-ttu-id="7664b-206">De volgende tabel bevat optionele filtervelden en de bijbehorende beschrijvingen:</span><span class="sxs-lookup"><span data-stu-id="7664b-206">The following table lists optional filter fields and their descriptions:</span></span>

| <span data-ttu-id="7664b-207">Veld</span><span class="sxs-lookup"><span data-stu-id="7664b-207">Field</span></span> | <span data-ttu-id="7664b-208">Type</span><span class="sxs-lookup"><span data-stu-id="7664b-208">Type</span></span> |  <span data-ttu-id="7664b-209">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7664b-209">Description</span></span> |
|-------|------|--------------|
| <span data-ttu-id="7664b-210">top</span><span class="sxs-lookup"><span data-stu-id="7664b-210">top</span></span> | <span data-ttu-id="7664b-211">int</span><span class="sxs-lookup"><span data-stu-id="7664b-211">int</span></span> | <span data-ttu-id="7664b-212">Het aantal rijen met gegevens dat in de aanvraag moet worden retourneren.</span><span class="sxs-lookup"><span data-stu-id="7664b-212">The number of rows of data to return in the request.</span></span> <span data-ttu-id="7664b-213">Als de waarde niet is opgegeven, zijn de maximumwaarde en de standaardwaarde 10000.</span><span class="sxs-lookup"><span data-stu-id="7664b-213">If the value isn't specified, the maximum value and the default value are 10000.</span></span> <span data-ttu-id="7664b-214">Als er meer rijen in de query staan, bevat de antwoord-body een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.</span><span class="sxs-lookup"><span data-stu-id="7664b-214">If there are more rows in the query, the response body includes a next link that you can use to request the next page of data.</span></span> |
| <span data-ttu-id="7664b-215">skip</span><span class="sxs-lookup"><span data-stu-id="7664b-215">skip</span></span> | <span data-ttu-id="7664b-216">int</span><span class="sxs-lookup"><span data-stu-id="7664b-216">int</span></span> | <span data-ttu-id="7664b-217">Het aantal rijen dat moet worden overgeslagen in de query.</span><span class="sxs-lookup"><span data-stu-id="7664b-217">The number of rows to skip in the query.</span></span> <span data-ttu-id="7664b-218">Gebruik deze parameter om door grote gegevenssets te gaan.</span><span class="sxs-lookup"><span data-stu-id="7664b-218">Use this parameter to page through large data sets.</span></span> <span data-ttu-id="7664b-219">Top=10000 en skip=0 haalt bijvoorbeeld de eerste 10000 rijen met gegevens op, top=10000 en skip=10000 haalt de volgende 10000 rijen met gegevens op.</span><span class="sxs-lookup"><span data-stu-id="7664b-219">For example, top=10000 and skip=0 retrieves the first 10000 rows of data, top=10000 and skip=10000 retrieves the next 10000 rows of data.</span></span> |
| <span data-ttu-id="7664b-220">filter</span><span class="sxs-lookup"><span data-stu-id="7664b-220">filter</span></span> | <span data-ttu-id="7664b-221">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-221">string</span></span> | <span data-ttu-id="7664b-222">Een of meer instructies die de rijen in het antwoord filteren.</span><span class="sxs-lookup"><span data-stu-id="7664b-222">One or more statements that filter the rows in the response.</span></span> <span data-ttu-id="7664b-223">Elke filter-instructie bevat een veldnaam van de antwoord-body en een waarde die zijn gekoppeld aan de operator , of voor **`eq`** **`ne`** bepaalde **`contains`** velden.</span><span class="sxs-lookup"><span data-stu-id="7664b-223">Each filter statement contains a field name from the response body and a value that are associated with the **`eq`**, **`ne`**, or for certain fields, the **`contains`** operator.</span></span> <span data-ttu-id="7664b-224">Instructies kunnen worden gecombineerd met **`and`** of **`or`** .</span><span class="sxs-lookup"><span data-stu-id="7664b-224">Statements can be combined using **`and`** or **`or`**.</span></span> <span data-ttu-id="7664b-225">Tekenreekswaarden moeten tussen enkele aanhalingstekens in de filterparameter staan.</span><span class="sxs-lookup"><span data-stu-id="7664b-225">String values must be surrounded by single quotes in the filter parameter.</span></span> <span data-ttu-id="7664b-226">Zie de volgende sectie voor een lijst met velden die kunnen worden gefilterd en de operators die worden ondersteund met deze velden.</span><span class="sxs-lookup"><span data-stu-id="7664b-226">See the following section for a list of fields that can be filtered and the operators that are supported with those fields.</span></span> |
| <span data-ttu-id="7664b-227">aggregationLevel</span><span class="sxs-lookup"><span data-stu-id="7664b-227">aggregationLevel</span></span> | <span data-ttu-id="7664b-228">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-228">string</span></span> | <span data-ttu-id="7664b-229">Hiermee geeft u het tijdsbereik op waarvoor geaggregeerde gegevens moeten worden opgehaald.</span><span class="sxs-lookup"><span data-stu-id="7664b-229">Specifies the time range for which to retrieve aggregate data.</span></span> <span data-ttu-id="7664b-230">Kan een van de volgende tekenreeksen zijn: **dag,** **week** of **maand.**</span><span class="sxs-lookup"><span data-stu-id="7664b-230">Can be one of the following strings: **day**, **week**, or **month**.</span></span> <span data-ttu-id="7664b-231">Als de waarde niet is opgegeven, is de **standaardwaarde dateRange.**</span><span class="sxs-lookup"><span data-stu-id="7664b-231">If the value isn't specified, the default is **dateRange**.</span></span> <span data-ttu-id="7664b-232">**Opmerking:** deze parameter is alleen van toepassing wanneer een datumveld wordt doorgegeven als onderdeel van de parameter groupBy.</span><span class="sxs-lookup"><span data-stu-id="7664b-232">**Note**: This parameter applies only when a date field is passed as part of the groupBy parameter.</span></span> |
| <span data-ttu-id="7664b-233">groupBy</span><span class="sxs-lookup"><span data-stu-id="7664b-233">groupBy</span></span> | <span data-ttu-id="7664b-234">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="7664b-234">string</span></span> | <span data-ttu-id="7664b-235">Een instructie die gegevensaggregatie alleen op de opgegeven velden van toepassing is.</span><span class="sxs-lookup"><span data-stu-id="7664b-235">A statement that applies data aggregation only to the specified fields.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="7664b-236">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7664b-236">Request headers</span></span>

<span data-ttu-id="7664b-237">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="7664b-237">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7664b-238">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7664b-238">Request body</span></span>

<span data-ttu-id="7664b-239">Geen.</span><span class="sxs-lookup"><span data-stu-id="7664b-239">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7664b-240">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7664b-240">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?groupBy=subscriptionType
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="7664b-241">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7664b-241">REST response</span></span>

<span data-ttu-id="7664b-242">Als dit lukt, bevat de antwoord-body een verzameling [abonnementsresources](partner-center-analytics-resources.md#subscription-resource) gegroepeerd op de opgegeven voorwaarden en datums.</span><span class="sxs-lookup"><span data-stu-id="7664b-242">If successful, the response body contains a collection of [Subscription](partner-center-analytics-resources.md#subscription-resource) resources grouped by the specified terms and dates.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7664b-243">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="7664b-243">Response success and error codes</span></span>

<span data-ttu-id="7664b-244">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="7664b-244">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7664b-245">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7664b-245">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7664b-246">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="7664b-246">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7664b-247">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="7664b-247">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7664b-248">Zie ook</span><span class="sxs-lookup"><span data-stu-id="7664b-248">See also</span></span>

[<span data-ttu-id="7664b-249">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="7664b-249">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
