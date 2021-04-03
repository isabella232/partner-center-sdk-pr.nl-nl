---
title: Klant resources
description: Klant bronnen die een klant of wederverkoper vertegenwoordigen.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 78622258880ab77ca99eae98082cc66acb3b66a7
ms.sourcegitcommit: 204e518e794b6b076a17488ee9ca1aaaa4beaaec
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/01/2021
ms.locfileid: "106103960"
---
# <a name="customer-resources"></a>Klant resources

**Van toepassing op:**

- Partnercentrum
- Partnercentrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

## <a name="customer"></a>Klant

De resource van de **klant** vertegenwoordigt een klant of wederverkoper. In het algemeen kan een klant resource iedereen, werk nemer of organisatie zijn die zaken wil doen met micro soft en de wederverkopers van micro soft. Klanten hebben ook een bedrijfs profiel en een facturerings profiel.

>[!NOTE]
>De resource van de **klant** heeft een frequentie limiet van 500 aanvragen per minuut per Tenant-id.

| Eigenschap              | Type                                                             | Beschrijving                                                                                                                                  |
|-----------------------|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks                                                           | De klant-ID.                                                                                                                             |
| commerceId            | tekenreeks                                                           | De commerce-ID.                                                                                                                             |
| companyProfile        | [CustomerCompanyProfile](#customercompanyprofile)                | Aanvullende informatie over het bedrijf of de organisatie.                                                                                    |
| billingProfile        | [CustomerBillingProfile](#customerbillingprofile)                | Aanvullende informatie die wordt gebruikt voor facturering.                                                                                                     |
| relationshipToPartner | tekenreeks                                                           | Hiermee wordt het licentie programma gedefinieerd dat de partner gebruikt voor deze klant: ' none ', ' wederverkoper ', ' Advisor ', ' Syndication ' of ' micro soft- \_ ondersteuning '. |
| allowDelegatedAccess  | booleaans                                                          | Hiermee wordt aangegeven of aan de partner gedelegeerde beheerders bevoegdheden zijn toegekend door deze klant. Deze eigenschap is alleen beschikbaar wanneer een klant wordt opgehaald op basis van ID, niet op lijst.                                                         |
| userCredentials       | [UserCredentials](user-resources.md#usercredentials) | De gebruikers referenties.                                                                                                                        |
| customDomains         | tekenreeksmatrix                                                 | Lijst met aangepaste domeinen van een klant.                                                                                                        |
| associatedPartnerId   | tekenreeks                                                           | De indirecte wederverkoper die aan dit klant account is gekoppeld. Deze waarde kan alleen worden ingesteld door de indirecte CSP-partners.                              |
| koppelen                 | [ResourceLinks](utility-resources.md#resourcelinks)             | De resource koppelingen in het profiel.                                                                                             |
| kenmerken            | [ResourceAttributes](utility-resources.md#resourceattributes)   | De meta gegevens kenmerken die overeenkomen met het profiel.                                                                                        |

## <a name="customercompanyprofile"></a>CustomerCompanyProfile

De **CustomerCompanyProfile** -resource is aanvullende informatie over het bedrijf of de organisatie.

| Eigenschap    | Type                                                           | Description                                                                       |
|-------------|----------------------------------------------------------------|-----------------------------------------------------------------------------------|
| tenantId    | tekenreeks                                                         | De Tenant-id van de klant voor Azure AD. Dit wordt ook wel een MicrosoftID genoemd. |
| domein      | tekenreeks                                                         | De naam van de klant, zoals contoso.onmicrosoft.com.                             |
| companyName | tekenreeks                                                         | De naam van het bedrijf of de organisatie.                                          |
| koppelen       | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen in het profiel.                                  |
| kenmerken  | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met het profiel.                             |
|organizationRegistrationNumber|Tekenreeks|Het registratie nummer van de klant (ook wel INN-nummer genoemd in bepaalde landen). Alleen vereist voor het bedrijf/de organisatie van de klant in de volgende landen: Armenië (AM), Azerbeidzjan (AZ), Belarus (op), Hongarije (HU), Kazachstan (KZ), Kirgizië (KG), Moldavië (MD), Rusland (RU), Tadzjikistan (TJ), Oezbekistan (UZ), Oekraïne (UA), India, Brazilië, Zuid-Afrika, Polen, Verenigde Arabische Emiraten, Saoedi-Arabië, Turkije, Thai, Vietnam, Myanmar, Irak, Zuid-Soedan en Venezuela. Voor het bedrijf/de organisatie van de klant die zich in andere landen bevindt, moet dit niet worden opgegeven.|


## <a name="customerbillingprofile"></a>CustomerBillingProfile

De **CustomerBillingProfile** -resource is aanvullende informatie die wordt gebruikt om de klant te factureren.

| Eigenschap       | Type                                                           | Beschrijving                                                                                                                                            |
|----------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| id             | tekenreeks                                                         | De profiel-id.                                                                                                                                |
| voornaam      | tekenreeks                                                         | De voor naam van de facturerings contactpersoon van het bedrijf van de klant. Dit is de persoon aan wie facturen en andere facturerings communicatie worden omgeleid. |
| achternaam       | tekenreeks                                                         | De achternaam van de facturerings contactpersoon.                                                                                                                  |
| e-mail          | tekenreeks                                                         | Het e-mail adres van de contact persoon voor facturering                                                                                                                    |
| culturele        | tekenreeks                                                         | De voorkeurs cultuur voor communicatie en valuta, zoals ' en-us '.                                                                               |
| language       | tekenreeks                                                         | De voorkeurs taal voor communicatie.                                                                                                            |
| companyName    | tekenreeks                                                         | De naam van het bedrijf of de organisatie.                                                                                                               |
| defaultAddress | [Adres](utility-resources.md#address)                       | Het adres waarnaar facturen worden verzonden, waarbij de contact persoon van de facturering werkt.                                                                                   |
| koppelen          | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen in het profiel.                                                                                                       |
| kenmerken     | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met het profiel.                                                                                                  |

## <a name="customerrelationshiprequest"></a>CustomerRelationshipRequest

De **CustomerRelationshipRequest** -resource bevat de URL die door de klant wordt gebruikt om een reseller-relatie met een partner tot stand te brengen.

| Eigenschap   | Type                                                           | Description                                                              |
|------------|----------------------------------------------------------------|--------------------------------------------------------------------------|
| url        | tekenreeks                                                         | De URL die door de klant wordt gebruikt om een relatie met een partner tot stand te brengen. |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met de relatie aanvraag.       |