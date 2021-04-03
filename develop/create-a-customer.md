---
title: Een klant maken
description: Meer informatie over hoe een Cloud Solution Provider (CSP)-partner Partner Center-Api's kan gebruiken om een nieuwe klant te maken. In dit artikel worden vereisten beschreven en wat er nog meer gebeurt.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: bc8e9d38353511e747ba4da99b11be40d08781e3
ms.sourcegitcommit: faea78fe3264cbafc2b02c04d98d5ce30e992124
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/03/2021
ms.locfileid: "106274594"
---
# <a name="create-a-customer-using-partner-center-apis"></a><span data-ttu-id="83faa-104">Een klant maken met partner Center-Api's</span><span class="sxs-lookup"><span data-stu-id="83faa-104">Create a customer using Partner Center APIs</span></span>

<span data-ttu-id="83faa-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="83faa-105">**Applies to:**</span></span>

- <span data-ttu-id="83faa-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="83faa-106">Partner Center</span></span>
- <span data-ttu-id="83faa-107">Partnercentrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="83faa-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="83faa-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="83faa-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="83faa-109">In dit artikel wordt uitgelegd hoe u een nieuwe klant maakt.</span><span class="sxs-lookup"><span data-stu-id="83faa-109">This article explains how to create a new customer.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="83faa-110">Als u een indirecte provider bent en u een klant voor een indirecte wederverkoper wilt maken, raadpleegt u [een klant maken voor een indirecte wederverkoper](create-a-customer-for-an-indirect-reseller.md).</span><span class="sxs-lookup"><span data-stu-id="83faa-110">If you are an indirect provider and you want to create a customer for an indirect reseller, please see [Create a customer for an indirect reseller](create-a-customer-for-an-indirect-reseller.md).</span></span>

<span data-ttu-id="83faa-111">Als Cloud Solution Provider (CSP)-partner, kunt u bij het maken van een klant orders namens de klant plaatsen.</span><span class="sxs-lookup"><span data-stu-id="83faa-111">As a cloud solution provider (CSP) partner, when you create a customer you can place orders on behalf of the customer.</span></span> <span data-ttu-id="83faa-112">Wanneer u een klant maakt, maakt u ook het volgende:</span><span class="sxs-lookup"><span data-stu-id="83faa-112">When you create a customer, you also create:</span></span>

- <span data-ttu-id="83faa-113">Een Azure Active Directory (AD)-Tenant object voor de klant.</span><span class="sxs-lookup"><span data-stu-id="83faa-113">An Azure Active Directory (AD) tenant object for the customer.</span></span>

- <span data-ttu-id="83faa-114">Een relatie tussen de wederverkoper en de klant, die wordt gebruikt voor gedelegeerde beheerders bevoegdheden.</span><span class="sxs-lookup"><span data-stu-id="83faa-114">A relationship between the reseller and customer, used for delegated admin privileges.</span></span>

- <span data-ttu-id="83faa-115">Een gebruikers naam en wacht woord om u aan te melden als beheerder voor de klant.</span><span class="sxs-lookup"><span data-stu-id="83faa-115">A user name and password to sign in as an admin for the customer.</span></span>

<span data-ttu-id="83faa-116">Nadat de klant is gemaakt, moet u ervoor zorgen dat u de klant-ID en Azure AD-gegevens opslaat voor toekomstig gebruik met de SDK van de partner centrum (bijvoorbeeld account beheer).</span><span class="sxs-lookup"><span data-stu-id="83faa-116">Once the customer is created, be sure to save the customer ID and Azure AD details for future use with the Partner Center SDK (for example, account management).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="83faa-117">Vereisten</span><span class="sxs-lookup"><span data-stu-id="83faa-117">Prerequisites</span></span>

