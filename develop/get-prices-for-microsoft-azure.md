---
title: Prijzen voor Microsoft Azure ophalen
description: Hoe u een Azure-tarief kaart krijgt met real-time prijzen voor een Azure-aanbieding. Prijzen voor Azure zijn vaak dynamisch en worden gewijzigd.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0716f0428b13604105b435a2ce8287a8b4609fea
ms.sourcegitcommit: 64c498d3571f2287305968890578bc7396779621
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97768690"
---
# <a name="get-prices-for-microsoft-azure"></a>Prijzen voor Microsoft Azure ophalen

**Van toepassing op**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Hoe u een [Azure-tarief kaart](azure-rate-card-resources.md) krijgt met real-time prijzen voor een Azure-aanbieding. Prijzen voor Azure zijn vaak dynamisch en worden gewijzigd.

Om het gebruik bij te houden en te helpen uw maandelijkse factuur en de facturen voor afzonderlijke klanten te voors pellen, kunt u deze Azure Rate Card-query combi neren om prijzen voor Microsoft Azure op te halen met een aanvraag om [de gebruiks gegevens van een klant voor Azure te verkrijgen](get-a-customer-s-utilization-record-for-azure.md).

De prijzen zijn afhankelijk van de markt en valuta en deze API houdt rekening met de locatie. De API maakt standaard gebruik van uw partner Profiel instellingen in partner centrum en uw browser taal, en deze instellingen zijn aanpasbaar. De locatie van het bewustzijn is vooral relevant als u de verkoop op meerdere markten beheert vanuit één gecentraliseerd kantoor. Zie [URI-para meters](#uri-parameters)voor meer informatie.

## <a name="c"></a>C\#

Als u de Azure-tarief kaart wilt ophalen, roept u de [**IAzureRateCard. Get**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.get) -methode aan om een [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) -resource te retour neren die de Azure-prijzen bevat.

```csharp
// IAggregatePartner partnerOperations;

var azureRateCard = partner.RateCards.Azure.Get();
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: Partner Center SDK-voor beelden **klasse**: GetAzureRateCard.cs

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Als u de Azure-tarief kaart wilt ophalen, roept u de functie **IAzureRateCard. Get** aan om de tarief kaart gegevens te retour neren die de Azure-prijzen bevatten.

```java
// IAggregatePartner partnerOperations;

AzureRateCard azureRateCard = partner.getRateCards().getAzure().get();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Als u de Azure-kaart wilt ophalen, voert u de opdracht [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) uit om de tarief kaart gegevens te retour neren die de prijzen van Azure bevatten.

```powershell
Get-PartnerAzureRateCard
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                        |
|---------|--------------------------------------------------------------------|
| **Toevoegen** | *{baseURL}*/v1/ratecards/Azure? Currency = {currency} &regio = {Region} |

### <a name="uri-parameters"></a>URI-para meters

| Naam     | Type   | Vereist | Beschrijving                                                                                                                                                                               |
|----------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| currency | tekenreeks | No       | Optionele ISO-code van drie letters voor de valuta waarin de resource tarieven worden gegeven (bijvoorbeeld `EUR` ). De standaardwaarde is `USD`. |
| regio   | tekenreeks | No       | Optionele ISO-land/regio code van twee letters waarmee de markt wordt aangegeven waar de aanbieding wordt gekocht (bijvoorbeeld `FR` ). De standaardwaarde is `US`.        |

U kunt de optionele X-locale- [header](headers.md#rest-request-headers) in uw aanvraag toevoegen. Als u de header X-locale niet opneemt, wordt de standaard waarde ("en-US") gebruikt.

- Als u in uw aanvraag valuta-en regio parameters opgeeft, wordt de waarde van de X-land instelling gebruikt om de taal van het antwoord te bepalen.

- Als u geen regio-en valuta parameters in uw aanvraag opgeeft, wordt de waarde van de X-land instelling gebruikt om de regio, valuta en taal van het antwoord te bepalen.

### <a name="request-header"></a>Aanvraagheader

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/ratecards/azure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 07ced227-3f32-4eeb-8062-f0bef849a9bc
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive
```

## <a name="rest-response"></a>REST-antwoord

Als de aanvraag is voltooid, wordt een [Azure-tarieven](azure-rate-card-resources.md) resource geretourneerd.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 1545508
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 57b25659-fc00-4215-87e7-2b09bac6845d
MS-RequestId: 870118d0-adbb-41a3-82d2-a3d45ade3c73
MS-CV: CYBB8PXMsEukJBIn.0
MS-ServerId: 201021413
Date: Wed, 01 Feb 2017 00:13:45 GMT

{
    "locale": "en",
    "currency": "USD",
    "isTaxIncluded": false,
    "meters": [{
            "id": "4b836326-7e19-46e6-8bce-1b19bb6cd91e",
            "name": "Unlimited Data - 1 Gbps",
            "rates": {
                "0": 7395.0
            },
            "tags": [],
            "category": "Networking",
            "subcategory": "ExpressRoute",
            "region": "Zone 2",
            "unit": "Connections",
            "includedQuantity": 0.0,
            "effectiveDate": "2015-09-01T00:00:00Z"
        }, {
            "id": "1e8f6d9f-8b40-4c97-80cc-cff87a290a93",
            "name": "Compute Hours",
            "rates": {
                "0": 3.9729
            },
            "tags": [],
            "category": "Cloud Services",
            "subcategory": "Standard_L16 Cloud Services",
            "region": "AU East",
            "unit": "1 Hour",
            "includedQuantity": 0.0,
            "effectiveDate": "2016-09-01T00:00:00Z"
        }, {
            "id": "7a2639ce-ae47-4413-9837-6b4f4b78be3d",
            "name": "Compute Hours",
            "rates": {
                "0": 0.1122
            },
            "tags": [],
            "category": "Virtual Machines",
            "subcategory": "Standard_D1_v2 VM (Windows)",
            "region": "BR South",
            "unit": "Hours",
            "includedQuantity": 0.0,
            "effectiveDate": "2017-01-01T00:00:00Z"
        }
    ],
    "offerTerms": [{
            "name": "Overage discount",
            "discount": 0.15,
            "excludedMeterIds": ["53cc0061-0fe2-4249-bf62-e1008c811f5c", "c82dbd27-c978-43a7-ad41-525a90d8962b"],
            "effectiveDate": "2014-01-01T00:00:00"
        }
    ],
    "attributes": {
        "objectType": "AzureRateCard"
    }
}
```
