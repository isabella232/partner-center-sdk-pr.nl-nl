---
title: Een geverifieerd domein voor een klant toevoegen
description: Meer informatie over het toevoegen van een geverifieerd domein aan de lijst met goedgekeurde domeinen voor een klant in Partner Center. Doe dit met behulp Partner Center API's en REST API's.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 570008c955ce3242b02c1df4c87df52aea3627abb6c86a069cc7c4c0d1d6f799
ms.sourcegitcommit: ac8f5f8bedaddba5110dd4e562fbd9a2b24837df
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/08/2021
ms.locfileid: "116885574"
---
# <a name="add-a-verified-domain-to-the-list-of-approved-domains-for-an-existing-customer"></a>Een geverifieerd domein toevoegen aan de lijst met goedgekeurde domeinen voor een bestaande klant 

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Een geverifieerd domein toevoegen aan de lijst met goedgekeurde domeinen voor een bestaande klant.

## <a name="prerequisites"></a>Vereisten

- U moet een partner zijn die een domeinregistrar is.

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="adding-a-verified-domain"></a>Een geverifieerd domein toevoegen

Als u een partner bent die een domeinregistrar is, kunt u de API gebruiken om een nieuwe domeinresource te plaatsen in de lijst met domeinen `verifieddomain` voor een bestaande klant. [](#domain) Als u dit wilt doen, identificeert u de klant met behulp van de CustomerTenantId. Geef een waarde op voor de eigenschap VerifiedDomainName. Geef een [domeinresource](#domain) door in de aanvraag met de vereiste eigenschappen Name, Capability, AuthenticationType, Status en VerificationMethod. Als u wilt opgeven dat het nieuwe domein een federatief [](#domain) domein [is,](#domain) stelt u de eigenschap AuthenticationType in de domeinresource in op en bevat u een `Federated` [DomainFederationSettings-resource](#domain-federation-settings) in de aanvraag. Als de methode is geslaagd, bevat het antwoord een [domeinresource](#domain) voor het nieuwe geverifieerde domein.

### <a name="custom-verified-domains"></a>Aangepaste geverifieerde domeinen

Wanneer u een aangepast geverifieerd domein toevoegt, een domein dat niet is geregistreerd op **onmicrosoft.com,** moet u de eigenschap [CustomerUser.immutableId](user-resources.md#customeruser) instellen op een unieke id-waarde voor de klant voor wie u het domein toevoegt. Deze unieke id is vereist tijdens het validatieproces wanneer het domein wordt geverifieerd. Zie Gebruikersaccounts maken voor een klant voor meer informatie [over gebruikersaccounts van klanten.](create-user-accounts-for-a-customer.md)

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| POST   | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{CustomerTenantId}/verifieddomain HTTP/1.1 |

#### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de klant op te geven voor wie u een geverifieerd domein toevoegt.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| CustomerTenantId | guid | J        | De waarde is een MET GUID **opgemaakte CustomerTenantId** waarmee u een klant kunt opgeven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.

| Naam                                                  | Type   | Vereist                                      | Beschrijving                                                |
|-------------------------------------------------------|--------|-----------------------------------------------|--------------------------------------------------------|
| VerifiedDomainName                                    | tekenreeks | Yes                                           | De geverifieerde domeinnaam. |
| [Domein](#domain)                                     | object | Yes                                           | Bevat de domeingegevens. |
| [DomainFederationSettings](#domain-federation-settings) | object | Ja (Als AuthenticationType = `Federated` )     | De federatie-instellingen voor het domein die moeten worden gebruikt als het domein een domein is `Federated` en geen `Managed` domein. |

### <a name="domain"></a>Domain

In deze tabel worden de vereiste en optionele **domeineigenschappen** in de aanvraag body beschreven.

| Naam               | Type                                     | Vereist | Beschrijving                                                                                                                                                                                                     |
|--------------------|------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| AuthenticationType                                    | tekenreeks           | Yes      | Hiermee definieert u of het domein een `Managed` domein of een domein `Federated` is. Ondersteunde waarden: `Managed` , `Federated` .|
| Mogelijkheid                                            | tekenreeks           | Yes      | Hiermee geeft u de domeinmogelijkheid. Bijvoorbeeld `Email`.                  |
| IsDefault                                             | booleaanse waarde null-waarde | No       | Geeft aan of het domein het standaarddomein voor de tenant is. Ondersteunde waarden: `True` , `False` , `Null` .        |
| IsInitial                                             | booleaanse waarde null-waarde | No       | Geeft aan of het domein een eerste domein is. Ondersteunde waarden: `True` , `False` , `Null` .                       |
| Name                                                  | tekenreeks           | Yes      | De domeinnaam.                                                          |
| RootDomain                                            | tekenreeks           | No       | De naam van het hoofddomein.                                              |
| Status                                                | tekenreeks           | Yes      | De domeinstatus. Bijvoorbeeld `Verified`. Ondersteunde waarden:  `Unverified` , `Verified` , `PendingDeletion` .                               |
| VerificationMethod                                    | tekenreeks           | Yes      | Het type domeinverificatiemethode. Ondersteunde waarden: `None` , `DnsRecord` , `Email` .                                    |

### <a name="domain-federation-settings"></a>Federatie-instellingen voor domein

In deze tabel worden de vereiste en **optionele eigenschappen DomainFederationSettings** in de aanvraag body beschreven.

| Naam   | Type   | Vereist | Beschrijving                                                  |
|--------|--------|----------|--------------------------------------------------------------|
| ActiveLogOnUri                         | tekenreeks           | No      | De aanmeldings-URI die wordt gebruikt door uitgebreide clients. Deze eigenschap is de STS-auth-URL van de partner. |
| DefaultInteractiveAuthenticationMethod | tekenreeks           | No      | Hiermee wordt de standaardverificatiemethode aangegeven die moet worden gebruikt wanneer een toepassing vereist dat de gebruiker interactieve aanmelding heeft. |
| FederationBrandName                    | tekenreeks           | No      | De naam van het federatief merk.        |
| IssuerUri                              | tekenreeks           | Yes     | De naam van de vergever van de certificaten.                        |
| LogOffUri                              | tekenreeks           | Yes     | De aanmeldings-URI. Deze eigenschap beschrijft de URI voor het uitloggen van federatief domein.        |
| MetadataExchangeUri                    | tekenreeks           | No      | De URL die het exchange-eindpunt voor metagegevens specificeert dat wordt gebruikt voor verificatie van uitgebreide clienttoepassingen. |
| NextSigningCertificate                 | tekenreeks           | No      | Het certificaat dat wordt gebruikt voor de komende toekomst door de ADFS V2 STS voor het ondertekenen van claims. Deze eigenschap is een base64-gecodeerde weergave van het certificaat. |
| OpenIdConnectDiscoveryEndpoint         | tekenreeks           | No      | De OpenID Verbinding maken detectie-eindpunt van de federatieve IDP STS. |
| PassiveLogOnUri                        | tekenreeks           | Yes     | De aanmeldings-URI die wordt gebruikt door oudere passieve clients. Deze eigenschap is het adres voor het verzenden van federatief aanmeldingsaanvragen. |
| PreferredAuthenticationProtocol        | tekenreeks           | Yes     | De indeling voor het verificatie-token. Bijvoorbeeld `WsFed`. Ondersteunde waarden: `WsFed` , `Samlp` |
| PromptLoginBehavior                    | tekenreeks           | Yes     | Het type aanmeldingsgedrag bij de prompt.  Bijvoorbeeld `TranslateToFreshPasswordAuth`. Ondersteunde waarden: `TranslateToFreshPasswordAuth` , `NativeSupport` , `Disabled` |
| SigningCertificate                     | tekenreeks           | Yes     | Het certificaat dat momenteel wordt gebruikt door de ADFS V2 STS om claims te ondertekenen. Deze eigenschap is een base64-gecodeerde weergave van het certificaat. |
| SigningCertificateUpdateStatus         | tekenreeks           | No      | Hiermee wordt de updatestatus van het handtekeningcertificaat aangegeven. |
| SigningCertificateUpdateStatus         | booleaanse waarde null-waarde | No      | Geeft aan of de IDP STS MFA ondersteunt. Ondersteunde waarden: `True` , `False` , `Null` .|

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

Als dit lukt, retourneert deze API een [domeinresource](#domain) voor het nieuwe geverifieerde domein.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
