---
title: Metagegevens van de overeenkomst voor Microsoft Cloud-overeenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u metagegevens van een overeenkomst voor Microsoft Cloud-overeenkomst.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 55a09752844f74caaf878f1e2dcfe3d8a70a283c5e0e9daefba89c558405690a
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994112"
---
# <a name="get-agreement-metadata-for-microsoft-cloud-agreement"></a>Metagegevens van de overeenkomst voor Microsoft Cloud-overeenkomst ophalen

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De **AgreementMetaData-resource** wordt momenteel alleen ondersteund door Partner Center in de openbare cloud van Microsoft.

## <a name="prerequisites"></a>Vereisten

- Als u de .NET SDK Partner Center, is versie 1.9 of nieuwer vereist.

- Als u de Java SDK Partner Center, is versie 1.8 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md). Dit scenario biedt ondersteuning voor app- en gebruikersverificatie.

## <a name="net-version-114-or-newer"></a>.NET (versie 1.14 of nieuwer)

De metagegevens van de overeenkomst voor de Microsoft Cloud-overeenkomst:

1. Haal eerst de **verzameling IAggregatePartner.AgreementDetails** op.

2. Roep **de methode ByAgreementType aan** om de verzameling te filteren op Microsoft Cloud-overeenkomst.

3. Roep ten slotte **de methode Get** of **GetAsync aan.**

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCloudAgreement";

var microsoftCloudAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

Een volledig voorbeeld vindt u in de [klasse GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)

## <a name="net-version-19---113"></a>.NET (versie 1.9 - 1.13)

De metagegevens van de overeenkomst voor de Microsoft Cloud-overeenkomst:

Haal eerst de **verzameling IAggregatePartner.AgreementDetails** op en roep vervolgens de **methoden Get** of **GetAsync aan.** Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud-overeenkomst:

```csharp
// IAggregatePartner partnerOperations;

var agreements = partnerOperations.AgreementDetails.Get();

AgreementMetaData microsoftCloudAgreement = agreements.Items.FirstOrDefault (agr => agr.AgreementType == AgreementType.MicrosoftCloudAgreement);
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

De metagegevens van de overeenkomst voor de Microsoft Cloud-overeenkomst:

Roep eerst de **functie IAggregatePartner.getAgreementDetails** aan en roep vervolgens de **functie get** aan. Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud-overeenkomst:

```java
// IAggregatePartner partnerOperations;

ResourceCollection<AgreementMetaData> agreements = partnerOperations.getAgreements().get();

AgreementMetaData microsoftCloudAgreement;

for (AgreementMetaData metadata : agreements)
{
    if(metadata.getAgreementType() == AgreementType.MicrosoftCloudAgreement)
    {
        microsoftCloudAgreement = metadata;
    }
}
```

Een volledig voorbeeld vindt u in de [klasse GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) van het [consoletest-app-project.](https://github.com/Microsoft/Partner-Center-Java-Samples)

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

De metagegevens van de overeenkomst voor de Microsoft Cloud-overeenkomst:

Gebruik de [**opdracht Get-PartnerAgreementDetail.**](/powershell/module/partnercenter/get-partneragreementdetail) Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud-overeenkomst:

```powershell
Get-PartnerAgreementDetail | Where-Object {$_.AgreementType -eq 'MicrosoftCloudAgreement'} | Select-Object -First 1
```

## <a name="rest-request"></a>REST-aanvraag

Als u metagegevens van overeenkomst voor Microsoft Cloud-overeenkomst, maakt u eerst een REST-aanvraag om de **verzameling AgreementMetaData op te** halen. Zoek vervolgens naar het item in de verzameling dat overeenkomt met de Microsoft Cloud-overeenkomst.

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI                                                         |
|--------|---------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/agreements HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een verzameling **AgreementMetaData-resources** in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
            "templateId": "998b88de-aa99-4388-a42c-1b3517d49490",
            "agreementType": "MicrosoftCloudAgreement",
            "agreementLink": "https://docs.microsoft.com/partner-center/agreements",
            "versionRank": 0
        }
    ],
    "links": {
        "self": {
            "uri": "/agreements",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

Als u de resource wilt identificeren in het antwoord dat overeenkomt met de Microsoft Cloud-overeenkomst, zoek dan naar de resource waarvan de eigenschap **agreementType** de waarde MicrosoftCloudAgreement heeft.
