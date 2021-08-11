---
title: Hulpprogramma-bronnen
description: De Partner Center REST API bevat veel resources die algemene gegevensmodellen beschrijven die in de SDK worden gebruikt.
ms.date: 03/30/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: de97feed13a4d0bae9743939a03f8cb8470f5f960bec0507cd9c5adfad287120
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115998039"
---
# <a name="utility-resources"></a>Hulpprogramma-bronnen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De Partner Center REST API bevat veel resources die algemene gegevensmodellen beschrijven die in de SDK worden gebruikt.

## <a name="address"></a>Adres

Het adres dat moet worden gebruikt voor de klant- of partnerprofielen. Zie Get [address formatting rules by market (Regels](get-market-specific-validation-data.md)voor adresopmaak op markt verkrijgen) voor meer informatie over de ondersteunde indelingen en eigenschappen in verschillende landen/regio's.

| Eigenschap     | Type   | Lengte (min. , max. ) | Description                                                                                      |
|--------------|--------|-------------------|--------------------------------------------------------------------------------------------------|
| AddressLine1 | tekenreeks | (1, 200)          | De eerste regel van het adres.                                                                   |
| AddressLine2 | tekenreeks | (0, 200)          | De tweede regel van het adres. Deze eigenschap is optioneel.                                       |
| Plaats         | tekenreeks | n.v.t.               | De plaats.                                                                                        |
| Staat        | tekenreeks | (0, 2)            | De status.                                                                                       |
| PostalCode   | tekenreeks | n.v.t.               | De postcode.                                                                     |
| Land/regio      | tekenreeks | (2, 2)            | Het land/de regio in de iso-landcodenotatie.                                                   |
| Region       | tekenreeks | n.v.t.               | De regio.                                                                                      |
| FirstName    | tekenreeks | (1, 50)           | De voornaam van een contactpersoon bij het bedrijf/de organisatie van de klant.                              |
| MiddleName   | tekenreeks | (1, 50)           | De middelste naam van een contactpersoon bij het bedrijf/de organisatie van de klant. Deze eigenschap is optioneel.  |
| LastName     | tekenreeks | (1, 50)           | De achternaam van een contactpersoon bij het bedrijf/de organisatie van de klant.                               |
| PhoneNumber  | tekenreeks | n.v.t.               | Het telefoonnummer van een contactpersoon bij het bedrijf/de organisatie van de klant. Deze eigenschap is optioneel.|
|PhoneNumber|tekenreeks|n.v.t.|Het telefoonnummer van een contactpersoon bij het bedrijf/de organisatie van de klant. In het klantprofiel is deze eigenschap verplicht voor het bedrijf/de organisatie van de klant die zich in de volgende landen bevindt: 100000000000000000000555(MD), Rusland(RU), Tstanikikik(TJ), Uzbekië (UZ), Finish (UA),India, Brazilië, Zuid-Afrika, Argentinië, Verenigde Arabische Republieken, Argentinië, Argentinië, Vietnam, Vietnam, South South En Vietnam. Anders is dit optioneel.|


## <a name="contact"></a>Contactpersoon

Beschrijft contactgegevens voor een specifieke persoon.

| Eigenschap    | Type   | Description                  |
|-------------|--------|------------------------------|
| FirstName   | tekenreeks | De voornaam van de contactpersoon.    |
| LastName    | tekenreeks | De achternaam van de contactpersoon.     |
| E-mail       | tekenreeks | Het e-mailadres van de contactpersoon. |
| PhoneNumber | tekenreeks | Het telefoonnummer van de contactpersoon.  |

## <a name="fieldfilter"></a>FieldFilter

Beschrijft een filter dat kan worden toegepast op zoekresultaten.

| Eigenschap | Type   | Description                                                                                                                                                                                        |
|----------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Operator | tekenreeks | De filteroperator: 'equals', \_ 'not equals', 'greater \_ than', 'greater \_ than or \_ \_ equals', 'less \_ than', 'less \_ than or \_ \_ equals', 'substring', 'and', 'or', 'starts \_ with', 'not \_ starts \_ with'. |

