---
title: Een beleid voor zelf behoud maken
description: Een nieuw beleid voor zelf behoud maken.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fd1579b2775ead57a440db0d6afb3bf22164c319
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/08/2020
ms.locfileid: "97768653"
---
# <a name="create-a-selfservepolicy"></a>Een SelfServePolicy maken

**Van toepassing op:**

- Partnercentrum

In dit onderwerp wordt uitgelegd hoe u een nieuw beleid voor zelf behoud maakt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met toepassings-en gebruikers referenties.

## <a name="c"></a>C\#

Een beleid voor zelf behoud maken:

1. Roep de [**IAggregatePartner. SelfServePolicies. Create**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.create) -of [**IAggregatePartner. SelfServePolicies. CreateAsync**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.createasync) -methode aan met de selfservice-beleids gegevens.

``` csharp
// IAggregatePartner partnerOperations;
string customerIdAsEntity;

var selfServePolicy = new SelfServePolicy
{
    SelfServeEntity = new SelfServeEntity
    {
        SelfServeEntityType = "customer",
        TenantID = customerIdAsEntity,
    },
    Grantor = new Grantor
    {
        GrantorType = "billToPartner",
        TenantID = partnerIdAsGrantor,
    },
    Permissions = new Permission[]
    {
        new Permission
        {
        Action = "Purchase",
        Resource = "AzureReservedInstances",
        },
    },
};

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// creates the self-serve policy
SelfServePolicy createdSelfServePolicy = scopedPartnerOperations.selfServePolicies.Create(selfServePolicy);
```

Voor een voor beeld ziet u het volgende:

- Voor beeld: [console test-app](console-test-app.md)
- Project: **PartnerSDK. FeatureSamples**
- Klasse: **CreateSelfServePolicies.cs**


## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                       |
|----------|-------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy http/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

- Een aanvraag-ID en correlatie-ID zijn vereist.
- Zie de [rest headers van het Partner Center](headers.md) voor meer informatie.

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.

| Naam                              | Type   | Description                                 |
|------------------------------------------------------------------|--------|---------------------------------------------|
| [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy)| object | De informatie over zelf-beleids regels. |

#### <a name="selfservepolicy"></a>SelfServePolicy

In deze tabel worden de minimale vereiste velden uit de [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) -resource beschreven die nodig zijn voor het maken van een nieuw beleid voor zelf behoud.

| Eigenschap              | Type             | Description                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| SelfServeEntity       | SelfServeEntity  | De selfservice-entiteit waarvoor toegang wordt verleend.                                                     |
| Verlener               | Verlener          | De subsidie die toegang verleent.                                                                    |
| Machtigingen           | Matrix van machtigingen| Een matrix met [machtigings](self-serve-policy-resources.md#permission) bronnen.                                                                     |


### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/SelfServePolicy HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 789
Expect: 100-continue
Connection: Keep-Alive

{
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
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als deze is geslaagd, retourneert deze API een [SelfServePolicy](self-serve-policy-resources.md#selfservepolicy) -resource voor het nieuwe beleid voor zelf behoud.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

Deze methode retourneert de volgende fout codes:

| HTTP-status code     | Foutcode   | Beschrijving                                                                |
|----------------------|--------------|----------------------------------------------------------------------------|
| 409                  | 600041       | Het beleid voor selfservice beheer bestaat al.                                                     |


### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 201 Created
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
        "etag": "\"933523d1-3f63-4fc3-8789-5e21c02cdaed\"",
        "objectType": "SelfServePolicy"
    }
}
```
