---
title: Haal de status van directe ondertekening van de klant op voor Microsoft-klantovereenkomst.
description: U kunt de resource DirectSignedCustomerAgreementStatus gebruiken om de status van de directe ondertekening (directe acceptatie) van de klant van de Microsoft-klantovereenkomst.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 544965ab05e3956aa5b7b6fa2ef9656ff33990ef9c8d91422797132a814b85f1
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115993346"
---
# <a name="get-the-status-of-a-customers-direct-signing-direct-acceptance-of-microsoft-customer-agreement"></a>De status van de directe ondertekening van de klant (directe acceptatie) van de Microsoft-klantovereenkomst

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De **resource DirectSignedCustomerAgreementStatus** wordt momenteel alleen Partner Center in de openbare Cloud van Microsoft.

In dit artikel wordt uitgelegd hoe u de status kunt ophalen van de directe acceptatie van de Microsoft-klantovereenkomst.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u de status van de directe acceptatie van de Microsoft-klantovereenkomst van een klant wilt ophalen, roept u de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id. Gebruik vervolgens de [**eigenschap Agreements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.agreements) om een [**ICustomerAgreementCollection-interface op te**](/dotnet/api/microsoft.store.partnercenter.agreements.icustomeragreementcollection) halen. Roep ten slotte `GetDirectSignedCustomerAgreementStatus()` of aan om de status op te `GetDirectSignedCustomerAgreementStatusAsync()` halen.

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
var customerDirectSigningStatus = partnerOperations.Customers.ById(selectedCustomerId).Agreements.GetDirectSignedCustomerAgreementStatus();
```

**Voorbeeld:** [Consolevoorbeeld-app.](https://github.com/microsoft/Partner-Center-DotNet-Samples) **Project:** SdkSamples-klasse: GetDirectSignedCustomerAgreementStatus.cs 

## <a name="rest-request"></a>REST-aanvraag

Als u de status wilt ophalen van de directe acceptatie van de Microsoft-klantovereenkomst van een klant, maakt u een REST-aanvraag om [de DirectSignedCustomerAgreementStatus](./customer-agreement-direct-sign-status-resource.md) voor de klant op te halen.

### <a name="request-syntax"></a>Aanvraagsyntaxis

Gebruik de volgende aanvraagsyntaxis:

| Methode | Aanvraag-URI                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus HTTP/1.1 |

### <a name="uri-parameters"></a>URI-parameters

U kunt de volgende URI-parameters gebruiken bij uw aanvraag:

| Naam             | Type | Vereist | Beschrijving                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| customer-tenant-id | GUID | Yes | De waarde is een **CustomerTenantId** in GUID-indeling waarmee u de tenant-id van een klant kunt opgeven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

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

Als dit lukt, retourneert deze methode een [ **DirectSignedCustomerAgreementStatus-resource**](./customer-agreement-direct-sign-status-resource.md) in de antwoord-body.

De resource heeft een **eigenschap isSigned** die de status van directe ondertekening (directe acceptatie) van de klant aangeeft.

- De waarde **true geeft** aan dat de overeenkomst rechtstreeks door de klant is ondertekend (geaccepteerd).

- De waarde **false geeft** aan dat de overeenkomst niet rechtstreeks door de klant is ondertekend (geaccepteerd). 

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.

Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 20
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b

{"isSigned":true}
```
