---
title: Een overdracht maken
description: Een overdracht van abonnementen voor een klant maken.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d459a0a96912ab27f312bc73af16af2d4fdb518c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973703"
---
# <a name="create-a-transfer"></a>Een overdracht maken

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                 |
|----------|-------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/transfers HTTP/1.1                    |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende padparameter om de klant te identificeren.

| Naam            | Type     | Vereist | Beschrijving                                                            |
|-----------------|----------|----------|------------------------------------------------------------------------|
| **customer-id** | tekenreeks   | Ja      | Een met GUID opgemaakte klant-id die de klant identificeert.             |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de [Eigenschappen van TransferEntity](transfer-entity-resources.md) in de aanvraag body beschreven.

| Eigenschap              | Type          | Vereist  | Beschrijving                                                                                |
|-----------------------|---------------|-----------|--------------------------------------------------------------------------------------------|
| id                    | tekenreeks        | No    | Een transferEntity-id die wordt opgegeven wanneer de transferEntity is gemaakt.                               |
| createdTime           | DateTime      | Nee    | De datum waarop de transferEntity is gemaakt, in datum/tijd-indeling. Toegepast wanneer de transferEntity is gemaakt.      |
| lastModifiedTime      | DateTime      | Nee    | De datum waarop de transferEntity voor het laatst is bijgewerkt, in datum/tijd-indeling. Toegepast wanneer de transferEntity is gemaakt. |
| lastModifiedUser      | tekenreeks        | No    | De gebruiker die voor het laatst de transferEntity heeft bijgewerkt. Toegepast bij het maken van transferEntity.                          |
| customerName          | tekenreeks        | No    | Optioneel. De naam van de klant van wie de abonnementen worden overgedragen.                                              |
| customerTenantId      | tekenreeks        | No    | Een met GUID opgemaakte klant-id die de klant identificeert. Toegepast wanneer de transferEntity is gemaakt.         |
| partnertenantid       | tekenreeks        | No    | Een partner-id met GUID-indeling die de partner identificeert.                                                                   |
| sourcePartnerName     | tekenreeks        | No    | Optioneel. De naam van de organisatie van de partner die de overdracht start.                                           |
| sourcePartnerTenantId | tekenreeks        | Ja   | Een partner-id met GUID-indeling die de partner identificeert die de overdracht start.                                           |
| targetPartnerName     | tekenreeks        | No    | Optioneel. De naam van de organisatie van de partner waarop de overdracht is gericht.                                         |
| targetPartnerTenantId | tekenreeks        | Ja   | Een partner-id met GUID-indeling die de partner identificeert waarop de overdracht is gericht.                                  |
| lineItems             | Matrix met objecten | Ja| Een matrix van [TransferLineItem-resources.](transfer-entity-resources.md#transferlineitem)                                   |
| status                | tekenreeks        | No    | De status van de transferEntity. Mogelijke waarden zijn 'Actief' (kan worden verwijderd/verzonden) en 'Voltooid' (is al voltooid). Toegepast wanneer de transferEntity is gemaakt.|

In deze tabel worden de [eigenschappen van TransferLineItem](transfer-entity-resources.md#transferlineitem) in de aanvraag body beschreven.

|      Eigenschap       |            Type             | Vereist | Beschrijving                                                                                     |
|---------------------|-----------------------------|----------|-------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                     | No       | Een unieke id voor een overdrachtsregelitem. Toegepast wanneer de transferEntity is gemaakt.|
| subscriptionId       | tekenreeks                     | Ja      | De abonnements-id.                                                                         |
| quantity             | int                        | Nee       | Het aantal licenties of exemplaren.                                                                 |
| billingCycle         | Object                     | Nee       | Het type factureringscyclus dat is ingesteld voor de huidige periode.                                                |
| Friendlyname         | tekenreeks                     | No       | Optioneel. De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.                |
| partnerIdOnRecord    | tekenreeks                     | No       | PartnerId on Record (MPN-id) voor de aankoop die wordt gedaan wanneer de overdracht wordt geaccepteerd.              |
| offerId              | tekenreeks                     | No       | De aanbiedings-id.                                                                                |
| addonItems           | Lijst met **TransferLineItem-objecten** | Nee | Een verzameling transferEntity-regelitems voor addons die samen met het basisabonnement dat wordt overgedragen, worden overgedragen. Toegepast wanneer de transferEntity is gemaakt.|
| transferError        | tekenreeks                     | No       | Toegepast nadat transferEntity is geaccepteerd als er een fout is opgetreden.                                        |
| status               | tekenreeks                     | No       | De status van het regelitem in de transferEntity.                                                    |

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

Als dit lukt, retourneert deze methode de ingevulde [TransferEnity-resource](transfer-entity-resources.md) in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

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
