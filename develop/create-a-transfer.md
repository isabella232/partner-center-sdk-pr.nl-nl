---
title: Een overdracht maken
description: Een overdracht van abonnementen voor een klant maken.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d5e70cc5b7ce4fcfa715f581a2151f0b8d1922b0
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767204"
---
# <a name="create-a-transfer"></a>Een overdracht maken

**Van toepassing op:**

- Partnercentrum

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/transfers http/1.1                    |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende para meter voor het identificeren van de klant.

| Naam            | Type     | Vereist | Beschrijving                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **klant-id** | tekenreeks   | Yes      | Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd.             |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de eigenschappen van [TransferEntity](transfer-entity-resources.md) in de hoofd tekst van de aanvraag beschreven.

| Eigenschap              | Type          | Vereist  | Beschrijving                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| id                    | tekenreeks        | No    | Een transferEntity-id die wordt geleverd bij het maken van de transferEntity.                               |
| createdTime           | DateTime      | No    | De datum waarop de transferEntity is gemaakt, in datum-tijd notatie. Wordt toegepast wanneer de transferEntity is gemaakt.      |
| lastModifiedTime      | DateTime      | No    | De datum waarop de transferEntity voor het laatst is bijgewerkt, in datum-tijd notatie. Wordt toegepast wanneer de transferEntity is gemaakt. |
| lastModifiedUser      | tekenreeks        | No    | De gebruiker die de transferEntity voor het laatst heeft bijgewerkt. Toegepast bij het maken van transferEntity.                          |
| customerName          | tekenreeks        | No    | Optioneel. De naam van de klant wiens abonnementen worden overgedragen.                                              |
| customerTenantId      | tekenreeks        | No    | Een door de klant-id opgemaakte GUID waarmee de klant wordt geïdentificeerd. Wordt toegepast wanneer de transferEntity is gemaakt.         |
| partnertenantid       | tekenreeks        | No    | Een door de GUID opgemaakte partner-id waarmee de partner wordt geïdentificeerd.                                                                   |
| sourcePartnerName     | tekenreeks        | No    | Optioneel. De naam van de organisatie van de partner die de overdracht initieert.                                           |
| sourcePartnerTenantId | tekenreeks        | Yes   | Een door de GUID opgemaakte partner-id waarmee de partner wordt geïdentificeerd die de overdracht initieert.                                           |
| targetPartnerName     | tekenreeks        | No    | Optioneel. De naam van de organisatie van de partner waarop de overdracht is gericht.                                         |
| targetPartnerTenantId | tekenreeks        | Yes   | Een door de GUID opgemaakte partner-id waarmee de partner wordt geïdentificeerd voor wie de overdracht is gericht.                                  |
| Regel items             | Matrix van objecten | Yes| Een matrix met [TransferLineItem](transfer-entity-resources.md#transferlineitem) -resources.                                   |
| status                | tekenreeks        | No    | De status van de transferEntity. Mogelijke waarden zijn ' Active ' (kunnen worden verwijderd/verzonden) en ' voltooid ' (is al voltooid). Wordt toegepast wanneer de transferEntity is gemaakt.|

In deze tabel worden de eigenschappen van [TransferLineItem](transfer-entity-resources.md#transferlineitem) in de hoofd tekst van de aanvraag beschreven.

|      Eigenschap       |            Type             | Vereist | Beschrijving                                                                                     |
|---------------------|-----------------------------|----------|-------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                     | No       | Een unieke id voor een regel item voor de overdracht. Wordt toegepast wanneer de transferEntity is gemaakt.|
| subscriptionId       | tekenreeks                     | Yes      | De abonnements-id.                                                                         |
| quantity             | int                        | No       | Het aantal licenties of exemplaren.                                                                 |
| billingCycle         | Object                     | No       | Het type facturerings cyclus dat voor de huidige periode is ingesteld.                                                |
| friendlyName         | tekenreeks                     | No       | Optioneel. De beschrijvende naam voor het item dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.                |
| partnerIdOnRecord    | tekenreeks                     | No       | Partner on record (MPNID) voor de aankoop die plaatsvindt wanneer de overdracht wordt geaccepteerd.              |
| offerId              | tekenreeks                     | No       | De aanbiedings-id.                                                                                |
| addonItems           | Lijst met **TransferLineItem** -objecten | No | Een verzameling transferEntity-regel items voor addons die worden overgedragen samen met het basis abonnement dat wordt overgedragen. Wordt toegepast wanneer de transferEntity is gemaakt.|
| transferError        | tekenreeks                     | No       | Wordt toegepast nadat transferEntity is geaccepteerd in het geval van een fout.                                        |
| status               | tekenreeks                     | No       | De status van de lineitem in de transferEntity.                                                    |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST /v1/customers/d6bf25b7-e0a8-4f2d-a31b-97b55cfc774d/transfers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4fa6dad6-a89f-4875-8247-7294a10ae1cf
MS-CorrelationId: 0e93c70c-977c-4a88-9580-7cf084c73286
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Expect: 100-continue

{
    "sourcePartnerTenantId": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "targetPartnerTenantId": "656218b1-80c9-40b2-83ae-3a2703b55271",
    "lineItems": [
        {
            "subscriptionId": "7291BFBF-1772-4C5B-A624-18B6152CD8CB",
            "partnerIdOnRecord": "517285"
        },
        {
            "subscriptionId": "6C0B221B-8DF9-4F4A-A5BB-4C9CBB7B27B0",
            "partnerIdOnRecord": "517285"
        }
    ]
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode de gevulde [TransferEnity](transfer-entity-resources.md) -resource in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 201 Created
Content-Length: 138
Content-Type: application/json; charset=utf-8
MS-RequestId: 4fa6dad6-a89f-4875-8247-7294a10ae1cf
MS-CorrelationId: 0e93c70c-977c-4a88-9580-7cf084c73286
X-Locale: en-US,en-US
{
    "id": "67c5b05b-09b5-47ba-9047-5056fe2afa4f",
    "status": "Active",
    "createdTime": "2020-03-24T20:44:14.9602781Z",
    "lastModifiedTime": "2020-03-24T20:44:15Z",
    "customerTenantId": "823c6c3f-9259-4d51-bae2-5dd06743177f",
    "partnertenantid": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "sourcePartnerTenantId": "da6c51b5-1246-4a42-b4ab-cbf38df54537",
    "targetPartnerTenantId": "656218b1-80c9-40b2-83ae-3a2703b55271",
    "lastModifiedUser": "d0648481-b615-45c9-8cd1-ff87940dbdc4",
    "lineItems": [
        {
            "id": 0,
            "subscriptionId": "7291BFBF-1772-4C5B-A624-18B6152CD8CB",
            "offerId": "50E9A47A-7B4D-4970-9D90-CAE927F53753",
            "billingCycle": "annual",
            "friendlyName": "Dynamics 365 for Sales Enterprise Attach to Qualifying Dynamics 365 Base Offer",
            "quantity": 1,
            "addonItems": [
                {
                    "id": 0,
                    "subscriptionId": "D738C6C9-DDBD-46E9-B316-65F9D9B3ECB4",
                    "offerId": "2BCF9FE8-8B65-4FCF-9240-419203FB8CF4",
                    "billingCycle": "annual",
                    "friendlyName": "Dynamics 365 - Additional Production Instance (Qualified Offer)",
                    "quantity": 4
                }
            ]
        },
        {
            "id": 0,
            "subscriptionId": "6C0B221B-8DF9-4F4A-A5BB-4C9CBB7B27B0",
            "offerId": "455DDD41-32ED-4E2D-B3A2-BBCB22CAA467",
            "billingCycle": "annual",
            "friendlyName": "Dynamics 365 Customer Engagement Plan Patch",
            "quantity": 8,
            "addonItems": []
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/823c6c3f-9259-4d51-bae2-5dd06743177f/transfers/67c5b05b-09b5-47ba-9047-5056fe2afa4f",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "TransferEntity"
    }
}
```
