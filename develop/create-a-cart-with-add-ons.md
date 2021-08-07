---
title: Een winkelwagen maken met invoegtoepassingen
description: Meer informatie over het gebruik Partner Center API's om een klantorder met invoegtoepassingen toe te voegen via een winkelwagen. In het artikel worden de vereisten en stappen voor het maken van een winkelwagen met invoegtoepassingen gedeeld.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: ed4b8be5171493f83aefef08253c748a7bfd90dc5f2b1e325e5ceba78e36bdc2
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991800"
---
# <a name="create-a-cart-with-add-ons-to-a-customer-order"></a>Een winkelwagen maken met invoegtoepassingen voor een klantorder

U kunt invoegtoepassingen aanschaffen via een winkelwagen. Zie Partneraanbiedingen in het Cloud Solution Provider programma voor meer informatie over [wat momenteel beschikbaar is om Cloud Solution Provider verkopen.](/partner-center/csp-offers)

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Met een winkelwagen kunnen een basisaanbieding en de bijbehorende invoegtoepassingen worden gekocht. Volg deze stappen om een winkelwagen te maken:

1. Een [**winkelwagenobject instanteren.**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart)

2. Maak een lijst met [**CartLineItem-objecten**](/dotnet/api/microsoft.store.partnercenter.models.carts.cartlineitem) die de basisaanbieding(en) vertegenwoordigen en wijs de lijst toe aan de eigenschap [**LineItems**](/dotnet/api/microsoft.store.partnercenter.models.carts.cart.lineitems) van de winkelwagen.

3. Vul onder het regelitem van elke basisaanbieding de lijst met **AddOnItems** in met andere **CartLineItem-objecten** die elk een invoeg-on vertegenwoordigen die wordt gekocht op basis van die basisaanbieding.

4. Verkrijg een interface voor winkelwagenbewerkingen door [**IAggregatePartner**](/dotnet/api/microsoft.store.partnercenter.iaggregatepartner) te gebruiken om de methode [**ICustomerCollection.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om de klant te identificeren en vervolgens de interface op te halen uit de eigenschap **Winkelwagen.**

5. Roep ten slotte de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.carts.icartcollection.createasync) om de winkelwagen te maken.

### <a name="c-example"></a>\#C-voorbeeld

```csharp
// IAggregatePartner partnerOperations;
// string customerId;

var cart = new Cart()
    {
        LineItems = new List<CartLineItem>()
        {
            new CartLineItem()
            {
                Id = 0,
                CatalogItemId = "A_base_offer_ID",
                FriendlyName = "Myofferpurchase",
                Quantity = 3,
                BillingCycle = BillingCycleType.Monthly,
                AddonItems = new List<CartLineItem>
                {
                    new CartLineItem
                    {
                        Id = 1,
                        CatalogItemId = "An_addon_item_ID",
                        BillingCycle = BillingCycleType.Monthly,
                        Quantity = 2,
                    },
                    new CartLineItem
                    {
                        Id = 2,
                        CatalogItemId = "Another_addon_item_ID",
                        BillingCycle = BillingCycleType.Monthly,
                        Quantity = 3
                    }
                }
            }
        }
    };

var createdCart = partnerOperations.Customers.ById(customerId).Carts.Create(cart);
```

Volg deze stappen om een winkelwagen te maken waarmee de aankoop van invoeg-invoegabonnementen voor bestaande basisabonnementen kan worden ingeschakeld:

1. Maak een **winkelwagen** met een nieuwe **CartLineItem** met de abonnements-id in de **eigenschap ProvisioningContext** met de sleutel ParentSubscriptionId.

2. Roep de **methode Create** of **CreateAsync aan.**

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var cart = new Cart()
    {
        LineItems = new List<CartLineItem>()
        {
            new CartLineItem()
            {
                Id = 0,
                CatalogItemId = "An_addon_item_ID",
                ProvisioningContext = new Dictionary<string, string>
                {
                    {
                        "ParentSubscriptionId", "An_existing_subscription_Id"
                    }
                },
                Quantity = 1,
                BillingCycle = BillingCycleType.Annual,
            }
        }
    };

var createdCart = partnerOperations.Customers.ById(selectedCustomerId).Carts.Create(cart);
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/carts HTTP/1.1                        |

#### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende padparameter om de klant te identificeren.

