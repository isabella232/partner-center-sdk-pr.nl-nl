---
title: Klantbronnen
description: Klantbronnen die een klant of wederverkoper vertegenwoordigen.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 7d76de33c9a0d28e9d3fb0b0821cbd37ad67e7af
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973142"
---
# <a name="customer-resources"></a>Klantbronnen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

## <a name="customer"></a>Klant

De **klantresource** vertegenwoordigt een klant of reseller. In het algemeen kan een klantresource elke persoon, werknemer of organisatie zijn die zaken wil doen met Microsoft en de wederverkopers van Microsoft. Klanten hebben ook een bedrijfsprofiel en een factureringsprofiel.

>[!NOTE]
>De **resource Klant** heeft een snelheidslimiet van 500 aanvragen per minuut per tenant-id.

| Eigenschap              | Type                                                             | Beschrijving                                                                                                                                  |
|-----------------------|------------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks                                                           | De klant-id.                                                                                                                             |
| commerceId            | tekenreeks                                                           | De handels-id.                                                                                                                             |
| companyProfile        | [CustomerCompanyProfile](#customercompanyprofile)                | Aanvullende informatie over het bedrijf of de organisatie.                                                                                    |
| billingProfile        | [CustomerBillingProfile](#customerbillingprofile)                | Aanvullende informatie die wordt gebruikt voor facturering.                                                                                                     |
| relationshipToPartner | tekenreeks                                                           | Definieert het licentieprogramma dat de partner voor deze klant gebruikt: 'geen', 'reseller', 'advisor', 'syndication' of 'microsoft \_ support'. |
| allowDelegatedAccess  | booleaans                                                          | Geeft aan of aan de partner gedelegeerde beheerdersbevoegdheden zijn verleend door deze klant. Deze eigenschap is alleen beschikbaar wanneer een klant wordt op id, niet per lijst.                                                         |
| userCredentials       | [UserCredentials](user-resources.md#usercredentials) | De gebruikersreferenties.                                                                                                                        |
| customDomains         | tekenreeksmatrix                                                 | Lijst met aangepaste domeinen van een klant.                                                                                                        |
| associatedPartnerId   | tekenreeks                                                           | De indirecte reseller die is gekoppeld aan dit klantaccount. Deze waarde kan alleen worden ingesteld door indirecte CSP-partners.                              |
| Verwijzigingen                 | [ResourceLinks](utility-resources.md#resourcelinks)             | De resourcekoppelingen in het profiel.                                                                                             |
| kenmerken            | [ResourceAttributes](utility-resources.md#resourceattributes)   | De metagegevenskenmerken die overeenkomen met het profiel.                                                                                        |

## <a name="customercompanyprofile"></a>CustomerCompanyProfile

De **resource CustomerCompanyProfile** is aanvullende informatie over het bedrijf of de organisatie.

| Eigenschap    | Type                                                           | Beschrijving                                                                       |
|-------------|----------------------------------------------------------------|-----------------------------------------------------------------------------------|
| tenantId    | tekenreeks                                                         | De tenant-id van de klant voor Azure AD. Dit wordt ook wel een MicrosoftID genoemd. |
| domein      | tekenreeks                                                         | De naam van de klant, zoals contoso.onmicrosoft.com.                             |
| companyName | tekenreeks                                                         | De naam van het bedrijf of de organisatie.                                          |
| Verwijzigingen       | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen in het profiel.                                  |
| kenmerken  | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met het profiel.                             |
|organizationRegistrationNumber|Tekenreeks|Het registratienummer van de organisatie van de klant (ook wel INN-nummer genoemd in bepaalde landen). Alleen vereist voor het bedrijf/de organisatie van de klant die zich in de volgende landen bevindt: 10000000000000. Voor het bedrijf/de organisatie van de klant die zich in andere landen bevindt, moet dit niet worden opgegeven.|


## <a name="customerbillingprofile"></a>CustomerBillingProfile

De **CustomerBillingProfile-resource** is aanvullende informatie die wordt gebruikt om de klant te factureren.

| Eigenschap       | Type                                                           | Beschrijving                                                                                                                                            |
|----------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| id             | tekenreeks                                                         | De profiel-id.                                                                                                                                |
| voornaam      | tekenreeks                                                         | De voornaam van de contactpersoon voor facturering bij het bedrijf van de klant. Dit is de persoon naar wie facturen en andere factureringscommunicatie wordt doorgestuurd. |
| achternaam       | tekenreeks                                                         | De achternaam van de contactpersoon voor facturering.                                                                                                                  |
| e-mail          | tekenreeks                                                         | Het e-mailadres van de contactpersoon voor facturering                                                                                                                    |
| Cultuur        | tekenreeks                                                         | Hun voorkeurscultuur voor communicatie en valuta, zoals 'en-us'.                                                                               |
| language       | tekenreeks                                                         | Hun voorkeurstaal voor communicatie.                                                                                                            |
| companyName    | tekenreeks                                                         | De naam van het bedrijf of de organisatie.                                                                                                               |
| defaultAddress | [Adres](utility-resources.md#address)                       | Het adres waar de factuur naar wordt verzonden, waar de contactpersoon voor facturering werkt.                                                                                   |
| Verwijzigingen          | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen in het profiel.                                                                                                       |
| kenmerken     | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met het profiel.                                                                                                  |

## <a name="customerrelationshiprequest"></a>CustomerRelationshipRequest

De **Resource CustomerRelationshipRequest bevat** de URL die door de klant wordt gebruikt om een resellerrelatie met een partner tot stand te stellen.

| Eigenschap   | Type                                                           | Beschrijving                                                              |
|------------|----------------------------------------------------------------|--------------------------------------------------------------------------|
| url        | tekenreeks                                                         | De URL die door de klant wordt gebruikt om een relatie met een partner tot stand te stellen. |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met de relatieaanvraag.       |