---
title: Een selfservice beleid bijwerken
description: Een selfservice beleid bijwerken.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4d53ab8e5b8ef5b7be83360a3f43ec7791b2e3b4
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/08/2020
ms.locfileid: "97768669"
---
# <a name="update-a-selfservepolicy"></a>Een SelfServePolicy bijwerken

**Van toepassing op:**

- Partnercentrum

In dit onderwerp wordt uitgelegd hoe u een beleid voor zelf behoud bijwerkt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met toepassings-en gebruikers referenties.

## <a name="c"></a>C\#

Een beleid voor zelf behoud verwijderen:

1. Roep de [**IAggregatePartner. SelfServePolicies. ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) -methode aan met de entiteit-id om een interface op te halen voor bewerkingen op het beleid.

2. Roep de [**put**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.put) -of [**PutAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.putasync) -methode aan om het beleid voor eigen beheer bij te werken.

``` csharp
// IAggregatePartner partnerOperations;
SelfServePolicy policy;

// All the operations executed on this partner operation instance will share the same correlation identifier but will differ in request identifier
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// updates the self-serve policies
partnerOperations.SelfServePolicies.ById(policy.id).Put(policy);
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                       |
|----------|-------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy http/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

- Een aanvraag-id en correlatie-id zijn vereist.
- Zie de [rest headers van het Partner Center](headers.md) voor meer informatie.

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.

| Naam                              | Type   | Description                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy)| object | De informatie over zelf-beleids regels. |

#### <a name="selfservepolicy"></a>SelfServePolicy

In deze tabel worden de minimale vereiste velden uit de [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) -resource beschreven die nodig zijn voor het maken van een nieuw beleid voor zelf behoud.

| Eigenschap              | Type             | Beschrijving                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | Een selfservice beleids-id die wordt geleverd bij het maken van het selfservice beleid.     |
| SelfServeEntity       | SelfServeEntity  | De selfservice-entiteit waarvoor toegang wordt verleend.                                                     |
| Verlener               | Verlener          | De subsidie die toegang verleent.                                                                    |
| Machtigingen           | Matrix van machtigingen| Een matrix met [machtigings](self-serve-policy-resources.md#permission) bronnen.                                                      |
| ETAG                  | tekenreeks           | De ETag.                                                                                               |


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

Als deze is geslaagd, retourneert deze API een [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) -resource voor het bijgewerkte beleid voor zelf behoud.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

Deze methode retourneert de volgende fout codes:

| HTTP-status code     | Foutcode   | Beschrijving                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| 404                  | 600039       | Het beleid voor selfservice beheer is niet gevonden                                            |
| 404                  | 600040       | De beleids-id zelf behouden is onjuist                                  |


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
