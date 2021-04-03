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
# <a name="create-a-customer-using-partner-center-apis"></a>Een klant maken met partner Center-Api's

**Van toepassing op:**

- Partnercentrum
- Partnercentrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt uitgelegd hoe u een nieuwe klant maakt.

> [!IMPORTANT]
> Als u een indirecte provider bent en u een klant voor een indirecte wederverkoper wilt maken, raadpleegt u [een klant maken voor een indirecte wederverkoper](create-a-customer-for-an-indirect-reseller.md).

Als Cloud Solution Provider (CSP)-partner, kunt u bij het maken van een klant orders namens de klant plaatsen. Wanneer u een klant maakt, maakt u ook het volgende:

- Een Azure Active Directory (AD)-Tenant object voor de klant.

- Een relatie tussen de wederverkoper en de klant, die wordt gebruikt voor gedelegeerde beheerders bevoegdheden.

- Een gebruikers naam en wacht woord om u aan te melden als beheerder voor de klant.

Nadat de klant is gemaakt, moet u ervoor zorgen dat u de klant-ID en Azure AD-gegevens opslaat voor toekomstig gebruik met de SDK van de partner centrum (bijvoorbeeld account beheer).

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

> [!IMPORTANT]
> Als u een Tenant van de klant wilt maken, moet u een geldig fysiek adres opgeven tijdens het aanmaak proces. U kunt een adres valideren door de stappen te volgen die worden beschreven in het scenario [een adres valideren](validate-an-address.md) . Als u een klant maakt met behulp van een ongeldig adres in de sandbox-omgeving, kunt u die Tenant van de klant niet verwijderen.

## <a name="c"></a>C\#

Een klant toevoegen:

1. Een nieuw [**klant**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object instantiëren. Zorg ervoor dat u de [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) en de [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile)invult.

2. Voeg de nieuwe klant toe aan uw verzameling [**IAggregatePartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) door [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync)aan te roepen.

### <a name="c-example"></a>C- \# voor beeld

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

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK samples **klasse**: CreateCustomer. cs

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Een nieuwe klant maken:

1. Maak een nieuw exemplaar van de **CustomerBillingProfile** -en **CustomerCompanyProfile** -objecten. Zorg ervoor dat u de vereiste velden vult.

2. Maak de klant door de functie **IAggregatePartner. getCustomers (). Create** aan te roepen.

### <a name="java-example"></a>Java-voor beeld

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

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Als u een klant wilt maken, voert u de opdracht [**New-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md) uit.

```powershell
New-PartnerCustomer -BillingAddressLine1 '1 Microsoft Way' -BillingAddressCity 'Redmond' -BillingAddressCountry 'US' -BillingAddressPostalCode '98052' -BillingAddressState 'WA' -ContactEmail 'jdoe@customer.com' -ContactFirstName 'Jane' -ContactLastName 'Doe' -Culture 'en-US' -Domain 'newcustomer.onmicrosoft.com' -Language 'en' -Name 'New Customer'
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                       |
|----------|-------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers http/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

- Deze API is idempotent (het levert geen ander resultaat op als u het meerdere keren aanroept).

- Een aanvraag-ID en correlatie-ID zijn vereist.

- Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.

| Naam                              | Type   | Beschrijving                                 |
|-----------------------------------|--------|---------------------------------------------|
| [BillingProfile](#billing-profile) | object | De facturerings profiel gegevens van de klant. |
| [CompanyProfile](#company-profile) | object | De gegevens van het bedrijfs profiel van de klant. |

#### <a name="billing-profile"></a>Factureringsprofiel

In deze tabel worden de minimale vereiste velden van de [CustomerBillingProfile](customer-resources.md#customerbillingprofile) -resource beschreven die nodig zijn om een nieuwe klant te maken.

| Naam             | Type                                     | Beschrijving                                                                                                                                                                                                     |
|------------------|------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| e-mail            | tekenreeks                                   | Het e-mail adres van de klant.                                                                                                                                                                                   |
| culturele          | tekenreeks                                   | De voorkeurs cultuur voor communicatie en valuta, zoals ' en-US '. Zie [ondersteunde talen en land instellingen voor het partner centrum](partner-center-supported-languages-and-locales.md) voor de ondersteunde cult uren. |
| language         | tekenreeks                                   | De standaard taal. Taal codes voor twee tekens (bijvoorbeeld `en` of `fr` ) worden ondersteund.                                                                                                                                |
| bedrijfs \_ naam    | tekenreeks                                   | De naam van het geregistreerde bedrijf/de organisatie.                                                                                                                                                                       |
| standaard \_ adres | [Adres](utility-resources.md#address) | Het geregistreerde adres van het bedrijf/de organisatie van de klant. Zie de [adres](utility-resources.md#address) bron voor informatie over de beperkingen van elke lengte.                                             |

#### <a name="company-profile"></a>Bedrijfs profiel

In deze tabel worden de minimale vereiste velden van de [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) -resource beschreven die nodig zijn om een nieuwe klant te maken.

| Naam   | Type   | Beschrijving                                                  |
|--------|--------|--------------------------------------------------------------|
| domein | tekenreeks | De domein naam van de klant, zoals contoso.onmicrosoft.com. |
|organizationRegistrationNumber|Tekenreeks|Het registratie nummer van de klant (ook wel INN-nummer genoemd in bepaalde landen). Alleen vereist voor het bedrijf/de organisatie van de klant in de volgende landen: Armenië (AM), Azerbeidzjan (AZ), Belarus (BY), Hongarije (HU), Kazachstan (KZ), Kirgizië (KG), Moldavië (MD), Rusland (RU), Tadzjikistan (TJ), Oezbekistan (UZ), Oekraïne (UA), Brazilië (BR), India, Zuid-Afrika, Polen, Verenigde Arabische Emiraten, Saoedi-Arabië, Turkije, Thai, Vietnam, Myanmar, Irak, Zuid-Soedan en Venezuela. Voor het bedrijf/de organisatie van de klant in andere landen is dit een optioneel veld.|

### <a name="request-example"></a>Voorbeeld van aanvraag

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

## <a name="rest-response"></a>REST-antwoord

Als deze is geslaagd, retourneert deze API een [klant](customer-resources.md#customer) resource voor de nieuwe klant. Sla de klant-ID en Azure AD-Details op voor toekomstig gebruik met de Partner Center-SDK. U hebt deze nodig voor gebruik met account beheer, bijvoorbeeld.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Antwoorden worden geleverd met een HTTP-status code die aangeeft of de fout is geslaagd of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

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
