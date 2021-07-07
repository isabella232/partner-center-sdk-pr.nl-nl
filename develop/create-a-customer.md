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
# <a name="create-a-customer-using-partner-center-apis"></a>Een klant maken met behulp Partner Center API's

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud for US Government

In dit artikel wordt uitgelegd hoe u een nieuwe klant maakt.

> [!IMPORTANT]
> Als u een indirecte provider bent en u een klant wilt maken voor een indirecte reseller, raadpleegt u Een klant [maken voor een indirecte reseller.](create-a-customer-for-an-indirect-reseller.md)

Wanneer u als CSP-partner (Cloud Solution Provider) een klant maakt, kunt u namens de klant orders plaatsen. Wanneer u een klant maakt, maakt u ook het volgende:

- Een Azure Active Directory (AD)-tenantobject voor de klant.

- Een relatie tussen de reseller en de klant, die wordt gebruikt voor gedelegeerde beheerdersbevoegdheden.

- Een gebruikersnaam en wachtwoord om u aan te melden als beheerder voor de klant.

Nadat de klant is gemaakt, moet u de klant-id en Azure AD-gegevens opslaan voor toekomstig gebruik met de Partnercentrum-SDK (bijvoorbeeld accountbeheer).

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

> [!IMPORTANT]
> Als u een klant-tenant wilt maken, moet u tijdens het maken een geldig fysiek adres verstrekken. Een adres kan worden gevalideerd door de stappen te volgen die worden beschreven in het [scenario Een adres valideren.](validate-an-address.md) Als u een klant maakt met een ongeldig adres in de sandbox-omgeving, kunt u die tenant van de klant niet verwijderen.

## <a name="c"></a>C\#

Een klant toevoegen:

1. Instantieer een nieuw [**klantobject.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) Vul het [**BillingProfile en**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) [**CompanyProfile in.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile)

2. Voeg de nieuwe klant toe aan uw [**verzameling IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) door [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) of [**CreateAsync aan te roepen.**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync)

### <a name="c-example"></a>\#C-voorbeeld

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

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project:** Partnercentrum-SDK Klasse **Samples:** CreateCustomer.cs

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Een nieuwe klant maken:

1. Maak een nieuw exemplaar van **het CustomerBillingProfile-** en **de CustomerCompanyProfile-objecten.** Vul de vereiste velden in.

2. Maak de klant door de functie **IAggregatePartner.getCustomers().create aan te** roepen.

### <a name="java-example"></a>Java-voorbeeld

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

Als u een klant wilt maken, voert u [**de opdracht New-PartnerCustomer**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/New-PartnerCustomer.md) uit.

```powershell
New-PartnerCustomer -BillingAddressLine1 '1 Microsoft Way' -BillingAddressCity 'Redmond' -BillingAddressCountry 'US' -BillingAddressPostalCode '98052' -BillingAddressState 'WA' -ContactEmail 'jdoe@customer.com' -ContactFirstName 'Jane' -ContactLastName 'Doe' -Culture 'en-US' -Domain 'newcustomer.onmicrosoft.com' -Language 'en' -Name 'New Customer'
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                       |
|----------|-------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

- Deze API is idempotent (deze levert geen ander resultaat op als u deze meerdere keren aanroept).

- Een aanvraag-id en correlatie-id zijn vereist.

- Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.

| Naam                              | Type   | Beschrijving                                 |
|-----------------------------------|--------|---------------------------------------------|
| [BillingProfile](#billing-profile) | object | De gegevens van het factureringsprofiel van de klant. |
| [CompanyProfile](#company-profile) | object | De bedrijfsprofielgegevens van de klant. |

#### <a name="billing-profile"></a>Factureringsprofiel

In deze tabel worden de minimaal vereiste velden van de [CustomerBillingProfile-resource](customer-resources.md#customerbillingprofile) beschreven die nodig zijn om een nieuwe klant te maken.

| Naam             | Type                                     | Beschrijving                                                                                                                                                                                                     |
|------------------|------------------------------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| e-mail            | tekenreeks                                   | Het e-mailadres van de klant.                                                                                                                                                                                   |
| Cultuur          | tekenreeks                                   | Hun voorkeurscultuur voor communicatie en valuta, zoals 'en-US'. Zie [Partner Center ondersteunde talen en talen voor](partner-center-supported-languages-and-locales.md) de ondersteunde culturen. |
| language         | tekenreeks                                   | De standaardtaal. Er worden twee tekentaalcodes `en` (bijvoorbeeld of `fr` ) ondersteund.                                                                                                                                |
| \_bedrijfsnaam    | tekenreeks                                   | De geregistreerde bedrijfsnaam/organisatienaam.                                                                                                                                                                       |
| \_standaardadres | [Adres](utility-resources.md#address) | Het geregistreerde adres van het bedrijf/de organisatie van de klant. Zie de [adresresource](utility-resources.md#address) voor informatie over lengtebeperkingen.                                             |

#### <a name="company-profile"></a>Bedrijfsprofiel

In deze tabel worden de minimaal vereiste velden van de resource [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) beschreven die nodig zijn om een nieuwe klant te maken.

| Naam   | Type   | Beschrijving                                                  |
|--------|--------|--------------------------------------------------------------|
| domein | tekenreeks | De domeinnaam van de klant, zoals contoso.onmicrosoft.com. |
|organizationRegistrationNumber|Tekenreeks|Het registratienummer van de organisatie van de klant (ook wel INN-nummer genoemd in bepaalde landen). Alleen vereist voor het bedrijf/de organisatie van de klant die zich in de volgende landen bevindt: 1000(AM), Zowel(AM), Elkaar(AZ), Gaata(NU), Als(KZ), Kyrgyzstan(KG), Espa(MD), Rusland(RU), Tstanikrov(TJ), Uzbekjik(UZ), UA (UA), Brazil(BR), India, Zuid-Afrika, Spanje, Verenigde Arabische Republieken, Hongkong, Republiek, Vietnam, Vietnam, Vietnam, Zuid-Afrika en Eu na. Voor het bedrijf/de organisatie van de klant in andere landen is dit een optioneel veld.|

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

Als dit lukt, retourneert deze API een [klantresource](customer-resources.md#customer) voor de nieuwe klant. Sla de klant-id en Azure AD-gegevens op voor toekomstig gebruik met de Partnercentrum-SDK. U hebt deze bijvoorbeeld nodig voor gebruik met accountbeheer.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Antwoorden worden verstrekt met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
