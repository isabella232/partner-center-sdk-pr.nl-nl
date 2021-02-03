---
title: Een geverifieerd domein voor een klant toevoegen
description: Meer informatie over het toevoegen van een geverifieerd domein aan de lijst met goedgekeurde domeinen voor een klant in Partner Center. Doe dit met behulp van partner Center Api's en REST Api's.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d0ea9998324e99c7986645dc90fdfba0a2a71571
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "97767583"
---
# <a name="add-a-verified-domain-to-the-list-of-approved-domains-for-an-existing-customer"></a>Een geverifieerd domein toevoegen aan de lijst met goedgekeurde domeinen voor een bestaande klant 

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Een geverifieerd domein toevoegen aan de lijst met goedgekeurde domeinen voor een bestaande klant.

## <a name="prerequisites"></a>Vereisten

- U moet een partner zijn die een domein registratie service is.

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="adding-a-verified-domain"></a>Een geverifieerd domein toevoegen

Als u een partner bent die een domein registratie service is, kunt u de `verifieddomain` API gebruiken om een nieuwe [domein](#domain) bron te plaatsen in de lijst met domeinen voor een bestaande klant. U kunt dit doen door de klant te identificeren met behulp van hun CustomerTenantId. Geef een waarde op voor de eigenschap VerifiedDomainName. Geef een [domein](#domain) resource op in de aanvraag met de vereiste eigenschappen name, Capability, AuthenticationType, status en VerificationMethod. Als u wilt opgeven dat het nieuwe [domein](#domain) een federatief domein is, stelt u de eigenschap AuthenticationType in de [domein](#domain) resource in op `Federated` en neemt u een [DomainFederationSettings](#domain-federation-settings) -resource op in de aanvraag. Als de methode is geslaagd, bevat het antwoord een [domein](#domain) resource voor het nieuwe geverifieerde domein.

### <a name="custom-verified-domains"></a>Aangepaste geverifieerde domeinen

Bij het toevoegen van een aangepast geverifieerd domein, een domein dat niet is geregistreerd op **onmicrosoft.com**, moet u de eigenschap [CustomerUser. immutableId](user-resources.md#customeruser) instellen op een unieke id-waarde voor de klant voor wie u het domein toevoegt. Deze unieke id is vereist tijdens het validatie proces wanneer het domein wordt geverifieerd. Zie [gebruikers accounts voor een klant maken](create-user-accounts-for-a-customer.md)voor meer informatie over gebruikers accounts van klanten.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode | Aanvraag-URI                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| POST   | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{CustomerTenantId}/verifieddomain http/1.1 |

#### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om de klant op te geven waarvoor u een geverifieerd domein wilt toevoegen.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| CustomerTenantId | guid | J        | De waarde is een GUID-indeling **CustomerTenantId** waarmee u een klant kunt opgeven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.

| Naam                                                  | Type   | Vereist                                      | Beschrijving                                                |
|-------------------------------------------------------|--------|-----------------------------------------------|--------------------------------------------------------|
| VerifiedDomainName                                    | tekenreeks | Yes                                           | De geverifieerde domein naam. |
| [Domein](#domain)                                     | object | Yes                                           | Bevat de domein gegevens. |
| [DomainFederationSettings](#domain-federation-settings) | object | Ja (indien AuthenticationType = `Federated` )     | De Federatie-instellingen van het domein die moeten worden gebruikt als het domein een `Federated` domein is en niet een `Managed` domein. |

### <a name="domain"></a>Domain

In deze tabel worden de vereiste en optionele **domein** eigenschappen in de hoofd tekst van de aanvraag beschreven.

| Naam               | Type                                     | Vereist | Beschrijving                                                                                                                                                                                                     |
|--------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AuthenticationType                                    | tekenreeks           | Yes      | Hiermee wordt gedefinieerd of het domein een `Managed` domein of een `Federated` domein is. Ondersteunde waarden: `Managed` , `Federated` .|
| Mogelijkheid                                            | tekenreeks           | Yes      | Hiermee geeft u de functionaliteit van het domein. Bijvoorbeeld `Email`.                  |
| IsDefault                                             | Booleaanse waarde waarvoor null is toegestaan | No       | Hiermee wordt aangegeven of het domein het standaard domein voor de Tenant is. Ondersteunde waarden: `True` , `False` , `Null` .        |
| IsInitial                                             | Booleaanse waarde waarvoor null is toegestaan | No       | Hiermee wordt aangegeven of het domein een initieel domein is. Ondersteunde waarden: `True` , `False` , `Null` .                       |
| Name                                                  | tekenreeks           | Yes      | De domein naam.                                                          |
| RootDomain                                            | tekenreeks           | No       | De naam van het hoofd domein.                                              |
| Status                                                | tekenreeks           | Yes      | De domein status. Bijvoorbeeld `Verified`. Ondersteunde waarden:  `Unverified` , `Verified` , `PendingDeletion` .                               |
| VerificationMethod                                    | tekenreeks           | Yes      | Het type domein verificatie methode. Ondersteunde waarden: `None` , `DnsRecord` , `Email` .                                    |

### <a name="domain-federation-settings"></a>Federatie-instellingen van domein

In deze tabel worden de vereiste en optionele eigenschappen van **DomainFederationSettings** in de hoofd tekst van de aanvraag beschreven.

| Naam   | Type   | Vereist | Beschrijving                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| ActiveLogOnUri                         | tekenreeks           | No      | De aanmeldings-URI die wordt gebruikt door uitgebreide clients. Deze eigenschap is de STS-verificatie-URL van de partner. |
| DefaultInteractiveAuthenticationMethod | tekenreeks           | No      | Hiermee wordt de standaard authenticatie methode aangegeven die moet worden gebruikt wanneer de gebruiker interactieve aanmelding moet hebben voor een toepassing. |
| FederationBrandName                    | tekenreeks           | No      | De naam van het federatieve merk.        |
| IssuerUri                              | tekenreeks           | Yes     | De naam van de uitgever van de certificaten.                        |
| LogOffUri                              | tekenreeks           | Yes     | De afmeldings-URI. Met deze eigenschap wordt de federatieve domein-afmeldings-URI beschreven.        |
| MetadataExchangeUri                    | tekenreeks           | No      | De URL waarmee het uitwisselings eindpunt voor meta gegevens wordt opgegeven dat wordt gebruikt voor verificatie van geavanceerde client toepassingen. |
| NextSigningCertificate                 | tekenreeks           | No      | Het certificaat dat wordt gebruikt voor de komende toekomst door de ADFS v2 STS om claims te ondertekenen. Deze eigenschap is een base64-gecodeerde representatie van het certificaat. |
| OpenIdConnectDiscoveryEndpoint         | tekenreeks           | No      | Het OpenID Connect Connect-detectie-eind punt van de federatieve IDP-STS. |
| PassiveLogOnUri                        | tekenreeks           | Yes     | De aanmeldings-URI die wordt gebruikt door oudere passieve clients. Deze eigenschap is het adres voor het verzenden van federatieve aanmeldings aanvragen. |
| PreferredAuthenticationProtocol        | tekenreeks           | Yes     | De indeling voor het verificatie token. Bijvoorbeeld `WsFed`. Ondersteunde waarden: `WsFed` , `Samlp` |
| PromptLoginBehavior                    | tekenreeks           | Yes     | Het type aanmeldings gedrag van de prompt.  Bijvoorbeeld `TranslateToFreshPasswordAuth`. Ondersteunde waarden: `TranslateToFreshPasswordAuth` , `NativeSupport` , `Disabled` |
| SigningCertificate                     | tekenreeks           | Yes     | Het certificaat dat momenteel wordt gebruikt door de ADFS v2 STS om claims te ondertekenen. Deze eigenschap is een base64-gecodeerde representatie van het certificaat. |
| SigningCertificateUpdateStatus         | tekenreeks           | No      | Hiermee wordt de update status van het handtekening certificaat aangegeven. |
| SigningCertificateUpdateStatus         | Booleaanse waarde waarvoor null is toegestaan | No      | Geeft aan of de IDP-STS MFA ondersteunt. Ondersteunde waarden: `True` , `False` , `Null` .|

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/customers/{CustomerTenantId}/verifieddomain HTTP/1.1
Authorization: Bearer <token>
Accept: application/json, text/plain, */*
MS-RequestId: 312b044d-dc41-4b37-c2d5-7d27322d9654
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
Content-Type: application/json;charset=utf-8
X-Locale: "en-US"

{
    "VerifiedDomainName": "Example.com",
    "Domain": {
        "AuthenticationType": "Federated",
        "Capability": "Email",
        "IsDefault": Null,
        "IsInitial": Null,
        "Name": "Example.com",
        "RootDomain": null,
        "Status": "Verified",
        "VerificationMethod": "None"
    },
    "DomainFederationSettings": {
        "ActiveLogOnUri": "https://sts.microsoftonline.com/FederationPassive/",
        "DefaultInteractiveAuthenticationMethod": "http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password",
        "FederationBrandName": "FederationBrandName",
        "IssuerUri": "Example.com",
        "LogOffUri": "https://sts.microsoftonline.com/FederationPassive/",
        "MetadataExchangeUri": null,
        "NextSigningCertificate": null,
        "OpenIdConnectDiscoveryEndpoint": "https://sts.contoso.com/adfs/.well-known/openid-configuration",
        "PassiveLogOnUri": "https://sts.microsoftonline.com/Trust/2005/UsernameMixed",
        "PreferredAuthenticationProtocol": "WsFed",
        "PromptLoginBehavior": "TranslateToFreshPasswordAuth",
        "SigningCertificate": <Certificate Signature goes here>,
        "SigningCertificateUpdateStatus": null,
        "SupportsMfa": true
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als deze is geslaagd, retourneert deze API een [domein](#domain) bron voor het nieuwe geverifieerde domein.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 201 Created
Content-Length: 206
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 7cb67bb7-4750-403d-cc2e-6bc44c52d52c
MS-RequestId: 312b044d-dc41-4b37-c2d5-7d27322d9654
Date: Tue, 14 Feb 2017 20:06:02 GMT

{
    "authenticationType": "federated",
    "capability": "email",
    "isDefault": false,
    "isInitial": false,
    "name": "Example.com",
    "status": "verified",
    "verificationMethod": "dns_record"
}
```
