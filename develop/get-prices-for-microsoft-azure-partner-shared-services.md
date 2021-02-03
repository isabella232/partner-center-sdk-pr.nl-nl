---
title: Prijzen voor Microsoft Azure Partner Shared Services ophalen
description: Hoe u een Azure-tarief kaart krijgt met de prijzen voor de gedeelde services van Microsoft Azure partner.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: cd396c35b6b89de4d0f092ba4da738a2ed0ac633
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767563"
---
# <a name="get-prices-for-microsoft-azure-partner-shared-services"></a>Prijzen voor Microsoft Azure Partner Shared Services ophalen

**Van toepassing op**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Hoe u een [Azure-tarief kaart](azure-rate-card-resources.md) krijgt met de prijzen voor de gedeelde Services van Microsoft Azure partner.

De prijzen zijn afhankelijk van de markt en valuta en deze API houdt rekening met de locatie. De API maakt standaard gebruik van uw partner Profiel instellingen in partner centrum en uw browser taal, en deze instellingen zijn aanpasbaar. De locatie van het bewustzijn is vooral relevant als u de verkoop op meerdere markten beheert vanuit één gecentraliseerd kantoor.

## <a name="example-code"></a>Voorbeeld code

## <a name="c"></a>C\#

Als u de Azure-tarief kaart wilt ophalen, roept u de methode [**IAzureRateCard. GetShared**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.getshared) aan om een [**AzureRateCard**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) -resource te retour neren die de Azure-prijzen bevat.

```csharp
// IAggregatePartner partnerOperations;

var azureRateCard = partner.RateCards.Azure.GetShared();
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Als u de Azure-tarief kaart wilt ophalen, roept u de functie **IAzureRateCard. getShared** aan om de tarief kaart gegevens te retour neren die de Azure-prijzen bevatten.

```java
// IAggregatePartner partnerOperations;

AzureRateCard azureRateCard = partner.getRateCards().getAzure().getShared();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Als u de Azure-kaart wilt ophalen, voert u de opdracht [**Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) uit en geeft u de para meter **SharedServices** op om de tarief kaart gegevens te retour neren die de Azure-prijzen bevatten.

```powershell
Get-PartnerAzureRateCard -SharedServices
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                               |
|---------|---------------------------------------------------------------------------|
| **Toevoegen** | *{baseURL}*/v1/ratecards/Azure-Shared? Currency = {currency} &regio = {Region} |

### <a name="uri-parameters"></a>URI-para meters

| Naam     | Type   | Vereist | Beschrijving                                                                                                                                                                               |
|----------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| currency | tekenreeks | No       | Optionele ISO-code van drie letters voor de valuta waarin de resource tarieven worden gegeven (bijvoorbeeld `EUR` ). De standaard waarde is de valuta die is gekoppeld aan de markt in het Partner profiel. |
| regio   | tekenreeks | No       | Optionele ISO-land/regio code van twee letters waarmee de markt wordt aangegeven waar de aanbieding wordt gekocht (bijvoorbeeld `FR` ). De standaard waarde is de land/regio code die is ingesteld in het Partner profiel.        |

Als de optionele X-locale header is opgenomen in de aanvraag, bepaalt de waarde ervan de taal die wordt gebruikt voor de details in het antwoord.

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/ratecards/azure-shared HTTP/1.1
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
    "locale": "en-US",
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
