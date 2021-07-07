---
title: Indirecte reseller maken in Sandbox
description: Biedt informatie voor indirecte sandboxproviders over het inschakelen van end-to-end testen met behulp van API's.
ms.date: 5/24/2021
ms.author: vijvala
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 93e26792b66e447a0047bd550f4302c7fca4e87b
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973431"
---
# <a name="create-indirect-reseller-in-sandbox"></a><span data-ttu-id="9a14f-103">Indirecte reseller maken in Sandbox</span><span class="sxs-lookup"><span data-stu-id="9a14f-103">Create Indirect Reseller in Sandbox</span></span>

<span data-ttu-id="9a14f-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="9a14f-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="9a14f-105">In dit document ziet u hoe u indirecte sandboxproviders maakt en end-to-end-tests inschakelen met behulp van API's.</span><span class="sxs-lookup"><span data-stu-id="9a14f-105">This document shows how to create Sandbox Indirect Providers and enable end-to-end testing using APIs.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9a14f-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9a14f-106">Prerequisites</span></span>

- <span data-ttu-id="9a14f-107">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="9a14f-107">Credentials as described in [Partner Center Authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9a14f-108">Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="9a14f-108">This scenario supports authentication with App+User credentials.</span></span>

## <a name="csp-indirect-provider"></a><span data-ttu-id="9a14f-109">CSP Indirect Provider</span><span class="sxs-lookup"><span data-stu-id="9a14f-109">CSP Indirect Provider</span></span>

| <span data-ttu-id="9a14f-110">Productiemogelijkheden</span><span class="sxs-lookup"><span data-stu-id="9a14f-110">Production capabilities</span></span>             | <span data-ttu-id="9a14f-111">Sandbox-mogelijkheden</span><span class="sxs-lookup"><span data-stu-id="9a14f-111">Sandbox capabilities</span></span>                            |
|-------------------------------------|-------------------------------------------------|
| <span data-ttu-id="9a14f-112">Verkoopt via de indirecte reseller aan de eindklant</span><span class="sxs-lookup"><span data-stu-id="9a14f-112">Sells through the indirect reseller to the end customer</span></span> | <span data-ttu-id="9a14f-113">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="9a14f-113">Supported</span></span> |
| <span data-ttu-id="9a14f-114">Is eigenaar van alle verkopen, facturering, inrichting en beheer/ondersteuning</span><span class="sxs-lookup"><span data-stu-id="9a14f-114">Owns all sales, billing, provisioning, and management/support</span></span> | <span data-ttu-id="9a14f-115">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="9a14f-115">Supported</span></span> |
| <span data-ttu-id="9a14f-116">Een samenwerking met de wederverkopers aanvragen</span><span class="sxs-lookup"><span data-stu-id="9a14f-116">Request a partnership with the resellers</span></span> | <span data-ttu-id="9a14f-117">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="9a14f-117">Supported</span></span> |
| <span data-ttu-id="9a14f-118">Klanten weergeven per reseller</span><span class="sxs-lookup"><span data-stu-id="9a14f-118">View customers by Reseller</span></span> | <span data-ttu-id="9a14f-119">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="9a14f-119">Supported</span></span> |
| <span data-ttu-id="9a14f-120">Nieuwe klanten toevoegen per reseller</span><span class="sxs-lookup"><span data-stu-id="9a14f-120">Add new customers by resellers</span></span> | <span data-ttu-id="9a14f-121">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="9a14f-121">Supported</span></span> |
| <span data-ttu-id="9a14f-122">Klanten uitnodigen</span><span class="sxs-lookup"><span data-stu-id="9a14f-122">Invite customers</span></span> | <span data-ttu-id="9a14f-123">Aanvraag voor klantrelatie wordt niet ondersteund in Sandbox</span><span class="sxs-lookup"><span data-stu-id="9a14f-123">Customer relationship request not supported in Sandbox</span></span> |
| <span data-ttu-id="9a14f-124">Indirecte sandboxprovider kan sandbox-IR (MPN-id) selecteren als DEEMAN tijdens het plaatsen van de transactie</span><span class="sxs-lookup"><span data-stu-id="9a14f-124">Sandbox Indirect Provider can select Sandbox IR (MPN ID) as the POR while placing the transaction</span></span> | <span data-ttu-id="9a14f-125">Ondersteund</span><span class="sxs-lookup"><span data-stu-id="9a14f-125">Supported</span></span> |
| <span data-ttu-id="9a14f-126">Niet ondersteund in productie</span><span class="sxs-lookup"><span data-stu-id="9a14f-126">Not supported in production</span></span> | <span data-ttu-id="9a14f-127">Indirecte sandboxprovider kan indirecte sandbox-reseller maken</span><span class="sxs-lookup"><span data-stu-id="9a14f-127">Sandbox Indirect Provider can create Sandbox Indirect Reseller</span></span> |
| <span data-ttu-id="9a14f-128">MpN-id voor sandbox moet worden ingevoerd. De MPN-id van het product werkt niet</span><span class="sxs-lookup"><span data-stu-id="9a14f-128">Sandbox MPN ID should be entered, the product MPN ID will not work</span></span> | <span data-ttu-id="9a14f-129">Niet ondersteund in productie</span><span class="sxs-lookup"><span data-stu-id="9a14f-129">Not supported in production</span></span> |
| <span data-ttu-id="9a14f-130">Niet ondersteund in productie</span><span class="sxs-lookup"><span data-stu-id="9a14f-130">Not supported in production</span></span> | <span data-ttu-id="9a14f-131">Indirecte sandboxprovider kan indirecte sandbox-reseller verwijderen</span><span class="sxs-lookup"><span data-stu-id="9a14f-131">Sandbox Indirect Provider can delete Sandbox Indirect Reseller</span></span> |

## <a name="sandbox-indirect-provider--create-sandbox-indirect-reseller"></a><span data-ttu-id="9a14f-132">Indirecte sandboxprovider : indirecte sandbox-reseller maken</span><span class="sxs-lookup"><span data-stu-id="9a14f-132">Sandbox Indirect Provider – Create Sandbox Indirect Reseller</span></span>

<span data-ttu-id="9a14f-133">Deze functie is alleen beschikbaar in de sandbox en biedt indirecte sandboxproviders de mogelijkheid om indirecte sandbox-resellers te maken.</span><span class="sxs-lookup"><span data-stu-id="9a14f-133">This feature is only available in the Sandbox and gives Sandbox Indirect Providers an ability to create Sandbox Indirect Resellers.</span></span>

1. <span data-ttu-id="9a14f-134">Limiet van vijf indirecte sandbox-resellers die zijn toegestaan per indirecte sandboxprovider</span><span class="sxs-lookup"><span data-stu-id="9a14f-134">Limit of five Sandbox Indirect Resellers allowed per Sandbox Indirect Provider</span></span>
2. <span data-ttu-id="9a14f-135">Indirecte sandboxproviders kunnen klanten maken met `associatedPartnerId` van indirecte Sandbox-reseller</span><span class="sxs-lookup"><span data-stu-id="9a14f-135">Sandbox Indirect Providers can create customers with `associatedPartnerId` of Sandbox Indirect Reseller</span></span>
3. <span data-ttu-id="9a14f-136">Voer de [MPN-id](/partner-center/mpn-create-a-partner-center-account) van een specifieke regio in tijdens het maken van een indirecte sandbox-reseller.</span><span class="sxs-lookup"><span data-stu-id="9a14f-136">Enter the [MPN](/partner-center/mpn-create-a-partner-center-account) ID of a specific region while creating a Sandbox Indirect Reseller.</span></span> <span data-ttu-id="9a14f-137">Er kunnen meerdere indirecte sandbox-resellers worden gemaakt met dezelfde MPN-id voor sandboxs.</span><span class="sxs-lookup"><span data-stu-id="9a14f-137">Multiple Sandbox Indirect Resellers can be created with the same Sandbox MPN ID.</span></span>
4. <span data-ttu-id="9a14f-138">Slechts 75 klanten zijn toegestaan per indirecte sandboxprovider</span><span class="sxs-lookup"><span data-stu-id="9a14f-138">Only 75 customers are allowed per Sandbox Indirect Provider</span></span>

## <a name="sandbox-indirect-resellers--view-customers"></a><span data-ttu-id="9a14f-139">Indirecte sandbox-resellers : klanten weergeven</span><span class="sxs-lookup"><span data-stu-id="9a14f-139">Sandbox Indirect Resellers – View customers</span></span>

1. <span data-ttu-id="9a14f-140">Indirecte sandbox-resellers kunnen de lijst met sandbox-klanten weergeven op indirecte Sandbox-providers.</span><span class="sxs-lookup"><span data-stu-id="9a14f-140">Sandbox Indirect Resellers can view the list of sandbox customers by Sandbox Indirect providers.</span></span>
2. <span data-ttu-id="9a14f-141">Indirecte resellers in sandbox kunnen het klantaccount beheren met behulp van gedelegeerde beheerdersmachtigingen.</span><span class="sxs-lookup"><span data-stu-id="9a14f-141">Sandbox Indirect Resellers can manage the customer account by using delegated administrator permissions.</span></span>

## <a name="create-sandbox-indirect-reseller-through-api"></a><span data-ttu-id="9a14f-142">Indirecte sandbox-reseller maken via API</span><span class="sxs-lookup"><span data-stu-id="9a14f-142">Create Sandbox Indirect Reseller through API</span></span>

### <a name="rest-request"></a><span data-ttu-id="9a14f-143">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9a14f-143">REST request</span></span>

#### <a name="request-syntax"></a><span data-ttu-id="9a14f-144">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="9a14f-144">Request syntax</span></span>

| <span data-ttu-id="9a14f-145">**Methode**</span><span class="sxs-lookup"><span data-stu-id="9a14f-145">**Method**</span></span> | <span data-ttu-id="9a14f-146">**Aanvraag-URI**</span><span class="sxs-lookup"><span data-stu-id="9a14f-146">**Request URI**</span></span>                                                        |
|------------|------------------------------------------------------------------------|
| <span data-ttu-id="9a14f-147">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="9a14f-147">**POST**</span></span>   | <span data-ttu-id="9a14f-148">[*{baseURL}*](partner-center-rest-urls.md)/v1 sandboxIndirectReseller</span><span class="sxs-lookup"><span data-stu-id="9a14f-148">[*{baseURL}*](partner-center-rest-urls.md)/v1//sandboxIndirectReseller</span></span> |

#### <a name="request-headers"></a><span data-ttu-id="9a14f-149">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9a14f-149">Request headers</span></span>

- <span data-ttu-id="9a14f-150">Deze API is idempotent (deze levert geen ander resultaat op als u deze meerdere keren aanroept).</span><span class="sxs-lookup"><span data-stu-id="9a14f-150">This API is idempotent (it will not yield a different result if you call it multiple times).</span></span>
- <span data-ttu-id="9a14f-151">Een aanvraag-id en correlatie-id zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="9a14f-151">A request ID and correlation ID are required.</span></span>
- <span data-ttu-id="9a14f-152">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="9a14f-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

#### <a name="request-body"></a><span data-ttu-id="9a14f-153">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9a14f-153">Request body</span></span>

<span data-ttu-id="9a14f-154">In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="9a14f-154">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="9a14f-155">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="9a14f-155">Property</span></span>             | <span data-ttu-id="9a14f-156">Type</span><span class="sxs-lookup"><span data-stu-id="9a14f-156">Type</span></span>           | <span data-ttu-id="9a14f-157">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9a14f-157">Description</span></span>                                      |
|----------------------|----------------|--------------------------------------------------|
| <span data-ttu-id="9a14f-158">mpnId</span><span class="sxs-lookup"><span data-stu-id="9a14f-158">mpnId</span></span>                | <span data-ttu-id="9a14f-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-159">string</span></span>         | <span data-ttu-id="9a14f-160">De MPN-id voor de IR in een specifieke regio</span><span class="sxs-lookup"><span data-stu-id="9a14f-160">The MPN ID for the IR in specific region</span></span>         |
| <span data-ttu-id="9a14f-161">tenant</span><span class="sxs-lookup"><span data-stu-id="9a14f-161">tenant</span></span>               | <span data-ttu-id="9a14f-162">&lt;Woordenlijstreeks, tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="9a14f-162">Dictionary&lt;string, string&gt;</span></span> | <span data-ttu-id="9a14f-163">Verzameling basisinformatie die een account definieert dat moet worden gemaakt</span><span class="sxs-lookup"><span data-stu-id="9a14f-163">Collection of basic information that defines an account to be created</span></span> |
| <span data-ttu-id="9a14f-164">legalBusinessProfile</span><span class="sxs-lookup"><span data-stu-id="9a14f-164">legalBusinessProfile</span></span> | <span data-ttu-id="9a14f-165">&lt;Woordenlijstreeks, tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="9a14f-165">Dictionary&lt;string, string&gt;</span></span> | <span data-ttu-id="9a14f-166">Verzameling informatie die de juridische bedrijfsentiteit vertegenwoordigt, zoals contactpersoon, adres en naam</span><span class="sxs-lookup"><span data-stu-id="9a14f-166">Collection of information that represents the legal business entity such as contact, address, and name</span></span> |
| <span data-ttu-id="9a14f-167">organizationProfileLanguage</span><span class="sxs-lookup"><span data-stu-id="9a14f-167">organizationProfileLanguage</span></span> | <span data-ttu-id="9a14f-168">&lt;Woordenlijstreeks, tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="9a14f-168">Dictionary&lt;string, string&gt;</span></span> | <span data-ttu-id="9a14f-169">De taal-id van de organisatie</span><span class="sxs-lookup"><span data-stu-id="9a14f-169">The organization language identifier</span></span> |

<span data-ttu-id="9a14f-170">In deze tabel worden de vereiste eigenschappen in het **tenantkenmerk** beschreven.</span><span class="sxs-lookup"><span data-stu-id="9a14f-170">This table describes the required properties in the **tenant** attribute.</span></span>

| <span data-ttu-id="9a14f-171">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="9a14f-171">Property</span></span>           | <span data-ttu-id="9a14f-172">Type</span><span class="sxs-lookup"><span data-stu-id="9a14f-172">Type</span></span>           | <span data-ttu-id="9a14f-173">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9a14f-173">Description</span></span>                         |
|--------------------|----------------|-------------------------------------|
| <span data-ttu-id="9a14f-174">domainPrefix</span><span class="sxs-lookup"><span data-stu-id="9a14f-174">domainPrefix</span></span>       | <span data-ttu-id="9a14f-175">Tekenreeks; Unieke</span><span class="sxs-lookup"><span data-stu-id="9a14f-175">String; unique</span></span> | <span data-ttu-id="9a14f-176">Domein voor het tenantaccount</span><span class="sxs-lookup"><span data-stu-id="9a14f-176">Domain for the tenant account</span></span>       |
| <span data-ttu-id="9a14f-177">naam</span><span class="sxs-lookup"><span data-stu-id="9a14f-177">name</span></span>               | <span data-ttu-id="9a14f-178">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-178">string</span></span>         | <span data-ttu-id="9a14f-179">Gebruiksvriendelijke naam van de tenant</span><span class="sxs-lookup"><span data-stu-id="9a14f-179">Friendly name of the tenant</span></span>         |
| <span data-ttu-id="9a14f-180">displayName</span><span class="sxs-lookup"><span data-stu-id="9a14f-180">displayName</span></span>        | <span data-ttu-id="9a14f-181">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-181">string</span></span>         | <span data-ttu-id="9a14f-182">Weergavenaam voor het account</span><span class="sxs-lookup"><span data-stu-id="9a14f-182">Display name for the account</span></span>        |
| <span data-ttu-id="9a14f-183">adminUserName</span><span class="sxs-lookup"><span data-stu-id="9a14f-183">adminUserName</span></span>      | <span data-ttu-id="9a14f-184">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-184">string</span></span>         | <span data-ttu-id="9a14f-185">Gebruikersnaam voor het account voor aanmelding</span><span class="sxs-lookup"><span data-stu-id="9a14f-185">User name for the account for login</span></span> |
| <span data-ttu-id="9a14f-186">adminfirstname</span><span class="sxs-lookup"><span data-stu-id="9a14f-186">adminfirstname</span></span>     | <span data-ttu-id="9a14f-187">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-187">string</span></span>         | <span data-ttu-id="9a14f-188">Voornaam voor de gebruiker met beheerdersrechten</span><span class="sxs-lookup"><span data-stu-id="9a14f-188">First Name for the admin user</span></span>       |
| <span data-ttu-id="9a14f-189">adminlastname</span><span class="sxs-lookup"><span data-stu-id="9a14f-189">adminlastname</span></span>      | <span data-ttu-id="9a14f-190">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-190">string</span></span>         | <span data-ttu-id="9a14f-191">Achternaam voor de gebruiker met beheerdersrechten</span><span class="sxs-lookup"><span data-stu-id="9a14f-191">Last Name for the admin user</span></span>        |
| <span data-ttu-id="9a14f-192">adminAlernateEmail</span><span class="sxs-lookup"><span data-stu-id="9a14f-192">adminAlernateEmail</span></span> | <span data-ttu-id="9a14f-193">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-193">string</span></span>         | <span data-ttu-id="9a14f-194">e-mailadres voor de gebruiker met beheerdersrechten</span><span class="sxs-lookup"><span data-stu-id="9a14f-194">email for the admin user</span></span>            |
| <span data-ttu-id="9a14f-195">country</span><span class="sxs-lookup"><span data-stu-id="9a14f-195">country</span></span>            | <span data-ttu-id="9a14f-196">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-196">string</span></span>         | <span data-ttu-id="9a14f-197">Land van het account</span><span class="sxs-lookup"><span data-stu-id="9a14f-197">Country of the account</span></span>              |
| <span data-ttu-id="9a14f-198">Cultuur</span><span class="sxs-lookup"><span data-stu-id="9a14f-198">culture</span></span>            | <span data-ttu-id="9a14f-199">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-199">string</span></span>         | <span data-ttu-id="9a14f-200">Taalvoorkeur voor account</span><span class="sxs-lookup"><span data-stu-id="9a14f-200">Language preference for account</span></span>     |

<span data-ttu-id="9a14f-201">In deze tabel worden de vereiste eigenschappen in het **kenmerk legalBusinessProfile** beschreven.</span><span class="sxs-lookup"><span data-stu-id="9a14f-201">This table describes the required properties in the **legalBusinessProfile** attribute.</span></span>

| <span data-ttu-id="9a14f-202">Eigenschap</span><span class="sxs-lookup"><span data-stu-id="9a14f-202">Property</span></span>       | <span data-ttu-id="9a14f-203">Type</span><span class="sxs-lookup"><span data-stu-id="9a14f-203">Type</span></span>                             | <span data-ttu-id="9a14f-204">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9a14f-204">Description</span></span>                          |
|----------------|----------------------------------|--------------------------------------|
| <span data-ttu-id="9a14f-205">companyName</span><span class="sxs-lookup"><span data-stu-id="9a14f-205">companyName</span></span>    | <span data-ttu-id="9a14f-206">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-206">string</span></span>                           | <span data-ttu-id="9a14f-207">Bedrijfsnaam voor juridische entiteit</span><span class="sxs-lookup"><span data-stu-id="9a14f-207">Company name for legal entity</span></span>        |
| <span data-ttu-id="9a14f-208">adres</span><span class="sxs-lookup"><span data-stu-id="9a14f-208">address</span></span>        | <span data-ttu-id="9a14f-209">&lt;Woordenlijstreeks, tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="9a14f-209">Dictionary&lt;string, string&gt;</span></span> | <span data-ttu-id="9a14f-210">Adres van de locatie van de juridische entiteit</span><span class="sxs-lookup"><span data-stu-id="9a14f-210">Address of the legal entity location</span></span> |
| <span data-ttu-id="9a14f-211">primaryContact</span><span class="sxs-lookup"><span data-stu-id="9a14f-211">primaryContact</span></span> | <span data-ttu-id="9a14f-212">&lt;Woordenlijstreeks, tekenreeks&gt;</span><span class="sxs-lookup"><span data-stu-id="9a14f-212">Dictionary&lt;string, string&gt;</span></span> | <span data-ttu-id="9a14f-213">Contactgegevens van het bedrijf</span><span class="sxs-lookup"><span data-stu-id="9a14f-213">Contact details of the company</span></span>       |
| <span data-ttu-id="9a14f-214">Cultuur</span><span class="sxs-lookup"><span data-stu-id="9a14f-214">culture</span></span>        | <span data-ttu-id="9a14f-215">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9a14f-215">string</span></span>                           | <span data-ttu-id="9a14f-216">Taal die de voorkeur heeft van het bedrijf</span><span class="sxs-lookup"><span data-stu-id="9a14f-216">Language preferred by the company</span></span>    |

### <a name="request-example"></a><span data-ttu-id="9a14f-217">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9a14f-217">Request Example</span></span>

```http
{
    "mpnId": "6363276",
    "tenant": {
        "domainPrefix": "TipIRIntTest705",
        "name": "TipIRIntTest705",
        "displayName": "TipIRIntTest705",
        "adminUserName": "admin",
        "adminFirstName": "TipIRIntTest705",
        "adminLastName": "TipIRIntTest705",
        "adminAlternateEmail": "TipIRIntTest705@test.com",
        "country": "US",
        "culture": "en-us"
    },
    "legalBusinessProfile": {
        "companyName": "TipIRIntTest705",
        "address": {
            "country": "FR",
            "city": "Issy-les-Moulineaux",
            "state": "",
            "addressLine1": "39-41 quai du Président Roosevelt",
            "addressLine2": "",
            "postalCode": "92130"
        },
        "primaryContact": {
            "firstName": "Sandbox",
            "lastName": "Scenario",
            "email": "Sandbox.Scenario@test.com",
            "phoneNumber": "1234567890"
        },
        "culture": "en-US"
    },
    "organizationProfileLanguage": "en"
}
```

### <a name="rest-response"></a><span data-ttu-id="9a14f-218">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9a14f-218">REST response</span></span>

<span data-ttu-id="9a14f-219">Als dit lukt, retourneert deze methode de ingevulde Sandbox IR-resource in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="9a14f-219">If successful, this method returns the populated Sandbox IR resource in the response body.</span></span>

```http
{

    "accountId": "6f94b119-793c-44c7-862b-c327c9057eab",
    "mpnId": "6363276",
    "tenant": {
        "id": "6f94b119-793c-44c7-862b-c327c9057eab",
        "adminUserAccount": "admin@TipIRIntTest705.onmicrosoft.com",
        "password": "\*\*\*\*\*\*”
    },
    "agreementSignature": {
        "id": "30ac23e7-e200-42cf-a5bc-dd9148cdc632",
        "accountId": "6f94b119-793c-44c7-862b-c327c9057eab",
        "agreementId": "1e18c5b2-e42a-4b84-82c8-d0155aa94c6e",
        "agreementType": "ValueAddedReseller",
        "dateSigned": "2021-02-23T18:10:14.8461137Z",
        "signedByFirstName": "Test123@PLAMUATT2NetNewTip.onmicrosoft.com",
        "signedByUserPrincipalName": "Test123@PLAMUATT2NetNewTip.onmicrosoft.com",
        "signedByUserObjectId": "e6e0c29d-acda-4ef2-b370-d37a4e06fb98",
        "signedByUserTenantId": "0e195b37-4574-4539-bc42-0e539b9684c0",
        "attributes": {
            "objectType": "AgreementSignatureResponse"
        }
    },
    "partnerRelationship": {
        "id": "0e195b37-4574-4539-bc42-0e539b9684c0",
        "name": "PLAMUATT2NetNew",
        "relationshipType": "is\_indirect\_reseller\_of",
        "state": "Active",
        "mpnId": "6363276",
        "attributes": {
            "objectType": "PartnerRelationshipResponse"
        }
    }
}
```
