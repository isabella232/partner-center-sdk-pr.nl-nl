---
title: De kwalificaties van een klant ophalen
description: Meer informatie over hoe u asynchrone validatie kunt gebruiken om de kwalificatie van een klant te verkrijgen via de Partner Center-API. Partners kunnen deze gebruiken om onderwijs klanten te valideren.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 9f9b9aaddde0d66caf9c7ef32e8fba6d5e3aba36
ms.sourcegitcommit: 0c98496e972aebe10eba23822aa229125bfc035d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767653"
---
# <a name="get-a-customers-qualifications-via-asynchronous-validation"></a>De kwalificaties van een klant ophalen via asynchrone validatie

**Van toepassing op**

- Partnercentrum

Meer informatie over hoe u de kwalificaties van een klant asynchroon kunt verkrijgen via partner Center-Api's. Zie [de kwalificatie van een klant ophalen via synchrone validatie](get-customer-qualification-synchronous.md)voor meer informatie over hoe u dit synchroon kunt doen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Qualifications http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Deze tabel bevat de vereiste query parameter om alle kwalificaties op te halen.

| Naam               | Type   | Vereist | Beschrijving                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| **klant-Tenant-id** | tekenreeks | Yes      | Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a>REST-antwoord

Als deze methode is geslaagd, wordt een verzameling kwalificaties in de antwoord tekst geretourneerd.  Hieronder vindt u voor beelden van de **Get** -aanroep voor een klant met de **opleidings** kwalificatie.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-examples"></a>Antwoord voorbeelden

In deze sectie vindt u antwoorden die kunnen worden weer gegeven wanneer een klant `vettingStatus` :

- Goedgekeurd
- Wordt gecontroleerd
- Geweigerd

**Goedgekeurd** voor beeld:

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "Approved",
    }
]

```

**In** dit voor beeld:

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "InReview",
        "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
    }
]

```

Voor beeld van **geweigerd** :

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
[
    {
        "qualification": "Education",
        "vettingStatus": "Denied",
        "vettingReason": "Not an Education Customer", // example Vetting Reason
        "vettingCreatedDate": "2020-12-03T10:37:38.885Z" // UTC
    }
]

```

## <a name="related-articles"></a>Verwante artikelen:

- [De kwalificaties van een klant bijwerken](update-a-customer-s-qualifications.md)