---
title: Ondersteunde talen en landinstellingen voor Partnercentrum
description: Lijst met ondersteunde land instellingen voor ISO2 en ISO3 voor partner centrum.
ms.date: 12/03/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 5f428bf9104fec3e4855706e8786ad3941875f3d
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767346"
---
# <a name="partner-center-supported-languages-and-locales"></a>Ondersteunde talen en landinstellingen voor Partnercentrum

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Sommige partner Center-Api's vereisen een waarde die een land instelling, land of regio aangeeft. Het [partner centrum voor de rest header](headers.md) X-locale vereist bijvoorbeeld een waarde vaak in de notatie ' taal-land ' (' nl-nl ' geeft ' English-Verenigde Staten ' aan).

In de door Partner Center beheerde Api's, de klasse [CountryValidationRules/DotNet/API/micro soft. Store. partnercenter. Models. CountryValidationRules. CountryValidationRules) en [OfferCategory. land instelling/DotNet/API/Microsoft. Store. partnercenter. Models. aanbiedingen. OfferCategory. land instelling), [ServiceRequest. CountryCode/DotNet/API/Microsoft. Store. partnercenter. Models. servicerequests. ServiceRequest. countrycode) of de eigenschappen [CustomerBillingProfile. Culture/DotNet/API/micro soft. Store. partnercenter. Models. klanten. CustomerBillingProfile. Culture) vereisen teken reeks waarden die een taal of land/regio aangeven (in de vorm van een ISO2-taal code of ISO3 land-/regiocode), een land instelling of een cultuur (een taal-ID gecombineerd met een land-/regionummer)

De volgende tabel geeft een lijst van de cultuur en ISO-land codes (International Standards Organization) die worden ondersteund in de partner centrum-Api's.

