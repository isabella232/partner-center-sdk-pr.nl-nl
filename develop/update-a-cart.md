---
title: Een winkelwagen bijwerken
description: Een order voor een klant in een winkelwagen bijwerken.
ms.date: 09/06/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 48fec2d9fb72d1a58fe79969e48ccd39a32c5ccc
ms.sourcegitcommit: 5f27733d7c984c29f71c8b9c8ba5f89753eeabc4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/07/2021
ms.locfileid: "123557283"
---
# <a name="update-a-cart"></a>Een winkelwagen bijwerken

Een order voor een klant in een winkelwagen bijwerken.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een winkelwagen-id voor een bestaande winkelwagen.

## <a name="c"></a>C\#

Als u een order voor een klant wilt bijwerken, moet u de winkelwagen op halen met behulp van de **methode Get()** door de klant- en winkelwagen-ID's door te geven met behulp van de **functie ById().** Wijzig de benodigde wijzigingen in de winkelwagen. Roep nu de **methode Put aan** met behulp van klant- en winkelwagen-ID's met behulp van de methode **ById().**

Roep ten slotte de **methode Put() of** **PutAsync()** aan om de bestelling te maken.

``` csharp
IAggregatePartner partnerOperations;
string customerId;
string cartId;

var cart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Get();

cart.LineItems.ToArray()[0].Quantity++;

var updatedCart = partnerOperations.Customers.ById(customerId).Cart.ById(cartId).Put(cart);
```

Zie het volgende voorbeeld om attestation te voltooien en aanvullende resellers op te nemen.

### <a name="api-sample---check-out-cart"></a>API-voorbeeld - Winkelwagen uitchecken

``` csharp
{
    "orders": [
        {
            "id": "f76c6b7f449d",
            "alternateId": "f76c6b7f449d",
            "referenceCustomerId": "f81d98dd-c2f4-499e-a194-5619e260344e",
            "billingCycle": "monthly",
            "currencyCode": "USD",
            "currencySymbol": "$",
            "lineItems": [
                {
                    "lineItemNumber": 0,
                    "offerId": "CFQ7TTC0LH0Z:0001:CFQ7TTC0K18P",
                    "subscriptionId": "ebc0beef-7ffb-4044-c074-16f324432139",
                    "termDuration": "P1M",
                    "transactionType": "New",
                    "friendlyName": "AI Builder Capacity add-on",
                    "quantity": 1,
                    "links": {
                        "product": {
                            "uri": "/products/CFQ7TTC0LH0Z?country=US",
                            "method": "GET",
                            "headers": []
                        },
                        "sku": {
                            "uri": "/products/CFQ7TTC0LH0Z/skus/0001?country=US",
                            "method": "GET",
                            "headers": []
                        },
                        "availability": {
                            "uri": "/products/CFQ7TTC0LH0Z/skus/0001/availabilities/CFQ7TTC0K18P?country=US",
                            "method": "GET",
                            "headers": []
                        }
                    }
                },
                {
                    "lineItemNumber": 1,
                    "offerId": "CFQ7TTC0LFLS:0002:CFQ7TTC0KDLJ",
                    "subscriptionId": "261bac40-7d88-4327-dfa3-dacd09222d62",
                    "termDuration": "P1Y",
                    "transactionType": "New",
                    "friendlyName": "Azure Active Directory Premium P1",
                    "quantity": 2,
                    "partnerIdOnRecord": "517285",
                    "additionalPartnerIdsOnRecord": 
                        "5357564",
                        "5357563"
                    ],
                 
   "links": {
                        "product": {
                            "uri": "/products/CFQ7TTC0LFLS?country=US",
                            "method": "GET",
                            "headers": []
                        },
                        "sku": {
                            "uri": "/products/CFQ7TTC0LFLS/skus/0002?country=US",
                            "method": "GET",
                            "headers": []
                        },
                        "availability": {
                            "uri": "/products/CFQ7TTC0LFLS/skus/0002/availabilities/CFQ7TTC0KDLJ?country=US",
                            "method": "GET",
                            "headers": []
                        }
                    }
                }
            ],
            "creationDate": "2021-08-18T07:52:23.1921872Z",
            "status": "pending",
            "transactionType": "UserPurchase",
            "links": {
                "self": {
                    "uri": "/customers/f81d98dd-c2f4-499e-a194-5619e260344e/orders/f76c6b7f449d",
                    "method": "GET",
                    "headers": []
                },
                "provisioningStatus": {
                    "uri": "/customers/f81d98dd-c2f4-499e-a194-5619e260344e/orders/f76c6b7f449d/provisioningstatus",
                    "method": "GET",
                    "headers": []
                },
                "patchOperation": {
                    "uri": "/customers/f81d98dd-c2f4-499e-a194-5619e260344e/orders/f76c6b7f449d",
                    "method": "PATCH",
                    "headers": []
                }
            },
            "client": {},
            "attributes": {
                "objectType": "Order"
            }
        }
    ],
    "attributes": {
        "objectType": "CartCheckoutResult"
    }
}

```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                 |
|---------|-------------------------------------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts/{cart-id} HTTP/1.1              |

### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende padparameters om de klant te identificeren en geef de winkelwagen op die moet worden bijgewerkt.

| Naam            | Type     | Vereist | Beschrijving                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **customer-id** | tekenreeks   | Yes      | Een met GUID opgemaakte klant-id die de klant identificeert.             |
| **cart-id**     | tekenreeks   | Yes      | Een cart-id met GUID-indeling die de winkelwagen identificeert.                     |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST Partner Center headers [voor meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de eigenschappen [van de winkelwagen](cart-resources.md) in de aanvraag body beschreven.

| Eigenschap              | Type             | Vereist        | Beschrijving                                                                                               |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | No              | Een winkelwagen-id die wordt opgegeven wanneer de winkelwagen is gemaakt.                                  |
| creationTimeStamp     | DateTime         | No              | De datum waarop de winkelwagen is gemaakt, in datum/tijd-indeling. Toegepast wanneer de winkelwagen is gemaakt.        |
| lastModifiedTimeStamp | DateTime         | No              | De datum waarop de winkelwagen het laatst is bijgewerkt, in datum/tijd-indeling. Toegepast wanneer de winkelwagen is gemaakt.    |
| expirationTimeStamp   | DateTime         | No              | De datum waarop de winkelwagen verloopt, in datum/tijd-indeling.  Toegepast nadat de winkelwagen is gemaakt.            |
| lastModifiedUser      | tekenreeks           | No              | De gebruiker die de winkelwagen voor het laatst heeft bijgewerkt. Toegepast nadat de winkelwagen is gemaakt.                             |
| lineItems             | Matrix met objecten | Yes             | Een matrix met [CartLineItem-resources.](cart-resources.md#cartlineitem)                                               |

In deze tabel worden de [eigenschappen van CartLineItem](cart-resources.md#cartlineitem) in de aanvraag body beschreven.

| Eigenschap             | Type                        | Vereist     | Beschrijving                                                                                        |
|----------------------|-----------------------------|--------------|----------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                      | No           | Een unieke id voor een winkelwagenregelitem. Toegepast nadat de winkelwagen is gemaakt.                |
| catalogId            | tekenreeks                      | Yes          | De id van het catalogusitem.                                                                       |
| Friendlyname         | tekenreeks                      | No           | Optioneel. De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.              |
| quantity             | int                         | Ja          | Het aantal licenties of exemplaren.     |
| currencyCode         | tekenreeks                      | No           | De valutacode.                                                                                 |
| billingCycle         | Object                      | Ja          | Het type factureringscyclus dat is ingesteld voor de huidige periode.                                              |
| deelnemers         | Lijst met objectreeksparen | No           | Een verzameling deelnemers aan de aankoop.                                                      |
| provisioningContext  | Woordenlijst<tekenreeks, tekenreeks>  | No           | Een context die wordt gebruikt voor het inrichten van de aanbieding.                                                          |
| orderGroup           | tekenreeks                      | No           | Een groep om aan te geven welke items bij elkaar kunnen worden geplaatst.                                            |
| fout                | Object                      | No           | Toegepast nadat de winkelwagen is gemaakt in het geval van een fout.                                                 |
| AdditionalPartnerIdsOnRecord | Tekenreeks | No | Wanneer een indirecte provider een order plaatst namens een indirecte reseller, vult u dit veld in met de MPN-id van de aanvullende indirecte **reseller** (nooit de id van de indirecte provider). Incentives zijn niet van toepassing op deze extra resellers. Er kunnen maximaal 5 indirecte resellers worden ingevoerd. Dit is alleen van toepassing zijn partners die werken binnen EU-/EFTA-landen.  |

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

Als dit lukt, retourneert deze methode de ingevulde [winkelwagenresource](cart-resources.md) in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

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
