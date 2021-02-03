---
title: De kwalificatie van een klant ophalen
description: Meer informatie over hoe u synchrone validatie kunt gebruiken om de kwalificatie van een klant te verkrijgen via de Partner Center-API. Partners kunnen deze gebruiken om onderwijs klanten te valideren.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 82812091be9c13d64ac183c37461e3b63b2ec294
ms.sourcegitcommit: 0c98496e972aebe10eba23822aa229125bfc035d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767652"
---
# <a name="get-a-customers-qualification-via-synchronous-validation"></a>De kwalificatie van een klant ophalen via synchrone validatie

**Van toepassing op**

- Partnercentrum

Meer informatie over hoe u de kwalificatie van een klant synchroon kunt verkrijgen via partner Center-Api's. Zie [de kwalificatie van een klant ophalen via asynchrone validatie](get-customer-qualification-asynchronous.md)voor meer informatie over hoe u dit asynchroon kunt doen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u de kwalificatie van een klant wilt ophalen, roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id. Gebruik vervolgens de [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) -eigenschap om een [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) -interface op te halen. Roep tot slot [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) aan om de kwalificatie van de klant op te halen.

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var customerQualification = partnerOperations.Customers.ById(customerId).Qualification.Get();
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Qualification http/1.1 |

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
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een kwalificatie waarde in de hoofd tekst van het antwoord.  Hieronder volgt een voor beeld van het **ophalen** van een klant met de **opleidings** kwalificatie.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length:
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

    "education"

```

## <a name="related-articles"></a>Verwante artikelen:

- [De kwalificatie van een klant bijwerken](update-a-customer-s-qualification.md)
