---
title: Een lijst met producten ophalen (per land)
description: U kunt de productresource gebruiken om een verzameling producten per klantland op te halen.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 6ec3a642006a100ef85c0af9eeddd9daf00cc1cd981eabd5dddb77e60e15111f
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989437"
---
# <a name="get-a-list-of-products-by-country"></a>Een lijst met producten ophalen (per land)

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

U kunt de volgende methoden gebruiken om een verzameling producten op te halen die beschikbaar zijn in een bepaald land.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een land.

## <a name="c"></a>C\#

Een lijst met producten op te halen:

1. Gebruik de **verzameling IAggregatePartner.Products** om het land te selecteren met behulp van de **methode ByCountry().**

2. Selecteer de catalogusweergave met behulp van **de methode ByTargetView().**

3. (Optioneel) Selecteer het reserveringsbereik met behulp **van de methode ByReservationScope().**

4. (Optioneel) Selecteer het doelsegment met behulp van **de methode ByTargetSegment().**

5. Roep de **methode Get()** of **GetAsync()** aan om de verzameling te retourneren.

```csharp
IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.Products.ByCountry("US").ByTargetView("MicrosoftAzure").Get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.Products.ByCountry("US").ByTargetView("MicrosoftAzure").ByTargetSegment("commercial").Get();

// Get the products for Azure reservations which are applicable to Microsoft Azure (MS-AZR-0145P) subscriptions only.
ResourceCollection<Product> products = partnerOperations.Products.ByCountry("US").ByTargetView("AzureReservations").Get();

// Get the products for Azure reservations which are applicable to Azure plans only.
ResourceCollection<Product> products = partnerOperations.Products.ByCountry("US").ByTargetView("AzureReservations").ByReservationScope("AzurePlan").Get();

```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Een lijst met producten op te halen:

1. Gebruik de **functie IAggregatePartner.getProducts** om het land te selecteren met behulp van **de functie byCountry().**

2. Selecteer de catalogusweergave met behulp van **de functie byTargetView().**
3. (Optioneel) Selecteer het doelsegment met behulp van **de functie byTargetSegment().**

4. Roep de **functie get() aan** om de verzameling te retourneren.

```java
// IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").byTargetSegment("commercial").get();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Een lijst met producten op te halen:

1. Voer de [**opdracht Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) uit.

2. Selecteer de catalogus door de parameter **Catalog op te** geven.
3. (Optioneel) Selecteer het doelsegment door de **parameter Segment op te** geven.

```powershell
Get-PartnerProduct -Catalog 'Azure' -Segment 'commercial'
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                                                    |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/products?country={country}&targetView={targetView}&targetSegment={targetSegment} HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

Gebruik het volgende pad en de queryparameters om een lijst met producten op te halen.

| Naam                   | Type     | Vereist | Beschrijving                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| country                | tekenreeks   | Yes      | De land-/regio-id.                                                  |
| targetView             | tekenreeks   | Yes      | Identificeert de doelweergave van de catalogus. De ondersteunde waarden zijn: <br/><br/>**Azure,** dat alle Azure-items bevat<br/><br/>**AzureReservations,** dat alle Azure-reserveringsitems bevat<br/><br/>**AzureReservationsVM,** dat alle reserveringsitems voor virtuele machines (VM's) bevat<br/><br/>**AzureReservationsSQL,** dat alle reserveringsitems SQL omvat<br/><br/>**AzureReservationsCosmosDb,** dat alle reserveringsitems voor de Cosmos-database bevat<br/><br/>**MicrosoftAzure,** dat items bevat voor Microsoft Azure -abonnementen (**MS-AZR-0145P**) en Azure-abonnementen<br/><br/>**OnlineServices,** die alle onlineservice-items (inclusief producten van de commerciële marketplace) bevat<br/><br/>**Software**, die alle software-items bevat<br/><br/>**SoftwareSUSELinux,** dat alle SUSE Linux-software-items bevat<br/><br/>**SoftwarePerpetual,** dat alle permanente software-items bevat<br/><br/>**SoftwareAbonnementen,** die alle softwareabonnementitems bevat    |
| targetSegment          | tekenreeks   | No       | Identificeert het doelsegment. De weergave voor verschillende doelgroepen. De ondersteunde waarden zijn: <br/><br/>**Commerciële**<br/>**Onderwijs**<br/>**Regering**<br/>**Non-profit**  |
| reservationScope | tekenreeks   | No | Wanneer u een query uitvoert voor een lijst met producten voor Azure-reserveringen, geeft u op om een lijst met producten op te halen die van `reservationScope=AzurePlan` toepassing zijn op Azure-abonnementen. Sluit deze parameter uit om een lijst met producten voor Azure-reserveringen op te halen die van toepassing zijn op abonnementen van Microsoft Azure (**MS-AZR-0145P).**  |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-examples"></a>Voorbeelden van aanvragen

#### <a name="products-by-country"></a>Producten per land

Volg dit voorbeeld om een lijst met producten per land op te halen voor Microsoft Azure-abonnementen (MS-AZR-0145P) en Azure-abonnementen.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-azure-plan"></a>Azure VM-reserveringen (Azure-plan)

Volg dit voorbeeld om een lijst met producten per land op te halen voor Azure VM-reserveringen die van toepassing zijn op Azure-abonnementen.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureAzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a>Azure VM-reserveringen voor Microsoft Azure -abonnementen (MS-AZR-0145P)

Volg dit voorbeeld voor een lijst met producten per land voor Azure VM-reserveringen die van toepassing zijn op Microsoft Azure-abonnementen (MS-AZR-0145P).

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body een verzameling [**productresources.**](product-resources.md#product)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).

Deze methode retourneert de volgende foutcodes:

| HTTP-statuscode     | Foutcode   | Beschrijving                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| 403                  | 400030       | Toegang tot het aangevraagde targetSegment is niet toegestaan.                                                     |
| 403                  | 400036       | Toegang tot de aangevraagde targetView is niet toegestaan.                                                        |

### <a name="response-example"></a>Voorbeeld van antwoord

```http
{
    "totalCount": 19,
    "items": [
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
        },
        ...
    ],
    "links": {
        "self": {
            "uri": "/products?country=US&targetView=Azure",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
