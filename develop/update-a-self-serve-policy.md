---
title: Een self-serve-beleid bijwerken
description: Een beleid voor self-serve bijwerken.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d94382e73fd2a79751fe5f8f8414df2befde584f
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445252"
---
# <a name="update-a-selfservepolicy"></a>Een SelfServePolicy bijwerken

In dit artikel wordt uitgelegd hoe u een beleid voor self-serve kunt bijwerken.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie ondersteund met referenties van toepassing en gebruiker.

## <a name="c"></a>C\#

Een beleid voor self-serve verwijderen:

1. Roep de [**methode IAggregatePartner.SelfServePolicies.ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) aan met de entiteits-id om een interface op te halen voor bewerkingen op het beleid.

2. Roep de [**methode Put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) of [**PutAsync aan**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) om het self-serve-beleid bij te werken.

``` csharp
// IAggregatePartner partnerOperations;
SelfServePolicy policy;

// All the operations executed on this partner operation instance will share the same correlation identifier but will differ in request identifier
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// updates the self-serve policies
partnerOperations.SelfServePolicies.ById(policy.id).Put(policy);
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                       |
|----------|-------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

- Een aanvraag-id en correlatie-id zijn vereist.
- Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.

| Naam                              | Type   | Beschrijving                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy)| object | De beleidsinformatie voor self-serve. |

#### <a name="selfservepolicy"></a>SelfServePolicy

In deze tabel worden de minimaal vereiste velden van de [SelfServePolicy-resource](self-serve-policy-resources.md#selfservepolicy) beschreven die nodig zijn om een nieuw beleid voor selfservice te maken.

| Eigenschap              | Type             | Beschrijving                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | Een self-serve beleids-id die wordt opgegeven wanneer het self-serve-beleid is gemaakt.     |
| SelfServeEntity       | SelfServeEntity  | De zelfhulpentiteit die toegang krijgt.                                                     |
| Grantor               | Grantor          | De grantor die toegang verleent.                                                                    |
| Machtigingen           | Matrix van machtigingen| Een matrix met [machtigingsbronnen.](self-serve-policy-resources.md#permission)                                                      |
| Etag                  | tekenreeks           | De Etag.                                                                                               |


### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PUT https://api.partnercenter.microsoft.com/v1/SelfServePolicy HTTP/1.1
Authorization: Bearer <token>
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Connection: Keep-Alive

{
    "id": "634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415",
    "selfServeEntity": {
        "selfServeEntityType": "customer",
        "tenantID": "0431a72c-7d8a-4393-b25e-ef63f5efb415"
    },
    "grantor": {
        "grantorType": "billToPartner",
        "tenantID": "634f6379-ad54-449b-9821-564f737158ab"
    },
    "permissions": [{
        "resource": "AzureReservedInstances",
        "action": "Purchase"
    }],
    "attributes": {
        "etag": "\"933523d1-3f63-4fc3-8789-5e21c02cdaed\"",
        "objectType": "SelfServePolicy"
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze API een [SelfServePolicy-resource](self-serve-policy-resources.md#selfservepolicy) voor het bijgewerkte beleid voor selfservice.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

Deze methode retourneert de volgende foutcodes:

| HTTP-statuscode     | Foutcode   | Beschrijving                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| 404                  | 600039       | Self-serve-beleid is niet gevonden                                            |
| 404                  | 600040       | De beleids-id voor self-serve is onjuist                                  |


### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 Ok
Content-Length: 834
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
Date: Tue, 14 Feb 2017 20:06:02 GMT

{
    "id": "634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415",
    "selfServeEntity": {
        "selfServeEntityType": "customer",
        "tenantID": "0431a72c-7d8a-4393-b25e-ef63f5efb415"
    },
    "grantor": {
        "grantorType": "billToPartner",
        "tenantID": "634f6379-ad54-449b-9821-564f737158ab"
    },
    "permissions": [{
        "resource": "AzureReservedInstances",
        "action": "Purchase"
    }],
    "attributes": {
        "etag": "\"1ec98034-a249-46f4-b9dd-9cd464fb5e47\"",
        "objectType": "SelfServePolicy"
    }
}
```
