---
title: Downloadkoppeling voor de sjabloon Microsoft-klantovereenkomst downloaden
description: Haal een downloadkoppeling op voor Microsoft-klantovereenkomst sjabloon.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: fccb9e3d4a837f3e8043f8c7ae1e3911d819afd7
ms.sourcegitcommit: d20e7d572fee09a83a4b23a92da7ff09cfebe75a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111906532"
---
# <a name="get-a-download-link-for-the-microsoft-customer-agreement-template"></a>Downloadkoppeling voor de sjabloon Microsoft-klantovereenkomst downloaden

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De **AgreementDocument-resource** wordt momenteel ondersteund door Partner Center alleen in de openbare Cloud van Microsoft.

In dit artikel wordt beschreven hoe u een koppeling krijgt om de sjabloon Microsoft-klantovereenkomst downloaden, op basis van het land en de taal van de klant.

## <a name="prerequisites"></a>Vereisten

- Als u de .NET SDK Partner Center, is versie 1.14 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md). Dit scenario ondersteunt alleen App+Gebruikersverificatie.

- Het land van de klant waarop de Microsoft-klantovereenkomst van toepassing is.

- De taal waarin de Microsoft-klantovereenkomst sjabloon moet worden gelokaliseerd.

> [!IMPORTANT]
>
> - De Microsoft-klantovereenkomst is specifiek voor het land. Wanneer u een koppeling aanvraagt om de sjabloon Microsoft-klantovereenkomst downloaden, moet u het juiste land opgeven op basis van de locatie van de klant. of lijst met ondersteunde landen, [raadpleegt u Lijst met ondersteunde landen en talen.](#list-of-supported-countries-and-languages)
>
> - Voor sommige landen is de Microsoft-klantovereenkomst beschikbaar in meerdere talen. Kies voor de beste klantervaring de taal die het beste bij de behoeften van de klant past. Raadpleeg Lijst met ondersteunde landen en talen voor een lijst met [ondersteunde talen.](#list-of-supported-countries-and-languages)
> - Deze methode wordt alleen ondersteund met de Microsoft-klantovereenkomst.

## <a name="net"></a>.NET

Een koppeling ophalen om de sjabloon Microsoft-klantovereenkomst downloaden:

1. Haal de metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst. U moet de **templateId van de** Microsoft-klantovereenkomst. Zie Get [agreement metadata for Microsoft-klantovereenkomst (Metagegevens van overeenkomst verkrijgen voor Microsoft-klantovereenkomst) voor meer informatie.](get-customer-agreement-metadata.md)

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   AgreementMetaData microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.   ByAgreementType(agreementType).Get().Items.Single();
   ```

2. Gebruik de verzameling IAggregatePartner.AgreementTemplates.

3. Roep de **ById-methode** aan en geef de **templateId** van de Microsoft-klantovereenkomst.

4. Haal de **eigenschap Document** op.

5. Roep de **ByCountry-methode** aan en geef het land van de klant op waarop de overeenkomstsjabloon van toepassing is. De query wordt standaard ingesteld *op US* als de methode niet is opgegeven. Raadpleeg Lijst met ondersteunde landen en talen voor een lijst met ondersteunde [landcodes.](#list-of-supported-countries-and-languages) Deze methode is **casegevoelig.**

6. Roep de **methode ByLanguage** aan en geef de taal op waarin de overeenkomstsjabloon moet worden gelokaliseerd. De query wordt standaard ingesteld *op en-US* als de methode niet is opgegeven of als de opgegeven landcode niet wordt ondersteund voor het opgegeven land. Raadpleeg Lijst met ondersteunde landen en talen voor een lijst met [ondersteunde taalcodes.](#list-of-supported-countries-and-languages)

7. Roep de **methode Get** of **GetAsync aan.**

   ```csharp
   // IAggregatePartner partnerOperations;

   string customerCountry = "US";

   string languageForLocalization = "en-US";

   var agreementDocument = partnerOperations.   AgreementTemplates.ById   (microsoftCustomerAgreementDetails.   TemplateId).Document.ByCountry   (customerCountry).ByLanguage   (languageForLocalization).Get();
   ```

Een volledig voorbeeld vindt u in de [klasse GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)

## <a name="rest-request"></a>REST-aanvraag

Een koppeling ophalen om de sjabloon Microsoft-klantovereenkomst downloaden:

1. Haal de metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst. U moet de **templateId van de** Microsoft-klantovereenkomst. Zie Get [agreement metadata for Microsoft-klantovereenkomst (Metagegevens van overeenkomst verkrijgen voor Microsoft-klantovereenkomst) voor meer informatie.](get-customer-agreement-metadata.md)

2. Maak een REST-aanvraag om een [ **AgreementDocument-resource op** te halen.](./agreement-document-resources.md) Zie het voorbeeld van de [aanvraagsyntaxis voor een](#request-syntax) voorbeeld. U moet de volgende informatie opgeven:

    - De **templateId** van de Microsoft-klantovereenkomst.
    - Het land waarop de Microsoft-klantovereenkomst is toegepast.
    - De taal waarin de Microsoft-klantovereenkomst sjabloon moet worden gelokaliseerd.

### <a name="request-syntax"></a>Aanvraagsyntaxis

Gebruik de volgende aanvraagsyntaxis voor deze resource:

| Methode | Aanvraag-URI |
|--------|---------------------------------------------------------------------|
| GET | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreementtemplates/{agreement-template-id}/document?language={language}&country={country} HTTP/1.1 |

### <a name="uri-parameters"></a>URI-parameters

U kunt de volgende URI-parameters gebruiken bij uw aanvraag:

| Naam                   | Type   | Vereist | Beschrijving                                 |
|------------------------|--------|----------|---------------------------------------------|
| agreement-template-id  | tekenreeks | Ja      | De unieke id van het overeenkomsttype. U kunt de templateId voor Microsoft-klantovereenkomst verkrijgen door de metagegevens van de overeenkomst op te halen voor Microsoft-klantovereenkomst. Zie Get [agreement metadata for Microsoft-klantovereenkomst (Metagegevens van overeenkomst verkrijgen voor Microsoft-klantovereenkomst) voor meer informatie.](./get-customer-agreement-metadata.md) Deze parameter is **casegevoelig.**|
| country                | tekenreeks | No       | Geeft het land aan waarop de overeenkomstsjabloon van toepassing is. De query wordt standaard ingesteld *op US* als de parameter niet is opgegeven. Raadpleeg Lijst met ondersteunde landen en talen voor een lijst met ondersteunde [landcodes.](#list-of-supported-countries-and-languages)|
| language               | tekenreeks | No       | Hiermee wordt de taal aangegeven waarin de overeenkomstsjabloon moet worden gelokaliseerd. De query wordt standaard ingesteld *op en-US* als de parameter niet is opgegeven of als de landcode die is opgegeven in niet wordt ondersteund voor het opgegeven land. Raadpleeg Lijst met ondersteunde landen en talen voor een lijst met [ondersteunde landcodes.](#list-of-supported-countries-and-languages)|

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/agreementtemplates/117a77b0-9360-443b-8795-c6dedc750cf9/document?language=en-US&country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een [ **AgreementDocument-resource**](./agreement-document-resources.md) in de antwoord-body.

De resource heeft de **eigenschap downloadUri,** die een URL-tekenreeks bevat die kan worden gebruikt om de overeenkomstsjabloon te downloaden. Telkens wanneer u een query maakt, wordt er een andere koppeling geretourneerd. Deze koppeling verloopt na vijf minuten.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.

Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 620
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "displayUri":"https://wopihost.int.l2o.microsoft.com/v1/officehost/agreement/files/Preview...",
    "downloadUri":"https://l2oagreementintbn2.blob.core.windows.net/agreementscontainer/Preview...",
    "language":"en-US",
    "country":"US"
}
```

## <a name="list-of-supported-countries-and-languages"></a>Lijst met ondersteunde landen en talen

> [!IMPORTANT]
> De eigenschap landcode is casegevoelig. Zorg ervoor dat u de juiste casing gebruikt die is opgegeven in de onderstaande tabel.

| Land/regio                   | Landcode   | Ondersteunde taalcode(s) |
|------------------------|--------|----------|
| Ålandeilanden | Ax | en-US |
| Afghanistan | AF | en-US |
| Albanië | AL | en-US |
| Algerije | DZ | en-US, fr-FR, en-US |
| Amerikaans-Samoa | AS | en-US |
| Andorra | AD | en-US |
| Angola | AO | en-US, pt-PT |
| Anguilla | AI | en-US |
| Antarctica | Aq | en-US |
| Antigua en Barbuda | AG | en-US |
| Argentinië | AR | en-US, es-ES |
| Armenië | AM | en-US |
| Aruba | Aw | en-US |
| Australië | AU | en-US |
| Oostenrijk | AT | en-US, de-DE |
| Azerbeidzjan | AZ | en-US |
| Bahama's | BS | en-US |
| Bahrein | BH | en-US, ar-SA |
| Bangladesh | BD | en-US |
| Barbados | BB | en-US |
| Belarus | BY | en-US, ru-RU |
| België | BE | en-US, nl-NL |
| Belize | BZ | en-US, es-ES |
| Benin | BJ | en-US |
| Bermuda | Bm | en-US |
| Bhutan | BT | en-US |
| Bolivia | BO | en-US, es-ES |
| Bonaire | Bq | en-US |
| Bosnië en Herzegovina | BA | en-US |
| Botswana | BW | en-US |
| Bouveteiland | Bv | en-US |
| Brazilië | BR | en-US, pt-BR |
| Brits Territorium in de Indische Oceaan | I/O | en-US |
| Britse Maagdeneilanden | VG | en-US |
| Brunei | BN | en-US |
| Bulgarije | BG | en-US, bg-BG |
| Burkina Faso | BF | en-US |
| Burundi | BI | en-US |
| Cote d'Ivoire | CI | en-US, fr-FR |
| Cabo Verde | CV | en-US, pt-PT |
| Cambodja | KH | en-US |
| Kameroen | CM | en-US, fr-FR |
| Canada | CA (consistentie en beschikbaarheid) | en-US, fr-FR |
| Kaaimaneilanden | KY | en-US, en-US |
| Centraal-Afrikaanse Republiek | CF | en-US |
| Tsjaad | TD | en-US |
| Chili | CL | en-US, es-ES |
| Christmaseiland | CX | en-US |
| Cocoseilanden | CC | en-US |
| Colombia | CO | en-US, es-ES |
| Comoren | Km | en-US |
| Congo (DRC) | CD | en-US |
| Congo | Cg | en-US |
| Cookeilanden | Ck | en-US |
| Costa Rica | CR | en-US, es-ES |
| Kroatië | HR | en-US, hr-HR |
| Curaçao | Cw | en-US |
| Cyprus | CY | en-US |
| Tsjechië | CZ | en-US, cs- CSR |
| Denemarken | DK | en-US, da-DK |
| Djibouti | Dj | en-US |
| Dominica | DM | en-US |
| Dominicaanse Republiek | DO | en-US, es-ES |
| Ecuador | EC | en-US |
| Egypte | EG | en-US, ar-SA |
| El Salvador | SV | en-US, es-ES |
| Equatoriaal-Guinea | Gq | en-US |
| Eritrea | ER | en-US |
| Estland | EE | en-US, et-EE |
| eSwaautoriteit | SZ | en-US |
| Ethiopië | ET | en-US |
| Falklandeilanden | Fk | en-US |
| Faröer | Fo | en-US |
| Fiji | FJ | en-US |
| Finland | FI | en-US, fi-FI |
| Frankrijk | FR | en-US, fr-FR |
| Frans-Guyana | GF | en-US, fr-FR  |
| Frans-Polynesië | PF | en-US |
| Franse Gebieden in de zuidelijke Indische Oceaan | Tf | en-US |
| Gabon | Algemene beschikbaarheid | en-US |
| Gambia | GM | en-US |
| Georgië | GE | en-US |
| Duitsland | DE | en-US, de-DE |
| Ghana | GH | en-US |
| Gibraltar | Gi | en-US |
| Griekenland | GR | en-US, el-GR |
| Groenland | Gl | en-US |
| Grenada | Gd | en-US |
| Guadeloupe | GP | en-US |
| Guam | GU | en-US |
| Guatemala | GT | en-US, es-ES |
| Guernsey | Gg | en-US |
| Guinee | GN | en-US |
| Guinee-Bissau | GW | en-US |
| Guyana | GY | en-US |
| Haïti | HT | en-US |
| Heard- en McDonald-eilanden | Hm | en-US |
| Honduras | HN | en-US, es-ES |
| Hongkong SAR | HK | en-US, zh-HK |
| Hongarije | HU | en-US, hu-HU |
| IJsland | IS | en-US |
| India | IN | en-US, hi-IN |
| Indonesië | Id | en-US, id-id |
| Irak | IQ | en-US, ar-SA |
| Ierland | IE | en-US |
| Isle of Man | IM | en-US |
| Israël | IL | en-US, he-IL |
| Italië | IT | en-US, it-IT |
| Jamaica | JM | en-US |
| Jan Mayen | Xj | en-US |
| Japan | JP | en-US, ja-JP |
| Jersey | JE | en-US |
| Jordanië | JO | en-US, ar-SA |
| Kazachstan | KZ | en-US, kk-KZ |
| Kenia | KE | en-US |
| Kiribati | KI | en-US |
| Korea | KR | en-US, ko-KR |
| Kosovo | XK | en-US |
| Koeweit | KW | en-US, ar-SA |
| Kirgistan | KG | en-US, ru-RU |
| Laos | LA | en-US |
| Letland | LV | en-US, lv-LV |
| Libanon | LB | en-US, ar-SA |
| Lesotho | LS | en-US |
| Liberia | LR | en-US |
| Libië | LY | en-US, ar-SA |
| Liechtenstein | LI | en-US, de-DE |
| Litouwen | LT | en-US, lt-LT |
| Luxemburg | LU | en-US, fr-FR |
| Macau SAR | MO | en-US, zh-HK |
| Noord-Oost, FYRO | MK | en-US |
| Madagaskar | MG | en-US |
| Malawi | MW | en-US |
| Maleisië | MY | en-US, ms-MY |
| Maldiven | MV | en-US |
| Mali | ML | en-US |
| Malta | MT | en-US |
| Marshalleilanden | MH | en-US |
| Martinique | MQ | en-US |
| Mauritanië | MR | en-US |
| Mauritius | Mu | en-US, ar-SA |
| Mayotte | YT | en-US |
| Mexico | MX | en-US, es-ES |
| Micronesia | FM | en-US |
| Moldavië | MD | en-US, ro-RO |
| Monaco | MC | en-US, fr-FR |
| Mongolië | MN | en-US |
| Montenegro | ME | en-US |
| Montserrat | MS | en-US |
| Marokko | MA | en-US, fr-FR, en-US |
| Mozambique | MZ | en-US |
| Myanmar | MM | en-US |
| Namibië | NA | en-US |
| Nauru | NR | en-US |
| Nepal | NP | en-US |
| Nederland | NL | en-US, nl-NL |
| Nieuw-Caledonië | NC | en-US |
| Nieuw-Zeeland | NZ | en-US |
| Nicaragua | NI | en-US, es-ES |
| Niger | NE | en-US |
| Nigeria | NG | en-US |
| Niue | NU | en-US |
| Norfolk | Nf | en-US |
| Noordelijke Marianen | MP | en-US |
| Noorwegen | NO | en-US, nb-NO |
| Oman | OM | en-US, ar-SA |
| Pakistan | PK | en-US |
| Palau | PW | en-US |
| Palestijnse Autoriteit | PS | en-US |
| Panama | PA | en-US, es-ES |
| Papoea-Nieuw-Guinea | Pg | en-US |
| Paraguay | PY | en-US, es-ES |
| Peru | PE | en-US, es-ES |
| Filipijnen | PH | en-US |
| Pitcairneilanden | Pn | en-US |
| Polen | PL | en-US, pl-PL |
| Portugal | PT | en-US, pt-PT |
| Puerto Rico | PR | en-US, en-US |
| Qatar | QA | en-US, ar-SA |
| Réunion | RE | en-US |
| Roemenië | RO | en-US, ro-RO |
| Rusland | RU | en-US, ru-RU |
| Rwanda | RW | en-US, fr-FR |
| Sño Toñ en Prñncipe | ST | en-US, fr-FR |
| Saba | Xs | en-US |
| Saint-Barthélemy | BL | en-US |
| Saint Kitts en Nevis | KN | en-US |
| Saint Lucia | Lc | en-US, en-US |
| Saint-Martin | Mf | en-US, en-US |
| Saint-Pierre en Miquelon | PM | en-US |
| Saint Vincent en de Grenadines | VC | en-US |
| Samoa | WS | en-US |
| San Marino | Sm | en-US |
| Saoedi-Arabië | SA | en-US |
| Senegal | SN | en-US, fr-FR |
| Servië | RS | en-US, sr-Latn-RS, en-US |
| Seychellen | SC | en-US |
| Sierra Leone | SL | en-US |
| Singapore | SG | en-US, zh-SG |
| Sint Eustatius | Xe | en-US |
| Sint Maarten | Sx | en-US, en-US |
| Slowakije | SK | en-US, sk-SK |
| Slovenië | SI | en-US, sl-SI |
| Salomonseilanden | Sb | en-US |
| Somalië | SO | en-US |
| Zuid-Afrika | ZA | en-US |
| Zuid-Georgië en de Zuidelijke Sandwicheilanden | Gs | en-US |
| Zuid-Soedan | SS | en-US |
| Spanje | ES | en-US, es-ES, en-US, en-US |
| Sri Lanka | LK | en-US |
| St Helena, Ascension, Tristan da Cunha | SH | en-US |
| Suriname | SR | en-US |
| Svalbard | Sj | en-US |
| Zweden | SE | en-US, sv-SE |
| Zwitserland | CH | en-US, fr-FR, en-US, en-US |
| Taiwan | TW | en-US, zh-HK |
| Tadzjikistan | Tj | en-US |
| Tanzania | TZ | en-US |
| Thailand | TH | en-US, th-TH |
| Timor-Leste | TL | en-US |
| Togo | TG | en-US |
| Tokelau | Tk | en-US |
| Tonga | TO | en-US |
| Trinidad en Tobago | TT | en-US |
| Tunesië | TN | en-US, fr-FR, en-US |
| Turkije | TR | en-US, tr-TR |
| Turkmenistan | TM | en-US |
| Turks- en Caicos-eilanden | TC | en-US |
| Tuvalu | TV | en-US |
| Amerikaanse outlyingeilanden | UM | en-US |
| Amerikaanse Maagdeneilanden | VI | en-US |
| Oeganda | UG | en-US |
| Oekraïne | UA | en-US, uk-UA |
| Verenigde Arabische Emiraten | AE | en-US, ar-SA |
| Verenigd Koninkrijk | GB | en-US |
| Verenigde Staten | VS | en-US |
| Uruguay | UY | en-US, es-ES |
| Oezbekistan | UZ | en-US, ru-RU |
| Vanuatu | Vu | en-US |
| Vaticaanstad | VA | en-US |
| Venezuela | VE | en-US, es-ES |
| Vietnam | VN | en-US, vi-VN |
| Wallis en Walluna | WF | en-US |
| Jemen | Gij | en-US, ar-SA |
| Zambia | ZM | en-US |
| Zimbabwe | ZW | en-US |
