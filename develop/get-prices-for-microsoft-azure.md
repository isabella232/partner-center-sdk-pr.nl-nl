---
title: Prijzen voor Microsoft Azure ophalen
description: Een Azure-tariefkaart met realtime prijzen voor een Azure-aanbieding krijgen. Azure-prijzen zijn zeer dynamisch en veranderen regelmatig.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4f66ab19ef3723fbaa27acff941cf48683a7c25c
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548784"
---
# <a name="get-prices-for-microsoft-azure"></a>Prijzen voor Microsoft Azure ophalen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Een [Azure-tariefkaart met](azure-rate-card-resources.md) realtime prijzen voor een Azure-aanbieding krijgen. Azure-prijzen zijn zeer dynamisch en veranderen regelmatig.

Als u het gebruik wilt bijhouden en uw maandelijkse factuur en de facturen voor afzonderlijke klanten wilt voorspellen, kunt u deze Azure Rate Card-query combineren om prijzen voor Microsoft Azure op te halen met een aanvraag om de gebruiksrecords van een klant voor Azure op te [halen.](get-a-customer-s-utilization-record-for-azure.md)

De prijzen verschillen per markt en valuta en deze API houdt rekening met de locatie. De API maakt standaard gebruik van uw partnerprofielinstellingen in Partner Center en uw browsertaal. Deze instellingen kunnen worden aangepast. De locatiebewustheid is vooral relevant als u de verkoop in meerdere markten beheert vanuit één gecentraliseerd kantoor. Zie [URI-parameters voor meer informatie.](#uri-parameters)

## <a name="c"></a>C\#

Als u de Azure-tariefkaart wilt verkrijgen, roept u de methode [**IAzureRateCard.Get**](/dotnet/api/microsoft.store.partnercenter.ratecards.iazureratecard.get) aan om een [**AzureRateCard-resource**](/dotnet/api/microsoft.store.partnercenter.models.ratecards.azureratecard) te retourneren die de Azure-prijzen bevat.

```csharp
// IAggregatePartner partnerOperations;

var azureRateCard = partner.RateCards.Azure.Get();
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project**: Partnercentrum-SDK Samples **Class**: GetAzureRateCard.cs

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Als u de Azure-tariefkaart wilt verkrijgen, roept u de **functie IAzureRateCard.get** aan om tariefkaartgegevens te retourneren die de Azure-prijzen bevatten.

```java
// IAggregatePartner partnerOperations;

AzureRateCard azureRateCard = partner.getRateCards().getAzure().get();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Als u de Azure-kaart wilt verkrijgen, voert u [**de opdracht Get-PartnerAzureRateCard**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerAzureRateCard.md) uit om tariefkaartgegevens te retourneren die de Azure-prijzen bevatten.

```powershell
Get-PartnerAzureRateCard
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                        |
|---------|--------------------------------------------------------------------|
| **Toevoegen** | *{baseURL}*/v1/ratecards/azure?currency={currency}&region={region} |

### <a name="uri-parameters"></a>URI-parameters

| Naam     | Type   | Vereist | Beschrijving                                                                                                                                                                               |
|----------|--------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| currency | tekenreeks | No       | Optionele ISO-code van drie letters voor de valuta waarin de resourcetarieven worden opgegeven (bijvoorbeeld `EUR` ). De standaardwaarde is `USD`. |
| regio   | tekenreeks | No       | Optionele iso-land-/regiocode van twee letters die de markt aangeeft waarop de aanbieding is gekocht (bijvoorbeeld `FR` ). De standaardwaarde is `US`.        |

U kunt de optionele X-Locale-header [opnemen](headers.md#rest-request-headers) in uw aanvraag. Als u de X-Locale-header niet op neemt, wordt de standaardwaarde ('en-US') gebruikt.

- Als u valuta- en regioparameters in uw aanvraag op geeft, wordt de waarde van X-Locale gebruikt om de taal van het antwoord te bepalen.

- Als u geen regio- en valutaparameters in uw aanvraag op geeft, wordt de waarde van X-Locale gebruikt om de regio, valuta en taal van het antwoord te bepalen.

### <a name="request-header"></a>Aanvraagheader

Zie REST-headers Partner Center [meer informatie.](headers.md)

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

Als de aanvraag is geslaagd, wordt een [Azure Rate Card-resource](azure-rate-card-resources.md) retourneert.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
