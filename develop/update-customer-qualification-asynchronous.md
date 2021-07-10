---
title: Kwalificaties van een klant bijwerken
description: Hiermee worden de kwalificaties van een klant asynchroon bijgewerkt, inclusief het adres dat aan het profiel is gekoppeld.
ms.date: 03/23/2021
ms.service: partner-dashboard
author: JoeyBytes
ms.author: jobiesel
ms.openlocfilehash: d7dd3593894ce91ddc7b96d604b80153d41d3a67
ms.sourcegitcommit: 51237e7e98d71a7e0590b4d6a4034b6409542126
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2021
ms.locfileid: "113572094"
---
# <a name="update-a-customers-qualifications-asynchronously"></a>De kwalificaties van een klant asynchroon bijwerken

Werkt de kwalificaties van een klant asynchroon bij.

Een partner kan de kwalificaties van een klant asynchroon bijwerken naar Education of GovernmentCommunityCloud. Andere waarden, Geen en Non-profitorganisatie, kunnen niet worden ingesteld.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u de kwalificatie van een klant voor Education wilt maken, maakt u eerst een object dat het kwalificatietype vertegenwoordigt. Roep vervolgens de [**methode IAggregatePartner.Customers.ById aan**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id. Gebruik vervolgens de [**eigenschap Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) om een [**ICustomerQualification-interface op te**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) halen. Roep ten slotte `CreateQualifications()` of aan met het `CreateQualificationsAsync()` kwalificatietypeobject als invoerparameter.

``` csharp
var qualificationToCreate = "education";    // can also be "StateOwnedEntity" or "GovernmentCommunityCloud". See GCC example below.
var qualificationType = { Qualification = qualificationToCreate };
var eduCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType);
```

**Voorbeeld:** [Consolevoorbeeld-app.](https://github.com/microsoft/Partner-Center-DotNet-Samples) **Project:** SdkSamples-klasse: CreateCustomerQualification.cs 

Als u de kwalificatie van een klant wilt bijwerken naar **GovernmentCommunityCloud** voor een bestaande klant zonder kwalificatie, moet de partner ook de ValidationCode van de klant [**opnemen.**](utility-resources.md#validationcode) Maak eerst een -object dat het kwalificatietype vertegenwoordigt. Roep vervolgens de [**methode IAggregatePartner.Customers.ById aan**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id. Gebruik vervolgens de [**eigenschap Kwalificatie**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.qualification) om een [**ICustomerQualification-interface op te**](/dotnet/api/microsoft.store.partnercenter.qualification.icustomerqualification) halen. Roep ten slotte `CreateQualifications()` of aan met het `CreateQualificationsAsync()` kwalificatietypeobject en de validatiecode als invoerparameters.

``` csharp
// GCC validation is type ValidationCode
var qualificationType = { Qualification = "GovernmentCommunityCloud" };
var gccCustomerQualification = partnerOperations.Customers.ById(existingCustomer.Id).Qualification.CreateQualifications(qualificationType, gccValidation);
```

**Voorbeeld:** [Consolevoorbeeld-app.](https://github.com/microsoft/Partner-Center-DotNet-Samples) **Project:** SdkSamples-klasse : CreateCustomerQualificationWithGCC.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                             |
|---------|---------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer_id}/kwalificaties?code={validationCode} HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de kwalificatie bij te werken.

| Naam                   | Type | Vereist | Beschrijving                                                                                                                                            |
|------------------------|------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | GUID | Yes      | De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort. |
| **validationCode**     | int  | No       | Alleen nodig voor Government Community Cloud.                                                                                                            |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel wordt het kwalificatieobject in de aanvraag body beschreven.

Eigenschap | Type | Vereist | Beschrijving
-------- | ---- | -------- | -----------
Kwalificatie | tekenreeks | Yes | De tekenreekswaarde uit [**de enum CustomerQualification.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerqualification)

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

Als dit lukt, retourneert deze methode een kwalificatieobject in de antwoord-body. Hieronder vindt u een voorbeeld van de **POST-aanroep** van een klant (met een eerdere kwalificatie van **Geen**) met de **kwalificatie voor** het onderwijs.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

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

- [De kwalificaties van een klant krijgen](./get-customer-qualification-asynchronous.md)
- [De validatiecodes van een partner ophalen](get-a-partner-s-validation-codes.md)
