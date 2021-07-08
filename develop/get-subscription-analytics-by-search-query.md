---
title: Abonnementsanalyses opvragen per zoekquery
description: Analytische gegevens van abonnementen filteren op een zoekquery.
ms.date: 05/10/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8df777b9a88206f8b22579f0f445c54d80f7cd64
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548733"
---
# <a name="get-subscription-analytics-information-filtered-by-a-search-query"></a><span data-ttu-id="2fdaa-103">Analysegegevens van abonnementen die is gefilterd met een zoekquery ophalen</span><span class="sxs-lookup"><span data-stu-id="2fdaa-103">Get subscription analytics information filtered by a search query</span></span>

<span data-ttu-id="2fdaa-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="2fdaa-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="2fdaa-105">Informatie over abonnementsanalyses voor uw klanten filteren op basis van een zoekquery.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-105">How to get subscription analytics information for your customers filtered by a search query.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2fdaa-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="2fdaa-106">Prerequisites</span></span>

- <span data-ttu-id="2fdaa-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="2fdaa-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="2fdaa-108">Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-108">This scenario supports authentication with User credentials only.</span></span>

## <a name="rest-request"></a><span data-ttu-id="2fdaa-109">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="2fdaa-109">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="2fdaa-110">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="2fdaa-110">Request syntax</span></span>

