---
title: Een klant maken
description: Ontdek hoe een Cloud Solution Provider (CSP)-partner Partner Center API's kan gebruiken om een nieuwe klant te maken. In dit artikel worden de vereisten beschreven en wat er nog meer gebeurt.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 6232ca77d057f2f5168b73d81ec551669d540246
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973720"
---
# <a name="create-a-customer-using-partner-center-apis"></a><span data-ttu-id="52583-104">Een klant maken met behulp Partner Center API's</span><span class="sxs-lookup"><span data-stu-id="52583-104">Create a customer using Partner Center APIs</span></span>

<span data-ttu-id="52583-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="52583-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="52583-106">In dit artikel wordt uitgelegd hoe u een nieuwe klant maakt.</span><span class="sxs-lookup"><span data-stu-id="52583-106">This article explains how to create a new customer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52583-107">Als u een indirecte provider bent en u een klant wilt maken voor een indirecte reseller, raadpleegt u Een klant [maken voor een indirecte reseller.](create-a-customer-for-an-indirect-reseller.md)</span><span class="sxs-lookup"><span data-stu-id="52583-107">If you are an indirect provider and you want to create a customer for an indirect reseller, please see [Create a customer for an indirect reseller](create-a-customer-for-an-indirect-reseller.md).</span></span>

<span data-ttu-id="52583-108">Wanneer u als CSP-partner (Cloud Solution Provider) een klant maakt, kunt u namens de klant orders plaatsen.</span><span class="sxs-lookup"><span data-stu-id="52583-108">As a cloud solution provider (CSP) partner, when you create a customer you can place orders on behalf of the customer.</span></span> <span data-ttu-id="52583-109">Wanneer u een klant maakt, maakt u ook het volgende:</span><span class="sxs-lookup"><span data-stu-id="52583-109">When you create a customer, you also create:</span></span>

- <span data-ttu-id="52583-110">Een Azure Active Directory (AD)-tenantobject voor de klant.</span><span class="sxs-lookup"><span data-stu-id="52583-110">An Azure Active Directory (AD) tenant object for the customer.</span></span>

- <span data-ttu-id="52583-111">Een relatie tussen de reseller en de klant, die wordt gebruikt voor gedelegeerde beheerdersbevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="52583-111">A relationship between the reseller and customer, used for delegated admin privileges.</span></span>

- <span data-ttu-id="52583-112">Een gebruikersnaam en wachtwoord om u aan te melden als beheerder voor de klant.</span><span class="sxs-lookup"><span data-stu-id="52583-112">A user name and password to sign in as an admin for the customer.</span></span>

<span data-ttu-id="52583-113">Nadat de klant is gemaakt, moet u de klant-id en Azure AD-gegevens opslaan voor toekomstig gebruik met de Partnercentrum-SDK (bijvoorbeeld accountbeheer).</span><span class="sxs-lookup"><span data-stu-id="52583-113">Once the customer is created, be sure to save the customer ID and Azure AD details for future use with the Partner Center SDK (for example, account management).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="52583-114">Vereisten</span><span class="sxs-lookup"><span data-stu-id="52583-114">Prerequisites</span></span>

- <span data-ttu-id="52583-115">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="52583-115">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="52583-116">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="52583-116">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="52583-117">Als u een klant-tenant wilt maken, moet u tijdens het maken een geldig fysiek adres verstrekken.</span><span class="sxs-lookup"><span data-stu-id="52583-117">To create a customer tenant you must provide a valid physical address during the creation process.</span></span> <span data-ttu-id="52583-118">Een adres kan worden gevalideerd door de stappen te volgen die worden beschreven in het [scenario Een adres valideren.](validate-an-address.md)</span><span class="sxs-lookup"><span data-stu-id="52583-118">An address can be validated by following the steps outlined in the [Validate an address](validate-an-address.md) scenario.</span></span> <span data-ttu-id="52583-119">Als u een klant maakt met een ongeldig adres in de sandbox-omgeving, kunt u die tenant van de klant niet verwijderen.</span><span class="sxs-lookup"><span data-stu-id="52583-119">If you create a customer using an invalid address in the sandbox environment, you will not be able to delete that customer tenant.</span></span>

## <a name="c"></a><span data-ttu-id="52583-120">C\#</span><span class="sxs-lookup"><span data-stu-id="52583-120">C\#</span></span>

<span data-ttu-id="52583-121">Een klant toevoegen:</span><span class="sxs-lookup"><span data-stu-id="52583-121">To add a customer:</span></span>

