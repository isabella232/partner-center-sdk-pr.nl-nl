---
title: Indirecte reseller maken in Sandbox
description: Biedt informatie voor indirecte sandboxproviders over het inschakelen van end-to-end testen met behulp van API's.
ms.date: 5/24/2021
ms.author: vijvala
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 93e26792b66e447a0047bd550f4302c7fca4e87b
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973431"
---
# <a name="create-indirect-reseller-in-sandbox"></a>Indirecte reseller maken in Sandbox

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland

In dit document ziet u hoe u indirecte sandboxproviders maakt en end-to-end-tests inschakelen met behulp van API's.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.

## <a name="csp-indirect-provider"></a>CSP Indirect Provider

| Productiemogelijkheden             | Sandbox-mogelijkheden                            |
|-------------------------------------|-------------------------------------------------|
| Verkoopt via de indirecte reseller aan de eindklant | Ondersteund |
| Is eigenaar van alle verkopen, facturering, inrichting en beheer/ondersteuning | Ondersteund |
| Een samenwerking met de wederverkopers aanvragen | Ondersteund |
| Klanten weergeven per reseller | Ondersteund |
| Nieuwe klanten toevoegen per reseller | Ondersteund |
| Klanten uitnodigen | Aanvraag voor klantrelatie wordt niet ondersteund in Sandbox |
| Indirecte sandboxprovider kan sandbox-IR (MPN-id) selecteren als DEEMAN tijdens het plaatsen van de transactie | Ondersteund |
| Niet ondersteund in productie | Indirecte sandboxprovider kan indirecte sandbox-reseller maken |
| MpN-id voor sandbox moet worden ingevoerd. De MPN-id van het product werkt niet | Niet ondersteund in productie |
| Niet ondersteund in productie | Indirecte sandboxprovider kan indirecte sandbox-reseller verwijderen |

## <a name="sandbox-indirect-provider--create-sandbox-indirect-reseller"></a>Indirecte sandboxprovider : indirecte sandbox-reseller maken

Deze functie is alleen beschikbaar in de sandbox en biedt indirecte sandboxproviders de mogelijkheid om indirecte sandbox-resellers te maken.

1. Limiet van vijf indirecte sandbox-resellers die zijn toegestaan per indirecte sandboxprovider
2. Indirecte sandboxproviders kunnen klanten maken met `associatedPartnerId` van indirecte Sandbox-reseller
3. Voer de [MPN-id](/partner-center/mpn-create-a-partner-center-account) van een specifieke regio in tijdens het maken van een indirecte sandbox-reseller. Er kunnen meerdere indirecte sandbox-resellers worden gemaakt met dezelfde MPN-id voor sandboxs.
4. Slechts 75 klanten zijn toegestaan per indirecte sandboxprovider

## <a name="sandbox-indirect-resellers--view-customers"></a>Indirecte sandbox-resellers : klanten weergeven

1. Indirecte sandbox-resellers kunnen de lijst met sandbox-klanten weergeven op indirecte Sandbox-providers.
2. Indirecte resellers in sandbox kunnen het klantaccount beheren met behulp van gedelegeerde beheerdersmachtigingen.

## <a name="create-sandbox-indirect-reseller-through-api"></a>Indirecte sandbox-reseller maken via API

### <a name="rest-request"></a>REST-aanvraag

#### <a name="request-syntax"></a>Aanvraagsyntaxis

| **Methode** | **Aanvraag-URI**                                                        |
|------------|------------------------------------------------------------------------|
| **Verzenden**   | [*{baseURL}*](partner-center-rest-urls.md)/v1 sandboxIndirectReseller |

#### <a name="request-headers"></a>Aanvraagheaders

- Deze API is idempotent (deze levert geen ander resultaat op als u deze meerdere keren aanroept).
- Een aanvraag-id en correlatie-id zijn vereist.
- Zie REST-headers Partner Center [meer informatie.](headers.md)

#### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.

| Eigenschap             | Type           | Beschrijving                                      |
|----------------------|----------------|--------------------------------------------------|
| mpnId                | tekenreeks         | De MPN-id voor de IR in een specifieke regio         |
| tenant               | &lt;Woordenlijstreeks, tekenreeks&gt; | Verzameling basisinformatie die een account definieert dat moet worden gemaakt |
| legalBusinessProfile | &lt;Woordenlijstreeks, tekenreeks&gt; | Verzameling informatie die de juridische bedrijfsentiteit vertegenwoordigt, zoals contactpersoon, adres en naam |
| organizationProfileLanguage | &lt;Woordenlijstreeks, tekenreeks&gt; | De taal-id van de organisatie |