| <span data-ttu-id="2fdaa-111">Methode</span><span class="sxs-lookup"><span data-stu-id="2fdaa-111">Method</span></span> | <span data-ttu-id="2fdaa-112">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="2fdaa-112">Request URI</span></span> |
|--------|-------------|
| <span data-ttu-id="2fdaa-113">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="2fdaa-113">**GET**</span></span> | <span data-ttu-id="2fdaa-114">[*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?filter={filter_string}</span><span class="sxs-lookup"><span data-stu-id="2fdaa-114">[*\{baseURL\}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?filter={filter_string}</span></span> |

### <a name="uri-parameters"></a><span data-ttu-id="2fdaa-115">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="2fdaa-115">URI parameters</span></span>

<span data-ttu-id="2fdaa-116">Gebruik de volgende vereiste padparameter om uw organisatie te identificeren en de zoekopdracht te filteren.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-116">Use the following required path parameter to identify your organization and filter the search.</span></span>

| <span data-ttu-id="2fdaa-117">Naam</span><span class="sxs-lookup"><span data-stu-id="2fdaa-117">Name</span></span> | <span data-ttu-id="2fdaa-118">Type</span><span class="sxs-lookup"><span data-stu-id="2fdaa-118">Type</span></span> | <span data-ttu-id="2fdaa-119">Vereist</span><span class="sxs-lookup"><span data-stu-id="2fdaa-119">Required</span></span> | <span data-ttu-id="2fdaa-120">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2fdaa-120">Description</span></span> |
|------|------|----------|-------------|
| <span data-ttu-id="2fdaa-121">filter_string</span><span class="sxs-lookup"><span data-stu-id="2fdaa-121">filter_string</span></span> | <span data-ttu-id="2fdaa-122">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2fdaa-122">string</span></span> | <span data-ttu-id="2fdaa-123">Ja</span><span class="sxs-lookup"><span data-stu-id="2fdaa-123">Yes</span></span> | <span data-ttu-id="2fdaa-124">Het filter dat moet worden toegepast op de abonnementsanalyses.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-124">The filter to apply to the subscription analytics.</span></span> <span data-ttu-id="2fdaa-125">Zie de secties Filtersyntaxis en Filtervelden voor de syntaxis, velden en operators die u in deze parameter kunt gebruiken.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-125">See the Filter syntax and Filter fields sections for the syntax, fields, and operators to use in this parameter.</span></span> |

### <a name="filter-syntax"></a><span data-ttu-id="2fdaa-126">Filtersyntaxis</span><span class="sxs-lookup"><span data-stu-id="2fdaa-126">Filter syntax</span></span>

<span data-ttu-id="2fdaa-127">De filterparameter moet bestaan uit een reeks combinaties van velden, waarden en operatoren.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-127">The filter parameter must be composed as a series of field, value, and operator combinations.</span></span> <span data-ttu-id="2fdaa-128">Meerdere combinaties kunnen worden gecombineerd met - **`and`** of **`or`** -operators.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-128">Multiple combinations can be combined using **`and`** or **`or`** operators.</span></span>

<span data-ttu-id="2fdaa-129">Een niet-gecodeerd voorbeeld ziet er als volgende uit:</span><span class="sxs-lookup"><span data-stu-id="2fdaa-129">An unencoded example looks like this:</span></span>

- <span data-ttu-id="2fdaa-130">Tekenreeks: `?filter=Field operator 'Value'`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-130">String: `?filter=Field operator 'Value'`</span></span>
- <span data-ttu-id="2fdaa-131">Booleaanse: `?filter=Field operator Value`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-131">Boolean: `?filter=Field operator Value`</span></span>
- <span data-ttu-id="2fdaa-132">Bevat `?filter=contains(field,'value')`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-132">Contains `?filter=contains(field,'value')`</span></span>

### <a name="filter-fields"></a><span data-ttu-id="2fdaa-133">Filtervelden</span><span class="sxs-lookup"><span data-stu-id="2fdaa-133">Filter fields</span></span>

<span data-ttu-id="2fdaa-134">De filterparameter van de aanvraag bevat een of meer instructies die de rijen in het antwoord filteren.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-134">The filter parameter of the request contains one or more statements that filter the rows in the response.</span></span> <span data-ttu-id="2fdaa-135">Elke instructie bevat een veld en waarde die zijn gekoppeld aan de **`eq`** operators of **`ne`** .</span><span class="sxs-lookup"><span data-stu-id="2fdaa-135">Each statement contains a field and value that are associated with the **`eq`** or **`ne`** operators.</span></span> <span data-ttu-id="2fdaa-136">Sommige velden ondersteunen ook de **`contains`** operators , , , en **`gt`** **`lt`** **`ge`** **`le`** .</span><span class="sxs-lookup"><span data-stu-id="2fdaa-136">Some fields also support the **`contains`**, **`gt`**, **`lt`**, **`ge`**, and **`le`** operators.</span></span> <span data-ttu-id="2fdaa-137">Instructies kunnen worden gecombineerd met behulp van **`and`** - of **`or`** -operators.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-137">Statements can be combined using **`and`** or **`or`** operators.</span></span>

<span data-ttu-id="2fdaa-138">Hier volgen enkele voorbeelden van filterreeksen:</span><span class="sxs-lookup"><span data-stu-id="2fdaa-138">The following are examples of filter strings:</span></span>

```http
autoRenewEnabled eq true

autoRenewEnabled eq true and customerMarket eq 'US'
```

<span data-ttu-id="2fdaa-139">In de volgende tabel ziet u een lijst met de ondersteunde velden en ondersteuningsoperators voor de filterparameter.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-139">The following table shows a list of the supported fields and support operators for the filter parameter.</span></span> <span data-ttu-id="2fdaa-140">Tekenreekswaarden moeten tussen enkele aanhalingstekens staan.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-140">String values must be surrounded by single quotes.</span></span>

| <span data-ttu-id="2fdaa-141">Parameter</span><span class="sxs-lookup"><span data-stu-id="2fdaa-141">Parameter</span></span> | <span data-ttu-id="2fdaa-142">Ondersteunde operators</span><span class="sxs-lookup"><span data-stu-id="2fdaa-142">Supported operators</span></span> | <span data-ttu-id="2fdaa-143">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="2fdaa-143">Description</span></span> |
|-----------|---------------------|-------------|
| <span data-ttu-id="2fdaa-144">autoRenewEnabled</span><span class="sxs-lookup"><span data-stu-id="2fdaa-144">autoRenewEnabled</span></span> | <span data-ttu-id="2fdaa-145">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-145">`eq`, `ne`</span></span> | <span data-ttu-id="2fdaa-146">Een waarde die aangeeft of het abonnement automatisch wordt verlengd.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-146">A value indicating whether the subscription is renewed automatically.</span></span> |
| <span data-ttu-id="2fdaa-147">commitmentEndDate</span><span class="sxs-lookup"><span data-stu-id="2fdaa-147">commitmentEndDate</span></span> | <span data-ttu-id="2fdaa-148">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-148">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="2fdaa-149">De datum waarop het abonnement eindigt.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-149">The date the subscription ends.</span></span> |
| <span data-ttu-id="2fdaa-150">creationDate</span><span class="sxs-lookup"><span data-stu-id="2fdaa-150">creationDate</span></span> | <span data-ttu-id="2fdaa-151">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-151">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="2fdaa-152">De datum waarop het abonnement is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-152">The date the subscription was created.</span></span> |
| <span data-ttu-id="2fdaa-153">currentStateEndDate</span><span class="sxs-lookup"><span data-stu-id="2fdaa-153">currentStateEndDate</span></span> | <span data-ttu-id="2fdaa-154">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-154">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="2fdaa-155">De datum waarop de huidige status van het abonnement wordt gewijzigd.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-155">The date that the current status of the subscription will change.</span></span> |
| <span data-ttu-id="2fdaa-156">customerMarket</span><span class="sxs-lookup"><span data-stu-id="2fdaa-156">customerMarket</span></span> | <span data-ttu-id="2fdaa-157">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-157">`eq`, `ne`</span></span> | <span data-ttu-id="2fdaa-158">Het land/de regio waarin de klant zaken doet.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-158">The country/region that the customer does business in.</span></span> |
| <span data-ttu-id="2fdaa-159">customerName</span><span class="sxs-lookup"><span data-stu-id="2fdaa-159">customerName</span></span> | `contains` | <span data-ttu-id="2fdaa-160">De naam van de klant.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-160">The name of the customer.</span></span> |
| <span data-ttu-id="2fdaa-161">customerTenantId</span><span class="sxs-lookup"><span data-stu-id="2fdaa-161">customerTenantId</span></span> | <span data-ttu-id="2fdaa-162">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-162">`eq`, `ne`</span></span> | <span data-ttu-id="2fdaa-163">Een tekenreeks in GUID-indeling die de tenant van de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-163">A GUID-formatted string that identifies the customer tenant.</span></span> |
| <span data-ttu-id="2fdaa-164">deprovisionedDate</span><span class="sxs-lookup"><span data-stu-id="2fdaa-164">deprovisionedDate</span></span> | <span data-ttu-id="2fdaa-165">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-165">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="2fdaa-166">De datum waarop het abonnement is uitprovisioned.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-166">The date that the subscription was deprovisioned.</span></span> <span data-ttu-id="2fdaa-167">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-167">The default value is null.</span></span> |
| <span data-ttu-id="2fdaa-168">effectiveStartDate</span><span class="sxs-lookup"><span data-stu-id="2fdaa-168">effectiveStartDate</span></span> | <span data-ttu-id="2fdaa-169">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-169">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="2fdaa-170">De datum waarop het abonnement wordt gestart.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-170">The date the subscription starts.</span></span> |
| <span data-ttu-id="2fdaa-171">Friendlyname</span><span class="sxs-lookup"><span data-stu-id="2fdaa-171">friendlyName</span></span> | `contains` | <span data-ttu-id="2fdaa-172">De naam van het abonnement.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-172">The name of the subscription.</span></span> |
| <span data-ttu-id="2fdaa-173">id</span><span class="sxs-lookup"><span data-stu-id="2fdaa-173">id</span></span> | <span data-ttu-id="2fdaa-174">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-174">`eq`, `ne`</span></span> | <span data-ttu-id="2fdaa-175">Een tekenreeks in GUID-indeling die het abonnement identificeert.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-175">A GUID-formatted string that identifies the subscription.</span></span> |
| <span data-ttu-id="2fdaa-176">lastRenewalDate</span><span class="sxs-lookup"><span data-stu-id="2fdaa-176">lastRenewalDate</span></span> | <span data-ttu-id="2fdaa-177">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-177">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="2fdaa-178">De datum waarop het abonnement voor het laatst is vernieuwd.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-178">The date that the subscription was last renewed.</span></span> <span data-ttu-id="2fdaa-179">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-179">The default value is null.</span></span> |
| <span data-ttu-id="2fdaa-180">lastUsageDate</span><span class="sxs-lookup"><span data-stu-id="2fdaa-180">lastUsageDate</span></span> | <span data-ttu-id="2fdaa-181">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-181">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="2fdaa-182">De datum waarop het abonnement voor het laatst is gebruikt.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-182">The date that the subscription was last used.</span></span> <span data-ttu-id="2fdaa-183">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-183">The default value is null.</span></span> |
| <span data-ttu-id="2fdaa-184">partnerId</span><span class="sxs-lookup"><span data-stu-id="2fdaa-184">partnerId</span></span> | <span data-ttu-id="2fdaa-185">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-185">`eq`, `ne`</span></span> | <span data-ttu-id="2fdaa-186">De MPN-id.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-186">The MPN ID.</span></span> <span data-ttu-id="2fdaa-187">Voor een directe reseller is deze waarde de MPN-id van de partner.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-187">For a direct reseller, this value will be the MPN ID of the partner.</span></span> <span data-ttu-id="2fdaa-188">Voor een indirecte reseller is deze waarde de MPN-id van de indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-188">For an indirect reseller, this value will be the MPN ID of the indirect reseller.</span></span> |
| <span data-ttu-id="2fdaa-189">partnerName</span><span class="sxs-lookup"><span data-stu-id="2fdaa-189">partnerName</span></span> | <span data-ttu-id="2fdaa-190">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2fdaa-190">string</span></span> | <span data-ttu-id="2fdaa-191">Naam van de partner voor wie het abonnement is gekocht</span><span class="sxs-lookup"><span data-stu-id="2fdaa-191">Name of the partner for whom the subscription was purchased</span></span> |
| <span data-ttu-id="2fdaa-192">Productnaam</span><span class="sxs-lookup"><span data-stu-id="2fdaa-192">productName</span></span> | <span data-ttu-id="2fdaa-193">`contains`, `eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-193">`contains`, `eq`, `ne`</span></span> | <span data-ttu-id="2fdaa-194">De naam van het product.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-194">The name of the product.</span></span> |
| <span data-ttu-id="2fdaa-195">providerName</span><span class="sxs-lookup"><span data-stu-id="2fdaa-195">providerName</span></span> | <span data-ttu-id="2fdaa-196">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="2fdaa-196">string</span></span> | <span data-ttu-id="2fdaa-197">Wanneer de abonnementstransactie voor de indirecte reseller is, is de providernaam de indirecte provider die het abonnement heeft gekocht.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-197">When subscription transaction is for the indirect reseller, provider name is the indirect provider who bought the subscription.</span></span>|
| <span data-ttu-id="2fdaa-198">status</span><span class="sxs-lookup"><span data-stu-id="2fdaa-198">status</span></span> | <span data-ttu-id="2fdaa-199">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-199">`eq`, `ne`</span></span> | <span data-ttu-id="2fdaa-200">De abonnementsstatus.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-200">The subscription status.</span></span> <span data-ttu-id="2fdaa-201">Ondersteunde waarden zijn: 'ACTIEF', 'SUSPENDED' of 'DEPROVISIONED'.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-201">Supported values are: "ACTIVE", "SUSPENDED", or "DEPROVISIONED".</span></span> |
| <span data-ttu-id="2fdaa-202">subscriptionType</span><span class="sxs-lookup"><span data-stu-id="2fdaa-202">subscriptionType</span></span> | <span data-ttu-id="2fdaa-203">`eq`, `ne`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-203">`eq`, `ne`</span></span> | <span data-ttu-id="2fdaa-204">Het abonnementstype.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-204">The subscription type.</span></span> <span data-ttu-id="2fdaa-205">**Opmerking:** dit veld is casegevoelig.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-205">**Note**: This field is case-sensitive.</span></span> <span data-ttu-id="2fdaa-206">Ondersteunde waarden zijn: 'Office', 'Azure', 'Microsoft365', 'Dynamics', 'EMS'.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-206">Supported values are: "Office", "Azure", "Microsoft365", "Dynamics", "EMS".</span></span> |
| <span data-ttu-id="2fdaa-207">trialStartDate</span><span class="sxs-lookup"><span data-stu-id="2fdaa-207">trialStartDate</span></span> | <span data-ttu-id="2fdaa-208">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-208">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span> | <span data-ttu-id="2fdaa-209">De datum waarop de proefperiode voor het abonnement is gestart.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-209">The date that the trial period for the subscription started.</span></span> <span data-ttu-id="2fdaa-210">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-210">The default value is null.</span></span> |
| <span data-ttu-id="2fdaa-211">trialToPaidConversionDate</span><span class="sxs-lookup"><span data-stu-id="2fdaa-211">trialToPaidConversionDate</span></span> | <span data-ttu-id="2fdaa-212">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span><span class="sxs-lookup"><span data-stu-id="2fdaa-212">`eq`, `ne`, `gt`, `lt`, `ge`, `le`</span></span>  | <span data-ttu-id="2fdaa-213">De datum waarop het abonnement wordt omgezet van proefversie naar betaald.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-213">The date that the subscription converts from trial to paid.</span></span> <span data-ttu-id="2fdaa-214">De standaardwaarde is null.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-214">The default value is null.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="2fdaa-215">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="2fdaa-215">Request headers</span></span>

<span data-ttu-id="2fdaa-216">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="2fdaa-216">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="2fdaa-217">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="2fdaa-217">Request body</span></span>

<span data-ttu-id="2fdaa-218">Geen.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-218">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="2fdaa-219">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="2fdaa-219">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?filter=autoRenewEnabled eq true
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="2fdaa-220">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="2fdaa-220">REST response</span></span>

<span data-ttu-id="2fdaa-221">Als dit lukt, bevat de antwoord-body een verzameling [abonnementsresources](partner-center-analytics-resources.md#subscription-resource) die voldoen aan de filtercriteria.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-221">If successful, the response body contains a collection of [Subscription](partner-center-analytics-resources.md#subscription-resource) resources that meet the filter criteria.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="2fdaa-222">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="2fdaa-222">Response success and error codes</span></span>

<span data-ttu-id="2fdaa-223">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-223">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="2fdaa-224">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="2fdaa-224">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="2fdaa-225">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="2fdaa-225">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="2fdaa-226">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="2fdaa-226">Response example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="2fdaa-227">Zie ook</span><span class="sxs-lookup"><span data-stu-id="2fdaa-227">See also</span></span>

- [<span data-ttu-id="2fdaa-228">Partnercentrum Analytics - Bronnen</span><span class="sxs-lookup"><span data-stu-id="2fdaa-228">Partner Center Analytics - Resources</span></span>](partner-center-analytics-resources.md)
