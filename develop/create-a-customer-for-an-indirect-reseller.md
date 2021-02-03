---
title: Een klant voor een indirecte reseller maken
description: Meer informatie over hoe een indirecte provider Partner Center-Api's kan gebruiken voor het maken van een klant voor een indirecte wederverkoper.
ms.date: 11/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: e2386f1963a5bb3ea4269bcbf4327c75987f3b91
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767650"
---
# <a name="create-a-customer-for-an-indirect-reseller-using-partner-center-apis"></a>Een klant voor een indirecte wederverkoper maken met behulp van partner Center-Api's

**Van toepassing op:**

- Partnercentrum

Een indirecte provider kan een klant maken voor een indirecte wederverkoper.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- De Tenant-id van de indirecte wederverkoper.

- De indirecte wederverkoper moet een partnerschap met de indirecte provider hebben.

## <a name="c"></a>C\#

Een nieuwe klant toevoegen voor een indirecte wederverkoper:

1. Exemplaar een nieuw [**klant**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object en pas vervolgens de [**BillingProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile) en [**CompanyProfile**](/dotnet/api/microsoft.store.partnercenter.models.customers.customercompanyprofile)aan. Zorg ervoor dat u de ID van de indirecte wederverkoper toewijst aan de eigenschap [**AssociatedPartnerID**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer.associatedpartnerid) .

2. Gebruik de eigenschap [**IAggregatePartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) om een interface voor het verzamelen van klanten op te halen.

3. Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientitycreateoperations-2.createasync) aan om de klant te maken.

### <a name="c-example"></a>C- \# voor beeld

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

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: CreateCustomerforIndirectReseller.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                       |
|----------|-------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers http/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.

| Naam                                          | Type   | Vereist | Beschrijving                                                                                                                                                                                                                                                                                                                                           |
|-----------------------------------------------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| [BillingProfile](#billing-profile)             | object | Yes      | De facturerings profiel gegevens van de klant.                                                                                                                                                                                                                                                                                                           |
| [CompanyProfile](#company-profile)             | object | Yes      | De gegevens van het bedrijfs profiel van de klant.                                                               
| [AssociatedPartnerId](customer-resources.md#customer) | tekenreeks | Yes      | De ID van de indirecte wederverkoper. De indirecte wederverkoper zoals aangegeven door de ID die u hier opgeeft, moet een partnerschap met de indirecte provider hebben, anders mislukt de aanvraag. Houd er ook rekening mee dat als de waarde AssociatedPartnerId niet wordt opgegeven, de klant wordt gemaakt als een rechtstreekse klant van de indirecte provider in plaats van de indirecte wederverkoper. |
|Domain| Tekenreeks| Ja|De domein naam van de klant, zoals contoso.onmicrosoft.com.|
|organizationRegistrationNumber|    tekenreeks|Yes|     Het registratie nummer van de klant (ook wel INN-nummer genoemd in bepaalde landen). Alleen vereist voor het bedrijf/de organisatie van de klant in de volgende landen. Armenië (AM), Azerbeidzjan (AZ), Belarus (BY), Hongarije (HU), Kazachstan (KZ), Kirgizië (KG), Moldavië (MD), Rusland (RU), Tadzjikistan (TJ), Oezbekistan (UZ), Oekraïne (UA). Voor het bedrijf/de organisatie van de klant die zich in andere landen bevindt, moet dit niet worden opgegeven.|



#### <a name="billing-profile"></a>Factureringsprofiel

In deze tabel worden de minimale vereiste velden van de [CustomerBillingProfile](customer-resources.md#customerbillingprofile) -resource beschreven die nodig zijn om een nieuwe klant te maken.

| Naam             | Type                                     | Vereist | Beschrijving                                                                                                                                                                                                     |
|------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| e-mail            | tekenreeks                                   | Yes      | Het e-mail adres van de klant.                                                                                                                                                                                   |
| culturele          | tekenreeks                                   | Yes      | De voorkeurs cultuur voor communicatie en valuta, zoals ' en-US '. Zie [ondersteunde talen en land instellingen voor het partner centrum](partner-center-supported-languages-and-locales.md) voor de ondersteunde cult uren. |
| language         | tekenreeks                                   | Yes      | De standaard taal. Taal codes voor twee tekens (bijvoorbeeld `en` of `fr` ) worden ondersteund.                                                                                                                                |
| bedrijfs \_ naam    | tekenreeks                                   | Yes      | De naam van het geregistreerde bedrijf/de organisatie.                                                                                                                                                                       |
| standaard \_ adres | [Adres](utility-resources.md#address) | Yes      | Het geregistreerde adres van het bedrijf/de organisatie van de klant. Zie de [adres](utility-resources.md#address) bron voor informatie over de beperkingen van elke lengte.                                             |

#### <a name="company-profile"></a>Bedrijfs profiel

In deze tabel worden de minimale vereiste velden van de [CustomerCompanyProfile](customer-resources.md#customercompanyprofile) -resource beschreven die nodig zijn om een nieuwe klant te maken.

| Naam   | Type   | Vereist | Beschrijving                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| domein | tekenreeks | Yes     | De domein naam van de klant, zoals contoso.onmicrosoft.com. |
| organizationRegistrationNumber | tekenreeks | Is afhankelijk van de voor waarde | Het registratie nummer van de klant (ook wel het INN-nummer in bepaalde landen genoemd). <br/><br/>Volt ooien van dit veld is alleen vereist als het bedrijf/de organisatie van een klant zich in de volgende landen bevindt: <br/><br/>-Armenië (AM) <br/>-Azerbeidzjan (AZ)<br/>-Belarus (per)<br/>-Hongarije (HU)<br/>-Kazachstan (KZ)<br/>-Kirgizië (KG)<br/>-Moldavië (MD)<br/>-Rusland (RU)<br/>-Tadzjikistan (TJ)<br/>-Oezbekistan (UZ)<br/>-Oekraïne (UA)<br/><br/>Dit veld is niet vereist als het bedrijf/de organisatie van de klant zich in andere landen bevindt dan de hier weer gegeven.  |

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

Als dit is gelukt, bevat het antwoord een [klant](customer-resources.md#customer) resource voor de nieuwe klant.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Antwoorden worden geleverd met een HTTP-status code die aangeeft of de fout is geslaagd of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

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