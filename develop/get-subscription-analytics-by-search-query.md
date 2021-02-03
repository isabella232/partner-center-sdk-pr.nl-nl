---
title: Abonnements analyse ophalen via zoek query
description: Abonnements analyserapporten filteren op basis van een zoek query.
ms.date: 05/10/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c1046ea3c7e813eedae4890eebf6356337c80ede
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767279"
---
# <a name="get-subscription-analytics-information-filtered-by-a-search-query"></a><span data-ttu-id="05afa-103">Analysegegevens van abonnementen die is gefilterd met een zoekquery ophalen</span><span class="sxs-lookup"><span data-stu-id="05afa-103">Get subscription analytics information filtered by a search query</span></span>

<span data-ttu-id="05afa-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="05afa-104">**Applies To**</span></span>

- <span data-ttu-id="05afa-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="05afa-105">Partner Center</span></span>
- <span data-ttu-id="05afa-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="05afa-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="05afa-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="05afa-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="05afa-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="05afa-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="05afa-109">Informatie over abonnements analyse ophalen voor uw klanten, gefilterd op een zoek query.</span><span class="sxs-lookup"><span data-stu-id="05afa-109">How to get subscription analytics information for your customers filtered by a search query.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="05afa-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="05afa-110">Prerequisites</span></span>

- <span data-ttu-id="05afa-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="05afa-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="05afa-112">Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="05afa-112">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="05afa-113">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="05afa-113">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="05afa-114">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="05afa-114">Request syntax</span></span>

| <span data-ttu-id="05afa-115">Methode</span><span class="sxs-lookup"><span data-stu-id="05afa-115">Method</span></span> | <span data-ttu-id="05afa-116">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="05afa-116">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="05afa-117">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="05afa-117">**GET**</span></span> | <span data-ttu-id="05afa-118">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/Subscriptions? filter = {filter_string}</span><span class="sxs-lookup"><span data-stu-id="05afa-118">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?filter={filter_string}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="05afa-119">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="05afa-119">URI parameters</span></span>

<span data-ttu-id="05afa-120">Gebruik de volgende vereiste para meter voor het identificeren van uw organisatie en het filteren van de zoek opdracht.</span><span class="sxs-lookup"><span data-stu-id="05afa-120">Use the following required path parameter to identify your organization and filter the search.</span></span>

| <span data-ttu-id="05afa-121">Naam</span><span class="sxs-lookup"><span data-stu-id="05afa-121">Name</span></span> | <span data-ttu-id="05afa-122">Type</span><span class="sxs-lookup"><span data-stu-id="05afa-122">Type</span></span> | <span data-ttu-id="05afa-123">Vereist</span><span class="sxs-lookup"><span data-stu-id="05afa-123">Required</span></span> | <span data-ttu-id="05afa-124">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="05afa-124">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="05afa-125">filter_string</span><span class="sxs-lookup"><span data-stu-id="05afa-125">filter_string</span></span> | <span data-ttu-id="05afa-126">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="05afa-126">string</span></span> | <span data-ttu-id="05afa-127">Yes</span><span class="sxs-lookup"><span data-stu-id="05afa-127">Yes</span></span> | <span data-ttu-id="05afa-128">Het filter dat moet worden toegepast op de abonnements analyse.</span><span class="sxs-lookup"><span data-stu-id="05afa-128">The filter to apply to the subscription analytics.</span></span> <span data-ttu-id="05afa-129">Zie de secties filter syntaxis en filter Fields voor de syntaxis, velden en Opera tors voor gebruik in deze para meter.</span><span class="sxs-lookup"><span data-stu-id="05afa-129">See the Filter syntax and Filter fields sections for the syntax, fields, and operators to use in this parameter.</span></span> |

### <a name="filter-syntax"></a><span data-ttu-id="05afa-130">Filter syntaxis</span><span class="sxs-lookup"><span data-stu-id="05afa-130">Filter syntax</span></span>

