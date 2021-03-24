---
title: De status van de directe ondertekening van de klant ophalen voor de micro soft-klant overeenkomst.
description: U kunt de DirectSignedCustomerAgreementStatus-Resource gebruiken om de status van de directe ondertekening (directe acceptatie) van een klant van de micro soft-klant overeenkomst te verkrijgen.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 267e3aa63a94c5045977ad566eb5061df3b59882
ms.sourcegitcommit: bbdb5f7c9ddd42c2fc4eaadbb67d61aeeae805ca
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/24/2021
ms.locfileid: "105030552"
---
# <a name="get-the-status-of-a-customers-direct-signing-direct-acceptance-of-microsoft-customer-agreement"></a>De status van de directe ondertekening van een klant (direct accepteren) van de micro soft-klant overeenkomst ophalen

**Van toepassing op:**

- Partnercentrum

De **DirectSignedCustomerAgreementStatus** -resource wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft.

Deze resource is *niet van toepassing* op:

- Partnercentrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt uitgelegd hoe u de status van de directe acceptatie van een klant kunt ophalen van de klant overeenkomst van micro soft.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u de status van de directe acceptatie van een klant wilt ophalen van de micro soft-klant overeenkomst, roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id. Gebruik vervolgens de eigenschap [**overeenkomsten**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.agreements) om een [**ICustomerAgreementCollection**](/dotnet/api/microsoft.store.partnercenter.agreements.icustomeragreementcollection) -interface op te halen. Roep tot slot `GetDirectSignedCustomerAgreementStatus()` `GetDirectSignedCustomerAgreementStatusAsync()` de status aan of op te halen.

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
var customerDirectSigningStatus = partnerOperations.Customers.ById(selectedCustomerId).Agreements.GetDirectSignedCustomerAgreementStatus();
```

Voor **beeld**: console-voor [beeld-app](https://github.com/microsoft/Partner-Center-DotNet-Samples). **Project**: SdkSamples- **klasse**: GetDirectSignedCustomerAgreementStatus. cs

## <a name="rest-request"></a>REST-aanvraag

Als u de status van de directe acceptatie van een klant wilt ophalen van de micro soft-klant overeenkomst, maakt u een REST-aanvraag om de [DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) voor de klant op te halen.

### <a name="request-syntax"></a>Syntaxis van aanvraag

Gebruik de volgende aanvraag syntaxis:

| Methode | Aanvraag-URI                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| GET    | [*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/directSignedMicrosoftCustomerAgreementStatus http/1.1 |

### <a name="uri-parameters"></a>URI-para meters

U kunt de volgende URI-para meters met uw aanvraag gebruiken:

| Naam             | Type | Vereist | Beschrijving                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| klant-Tenant-id | GUID | Ja | De waarde is een **CustomerTenantId** met de GUID-indeling waarmee u de Tenant-id van een klant kunt opgeven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een [ **DirectSignedCustomerAgreementStatus** -resource](./customer-agreement-direct-sign-status-resource.md) in de hoofd tekst van het antwoord.

De resource heeft een **isSigned** -eigenschap die de directe goedkeurings status van de klant aanduidt.

- De waarde **True** geeft aan dat de overeenkomst rechtstreeks door de klant is ondertekend (geaccepteerd).

- De waarde **False** geeft aan dat de overeenkomst rechtstreeks door de *klant is ondertekend* (geaccepteerd).

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.

Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 20
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b

{"isSigned":true}
```
