---
title: Een klant voor een indirecte reseller maken
description: Meer informatie over hoe een indirecte provider Partner Center API's kan gebruiken om een klant te maken voor een indirecte reseller.
ms.date: 04/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 9a6218aeb61f3775c89d34b4d57a17741e3a1e93
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973737"
---
# <a name="create-a-customer-for-an-indirect-reseller-using-partner-center-apis"></a><span data-ttu-id="e784f-103">Een klant maken voor een indirecte reseller met behulp van Partner Center API's</span><span class="sxs-lookup"><span data-stu-id="e784f-103">Create a customer for an indirect reseller using Partner Center APIs</span></span>

<span data-ttu-id="e784f-104">Een indirecte provider kan een klant maken voor een indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="e784f-104">An indirect provider can create a customer for an indirect reseller.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e784f-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="e784f-105">Prerequisites</span></span>

- <span data-ttu-id="e784f-106">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="e784f-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="e784f-107">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="e784f-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="e784f-108">De tenant-id van de indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="e784f-108">The tenant identifier of the indirect reseller.</span></span>

- <span data-ttu-id="e784f-109">De indirecte reseller moet een partnerschap hebben met de indirecte provider.</span><span class="sxs-lookup"><span data-stu-id="e784f-109">The indirect reseller must have a partnership with the indirect provider.</span></span>

## <a name="c"></a><span data-ttu-id="e784f-110">C\#</span><span class="sxs-lookup"><span data-stu-id="e784f-110">C\#</span></span>

<span data-ttu-id="e784f-111">Een nieuwe klant toevoegen voor een indirecte reseller:</span><span class="sxs-lookup"><span data-stu-id="e784f-111">To add a new customer for an indirect reseller:</span></span>

