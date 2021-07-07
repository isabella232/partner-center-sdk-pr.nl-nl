---
title: Informatiebronnen voor landen
description: Meer informatie over het Partner Center API's met landgegevensbronnen en beschrijvende metagegevens met betrekking tot een specifiek land of specifieke regio.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: caf56282d21df35ae9e179a98a37317f864117a3
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973822"
---
# <a name="country-information-resources-available-from-partner-center-apis"></a>Informatiebronnen voor landen die beschikbaar zijn Partner Center API's

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De volgende resources zijn beschrijvende metagegevens voor een land/regio.

## <a name="countryinformation"></a>CountryInformation

| Eigenschap                      | Type               | Beschrijving                                                                                        |
|-------------------------------|--------------------|----------------------------------------------------------------------------------------------------|
| ExtensionData                 | tekenreeks             | De extensiegegevens.                                                                                |
| Iso2Code                      | tekenreeks             | Een ISO-2-code.                                                                                     |
| Iso3Code                      | tekenreeks             | Een ISO-3-code.                                                                                     |
| DefaultWaarden                | tekenreeks             | De standaardcultuur.                                                                               |
| IsStateRequired               | booleaans            | Geeft aan of een staat/provincie vereist is.                                             |
| SupportedStatesList           | tekenreeksmatrix   | Als een staat/provincie vereist is, retourneert de volledige lijst voor dat land/de regio.                    |
| SupportedLanguagesList        | tekenreeksmatrix   | Een lijst met ondersteunde talen.                                                                     |
| SupportedCulturesList         | tekenreeksmatrix   | Een lijst met ondersteunde culturen.                                                                      |
| IsPostalCodeRequired          | booleaans            | Geeft aan of een postcode of postcode vereist is.                                    |
| PostalCodeRegex               | tekenreeks             | De reguliere expressie die de POSTCODE definieert.                                          |
| IsCityRequired                | booleaans            | Geeft aan of een stad vereist is of niet.                                                       |
| IsVatIdSupported              | booleaans            | Geeft aan of een btw-nummer vereist is.                                                     |
| TaxIdFormat                   | tekenreeks             | De btw-id-indeling.                                                                                 |
| TaxIdSample                   | tekenreeks             | Het belasting-id-voorbeeld.                                                                                 |
| VatIdRegex                    | tekenreeks             | De reguliere expressie van het belasting-id.                                                                     |
| PhoneNumberRegex              | tekenreeks             | De reguliere expressie van het telefoonnummer.                                                               |
| IsRegistrationNumberSupported | booleaans            | Geeft aan of een registratienummer wordt ondersteund of niet.                                       |
| IsTaxIdSupported              | booleaans            | Geeft aan of een belasting-id al dan niet wordt ondersteund. Dit is anders dan IsVatIdSupported. |
| ResellerAgreementRegion       | tekenreeks             | De regio van de resellerovereenkomst.                                                                     |
| GeographicRegion              | tekenreeks             | De geografische regio.                                                                             |
| CountryCallingCodesList       | tekenreeksmatrix   | De aanroepcodes die worden ondersteund in het land/de regio.                                                 |
| Kenmerken                    | ResourceAttributes | De metagegevenskenmerken die overeenkomen met de resource CountryInformation.                          |

## <a name="countryvalidationrules"></a>CountryValidationRules

Beschrijft de regels voor adresopmaak voor een land/regio.

| Eigenschap                | Type               | Beschrijving                                                                                        |
|-------------------------|--------------------|----------------------------------------------------------------------------------------------------|
| Iso2Code                | tekenreeks             | Een ISO-2-code.                                                                                     |
| DefaultWaarden          | tekenreeks             | De standaardcultuur.                                                                               |
| IsStateRequired         | booleaans            | Geeft aan of een staat/provincie vereist is.                                             |
| SupportedStatesList     | tekenreeksmatrix   | Als een staat/provincie vereist is, retourneert de volledige lijst voor dat land/de regio.                    |
| SupportedLanguagesList  | tekenreeksmatrix   | Een lijst met ondersteunde talen.                                                                     |
| SupportedCulturesList   | tekenreeksmatrix   | Een lijst met ondersteunde culturen.                                                                      |
| IsPostalCodeRequired    | booleaans            | Geeft aan of een postcode of postcode vereist is.                                    |
| PostalCodeRegex         | tekenreeks             | De reguliere expressie die de POSTCODE definieert.                                          |
| IsCityRequired          | booleaans            | Geeft aan of een stad vereist is of niet.                                                       |
| IsVatIdSupported        | booleaans            | Geeft aan of een btw-nummer vereist is.                                                     |
| TaxIdFormat             | tekenreeks             | De btw-id-indeling.                                                                                 |
| TaxIdSample             | tekenreeks             | Het belasting-id-voorbeeld.                                                                                 |
| VatIdRegex              | tekenreeks             | De reguliere expressie van het belasting-id.                                                                     |
| PhoneNumberRegex        | tekenreeks             | De reguliere expressie van het telefoonnummer.                                                               |
| IsTaxIdSupported        | booleaans            | Geeft aan of een belasting-id al dan niet wordt ondersteund. Deze eigenschap wijkt af van IsVatIdSupported. |
| IsTaxIdOptional         | booleaans            | Geeft aan of een btw-nummer optioneel is of niet.                                                     |
| CountryCallingCodesList | tekenreeksmatrix   | De aanroepcodes die worden ondersteund in het land/de regio.                                                 |
| Kenmerken              | ResourceAttributes | De metagegevenskenmerken die overeenkomen met de Resource CountryInformation.                          |
