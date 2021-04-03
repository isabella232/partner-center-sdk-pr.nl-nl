---
title: Een klant voor een indirecte reseller maken
description: Meer informatie over hoe een indirecte provider Partner Center-Api's kan gebruiken voor het maken van een klant voor een indirecte wederverkoper.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 13cd1b051abb536d397dcd4000228f67fe3206b8
ms.sourcegitcommit: 204e518e794b6b076a17488ee9ca1aaaa4beaaec
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/01/2021
ms.locfileid: "106103943"
---
# <a name="create-a-customer-for-an-indirect-reseller-using-partner-center-apis"></a><span data-ttu-id="e8cd3-103">Een klant voor een indirecte wederverkoper maken met behulp van partner Center-Api's</span><span class="sxs-lookup"><span data-stu-id="e8cd3-103">Create a customer for an indirect reseller using Partner Center APIs</span></span>

<span data-ttu-id="e8cd3-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="e8cd3-104">**Applies to:**</span></span>

- <span data-ttu-id="e8cd3-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e8cd3-105">Partner Center</span></span>

<span data-ttu-id="e8cd3-106">Een indirecte provider kan een klant maken voor een indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-106">An indirect provider can create a customer for an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e8cd3-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e8cd3-107">Prerequisites</span></span>

- <span data-ttu-id="e8cd3-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="e8cd3-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e8cd3-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e8cd3-110">De Tenant-id van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-110">The tenant identifier of the indirect reseller.</span></span>

- <span data-ttu-id="e8cd3-111">De indirecte wederverkoper moet een partnerschap met de indirecte provider hebben.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-111">The indirect reseller must have a partnership with the indirect provider.</span></span>

## <a name="c"></a><span data-ttu-id="e8cd3-112">C\#</span><span class="sxs-lookup"><span data-stu-id="e8cd3-112">C\#</span></span>

<span data-ttu-id="e8cd3-113">Een nieuwe klant toevoegen voor een indirecte wederverkoper:</span><span class="sxs-lookup"><span data-stu-id="e8cd3-113">To add a new customer for an indirect reseller:</span></span>

1. <span data-ttu-id="e8cd3-114">Exemplaar een nieuw [**klant**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object en pas vervolgens de [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) en [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile)aan.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-114">Instantiate a new [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object and then instantiate and populate the [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) and [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span></span> <span data-ttu-id="e8cd3-115">Zorg ervoor dat u de ID van de indirecte wederverkoper toewijst aan de eigenschap [**AssociatedPartnerID**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid) .</span><span class="sxs-lookup"><span data-stu-id="e8cd3-115">Be sure to assign the indirect reseller ID to the [**AssociatedPartnerID**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid) property.</span></span>

2. <span data-ttu-id="e8cd3-116">Gebruik de eigenschap [**IAggregatePartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) om een interface voor het verzamelen van klanten op te halen.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-116">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) property to get an interface to customer collection operations.</span></span>

3. <span data-ttu-id="e8cd3-117">Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) aan om de klant te maken.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-117">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) method to create the customer.</span></span>

### <a name="c-example"></a><span data-ttu-id="e8cd3-118">C- \# voor beeld</span><span class="sxs-lookup"><span data-stu-id="e8cd3-118">C\# example</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var indirectResellerId;
var customerToCreate = new Customer()
{
    CompanyProfile = new CustomerCompanyProfile()
    {
        Domain = string.Format(CultureInfo.InvariantCulture,
            "WingtipToys{0}.{1}",
            new Random().Next(),
            this.Context.Configuration.Scenario.CustomerDomainSuffix)
    },
    BillingProfile = new CustomerBillingProfile()
    {
        Culture = "EN-US",
        Email = "Gena@wingtiptoys.com",
        Language = "En",
        CompanyName = "Wingtip Toys" + new Random().Next(),
        DefaultAddress = new Address()
        {
            FirstName = "Gena",
            LastName = "Soto",
            AddressLine1 = "One Microsoft Way",
            City = "Redmond",
            State = "WA",
            Country = "US",
            PostalCode = "98052",
            PhoneNumber = "4255550101"
        }
    },
    AssociatedPartnerId = indirectResellerId
};

