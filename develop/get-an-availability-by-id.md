---
title: De beschik baarheid op basis van ID ophalen
description: Hiermee wordt de beschik baarheid voor het opgegeven product en de SKU opgehaald met behulp van een beschikbaarheids-ID.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 824303d40e1dcb0405246c8e29562c4527d147fd
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767181"
---
# <a name="get-the-availability-by-id"></a>De beschik baarheid op basis van ID ophalen

**Van toepassing op**

- Partnercentrum

Hiermee wordt de beschik baarheid voor het opgegeven product en de SKU opgehaald met behulp van een beschikbaarheids-ID.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een product-ID.

- EEN SKU-ID.

- Een beschikbaarheids-ID.

## <a name="c"></a>C\#

Als u meer wilt weten over een specifieke [Beschik baarheid](product-resources.md#availability), kunt u beginnen met de stappen in [een SKU ophalen op basis](get-a-sku-by-id.md) van de id om de interface te verkrijgen voor een specifieke [SKU](product-resources.md#sku) -bewerking. Selecteer in de resulterende interface de eigenschap **Availabilities** om een interface te verkrijgen met de beschik bare bewerkingen voor Availabilities. Daarna geeft u de beschikbaarheids-ID door aan de methode **ById ()** om de bewerkingen voor die specifieke Beschik baarheid te verkrijgen en roept u **Get ()** of **GetAsync (** ) aan om de beschikbaarheids gegevens op te halen.

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

Als u meer wilt weten over een specifieke [Beschik baarheid](product-resources.md#availability), kunt u beginnen met de stappen in [een SKU ophalen op basis](get-a-sku-by-id.md) van de id om de interface te verkrijgen voor een specifieke [SKU](product-resources.md#sku) -bewerking. Selecteer in de resulterende interface de functie **getAvailabilities** om een interface te verkrijgen met de beschik bare bewerkingen voor Availabilities. Daarna geeft u de beschikbaarheids-ID door aan de functie **byId ()** om de bewerkingen voor die specifieke Beschik baarheid op te halen. Vervolgens roept u de functie **Get ()** aan om de beschikbaarheids gegevens op te halen.

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

Als u meer wilt weten over een specifieke [Beschik baarheid](product-resources.md#availability), voert u de [**Get-PartnerProductAvailability**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProductAvailability.md) uit en geeft u de para meters **AvailabilityId**, **CountryCode**, **ProductID** en **SkuId** op om de beschikbaarheids gegevens op te halen.

```powershell
Get-PartnerProductAvailability -Product $productId -SkuId $skuId -AvailabilityId $availabilityId
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI |
|---------|------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/SKUs/{SKU-id}/Availabilities/{Availability-id}? land = {land nummer} http/1.1         |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende pad-en query parameters om een specifieke Beschik baarheid te verkrijgen met behulp van een beschikbaarheids-ID.

| Naam                   | Type     | Vereist | Beschrijving                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| product-id             | tekenreeks   | Yes      | Een teken reeks met een GUID-indeling waarmee het product wordt geïdentificeerd.            |
| SKU-id                 | tekenreeks   | Yes      | Een teken reeks met een GUID-indeling waarmee de SKU wordt geïdentificeerd.                |
| Beschik baarheid-id        | tekenreeks   | Yes      | Een teken reeks met een GUID-indeling waarmee de beschik baarheid wordt geïdentificeerd.       |
| land code           | tekenreeks   | Yes      | Een land/regio-ID.                                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, bevat de antwoord tekst een [beschikbaarheids](product-resources.md#availability) resource.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.

Deze methode retourneert de volgende fout codes:

| HTTP-status code     | Foutcode   | Beschrijving                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| 404                  | 400013       | Het product is niet gevonden.                                                                                    |
| 404                  | 400018       | SKU is niet gevonden.                                                                                        |
| 404                  | 400019       | Kan geen Beschik baarheid vinden.                                                                                   |

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