<span data-ttu-id="05afa-131">De filter parameter moet worden samengesteld als een reeks combi Naties van velden, waarden en operators.</span><span class="sxs-lookup"><span data-stu-id="05afa-131">The filter parameter must be composed as a series of field, value, and operator combinations.</span></span> <span data-ttu-id="05afa-132">Meerdere combi Naties kunnen worden gecombineerd met **`and`** of- **`or`** Opera tors.</span><span class="sxs-lookup"><span data-stu-id="05afa-132">Multiple combinations can be combined using **`and`** or **`or`** operators.</span></span>

<span data-ttu-id="05afa-133">Een niet-gecodeerd voor beeld ziet er als volgt uit:</span><span class="sxs-lookup"><span data-stu-id="05afa-133">An unencoded example looks like this:</span></span>

- <span data-ttu-id="05afa-134">Tekenreeksexpressie `?filter=Field operator 'Value'`</span><span class="sxs-lookup"><span data-stu-id="05afa-134">String: `?filter=Field operator 'Value'`</span></span>
- <span data-ttu-id="05afa-135">True `?filter=Field operator Value`</span><span class="sxs-lookup"><span data-stu-id="05afa-135">Boolean: `?filter=Field operator Value`</span></span>
- <span data-ttu-id="05afa-136">Daarin `?filter=contains(field,'value')`</span><span class="sxs-lookup"><span data-stu-id="05afa-136">Contains `?filter=contains(field,'value')`</span></span>

### <a name="filter-fields"></a><span data-ttu-id="05afa-137">Filter velden</span><span class="sxs-lookup"><span data-stu-id="05afa-137">Filter fields</span></span>

<span data-ttu-id="05afa-138">De filter parameter van de aanvraag bevat een of meer instructies waarmee de rijen in het antwoord worden gefilterd.</span><span class="sxs-lookup"><span data-stu-id="05afa-138">The filter parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="05afa-139">Elke instructie bevat een veld en waarde die zijn gekoppeld aan de **`eq`** or- **`ne`** Opera tors.</span><span class="sxs-lookup"><span data-stu-id="05afa-139">Each statement contains a field and value that are associated with the **`eq`** or **`ne`** operators.</span></span> <span data-ttu-id="05afa-140">Sommige velden bieden ook ondersteuning voor de **`contains`** **`gt`** **`lt`** Opera Tors,,, **`ge`** en **`le`** .</span><span class="sxs-lookup"><span data-stu-id="05afa-140">Some fields also support the **`contains`**, **`gt`**, **`lt`**, **`ge`**, and **`le`** operators.</span></span> <span data-ttu-id="05afa-141">Instructies kunnen worden gecombineerd met behulp van **`and`** or- **`or`** Opera tors.</span><span class="sxs-lookup"><span data-stu-id="05afa-141">Statements can be combined using **`and`** or **`or`** operators.</span></span>

<span data-ttu-id="05afa-142">Hier volgen enkele voor beelden van filter reeksen:</span><span class="sxs-lookup"><span data-stu-id="05afa-142">The following are examples of filter strings:</span></span>

```http
autoRenewEnabled eq true

autoRenewEnabled eq true and customerMarket eq 'US'
```

<span data-ttu-id="05afa-143">De volgende tabel bevat een lijst met de ondersteunde velden en ondersteunings operatoren voor de filter parameter.</span><span class="sxs-lookup"><span data-stu-id="05afa-143">The following table shows a list of the supported fields and support operators for the filter parameter.</span></span> <span data-ttu-id="05afa-144">Teken reeks waarden moeten tussen enkele aanhalings tekens worden geplaatst.</span><span class="sxs-lookup"><span data-stu-id="05afa-144">String values must be surrounded by single quotes.</span></span>

