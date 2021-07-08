---
title: Een product ophalen op basis van id
description: Hiermee haalt u de opgegeven productresource op met behulp van een product-id.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 769a4307dc3cebdc7ebbdcf51d9f2b67a9f4b7c2
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874020"
---
# <a name="get-a-product-by-id"></a>Een product ophalen op basis van id

Hiermee haalt u de opgegeven productresource op met behulp van een product-id.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een product-id.

## <a name="c"></a>C\#

Als u een specifiek product op id wilt zoeken, gebruikt u de verzameling **IAggregatePartner.Products,** selecteert u het land met behulp van de **methode ByCountry()** en roept u vervolgens de **methode ById()** aan. Roep ten slotte de **methode Get()** of **GetAsync()** aan om het product te retourneren.

```csharp
// IAggregatePartner partnerOperations;

Product productDetail = partnerOperations.Products.ByCountry("US").ById("DZH318Z0BQ3Q").Get();
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](<../includes/java-sdk-support.md>)]

Als u een specifiek product op id wilt zoeken, gebruikt u de functie **IAggregatePartner.getProducts,** selecteert u het land met behulp van de functie **byCountry()** en roept u vervolgens de **functie byId()** aan. Roep ten slotte de **functie get() aan** om het product te retourneren.

```java
// IAggregatePartner partnerOperations;

Product productDetail = partnerOperations.getProducts().byCountry("US").byId("DZH318Z0BQ3Q").get();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](<../includes/powershell-module-support.md>)]

Als u een specifiek product wilt zoeken op id, voert u [**de opdracht Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) uit en geeft u de **parameter ProductId** op. De **parameter CountryCode** is opties. Als deze niet is opgegeven, wordt het land gebruikt dat is gekoppeld aan de reseller.

```powershell
Get-PartnerProduct -ProductId 'DZH318Z0BQ3Q'
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/products/{product-id}?country={country} HTTP/1.1  |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende padparameters om het opgegeven product op te halen.

| Naam                   | Type     | Vereist | Beschrijving                                                     |
|------------------------|----------|----------|-----------------------------------------------------------------|
| product-id             | tekenreeks   | Ja      | Een tekenreeks die het product identificeert.                           |
| country                | tekenreeks   | Ja      | Een land-/regio-id.                                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/products/{product-id}?country=US HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body een [Product-resource.](product-resources.md#product)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)

Deze methode retourneert de volgende foutcodes:

| HTTP-statuscode     | Foutcode   | Beschrijving                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| 404                  | 400013       | Product is niet gevonden.                                                     |

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 1918
Content-Type: application/json
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
MS-RequestId: ac943950-ba3d-47a0-bd2a-c5617a7fefe8
Date: Tue, 23 Jan 2018 23:13:01 GMT

{
    "id": "DZH318Z0BQ3Q",
    "title": "Virtual Machines DSv2 Series",
    "description": "Dsv2-series instances are the latest generation of D-series instances that will carry more powerful CPUs which are on average about 35% faster than D-series instances, and carry the same memory and disk configurations as the D-series. Dsv2-series instances are based on the latest generation 2.4 GHz Intel Xeon® E5-2673 v3 (Haswell) processor, and with Intel Turbo Boost Technology 2.0 can go to 3.2 GHz.",
    "productType": {
        "id": "Azure",
        "displayName": "Azure",
        "subType": {
            "id": "VirtualMachines",
            "displayName": "VirtualMachines"
        }
    },
    "isMicrosoftProduct": true,
    "publisherName": "Microsoft",
    "links": {
        "skus": {
            "uri": "/products/DZH318Z0BQ3Q/skus?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/products/DZH318Z0BQ3Q?country=US",
            "method": "GET",
            "headers": []
        }
    }
}
```
