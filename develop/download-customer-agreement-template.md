---
title: Een download koppeling voor de micro soft-sjabloon voor klant overeenkomsten ophalen
description: Een download koppeling voor de micro soft-sjabloon voor klant overeenkomsten ophalen.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 8c794d264ad64a42fa6ca823ddfc3841248c01cd
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767319"
---
# <a name="get-a-download-link-for-the-microsoft-customer-agreement-template"></a>Een download koppeling voor de micro soft-sjabloon voor klant overeenkomsten ophalen

**Van toepassing op:**

- Partnercentrum

De **AgreementDocument** -resource wordt momenteel alleen ondersteund door het partner centrum in de *open bare cloud van micro soft*. Deze resource is niet van toepassing op:

- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt beschreven hoe u een koppeling krijgt voor het downloaden van de micro soft-sjabloon voor klant overeenkomsten, op basis van het land en de taal van de klant.

## <a name="prerequisites"></a>Vereisten

- Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,14 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md). Dit scenario ondersteunt alleen app + gebruikers verificatie.

- Het land van de klant waarop de micro soft-sjabloon voor klant overeenkomst van toepassing is.

- De taal waarin de micro soft-sjabloon voor klant overeenkomsten moet worden gelokaliseerd.

> [!IMPORTANT]
>
> - De klant overeenkomst van micro soft is specifiek voor het land. Bij het aanvragen van een koppeling voor het downloaden van de micro soft-sjabloon voor klant overeenkomsten, moet u het juiste land opgeven op basis van de locatie van de klant. of lijst met ondersteunde landen, verwijzen we naar een [lijst met ondersteunde landen en talen](#list-of-supported-countries-and-languages).
>
> - Voor sommige landen is de micro soft-klant overeenkomst beschikbaar in meerdere talen. Kies voor de beste gebruikers ervaring de taal die het beste overeenkomt met de behoeften van de klant. Raadpleeg de [lijst met ondersteunde landen en talen](#list-of-supported-countries-and-languages)voor een lijst met ondersteunde talen.
> - Deze methode wordt alleen ondersteund in de micro soft-klanten overeenkomst.

## <a name="net"></a>.NET

Een koppeling ophalen om de micro soft-sjabloon voor klant overeenkomsten te downloaden:

1. Haal de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op. U moet de **ontbrekende templateid** van de micro soft-klant overeenkomst verkrijgen. Zie voor meer informatie de [meta gegevens van de overeenkomst ophalen voor de micro soft-klant overeenkomst](get-customer-agreement-metadata.md).

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   AgreementMetaData microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.   ByAgreementType(agreementType).Get().Items.Single();
   ```

2. Gebruik de verzameling IAggregatePartner. AgreementTemplates.

3. Roep de **ById** -methode aan en geef de **ontbrekende templateid** van de micro soft-klant overeenkomst op.

4. Haal de **document** eigenschap op.

5. Roep de methode **ByCountry** aan en geef het land van de klant op waarop de overeenkomst sjabloon van toepassing is. De query wordt standaard *ingesteld als de* methode niet is opgegeven. Raadpleeg de [lijst met ondersteunde landen en talen](#list-of-supported-countries-and-languages)voor een lijst met ondersteunde land codes. Deze methode is **hoofdletter gevoelig**.

6. Roep de methode **ByLanguage** aan en geef de taal op waarin de overeenkomst sjabloon moet worden gelokaliseerd. De query wordt standaard ingesteld op *nl-nl* als de methode niet is opgegeven, of de opgegeven land code niet wordt ondersteund voor het opgegeven land. Raadpleeg de [lijst met ondersteunde landen en talen](#list-of-supported-countries-and-languages)voor een lijst met ondersteunde taal codes.

7. Roep de methode Get of **GetAsync** **aan** .

   ```csharp
   // IAggregatePartner partnerOperations;

   string customerCountry = "US";

   string languageForLocalization = "en-US";

   var agreementDocument = partnerOperations.   AgreementTemplates.ById   (microsoftCustomerAgreementDetails.   TemplateId).Document.ByCountry   (customerCountry).ByLanguage   (languageForLocalization).Get();
   ```

Een volledig voor beeld vindt u in de [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.

## <a name="rest-request"></a>REST-aanvraag

Een koppeling ophalen om de micro soft-sjabloon voor klant overeenkomsten te downloaden:

1. Haal de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op. U moet de **ontbrekende templateid** van de micro soft-klant overeenkomst verkrijgen. Zie voor meer informatie de [meta gegevens van de overeenkomst ophalen voor de micro soft-klant overeenkomst](get-customer-agreement-metadata.md).

2. Maak een REST-aanvraag om een [ **AgreementDocument** -resource](./agreement-document-resources.md)op te halen. Zie voor een voor beeld de [syntaxis](#request-syntax) van de aanvraag. U moet de volgende informatie opgeven:

    - De **ontbrekende templateid** van de micro soft-klant overeenkomst.
    - Het land waarop de micro soft-sjabloon voor klant overeenkomst van toepassing is.
    - De taal waarin de micro soft-sjabloon voor klant overeenkomsten moet worden gelokaliseerd.

### <a name="request-syntax"></a>Syntaxis van aanvraag

Gebruik de volgende aanvraag syntaxis voor deze resource:

| Methode | Aanvraag-URI |
|--------|---------------------------------------------------------------------|
| GET | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreementtemplates/{Agreement-Template-id}/document? taal = {taal} &land = {Country} http/1.1 |

### <a name="uri-parameters"></a>URI-para meters

U kunt de volgende URI-para meters met uw aanvraag gebruiken:

| Naam                   | Type   | Vereist | Beschrijving                                 |
|------------------------|--------|----------|---------------------------------------------|
| overeenkomst-sjabloon-id  | tekenreeks | Yes      | De unieke id van het overeenkomst type. U kunt de ontbrekende templateid voor de micro soft-klant overeenkomst verkrijgen door de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op te halen. Zie voor meer informatie de [meta gegevens van de overeenkomst ophalen voor de micro soft-klant overeenkomst](./get-customer-agreement-metadata.md). Deze para meter is **hoofdletter gevoelig**.|
| country                | tekenreeks | No       | Hiermee wordt het land aangegeven waarop de overeenkomst sjabloon van toepassing is. De query wordt standaard *ingesteld als de* para meter niet is opgegeven. Raadpleeg de [lijst met ondersteunde landen en talen](#list-of-supported-countries-and-languages)voor een lijst met ondersteunde land codes.|
| language               | tekenreeks | No       | Hiermee wordt de taal aangegeven waarin de overeenkomst sjabloon moet worden gelokaliseerd. De query wordt standaard ingesteld op *nl-nl* als de para meter niet is opgegeven, of de land code die is opgegeven in't wordt ondersteund voor het opgegeven land. Raadpleeg de [lijst met ondersteunde landen en talen](#list-of-supported-countries-and-languages)voor een lijst met ondersteunde land codes.|

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, retourneert deze methode een [ **AgreementDocument** -resource](./agreement-document-resources.md) in de hoofd tekst van het antwoord.

De resource heeft een eigenschap **downloadUri** , die een URL-teken reeks bevat die kan worden gebruikt om de overeenkomst sjabloon te downloaden. Telkens wanneer u een query maakt, wordt er een andere koppeling geretourneerd. Deze koppeling verloopt na vijf minuten.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.

Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

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
> De land code-eigenschap is hoofdletter gevoelig. Zorg ervoor dat u de juiste behuizing gebruikt die in de onderstaande tabel is opgegeven.

| Land/regio                   | Landcode   | Ondersteunde taal code (s) |
|------------------------|--------|----------|
| Åland-eilanden | AX | en-US |
| Afghanistan | AF | en-US |
| Albanië | AL | en-US |
| Algerije | DZ | nl-nl, fr-FR en nl-US |
| Amerikaans-Samoa | AS | en-US |
| Andorra | AD | en-US |
| Angola | AO | en-US, pt-PT |
| Anguilla | AI | en-US |
| Antarctica | AQ | en-US |
| Antigua en Barbuda | AG | en-US |
| Argentinië | AR | en-US, es-ES |
| Armenië | AM | en-US |
| Aruba | AW | en-US |
| Australië | AU | en-US |
| Oostenrijk | AT | nl-nl, de-DE |
| Azerbeidzjan | AZ | en-US |
| Bahama's | BS | en-US |
| Bahrein | BH | en-US, AR-SA |
| Bangladesh | BD | en-US |
| Barbados | BB | en-US |
| Belarus | BY | en-US, ru-RU |
| België | BE | en-US, nl-NL |
| Belize | BZ | en-US, es-ES |
| Benin | BJ | en-US |
| Bermuda | BM | en-US |
| Bhutan | BT | en-US |
| Bolivia | BO | en-US, es-ES |
| Bonaire | BV | en-US |
| Bosnië en Herzegovina | BA | en-US |
| Botswana | BW | en-US |
| Bouveteiland | BW | en-US |
| Brazilië | BR | en-US, pt-BR |
| Brits Territorium in de Indische Oceaan | I/O | en-US |
| Britse Maagdeneilanden | VG | en-US |
| Brunei | BN | en-US |
| Bulgarije | BG | en-US, bg-BG |
| Burkina Faso | BF | en-US |
| Burundi | BI | en-US |
| Cote d'Ivoire | CI | nl-nl, fr-FR |
| Cabo Verde | CV | en-US, pt-PT |
| Cambodja | KH | en-US |
| Kameroen | CM | nl-nl, fr-FR |
| Canada | CA (consistentie en beschikbaarheid) | nl-nl, fr-FR |
| Kaaimaneilanden | KY | nl-nl, nl-nl |
| Centraal-Afrikaanse Republiek | CF | en-US |
| Tsjaad | TD | en-US |
| Chili | CL | en-US, es-ES |
| Christmaseiland | CX | en-US |
| Cocoseilanden | CC | en-US |
| Colombia | CO | en-US, es-ES |
| Comoren | KM | en-US |
| Congo (DRC) | CD | en-US |
| Congo | CG | en-US |
| Cookeilanden | CK | en-US |
| Costa Rica | CR | en-US, es-ES |
| Kroatië | HR | nl-nl, HR-HR |
| Curaçao | WAARNAAR | en-US |
| Cyprus | CY | en-US |
| Czechia | CZ | en-US, CS-CZ |
| Denemarken | DK | en-US, da-DK |
| Djibouti | DJ | en-US |
| Dominica | DM | en-US |
| Dominicaanse Republiek | DO | en-US, es-ES |
| Ecuador | EC | en-US |
| Egypte | EG | en-US, AR-SA |
| El Salvador | SV | en-US, es-ES |
| Equatoriaal-Guinea | GQ | en-US |
| Eritrea | ER | en-US |
| Estland | EE | en-US, et-EE |
| eSwatini | SZ | en-US |
| Ethiopië | ET | en-US |
| Falklandeilanden | FK | en-US |
| Faröer | FO | en-US |
| Fiji | FJ | en-US |
| Finland | FI | nl-nl, fi-FI |
| Frankrijk | FR | nl-nl, fr-FR |
| Frans-Guyana | GF | nl-nl, fr-FR  |
| Frans-Polynesië | PF | en-US |
| Franse Gebieden in de zuidelijke Indische Oceaan | TF | en-US |
| Gabon | Algemene beschikbaarheid | en-US |
| Gambia | GM | en-US |
| Georgië | GE | en-US |
| Duitsland | DE | nl-nl, de-DE |
| Ghana | GH | en-US |
| Gibraltar | GI | en-US |
| Griekenland | GR | nl-nl, El-GR |
| Groenland | BOEKHOUD | en-US |
| Grenada | GD | en-US |
| Guadeloupe | GP | en-US |
| Guam | GU | en-US |
| Guatemala | GT | en-US, es-ES |
| Guernsey | GG | en-US |
| Guinee | GN | en-US |
| Guinee-Bissau | GW | en-US |
| Guyana | GY | en-US |
| Haïti | HT | en-US |
| Heard- en McDonald-eilanden | HM | en-US |
| Honduras | HN | en-US, es-ES |
| Hongkong SAR | HK | nl-nl, zh-HK |
| Hongarije | HU | en-US, hu-HU |
| IJsland | IS | en-US |
| India | IN | en-US, Hi-IN |
| Indonesië | Id | nl-nl, id-ID |
| Irak | IQ | en-US, AR-SA |
| Ierland | IE | en-US |
| Isle of Man | IM | en-US |
| Israël | IL | en-US, hij-IL |
| Italië | IT | en-US, it-IT |
| Jamaica | JM | en-US |
| Jan Mayen | XJ | en-US |
| Japan | JP | en-US, ja-JP |
| Jersey | JE | en-US |
| Jordanië | JO | en-US, AR-SA |
| Kazachstan | KZ | nl-nl, KK-KZ |
| Kenia | KE | en-US |
| Kiribati | KI | en-US |
| Korea | KR | en-US, ko-KR |
| Kosovo | XK | en-US |
| Koeweit | KW | en-US, AR-SA |
| Kirgistan | KG | en-US, ru-RU |
| Laos | LA | en-US |
| Letland | LV | en-US, LV-LV |
| Libanon | LB | en-US, AR-SA |
| Lesotho | LS | en-US |
| Liberia | LR | en-US |
| Libië | LY | en-US, AR-SA |
| Liechtenstein | LI | nl-nl, de-DE |
| Litouwen | LT | en-US, lt-LT |
| Luxemburg | LU | nl-nl, fr-FR |
| Macau SAR | MO | nl-nl, zh-HK |
| Macedonië, voormalige Joegoslavische Republiek | MK | en-US |
| Madagaskar | MG | en-US |
| Malawi | MW | en-US |
| Maleisië | MY | nl-nl, MS-MY |
| Maldiven | MV | en-US |
| Mali | ML | en-US |
| Malta | MT | en-US |
| Marshalleilanden | MH | en-US |
| Martinique | MQ | en-US |
| Mauritanië | MR | en-US |
| Mauritius | MU | en-US, AR-SA |
| Mayotte | YT | en-US |
| Mexico | MX | en-US, es-ES |
| Micronesia | FM | en-US |
| Moldavië | MD | en-US, RO-RO |
| Monaco | MC | nl-nl, fr-FR |
| Mongolië | MN | en-US |
| Montenegro | ME | en-US |
| Montserrat | MS | en-US |
| Marokko | MA | nl-nl, fr-FR en nl-US |
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
| Norfolk | NF | en-US |
| Noordelijke Marianen | MP | en-US |
| Noorwegen | NO | nl-nl, nb-NO |
| Oman | OM | en-US, AR-SA |
| Pakistan | PK | en-US |
| Palau | PW | en-US |
| Palestijnse Autoriteit | PS | en-US |
| Panama | PA | en-US, es-ES |
| Papoea-Nieuw-Guinea | 3000CN | en-US |
| Paraguay | PY | en-US, es-ES |
| Peru | PE | en-US, es-ES |
| Filipijnen | PH | en-US |
| Pitcairneilanden | PN | en-US |
| Polen | PL | en-US, pl-PL |
| Portugal | PT | en-US, pt-PT |
| Puerto Rico | PR | nl-nl, nl-nl |
| Qatar | QA | en-US, AR-SA |
| Réunion | RE | en-US |
| Roemenië | RO | en-US, RO-RO |
| Rusland | RU | en-US, ru-RU |
| Rwanda | RW | nl-nl, fr-FR |
| Sao Tomé en principe | ST | nl-nl, fr-FR |
| Saba | X'EN | en-US |
| Saint-Barthélemy | BL | en-US |
| Saint Kitts en Nevis | KN | en-US |
| Saint Lucia | KREDIET | nl-nl, nl-nl |
| Saint-Martin | V | nl-nl, nl-nl |
| Saint-Pierre en Miquelon | PM | en-US |
| Saint Vincent en de Grenadines | VC | en-US |
| Samoa | WS | en-US |
| San Marino | 'S | en-US |
| Saoedi-Arabië | SA | en-US |
| Senegal | SN | nl-nl, fr-FR |
| Servië | RS | en-US, sr-Latn-RS en nl-US |
| Seychellen | SC | en-US |
| Sierra Leone | SL | en-US |
| Singapore | SG | en-US, zh-AG |
| Sint Eustatius | XE | en-US |
| Sint Maarten | SX | nl-nl, nl-nl |
| Slowakije | SK | en-US, sk-SK |
| Slovenië | SI | en-US, sl-SI |
| Salomonseilanden | SB | en-US |
| Somalië | SO | en-US |
| Zuid-Afrika | ZA | en-US |
| Zuid-Georgië en de Zuidelijke Sandwicheilanden | GS | en-US |
| Zuid-Soedan | SS | en-US |
| Spanje | ES | en-US, es-ES, nl-nl en nl-nl |
| Sri Lanka | LK | en-US |
| Sint-Helena, Ascension en Tristan da Cunha | SH | en-US |
| Suriname | SR | en-US |
| Svalbard | SJ | en-US |
| Zweden | SE | nl-nl, sv-SE |
| Zwitserland | CH | nl-nl, fr-FR, en-US en nl-nl |
| Taiwan | TW | nl-nl, zh-HK |
| Tadzjikistan | TJ | en-US |
| Tanzania | TZ | en-US |
| Thailand | TH | en-US, th-do |
| Timor-Leste | TL | en-US |
| Togo | TG | en-US |
| Tokelau | TK | en-US |
| Tonga | TO | en-US |
| Trinidad en Tobago | TT | en-US |
| Tunesië | TN | nl-nl, fr-FR en nl-US |
| Turkije | TR | en-US, tr-TR |
| Turkmenistan | TM | en-US |
| Turks- en Caicos-eilanden | TC | en-US |
| Tuvalu | TV | en-US |
| Amerikaanse ondergeschikte afgelegen eilanden | UM | en-US |
| Amerikaanse Maagden eilanden | VI | en-US |
| Oeganda | UG | en-US |
| Oekraïne | UA | nl-nl, UK-UA |
| Verenigde Arabische Emiraten | AE | en-US, AR-SA |
| Verenigd Koninkrijk | GB | en-US |
| Verenigde Staten | VS | en-US |
| Uruguay | UY | en-US, es-ES |
| Oezbekistan | UZ | en-US, ru-RU |
| Vanuatu | VU | en-US |
| Vaticaanstad | VA | en-US |
| Venezuela | VE | en-US, es-ES |
| Vietnam | VN | nl-nl, VI-VN |
| Wallis en Futuna | WF | en-US |
| Jemen | TEZAM | en-US, AR-SA |
| Zambia | ZM | en-US |
| Zimbabwe | ZW | en-US |