1. <span data-ttu-id="52583-122">Instantieer een nieuw [**klantobject.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer)</span><span class="sxs-lookup"><span data-stu-id="52583-122">Instantiate a new [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object.</span></span> <span data-ttu-id="52583-123">Vul het [**BillingProfile en**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) [**CompanyProfile in.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile)</span><span class="sxs-lookup"><span data-stu-id="52583-123">Be sure to fill in the [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) and [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span></span>

2. <span data-ttu-id="52583-124">Voeg de nieuwe klant toe aan uw [**verzameling IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) door [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) of [**CreateAsync aan te roepen.**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync)</span><span class="sxs-lookup"><span data-stu-id="52583-124">Add the new customer to your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection by calling [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync).</span></span>

### <a name="c-example"></a><span data-ttu-id="52583-125">\#C-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="52583-125">C\# example</span></span>

```csharp
// IAggregatePartner partnerOperations;

var partnerOperations = this.Context.UserPartnerOperations;

var customerToCreate = new Customer()
{
    CompanyProfile = new CustomerCompanyProfile()
    {
        Domain = string.Format(CultureInfo.InvariantCulture,
            "SampleApplication{0}.{1}",
            new Random().Next(),
            this.Context.Configuration.Scenario.CustomerDomainSuffix),
        //// OrganizationRegistrationNumber = "123456" // Please add if in specific country that requires
    },
    BillingProfile = new CustomerBillingProfile()
    {
        Culture = "EN-US",
        Email = "someone@example.com",
        Language = "En",
        CompanyName = "Some Company" + new Random().Next(),
        DefaultAddress = new Address()
        {
            FirstName = "Tania",
            MiddleName = "MiddleName",
            LastName = "Carr",
            AddressLine1 = "One Microsoft Way",
            City = "Redmond",
            State = "WA",
            Country = "US",
            PostalCode = "98052",
            PhoneNumber = ""
        }
    }
};

var newCustomer = partnerOperations.Customers.Create(customerToCreate);
```

<span data-ttu-id="52583-126">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="52583-126">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="52583-127">**Project:** Partnercentrum-SDK Klasse **Samples:** CreateCustomer.cs</span><span class="sxs-lookup"><span data-stu-id="52583-127">**Project**: Partner Center SDK Samples **Class**: CreateCustomer.cs</span></span>

## <a name="java"></a><span data-ttu-id="52583-128">Java</span><span class="sxs-lookup"><span data-stu-id="52583-128">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="52583-129">Een nieuwe klant maken:</span><span class="sxs-lookup"><span data-stu-id="52583-129">To create a new customer:</span></span>

1. <span data-ttu-id="52583-130">Maak een nieuw exemplaar van **het CustomerBillingProfile-** en **de CustomerCompanyProfile-objecten.**</span><span class="sxs-lookup"><span data-stu-id="52583-130">Create a new instance of the **CustomerBillingProfile** and the **CustomerCompanyProfile** objects.</span></span> <span data-ttu-id="52583-131">Vul de vereiste velden in.</span><span class="sxs-lookup"><span data-stu-id="52583-131">Be sure to populate the required fields.</span></span>

2. <span data-ttu-id="52583-132">Maak de klant door de functie **IAggregatePartner.getCustomers().create aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="52583-132">Create the customer by calling the **IAggregatePartner.getCustomers().create** function.</span></span>

### <a name="java-example"></a><span data-ttu-id="52583-133">Java-voorbeeld</span><span class="sxs-lookup"><span data-stu-id="52583-133">Java example</span></span>

```java
// IAggregatePartner partnerOperations;

Address address = new Address();

address.setFirstName( "Gena" );
address.setLastName( "Soto" );
address.setAddressLine1( "One Microsoft Way" );
address.setCity( "Redmond" );
address.setState( "WA" );
address.setCountry( "US" );
address.setPostalCode( "98052" );
address.setPhoneNumber( "4255550101" );

CustomerBillingProfile billingProfile = new CustomerBillingProfile();

billingProfile.setCulture( "en-US" );
billingProfile.setEmail( "gena@wingtiptoys.com" );
billingProfile.setLanguage( "en" );
billingProfile.setCompanyName( "Wingtip Toys" + new Random().nextInt() );
billingProfile.setDefaultAddress( address );

CustomerCompanyProfile companyProfile = new CustomerCompanyProfile();

companyProfile.setDomain( "WingtipToys" + Math.abs( new Random().nextInt() ) + ".onmicrosoft.com" );

Customer customerToCreate = new Customer();

customerToCreate.setBillingProfile( billingProfile );
customerToCreate.setCompanyProfile( companyProfile );

Customer newCustomer = partnerOperations.getCustomers().create( customerToCreate );
```

## <a name="powershell"></a><span data-ttu-id="52583-134">PowerShell</span><span class="sxs-lookup"><span data-stu-id="52583-134">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="52583-135">Als u een klant wilt maken, voert u [**de opdracht New-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md) uit.</span><span class="sxs-lookup"><span data-stu-id="52583-135">To create a customer, execute the [**New-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md) command.</span></span>

```powershell
New-PartnerCustomer -BillingAddressLine1 '1 Microsoft Way' -BillingAddressCity 'Redmond' -BillingAddressCountry 'US' -BillingAddressPostalCode '98052' -BillingAddressState 'WA' -ContactEmail 'jdoe@customer.com' -ContactFirstName 'Jane' -ContactLastName 'Doe' -Culture 'en-US' -Domain 'newcustomer.onmicrosoft.com' -Language 'en' -Name 'New Customer'
```

## <a name="rest-request"></a><span data-ttu-id="52583-136">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="52583-136">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="52583-137">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="52583-137">Request syntax</span></span>

| <span data-ttu-id="52583-138">Methode</span><span class="sxs-lookup"><span data-stu-id="52583-138">Method</span></span>   | <span data-ttu-id="52583-139">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="52583-139">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="52583-140">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="52583-140">**POST**</span></span> | <span data-ttu-id="52583-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="52583-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="52583-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="52583-142">Request headers</span></span>

- <span data-ttu-id="52583-143">Deze API is idempotent (deze levert geen ander resultaat op als u deze meerdere keren aanroept).</span><span class="sxs-lookup"><span data-stu-id="52583-143">This API is idempotent (it will not yield a different result if you call it multiple times).</span></span>

- <span data-ttu-id="52583-144">Een aanvraag-id en correlatie-id zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="52583-144">A request ID and correlation ID are required.</span></span>

- <span data-ttu-id="52583-145">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="52583-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="52583-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="52583-146">Request body</span></span>

<span data-ttu-id="52583-147">In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="52583-147">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="52583-148">Naam</span><span class="sxs-lookup"><span data-stu-id="52583-148">Name</span></span>                              | <span data-ttu-id="52583-149">Type</span><span class="sxs-lookup"><span data-stu-id="52583-149">Type</span></span>   | <span data-ttu-id="52583-150">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="52583-150">Description</span></span>                                 |
|-----------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="52583-151">BillingProfile</span><span class="sxs-lookup"><span data-stu-id="52583-151">BillingProfile</span></span>](#billing-profile) | <span data-ttu-id="52583-152">object</span><span class="sxs-lookup"><span data-stu-id="52583-152">object</span></span> | <span data-ttu-id="52583-153">De gegevens van het factureringsprofiel van de klant.</span><span class="sxs-lookup"><span data-stu-id="52583-153">The customer's billing profile information.</span></span> |
| [<span data-ttu-id="52583-154">CompanyProfile</span><span class="sxs-lookup"><span data-stu-id="52583-154">CompanyProfile</span></span>](#company-profile) | <span data-ttu-id="52583-155">object</span><span class="sxs-lookup"><span data-stu-id="52583-155">object</span></span> | <span data-ttu-id="52583-156">De bedrijfsprofielgegevens van de klant.</span><span class="sxs-lookup"><span data-stu-id="52583-156">The customer's company profile information.</span></span> |

#### <a name="billing-profile"></a><span data-ttu-id="52583-157">Factureringsprofiel</span><span class="sxs-lookup"><span data-stu-id="52583-157">Billing profile</span></span>

<span data-ttu-id="52583-158">In deze tabel worden de minimaal vereiste velden van de [CustomerBillingProfile-resource](customer-resources.md#customerbillingprofile) beschreven die nodig zijn om een nieuwe klant te maken.</span><span class="sxs-lookup"><span data-stu-id="52583-158">This table describes the minimum required fields from the [CustomerBillingProfile](customer-resources.md#customerbillingprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="52583-159">Naam</span><span class="sxs-lookup"><span data-stu-id="52583-159">Name</span></span>             | <span data-ttu-id="52583-160">Type</span><span class="sxs-lookup"><span data-stu-id="52583-160">Type</span></span>                                     | <span data-ttu-id="52583-161">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="52583-161">Description</span></span>                                                                                                                                                                                                     |
|------------------|------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="52583-162">e-mail</span><span class="sxs-lookup"><span data-stu-id="52583-162">email</span></span>            | <span data-ttu-id="52583-163">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="52583-163">string</span></span>                                   | <span data-ttu-id="52583-164">Het e-mailadres van de klant.</span><span class="sxs-lookup"><span data-stu-id="52583-164">The customer's email address.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="52583-165">Cultuur</span><span class="sxs-lookup"><span data-stu-id="52583-165">culture</span></span>          | <span data-ttu-id="52583-166">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="52583-166">string</span></span>                                   | <span data-ttu-id="52583-167">Hun voorkeurscultuur voor communicatie en valuta, zoals 'en-US'.</span><span class="sxs-lookup"><span data-stu-id="52583-167">Their preferred culture for communication and currency, such as "en-US".</span></span> <span data-ttu-id="52583-168">Zie [Partner Center ondersteunde talen en talen voor](partner-center-supported-languages-and-locales.md) de ondersteunde culturen.</span><span class="sxs-lookup"><span data-stu-id="52583-168">See [Partner Center supported languages and locales](partner-center-supported-languages-and-locales.md) for the supported cultures.</span></span> |
| <span data-ttu-id="52583-169">language</span><span class="sxs-lookup"><span data-stu-id="52583-169">language</span></span>         | <span data-ttu-id="52583-170">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="52583-170">string</span></span>                                   | <span data-ttu-id="52583-171">De standaardtaal.</span><span class="sxs-lookup"><span data-stu-id="52583-171">The default language.</span></span> <span data-ttu-id="52583-172">Er worden twee tekentaalcodes `en` (bijvoorbeeld of `fr` ) ondersteund.</span><span class="sxs-lookup"><span data-stu-id="52583-172">Two character language codes (for example `en` or `fr`) are supported.</span></span>                                                                                                                                |
| <span data-ttu-id="52583-173">\_bedrijfsnaam</span><span class="sxs-lookup"><span data-stu-id="52583-173">company\_name</span></span>    | <span data-ttu-id="52583-174">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="52583-174">string</span></span>                                   | <span data-ttu-id="52583-175">De geregistreerde bedrijfsnaam/organisatienaam.</span><span class="sxs-lookup"><span data-stu-id="52583-175">The registered company/organization name.</span></span>                                                                                                                                                                       |
| <span data-ttu-id="52583-176">\_standaardadres</span><span class="sxs-lookup"><span data-stu-id="52583-176">default\_address</span></span> | [<span data-ttu-id="52583-177">Adres</span><span class="sxs-lookup"><span data-stu-id="52583-177">Address</span></span>](utility-resources.md#address) | <span data-ttu-id="52583-178">Het geregistreerde adres van het bedrijf/de organisatie van de klant.</span><span class="sxs-lookup"><span data-stu-id="52583-178">The registered address of the customer's company/organization.</span></span> <span data-ttu-id="52583-179">Zie de [adresresource](utility-resources.md#address) voor informatie over lengtebeperkingen.</span><span class="sxs-lookup"><span data-stu-id="52583-179">See the [Address](utility-resources.md#address) resource for information on any length limitations.</span></span>                                             |

#### <a name="company-profile"></a><span data-ttu-id="52583-180">Bedrijfsprofiel</span><span class="sxs-lookup"><span data-stu-id="52583-180">Company profile</span></span>

<span data-ttu-id="52583-181">In deze tabel worden de minimaal vereiste velden van de resource [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) beschreven die nodig zijn om een nieuwe klant te maken.</span><span class="sxs-lookup"><span data-stu-id="52583-181">This table describes the minimum required fields from the [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="52583-182">Naam</span><span class="sxs-lookup"><span data-stu-id="52583-182">Name</span></span>   | <span data-ttu-id="52583-183">Type</span><span class="sxs-lookup"><span data-stu-id="52583-183">Type</span></span>   | <span data-ttu-id="52583-184">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="52583-184">Description</span></span>                                                  |
|--------|--------|--------------------------------------------------------------|
| <span data-ttu-id="52583-185">domein</span><span class="sxs-lookup"><span data-stu-id="52583-185">domain</span></span> | <span data-ttu-id="52583-186">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="52583-186">string</span></span> | <span data-ttu-id="52583-187">De domeinnaam van de klant, zoals contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="52583-187">The customer's domain name, such as contoso.onmicrosoft.com.</span></span> |
|<span data-ttu-id="52583-188">organizationRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="52583-188">organizationRegistrationNumber</span></span>|<span data-ttu-id="52583-189">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="52583-189">String</span></span>|<span data-ttu-id="52583-190">Het registratienummer van de organisatie van de klant (ook wel INN-nummer genoemd in bepaalde landen).</span><span class="sxs-lookup"><span data-stu-id="52583-190">The customer’s organization registration number (also referred to as INN number in certain countries).</span></span> <span data-ttu-id="52583-191">Alleen vereist voor het bedrijf/de organisatie van de klant die zich in de volgende landen bevindt: 1000(AM), Zowel(AM), Elkaar(AZ), Gaata(NU), Als(KZ), Kyrgyzstan(KG), Espa(MD), Rusland(RU), Tstanikrov(TJ), Uzbekjik(UZ), UA (UA), Brazil(BR), India, Zuid-Afrika, Spanje, Verenigde Arabische Republieken, Hongkong, Republiek, Vietnam, Vietnam, Vietnam, Zuid-Afrika en Eu na.</span><span class="sxs-lookup"><span data-stu-id="52583-191">Only required for customer’s company/organization located in the following countries: Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA), Brazil(BR), India, South Africa, Poland, United Arab Emirates, Saudi Arabia, Turkey, Thailand, Vietnam, Myanmar, Iraq, South Sudan, and Venezuela.</span></span> <span data-ttu-id="52583-192">Voor het bedrijf/de organisatie van de klant in andere landen is dit een optioneel veld.</span><span class="sxs-lookup"><span data-stu-id="52583-192">For customer’s company/organization located in other countries, this is an optional field.</span></span>|

### <a name="request-example"></a><span data-ttu-id="52583-193">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="52583-193">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 789
Expect: 100-continue
Connection: Keep-Alive

{
    "CompanyProfile": {
        "Domain": "xyz.ccsctp.net",
    },
    "BillingProfile": {
        "Culture": "EN-US",
        "Email": "test@outlook.com",
        "Language": "en",
        "CompanyName": "test company",
        "DefaultAddress": {
            "FirstName": "Test",
            "LastName": "Test",
            "AddressLine1": "One Microsoft Way",
            "City": "Redmond",
            "State": "WA",
            "PostalCode": "98052",
            "Country": "US",
        }
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="52583-194">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="52583-194">REST response</span></span>

<span data-ttu-id="52583-195">Als dit lukt, retourneert deze API een [klantresource](customer-resources.md#customer) voor de nieuwe klant.</span><span class="sxs-lookup"><span data-stu-id="52583-195">If successful, this API returns a [Customer](customer-resources.md#customer) resource for the new customer.</span></span> <span data-ttu-id="52583-196">Sla de klant-id en Azure AD-gegevens op voor toekomstig gebruik met de Partnercentrum-SDK.</span><span class="sxs-lookup"><span data-stu-id="52583-196">Save the customer ID and Azure AD details for future use with the Partner Center SDK.</span></span> <span data-ttu-id="52583-197">U hebt deze bijvoorbeeld nodig voor gebruik met accountbeheer.</span><span class="sxs-lookup"><span data-stu-id="52583-197">You will need them for use with account management, for example.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="52583-198">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="52583-198">Response success and error codes</span></span>

<span data-ttu-id="52583-199">Antwoorden worden verstrekt met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="52583-199">Responses come with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="52583-200">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="52583-200">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="52583-201">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="52583-201">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="52583-202">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="52583-202">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 834
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CV: ObwhuhD2tUKJoM+Z.0
MS-ServerId: 202010223
Date: Tue, 14 Feb 2017 20:06:02 GMT

{
    "id": "dfd8cc0a-c592-468c-8461-869a38d24738",
    "commerceId": "0a4ce58a-6f96-4273-8035-d9c7d31b9ba4",
    "companyProfile": {
        "tenantId": "dfd8cc0a-c592-468c-8461-869a38d24738",
        "domain": "xyz.ccsctp.net",
        "attributes": {
            "objectType": "CustomerCompanyProfile"
        }
    },
    "billingProfile": {
        "id": "d17c0275-da92-5c33-9032-782ef1d0b69b",
        "email": "test@outlook.com",
        "culture": "en-US",
        "language": "en",
        "companyName": "test company",
        "defaultAddress": {
            "country": "US",
            "city": "Redmond",
            "state": "WA",
            "addressLine1": "One Microsoft Way",
            "postalCode": "98052",
            "firstName": "Test",
            "lastName": "Test",
            "phoneNumber": ""
        },
        "attributes": {
            "etag": "5920358838484612121",
            "objectType": "CustomerBillingProfile"
        }
    },
    "relationshipToPartner": "none",
    "userCredentials": {
        "userName": "admin",
        "password": "=;;n.=s9Z"
    },
    "attributes": {
        "objectType": "Customer"
    }
}
```
