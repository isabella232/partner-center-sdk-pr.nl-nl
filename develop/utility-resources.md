---
title: Hulpprogramma-bronnen
description: Het partner centrum REST API bevat veel resources die algemene gegevens modellen beschrijven die in de SDK worden gebruikt.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 115b0508f956c4b60e4db53193ef2585fa0c9a34
ms.sourcegitcommit: 204e518e794b6b076a17488ee9ca1aaaa4beaaec
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 04/01/2021
ms.locfileid: "106103977"
---
# <a name="utility-resources"></a>Hulpprogramma-bronnen

**Van toepassing op**

- Partnercentrum
- Partnercentrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Het partner centrum REST API bevat veel resources die algemene gegevens modellen beschrijven die in de SDK worden gebruikt.

## <a name="address"></a>Adres

Het adres dat moet worden gebruikt voor de klant-of partner profielen. Zie voor meer informatie over de ondersteunde indelingen en eigenschappen in verschillende landen/regio's de [regels voor adres opmaak ophalen per markt](get-market-specific-validation-data.md).

| Eigenschap     | Type   | Lengte (min., Max.) | Description                                                                                      |
|--------------|--------|-------------------|--------------------------------------------------------------------------------------------------|
| AddressLine1 | tekenreeks | (1, 200)          | De eerste regel van het adres.                                                                   |
| AddressLine2 | tekenreeks | (0, 200)          | De tweede regel van het adres. Deze eigenschap is optioneel.                                       |
| Plaats         | tekenreeks | n.v.t.               | De plaats.                                                                                        |
| Staat        | tekenreeks | (0, 2)            | De status.                                                                                       |
| PostalCode   | tekenreeks | n.v.t.               | De post code.                                                                     |
| Land/regio      | tekenreeks | (2, 2)            | Het land/de regio in de ISO-land nummer indeling.                                                   |
| Region       | tekenreeks | n.v.t.               | De regio.                                                                                      |
| FirstName    | tekenreeks | (1, 50)           | De voor naam van een contact persoon bij het bedrijf/de organisatie van de klant.                              |
| Middelste naam   | tekenreeks | (1, 50)           | De tweede naam van een contact persoon bij het bedrijf/de organisatie van de klant. Deze eigenschap is optioneel.  |
| LastName     | tekenreeks | (1, 50)           | De achternaam van een contact persoon bij het bedrijf/de organisatie van de klant.                               |
| PhoneNumber  | tekenreeks | n.v.t.               | Het telefoon nummer van een contact persoon bij het bedrijf/de organisatie van de klant. Deze eigenschap is optioneel.|
|PhoneNumber|tekenreeks|n.v.t.|Het telefoon nummer van een contact persoon bij het bedrijf/de organisatie van de klant. In klant profiel is deze eigenschap verplicht voor het bedrijf/de organisatie van de klant in de volgende landen: Armenië (AM), Azerbeidzjan (AZ), Belarus (op), Hongarije (HU), Kazachstan (KZ), Kirgizië (KG), Moldavië (MD), Rusland (RU), Tadzjikistan (TJ), Oezbekistan (UZ), Oekraïne (UA)), India, Brazilië, Zuid-Afrika, Polen, Verenigde Arabische Emiraten, Saoedi-Arabië, Zuid-Sudan en Venezuela. Anders is dit optioneel.|


## <a name="contact"></a>Contactpersoon

Hierin worden de contact gegevens voor een specifieke persoon beschreven.

| Eigenschap    | Type   | Description                  |
|-------------|--------|------------------------------|
| FirstName   | tekenreeks | De voor naam van de contact persoon.    |
| LastName    | tekenreeks | De achternaam van de contact persoon.     |
| E-mail       | tekenreeks | Het e-mail adres van de contact persoon. |
| PhoneNumber | tekenreeks | Het telefoon nummer van de contact persoon.  |

## <a name="fieldfilter"></a>FieldFilter

Beschrijft een filter dat kan worden toegepast op zoek resultaten.