1. <span data-ttu-id="e784f-112">Instantieer een nieuw [**Customer-object**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) en instantieer en vul het [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) en [**CompanyProfile in.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile)</span><span class="sxs-lookup"><span data-stu-id="e784f-112">Instantiate a new [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object and then instantiate and populate the [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) and [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span></span> <span data-ttu-id="e784f-113">Zorg ervoor dat u de indirecte reseller-id toewijst aan de [**eigenschap AssociatedPartnerID.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid)</span><span class="sxs-lookup"><span data-stu-id="e784f-113">Be sure to assign the indirect reseller ID to the [**AssociatedPartnerID**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid) property.</span></span>

2. <span data-ttu-id="e784f-114">Gebruik de [**eigenschap IAggregatePartner.Customers om**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) een interface op te halen voor bewerkingen voor het verzamelen van klanten.</span><span class="sxs-lookup"><span data-stu-id="e784f-114">Use the [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) property to get an interface to customer collection operations.</span></span>

3. <span data-ttu-id="e784f-115">Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) om de klant te maken.</span><span class="sxs-lookup"><span data-stu-id="e784f-115">Call the [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) method to create the customer.</span></span>

### <a name="c-example"></a><span data-ttu-id="e784f-116">\#C-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="e784f-116">C\# example</span></span>

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

<span data-ttu-id="e784f-117">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="e784f-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="e784f-118">**Project**: Partnercentrum-SDK Samples **Class**: CreateCustomerforIndirectReseller.cs</span><span class="sxs-lookup"><span data-stu-id="e784f-118">**Project**: Partner Center SDK Samples **Class**: CreateCustomerforIndirectReseller.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="e784f-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="e784f-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="e784f-120">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="e784f-120">Request syntax</span></span>

| <span data-ttu-id="e784f-121">Methode</span><span class="sxs-lookup"><span data-stu-id="e784f-121">Method</span></span>   | <span data-ttu-id="e784f-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="e784f-122">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="e784f-123">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="e784f-123">**POST**</span></span> | <span data-ttu-id="e784f-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="e784f-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="e784f-125">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="e784f-125">Request headers</span></span>

<span data-ttu-id="e784f-126">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="e784f-126">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="e784f-127">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="e784f-127">Request body</span></span>

<span data-ttu-id="e784f-128">In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="e784f-128">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="e784f-129">Naam</span><span class="sxs-lookup"><span data-stu-id="e784f-129">Name</span></span>                                          | <span data-ttu-id="e784f-130">Type</span><span class="sxs-lookup"><span data-stu-id="e784f-130">Type</span></span>   | <span data-ttu-id="e784f-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="e784f-131">Required</span></span> | <span data-ttu-id="e784f-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e784f-132">Description</span></span>                                                                                                                                                                                                                                                                                                                                           |
|-----------------------------------------------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [<span data-ttu-id="e784f-133">BillingProfile</span><span class="sxs-lookup"><span data-stu-id="e784f-133">BillingProfile</span></span>](#billing-profile)             | <span data-ttu-id="e784f-134">object</span><span class="sxs-lookup"><span data-stu-id="e784f-134">object</span></span> | <span data-ttu-id="e784f-135">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-135">Yes</span></span>      | <span data-ttu-id="e784f-136">De factureringsprofielgegevens van de klant.</span><span class="sxs-lookup"><span data-stu-id="e784f-136">The customer's billing profile information.</span></span>                                                                                                                                                                                                                                                                                                           |
| [<span data-ttu-id="e784f-137">CompanyProfile</span><span class="sxs-lookup"><span data-stu-id="e784f-137">CompanyProfile</span></span>](#company-profile)             | <span data-ttu-id="e784f-138">object</span><span class="sxs-lookup"><span data-stu-id="e784f-138">object</span></span> | <span data-ttu-id="e784f-139">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-139">Yes</span></span>      | <span data-ttu-id="e784f-140">De bedrijfsprofielgegevens van de klant.</span><span class="sxs-lookup"><span data-stu-id="e784f-140">The customer's company profile information.</span></span>                                                               
| [<span data-ttu-id="e784f-141">AssociatedPartnerId</span><span class="sxs-lookup"><span data-stu-id="e784f-141">AssociatedPartnerId</span></span>](customer-resources.md#customer) | <span data-ttu-id="e784f-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e784f-142">string</span></span> | <span data-ttu-id="e784f-143">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-143">Yes</span></span>      | <span data-ttu-id="e784f-144">De indirecte reseller-id.</span><span class="sxs-lookup"><span data-stu-id="e784f-144">The indirect reseller ID.</span></span> <span data-ttu-id="e784f-145">De indirecte reseller, zoals aangegeven door de id die hier is opgegeven, moet een partnerschap hebben met de indirecte provider, anders mislukt de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="e784f-145">The indirect reseller as indicated by the ID supplied here must have a partnership with the indirect provider or the request will fail.</span></span> <span data-ttu-id="e784f-146">Houd er ook rekening mee dat als de associatedPartnerId-waarde niet wordt opgegeven, de klant wordt gemaakt als een directe klant van de indirecte provider in plaats van de indirecte reseller.</span><span class="sxs-lookup"><span data-stu-id="e784f-146">Also note that if the AssociatedPartnerId value isn't supplied, the customer is created as a direct customer of the indirect provider rather than the indirect reseller.</span></span> |
|<span data-ttu-id="e784f-147">Domain</span><span class="sxs-lookup"><span data-stu-id="e784f-147">Domain</span></span>| <span data-ttu-id="e784f-148">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e784f-148">String</span></span>| <span data-ttu-id="e784f-149">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-149">Yes</span></span>|<span data-ttu-id="e784f-150">De domeinnaam van de klant, zoals contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="e784f-150">The customer's domain name, such as contoso.onmicrosoft.com.</span></span>|
|<span data-ttu-id="e784f-151">organizationRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="e784f-151">organizationRegistrationNumber</span></span>|    <span data-ttu-id="e784f-152">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e784f-152">string</span></span>|<span data-ttu-id="e784f-153">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-153">Yes</span></span>|     <span data-ttu-id="e784f-154">Het registratienummer van de organisatie van de klant (in bepaalde landen ook wel HETN-nummer genoemd).</span><span class="sxs-lookup"><span data-stu-id="e784f-154">The customer’s organization registration number (also referred to as INN number in certain countries).</span></span> <span data-ttu-id="e784f-155">Alleen vereist voor het bedrijf/de organisatie van de klant die zich in de volgende landen bevindt: 100000000000000000005555555(MD), China(AM), Tzard (TJ), Uzbekje (UZ), UZ ( UA), India, Brazilië, Zuid-Afrika, United United Afs, United South, South South South, SouthEse,</span><span class="sxs-lookup"><span data-stu-id="e784f-155">Only required for customer’s company/organization located in the following countries: Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA), India, Brazil, South Africa, Poland, United Arab Emirates, Saudi Arabia, Turkey, Thailand, Vietnam, Myanmar, Iraq, South Sudan, and Venezuela.</span></span> <span data-ttu-id="e784f-156">Voor het bedrijf/de organisatie van de klant in andere landen is dit een optioneel veld.</span><span class="sxs-lookup"><span data-stu-id="e784f-156">For customer’s company/organization located in other countries this is an optional field.</span></span>|



#### <a name="billing-profile"></a><span data-ttu-id="e784f-157">Factureringsprofiel</span><span class="sxs-lookup"><span data-stu-id="e784f-157">Billing profile</span></span>

<span data-ttu-id="e784f-158">In deze tabel worden de minimaal vereiste velden van de [Resource CustomerBillingProfile](customer-resources.md#customerbillingprofile) beschreven die nodig zijn om een nieuwe klant te maken.</span><span class="sxs-lookup"><span data-stu-id="e784f-158">This table describes the minimum required fields from the [CustomerBillingProfile](customer-resources.md#customerbillingprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="e784f-159">Naam</span><span class="sxs-lookup"><span data-stu-id="e784f-159">Name</span></span>             | <span data-ttu-id="e784f-160">Type</span><span class="sxs-lookup"><span data-stu-id="e784f-160">Type</span></span>                                     | <span data-ttu-id="e784f-161">Vereist</span><span class="sxs-lookup"><span data-stu-id="e784f-161">Required</span></span> | <span data-ttu-id="e784f-162">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e784f-162">Description</span></span>                                                                                                                                                                                                     |
|------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="e784f-163">e-mail</span><span class="sxs-lookup"><span data-stu-id="e784f-163">email</span></span>            | <span data-ttu-id="e784f-164">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e784f-164">string</span></span>                                   | <span data-ttu-id="e784f-165">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-165">Yes</span></span>      | <span data-ttu-id="e784f-166">Het e-mailadres van de klant.</span><span class="sxs-lookup"><span data-stu-id="e784f-166">The customer's email address.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="e784f-167">Cultuur</span><span class="sxs-lookup"><span data-stu-id="e784f-167">culture</span></span>          | <span data-ttu-id="e784f-168">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e784f-168">string</span></span>                                   | <span data-ttu-id="e784f-169">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-169">Yes</span></span>      | <span data-ttu-id="e784f-170">Hun voorkeurscultuur voor communicatie en valuta, zoals 'en-US'.</span><span class="sxs-lookup"><span data-stu-id="e784f-170">Their preferred culture for communication and currency, such as "en-US".</span></span> <span data-ttu-id="e784f-171">Zie [Partner Center ondersteunde talen en landen voor](partner-center-supported-languages-and-locales.md) de ondersteunde culturen.</span><span class="sxs-lookup"><span data-stu-id="e784f-171">See [Partner Center supported languages and locales](partner-center-supported-languages-and-locales.md) for the supported cultures.</span></span> |
| <span data-ttu-id="e784f-172">language</span><span class="sxs-lookup"><span data-stu-id="e784f-172">language</span></span>         | <span data-ttu-id="e784f-173">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e784f-173">string</span></span>                                   | <span data-ttu-id="e784f-174">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-174">Yes</span></span>      | <span data-ttu-id="e784f-175">De standaardtaal.</span><span class="sxs-lookup"><span data-stu-id="e784f-175">The default language.</span></span> <span data-ttu-id="e784f-176">Er worden twee tekentaalcodes `en` (bijvoorbeeld of `fr` ) ondersteund.</span><span class="sxs-lookup"><span data-stu-id="e784f-176">Two character language codes (for example `en` or `fr`) are supported.</span></span>                                                                                                                                |
| <span data-ttu-id="e784f-177">\_bedrijfsnaam</span><span class="sxs-lookup"><span data-stu-id="e784f-177">company\_name</span></span>    | <span data-ttu-id="e784f-178">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e784f-178">string</span></span>                                   | <span data-ttu-id="e784f-179">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-179">Yes</span></span>      | <span data-ttu-id="e784f-180">De geregistreerde bedrijfsnaam/organisatienaam.</span><span class="sxs-lookup"><span data-stu-id="e784f-180">The registered company/organization name.</span></span>                                                                                                                                                                       |
| <span data-ttu-id="e784f-181">\_standaardadres</span><span class="sxs-lookup"><span data-stu-id="e784f-181">default\_address</span></span> | [<span data-ttu-id="e784f-182">Adres</span><span class="sxs-lookup"><span data-stu-id="e784f-182">Address</span></span>](utility-resources.md#address) | <span data-ttu-id="e784f-183">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-183">Yes</span></span>      | <span data-ttu-id="e784f-184">Het geregistreerde adres van het bedrijf/de organisatie van de klant.</span><span class="sxs-lookup"><span data-stu-id="e784f-184">The registered address of the customer's company/organization.</span></span> <span data-ttu-id="e784f-185">Zie de [adresresource](utility-resources.md#address) voor informatie over lengtebeperkingen.</span><span class="sxs-lookup"><span data-stu-id="e784f-185">See the [Address](utility-resources.md#address) resource for information on any length limitations.</span></span>                                             |

#### <a name="company-profile"></a><span data-ttu-id="e784f-186">Bedrijfsprofiel</span><span class="sxs-lookup"><span data-stu-id="e784f-186">Company profile</span></span>

<span data-ttu-id="e784f-187">In deze tabel worden de minimaal vereiste velden van de resource [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) beschreven die nodig zijn om een nieuwe klant te maken.</span><span class="sxs-lookup"><span data-stu-id="e784f-187">This table describes the minimum required fields from the [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="e784f-188">Naam</span><span class="sxs-lookup"><span data-stu-id="e784f-188">Name</span></span>   | <span data-ttu-id="e784f-189">Type</span><span class="sxs-lookup"><span data-stu-id="e784f-189">Type</span></span>   | <span data-ttu-id="e784f-190">Vereist</span><span class="sxs-lookup"><span data-stu-id="e784f-190">Required</span></span> | <span data-ttu-id="e784f-191">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e784f-191">Description</span></span>                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| <span data-ttu-id="e784f-192">domein</span><span class="sxs-lookup"><span data-stu-id="e784f-192">domain</span></span> | <span data-ttu-id="e784f-193">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e784f-193">string</span></span> | <span data-ttu-id="e784f-194">Ja</span><span class="sxs-lookup"><span data-stu-id="e784f-194">Yes</span></span>     | <span data-ttu-id="e784f-195">De domeinnaam van de klant, zoals contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="e784f-195">The customer's domain name, such as contoso.onmicrosoft.com.</span></span> |
| <span data-ttu-id="e784f-196">organizationRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="e784f-196">organizationRegistrationNumber</span></span> | <span data-ttu-id="e784f-197">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="e784f-197">string</span></span> | <span data-ttu-id="e784f-198">Afhankelijk van de voorwaarde</span><span class="sxs-lookup"><span data-stu-id="e784f-198">Depends on condition</span></span> | <span data-ttu-id="e784f-199">Het registratienummer van de organisatie van de klant (in bepaalde landen ook wel het INN-nummer genoemd).</span><span class="sxs-lookup"><span data-stu-id="e784f-199">The customer’s organization registration number (also referred to as the INN number in certain countries).</span></span> <br/><br/><span data-ttu-id="e784f-200">Het voltooien van dit veld is alleen vereist als het bedrijf/de organisatie van een klant zich in de volgende landen bevindt:</span><span class="sxs-lookup"><span data-stu-id="e784f-200">Completing this field is required only if a customer’s company/organization is located in the following countries:</span></span> <br/><br/><span data-ttu-id="e784f-201">- Uiting (AM)</span><span class="sxs-lookup"><span data-stu-id="e784f-201">- Armenia (AM)</span></span> <br/><span data-ttu-id="e784f-202">- Tussenseen (AZ)</span><span class="sxs-lookup"><span data-stu-id="e784f-202">- Azerbaijan (AZ)</span></span><br/><span data-ttu-id="e784f-203">- None (BY)</span><span class="sxs-lookup"><span data-stu-id="e784f-203">- Belarus (BY)</span></span><br/><span data-ttu-id="e784f-204">- Doornige (HU)</span><span class="sxs-lookup"><span data-stu-id="e784f-204">- Hungary (HU)</span></span><br/><span data-ttu-id="e784f-205">- Tussenseen (KZ)</span><span class="sxs-lookup"><span data-stu-id="e784f-205">- Kazakhstan (KZ)</span></span><br/><span data-ttu-id="e784f-206">- Kyrgyzstan (KG)</span><span class="sxs-lookup"><span data-stu-id="e784f-206">- Kyrgyzstan (KG)</span></span><br/><span data-ttu-id="e784f-207">- Ligt (MD)</span><span class="sxs-lookup"><span data-stu-id="e784f-207">- Moldova (MD)</span></span><br/><span data-ttu-id="e784f-208">- Rusland (RU)</span><span class="sxs-lookup"><span data-stu-id="e784f-208">- Russia (RU)</span></span><br/><span data-ttu-id="e784f-209">- Tjikjikjik (TJ)</span><span class="sxs-lookup"><span data-stu-id="e784f-209">- Tajikistan (TJ)</span></span><br/><span data-ttu-id="e784f-210">- Uzbekjik (UZ)</span><span class="sxs-lookup"><span data-stu-id="e784f-210">- Uzbekistan (UZ)</span></span><br/><span data-ttu-id="e784f-211">- Uiting (UA)</span><span class="sxs-lookup"><span data-stu-id="e784f-211">- Ukraine (UA)</span></span><br/><span data-ttu-id="e784f-212">- India</span><span class="sxs-lookup"><span data-stu-id="e784f-212">- India</span></span> <br/><span data-ttu-id="e784f-213">- Brazilië</span><span class="sxs-lookup"><span data-stu-id="e784f-213">- Brazil</span></span> <br/><span data-ttu-id="e784f-214">- Zuid-Afrika</span><span class="sxs-lookup"><span data-stu-id="e784f-214">- South Africa</span></span> <br/><span data-ttu-id="e784f-215">- Niet-gedys</span><span class="sxs-lookup"><span data-stu-id="e784f-215">- Poland</span></span> <br/><span data-ttu-id="e784f-216">- Verenigde Arabische Republieken</span><span class="sxs-lookup"><span data-stu-id="e784f-216">- United Arab Emirates</span></span> <br/><span data-ttu-id="e784f-217">- Hongkong</span><span class="sxs-lookup"><span data-stu-id="e784f-217">- Saudi Arabia</span></span> <br/><span data-ttu-id="e784f-218">- Uitsporing</span><span class="sxs-lookup"><span data-stu-id="e784f-218">- Turkey</span></span> <br/><span data-ttu-id="e784f-219">-</span><span class="sxs-lookup"><span data-stu-id="e784f-219">- Thailand</span></span> <br/><span data-ttu-id="e784f-220">- Vietnam</span><span class="sxs-lookup"><span data-stu-id="e784f-220">- Vietnam</span></span> <br/><span data-ttu-id="e784f-221">-</span><span class="sxs-lookup"><span data-stu-id="e784f-221">- Myanmar</span></span> <br/><span data-ttu-id="e784f-222">- Uithalen</span><span class="sxs-lookup"><span data-stu-id="e784f-222">- Iraq</span></span> <br/><span data-ttu-id="e784f-223">- Zuid-Korea</span><span class="sxs-lookup"><span data-stu-id="e784f-223">- South Sudan</span></span> <br/><span data-ttu-id="e784f-224">-</span><span class="sxs-lookup"><span data-stu-id="e784f-224">- Venezuela</span></span><br/> <br/><span data-ttu-id="e784f-225">Voor het bedrijf/de organisatie van de klant in andere landen is dit een optioneel veld.</span><span class="sxs-lookup"><span data-stu-id="e784f-225">For customer’s company/organization located in other countries, this is an optional field.</span></span>  |

### <a name="request-example"></a><span data-ttu-id="e784f-226">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="e784f-226">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="e784f-227">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="e784f-227">REST response</span></span>

<span data-ttu-id="e784f-228">Als dit lukt, bevat het antwoord een [klantresource](customer-resources.md#customer) voor de nieuwe klant.</span><span class="sxs-lookup"><span data-stu-id="e784f-228">If successful, the response contains a [Customer](customer-resources.md#customer) resource for the new customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="e784f-229">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="e784f-229">Response success and error codes</span></span>

<span data-ttu-id="e784f-230">Antwoorden worden verstrekt met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="e784f-230">Responses come with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="e784f-231">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="e784f-231">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="e784f-232">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="e784f-232">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="e784f-233">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="e784f-233">Response example</span></span>

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