| <span data-ttu-id="05afa-145">Parameter</span><span class="sxs-lookup"><span data-stu-id="05afa-145">Parameter</span></span> | <span data-ttu-id="05afa-146">Ondersteunde Opera tors</span><span class="sxs-lookup"><span data-stu-id="05afa-146">Supported operators</span></span> | <span data-ttu-id="05afa-147">Description</span><span class="sxs-lookup"><span data-stu-id="05afa-147">Description</span></span> |
|-----------|---------------------|-------------|
| <span data-ttu-id="05afa-148">autoRenewEnabled</span><span class="sxs-lookup"><span data-stu-id="05afa-148">autoRenewEnabled</span></span> | <span data-ttu-id="05afa-149">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="05afa-149">`eq`, `ne`</span></span> | <span data-ttu-id="05afa-150">Een waarde die aangeeft of het abonnement automatisch wordt vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="05afa-150">A value indicating whether the subscription is renewed automatically.</span></span> |
| <span data-ttu-id="05afa-151">commitmentEndDate</span><span class="sxs-lookup"><span data-stu-id="05afa-151">commitmentEndDate</span></span> | <span data-ttu-id="05afa-152">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="05afa-152">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="05afa-153">De datum waarop het abonnement eindigt.</span><span class="sxs-lookup"><span data-stu-id="05afa-153">The date the subscription ends.</span></span> |
| <span data-ttu-id="05afa-154">creationDate</span><span class="sxs-lookup"><span data-stu-id="05afa-154">creationDate</span></span> | <span data-ttu-id="05afa-155">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="05afa-155">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="05afa-156">De datum waarop het abonnement is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="05afa-156">The date the subscription was created.</span></span> |
| <span data-ttu-id="05afa-157">currentStateEndDate</span><span class="sxs-lookup"><span data-stu-id="05afa-157">currentStateEndDate</span></span> | <span data-ttu-id="05afa-158">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="05afa-158">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="05afa-159">De datum waarop de huidige status van het abonnement wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="05afa-159">The date that the current status of the subscription will change.</span></span> |
| <span data-ttu-id="05afa-160">customerMarket</span><span class="sxs-lookup"><span data-stu-id="05afa-160">customerMarket</span></span> | <span data-ttu-id="05afa-161">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="05afa-161">`eq`, `ne`</span></span> | <span data-ttu-id="05afa-162">Het land/de regio waarin de klant zaken doet.</span><span class="sxs-lookup"><span data-stu-id="05afa-162">The country/region that the customer does business in.</span></span> |
| <span data-ttu-id="05afa-163">customerName</span><span class="sxs-lookup"><span data-stu-id="05afa-163">customerName</span></span> | `contains` | <span data-ttu-id="05afa-164">De naam van de klant.</span><span class="sxs-lookup"><span data-stu-id="05afa-164">The name of the customer.</span></span> |
| <span data-ttu-id="05afa-165">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="05afa-165">customerTenantId</span></span> | <span data-ttu-id="05afa-166">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="05afa-166">`eq`, `ne`</span></span> | <span data-ttu-id="05afa-167">Een teken reeks met een GUID-indeling die de Tenant van de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="05afa-167">A GUID-formatted string that identifies the customer tenant.</span></span> |
| <span data-ttu-id="05afa-168">deprovisionedDate</span><span class="sxs-lookup"><span data-stu-id="05afa-168">deprovisionedDate</span></span> | <span data-ttu-id="05afa-169">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="05afa-169">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="05afa-170">De datum waarop het abonnement is ongedaan gemaakt.</span><span class="sxs-lookup"><span data-stu-id="05afa-170">The date that the subscription was deprovisioned.</span></span> <span data-ttu-id="05afa-171">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="05afa-171">The default value is null.</span></span> |
| <span data-ttu-id="05afa-172">effectiveStartDate</span><span class="sxs-lookup"><span data-stu-id="05afa-172">effectiveStartDate</span></span> | <span data-ttu-id="05afa-173">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="05afa-173">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="05afa-174">De datum waarop het abonnement wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="05afa-174">The date the subscription starts.</span></span> |
| <span data-ttu-id="05afa-175">friendlyName</span><span class="sxs-lookup"><span data-stu-id="05afa-175">friendlyName</span></span> | `contains` | <span data-ttu-id="05afa-176">De naam van het abonnement.</span><span class="sxs-lookup"><span data-stu-id="05afa-176">The name of the subscription.</span></span> |
| <span data-ttu-id="05afa-177">id</span><span class="sxs-lookup"><span data-stu-id="05afa-177">id</span></span> | <span data-ttu-id="05afa-178">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="05afa-178">`eq`, `ne`</span></span> | <span data-ttu-id="05afa-179">Een teken reeks met een GUID-indeling waarmee het abonnement wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="05afa-179">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="05afa-180">lastRenewalDate</span><span class="sxs-lookup"><span data-stu-id="05afa-180">lastRenewalDate</span></span> | <span data-ttu-id="05afa-181">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="05afa-181">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="05afa-182">De datum waarop het abonnement voor het laatst is vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="05afa-182">The date that the subscription was last renewed.</span></span> <span data-ttu-id="05afa-183">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="05afa-183">The default value is null.</span></span> |
| <span data-ttu-id="05afa-184">lastUsageDate</span><span class="sxs-lookup"><span data-stu-id="05afa-184">lastUsageDate</span></span> | <span data-ttu-id="05afa-185">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="05afa-185">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="05afa-186">De datum waarop het abonnement voor het laatst is gebruikt.</span><span class="sxs-lookup"><span data-stu-id="05afa-186">The date that the subscription was last used.</span></span> <span data-ttu-id="05afa-187">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="05afa-187">The default value is null.</span></span> |
| <span data-ttu-id="05afa-188">Partner</span><span class="sxs-lookup"><span data-stu-id="05afa-188">partnerId</span></span> | <span data-ttu-id="05afa-189">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="05afa-189">`eq`, `ne`</span></span> | <span data-ttu-id="05afa-190">De MPN-ID.</span><span class="sxs-lookup"><span data-stu-id="05afa-190">The MPN ID.</span></span> <span data-ttu-id="05afa-191">Voor een rechtstreekse wederverkoper is deze waarde de MPN-ID van de partner.</span><span class="sxs-lookup"><span data-stu-id="05afa-191">For a direct reseller, this value will be the MPN ID of the partner.</span></span> <span data-ttu-id="05afa-192">Voor een indirecte wederverkoper is deze waarde de MPN-ID van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="05afa-192">For an indirect reseller, this value will be the MPN ID of the indirect reseller.</span></span> |
| <span data-ttu-id="05afa-193">partnerName</span><span class="sxs-lookup"><span data-stu-id="05afa-193">partnerName</span></span> | <span data-ttu-id="05afa-194">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="05afa-194">string</span></span> | <span data-ttu-id="05afa-195">De naam van de partner voor wie het abonnement is aangeschaft</span><span class="sxs-lookup"><span data-stu-id="05afa-195">Name of the partner for whom the subscription was purchased</span></span> |
| <span data-ttu-id="05afa-196">Product</span><span class="sxs-lookup"><span data-stu-id="05afa-196">productName</span></span> | <span data-ttu-id="05afa-197">`contains`, `eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="05afa-197">`contains`, `eq`, `ne`</span></span> | <span data-ttu-id="05afa-198">De naam van het product.</span><span class="sxs-lookup"><span data-stu-id="05afa-198">The name of the product.</span></span> |
| <span data-ttu-id="05afa-199">providerName</span><span class="sxs-lookup"><span data-stu-id="05afa-199">providerName</span></span> | <span data-ttu-id="05afa-200">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="05afa-200">string</span></span> | <span data-ttu-id="05afa-201">Wanneer abonnements transactie voor de indirecte wederverkoper is, is de naam van de provider de indirecte provider die het abonnement heeft gekocht.</span><span class="sxs-lookup"><span data-stu-id="05afa-201">When subscription transaction is for the indirect reseller, provider name is the indirect provider who bought the subscription.</span></span>|
| <span data-ttu-id="05afa-202">status</span><span class="sxs-lookup"><span data-stu-id="05afa-202">status</span></span> | <span data-ttu-id="05afa-203">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="05afa-203">`eq`, `ne`</span></span> | <span data-ttu-id="05afa-204">De abonnements status.</span><span class="sxs-lookup"><span data-stu-id="05afa-204">The subscription status.</span></span> <span data-ttu-id="05afa-205">Ondersteunde waarden zijn: ' Active ', ' Suspended ' of ' provisioned '.</span><span class="sxs-lookup"><span data-stu-id="05afa-205">Supported values are: "ACTIVE", "SUSPENDED", or "DEPROVISIONED".</span></span> |
| <span data-ttu-id="05afa-206">subscriptionType</span><span class="sxs-lookup"><span data-stu-id="05afa-206">subscriptionType</span></span> | <span data-ttu-id="05afa-207">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="05afa-207">`eq`, `ne`</span></span> | <span data-ttu-id="05afa-208">Het type abonnement.</span><span class="sxs-lookup"><span data-stu-id="05afa-208">The subscription type.</span></span> <span data-ttu-id="05afa-209">**Opmerking**: dit veld is hoofdletter gevoelig.</span><span class="sxs-lookup"><span data-stu-id="05afa-209">**Note**: This field is case-sensitive.</span></span> <span data-ttu-id="05afa-210">Ondersteunde waarden zijn: ' Office ', ' Azure ', ' Microsoft365 ', ' Dynamics ', ' EMS '.</span><span class="sxs-lookup"><span data-stu-id="05afa-210">Supported values are: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span></span> |
| <span data-ttu-id="05afa-211">trialStartDate</span><span class="sxs-lookup"><span data-stu-id="05afa-211">trialStartDate</span></span> | <span data-ttu-id="05afa-212">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="05afa-212">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="05afa-213">De datum waarop de proef periode voor het abonnement is gestart.</span><span class="sxs-lookup"><span data-stu-id="05afa-213">The date that the trial period for the subscription started.</span></span> <span data-ttu-id="05afa-214">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="05afa-214">The default value is null.</span></span> |
| <span data-ttu-id="05afa-215">trialToPaidConversionDate</span><span class="sxs-lookup"><span data-stu-id="05afa-215">trialToPaidConversionDate</span></span> | <span data-ttu-id="05afa-216">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="05afa-216">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="05afa-217">De datum waarop het abonnement wordt geconverteerd van een proef versie naar betaald.</span><span class="sxs-lookup"><span data-stu-id="05afa-217">The date that the subscription converts from trial to paid.</span></span> <span data-ttu-id="05afa-218">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="05afa-218">The default value is null.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="05afa-219">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="05afa-219">Request headers</span></span>

<span data-ttu-id="05afa-220">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="05afa-220">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="05afa-221">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="05afa-221">Request body</span></span>

<span data-ttu-id="05afa-222">Geen.</span><span class="sxs-lookup"><span data-stu-id="05afa-222">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="05afa-223">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="05afa-223">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?filter=autoRenewEnabled eq true
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="05afa-224">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="05afa-224">REST response</span></span>

<span data-ttu-id="05afa-225">Als dit lukt, bevat de antwoord tekst een verzameling [abonnements](partner-center-analytics-resources.md#subscription-resource) resources die voldoen aan de filter criteria.</span><span class="sxs-lookup"><span data-stu-id="05afa-225">If successful, the response body contains a collection of [Subscription](partner-center-analytics-resources.md#subscription-resource) resources that meet the filter criteria.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="05afa-226">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="05afa-226">Response success and error codes</span></span>

<span data-ttu-id="05afa-227">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="05afa-227">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="05afa-228">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="05afa-228">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="05afa-229">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="05afa-229">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="05afa-230">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="05afa-230">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123

{
    "customerTenantId": "735920EB-A564-4C72-9FE5-52632562712C",
    "customerName": "SURFACE TEST2",
    "customerMarket": "US",
    "id": "B76412DA-D382-4688-A6A4-711A207C1C2E",
    "status": "ACTIVE",
    "productName": "UNKNOWN",
    "subscriptionType": "Azure",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "MICROSOFT AZURE",
    "creationDate": "2017-06-02T23:11:58.747",
    "effectiveStartDate": "2017-06-02T00:00:00",
    "commitmentEndDate": null,
    "currentStateEndDate": null,
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": null,
    "licenseCount": 0
}
```

## <a name="see-also"></a><span data-ttu-id="05afa-231">Zie ook</span><span class="sxs-lookup"><span data-stu-id="05afa-231">See also</span></span>

- [<span data-ttu-id="05afa-232">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="05afa-232">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
