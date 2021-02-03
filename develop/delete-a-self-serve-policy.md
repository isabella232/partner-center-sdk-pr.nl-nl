---
title: Een beleid voor zelf behoud verwijderen
description: Een selfservice beleid verwijderen.
ms.date: 04/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 3450145d6daf2ffca5e2886245e592406cb0886d
ms.sourcegitcommit: 01e75175077611da92175c777a440a594fb05797
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/08/2020
ms.locfileid: "97768657"
---
# <a name="delete-a-selfservepolicy"></a>Een SelfServePolicy verwijderen

**Van toepassing op:**

- Partnercentrum

In dit onderwerp wordt uitgelegd hoe u een beleid voor zelf behoud bijwerkt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met toepassings-en gebruikers referenties.

## <a name="c"></a>C\#

Een beleid voor zelf behoud verwijderen:

1. Roep de [**IAggregatePartner. SelfServePolicies. ById**](/dotnet/api/microsoft.store.partnercenter.iselfservepoliciescollection.byid) -methode aan met de entiteit-id om een interface op te halen voor bewerkingen op het beleid.

2. Roep de methode [**Delete**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.delete) of [**DeleteAsync**](/dotnet/api/microsoft.store.partnercenter.SelfServePolicies.deleteasync) aan om het beleid voor zelf behoud te verwijderen.

``` csharp
// IAggregatePartner partnerOperations;
string policyId;

// All the operations executed on this partner operation instance will share the same correlation Id but will differ in request Id
IPartner scopedPartnerOperations = partnerOperations.With(RequestContextFactory.Instance.Create(Guid.NewGuid()));

// deletes the self-serve policies
partnerOperations.SelfServePolicies.ById(policyId).Delete();
```

Voor een voor beeld ziet u het volgende:

- Voor beeld: [console test-app](console-test-app.md)
- Project: **PartnerSDK. FeatureSamples**
- Klasse: **DeleteSelfServePolicies.cs**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                   |
|---------|-------------------------------------------------------------------------------|
| **VERWIJDERD** | [*{baseURL}*](partner-center-rest-urls.md)/v1/SelfServePolicy/{id} http/1.1 |

**URI-para meter**

Gebruik de volgende Path-para meters om het opgegeven product op te halen.

| Naam                       | Type         | Vereist | Beschrijving                                                     |
|----------------------------|--------------|----------|-----------------------------------------------------------------|
| **SelfServePolicy-id**     | **tekenreeksexpressie**   | Yes      | Een teken reeks die het selfservice beleid identificeert.                 |

### <a name="request-headers"></a>Aanvraagheaders

- Een aanvraag-ID en correlatie-ID zijn vereist.
- Zie de [rest headers van het Partner Center](headers.md) voor meer informatie.

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
DELETE https://api.partnercenter.microsoft.com/v1/SelfServePolicy/634f6379-ad54-449b-9821-564f737158ab_0431a72c-7d8a-4393-b25e-ef63f5efb415 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 789
Connection: Keep-Alive

```

## <a name="rest-response"></a>REST-antwoord

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 204 deleted
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
Date: Tue, 14 Feb 2017 20:06:02 GMT

```