| Land/regio                           | ISO alpha 2-land code | ISO Alpha 3-land code | Ondersteunde cultuur (s)                  |
|------------------------------------------|--------------------------|--------------------------|---------------------------------------|
| Afghanistan                              | AF                       | AFG                      | PS-AF/en-US                         |
| Åland-eilanden                            | AX                       | ALA                      | SV-SE/en-US                         |
| Albanië                                  | AL                       | ALB                      | VK-AL/en-US                         |
| Algerije                                  | DZ                       | DZA                      | AR-DZ/en-US                         |
| Amerikaans-Samoa                           | AS                       | ASM                      | en-US                                 |
| Andorra                                  | AD                       | AND                      | CA-ES/en-US                         |
| Angola                                   | AO                       | LATER                      | pt-PT/en-US                         |
| Anguilla                                 | AI                       | AIA                      | en-US                                 |
| Antarctica                               | AQ                       | ATA                      | en-US                                 |
| Antigua en Barbuda                      | AG                       | ATG                      | en-US                                 |
| Argentinië                                | AR                       | ARG                      | es-AR/en-US                         |
| Armenië                                  | AM                       | ARM                      | HY-AM/nl-US                         |
| Aruba                                    | AW                       | ABW                      | nl-NL/nl-US                         |
| Australië                                | AU                       | AU'S                      | en-AU/nl-nl                         |
| Oostenrijk                                  | AT                       | AUT                      | de-AT/nl-nl                         |
| Azerbeidzjan                               | AZ                       | AZE                      | AZ-Latn-AZ/nl-nl                    |
| Bahama's                                  | BS                       | BHS                      | en-GB/en-US                         |
| Bahrein                                  | BH                       | BHR                      | AR-BH/en-US                         |
| Bangladesh                               | BD                       | BGD                      | bn-BD/en-US                         |
| Barbados                                 | BB                       | BRB                      | en-GB/en-US                         |
| Belarus                                  | BY                       | BLR                      | VOOR-en-US                         |
| België                                  | BE                       | LABELNAAM                      | FR-gepaard/nl-nl                 |
| Belize                                   | BZ                       | BLZ                      | en-BZ/en-US                         |
| Benin                                    | BJ                       | Jan                      | fr-FR/en-US                         |
| Bermuda                                  | BM                       | BMU                      | en-GB/en-US                         |
| Bhutan                                   | BT                       | BTN                      | en-US                                 |
| Bolivia                                  | BO                       | BOL                      | es-BO/en-US                         |
| Bonaire                                  | BV                       | BES                      | nl-NL/nl-US                         |
| Bosnië en Herzegovina                   | BA                       | BIH                      | BS-Latn-BA/nl-nl                    |
| Botswana                                 | BW                       | BWA                      | en-GB/en-US                         |
| Bouveteiland                            | BW                       | BVT                      | nb-NO/nl-nl                         |
| Brazilië                                   | BR                       | BRA                      | pt-BR/en-US                         |
| Brits Territorium in de Indische Oceaan           | I/O                       | IoT                      | en-US                                 |
| Britse Maagdeneilanden                   | VG                       | VGB                      | en-US                                 |
| Brunei                                   | BN                       | BRN                      | MS-BN/en-US                         |
| Bulgarije                                 | BG                       | BGR                      | bg-BG/nl-US                         |
| Burkina Faso                             | BF                       | BFA                      | fr-FR/en-US                         |
| Burundi                                  | BI                       | BDI                      | fr-FR/en-US                         |
| Cabo Verde                               | CV                       | CPV                      | PT-CV/en-US                         |
| Cambodja                                 | KH                       | KHM                      | km-KH/en-US                         |
| Kameroen                                 | CM                       | Verzend                      | fr-FR/en-US                         |
| Canada                                   | CA (consistentie en beschikbaarheid)                       | KUNNEN                      | FR-CA/en-US                         |
| Kaaimaneilanden                           | KY                       | CYM                      | en-GB/en-US                         |
| Centraal-Afrikaanse Republiek                 | CF                       | CAF                      | fr-FR/en-US                         |
| Tsjaad                                     | TD                       | TCD                      | fr-FR/en-US                         |
| Chili                                    | CL                       | CHL                      | es-LC/nl-US                         |
| China                                    | CN                       | CHN                      | zh-CN/nl-US                         |
| Christmaseiland                         | CX                       | CXR                      | en-US                                 |
| Cocoseilanden                  | CC                       | CCK                      | en-US                                 |
| Colombia                                 | CO                       | COL                      | es-CO/en-US                         |
| Comoren                                  | KM                       | COM                      | fr-FR/en-US                         |
| Congo                                    | CG                       | TANDWIEL                      | fr-FR/en-US                         |
| Congo (DRC)                              | CD                       | COD (Company Owned Devices)                      | fr-FR/en-US                         |
| Cookeilanden                             | CK                       | COK                      | en-US                                 |
| Costa Rica                               | CR                       | CRI                      | es-CR/en-US                         |
| Cote d'Ivoire                            | CI                       | CIV                      | fr-FR/en-US                         |
| Kroatië                                  | HR                       | HRV                      | HR-HR/nl-US                         |
| Curaçao                                  | WAARNAAR                       | CUW                      | nl-NL/nl-US                         |
| Cyprus                                   | CY                       | CYP                      | El-GR/en-US                         |
| Czechia                                  | CZ                       | CZE                      | CS-CZ/en-US                         |
| Denemarken                                  | DK                       | DNK                      | da-DK/nl-US                         |
| Djibouti                                 | DJ                       | DJI                      | fr-FR/en-US                         |
| Dominica                                 | DM                       | DMA                      | en-US                                 |
| Dominicaanse Republiek                       | DO                       | NAT                      | es-DO/en-US                         |
| Ecuador                                  | EC                       | GEDRUCT                      | es-EC/nl-US                         |
| Egypte                                    | EG                       | EGY                      | AR-bijvoorbeeld/nl-nl                         |
| El Salvador                              | SV                       | SLV                      | es-SV/en-US                         |
| Equatoriaal-Guinea                        | GQ                       | GNQ                      | es-ES/en-US                         |
| Eritrea                                  | ER                       | ERI                      | AR-SA/en-US                         |
| Estland                                  | EE                       | EST                      | et-EE/nl-nl                         |
| eSwatini                                 | SZ                       | SWZ                      | en-US                                 |
| Ethiopië                                 | ET                       | ETH                      | am-ET-en-US                         |
| Falklandeilanden                         | FK                       | FLK                      | en-US                                 |
| Faröer                            | FO                       | PROGRAMS                      | FO/en-US                         |
| Fiji                                     | FJ                       | FJI                      | en-GB/en-US                         |
| Finland                                  | FI                       | FIN                      | fi-FI/SV-FI/nl-nl                 |
| Frankrijk                                   | FR                       | FRA                      | fr-FR/en-US                         |
| Frans-Guyana                            | GF                       | GUF                      | fr-FR/en-US                         |
| Frans-Polynesië                         | PF                       | PYF                      | fr-FR/en-US                         |
| Franse Gebieden in de zuidelijke Indische Oceaan              | TF                       | ATF                      | fr-FR/en-US                         |
| Gabon                                    | Algemene beschikbaarheid                       | GAB                      | fr-FR/en-US                         |
| Gambia                                   | GM                       | GMB                      | en-US                                 |
| Georgië                                  | GE                       | GEO                      | ka-GE/en-US                         |
| Duitsland                                  | DE                       | DEU                      | de-DE/nl-nl                         |
| Ghana                                    | GH                       | GHA                      | en-GB/en-US                         |
| Gibraltar                                | GI                       | GIB                      | en-US                                 |
| Griekenland                                   | GR                       | GRC                      | El-GR/en-US                         |
| Groenland                                | BOEKHOUD                       | GRL                      | da-DK/nl-US                         |
| Grenada                                  | GD                       | GRD                      | en-US                                 |
| Guadeloupe                               | GP                       | GLP                      | fr-FR/en-US                         |
| Guam                                     | GU                       | VLEES                      | en-US                                 |
| Guatemala                                | GT                       | GTM                      | es-GT/nl-US                         |
| Guernsey                                 | GG                       | GGY                      | en-US                                 |
| Guinee                                   | GN                       | EGINNEN                      | fr-FR/en-US                         |
| Guinee-Bissau                            | GW                       | GNB                      | pt-PT/en-US                         |
| Guyana                                   | GY                       | Column                      | en-US                                 |
| Haïti                                    | HT                       | HTI                      | fr-FR/en-US                         |
| Heard- en McDonald-eilanden        | HM                       | HMD                      | en-US                                 |
| Honduras                                 | HN                       | HND                      | es-HN/en-US                         |
| Hongkong SAR                            | HK                       | HKG                      | zh-HK/en-US                         |
| Hongarije                                  | HU                       | HUN                      | hu-HU/en-US                         |
| IJsland                                  | IS                       | LINKS                      | is-IS/en-US                         |
| India                                    | IN                       | IND                      | en-IN/Hi-IN/en-US                 |
| Indonesië                                | Id                       | IDN                      | id-ID/en-US                         |
| Irak                                     | IQ                       | IRQ                      | AR-IQ/nl-US                         |
| Ierland                                  | IE                       | IRL                      | en-IE/en-US                         |
| Isle of Man                              | IM                       | IMN                      | en-US                                 |
| Israël                                   | IL                       | ISR                      | he IL/nl-nl                         |
| Italië                                    | IT                       | ITA                      | IT-IT/nl-nl                         |
| Jamaica                                  | JM                       | BRAND                      | en-JM/en-US                         |
| Jan Mayen                                | XJ                       | XJA                      | nb-NO/nl-nl                         |
| Japan                                    | JP                       | JPN                      | ja-JP/en-US                         |
| Jersey                                   | JE                       | JEY                      | en-US                                 |
| Jordanië                                   | JO                       | JOR                      | AR-JO/nl-US                         |
| Kazachstan                               | KZ                       | KAZ                      | kk-KZ/nl-nl                         |
| Kenia                                    | KE                       | KEN                      | SW-KE/en-US                         |
| Kiribati                                 | KI                       | KIR                      | en-US                                 |
| Korea                                    | KR                       | KOR                      | ko-KR/en-US                         |
| Kosovo                                   | XK                       | XKS                      | en-US                                 |
| Koeweit                                   | KW                       | KWT                      | AR-KW/en-US                         |
| Kirgistan                               | KG                       | KGZ                      | KY-KG/en-VS                         |
| Laos                                     | LA                       | DEMOCRATISCHE                      | Lo-LA/en-US                         |
| Letland                                   | LV                       | LVA                      | LV-LV/nl-nl                         |
| Libanon                                  | LB                       | LBN                      | AR-LB/en-US                         |
| Lesotho                                  | LS                       | LSO                      | en-US                                 |
| Liberia                                  | LR                       | LBR                      | en-US                                 |
| Libië                                    | LY                       | LBY                      | AR-en-US                         |
| Liechtenstein                            | LI                       | BERUST                      | de-LI/nl-nl                         |
| Litouwen                                | LT                       | LTU                      | lt-LT/en-US                         |
| Luxemburg                               | LU                       | LUX                      | de-LU/fr-LU/nl-US                 |
| Macau SAR                                | MO                       | MAC                      | zh-MO/nl-US                         |
| Macedonië, voormalige Joegoslavische Republiek                          | MK                       | MKD                      | MK-MK/en-US                         |
| Madagaskar                               | MG                       | MDG                      | fr-FR/en-US                         |
| Malawi                                   | MW                       | MWI                      | en-US                                 |
| Maleisië                                 | MY                       | MYS                      | en-mijn/en-US                         |
| Maldiven                                 | MV                       | MDV                      | DV-MV/en-US                         |
| Mali                                     | ML                       | MLI                      | fr-FR/en-US                         |
| Malta                                    | MT                       | MLT                      | MT-MT/en-US                         |
| Marshalleilanden                         | MH                       | MHL                      | en-US                                 |
| Martinique                               | MQ                       | MTQ                      | fr-FR/en-US                         |
| Mauritanië                               | MR                       | BESTAND                      | AR-SA/en-US                         |
| Mauritius                                | MU                       | MUS                      | en-GB/en-US                         |
| Mayotte                                  | YT                       | MYT                      | fr-FR/en-US                         |
| Mexico                                   | MX                       | MEX                      | es-MX/en-US                         |
| Micronesia                               | FM                       | FSM                      | en-US                                 |
| Moldavië                                  | MD                       | MDA                      | RO-RO/en-US                         |
| Monaco                                   | MC                       | MCO                      | FR-MC/en-US                         |
| Mongolië                                 | MN                       | MNG                      | MN-MN/en-US                         |
| Montenegro                               | ME                       | MNE                      | sr-Latn-ME/en-US                    |
| Montserrat                               | MS                       | MSR                      | en-US                                 |
| Marokko                                  | MA                       | MRT                      | AR-MA/en-US                         |
| Mozambique                               | MZ                       | MOZ                      | pt-PT/en-US                         |
| Myanmar                                  | MM                       | MMR                      | en-US                                 |
| Namibië                                  | NA                       | Vietnam                      | en-GB/en-US                         |
| Nauru                                    | NR                       | NRU                      | en-US                                 |
| Nepal                                    | NP                       | NPL                      | nieu-NP/en-US                         |
| Nederlandse Antillen                     | EEN                       | ANT                      | en-US                                 |
| Nederland, de                         | NL                       | NLD                      | nl-NL/nl-US                         |
| Nieuw-Caledonië                            | NC                       | NCL                      | fr-FR/en-US                         |
| Nieuw-Zeeland                              | NZ                       | NZL                      | en-NZ/en-US                         |
| Nicaragua                                | NI                       | NIC                      | es-NI/en-US                         |
| Niger                                    | NE                       | NER                      | fr-FR/en-US                         |
| Nigeria                                  | NG                       | NGA                      | ha-Latn-aardgas/nl-nl                    |
| Niue                                     | NU                       | NIU                      | en-US                                 |
| Norfolk                           | NF                       | NFK                      | en-US                                 |
| Noordelijke Marianen                 | MP                       | MNP                      | en-US                                 |
| Noorwegen                                   | NO                       | NOR                      | nb-NO/nl-nl                         |
| Oman                                     | OM                       | OMN                      | AR-OM/nl-nl                         |
| Pakistan                                 | PK                       | PAKKET                      | uw-PK/en-US                         |
| Palau                                    | PW                       | PLW                      | en-US                                 |
| Palestijnse Autoriteit                    | PS                       | PSE                      | AR-SA/en-US                         |
| Panama                                   | PA                       | PAN                      | es-PA/en-US                         |
| Papoea-Nieuw-Guinea                         | 3000CN                       | PNG                      | en-US                                 |
| Paraguay                                 | PY                       | PRY                      | es-PY/nl-US                         |
| Peru                                     | PE                       | PER                      | es-PE/en-US                         |
| Filipijnen                              | PH                       | PHL                      | en-PH/en-US                         |
| Pitcairneilanden                         | PN                       | PCN                      | en-US                                 |
| Polen                                   | PL                       | POL                      | pl-PL/en-US                         |
| Portugal                                 | PT                       | PRT                      | pt-PT/en-US                         |
| Puerto Rico                              | PR                       | PRI                      | es-PR/en-US                         |
| Qatar                                    | QA                       | QAT                      | AR-QA/en-US                         |
| Réunion                                  | RE                       | REU                      | fr-FR/en-US                         |
| Roemenië                                  | RO                       | ROU                      | RO-RO/en-US                         |
| Rusland                                   | RU                       | RUS                      | ru-RU/en-US                         |
| Rwanda                                   | RW                       | RWA                      | RW-RW/nl-US                         |
| Saba                                     | X'EN                       | XSA                      | nl-NL/nl-US                         |
| Saint Kitts en Nevis                    | KN                       | KNA                      | en-GB/en-US                         |
| Saint Lucia                              | KREDIET                       | LCA                      | en-US                                 |
| Saint-Martin                             | V                       | MAF                      | fr-FR/en-US                         |
| Saint-Pierre en Miquelon                | PM                       | SPM                      | fr-FR/en-US                         |
| Saint Vincent en de Grenadines         | VC                       | VCT                      | en-US                                 |
| Saint-Barthélemy                         | BL                       | BLM                      | fr-FR/en-US                         |
| Samoa                                    | WS                       | WSM                      | en-US                                 |
| San Marino                               | 'S                       | SMR                      | IT-IT/nl-nl                         |
| Sao Tomé en principe                    | ST                       | STP                      | pt-PT/en-US                         |
| Saoedi-Arabië                             | SA                       | SAU                      | AR-SA/en-US                         |
| Senegal                                  | SN                       | AFZEN                      | wo-SN/nl-US                         |
| Servië                                   | RS                       | SRB                      | sr-Latn-RS/SR-Cyrl-RS/en-US       |
| Seychellen                               | SC                       | SYC                      | en-US                                 |
| Sierra Leone                             | SL                       | SLE                      | en-US                                 |
| Singapore                                | SG                       | SGP                      | en-SG/zh-SG/nl-US                 |
| Sint Eustatius                           | XE                       | XSE                      | nl-NL/nl-US                         |
| Sint Maarten                             | SX                       | SXM                      | en-US                                 |
| Slowakije                                 | SK                       | SVK                      | sk-SK/nl-nl                         |
| Slovenië                                 | SI                       | SVN                      | sl-SI/nl-nl                         |
| Salomonseilanden                          | SB                       | SLB                      | en-US                                 |
| Somalië                                  | SO                       | SOM                      | AR-SA/en-US                         |
| Zuid-Afrika                             | ZA                       | ZAF                      | en-ZA/en-US                         |
| Zuid-Georgië en de Zuidelijke Sandwicheilanden | GS                       | BEVEILIGINGS groepen                      | en-US                                 |
| Zuid-Soedan                              | SS                       | SSD                      | en-US                                 |
| Spanje                                    | ES                       | PROTOCOLSPECIFIEKE                      | es-ES/ca-es/EU-ES/gl-ES/en-US |
| Sri Lanka                                | LK                       | LKA                      | si-LK/en-US                         |
| Sint-Helena, Ascension en Tristan da Cunha   | SH                       | SHN                      | en-US                                 |
| Suriname                                 | SR                       | SUR                      | nl-NL                                 |
| Svalbard                                 | SJ                       | SJM                      | nb-NO/nl-nl                         |
| Zweden                                   | SE                       | Zwe                      | SV-SE/en-US                         |
| Zwitserland                              | CH                       | OPSLAAN                      | de-CH/fr-CH/it-CH/nl-nl         |
| Taiwan                                   | TW                       | TWN                      | zh-TW/nl-US                         |
| Tadzjikistan                               | TJ                       | TJK                      | TG-Cyrl-TJ/en-US                    |
| Tanzania                                 | TZ                       | TZA                      | en-GB/en-US                         |
| Thailand                                 | TH                       | THA                      | th-do/nl-nl                         |
| Timor-Leste                              | TL                       | TLS                      | pt-PT/en-US                         |
| Togo                                     | TG                       | TGO                      | fr-FR/en-US                         |
| Tokelau                                  | TK                       | TKL                      | en-US                                 |
| Tonga                                    | TO                       | TON                      | en-US                                 |
| Trinidad en Tobago                      | TT                       | TTO                      | en-TT/en-US                         |
| Tunesië                                  | TN                       | TUN                      | AR-TN/en-US                         |
| Turkije                                   | TR                       | TUR                      | tr-TR/en-US                         |
| Turkmenistan                             | TM                       | TKM                      | tk-TM/en-US                         |
| Turks- en Caicos-eilanden                 | TC                       | TCA                      | en-US                                 |
| Tuvalu                                   | TV                       | TUV                      | en-US                                 |
| Oeganda                                   | UG                       | UGA                      | en-GB/en-US                         |
| Oekraïne                                  | UA                       | UKR                      | UK-UA/en-US                         |
| Verenigde Arabische Emiraten                     | AE                       | ZIJN                      | AR-AE/nl-US                         |
| Verenigd Koninkrijk                           | GB                       | GBR                      | en-GB/en-US                         |
| Amerikaanse ondergeschikte afgelegen eilanden                    | UM                       | UMI                      | en-US                                 |
| Amerikaanse Maagden eilanden                      | VI                       | VIR                      | en-US                                 |
| Verenigde Staten                            | VS                       | VS                      | en-US/es-VS                         |
| Uruguay                                  | UY                       | URY                      | es-UY/en-US                         |
| Oezbekistan                               | UZ                       | UZB                      | UZ-Latn-UZ/nl-nl                    |
| Vanuatu                                  | VU                       | VUT                      | en-US                                 |
| Vaticaanstad                             | VA                       | BELASTING                      | IT-IT/nl-nl                         |
| Venezuela                                | VE                       | VEN                      | es-VE/en-US                         |
| Vietnam                                  | VN                       | VNM                      | VI-VN/en-US                         |
| Wallis en Futuna                        | WF                       | WLF                      | fr-FR/en-US                         |
| Jemen                                    | TEZAM                       | YEM                      | AR-YE/nl-nl                         |
| Zambia                                   | ZM                       | ZMB                      | en-GB/en-US                         |
| Zimbabwe                                 | ZW                       | ZWE                      | en-ZW/en-US                         |