| Eigenschap | Type   | Description                                                                                                                                                                                        |
|----------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operator | tekenreeks | De operator filter: ' is gelijk aan ', ' is niet \_ gelijk aan ', ' groter \_ dan ', ' groter dan \_ \_ of \_ gelijk aan ', ' kleiner dan ', ' \_ kleiner \_ dan \_ of \_ gelijk aan ', ' subtekenreeks ', ' en ', ' of ', ' begint \_ met ', ' \_ begint niet \_ met '. |

## <a name="fileinfo"></a>File info

Hiermee wordt een extern bestand aangeduid dat is geüpload naar het partner centrum.

| Eigenschap                 | Type   | Description                                   |
|--------------------------|--------|-----------------------------------------------|
| Opmerking                  | tekenreeks | Een opmerking bij het uploaden van het bestand.    |
| File Extension            | tekenreeks | De bestands extensie.                           |
| FileNameWithoutExtension | tekenreeks | De naam van het bestand, extensie niet opgenomen. |
| FileSize                 | long   | De grootte van het bestand.                         |
| Id                       | tekenreeks | De unieke ID voor het uploaden van het bestand.            |

## <a name="link"></a>Koppeling

Bevat een URI-koppeling en bijbehorende informatie.

| Eigenschap | Type                   | Description                        |
|----------|------------------------|------------------------------------|
| URI      | tekenreeks                 | De URI.                           |
| Methode   | tekenreeks                 | De methode die wordt vertegenwoordigd door de URI. |
| Kopteksten  | Matrix van KeyValuePairs | De kopteksten voor de koppeling.          |

## <a name="passwordprofile"></a>PasswordProfile

Beschrijft een specifiek wacht woord en als dat wacht woord moet worden gewijzigd.

>[!NOTE]
>Niet ondersteund in een partner centrum dat wordt beheerd door 21Vianet.

| Eigenschap            | Type                          | Description                                                            |
|---------------------|-------------------------------|------------------------------------------------------------------------|
| Wachtwoord            | [SecureString](#securestring) | Het wacht woord.                                                          |
| ForceChangePassword | booleaans                       | Hiermee wordt bepaald of het wacht woord bij de volgende aanmelding moet worden gewijzigd. |

## <a name="resourcelinks"></a>ResourceLinks

Bevat een lijst met koppelingen voor een resource.

| Eigenschap   | Type                                      | Description                                        |
|------------|-------------------------------------------|----------------------------------------------------|
| Zelf       | [Koppeling](#link)                             | De zelf-URI.                                      |
| Volgende       | [Koppeling](#link)                             | De volgende pagina met items.                            |
| Vorige   | [Koppeling](#link)                             | De vorige pagina met items.                        |
| Kenmerken | [ResourceAttributes](#resourceattributes) | De meta gegevens kenmerken die overeenkomen met de gebruiker. |

## <a name="resourceattributes"></a>ResourceAttributes

Bevat kenmerk-meta gegevens voor een resource.

| Eigenschap   | Type   | Description                                 |
|------------|--------|---------------------------------------------|
| ETAG       | tekenreeks | De ETAG, ook wel bekend als de object versie. |
| ObjectType | tekenreeks | Het type van het object van de basis resource.    |

## <a name="securestring"></a>SecureString

Slaat beveiligde informatie, zoals een wacht woord, op.

| Eigenschap | Type | Description                       |
|----------|------|-----------------------------------|
| Lengte   | int  | De lengte van de beveiligde teken reeks. |

## <a name="validationcode"></a>ValidationCode

Vertegenwoordigt de Cloud validatie code van de regering van een partner.

| Eigenschap         | Type         | Description                                                              |
|------------------|--------------|--------------------------------------------------------------------------|
| Partner        | GUID         | Partner-id                                                       |
| OrganizationName | tekenreeks       | De organisatie naam die tijdens het validatie proces is gegeven             |
| ValidationId     | int          | Een unieke id voor validatie                                       |
| MaxCreates       | nullable int | Het maximum aantal klanten dat met deze validatie code mag worden gemaakt    |
| RemainingCreates | nullable int | De resterende klant maakt onder deze validatie-ID                      |
| ETag             | tekenreeks       | De specifieke versie van deze resource. Verandert wanneer de resource wordt gewijzigd. |
