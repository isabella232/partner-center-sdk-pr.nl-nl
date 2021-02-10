---
title: Acceptatie door de klant van Microsoft-klantovereenkomst bevestigen
description: Meer informatie over het bevestigen van de acceptatie van klanten van de micro soft-klant overeenkomst met behulp van partner Center-Api's.
ms.date: 02/08/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 62a6cebd5d6d093377dd5940dcff6204b7095c70
ms.sourcegitcommit: ebb36208d6e2dea705f62b7d60d471f10c55132e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/09/2021
ms.locfileid: "100006075"
---
# <a name="confirm-customer-acceptance-of-the-microsoft-customer-agreement-using-partner-center-apis"></a>Acceptatie van klant bevestigen voor de micro soft-klant overeenkomst met behulp van partner Center-Api's

**Van toepassing op:**

- Partnercentrum

Het partner Centrum ondersteunt momenteel alleen bevestiging van klant acceptatie van de micro soft-klant overeenkomst in de *open bare cloud van micro soft*. Deze functionaliteit is momenteel niet van toepassing op:

- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt beschreven hoe u de acceptatie van klanten van micro soft-klanten overeenkomst bevestigt of opnieuw bevestigt.

## <a name="prerequisites"></a>Vereisten

- Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,14 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md). *Dit scenario ondersteunt alleen app + gebruikers verificatie.*

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- De datum (**dateAgreed**) waarop de klant de micro soft-klant overeenkomst heeft geaccepteerd.

- Informatie over de gebruiker van de organisatie van de klant die de micro soft-klant overeenkomst heeft geaccepteerd. Dit omvat:
  - Voornaam
  - Achternaam
  - E-mailadres
  - Telefoon nummer (optioneel)
- Als de volgende waarden voor een klant worden gewijzigd, kan het partner centrum een andere overeenkomst voor die klant maken: voor naam achternaam e-mail adres telefoon nummer, anders ontvangen partners de volgende fout code, vanwege een dubbele klant die wordt gemaakt


```
{
"code": 600061,
"message": "A partner confirmed agreement already exists for the customer.",
"description": "A partner confirmed agreement already exists for the customer.",
"errorName": "PartnerConfirmedAgreementAlreadyExists",
"isRetryable": false,
"parameters": {},
"errorMessageExtended": "InternalErrorCode=600061"
}
 ```

## <a name="net"></a>.NET

Bevestigen of herbevestigen van de acceptatie van de klant door de klant overeenkomst van micro soft:

1. Haal de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op. U moet de **ontbrekende templateid** van de micro soft-klant overeenkomst verkrijgen. Zie voor meer informatie de [meta gegevens van de overeenkomst ophalen voor de micro soft-klant overeenkomst](get-customer-agreement-metadata.md).

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
   ```

2. Maak een nieuw object **overeenkomst** met details van de bevestiging.

3. Gebruik de verzameling **IAgreggatePartner. Customers** en roep de methode **ById** aan met de opgegeven **klant-Tenant-id**.

4. Gebruik de eigenschap **overeenkomsten** , gevolgd door het aanroepen van **Create** of **CreateAsync**.

   ```csharp
   // string selectedCustomerId;

   var agreementToCreate = new Agreement
   {
       DateAgreed = DateTime.UtcNow,
       TemplateId = microsoftCustomerAgreementDetails.TemplateId,
       PrimaryContact = new Contact
       {
           FirstName = "Tania",
           LastName = "Carr",
           Email = "someone@example.com",
           PhoneNumber = "1234567890"
       }
   };

   Agreement agreement = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Create(agreementToCreate);
   ```

Een volledig voor beeld vindt u in de [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.

## <a name="rest-request"></a>REST-aanvraag

Bevestigen of herbevestigen van de acceptatie van de klant door de klant overeenkomst van micro soft:

1. Haal de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op. U moet de **ontbrekende templateid** van de micro soft-klant overeenkomst verkrijgen. Zie voor meer informatie de [meta gegevens van de overeenkomst ophalen voor de micro soft-klant overeenkomst](get-customer-agreement-metadata.md).

2. Maak een nieuwe [ **overeenkomst** resource](agreement-resources.md) om te bevestigen dat een klant de micro soft-klant overeenkomst heeft geaccepteerd. Gebruik de volgende [syntaxis voor rest-aanvragen](#request-syntax).

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode | Aanvraag-URI                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| POST   | [*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/agreements http/1.1 |

#### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om de klant op te geven die u wilt bevestigen.

| Naam               | Type | Vereist | Beschrijving                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| klant-Tenant-id | GUID | Ja | De waarde is een **klant-Tenant-id** van de GUID-indeling, een id waarmee u een klant kunt opgeven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de REST-aanvraag beschreven.

| Naam      | Type   | Description                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------|
| Overeenkomst | object | Details van de partner voor het bevestigen van de acceptatie van de klant door de klant overeenkomst van micro soft. |

#### <a name="agreement"></a>Overeenkomst

In deze tabel worden de minimale vereiste velden voor het maken van een [ **overeenkomst** resource](agreement-resources.md)beschreven.

| Eigenschap       | Type   | Description                              |
|----------------|--------|------------------------------------------|
| primaryContact | [Contact](./utility-resources.md#contact) | Informatie over de gebruiker van de organisatie van de klant die de klant overeenkomst van micro soft heeft geaccepteerd, waaronder:  **FirstName**, **LastName**, **email** en **phonenumber** (optioneel) |
| dateAgreed     | teken reeks in UTC-datum tijd notatie |De datum waarop de klant de overeenkomst heeft geaccepteerd. |
| Ontbrekende templateid     | tekenreeks | De unieke id van het overeenkomst type dat door de klant is geaccepteerd. U kunt de **ontbrekende templateid** voor de micro soft-klant overeenkomst verkrijgen door de meta gegevens van de overeenkomst voor de micro soft-klant overeenkomst op te halen. Zie de [meta gegevens van de overeenkomst voor micro soft Customer Agreement ophalen](./get-customer-agreement-metadata.md) voor meer informatie. |
| type           | tekenreeks | Type overeenkomst geaccepteerd door de klant. Gebruik ' MicrosoftCustomerAgreement ' als de klant de micro soft-klant overeenkomst heeft geaccepteerd. |

#### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "primaryContact": {
        "firstName": "Tania",
        "lastName": "Carr",
        "email": "someone@example.com",
        "phoneNumber": "1234567890"
    },
    "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
    "dateAgreed": "2018-06-14T00:00:00.000Z",
    "type": "MicrosoftCustomerAgreement"
}
```

## <a name="rest-response"></a>REST-antwoord

Als deze methode is geslaagd, wordt een [ **overeenkomst** resource](./agreement-resources.md)geretourneerd.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.

Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

#### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 201 Created
Content-Length: 261
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "userId": "3d6f2c09-eb40-48ca-a4b3-d24c9c007531",
    "primaryContact": {
        "firstName": "Tania",
        "lastName": "Carr",
        "email": "someone@example.com",
        "phoneNumber": "1234567890"
    },
    "templateId": "117a77b0-9360-443b-8795-c6dedc750cf9",
    "dateAgreed": "2018-06-14T00:00:00.000Z",
    "type": "MicrosoftCustomerAgreement"
}
```