- <span data-ttu-id="83faa-118">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="83faa-118">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="83faa-119">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="83faa-119">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="83faa-120">Als u een Tenant van de klant wilt maken, moet u een geldig fysiek adres opgeven tijdens het aanmaak proces.</span><span class="sxs-lookup"><span data-stu-id="83faa-120">To create a customer tenant you must provide a valid physical address during the creation process.</span></span> <span data-ttu-id="83faa-121">U kunt een adres valideren door de stappen te volgen die worden beschreven in het scenario [een adres valideren](validate-an-address.md) .</span><span class="sxs-lookup"><span data-stu-id="83faa-121">An address can be validated by following the steps outlined in the [Validate an address](validate-an-address.md) scenario.</span></span> <span data-ttu-id="83faa-122">Als u een klant maakt met behulp van een ongeldig adres in de sandbox-omgeving, kunt u die Tenant van de klant niet verwijderen.</span><span class="sxs-lookup"><span data-stu-id="83faa-122">If you create a customer using an invalid address in the sandbox environment, you will not be able to delete that customer tenant.</span></span>

## <a name="c"></a><span data-ttu-id="83faa-123">C\#</span><span class="sxs-lookup"><span data-stu-id="83faa-123">C\#</span></span>

<span data-ttu-id="83faa-124">Een klant toevoegen:</span><span class="sxs-lookup"><span data-stu-id="83faa-124">To add a customer:</span></span>

