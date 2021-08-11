---
title: De beschikbaarheid op id op halen
description: Hiermee haalt u de beschikbaarheid voor het opgegeven product en de SKU op met behulp van een beschikbaarheids-id.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: fccd566e83dab8994280fdee072c0d6f27b690d5292ed3973427088f46b30d6b
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115993551"
---
# <a name="get-the-availability-by-id"></a>De beschikbaarheid op id op halen

Hiermee haalt u de beschikbaarheid voor het opgegeven product en de SKU op met behulp van een beschikbaarheids-id.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een product-id.

- Een SKU-id.

- Een beschikbaarheids-id.

## <a name="c"></a>C\#

Als u meer informatie wilt over een specifieke [beschikbaarheid,](product-resources.md#availability)begint u met de stappen in Een [SKU](get-a-sku-by-id.md) op id op halen om de interface voor de bewerkingen van een specifieke [SKU op te](product-resources.md#sku) halen. Selecteer in de resulterende interface de eigenschap **Beschikbaarheid** om een interface te verkrijgen met de beschikbare bewerkingen voor beschikbaarheid. Geef daarna de beschikbaarheids-id door aan de **methode ById()** om de bewerkingen voor die specifieke beschikbaarheid op te halen en roep vervolgens **Get()** of **GetAsync()** aan om de beschikbaarheidsgegevens op te halen.

```csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;
string availabilityId;

// Get the availability details.
var availability = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.ById(availabilityId).Get();
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Als u meer informatie wilt over een specifieke [beschikbaarheid,](product-resources.md#availability)begint u met de stappen in Een [SKU](get-a-sku-by-id.md) op id op halen om de interface voor de bewerkingen van een specifieke [SKU op te](product-resources.md#sku) halen. Selecteer in de resulterende interface de **functie getAvailabilities** om een interface te verkrijgen met de beschikbare bewerkingen voor Beschikbaarheid. Geef daarna de beschikbaarheids-id door aan de **functie byId()** om de bewerkingen voor die specifieke beschikbaarheid op te halen en roep vervolgens de **functie get()** aan om de beschikbaarheidsdetails op te halen.

```java
IAggregatePartner partnerOperations;
String countryCode;
String productId;
String skuId;
String availabilityId;

// Get the availability details.
Availability availability = partnerOperations.getProducts().byCountry(countryCode).byId(productId).getSkus().byId(skuId).getAvailabilities().byId(availabilityId).get();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Als u details over een specifieke beschikbaarheid wilt [ophalen,](product-resources.md#availability)voert u [**get-PartnerProductAvailability**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) uit en geeft u de parameters **AvailabilityId,** **CountryCode,** **ProductId** en **SkuId** op om de beschikbaarheidsgegevens op te halen.

```powershell
Get-PartnerProductAvailability -Product $productId -SkuId $skuId -AvailabilityId $availabilityId
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/skus/{sku-id}/availabilities/{availability-id}?country={country-code} HTTP/1.1         |

### <a name="uri-parameter"></a>URI-parameter

Gebruik het volgende pad en de queryparameters om een specifieke beschikbaarheid te krijgen met behulp van een beschikbaarheids-id.

| Naam                   | Type     | Vereist | Beschrijving                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| product-id             | tekenreeks   | Yes      | Een tekenreeks met GUID-indeling die het product identificeert.            |
| sku-id                 | tekenreeks   | Yes      | Een tekenreeks met GUID-indeling die de SKU identificeert.                |
| availability-id        | tekenreeks   | Yes      | Een tekenreeks met GUID-indeling die de beschikbaarheid identificeert.       |
| country-code           | tekenreeks   | Yes      | Een land-/regio-id.                                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET http://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318XZXPHL?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 2e12a576-ded5-437e-a5ec-dbfbcbd1624c
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body een [beschikbaarheidsresource.](product-resources.md#availability)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)

Deze methode retourneert de volgende foutcodes:

| HTTP-statuscode     | Foutcode   | Beschrijving                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| 404                  | 400013       | Product is niet gevonden.                                                                                    |
| 404                  | 400018       | SKU is niet gevonden.                                                                                        |
| 404                  | 400019       | Beschikbaarheid niet gevonden.                                                                                   |

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58,83b644b5-e54a-4bdc-b354-f96c525b3c58
MS-RequestId: 2e12a576-ded5-437e-a5ec-dbfbcbd1624c,2e12a576-ded5-437e-a5ec-dbfbcbd1624c
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTNRXHNrdXNcMDAwMVxhdmFpbGFiaWxpdGllc1xEWkgzMThaMEhNS1E=?=
X-Powered-By: ASP.NET
Date: Wed, 14 Mar 2018 22:19:43 GMT
Content-Length: 440

{
    "id": "DZH318XZXPHL",
    "productId": "DZH318Z0BQ3Q",
    "skuId": "0001",
    "catalogItemId": "DZH318Z0BQ3Q:0001:DZH318XZXPHL",
    "defaultCurrency": {
        "code": "USD",
        "symbol": "$"
    },
    "segment": "commercial",
    "country": "US",
    "isPurchasable": true,
    "isRenewable": false,
    "terms": [{
        "duration": "P1Y",
        "description": "1 Year Prepaid"
    }],
    "product": { ... },
    "sku": { ... },
    "links": {
        "self": {
            "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318XZXPHL?country=US",
            "method": "GET",
            "headers": []
        }
    }
}
```
