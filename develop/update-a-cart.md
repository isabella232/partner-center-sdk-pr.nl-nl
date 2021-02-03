---
title: Een winkelwagen bijwerken
description: Hoe u een bestelling voor een klant in een winkel wagen bijwerkt.
ms.date: 10/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7c0806ccc87281b9b34005f22cd8d6ad57fb5de5
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767241"
---
# <a name="update-a-cart"></a>Een winkelwagen bijwerken

**Van toepassing op**

- Partnercentrum

Hoe u een bestelling voor een klant in een winkel wagen bijwerkt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een winkel wagen-ID voor een bestaande winkel wagen.

## <a name="c"></a>C\#

Als u een bestelling voor een klant wilt bijwerken, haalt u de winkel wagen op met de methode **Get ()** door de id van de klant en de winkel wagen te geven met behulp van de functie **ById ()** . Breng de benodigde wijzigingen aan in de winkel wagen. Roep nu de **put** -methode aan met behulp van de methode **ById ()** .

Roep ten slotte de methode **put ()** of **PutAsync ()** aan om de volg orde te maken.

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string cartId;

var cart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Get();

cart.LineItems.ToArray()[0].Quantity++;

var updatedCart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Put(cart);
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Carts/{Cart-id} http/1.1              |

### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende pad-para meters om de klant te identificeren en geef op welke winkel wagen moet worden bijgewerkt.

| Naam            | Type     | Vereist | Beschrijving                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **klant-id** | tekenreeks   | Yes      | Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.             |
| **Winkel wagen-id**     | tekenreeks   | Yes      | Een door de GUID ingedeelde winkel wagen-id waarmee de winkel wagen wordt aangeduid.                     |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de eigenschappen van de [winkel wagen](cart-resources.md) in de hoofd tekst van de aanvraag beschreven.

| Eigenschap              | Type             | Vereist        | Beschrijving                                                                                               |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | No              | Een winkel wagen-id die is opgegeven bij het maken van de winkel wagen.                                  |
| creationTimeStamp     | DateTime         | No              | De datum waarop de winkel wagen is gemaakt, in datum-tijd notatie. Wordt toegepast bij het maken van de winkel wagen.        |
| lastModifiedTimeStamp | DateTime         | No              | De datum waarop de winkel wagen voor het laatst is bijgewerkt, in datum-tijd notatie. Wordt toegepast bij het maken van de winkel wagen.    |
| expirationTimeStamp   | DateTime         | No              | De datum waarop de winkel wagen verloopt, in datum-tijd notatie.  Wordt toegepast bij het maken van de winkel wagen.            |
| lastModifiedUser      | tekenreeks           | No              | De gebruiker die de winkel wagen het laatst heeft bijgewerkt. Wordt toegepast bij het maken van de winkel wagen.                             |
| Regel items             | Matrix van objecten | Yes             | Een matrix met [CartLineItem](cart-resources.md#cartlineitem) -resources.                                               |

In deze tabel worden de eigenschappen van [CartLineItem](cart-resources.md#cartlineitem) in de hoofd tekst van de aanvraag beschreven.

| Eigenschap             | Type                        | Vereist     | Beschrijving                                                                                        |
|----------------------|-----------------------------|--------------|----------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                      | No           | Een unieke id voor een winkelwagen regel item. Wordt toegepast bij het maken van de winkel wagen.                |
| catalogId            | tekenreeks                      | Yes          | De id van het catalogus item.                                                                       |
| friendlyName         | tekenreeks                      | No           | Optioneel. De beschrijvende naam voor het item dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.              |
| quantity             | int                         | Ja          | Het aantal licenties of exemplaren.     |
| currencyCode         | tekenreeks                      | No           | De valuta code.                                                                                 |
| billingCycle         | Object                      | Ja          | Het type facturerings cyclus dat voor de huidige periode is ingesteld.                                              |
| deelnemers         | Lijst met object teken reeks paren | No           | Een verzameling deel nemers aan de aankoop.                                                      |
| provisioningContext  | Dictionary<teken reeks, teken reeks>  | No           | Een context die wordt gebruikt voor het inrichten van de aanbieding.                                                          |
| orderGroup           | tekenreeks                      | No           | Een groep om aan te geven welke items bij elkaar kunnen worden geplaatst.                                            |
| fout                | Object                      | No           | Wordt toegepast nadat de winkel wagen is gemaakt in het geval van een fout.                                                 |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PUT /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts/65faf57b-0205-47ee-92b3-08dcf233ea73/ HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
X-Locale: en-US
MS-PartnerCenter-Client: Partner Center .NET SDK
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 496
Expect: 100-continue

{
    {
        "Id":"b4c8fdea-cbe4-4d17-9576-13fcacbf9605",
        "CreationTimestamp":"2018-03-15T17:15:02.3840528Z",
        "LastModifiedTimestamp":"2018-03-15T17:15:02.3840528Z",
        "ExpirationTimestamp":"0001-01-01T00:00:00",
        "LastModifiedUser":"2713ccd7-ea3b-470a-9cfb-451d5d0482cc",
        "LineItems":[
            {
                "Id":0,
                "CatalogItemId":"DG7GMGF0DWTL:0001:DG7GMGF0DSJB",
                "FriendlyName":"A_sample_Azure_RI",
                "Quantity":2,
                "BillingCycle":"one_time",
                "ProvisioningContext": {
                    "SubscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
                    "Scope": "shared",
                    "Duration": "1Year"
                }
            }
        ],
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode de gevulde [Winkelwagen](cart-resources.md) resource in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 201 Created
Content-Length: 764
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 0e93c70c-977a-4a88-9580-7cf084c73286
MS-RequestId: 4fa6dad6-a89f-4875-8247-8294a10ae1cf
X-Locale: en-US,en-US
MS-CV: sF/wRa2ih0CzbABc.0
MS-ServerId: 000001
Date: Thu, 15 Mar 2018 17:15:01 GMT
{
    "id": "b4c8fdea-cbe4-4d17-9576-13fcacbf9605",
    "creationTimestamp": "2018-03-15T17:15:02.3840528Z",
    "lastModifiedTimestamp": "2018-03-15T17:15:02.3840528Z",
    "lastModifiedUser": "2713ccd7-ea3b-470a-9cfb-451d5d0482cc",
    "lineItems": [
        {
            "id": 0,
            "catalogItemId": "DG7GMGF0DWTL:0001:DG7GMGF0DSJB",
            "friendlyName": "A_sample_Azure_RI",
            "quantity": 2,
            "currencyCode": "USD",
            "billingCycle": "one_time",
            "ProvisioningContext": {
                "subscriptionId": "3D5ECED6-1151-44C7-AEE6-70A4BB725666",
                "scope": "shared",
                "duration": "1Year"
            }
            "orderGroup": "0"
        }
    ],
    "links": {
        "self": {
            "uri": "/v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/carts/b4c8fdea-cbe4-4d17-9576-13fcacbf9605/",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Cart"
    }
}
```
