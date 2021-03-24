---
title: Kwalificaties van een klant bijwerken
description: Hiermee worden de kwalificaties van een klant asynchroon bijgewerkt, met inbegrip van het adres dat aan het profiel is gekoppeld.
ms.date: 03/23/2021
ms.service: partner-dashboard
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: 7606eeaac4df158ec0fad6ffd4e565bb250f448e
ms.sourcegitcommit: bbdb5f7c9ddd42c2fc4eaadbb67d61aeeae805ca
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/24/2021
ms.locfileid: "105030603"
---
# <a name="update-a-customers-qualifications-asynchronously"></a>De kwalificaties van een klant asynchroon bijwerken

Hiermee worden de kwalificaties van een klant asynchroon bijgewerkt.

Een partner kan de kwalificaties van een klant asynchroon bijwerken om "Education" of "GovernmentCommunityCloud" te zijn. Andere waarden ' none ' en ' non profit ' kunnen niet worden ingesteld.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u de kwalificatie van een klant voor ' opleidingen ' wilt maken, maakt u eerst een-object dat het kwalificatie type vertegenwoordigt. Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id. Gebruik vervolgens de [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) -eigenschap om een [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) -interface op te halen. Roep ten slotte `CreateQualifications()` `CreateQualificationsAsync()` het object kwalificatie type aan als een invoer parameter.

``` csharp
var qualificationType = { Qualification = "education" };
var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType);
```

Voor **beeld**: console-voor [beeld-app](https://github.com/microsoft/Partner-Center-DotNet-Samples). **Project**: SdkSamples- **klasse**: CreateCustomerQualification. cs

Als u de kwalificatie van een klant wilt bijwerken naar **GovernmentCommunityCloud** op een bestaande klant zonder kwalificatie, moet de partner ook de [**ValidationCode**](utility-resources.md#validationcode)van de klant bevatten. Maak eerst een object dat het kwalificatie type vertegenwoordigt. Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id. Gebruik vervolgens de [**Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) -eigenschap om een [**ICustomerQualification**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) -interface op te halen. Roep ten slotte `CreateQualifications()` `CreateQualificationsAsync()` het object kwalificatie type en de validatie code aan als invoer parameters.

``` csharp
// GCC validation is type ValidationCode
var qualificationType = { Qualification = "GovernmentCommunityCloud" };
var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType, gccValidation);
```

Voor **beeld**: console-voor [beeld-app](https://github.com/microsoft/Partner-Center-DotNet-Samples). **Project**: SdkSamples- **klasse**: CreateCustomerQualificationWithGCC. cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer_ID}/Qualifications? code = {VALIDATIONCODE} http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om de kwalificatie bij te werken.

| Naam                   | Type | Vereist | Beschrijving                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **klant-Tenant-id** | GUID | Ja      | De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort. |
| **validationCode**     | int  | Nee       | Alleen nodig voor de cloud van de community.                                                                                                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In deze tabel wordt het kwalificatie object in de hoofd tekst van de aanvraag beschreven.

Eigenschap | Type | Vereist | Beschrijving
-------- | ---- | -------- | -----------
Kwalificatie | tekenreeks | Ja | De teken reeks waarde van de Enum van [**CustomerQualification**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification) .

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/qualifications?code=<validation-code> HTTP/1.1
Accept: application/json
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68

{
    "Qualification": "Education"
}

```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een object kwalificaties in de hoofd tekst van het antwoord. Hieronder volgt een voor beeld van de **post** -oproep voor een klant (met een eerdere kwalificatie van **geen**) met de **opleidings** kwalificatie.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 201 CREATED
Content-Length: 29
Content-Type: application/json
MS-CorrelationId: 7d2456fd-2d79-46d0-9f8e-5d7ecd5f8745
MS-RequestId: 037db222-6d8e-4d7f-ba78-df3dca33fb68
{
    "qualification": "Education",
    "vettingStatus": "InReview",
    "vettingCreateDate": "2020-12-04T20:54:24Z" // UTC
}
```

## <a name="related-articles"></a>Verwante artikelen:

- [De kwalificaties van een klant ophalen](./get-customer-qualification-asynchronous.md)
- [De validatiecodes van een partner ophalen](get-a-partner-s-validation-codes.md)
