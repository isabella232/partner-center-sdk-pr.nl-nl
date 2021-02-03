---
title: Een lijst met producten ophalen (per land)
description: U kunt de product Resource gebruiken om een verzameling producten te verkrijgen op basis van het klant land.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: ea239aa008a5b7c33740e9c4697c3795908415cd
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767410"
---
# <a name="get-a-list-of-products-by-country"></a>Een lijst met producten ophalen (per land)

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

U kunt de volgende methoden gebruiken om een verzameling producten te verkrijgen die beschikbaar zijn in een bepaald land.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een land.

## <a name="c"></a>C\#

Een lijst met producten ophalen:

1. Gebruik de verzameling **IAggregatePartner. Products** om het land te selecteren met behulp van de methode **ByCountry ()** .

2. Selecteer de catalogus weergave met de methode **ByTargetView ()** .

3. Beschrijving Selecteer het reserverings bereik met de methode **ByReservationScope ()** .

4. Beschrijving Selecteer het doel segment met de methode **ByTargetSegment ()** .

5. Roep de methode **Get ()** of **GetAsync ()** aan om de verzameling te retour neren.

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

Een lijst met producten ophalen:

1. Gebruik de functie **IAggregatePartner. getProducts** om het land te selecteren met behulp van de functie **byCountry ()** .

2. Selecteer de catalogus weergave met behulp van de functie **byTargetView ()** .
3. Beschrijving Selecteer het doel segment met behulp van de functie **byTargetSegment ()** .

4. Roep de functie **Get ()** aan om de verzameling te retour neren.

```java
// IAggregatePartner partnerOperations;

// Get the products for the specified catalog view.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").get();

// Get the products filtered by target view and target segment.
ResourceCollection<Products> products = partnerOperations.getProducts().byCountry("US").byTargetView("Azure").byTargetSegment("commercial").get();
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Een lijst met producten ophalen:

1. Voer de opdracht [**Get-PartnerProduct**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerProduct.md) uit.

2. Selecteer de catalogus door de para meter **Catalog** op te geven.
3. Beschrijving Selecteer het doel segment door de para meter **segment** op te geven.

```powershell
Get-PartnerProduct -Catalog 'Azure' -Segment 'commercial'
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                                                                    |
|---------|----------------------------------------------------------------------------------------------------------------------------------------------- |
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Products? land = {country} &targetView = {targetView} &targetSegment = {TARGETSEGMENT} http/1.1 |

#### <a name="uri-parameters"></a>URI-para meters

Gebruik het volgende pad en de query parameters om een lijst met producten op te halen.

| Naam                   | Type     | Vereist | Beschrijving                                                             |
|------------------------|----------|----------|-------------------------------------------------------------------------|
| country                | tekenreeks   | Yes      | De ID van het land/de regio.                                                  |
| targetView             | tekenreeks   | Yes      | Hiermee wordt de doel weergave van de catalogus geïdentificeerd. De ondersteunde waarden zijn: <br/><br/>**Azure**, inclusief alle Azure-items<br/><br/>**AzureReservations**, inclusief alle Azure-reserverings items<br/><br/>**AzureReservationsVM**, dat alle reserve ringen items van virtuele machines (VM) omvat<br/><br/>**AzureReservationsSQL**, inclusief alle SQL-reserverings items<br/><br/>**AzureReservationsCosmosDb**, met alle reserverings items voor de Cosmos-data base<br/><br/>**MicrosoftAzure**, die items bevat voor Microsoft Azure-abonnementen (**MS-AZR-0145P**) en Azure-plannen<br/><br/>**OnlineServices**, dat alle online service-items omvat (inclusief commerciële Marketplace-Producten)<br/><br/>**Software**, inclusief alle software-items<br/><br/>**SoftwareSUSELinux**, dat alle software SuSE Linux-items omvat<br/><br/>**SoftwarePerpetual**, inclusief alle permanente software-items<br/><br/>**SoftwareSubscriptions**, inclusief alle software-abonnements items    |
| targetSegment          | tekenreeks   | No       | Hiermee wordt het doel segment aangeduid. De weer gave voor verschillende doel groepen. De ondersteunde waarden zijn: <br/><br/>**politieke**<br/>**personeel**<br/>**Government**<br/>**profit**  |
| reservationScope | tekenreeks   | No | Wanneer u een query uitvoert voor een lijst met producten voor Azure Reservations, geeft `reservationScope=AzurePlan` u een lijst op met producten die van toepassing zijn op Azure-abonnementen. Sluit deze para meter uit om een lijst met producten voor Azure-reserve ringen op te halen die van toepassing zijn op Microsoft Azure-abonnementen (**MS-AZR-0145P**).  |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-examples"></a>Aanvraag voorbeelden

#### <a name="products-by-country"></a>Producten op land

Volg dit voor beeld om een lijst met producten te verkrijgen per land voor Microsoft Azure (MS-AZR-0145P) en Azure-abonnementen.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=MicrosoftAzure HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-azure-plan"></a>Azure VM-reserve ringen (Azure-abonnement)

Volg dit voor beeld om een lijst met producten te verkrijgen per land voor Azure VM-reserve ringen die van toepassing zijn op Azure-abonnementen.

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureAzureReservationsVM&reservationScope=AzurePlan HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

#### <a name="azure-vm-reservations-for-microsoft-azure-ms-azr-0145p-subscriptions"></a>Azure VM-reserve ringen voor Microsoft Azure-abonnementen (MS-AZR-0145P)

Volg dit voor beeld om een lijst met producten te verkrijgen per land voor Azure VM-reserve ringen die van toepassing zijn op Microsoft Azure-abonnementen (MS-AZR-0145P).

```http
GET https://api.partnercenter.microsoft.com/v1/products?country=US&targetView=AzureReservationsVM HTTP/1.1
Authorization: Bearer
Accept: application/json
MS-RequestId: 031160b2-b0b0-4d40-b2b1-aaa9bb84211d
MS-CorrelationId: 7c1f6619-c176-4040-a88f-2c71f3ba4533
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord tekst een verzameling [**product**](product-resources.md#product) resources.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.

Deze methode retourneert de volgende fout codes:

| HTTP-status code     | Foutcode   | Beschrijving                                                                                               |
|----------------------|--------------|-----------------------------------------------------------------------------------------------------------|
| 403                  | 400030       | Toegang tot de aangevraagde targetSegment is niet toegestaan.                                                     |
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
