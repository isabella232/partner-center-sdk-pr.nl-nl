---
title: Een lijst met beschikbaarheid voor een SKU ophalen (per land)
description: Het ophalen van een verzameling van Beschik baarheid voor het opgegeven product en de SKU per klant land.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: b97a4ce85b5edd9de1301a577988f8c54096ebeb
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767302"
---
# <a name="get-a-list-of-availabilities-for-a-sku-by-country"></a>Een lijst met beschikbaarheid voor een SKU ophalen (per land)

**Van toepassing op:**

- Partnercentrum

In dit artikel wordt beschreven hoe u een verzameling van Beschik baarheid in een bepaald land kunt ophalen voor een opgegeven product en SKU.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een product-id.

- Een SKU-id.

- Een land.

## <a name="c"></a>C\#

De lijst met beschik [baarheid voor](product-resources.md#availability) een [SKU](product-resources.md#sku)ophalen:

1. Volg de stappen in [een SKU ophalen op basis](get-a-sku-by-id.md) van de id om de interface te verkrijgen voor een specifieke SKU-bewerking.

2. Selecteer de eigenschap **Availabilities** van de SKU-interface om een interface met de bewerkingen voor Availabilities op te halen.

3. Beschrijving Gebruik de methode **ByTargetSegment ()** om de beschik baarheid per doel segment te filteren.

4. Roep **Get ()** of **GetAsync ()** aan om een verzameling van de beschik baarheid voor deze SKU op te halen.

``` csharp
IAggregatePartner partnerOperations;
string countryCode;
string productId;
string skuId;
string targetSegment;
string productIdForAzureReservation;
string skuIdForAzureReservation;

// Get the availabilities.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.Get();

// Get the availabilities, filtered by target segment.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productId).Skus.ById(skuId).Availabilities.BySegment(targetSegment).Get();

// Get the availabilities for an Azure reservation product and sku which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.ById(skuIdForAzureReservation).Availabilities.ByReservationScope("AzurePlan").Get();

// Get the availabilities for an Azure reservation product and sku which are applicable to Azure plans only.
var availabilities = partnerOperations.Products.ByCountry(countryCode).ById(productIdForAzureReservation).Skus.ById(skuIdForAzureReservation).Availabilities.Get();

```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                                                              |
|---------|------------------------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}/SKUs/{SKU-id}/Availabilities? land = {land nummer} &targetSegment = {target-segment} http/1.1     |

### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende pad-en query parameters om een lijst met Beschik baarheid voor een SKU op te halen.

| Naam                   | Type     | Vereist | Beschrijving                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| product-id             | tekenreeks   | Yes      | Een teken reeks waarmee het product wordt geïdentificeerd.                           |
| SKU-id                 | tekenreeks   | Yes      | Een teken reeks waarmee de SKU wordt geïdentificeerd.                               |
| land code           | tekenreeks   | Yes      | Een land/regio-ID.                                            |
| doel segment         | tekenreeks   | No       | Een teken reeks die het doel segment identificeert dat wordt gebruikt voor het filteren. |
| reservationScope | tekenreeks   | No | Bij het uitvoeren van een query op een lijst met Beschik baarheid voor een Azure reservation-SKU, geeft `reservationScope=AzurePlan` u een lijst op met Availabilities die van toepassing is op AzurePlan. Sluit deze para meter uit voor een lijst met Beschik baarheid die van toepassing is op Microsoft Azure (MS-AZR-0145P)-abonnementen.  |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-examples"></a>Aanvraag voorbeelden

#### <a name="availabilities-for-sku-by-country"></a>Beschik baarheid voor SKU per land

Volg dit voor beeld voor een lijst met Beschik baarheid voor een bepaalde SKU per land:

```http
GET http:// api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 70324727-62d8-4195-8f99-70ea25058d02
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58
```

#### <a name="availabilities-for-vm-reservations-azure-plan"></a>Beschik baarheid voor VM-reserve ringen (Azure-abonnement)

Volg dit voor beeld voor een lijst met Beschik baarheid per land voor Sku's voor Azure VM-reserve ring. Dit voor beeld is voor Sku's die van toepassing zijn op Azure-abonnementen:

```http
GET https://api.partnercenter.microsoft.com/v1/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="availabilities-for-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a>Beschik baarheid voor VM-reserve ringen voor Microsoft Azure-abonnementen (MS-AZR-0145P)

Volg dit voor beeld om een lijst op te halen van Beschik baarheid per land voor Azure VM-reserve ringen die van toepassing zijn op Microsoft Azure (MS-AZR-0145P)-abonnementen.

```http
GET https://api.partnercenter.microsoft.com/v1/productsDZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetView=AzureAzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord tekst een verzameling [**beschik**](product-resources.md#availability) bare resources.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes voor Partner Center](error-codes.md)voor een volledige lijst.

Deze methode retourneert de volgende fout codes:

| HTTP-status code     | Foutcode   | Beschrijving                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| 403                  | 400030       | Toegang tot de aangevraagde **targetSegment** is niet toegestaan.                                                     |

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Type: application/json; charset=utf-8
Server: Microsoft-IIS/10.0
MS-CorrelationId: 83b644b5-e54a-4bdc-b354-f96c525b3c58,83b644b5-e54a-4bdc-b354-f96c525b3c58
MS-RequestId: 70324727-62d8-4195-8f99-70ea25058d02,70324727-62d8-4195-8f99-70ea25058d02
X-Locale: en-US,en-US
X-SourceFiles: =?UTF-8?B?QzpcVXNlcnNcbWFtZW5kZVxkZXZcZHBzLXJwZVxSUEUuUGFydG5lci5TZXJ2aWNlLkNhdGFsb2dcV2ViQXBpc1xDYXRhbG9nU2VydmljZS5WMi5XZWJcdjFccHJvZHVjdHNcRFpIMzE4WjBCUTNRXHNrdXNcMDAwMVxhdmFpbGFiaWxpdGllcw==?=
X-Powered-By: ASP.NET
Date: Wed, 14 Mar 2018 22:19:37 GMT
Content-Length: 808

{
    "totalCount": 1,
    "items": [
        {
            "id": "DZH318XZXVNF",
            "productId": "DZH318Z0BQ3Q",
            "skuId": "0001",
            "catalogItemId": "DZH318Z0BQ3Q:0001:DZH318XZXVNF",
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
                    "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities/DZH318Z0HMKQ?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/products/DZH318Z0BQ3Q/skus/0001/availabilities?country=US&targetSegment=commercial",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
