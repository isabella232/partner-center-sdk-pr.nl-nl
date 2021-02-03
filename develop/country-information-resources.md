---
title: Informatie bronnen over het land
description: Meer informatie over het gebruik van partner centrum-Api's met informatie bronnen van het land en beschrijvende meta gegevens die betrekking hebben op een bepaald land of bepaalde regio.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ba0974cf736ff86038f8abf9c77d6a648984d1df
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767641"
---
# <a name="country-information-resources-available-from-partner-center-apis"></a>Land informatie bronnen die beschikbaar zijn via partner Center-Api's

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De volgende resources zijn beschrijvende meta gegevens voor een land/regio.

## <a name="countryinformation"></a>CountryInformation

| Eigenschap                      | Type               | Description                                                                                        |
|-------------------------------|--------------------|----------------------------------------------------------------------------------------------------|
| ExtensionData                 | tekenreeks             | De gegevens van de extensie.                                                                                |
| Iso2Code                      | tekenreeks             | Een ISO-2-code.                                                                                     |
| Iso3Code                      | tekenreeks             | Een ISO-3-code.                                                                                     |
| DefaultCulture                | tekenreeks             | De standaard cultuur.                                                                               |
| IsStateRequired               | booleaans            | Hiermee wordt aangegeven of een staat/provincie vereist is of niet.                                             |
| SupportedStatesList           | tekenreeksmatrix   | Als een staat/provincie vereist is, retourneert de volledige lijst voor dat land of deze regio.                    |
| SupportedLanguagesList        | tekenreeksmatrix   | Een lijst met ondersteunde talen.                                                                     |
| SupportedCulturesList         | tekenreeksmatrix   | Een lijst met ondersteunde cult uren.                                                                      |
| IsPostalCodeRequired          | booleaans            | Hiermee geeft u op of een post code of post code vereist is of niet.                                    |
| PostalCodeRegex               | tekenreeks             | De reguliere expressie die de post code definieert.                                          |
| IsCityRequired                | booleaans            | Hiermee wordt aangegeven of een stad vereist is of niet.                                                       |
| IsVatIdSupported              | booleaans            | Hiermee wordt aangegeven of een BTW-ID vereist is of niet.                                                     |
| TaxIdFormat                   | tekenreeks             | De indeling van de BTW-ID.                                                                                 |
| TaxIdSample                   | tekenreeks             | Het BTW-ID-voor beeld.                                                                                 |
| VatIdRegex                    | tekenreeks             | De reguliere expressie voor BTW-identificatie.                                                                     |
| PhoneNumberRegex              | tekenreeks             | De reguliere expressie voor het telefoon nummer.                                                               |
| IsRegistrationNumberSupported | booleaans            | Hiermee wordt aangegeven of een registratie nummer wordt ondersteund.                                       |
| IsTaxIdSupported              | booleaans            | Hiermee wordt aangegeven of een BTW-ID wordt ondersteund. Dit wijkt af van IsVatIdSupported. |
| ResellerAgreementRegion       | tekenreeks             | De wederverkoper-overeenkomst regio.                                                                     |
| GeographicRegion              | tekenreeks             | De geografische regio.                                                                             |
| CountryCallingCodesList       | tekenreeksmatrix   | De aanroepende codes die worden ondersteund in het land/de regio.                                                 |
| Kenmerken                    | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de CountryInformation-resource.                          |

## <a name="countryvalidationrules"></a>CountryValidationRules

Hierin worden de adres notatie regels voor een land/regio beschreven.

| Eigenschap                | Type               | Description                                                                                        |
|-------------------------|--------------------|----------------------------------------------------------------------------------------------------|
| Iso2Code                | tekenreeks             | Een ISO-2-code.                                                                                     |
| DefaultCulture          | tekenreeks             | De standaard cultuur.                                                                               |
| IsStateRequired         | booleaans            | Hiermee wordt aangegeven of een staat/provincie vereist is of niet.                                             |
| SupportedStatesList     | tekenreeksmatrix   | Als een staat/provincie vereist is, retourneert de volledige lijst voor dat land of deze regio.                    |
| SupportedLanguagesList  | tekenreeksmatrix   | Een lijst met ondersteunde talen.                                                                     |
| SupportedCulturesList   | tekenreeksmatrix   | Een lijst met ondersteunde cult uren.                                                                      |
| IsPostalCodeRequired    | booleaans            | Hiermee geeft u op of een post code of post code vereist is of niet.                                    |
| PostalCodeRegex         | tekenreeks             | De reguliere expressie die de post code definieert.                                          |
| IsCityRequired          | booleaans            | Hiermee wordt aangegeven of een stad vereist is of niet.                                                       |
| IsVatIdSupported        | booleaans            | Hiermee wordt aangegeven of een BTW-ID vereist is of niet.                                                     |
| TaxIdFormat             | tekenreeks             | De indeling van de BTW-ID.                                                                                 |
| TaxIdSample             | tekenreeks             | Het BTW-ID-voor beeld.                                                                                 |
| VatIdRegex              | tekenreeks             | De reguliere expressie voor BTW-identificatie.                                                                     |
| PhoneNumberRegex        | tekenreeks             | De reguliere expressie voor het telefoon nummer.                                                               |
| IsTaxIdSupported        | booleaans            | Hiermee wordt aangegeven of een BTW-ID wordt ondersteund. Deze eigenschap wijkt af van de IsVatIdSupported. |
| IsTaxIdOptional         | booleaans            | Hiermee wordt aangegeven of een BTW-ID optioneel is of niet.                                                     |
| CountryCallingCodesList | tekenreeksmatrix   | De aanroepende codes die worden ondersteund in het land/de regio.                                                 |
| Kenmerken              | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de CountryInformation-resource.                          |