| Naam            | Type     | Vereist | Beschrijving                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **customer-id** | tekenreeks   | Yes      | Een in GUID opgemaakte klant-id die de klant identificeert.             |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de eigenschappen [van de winkelwagen](cart-resources.md) in de aanvraag body beschreven.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-----------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | No              | Een winkelwagen-id die wordt opgegeven wanneer de winkelwagen is gemaakt.                                  |
| creationTimeStamp     | DateTime         | No              | De datum waarop de winkelwagen is gemaakt, in datum/tijd-indeling. Toegepast wanneer de winkelwagen is gemaakt.         |
| lastModifiedTimeStamp | DateTime         | No              | De datum waarop de winkelwagen voor het laatst is bijgewerkt, in datum/tijd-indeling. Toegepast wanneer de winkelwagen is gemaakt.    |
| expirationTimeStamp   | DateTime         | No              | De datum waarop de winkelwagen verloopt, in datum/tijd-indeling.  Toegepast bij het maken van de winkelwagen.            |
| lastModifiedUser      | tekenreeks           | No              | De gebruiker die de winkelwagen voor het laatst heeft bijgewerkt. Toegepast bij het maken van de winkelwagen.                             |
| lineItems             | Matrix met objecten | Yes             | Een matrix van [CartLineItem-resources.](cart-resources.md#cartlineitem)                                             |

In deze tabel worden de [eigenschappen van CartLineItem](cart-resources.md#cartlineitem) in de aanvraag body beschreven.

| Eigenschap             | Type                             | Beschrijving                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                           | Een unieke id voor een winkelwagenregelitem. Toegepast bij het maken van de winkelwagen.                                                                   |
| catalogId            | tekenreeks                           | De id van het catalogusitem.                                                                                                                          |
| Friendlyname         | tekenreeks                           | Optioneel. De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het opsysen van ambiguïteit.                                                                 |
| quantity             | int                              | Het aantal licenties of instanties.                                                                                                                  |
| currencyCode         | tekenreeks                           | De valutacode.                                                                                                                                    |
| billingCycle         | Object                           | Het type factureringscyclus dat is ingesteld voor de huidige periode.                                                                                                 |
| deelnemers         | Lijst met objectreeksparen      | Een verzameling PartnerId on Record (MPN-id) voor de aankoop.                                                                                          |
| provisioningContext  | Woordenlijst<tekenreeks, tekenreeks>       | Een context die wordt gebruikt voor het inrichten van de aanbieding.                                                                                                             |
| orderGroup           | tekenreeks                           | Een groep om aan te geven welke items samen kunnen worden geplaatst.                                                                                               |
| addonItems           | Lijst met **CartLineItem-objecten** | Een verzameling winkelwagenregelitems voor invoegtoepassingen die worden aangeschaft voor het basisabonnement dat het resultaat is van de aankoop van het bovenliggende winkelwagenlijnitem. |
| fout                | Object                           | Toegepast nadat de winkelwagen is gemaakt als er een fout is opgetreden.                                                                                                    |

### <a name="request-example-new-base-subscription"></a>Voorbeeld van aanvraag (nieuw basisabonnement)

In het volgende REST-voorbeeld ziet u hoe u een winkelwagen maakt met invoegitems voor een nieuw basisabonnement.

```http
POST https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f931348a-6312-47d0-a8dd-31a386dedb8f
MS-CorrelationId: f73baf70-bbc3-43d0-8b29-dffa08ff9511

{
    "LineItems": [
        {
            "Id":0,
            "CatalogItemId":"91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "FriendlyName":"Myofferpurchase",
            "Quantity":3,
            "BillingCycle":"monthly",
            "AddonItems": [
                {
                    "Id":1,
                    "CatalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
                    "Quantity":2,
                    "BillingCycle":"monthly"
                },
                {
                    "Id":2,
                    "CatalogItemId":"43FCE491-76D1-4BCC-B709-8A288786DBAE",
                    "Quantity":3,
                    "BillingCycle":"monthly"
                }
            ]
        }
    ]
}
```

#### <a name="request-example-existing-base-subscription"></a>Voorbeeld van aanvraag (bestaand basisabonnement)

In het volgende REST-voorbeeld ziet u hoe u invoegtoepassingen toevoegt aan een bestaand basisabonnement.

```http
POST https://api.partnercenter.microsoft.com/v1/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 512a777a-5427-452d-9637-18421387e435
MS-CorrelationId: 182474ba-7303-4d0f-870a-8c7fba5ccc4b

{
    "LineItems": [
        {
            "Id":0,
            "CatalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
            "Quantity":1,
            "BillingCycle":"annual",
            "ProvisioningContext":{"ParentSubscriptionId":"97555B61-7461-477A-A98C-9C76148783E4"}
        }
    ]
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode de ingevulde [winkelwagenresource](cart-resources.md) in de antwoord-body.

#### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

#### <a name="response-example-new-base-subscription"></a>Voorbeeld van antwoord (nieuw basisabonnement)

```http
HTTP/1.1 201 Created
Content-Length: 958
Content-Type: application/json
MS-CorrelationId: f73baf70-bbc3-43d0-8b29-dffa08ff9511
MS-RequestId: f931348a-6312-47d0-a8dd-31a386dedb8f
X-Locale: en-US,en-US
Date: Thu, 01 Nov 2018 22:29:05 GMT

{
    "id":"dbe2f8d4-f21d-43e2-9356-cff6387c4ba1",
    "creationTimestamp":"2018-11-01T22:29:03.6900182Z",
    "lastModifiedTimestamp":"2018-11-01T22:29:03.6900182Z",
    "expirationTimestamp":"2018-11-01T22:44:05.0025799Z",
    "lastModifiedUser":"1824b7fc-2fac-4478-b177-66823c40ab75",
    "status":"Active",
    "lineItems": [
        {
            "id":0,
            "catalogItemId":"91FD106F-4B2C-4938-95AC-F54F74E9A239",
            "friendlyName":"Myofferpurchase",
            "quantity":3,
            "currencyCode":"USD",
            "billingCycle":"monthly",
            "orderGroup":"OMS-0",
            "addonItems": [
                {
                    "id":1,
                    "catalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
                    "quantity":2,
                    "currencyCode":"USD",
                    "billingCycle":"monthly",
                    "orderGroup":"OMS-0"
                },
                {
                    "id":2,
                    "catalogItemId":"43FCE491-76D1-4BCC-B709-8A288786DBAE",
                    "quantity":3,
                    "currencyCode":"USD",
                    "billingCycle":"monthly",
                    "orderGroup":"OMS-0"
                }
            ]
        }
],
    "links": {
        "self": {
            "uri":"/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts/dbe2f8d4-f21d-43e2-9356-cff6387c4ba1",
            "method":"GET",
            "headers":[
            ]
        }
    },
    "attributes": {
        "objectType":"Cart"
    }
}
```

#### <a name="response-example-existing-base-subscription"></a>Voorbeeld van antwoord (bestaand basisabonnement)

```http
HTTP/1.1 201 Created
Content-Length: 707
Content-Type: application/json
MS-CorrelationId: 182474ba-7303-4d0f-870a-8c7fba5ccc4b
MS-RequestId: 512a777a-5427-452d-9637-18421387e435
X-Locale: en-US,en-US
Date: Thu, 01 Nov 2018 22:46:18 GMT

{
    "id":"4d927e27-93d1-448b-abe5-819b66ecca22",
    "creationTimestamp":"2018-11-01T22:46:16.2996364Z",
    "lastModifiedTimestamp":"2018-11-01T22:46:16.2996364Z",
    "expirationTimestamp":"2018-11-01T23:01:18.7543264Z",
    "lastModifiedUser":"1824b7fc-2fac-4478-b177-66823c40ab75",
    "status":"Active",
    "lineItems": [
        {
            "id":0,
            "catalogItemId":"C94271D8-B431-4A25-A3C5-A57737A1C909",
            "quantity":1,
            "currencyCode":"USD",
            "billingCycle":"annual",
            "provisioningContext": {
                "parentSubscriptionId":"97555B61-7461-477A-A98C-9C76148783E4"
            },
            "orderGroup":"OMS-0"
        }
    ],
    "links": {
        "self": {
            "uri":"/customers/18ac2950-8ea9-4dfc-92a4-ff4d4cd57796/carts/4d927e27-93d1-448b-abe5-819b66ecca22",
            "method":"GET",
            "headers":[
            ]
        }
    },
    "attributes": {
        "objectType":"Cart"
    }
}
```
