---
title: De kwalificatie van een klant bijwerken
description: Meer informatie over het bijwerken van de kwalificaties van een klant via synchrone screening of hebben, met inbegrip van het adres dat aan het profiel is gekoppeld.
ms.date: 12/07/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 7faab68d20c698f5b040a76f4776dbdf14180640
ms.sourcegitcommit: 0c98496e972aebe10eba23822aa229125bfc035d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767657"
---
# <a name="update-a-customers-qualification-via-synchronous-validation"></a>De kwalificatie van een klant bijwerken via synchrone validatie

**Van toepassing op**

- Partnercentrum

Meer informatie over hoe u de kwalificaties van een klant synchroon kunt bijwerken via partner Center-Api's. Zie [de kwalificatie van een klant bijwerken via asynchrone validatie](update-customer-qualification-asynchronous.md)voor meer informatie over hoe u dit asynchroon kunt doen.

Een partner kan de kwalificatie van een klant zo bijwerken dat deze ' Education ' of ' GovernmentCommunityCloud ' is. Andere waarden ' none ' en ' non profit ' kunnen niet worden ingesteld.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u de kwalificatie van een klant wilt bijwerken naar ' Education ', roept u **[Update/DotNet/API/Microsoft. Store. partnercenter. kwalificatie. icustomerqualification. update)** aan voor een bestaande  [**klant**](/dotnet/api/microsoft.store.partnercenter.models.customers.customer).

``` csharp
// CustomerQualification is an enum

var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.Education);
```

Voor **beeld**: [console test-app](console-test-app.md). **Project**: PartnerSDK. FeatureSamples- **klasse**: CustomerQualificationOperations.cs

Het bijwerken van de kwalificatie van een klant naar **GovernmentCommunityCloud** op een bestaande klant zonder een kwalificatie.  De partner is ook vereist voor het toevoegen van de [**ValidationCode**](utility-resources.md#validationcode)van de klant.

``` csharp
// CustomerQualification is an enum
// GCC validation is type ValidationCode

var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.Update(CustomerQualification.GovernmentCommunityCloud, gccValidation);
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| **PUT** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer_ID}/Qualification? code = {VALIDATIONCODE} http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om de kwalificatie bij te werken.

| Naam                   | Type | Vereist | Beschrijving                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **klant-Tenant-id** | GUID | Yes      | De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort. |
| **validationCode**     | int  | No       | Alleen nodig voor de cloud van de community.                                                                                                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

De waarde van het gehele getal uit de Enum van de [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) .

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PUT https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualification?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode de bijgewerkte [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) -eigenschap in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

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

- [De kwalificatie van een klant ophalen](get-a-customer-s-qualification.md)
- [De validatiecodes van een partner ophalen](get-a-partner-s-validation-codes.md)
