---
title: Metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u metagegevens van een overeenkomst voor Microsoft-klantovereenkomst.
ms.date: 8/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khakiali
ms.author: alikhaki
ms.openlocfilehash: 384fa227a103ed10dc2fd055afa7688d3b2a418504360eb4a5025615cf2a4f67
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989352"
---
# <a name="get-agreement-metadata-for-the-microsoft-customer-agreement"></a>Metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst ophalen

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Metagegevens van overeenkomst voor Microsoft-klantovereenkomst worden momenteel ondersteund door Partner Center alleen in de openbare Cloud van Microsoft.

U moet de metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst voordat u het volgende kunt doen:

- [Bevestig dat een klant de Microsoft-klantovereenkomst](./confirm-customer-consent-customer-agreement.md)
- [Een downloadkoppeling ophalen voor de Microsoft-klantovereenkomst sjabloon](./download-customer-agreement-template.md)

## <a name="prerequisites"></a>Vereisten

- Als u de .NET SDK Partner Center, is versie 1.14 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md). Dit scenario biedt alleen ondersteuning voor app-gebruikersverificatie.

## <a name="net-version-114-or-newer"></a>.NET (versie 1.14 of nieuwer)

De metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst:

1. Haal eerst de **verzameling IAggregatePartner.AgreementDetails** op.

2. Roep **de methode ByAgreementType aan** om de verzameling te filteren op Microsoft-klantovereenkomst.

3. Roep ten slotte **de methode Get** of **GetAsync aan.**

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCustomerAgreement";

var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

Een volledig voorbeeld vindt u in de [klasse GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)

## <a name="rest-request"></a>REST-aanvraag

De metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst:

1. Maak een REST-aanvraag om de [verzameling AgreementMetaData op te](./agreement-metadata-resources.md) halen.

2. Gebruik de **queryparameter agreementType** om het bereik van het resultaat alleen te Microsoft-klantovereenkomst.

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI                                                         |
|--------|---------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreements?agreementType={agreement-type} HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

| Naam                   | Type     | Vereist | Beschrijving                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| agreement-type | tekenreeks | No | Gebruik deze parameter om het bereik van de queryreactie te wijzigen in een specifiek overeenkomsttype. De ondersteunde waarden zijn: <br/><br/>**MicrosoftCloudAgreement dat** alleen metagegevens van overeenkomst bevat van het type *MicrosoftCloudAgreement*<br/><br/>**MicrosoftCustomerAgreement** dat alleen metagegevens van overeenkomst bevat van het type *MicrosoftCustomerAgreement*.<br/><br/>**\**_ die alle metagegevens van de overeenkomst retourneert. (Gebruik niet _* \* *_ tenzij uw code de benodigde runtimelogica heeft om onbekende typen overeenkomst af te handelen, omdat Microsoft op elk moment metagegevens van overeenkomst met nieuwe typen overeenkomst kan introduceren.) <br/> <br/> _* Opmerking:** als de URI-parameter niet is opgegeven, wordt de query standaard ingesteld op **MicrosoftCloudAgreement** voor compatibiliteit met eerdere compatibiliteit.  |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

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

Als dit lukt, retourneert deze methode een verzameling [ **AgreementMetaData-resources**](./agreement-metadata-resources.md) in de antwoord-body.

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