In deze tabel worden de vereiste eigenschappen in het **tenantkenmerk** beschreven.

| Eigenschap           | Type           | Beschrijving                         |
|--------------------|----------------|-------------------------------------|
| domainPrefix       | Tekenreeks; Unieke | Domein voor het tenantaccount       |
| naam               | tekenreeks         | Gebruiksvriendelijke naam van de tenant         |
| displayName        | tekenreeks         | Weergavenaam voor het account        |
| adminUserName      | tekenreeks         | Gebruikersnaam voor het account voor aanmelding |
| adminfirstname     | tekenreeks         | Voornaam voor de gebruiker met beheerdersrechten       |
| adminlastname      | tekenreeks         | Achternaam voor de gebruiker met beheerdersrechten        |
| adminAlernateEmail | tekenreeks         | e-mailadres voor de gebruiker met beheerdersrechten            |
| country            | tekenreeks         | Land van het account              |
| Cultuur            | tekenreeks         | Taalvoorkeur voor account     |

In deze tabel worden de vereiste eigenschappen in het **kenmerk legalBusinessProfile** beschreven.

| Eigenschap       | Type                             | Beschrijving                          |
|----------------|----------------------------------|--------------------------------------|
| companyName    | tekenreeks                           | Bedrijfsnaam voor juridische entiteit        |
| adres        | &lt;Woordenlijstreeks, tekenreeks&gt; | Adres van de locatie van de juridische entiteit |
| primaryContact | &lt;Woordenlijstreeks, tekenreeks&gt; | Contactgegevens van het bedrijf       |
| Cultuur        | tekenreeks                           | Taal die de voorkeur heeft van het bedrijf    |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
{
    "mpnId": "6363276",
    "tenant": {
        "domainPrefix": "TipIRIntTest705",
        "name": "TipIRIntTest705",
        "displayName": "TipIRIntTest705",
        "adminUserName": "admin",
        "adminFirstName": "TipIRIntTest705",
        "adminLastName": "TipIRIntTest705",
        "adminAlternateEmail": "TipIRIntTest705@test.com",
        "country": "US",
        "culture": "en-us"
    },
    "legalBusinessProfile": {
        "companyName": "TipIRIntTest705",
        "address": {
            "country": "FR",
            "city": "Issy-les-Moulineaux",
            "state": "",
            "addressLine1": "39-41 quai du Président Roosevelt",
            "addressLine2": "",
            "postalCode": "92130"
        },
        "primaryContact": {
            "firstName": "Sandbox",
            "lastName": "Scenario",
            "email": "Sandbox.Scenario@test.com",
            "phoneNumber": "1234567890"
        },
        "culture": "en-US"
    },
    "organizationProfileLanguage": "en"
}
```

### <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode de ingevulde Sandbox IR-resource in de antwoord-body.

```http
{

    "accountId": "6f94b119-793c-44c7-862b-c327c9057eab",
    "mpnId": "6363276",
    "tenant": {
        "id": "6f94b119-793c-44c7-862b-c327c9057eab",
        "adminUserAccount": "admin@TipIRIntTest705.onmicrosoft.com",
        "password": "\*\*\*\*\*\*”
    },
    "agreementSignature": {
        "id": "30ac23e7-e200-42cf-a5bc-dd9148cdc632",
        "accountId": "6f94b119-793c-44c7-862b-c327c9057eab",
        "agreementId": "1e18c5b2-e42a-4b84-82c8-d0155aa94c6e",
        "agreementType": "ValueAddedReseller",
        "dateSigned": "2021-02-23T18:10:14.8461137Z",
        "signedByFirstName": "Test123@PLAMUATT2NetNewTip.onmicrosoft.com",
        "signedByUserPrincipalName": "Test123@PLAMUATT2NetNewTip.onmicrosoft.com",
        "signedByUserObjectId": "e6e0c29d-acda-4ef2-b370-d37a4e06fb98",
        "signedByUserTenantId": "0e195b37-4574-4539-bc42-0e539b9684c0",
        "attributes": {
            "objectType": "AgreementSignatureResponse"
        }
    },
    "partnerRelationship": {
        "id": "0e195b37-4574-4539-bc42-0e539b9684c0",
        "name": "PLAMUATT2NetNew",
        "relationshipType": "is\_indirect\_reseller\_of",
        "state": "Active",
        "mpnId": "6363276",
        "attributes": {
            "objectType": "PartnerRelationshipResponse"
        }
    }
}
```
