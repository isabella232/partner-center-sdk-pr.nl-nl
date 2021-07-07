---
title: De kwalificatie van een klant bijwerken
description: Meer informatie over het bijwerken van de kwalificaties van een klant via synchrone screening of controle, met inbegrip van het adres dat is gekoppeld aan het profiel.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 5047743afdef02033d9494e3d8c16c9ab96b3fe9
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446646"
---
# <a name="update-a-customers-qualification-via-synchronous-validation"></a>De kwalificatie van een klant bijwerken via synchrone validatie

Meer informatie over het synchroon bijwerken van de kwalificaties van een klant via Partner Center API's. Zie Kwalificatie van een klant bijwerken via asynchrone validatie voor meer informatie over hoe u [dit asynchroon kunt doen.](update-customer-qualification-asynchronous.md)

Een partner kan de kwalificatie van een klant bijwerken naar Education of GovernmentCommunityCloud. Andere waarden, 'Geen' en 'Non-non-profit', kunnen niet worden ingesteld.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u de kwalificatie van een klant wilt bijwerken naar Education, roept u **[Update/dotnet/api/microsoft.store.partnercenter.kwalificatie.edtomerqualification.update)** aan bij een bestaande [**klant.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer)

``` csharp
// CustomerQualification is an enum

var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.Education);
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project:** Klasse PartnerSDK.FeatureSamples: CustomerQualificationOperations.cs 

Als u de kwalificatie van een klant wilt bijwerken naar **GovernmentCommunityCloud** voor een bestaande klant zonder kwalificatie, moet de partner de [**ValidationCode van de klant opnemen.**](utility-resources.md#validationcode)

``` csharp
// CustomerQualification is an enum
// GCC validation is type ValidationCode

var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.GovernmentCommunityCloud, gccValidation);
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/kwalificatie?code={validationCode} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de kwalificatie bij te werken.

| Naam                   | Type | Vereist | Beschrijving                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | GUID | Ja      | De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort. |
| **validationCode**     | int  | Nee       | Alleen nodig voor Government Community Cloud.                                                                                                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

De gehele waarde uit de [**enum CustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification)

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode de [**bijgewerkte eigenschap Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 14
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
"governmentcommunitycloud"
```

## <a name="related-articles"></a>Verwante artikelen:

- [De kwalificatie van een klant ophalen](./get-customer-qualification-synchronous.md)
- [De validatiecodes van een partner ophalen](get-a-partner-s-validation-codes.md)
