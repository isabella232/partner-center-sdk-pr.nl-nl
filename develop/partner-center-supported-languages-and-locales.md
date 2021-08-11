---
title: Ondersteunde talen en landinstellingen voor Partnercentrum
description: Lijst met ondersteunde ISO2- en ISO3-Partner Center.
ms.date: 12/03/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 6f2e1d50fa0f2ace2e94f4dbb5681e2164241ee57a85249136a55fce20893fbb
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997580"
---
# <a name="partner-center-supported-languages-and-locales"></a>Ondersteunde talen en landinstellingen voor Partnercentrum

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Voor Partner Center API's is een waarde vereist die een land/regio aangeeft. Zo vereist de [Partner Center REST-header](headers.md) X-Locale vaak een waarde in de notatie 'taal-land' ('en-US' geeft 'Engels - Verenigde Staten').

In de Partner Center beheerde API's, de klasse [CountryValidationRules/dotnet/api/microsoft.store.partnercenter.models.countryvalidationrules.countryvalidationrules) en de klasse [OfferCategory.Locale/dotnet/api/microsoft.store.partnercenter.models.offers.offercategory.locale), [ServiceRequest.CountryCode/dotnet/dotnet/api/microsoft.store.partnercenter.models.servicerequests.servicerequest.countrycode) of [CustomerBillingProfile.Culture/dotnet/api/microsoft.store.partnercenter.models.customers.customerbillingprofile.culture) vereisen tekenreekswaarden die een taal of land/regio aangeven (in de vorm van een ISO2-taalcode of ISO3-land/regiocode), een land/regio, of een cultuur (een taal-id in combinatie met een land-/regiocode).

De volgende tabel bevat de culturen en ISO-landcodes (International Standards Organization) die worden ondersteund in de Partner Center API's.