1. <span data-ttu-id="83faa-125">Een nieuw [**klant**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object instantiëren.</span><span class="sxs-lookup"><span data-stu-id="83faa-125">Instantiate a new [**Customer**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object.</span></span> <span data-ttu-id="83faa-126">Zorg ervoor dat u de [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) en de [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile)invult.</span><span class="sxs-lookup"><span data-stu-id="83faa-126">Be sure to fill in the [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) and [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile).</span></span>

2. <span data-ttu-id="83faa-127">Voeg de nieuwe klant toe aan uw verzameling [**IAggregatePartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) door [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync)aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="83faa-127">Add the new customer to your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection by calling [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) or [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync).</span></span>

### <a name="c-example"></a><span data-ttu-id="83faa-128">C- \# voor beeld</span><span class="sxs-lookup"><span data-stu-id="83faa-128">C\# example</span></span>

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

<span data-ttu-id="83faa-129">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="83faa-129">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="83faa-130">**Project**: Partner Center SDK samples **klasse**: CreateCustomer. cs</span><span class="sxs-lookup"><span data-stu-id="83faa-130">**Project**: Partner Center SDK Samples **Class**: CreateCustomer.cs</span></span>

## <a name="java"></a><span data-ttu-id="83faa-131">Java</span><span class="sxs-lookup"><span data-stu-id="83faa-131">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="83faa-132">Een nieuwe klant maken:</span><span class="sxs-lookup"><span data-stu-id="83faa-132">To create a new customer:</span></span>

1. <span data-ttu-id="83faa-133">Maak een nieuw exemplaar van de **CustomerBillingProfile** -en **CustomerCompanyProfile** -objecten.</span><span class="sxs-lookup"><span data-stu-id="83faa-133">Create a new instance of the **CustomerBillingProfile** and the **CustomerCompanyProfile** objects.</span></span> <span data-ttu-id="83faa-134">Zorg ervoor dat u de vereiste velden vult.</span><span class="sxs-lookup"><span data-stu-id="83faa-134">Be sure to populate the required fields.</span></span>

2. <span data-ttu-id="83faa-135">Maak de klant door de functie **IAggregatePartner. getCustomers (). Create** aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="83faa-135">Create the customer by calling the **IAggregatePartner.getCustomers().create** function.</span></span>

### <a name="java-example"></a><span data-ttu-id="83faa-136">Java-voor beeld</span><span class="sxs-lookup"><span data-stu-id="83faa-136">Java example</span></span>

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

## <a name="powershell"></a><span data-ttu-id="83faa-137">PowerShell</span><span class="sxs-lookup"><span data-stu-id="83faa-137">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="83faa-138">Als u een klant wilt maken, voert u de opdracht [**New-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md) uit.</span><span class="sxs-lookup"><span data-stu-id="83faa-138">To create a customer execute the [**New-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md) command.</span></span>

```powershell
New-PartnerCustomer -BillingAddressLine1 '1 Microsoft Way' -BillingAddressCity 'Redmond' -BillingAddressCountry 'US' -BillingAddressPostalCode '98052' -BillingAddressState 'WA' -ContactEmail 'jdoe@customer.com' -ContactFirstName 'Jane' -ContactLastName 'Doe' -Culture 'en-US' -Domain 'newcustomer.onmicrosoft.com' -Language 'en' -Name 'New Customer'
```

## <a name="rest-request"></a><span data-ttu-id="83faa-139">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="83faa-139">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="83faa-140">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="83faa-140">Request syntax</span></span>

| <span data-ttu-id="83faa-141">Methode</span><span class="sxs-lookup"><span data-stu-id="83faa-141">Method</span></span>   | <span data-ttu-id="83faa-142">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="83faa-142">Request URI</span></span>                                                       |
|----------|-------------------------------------------------------------------|
| <span data-ttu-id="83faa-143">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="83faa-143">**POST**</span></span> | <span data-ttu-id="83faa-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers http/1.1</span><span class="sxs-lookup"><span data-stu-id="83faa-144">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1</span></span> |

### <a name="request-headers"></a><span data-ttu-id="83faa-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="83faa-145">Request headers</span></span>

- <span data-ttu-id="83faa-146">Deze API is idempotent (het levert geen ander resultaat op als u het meerdere keren aanroept).</span><span class="sxs-lookup"><span data-stu-id="83faa-146">This API is idempotent (it will not yield a different result if you call it multiple times).</span></span>

- <span data-ttu-id="83faa-147">Een aanvraag-ID en correlatie-ID zijn vereist.</span><span class="sxs-lookup"><span data-stu-id="83faa-147">A request ID and correlation ID are required.</span></span>

- <span data-ttu-id="83faa-148">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="83faa-148">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="83faa-149">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="83faa-149">Request body</span></span>

<span data-ttu-id="83faa-150">In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="83faa-150">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="83faa-151">Naam</span><span class="sxs-lookup"><span data-stu-id="83faa-151">Name</span></span>                              | <span data-ttu-id="83faa-152">Type</span><span class="sxs-lookup"><span data-stu-id="83faa-152">Type</span></span>   | <span data-ttu-id="83faa-153">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="83faa-153">Description</span></span>                                 |
|-----------------------------------|--------|---------------------------------------------|
| [<span data-ttu-id="83faa-154">BillingProfile</span><span class="sxs-lookup"><span data-stu-id="83faa-154">BillingProfile</span></span>](#billing-profile) | <span data-ttu-id="83faa-155">object</span><span class="sxs-lookup"><span data-stu-id="83faa-155">object</span></span> | <span data-ttu-id="83faa-156">De facturerings profiel gegevens van de klant.</span><span class="sxs-lookup"><span data-stu-id="83faa-156">The customer's billing profile information.</span></span> |
| [<span data-ttu-id="83faa-157">CompanyProfile</span><span class="sxs-lookup"><span data-stu-id="83faa-157">CompanyProfile</span></span>](#company-profile) | <span data-ttu-id="83faa-158">object</span><span class="sxs-lookup"><span data-stu-id="83faa-158">object</span></span> | <span data-ttu-id="83faa-159">De gegevens van het bedrijfs profiel van de klant.</span><span class="sxs-lookup"><span data-stu-id="83faa-159">The customer's company profile information.</span></span> |

#### <a name="billing-profile"></a><span data-ttu-id="83faa-160">Factureringsprofiel</span><span class="sxs-lookup"><span data-stu-id="83faa-160">Billing profile</span></span>

<span data-ttu-id="83faa-161">In deze tabel worden de minimale vereiste velden van de [CustomerBillingProfile](customer-resources.md#customerbillingprofile) -resource beschreven die nodig zijn om een nieuwe klant te maken.</span><span class="sxs-lookup"><span data-stu-id="83faa-161">This table describes the minimum required fields from the [CustomerBillingProfile](customer-resources.md#customerbillingprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="83faa-162">Naam</span><span class="sxs-lookup"><span data-stu-id="83faa-162">Name</span></span>             | <span data-ttu-id="83faa-163">Type</span><span class="sxs-lookup"><span data-stu-id="83faa-163">Type</span></span>                                     | <span data-ttu-id="83faa-164">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="83faa-164">Description</span></span>                                                                                                                                                                                                     |
|------------------|------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="83faa-165">e-mail</span><span class="sxs-lookup"><span data-stu-id="83faa-165">email</span></span>            | <span data-ttu-id="83faa-166">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="83faa-166">string</span></span>                                   | <span data-ttu-id="83faa-167">Het e-mail adres van de klant.</span><span class="sxs-lookup"><span data-stu-id="83faa-167">The customer's email address.</span></span>                                                                                                                                                                                   |
| <span data-ttu-id="83faa-168">culturele</span><span class="sxs-lookup"><span data-stu-id="83faa-168">culture</span></span>          | <span data-ttu-id="83faa-169">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="83faa-169">string</span></span>                                   | <span data-ttu-id="83faa-170">De voorkeurs cultuur voor communicatie en valuta, zoals ' en-US '.</span><span class="sxs-lookup"><span data-stu-id="83faa-170">Their preferred culture for communication and currency, such as "en-US".</span></span> <span data-ttu-id="83faa-171">Zie [ondersteunde talen en land instellingen voor het partner centrum](partner-center-supported-languages-and-locales.md) voor de ondersteunde cult uren.</span><span class="sxs-lookup"><span data-stu-id="83faa-171">See [Partner Center supported languages and locales](partner-center-supported-languages-and-locales.md) for the supported cultures.</span></span> |
| <span data-ttu-id="83faa-172">language</span><span class="sxs-lookup"><span data-stu-id="83faa-172">language</span></span>         | <span data-ttu-id="83faa-173">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="83faa-173">string</span></span>                                   | <span data-ttu-id="83faa-174">De standaard taal.</span><span class="sxs-lookup"><span data-stu-id="83faa-174">The default language.</span></span> <span data-ttu-id="83faa-175">Taal codes voor twee tekens (bijvoorbeeld `en` of `fr` ) worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="83faa-175">Two character language codes (for example `en` or `fr`) are supported.</span></span>                                                                                                                                |
| <span data-ttu-id="83faa-176">bedrijfs \_ naam</span><span class="sxs-lookup"><span data-stu-id="83faa-176">company\_name</span></span>    | <span data-ttu-id="83faa-177">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="83faa-177">string</span></span>                                   | <span data-ttu-id="83faa-178">De naam van het geregistreerde bedrijf/de organisatie.</span><span class="sxs-lookup"><span data-stu-id="83faa-178">The registered company/organization name.</span></span>                                                                                                                                                                       |
| <span data-ttu-id="83faa-179">standaard \_ adres</span><span class="sxs-lookup"><span data-stu-id="83faa-179">default\_address</span></span> | [<span data-ttu-id="83faa-180">Adres</span><span class="sxs-lookup"><span data-stu-id="83faa-180">Address</span></span>](utility-resources.md#address) | <span data-ttu-id="83faa-181">Het geregistreerde adres van het bedrijf/de organisatie van de klant.</span><span class="sxs-lookup"><span data-stu-id="83faa-181">The registered address of the customer's company/organization.</span></span> <span data-ttu-id="83faa-182">Zie de [adres](utility-resources.md#address) bron voor informatie over de beperkingen van elke lengte.</span><span class="sxs-lookup"><span data-stu-id="83faa-182">See the [Address](utility-resources.md#address) resource for information on any length limitations.</span></span>                                             |

#### <a name="company-profile"></a><span data-ttu-id="83faa-183">Bedrijfs profiel</span><span class="sxs-lookup"><span data-stu-id="83faa-183">Company profile</span></span>

<span data-ttu-id="83faa-184">In deze tabel worden de minimale vereiste velden van de [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) -resource beschreven die nodig zijn om een nieuwe klant te maken.</span><span class="sxs-lookup"><span data-stu-id="83faa-184">This table describes the minimum required fields from the [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) resource needed to create a new customer.</span></span>

| <span data-ttu-id="83faa-185">Naam</span><span class="sxs-lookup"><span data-stu-id="83faa-185">Name</span></span>   | <span data-ttu-id="83faa-186">Type</span><span class="sxs-lookup"><span data-stu-id="83faa-186">Type</span></span>   | <span data-ttu-id="83faa-187">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="83faa-187">Description</span></span>                                                  |
|--------|--------|--------------------------------------------------------------|
| <span data-ttu-id="83faa-188">domein</span><span class="sxs-lookup"><span data-stu-id="83faa-188">domain</span></span> | <span data-ttu-id="83faa-189">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="83faa-189">string</span></span> | <span data-ttu-id="83faa-190">De domein naam van de klant, zoals contoso.onmicrosoft.com.</span><span class="sxs-lookup"><span data-stu-id="83faa-190">The customer's domain name, such as contoso.onmicrosoft.com.</span></span> |
|<span data-ttu-id="83faa-191">organizationRegistrationNumber</span><span class="sxs-lookup"><span data-stu-id="83faa-191">organizationRegistrationNumber</span></span>|<span data-ttu-id="83faa-192">Tekenreeks</span><span class="sxs-lookup"><span data-stu-id="83faa-192">String</span></span>|<span data-ttu-id="83faa-193">Het registratie nummer van de klant (ook wel INN-nummer genoemd in bepaalde landen).</span><span class="sxs-lookup"><span data-stu-id="83faa-193">The customer’s organization registration number (also referred to as INN number in certain countries).</span></span> <span data-ttu-id="83faa-194">Alleen vereist voor het bedrijf/de organisatie van de klant in de volgende landen: Armenië (AM), Azerbeidzjan (AZ), Belarus (BY), Hongarije (HU), Kazachstan (KZ), Kirgizië (KG), Moldavië (MD), Rusland (RU), Tadzjikistan (TJ), Oezbekistan (UZ), Oekraïne (UA), Brazilië (BR), India, Zuid-Afrika, Polen, Verenigde Arabische Emiraten, Saoedi-Arabië, Turkije, Thai, Vietnam, Myanmar, Irak, Zuid-Soedan en Venezuela.</span><span class="sxs-lookup"><span data-stu-id="83faa-194">Only required for customer’s company/organization located in the following countries: Armenia(AM), Azerbaijan(AZ), Belarus(BY), Hungary(HU), Kazakhstan(KZ), Kyrgyzstan(KG), Moldova(MD), Russia(RU), Tajikistan(TJ), Uzbekistan(UZ), Ukraine(UA), Brazil(BR), India, South Africa, Poland, United Arab Emirates, Saudi Arabia, Turkey, Thailand, Vietnam, Myanmar, Iraq, South Sudan and Venezuela.</span></span> <span data-ttu-id="83faa-195">Voor het bedrijf/de organisatie van de klant in andere landen is dit een optioneel veld.</span><span class="sxs-lookup"><span data-stu-id="83faa-195">For customer’s company/organization located in other countries this is an optional field.</span></span>|

### <a name="request-example"></a><span data-ttu-id="83faa-196">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="83faa-196">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="83faa-197">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="83faa-197">REST response</span></span>

<span data-ttu-id="83faa-198">Als deze is geslaagd, retourneert deze API een [klant](customer-resources.md#customer) resource voor de nieuwe klant.</span><span class="sxs-lookup"><span data-stu-id="83faa-198">If successful, this API returns a [Customer](customer-resources.md#customer) resource for the new customer.</span></span> <span data-ttu-id="83faa-199">Sla de klant-ID en Azure AD-Details op voor toekomstig gebruik met de Partner Center-SDK.</span><span class="sxs-lookup"><span data-stu-id="83faa-199">Save the customer ID and Azure AD details for future use with the Partner Center SDK.</span></span> <span data-ttu-id="83faa-200">U hebt deze nodig voor gebruik met account beheer, bijvoorbeeld.</span><span class="sxs-lookup"><span data-stu-id="83faa-200">You will need them for use with account management, for example.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="83faa-201">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="83faa-201">Response success and error codes</span></span>

<span data-ttu-id="83faa-202">Antwoorden worden geleverd met een HTTP-status code die aangeeft of de fout is geslaagd of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="83faa-202">Responses come with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="83faa-203">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="83faa-203">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="83faa-204">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="83faa-204">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="83faa-205">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="83faa-205">Response example</span></span>

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
