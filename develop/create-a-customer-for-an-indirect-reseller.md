---
title: Een klant voor een indirecte reseller maken
description: Meer informatie over hoe een indirecte provider Partner Center API's kan gebruiken om een klant te maken voor een indirecte reseller.
ms.date: 04/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: e54e083dda758cc712c889916676007a389ba69c8009bb3d4907df343a436004
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991732"
---
# <a name="create-a-customer-for-an-indirect-reseller-using-partner-center-apis"></a>Een klant maken voor een indirecte reseller met behulp van Partner Center API's

Een indirecte provider kan een klant maken voor een indirecte reseller.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- De tenant-id van de indirecte reseller.

- De indirecte reseller moet een partnerschap hebben met de indirecte provider.

## <a name="c"></a>C\#

Een nieuwe klant toevoegen voor een indirecte reseller:

1. Instantieer een nieuw [**Customer-object**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) en instantieer en vul het [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) en [**CompanyProfile in.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile) Zorg ervoor dat u de indirecte reseller-id toewijst aan de [**eigenschap AssociatedPartnerID.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid)

2. Gebruik de [**eigenschap IAggregatePartner.Customers om**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) een interface op te halen voor bewerkingen voor het verzamelen van klanten.

3. Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) om de klant te maken.

### <a name="c-example"></a>\#C-voorbeeld

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

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: CreateCustomerforIndirectReseller.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                       |
|----------|-------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.

| Naam                                          | Type   | Vereist | Beschrijving                                                                                                                                                                                                                                                                                                                                           |
|-----------------------------------------------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [BillingProfile](#billing-profile)             | object | Yes      | De factureringsprofielgegevens van de klant.                                                                                                                                                                                                                                                                                                           |
| [CompanyProfile](#company-profile)             | object | Yes      | De bedrijfsprofielgegevens van de klant.                                                               
| [AssociatedPartnerId](customer-resources.md#customer) | tekenreeks | Yes      | De indirecte reseller-id. De indirecte reseller, zoals aangegeven door de id die hier is opgegeven, moet een partnerschap hebben met de indirecte provider, anders mislukt de aanvraag. Houd er ook rekening mee dat als de associatedPartnerId-waarde niet wordt opgegeven, de klant wordt gemaakt als een directe klant van de indirecte provider in plaats van de indirecte reseller. |
|Domain| Tekenreeks| Ja|De domeinnaam van de klant, zoals contoso.onmicrosoft.com.|
|organizationRegistrationNumber|    tekenreeks|Yes|     Het registratienummer van de organisatie van de klant (in bepaalde landen ook wel HETN-nummer genoemd). Alleen vereist voor het bedrijf/de organisatie van de klant die zich in de volgende landen bevindt: 100000000000000000005555555(MD), China(AM), Tzard (TJ), Uzbekje (UZ), UZ ( UA), India, Brazilië, Zuid-Afrika, United United Afs, United South, South South South, SouthEse, Voor het bedrijf/de organisatie van de klant in andere landen is dit een optioneel veld.|



#### <a name="billing-profile"></a>Factureringsprofiel

In deze tabel worden de minimaal vereiste velden van de [Resource CustomerBillingProfile](customer-resources.md#customerbillingprofile) beschreven die nodig zijn om een nieuwe klant te maken.

| Naam             | Type                                     | Vereist | Beschrijving                                                                                                                                                                                                     |
|------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| e-mail            | tekenreeks                                   | Yes      | Het e-mailadres van de klant.                                                                                                                                                                                   |
| Cultuur          | tekenreeks                                   | Yes      | Hun voorkeurscultuur voor communicatie en valuta, zoals 'en-US'. Zie [Partner Center ondersteunde talen en landen voor](partner-center-supported-languages-and-locales.md) de ondersteunde culturen. |
| language         | tekenreeks                                   | Yes      | De standaardtaal. Er worden twee tekentaalcodes `en` (bijvoorbeeld of `fr` ) ondersteund.                                                                                                                                |
| \_bedrijfsnaam    | tekenreeks                                   | Yes      | De geregistreerde bedrijfsnaam/organisatienaam.                                                                                                                                                                       |
| \_standaardadres | [Adres](utility-resources.md#address) | Yes      | Het geregistreerde adres van het bedrijf/de organisatie van de klant. Zie de [Adresresource](utility-resources.md#address) voor informatie over lengtebeperkingen.                                             |

#### <a name="company-profile"></a>Bedrijfsprofiel

In deze tabel worden de minimaal vereiste velden van de resource [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) beschreven die nodig zijn om een nieuwe klant te maken.

| Naam   | Type   | Vereist | Beschrijving                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| domein | tekenreeks | Yes     | De domeinnaam van de klant, zoals contoso.onmicrosoft.com. |
| organizationRegistrationNumber | tekenreeks | Afhankelijk van de voorwaarde | Het registratienummer van de organisatie van de klant (in bepaalde landen ook wel het INN-nummer genoemd). <br/><br/>Het voltooien van dit veld is alleen vereist als het bedrijf/de organisatie van een klant zich in de volgende landen bevindt: <br/><br/>- Uiting (AM) <br/>- Tussensen (AZ)<br/>- None (BY)<br/>- Doornige (HU)<br/>- Tussenseen (KZ)<br/>- Kyrgyzstan (KG)<br/>- Ligt (MD)<br/>- Rusland (RU)<br/>- Tjikjikjik (TJ)<br/>- Uzbekjik (UZ)<br/>- Uiting (UA)<br/>- India <br/>- Brazilië <br/>- Zuid-Afrika <br/>- Niet-gedys <br/>- Verenigde Arabische Republieken <br/>- Hongkong <br/>- Uitsporing <br/>- <br/>- Vietnam <br/>- <br/>- Uithalen <br/>- Zuid-Korea <br/>-<br/> <br/>Voor het bedrijf/de organisatie van de klant in andere landen is dit een optioneel veld.  |

### <a name="request-example"></a>Voorbeeld van aanvraag

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

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat het antwoord een [klantresource](customer-resources.md#customer) voor de nieuwe klant.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Antwoorden worden verstrekt met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

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