| Land/regio                           | ISO Alpha 2 Country Code | ISO Alpha 3 Country Code | Ondersteunde cultuur(en)                  |
|------------------------------------------|--------------------------|--------------------------|---------------------------------------|
| Afghanistan                              | AF                       | Afg                      | ps-AF/ en-US                         |
| Ålandeilanden                            | Ax                       | Ala                      | sv-SE / en-US                         |
| Albanië                                  | AL                       | Alb                      | sq-AL / en-US                         |
| Algerije                                  | DZ                       | Dza                      | ar-DZ/ en-US                         |
| Amerikaans-Samoa                           | AS                       | ASM                      | en-US                                 |
| Andorra                                  | AD                       | AND                      | ca-ES/en-US                         |
| Angola                                   | AO                       | Geleden                      | pt-PT/ en-US                         |
| Anguilla                                 | AI                       | Aia                      | en-US                                 |
| Antarctica                               | Aq                       | Ata                      | en-US                                 |
| Antigua en Barbuda                      | AG                       | Atg                      | en-US                                 |
| Argentinië                                | AR                       | Arg                      | es-AR/en-US                         |
| Armenië                                  | AM                       | ARM                      | hy-AM/en-US                         |
| Aruba                                    | Aw                       | ABW                      | nl-NL / en-US                         |
| Australië                                | AU                       | Aus                      | en-AU / en-US                         |
| Oostenrijk                                  | AT                       | Aut                      | de-AT / en-US                         |
| Azerbeidzjan                               | AZ                       | AZE                      | az-Latn-AZ / en-US                    |
| Bahama's                                  | BS                       | Bhs                      | en-GB / en-US                         |
| Bahrein                                  | BH                       | BHR                      | ar-WORDT/en-US                         |
| Bangladesh                               | BD                       | BGD                      | bn-BD / en-US                         |
| Barbados                                 | BB                       | Brb                      | en-GB / en-US                         |
| Belarus                                  | BY                       | BLR                      | be-BY / en-US                         |
| België                                  | BE                       | BEL                      | fr-BE / nl-BE / en-US                 |
| Belize                                   | BZ                       | DEN                      | en-BZ / en-US                         |
| Benin                                    | BJ                       | BEN                      | fr-FR / en-US                         |
| Bermuda                                  | Bm                       | BMU                      | en-GB / en-US                         |
| Bhutan                                   | BT                       | BTN                      | en-US                                 |
| Bolivia                                  | BO                       | BOL                      | es-BO/en-US                         |
| Bonaire                                  | Bq                       | BES                      | nl-NL / en-US                         |
| Bosnië en Herzegovina                   | BA                       | Bih                      | bs-Latn-BA / en-US                    |
| Botswana                                 | BW                       | Bwa                      | en-GB / en-US                         |
| Bouveteiland                            | Bv                       | BLIJFTT                      | nb-NO / en-US                         |
| Brazilië                                   | BR                       | Beha                      | pt-BR/ en-US                         |
| Brits Territorium in de Indische Oceaan           | I/O                       | IoT                      | en-US                                 |
| Britse Maagdeneilanden                   | VG                       | VGB                      | en-US                                 |
| Brunei                                   | BN                       | Brn                      | ms-BN / en-US                         |
| Bulgarije                                 | BG                       | Bgr                      | bg-BG / en-US                         |
| Burkina Faso                             | BF                       | Bfa                      | fr-FR / en-US                         |
| Burundi                                  | BI                       | BDI                      | fr-FR / en-US                         |
| Cabo Verde                               | CV                       | Cpv                      | pt-CV / en-US                         |
| Cambodja                                 | KH                       | KHM                      | km-KH/ en-US                         |
| Kameroen                                 | CM                       | Cmr                      | fr-FR / en-US                         |
| Canada                                   | CA (consistentie en beschikbaarheid)                       | Kunt                      | fr-CA / en-US                         |
| Kaaimaneilanden                           | KY                       | CYM                      | en-GB / en-US                         |
| Centraal-Afrikaanse Republiek                 | CF                       | Caf                      | fr-FR / en-US                         |
| Tsjaad                                     | TD                       | Tcd                      | fr-FR / en-US                         |
| Chili                                    | CL                       | Chl                      | es-CL / en-US                         |
| China                                    | CN                       | Chn                      | zh-CN / en-US                         |
| Christmaseiland                         | CX                       | CXR                      | en-US                                 |
| Cocoseilanden                  | CC                       | Cck                      | en-US                                 |
| Colombia                                 | CO                       | Kolonel                      | es-CO /en-US                         |
| Comoren                                  | Km                       | Com                      | fr-FR / en-US                         |
| Congo                                    | Cg                       | Cog                      | fr-FR / en-US                         |
| Congo (DRC)                              | CD                       | COD (Company Owned Devices)                      | fr-FR / en-US                         |
| Cookeilanden                             | Ck                       | COK                      | en-US                                 |
| Costa Rica                               | CR                       | Cri                      | es-CR / en-US                         |
| Cote d'Ivoire                            | CI                       | Civ                      | fr-FR / en-US                         |
| Kroatië                                  | HR                       | Hrv                      | hr-HR /en-US                         |
| Curaçao                                  | Cw                       | CUW                      | nl-NL / en-US                         |
| Cyprus                                   | CY                       | Cyp                      | el-GR / en-US                         |
| Tsjechië                                  | CZ                       | Cze                      | cs-ORDE / en-US                         |
| Denemarken                                  | DK                       | DNK                      | da-DK / en-US                         |
| Djibouti                                 | Dj                       | Dji                      | fr-FR / en-US                         |
| Dominica                                 | DM                       | DMA                      | en-US                                 |
| Dominicaanse Republiek                       | DO                       | Dom                      | es-DO / en-US                         |
| Ecuador                                  | EC                       | Ecu                      | es-EC/ en-US                         |
| Egypte                                    | EG                       | Egy                      | ar-EG / en-US                         |
| El Salvador                              | SV                       | Slv                      | es-SV / en-US                         |
| Equatoriaal-Guinea                        | Gq                       | GNQ                      | es-ES/ en-US                         |
| Eritrea                                  | ER                       | Eri                      | ar-SA / en-US                         |
| Estland                                  | EE                       | Est                      | et-EE / en-US                         |
| eSwaautoriteit                                 | SZ                       | SWZ                      | en-US                                 |
| Ethiopië                                 | ET                       | Eth                      | am-ET/ en-US                         |
| Falklandeilanden                         | Fk                       | FLK                      | en-US                                 |
| Faröer                            | Fo                       | Fro                      | fo-FO / en-US                         |
| Fiji                                     | FJ                       | FJI                      | en-GB / en-US                         |
| Finland                                  | FI                       | FIN                      | fi-FI / sv-FI / en-US                 |
| Frankrijk                                   | FR                       | FRA                      | fr-FR / en-US                         |
| Frans-Guyana                            | GF                       | GUF                      | fr-FR / en-US                         |
| Frans-Polynesië                         | PF                       | PYF                      | fr-FR / en-US                         |
| Franse Gebieden in de zuidelijke Indische Oceaan              | Tf                       | Atf                      | fr-FR / en-US                         |
| Gabon                                    | Algemene beschikbaarheid                       | Gab                      | fr-FR / en-US                         |
| Gambia                                   | GM                       | GMB                      | en-US                                 |
| Georgië                                  | GE                       | Geo                      | ka-GE / en-US                         |
| Duitsland                                  | DE                       | DEU                      | de-DE / en-US                         |
| Ghana                                    | GH                       | GHA                      | en-GB / en-US                         |
| Gibraltar                                | Gi                       | Gib                      | en-US                                 |
| Griekenland                                   | GR                       | GRC                      | el-GR / en-US                         |
| Groenland                                | Gl                       | GRL                      | da-DK / en-US                         |
| Grenada                                  | Gd                       | Grd                      | en-US                                 |
| Guadeloupe                               | GP                       | Glp                      | fr-FR / en-US                         |
| Guam                                     | GU                       | Gom                      | en-US                                 |
| Guatemala                                | GT                       | Gtm                      | es-GT / en-US                         |
| Guernsey                                 | Gg                       | GGY                      | en-US                                 |
| Guinee                                   | GN                       | Gin                      | fr-FR / en-US                         |
| Guinee-Bissau                            | GW                       | Gnb                      | pt-PT / en-US                         |
| Guyana                                   | GY                       | Man                      | en-US                                 |
| Haïti                                    | HT                       | Hti                      | fr-FR / en-US                         |
| Heard- en McDonald-eilanden        | Hm                       | Hmd                      | en-US                                 |
| Honduras                                 | HN                       | Hnd                      | es-HN / en-US                         |
| Hongkong SAR                            | HK                       | Hkg                      | zh-HK / en-US                         |
| Hongarije                                  | HU                       | HUN                      | hu-HU / en-US                         |
| IJsland                                  | IS                       | Isl                      | is-IS/en-US                         |
| India                                    | IN                       | IND                      | en-IN / hi-IN / en-US                 |
| Indonesië                                | Id                       | Idn                      | id-ID / en-US                         |
| Irak                                     | IQ                       | Irq                      | ar-IQ / en-US                         |
| Ierland                                  | IE                       | Irl                      | en-IE / en-US                         |
| Isle of Man                              | IM                       | IMN                      | en-US                                 |
| Israël                                   | IL                       | ISR                      | he-IL /en-US                         |
| Italië                                    | IT                       | ITA                      | it-IT /en-US                         |
| Jamaica                                  | JM                       | Jam                      | en-JM / en-US                         |
| Jan Mayen                                | Xj                       | XJA                      | nb-NO / en-US                         |
| Japan                                    | JP                       | JPN                      | ja-JP / en-US                         |
| Jersey                                   | JE                       | Jey                      | en-US                                 |
| Jordanië                                   | JO                       | Jor                      | ar-JO / en-US                         |
| Kazachstan                               | KZ                       | Kaz                      | kk-KZ / en-US                         |
| Kenia                                    | KE                       | KEN                      | sw-KE / en-US                         |
| Kiribati                                 | KI                       | Kir                      | en-US                                 |
| Korea                                    | KR                       | KOR                      | ko-KR / en-US                         |
| Kosovo                                   | XK                       | XKS                      | en-US                                 |
| Koeweit                                   | KW                       | KWT                      | ar-KW / en-US                         |
| Kirgistan                               | KG                       | KGZ                      | ky-KG /en-US                         |
| Laos                                     | LA                       | Lao                      | lo-LA / en-US                         |
| Letland                                   | LV                       | LVA                      | lv-LV / en-US                         |
| Libanon                                  | LB                       | LBN                      | ar-LB/en-US                         |
| Lesotho                                  | LS                       | Lso                      | en-US                                 |
| Liberia                                  | LR                       | LBR                      | en-US                                 |
| Libië                                    | LY                       | LBY                      | ar-LY / en-US                         |
| Liechtenstein                            | LI                       | Liggen                      | de-LI / en-US                         |
| Litouwen                                | LT                       | Ltu                      | lt-LT / en-US                         |
| Luxemburg                               | LU                       | Lux                      | de-LU / fr-LU / en-US                 |
| Macau SAR                                | MO                       | Mac                      | zh-MO / en-US                         |
| Noord-Oost, FYRO                          | MK                       | MKD                      | mk-MK / en-US                         |
| Madagaskar                               | MG                       | Mdg                      | fr-FR / en-US                         |
| Malawi                                   | MW                       | MWI                      | en-US                                 |
| Maleisië                                 | MY                       | MYS                      | en-MY / en-US                         |
| Maldiven                                 | MV                       | MDV                      | dv-MV / en-US                         |
| Mali                                     | ML                       | MLI                      | fr-FR / en-US                         |
| Malta                                    | MT                       | MLT                      | mt-MT / en-US                         |
| Marshalleilanden                         | MH                       | Mhl                      | en-US                                 |
| Martinique                               | MQ                       | MTQ                      | fr-FR / en-US                         |
| Mauritanië                               | MR                       | MRT                      | ar-SA / en-US                         |
| Mauritius                                | Mu                       | Mus                      | en-GB / en-US                         |
| Mayotte                                  | YT                       | MYT                      | fr-FR / en-US                         |
| Mexico                                   | MX                       | Mex                      | es-MX / en-US                         |
| Micronesia                               | FM                       | Fsm                      | en-US                                 |
| Moldavië                                  | MD                       | Mda                      | ro-RO / en-US                         |
| Monaco                                   | MC                       | Mco                      | fr-MC / en-US                         |
| Mongolië                                 | MN                       | Mng                      | mn-MN / en-US                         |
| Montenegro                               | ME                       | MNE                      | sr-Latn-ME / en-US                    |
| Montserrat                               | MS                       | MSR                      | en-US                                 |
| Marokko                                  | MA                       | MRT                      | ar-MA / en-US                         |
| Mozambique                               | MZ                       | Moz                      | pt-PT                                 |
| Myanmar                                  | MM                       | Mmr                      | en-US                                 |
| Namibië                                  | NA                       | NAM                      | en-GB / en-US                         |
| Nauru                                    | NR                       | Nru                      | en-US                                 |
| Nepal                                    | NP                       | Npl                      | ne-NP / en-US                         |
| Nederlandse Antillen                     | Een                       | Ant                      | en-US                                 |
| Nederland, de                         | NL                       | NLD                      | nl-NL / en-US                         |
| Nieuw-Caledonië                            | NC                       | NCL                      | fr-FR / en-US                         |
| Nieuw-Zeeland                              | NZ                       | Nzl                      | en-NZ / en-US                         |
| Nicaragua                                | NI                       | NIC                      | es-NI/en-US                         |
| Niger                                    | NE                       | Ner                      | fr-FR / en-US                         |
| Nigeria                                  | NG                       | Nga                      | ha-Latn-NG / en-US                    |
| Niue                                     | NU                       | Niu                      | en-US                                 |
| Norfolk                           | Nf                       | NFK                      | en-US                                 |
| Noordelijke Marianen                 | MP                       | MNP                      | en-US                                 |
| Noorwegen                                   | NO                       | NOR                      | nb-NO / en-US                         |
| Oman                                     | OM                       | OMN                      | ar-OM/en-US                         |
| Pakistan                                 | PK                       | PAK                      | your-PK/en-US                         |
| Palau                                    | PW                       | PLW                      | en-US                                 |
| Palestijnse Autoriteit                    | PS                       | Pse                      | ar-SA / en-US                         |
| Panama                                   | PA                       | PAN                      | es-PA /en-US                         |
| Papoea-Nieuw-Guinea                         | Pg                       | PNG                      | en-US                                 |
| Paraguay                                 | PY                       | Wrikken                      | es-PY/en-US                         |
| Peru                                     | PE                       | PER                      | es-PE/en-US                         |
| Filipijnen                              | PH                       | Phl                      | en-PH / en-US                         |
| Pitcairneilanden                         | Pn                       | Pcn                      | en-US                                 |
| Polen                                   | PL                       | Pol                      | pl-PL/en-US                         |
| Portugal                                 | PT                       | Prt                      | pt-PT/ en-US                         |
| Puerto Rico                              | PR                       | Pri                      | es-PR/ en-US                         |
| Qatar                                    | QA                       | Qat                      | ar-QA/en-US                         |
| Réunion                                  | RE                       | REU                      | fr-FR / en-US                         |
| Roemenië                                  | RO                       | Rou                      | ro-RO/ en-US                         |
| Rusland                                   | RU                       | RUS                      | ru-RU /en-US                         |
| Rwanda                                   | RW                       | RWA                      | rw-RW/ en-US                         |
| Saba                                     | Xs                       | XSA                      | nl-NL / en-US                         |
| Saint Kitts en Nevis                    | KN                       | Kna                      | en-GB / en-US                         |
| Saint Lucia                              | Lc                       | Lca                      | en-US                                 |
| Saint-Martin                             | Mf                       | Maf                      | fr-FR / en-US                         |
| Saint-Pierre en Miquelon                | PM                       | Spm                      | fr-FR / en-US                         |
| Saint Vincent en de Grenadines         | VC                       | Vct                      | en-US                                 |
| Saint-Barthélemy                         | BL                       | Blm                      | fr-FR / en-US                         |
| Samoa                                    | WS                       | Wsm                      | en-US                                 |
| San Marino                               | Sm                       | Smr                      | it-IT/en-US                         |
| Sño Toñ en Prñncipe                    | ST                       | Stp                      | pt-PT/ en-US                         |
| Saoedi-Arabië                             | SA                       | Sau                      | ar-SA/en-US                         |
| Senegal                                  | SN                       | Sen                      | wo-SN / en-US                         |
| Servië                                   | RS                       | Srb                      | sr-Latn-RS / sr-Cyrl-RS / en-US       |
| Seychellen                               | SC                       | SYC                      | en-US                                 |
| Sierra Leone                             | SL                       | Sle                      | en-US                                 |
| Singapore                                | SG                       | Sgp                      | en-SG / zh-SG / en-US                 |
| Sint Eustatius                           | Xe                       | XSE                      | nl-NL / en-US                         |
| Sint Maarten                             | Sx                       | Sxm                      | en-US                                 |
| Slowakije                                 | SK                       | Svk                      | sk-SK / en-US                         |
| Slovenië                                 | SI                       | Svn                      | sl-SI / en-US                         |
| Salomonseilanden                          | Sb                       | Slb                      | en-US                                 |
| Somalië                                  | SO                       | SOM                      | ar-SA/en-US                         |
| Zuid-Afrika                             | ZA                       | ZAF                      | en-ZA / en-US                         |
| Zuid-Georgië en de Zuidelijke Sandwicheilanden | Gs                       | Sgs                      | en-US                                 |
| Zuid-Soedan                              | SS                       | SSD                      | en-US                                 |
| Spanje                                    | ES                       | Ihb                      | es-ES / ca-ES / eu-ES / gl-ES / en-US |
| Sri Lanka                                | LK                       | LKA                      | si-HE/ en-US                         |
| St Helena, Ascension, Tristan da Cunha   | SH                       | Shn                      | en-US                                 |
| Suriname                                 | SR                       | Sur                      | nl-NL                                 |
| Svalbard                                 | Sj                       | SJM                      | nb-NO / en-US                         |
| Zweden                                   | SE                       | Swe                      | sv-SE / en-US                         |
| Zwitserland                              | CH                       | Che                      | de-CH / fr-CH / it-CH / en-US         |
| Taiwan                                   | TW                       | TWN                      | zh-TW/ en-US                         |
| Tadzjikistan                               | Tj                       | TJK                      | tg-Cyrl-TJ / en-US                    |
| Tanzania                                 | TZ                       | TZA                      | en-GB / en-US                         |
| Thailand                                 | TH                       | Tha                      | th-TH / en-US                         |
| Timor-Leste                              | TL                       | TLS                      | pt-PT/ en-US                         |
| Togo                                     | TG                       | Tgo                      | fr-FR / en-US                         |
| Tokelau                                  | Tk                       | TKL                      | en-US                                 |
| Tonga                                    | TO                       | TON                      | en-US                                 |
| Trinidad en Tobago                      | TT                       | TTO                      | en-TT / en-US                         |
| Tunesië                                  | TN                       | Tun                      | ar-TN / en-US                         |
| Turkije                                   | TR                       | Tur                      | tr-TR / en-US                         |
| Turkmenistan                             | TM                       | Tkm                      | tk-TM / en-US                         |
| Turks- en Caicos-eilanden                 | TC                       | Tca                      | en-US                                 |
| Tuvalu                                   | TV                       | TUV                      | en-US                                 |
| Oeganda                                   | UG                       | Uga                      | en-GB / en-US                         |
| Oekraïne                                  | UA                       | Ukr                      | uk-UA/en-US                         |
| Verenigde Arabische Emiraten                     | AE                       | Zijn                      | ar-AE/ en-US                         |
| Verenigd Koninkrijk                           | GB                       | Gbr                      | en-GB / en-US                         |
| Amerikaanse outlyingeilanden                    | UM                       | Umi                      | en-US                                 |
| Amerikaanse Maagdeneilanden                      | VI                       | Vir                      | en-US                                 |
| Verenigde Staten                            | VS                       | VS                      | en-US /es-US                         |
| Uruguay                                  | UY                       | Ury                      | es-UY/ en-US                         |
| Oezbekistan                               | UZ                       | UZB                      | uz-Latn-UZ / en-US                    |
| Vanuatu                                  | Vu                       | VUT                      | en-US                                 |
| Vaticaanstad                             | VA                       | Btw                      | it-IT/en-US                         |
| Venezuela                                | VE                       | Ven                      | es-VE / en-US                         |
| Vietnam                                  | VN                       | VNM                      | vi-VN/ en-US                         |
| Wallis en Walluna                        | WF                       | WLF                      | fr-FR / en-US                         |
| Jemen                                    | Gij                       | Yem                      | ar-YE / en-US                         |
| Zambia                                   | ZM                       | ZMB                      | en-GB / en-US                         |
| Zimbabwe                                 | ZW                       | ZWE                      | en-ZW / en-US                         |

