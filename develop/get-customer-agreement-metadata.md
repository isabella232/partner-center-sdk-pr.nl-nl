---
title: Metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u de meta gegevens van de overeenkomst voor micro soft-klanten overeenkomst kunt ophalen.
ms.date: 8/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khakiali
ms.author: alikhaki
ms.openlocfilehash: c3ebecc51859c9d2240d319d823f7e555eaecc27
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767405"
---
# <a name="get-agreement-metadata-for-the-microsoft-customer-agreement"></a>Metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst ophalen

**Van toepassing op:**

- Partnercentrum

De meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst worden momenteel alleen ondersteund door het partner centrum in de *open bare cloud van micro soft*. Het is niet van toepassing op:

- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

U moet de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst ophalen voordat u het volgende kunt doen:

- [Bevestig de acceptatie van de micro soft-klant overeenkomst door de klant](./confirm-customer-consent-customer-agreement.md)
- [Een download koppeling voor de micro soft-sjabloon voor klant overeenkomsten ophalen](./download-customer-agreement-template.md)

## <a name="prerequisites"></a>Vereisten

- Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,14 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md). Dit scenario ondersteunt alleen app + gebruikers authenticatie.

## <a name="net-version-114-or-newer"></a>.NET (versie 1,14 of nieuwer)

De meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst ophalen:

1. Haal eerst de verzameling **IAggregatePartner. AgreementDetails** op.

2. Roep **ByAgreementType** -methode aan om de verzameling te filteren op de micro soft-klant overeenkomst.

3. Tot slot roept u de methode Get of **GetAsync** **aan** .

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCustomerAgreement";

var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

Een volledig voor beeld vindt u in de [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.

## <a name="rest-request"></a>REST-aanvraag

De meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst ophalen:

1. Maak een REST-aanvraag om de [AgreementMetaData](./agreement-metadata-resources.md) -verzameling op te halen.

2. Gebruik de **Agreement type** -query parameter om het resultaat te beperken tot alleen de micro soft-klant overeenkomst.

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode | Aanvraag-URI                                                         |
|--------|---------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreements? Agreement type = {Agreement-type} HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-para meters

| Naam                   | Type     | Vereist | Beschrijving                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| overeenkomst-type | tekenreeks | No | Gebruik deze para meter om het query-antwoord op een specifiek overeenkomst type te bereiken. De ondersteunde waarden zijn: <br/><br/>**MicrosoftCloudAgreement** die alleen overeenkomst meta gegevens van het type *MicrosoftCloudAgreement* bevat<br/><br/>**MicrosoftCustomerAgreement** die alleen overeenkomst met de meta gegevens van het type *MicrosoftCustomerAgreement* bevat.<br/><br/>**\*** Hiermee worden alle meta gegevens van de overeenkomst geretourneerd. (Alleen gebruiken **\*** als uw code de nood zakelijke runtime logica heeft voor het verwerken van onbekende overeenkomst typen, omdat micro soft op elk moment overeenkomst meta gegevens kan introduceren met nieuwe overeenkomst typen.)<br/><br/> **Opmerking:** Als de URI-para meter niet is opgegeven, wordt de query standaard ingesteld op **MicrosoftCloudAgreement** voor achterwaartse compatibiliteit.  |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een verzameling [ **AgreementMetaData** -resources](./agreement-metadata-resources.md) in de hoofd tekst van het antwoord.

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
    "totalCount": 1,
    "items": [
        {
            "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
            "agreementType": "MicrosoftCustomerAgreement",
            "agreementLink": "https://aka.ms/customeragreement",
            "versionRank": 0
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
