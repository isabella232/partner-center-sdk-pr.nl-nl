---
title: Metagegevens van de overeenkomst voor Microsoft Cloud-overeenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u de meta gegevens van de overeenkomst kunt ophalen voor Microsoft Cloud overeenkomst.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: c6a404eb38c4c31d3e69bb598872b932d8985529
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767348"
---
# <a name="get-agreement-metadata-for-microsoft-cloud-agreement"></a>Metagegevens van de overeenkomst voor Microsoft Cloud-overeenkomst ophalen

**Van toepassing op**

- Partnercentrum

> [!NOTE]
> De **AgreementMetaData** -resource wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft. Het is niet van toepassing op:
> - Partner centrum beheerd door 21Vianet
> - Partnercentrum voor Microsoft Cloud Duitsland
> - Partnercentrum voor Microsoft Cloud for US Government

## <a name="prerequisites"></a>Vereisten

- Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,9 of nieuwer vereist.

- Als u de Java SDK van het partner centrum gebruikt, is versie 1,8 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md). Dit scenario ondersteunt app en verificatie van de gebruiker...

## <a name="net-version-114-or-newer"></a>.NET (versie 1,14 of nieuwer)

De meta gegevens van de overeenkomst voor Microsoft Cloud overeenkomst ophalen:

1. Haal eerst de verzameling **IAggregatePartner. AgreementDetails** op.

2. Roep **ByAgreementType** -methode aan om de verzameling te filteren op Microsoft Cloud overeenkomst.

3. Tot slot roept u de methode Get of **GetAsync** **aan** .

```csharp
// IAggregatePartner partnerOperations;

string agreementType = "MicrosoftCloudAgreement";

var microsoftCloudAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
```

Een volledig voor beeld vindt u in de [GetAgreementDetails](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetAgreementDetails.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.

## <a name="net-version-19---113"></a>.NET (versie 1,9-1,13)

U kunt als volgt meta gegevens van de overeenkomst ophalen voor de Microsoft Cloud overeenkomst:

Haal eerst de verzameling **IAggregatePartner. AgreementDetails** op en roep vervolgens de methoden Get of **GetAsync** **aan** . Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud overeenkomst:

```csharp
// IAggregatePartner partnerOperations;

var agreements = partnerOperations.AgreementDetails.Get();

AgreementMetaData microsoftCloudAgreement = agreements.Items.FirstOrDefault (agr => agr.AgreementType == AgreementType.MicrosoftCloudAgreement);
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

U kunt als volgt meta gegevens van de overeenkomst ophalen voor de Microsoft Cloud overeenkomst:

Roep eerst de functie **IAggregatePartner. getAgreementDetails** aan en roep vervolgens de Get-functie **aan** . Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud overeenkomst:

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

Een volledig voor beeld vindt u in de [GetAgreementDetails](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetAgreementDetails.java) -klasse in het [console test-app](https://github.com/Microsoft/Partner-Center-Java-Samples) -project.

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

U kunt als volgt meta gegevens van de overeenkomst ophalen voor de Microsoft Cloud overeenkomst:

Gebruik de opdracht [**Get-PartnerAgreementDetail**](/powershell/module/partnercenter/get-partneragreementdetail) . Zoek vervolgens naar het item in de verzameling, dat overeenkomt met de Microsoft Cloud overeenkomst:

```powershell
Get-PartnerAgreementDetail | Where-Object {$_.AgreementType -eq 'MicrosoftCloudAgreement'} | Select-Object -First 1
```

## <a name="rest-request"></a>REST-aanvraag

Als u de meta gegevens van de overeenkomst voor Microsoft Cloud overeenkomst wilt ophalen, maakt u eerst een REST-aanvraag om de **AgreementMetaData** -verzameling op te halen. Zoek vervolgens naar het item in de verzameling dat overeenkomt met de Microsoft Cloud overeenkomst.

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode | Aanvraag-URI                                                         |
|--------|---------------------------------------------------------------------|
| GET    | [*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/agreements http/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, retourneert deze methode een verzameling **AgreementMetaData** -resources in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

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

Als u de resource wilt identificeren in het antwoord dat overeenkomt met de Microsoft Cloud overeenkomst, zoekt u naar de resource waarvan de eigenschap **Agreement type** de waarde ' MicrosoftCloudAgreement ' heeft.