## <a name="fileinfo"></a>Fileinfo

Vertegenwoordigt een extern bestand dat is geüpload naar Partner Center.

| Eigenschap                 | Type   | Description                                   |
|--------------------------|--------|-----------------------------------------------|
| Opmerking                  | tekenreeks | Een opmerking die is gekoppeld aan het uploaden van het bestand.    |
| FileExtension            | tekenreeks | De bestandsextensie.                           |
| FileNameWithoutExtension | tekenreeks | De naam van het bestand, de extensie niet inbegrepen. |
| Bestandsgrootte                 | long   | De grootte van het bestand.                         |
| Id                       | tekenreeks | De unieke id voor het uploaden van het bestand.            |

## <a name="link"></a>Koppeling

Bevat een URI-koppeling en bijbehorende informatie.

| Eigenschap | Type                   | Description                        |
|----------|------------------------|------------------------------------|
| URI      | tekenreeks                 | De URI.                           |
| Methode   | tekenreeks                 | De methode die wordt vertegenwoordigd door de URI. |
| Kopteksten  | Matrix van KeyValuePairs | De headers voor de koppeling.          |

## <a name="passwordprofile"></a>PasswordProfile

Beschrijft een specifiek wachtwoord en of dat wachtwoord moet worden gewijzigd.

>[!NOTE]
>Niet ondersteund op Partner Center beheerd door 21Vianet.

| Eigenschap            | Type                          | Description                                                            |
|---------------------|-------------------------------|------------------------------------------------------------------------|
| Wachtwoord            | [SecureString](#securestring) | Het wachtwoord.                                                          |
| ForceChangePassword | booleaans                       | Hiermee bepaalt u of het wachtwoord gecimeerd moet worden gewijzigd bij de volgende aanmelding. |

## <a name="resourcelinks"></a>ResourceLinks

Bevat een lijst met koppelingen voor een resource.

| Eigenschap   | Type                                      | Description                                        |
|------------|-------------------------------------------|----------------------------------------------------|
| Zelf       | [Koppeling](#link)                             | De zelf-URI.                                      |
| Volgende       | [Koppeling](#link)                             | De volgende pagina met items.                            |
| Vorige   | [Koppeling](#link)                             | De vorige pagina met items.                        |
| Kenmerken | [ResourceAttributes](#resourceattributes) | De metagegevenskenmerken die overeenkomen met de gebruiker. |

## <a name="resourceattributes"></a>ResourceAttributes

Bevat kenmerkmetagegevens voor een resource.

| Eigenschap   | Type   | Description                                 |
|------------|--------|---------------------------------------------|
| Etag       | tekenreeks | De etag, ook wel bekend als de objectversie. |
| ObjectType | tekenreeks | Het type object van de basisresource.    |

## <a name="securestring"></a>SecureString

Slaat beveiligde informatie op, zoals een wachtwoord.

| Eigenschap | Type | Description                       |
|----------|------|-----------------------------------|
| Lengte   | int  | De lengte van de beveiligde tekenreeks. |

## <a name="validationcode"></a>ValidationCode

Vertegenwoordigt de validatiecode van Government Community Cloud partner.

| Eigenschap         | Type         | Description                                                              |
|------------------|--------------|--------------------------------------------------------------------------|
| PartnerId        | GUID         | Partner-id                                                       |
| OrganizationName | tekenreeks       | De organisatienaam die is opgegeven tijdens het validatieproces             |
| ValidationId     | int          | Een unieke id voor validatie                                       |
| MaxCreates       | nullable int | Het maximum aantal klanten dat mag worden gemaakt met deze validatiecode    |
| RemainingCreates | nullable int | Resterende klant maakt onder deze validatie-id                      |
| ETag             | tekenreeks       | De specifieke versie van deze resource. Wijzigingen wanneer de resource wordt gewijzigd. |