var newCustomer = partnerOperations.Customers.Create(customerToCreate);
```

<span data-ttu-id="e8cd3-119">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e8cd3-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e8cd3-120">**Project**: Partner Center SDK samples **klasse**: CreateCustomerforIndirectReseller. cs</span><span class="sxs-lookup"><span data-stu-id="e8cd3-120">**Project**: Partner Center SDK Samples **Class**: CreateCustomerforIndirectReseller.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e8cd3-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e8cd3-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e8cd3-122">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e8cd3-122">Request syntax</span></span>

| <span data-ttu-id="e8cd3-123">Methode</span><span class="sxs-lookup"><span data-stu-id="e8cd3-123">Method</span></span>   | <span data-ttu-id="e8cd3-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e8cd3-124">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="e8cd3-125">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="e8cd3-125">**POST**</span></span> | <span data-ttu-id="e8cd3-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers http/1.1</span><span class="sxs-lookup"><span data-stu-id="e8cd3-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e8cd3-127">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e8cd3-127">Request headers</span></span>

<span data-ttu-id="e8cd3-128">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="e8cd3-128">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e8cd3-129">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e8cd3-129">Request body</span></span>

<span data-ttu-id="e8cd3-130">In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-130">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="e8cd3-131">Naam</span><span class="sxs-lookup"><span data-stu-id="e8cd3-131">Name</span></span>                                          | <span data-ttu-id="e8cd3-132">Type</span><span class="sxs-lookup"><span data-stu-id="e8cd3-132">Type</span></span>   | <span data-ttu-id="e8cd3-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="e8cd3-133">Required</span></span> | <span data-ttu-id="e8cd3-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e8cd3-134">Description</span></span>                                                                                                                                                                                                                                                                                                                                           |
|-----------------------------------------------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<span data-ttu-id="e8cd3-135">BillingProfile</span><span class="sxs-lookup"><span data-stu-id="e8cd3-135">BillingProfile</span></span>](#billing-profile)             | <span data-ttu-id="e8cd3-136">object</span><span class="sxs-lookup"><span data-stu-id="e8cd3-136">object</span></span> | <span data-ttu-id="e8cd3-137">Yes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-137">Yes</span></span>      | <span data-ttu-id="e8cd3-138">De facturerings profiel gegevens van de klant.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-138">The customer's billing profile information.</span></span>                                                                                                                                                                                                                                                                                                           |
| [<span data-ttu-id="e8cd3-139">CompanyProfile</span><span class="sxs-lookup"><span data-stu-id="e8cd3-139">CompanyProfile</span></span>](#company-profile)             | <span data-ttu-id="e8cd3-140">object</span><span class="sxs-lookup"><span data-stu-id="e8cd3-140">object</span></span> | <span data-ttu-id="e8cd3-141">Yes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-141">Yes</span></span>      | <span data-ttu-id="e8cd3-142">De gegevens van het bedrijfs profiel van de klant.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-142">The customer's company profile information.</span></span>                                                               
| [<span data-ttu-id="e8cd3-143">AssociatedPartnerId</span><span class="sxs-lookup"><span data-stu-id="e8cd3-143">AssociatedPartnerId</span></span>](customer-resources.md#customer) | <span data-ttu-id="e8cd3-144">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8cd3-144">string</span></span> | <span data-ttu-id="e8cd3-145">Yes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-145">Yes</span></span>      | <span data-ttu-id="e8cd3-146">De ID van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-146">The indirect reseller ID.</span></span> <span data-ttu-id="e8cd3-147">De indirecte wederverkoper zoals aangegeven door de ID die u hier opgeeft, moet een partnerschap met de indirecte provider hebben, anders mislukt de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-147">The indirect reseller as indicated by the ID supplied here must have a partnership with the indirect provider or the request will fail.</span></span> <span data-ttu-id="e8cd3-148">Houd er ook rekening mee dat als de waarde AssociatedPartnerId niet wordt opgegeven, de klant wordt gemaakt als een rechtstreekse klant van de indirecte provider in plaats van de indirecte wederverkoper.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-148">Also note that if the AssociatedPartnerId value isn't supplied, the customer is created as a direct customer of the indirect provider rather than the indirect reseller.</span></span> |
|<span data-ttu-id="e8cd3-149">Domain</span><span class="sxs-lookup"><span data-stu-id="e8cd3-149">Domain</span></span>| <span data-ttu-id="e8cd3-150">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8cd3-150">String</span></span>| <span data-ttu-id="e8cd3-151">Ja</span><span class="sxs-lookup"><span data-stu-id="e8cd3-151">Yes</span></span>|<span data-ttu-id="e8cd3-152">De domein naam van de klant, zoals contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-152">The customer's domain name, such as contoso.onmicrosoft.com.</span></span>|
|<span data-ttu-id="e8cd3-153">organizationRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="e8cd3-153">organizationRegistrationNumber</span></span>|    <span data-ttu-id="e8cd3-154">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8cd3-154">string</span></span>|<span data-ttu-id="e8cd3-155">Yes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-155">Yes</span></span>|     <span data-ttu-id="e8cd3-156">Het registratie nummer van de klant (ook wel INN-nummer genoemd in bepaalde landen).</span><span class="sxs-lookup"><span data-stu-id="e8cd3-156">The customer’s organization registration number (also referred to as INN number in certain countries).</span></span> <span data-ttu-id="e8cd3-157">Alleen vereist voor het bedrijf/de organisatie van de klant in de volgende landen: Armenië (AM), Azerbeidzjan (AZ), Belarus (op), Hongarije (HU), Kazachstan (KZ), Kirgizië (KG), Moldavië (MD), Rusland (RU), Tadzjikistan (TJ), Oezbekistan (UZ), Oekraïne (UA), India, Brazilië, Zuid-Afrika, Polen, Verenigde Arabische Emiraten, Saoedi-Arabië, Turkije, Thai, Vietnam, Myanmar, Irak, Zuid-Soedan en Venezuela.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-157">Only required for customer’s company/organization located in the following countries: Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA), India, Brazil, South Africa, Poland, United Arab Emirates, Saudi Arabia, Turkey, Thailand, Vietnam, Myanmar, Iraq, South Sudan and Venezuela.</span></span> <span data-ttu-id="e8cd3-158">Voor het bedrijf/de organisatie van de klant in andere landen is dit een optioneel veld.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-158">For customer’s company/organization located in other countries this is an optional field.</span></span>|



#### <a name="billing-profile"></a><span data-ttu-id="e8cd3-159">Factureringsprofiel</span><span class="sxs-lookup"><span data-stu-id="e8cd3-159">Billing profile</span></span>

<span data-ttu-id="e8cd3-160">In deze tabel worden de minimale vereiste velden van de [CustomerBillingProfile](customer-resources.md#customerbillingprofile) -resource beschreven die nodig zijn om een nieuwe klant te maken.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-160">This table describes the minimum required fields from the [CustomerBillingProfile](customer-resources.md#customerbillingprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="e8cd3-161">Naam</span><span class="sxs-lookup"><span data-stu-id="e8cd3-161">Name</span></span>             | <span data-ttu-id="e8cd3-162">Type</span><span class="sxs-lookup"><span data-stu-id="e8cd3-162">Type</span></span>                                     | <span data-ttu-id="e8cd3-163">Vereist</span><span class="sxs-lookup"><span data-stu-id="e8cd3-163">Required</span></span> | <span data-ttu-id="e8cd3-164">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e8cd3-164">Description</span></span>                                                                                                                                                                                                     |
|------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e8cd3-165">e-mail</span><span class="sxs-lookup"><span data-stu-id="e8cd3-165">email</span></span>            | <span data-ttu-id="e8cd3-166">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8cd3-166">string</span></span>                                   | <span data-ttu-id="e8cd3-167">Yes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-167">Yes</span></span>      | <span data-ttu-id="e8cd3-168">Het e-mail adres van de klant.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-168">The customer's email address.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="e8cd3-169">culturele</span><span class="sxs-lookup"><span data-stu-id="e8cd3-169">culture</span></span>          | <span data-ttu-id="e8cd3-170">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8cd3-170">string</span></span>                                   | <span data-ttu-id="e8cd3-171">Yes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-171">Yes</span></span>      | <span data-ttu-id="e8cd3-172">De voorkeurs cultuur voor communicatie en valuta, zoals ' en-US '.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-172">Their preferred culture for communication and currency, such as "en-US".</span></span> <span data-ttu-id="e8cd3-173">Zie [ondersteunde talen en land instellingen voor het partner centrum](partner-center-supported-languages-and-locales.md) voor de ondersteunde cult uren.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-173">See [Partner Center supported languages and locales](partner-center-supported-languages-and-locales.md) for the supported cultures.</span></span> |
| <span data-ttu-id="e8cd3-174">language</span><span class="sxs-lookup"><span data-stu-id="e8cd3-174">language</span></span>         | <span data-ttu-id="e8cd3-175">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8cd3-175">string</span></span>                                   | <span data-ttu-id="e8cd3-176">Yes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-176">Yes</span></span>      | <span data-ttu-id="e8cd3-177">De standaard taal.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-177">The default language.</span></span> <span data-ttu-id="e8cd3-178">Taal codes voor twee tekens (bijvoorbeeld `en` of `fr` ) worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-178">Two character language codes (for example `en` or `fr`) are supported.</span></span>                                                                                                                                |
| <span data-ttu-id="e8cd3-179">bedrijfs \_ naam</span><span class="sxs-lookup"><span data-stu-id="e8cd3-179">company\_name</span></span>    | <span data-ttu-id="e8cd3-180">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8cd3-180">string</span></span>                                   | <span data-ttu-id="e8cd3-181">Yes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-181">Yes</span></span>      | <span data-ttu-id="e8cd3-182">De naam van het geregistreerde bedrijf/de organisatie.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-182">The registered company/organization name.</span></span>                                                                                                                                                                       |
| <span data-ttu-id="e8cd3-183">standaard \_ adres</span><span class="sxs-lookup"><span data-stu-id="e8cd3-183">default\_address</span></span> | [<span data-ttu-id="e8cd3-184">Adres</span><span class="sxs-lookup"><span data-stu-id="e8cd3-184">Address</span></span>](utility-resources.md#address) | <span data-ttu-id="e8cd3-185">Yes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-185">Yes</span></span>      | <span data-ttu-id="e8cd3-186">Het geregistreerde adres van het bedrijf/de organisatie van de klant.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-186">The registered address of the customer's company/organization.</span></span> <span data-ttu-id="e8cd3-187">Zie de [adres](utility-resources.md#address) bron voor informatie over de beperkingen van elke lengte.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-187">See the [Address](utility-resources.md#address) resource for information on any length limitations.</span></span>                                             |

#### <a name="company-profile"></a><span data-ttu-id="e8cd3-188">Bedrijfs profiel</span><span class="sxs-lookup"><span data-stu-id="e8cd3-188">Company profile</span></span>

<span data-ttu-id="e8cd3-189">In deze tabel worden de minimale vereiste velden van de [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) -resource beschreven die nodig zijn om een nieuwe klant te maken.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-189">This table describes the minimum required fields from the [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="e8cd3-190">Naam</span><span class="sxs-lookup"><span data-stu-id="e8cd3-190">Name</span></span>   | <span data-ttu-id="e8cd3-191">Type</span><span class="sxs-lookup"><span data-stu-id="e8cd3-191">Type</span></span>   | <span data-ttu-id="e8cd3-192">Vereist</span><span class="sxs-lookup"><span data-stu-id="e8cd3-192">Required</span></span> | <span data-ttu-id="e8cd3-193">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e8cd3-193">Description</span></span>                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| <span data-ttu-id="e8cd3-194">domein</span><span class="sxs-lookup"><span data-stu-id="e8cd3-194">domain</span></span> | <span data-ttu-id="e8cd3-195">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8cd3-195">string</span></span> | <span data-ttu-id="e8cd3-196">Yes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-196">Yes</span></span>     | <span data-ttu-id="e8cd3-197">De domein naam van de klant, zoals contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-197">The customer's domain name, such as contoso.onmicrosoft.com.</span></span> |
| <span data-ttu-id="e8cd3-198">organizationRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="e8cd3-198">organizationRegistrationNumber</span></span> | <span data-ttu-id="e8cd3-199">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e8cd3-199">string</span></span> | <span data-ttu-id="e8cd3-200">Is afhankelijk van de voor waarde</span><span class="sxs-lookup"><span data-stu-id="e8cd3-200">Depends on condition</span></span> | <span data-ttu-id="e8cd3-201">Het registratie nummer van de klant (ook wel het INN-nummer in bepaalde landen genoemd).</span><span class="sxs-lookup"><span data-stu-id="e8cd3-201">The customer’s organization registration number (also referred to as the INN number in certain countries).</span></span> <br/><br/><span data-ttu-id="e8cd3-202">Volt ooien van dit veld is alleen vereist als het bedrijf/de organisatie van een klant zich in de volgende landen bevindt:</span><span class="sxs-lookup"><span data-stu-id="e8cd3-202">Completing this field is required only if a customer’s company/organization is located in the following countries:</span></span> <br/><br/><span data-ttu-id="e8cd3-203">-Armenië (AM)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-203">- Armenia (AM)</span></span> <br/><span data-ttu-id="e8cd3-204">-Azerbeidzjan (AZ)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-204">- Azerbaijan (AZ)</span></span><br/><span data-ttu-id="e8cd3-205">-Belarus (per)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-205">- Belarus (BY)</span></span><br/><span data-ttu-id="e8cd3-206">-Hongarije (HU)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-206">- Hungary (HU)</span></span><br/><span data-ttu-id="e8cd3-207">-Kazachstan (KZ)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-207">- Kazakhstan (KZ)</span></span><br/><span data-ttu-id="e8cd3-208">-Kirgizië (KG)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-208">- Kyrgyzstan (KG)</span></span><br/><span data-ttu-id="e8cd3-209">-Moldavië (MD)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-209">- Moldova (MD)</span></span><br/><span data-ttu-id="e8cd3-210">-Rusland (RU)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-210">- Russia (RU)</span></span><br/><span data-ttu-id="e8cd3-211">-Tadzjikistan (TJ)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-211">- Tajikistan (TJ)</span></span><br/><span data-ttu-id="e8cd3-212">-Oezbekistan (UZ)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-212">- Uzbekistan (UZ)</span></span><br/><span data-ttu-id="e8cd3-213">-Oekraïne (UA)</span><span class="sxs-lookup"><span data-stu-id="e8cd3-213">- Ukraine (UA)</span></span><br/><br/><span data-ttu-id="e8cd3-214">Dit veld is niet vereist als het bedrijf/de organisatie van de klant zich in andere landen bevindt dan de hier weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-214">This field is not required if the customer’s company/organization is located in other countries beyond those shown here.</span></span>  |

### <a name="request-example"></a><span data-ttu-id="e8cd3-215">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e8cd3-215">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: d628adbe-b7ee-412e-ac55-58f22b4ba2f4
MS-CorrelationId: 0dd197a8-992c-44ca-aeae-21cd83494dce
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 823
Expect: 100-continue
Connection: Keep-Alive

{
    "Id": null,
    "CommerceId": null,
    "CompanyProfile": {
        "TenantId": null,
        "Domain": "WingtipToys678152504.onmicrosoft.com",
        "CompanyName": null,
        "Attributes": {
            "ObjectType": "CustomerCompanyProfile"
        }
    },
    "BillingProfile": {
        "Id": null,
        "FirstName": null,
        "LastName": null,
        "Email": "Gena@wingtiptoys.com",
        "Culture": "EN-US",
        "Language": "En",
        "CompanyName": "Wingtip Toys678152504",
        "DefaultAddress": {
            "Country": "US",
            "Region": null,
            "City": "Redmond",
            "State": "WA",
            "AddressLine1": "One Microsoft Way",
            "AddressLine2": null,
            "PostalCode": "98052",
            "FirstName": "Gena",
            "LastName": "Soto",
            "PhoneNumber": "4255550101"
        },
        "Attributes": {
            "ObjectType": "CustomerBillingProfile"
        }
    },
    "RelationshipToPartner": "none",
    "AllowDelegatedAccess": null,
    "UserCredentials": null,
    "CustomDomains": null,
    "AssociatedPartnerId": "484e548c-f5f3-4528-93a9-c16c6373cb59",
    "Attributes": {
        "ObjectType": "Customer"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="e8cd3-216">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e8cd3-216">REST response</span></span>

<span data-ttu-id="e8cd3-217">Als dit is gelukt, bevat het antwoord een [klant](customer-resources.md#customer) resource voor de nieuwe klant.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-217">If successful, the response contains a [Customer](customer-resources.md#customer) resource for the new customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e8cd3-218">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="e8cd3-218">Response success and error codes</span></span>

<span data-ttu-id="e8cd3-219">Antwoorden worden geleverd met een HTTP-status code die aangeeft of de fout is geslaagd of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-219">Responses come with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e8cd3-220">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-220">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e8cd3-221">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="e8cd3-221">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e8cd3-222">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e8cd3-222">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 1085
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0dd197a8-992c-44ca-aeae-21cd83494dce
MS-RequestId: d628adbe-b7ee-412e-ac55-58f22b4ba2f4
MS-CV: Yy/YaA0gYEmfQyR/.0
MS-ServerId: 030020525
Date: Tue, 06 Jun 2017 23:11:40 GMT

{
    "id": "626099fe-17af-4756-9fd0-6a73b7127859",
    "commerceId": "626099fe-17af-4756-9fd0-6a73b7127859",
    "companyProfile": {
        "tenantId": "626099fe-17af-4756-9fd0-6a73b7127859",
        "domain": "WingtipToys678152504.onmicrosoft.com",
        "companyName": "Wingtip Toys678152504",
        "links": {
            "self": {
                "uri": "/customers/626099fe-17af-4756-9fd0-6a73b7127859/profiles/company",
                "method": "GET",
                "headers": []
            }
        },
        "attributes": {
            "objectType": "CustomerCompanyProfile"
        }
    },
    "billingProfile": {
        "id": "7079246e-7b62-56ef-7cbd-a819514b54b5",
        "email": "Gena@wingtiptoys.com",
        "culture": "en-US",
        "language": "En",
        "companyName": "Wingtip Toys678152504",
        "defaultAddress": {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "One Microsoft Way",
            "postalCode": "98052",
            "firstName": "Gena",
            "lastName": "Soto",
            "phoneNumber": "4255550101"
        },
        "attributes": {
            "etag": "-8799889149591823008",
            "objectType": "CustomerBillingProfile"
        }
    },
    "relationshipToPartner": "reseller",
    "allowDelegatedAccess": true,
    "userCredentials": {
        "userName": "admin",
        "password": "0Krha*Io"
    },
    "associatedPartnerId": "484e548c-f5f3-4528-93a9-c16c6373cb59",
    "attributes": {
        "objectType": "Customer"
    }
}
```