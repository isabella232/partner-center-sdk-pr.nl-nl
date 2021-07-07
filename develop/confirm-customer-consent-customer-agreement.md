---
title: Acceptatie door de klant van Microsoft-klantovereenkomst bevestigen
description: Meer informatie over hoe u de klantacceptatie van de Microsoft-klantovereenkomst met behulp Partner Center API's.
ms.date: 02/08/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 002508109191ede53cd06f25efc38286647fd67c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974009"
---
# <a name="confirm-customer-acceptance-of-the-microsoft-customer-agreement-using-partner-center-apis"></a>Bevestig dat de klant de Microsoft-klantovereenkomst met Partner Center API's

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Partner Center ondersteunt momenteel bevestiging van de klantacceptatie van de Microsoft-klantovereenkomst alleen in de openbare Cloud van Microsoft.

In dit artikel wordt beschreven hoe u de acceptatie van de klant van de Microsoft-klantovereenkomst.

## <a name="prerequisites"></a>Vereisten

- Als u de .NET SDK Partner Center, is versie 1.14 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md). *Dit scenario biedt alleen ondersteuning voor app- en gebruikersverificatie.*

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- De datum (**dateAgreed**) wanneer de klant de Microsoft-klantovereenkomst.

- Informatie over de gebruiker van de klantorganisatie die de Microsoft-klantovereenkomst. Dit omvat:
  - Voornaam
  - Achternaam
  - E-mailadres
  - Telefoon getal (optioneel)
- Als de volgende waarden voor een klant worden gewijzigd, kan Partner Center een andere overeenkomst maken voor die klant: Voornaam achternaam e-mailadres Telefoon nummer Anders ontvangen partners de volgende foutcode omdat er een dubbele klant wordt gemaakt


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

Bevestig of bevestig de klantacceptatie van de Microsoft-klantovereenkomst:

1. Haal de metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst. U moet de **templateId van** de Microsoft-klantovereenkomst. Zie Get [agreement metadata for Microsoft-klantovereenkomst (Metagegevens van overeenkomst verkrijgen voor Microsoft-klantovereenkomst) voor meer informatie.](get-customer-agreement-metadata.md)

   ```csharp
   // IAggregatePartner partnerOperations;

   string agreementType = "MicrosoftCustomerAgreement";

   var microsoftCustomerAgreementDetails = partnerOperations.AgreementDetails.ByAgreementType(agreementType).Get().Items.Single();
   ```

2. Maak een nieuw **Agreement-object** met details van de bevestiging.

3. Gebruik de **verzameling IAgreggatePartner.Customers** en roep de **ById-methode** aan met de opgegeven **customer-tenant-id**.

4. Gebruik de **eigenschap Agreements,** gevolgd door het aanroepen **van Create** of **CreateAsync.**

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

Een volledig voorbeeld vindt u in de klasse [CreateCustomerAgreement](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/CreateCustomerAgreement.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)

## <a name="rest-request"></a>REST-aanvraag

Bevestig of bevestig de klantacceptatie van de Microsoft-klantovereenkomst:

1. Haal de metagegevens van de overeenkomst voor de Microsoft-klantovereenkomst. U moet de **templateId van** de Microsoft-klantovereenkomst. Zie Get [agreement metadata for Microsoft-klantovereenkomst (Metagegevens van overeenkomst verkrijgen voor Microsoft-klantovereenkomst) voor meer informatie.](get-customer-agreement-metadata.md)

2. Maak een nieuwe [ **overeenkomstresource**](agreement-resources.md) om te bevestigen dat een klant de Microsoft-klantovereenkomst. Gebruik de volgende [REST-aanvraagsyntaxis](#request-syntax).

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI                                                                                        |
|--------|----------------------------------------------------------------------------------------------------|
| POST   | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1 |

#### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de klant op te geven die u wilt bevestigen.

| Naam               | Type | Vereist | Beschrijving                                                                                 |
|--------------------|------|----------|---------------------------------------------------------------------------------------------|
| customer-tenant-id | GUID | Ja | De waarde is een **klant-tenant-id** in GUID-indeling. Dit is een id waarmee u een klant kunt opgeven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

In deze tabel worden de vereiste eigenschappen in de rest-aanvraag body beschreven.

| Naam      | Type   | Beschrijving                                                                                  |
|-----------|--------|----------------------------------------------------------------------------------------------|
| Overeenkomst | object | Details die door de partner worden verstrekt om te bevestigen dat de klant de Microsoft-klantovereenkomst. |

#### <a name="agreement"></a>Overeenkomst

In deze tabel worden de minimaal vereiste velden beschreven voor het maken van een [ **Agreement-resource.**](agreement-resources.md)

| Eigenschap       | Type   | Beschrijving                              |
|----------------|--------|------------------------------------------|
| primaryContact | [Contact](./utility-resources.md#contact) | Informatie over de gebruiker van de klantorganisatie die de Microsoft-klantovereenkomst heeft geaccepteerd, waaronder:  **firstName,** **lastName,** **email** en **phoneNumber** (optioneel) |
| dateAgreed     | tekenreeks in UTC-datum/tijd-indeling |De datum waarop de klant de overeenkomst heeft geaccepteerd. |
| templateId     | tekenreeks | De unieke id van het overeenkomsttype dat door de klant is geaccepteerd. U kunt de **templateId voor Microsoft-klantovereenkomst verkrijgen** door de metagegevens van de overeenkomst op te halen voor Microsoft-klantovereenkomst. Zie [Metagegevens van overeenkomst Microsoft-klantovereenkomst](./get-customer-agreement-metadata.md) voor meer informatie. |
| type           | tekenreeks | Overeenkomsttype dat door de klant is geaccepteerd. Gebruik MicrosoftCustomerAgreement als de klant de Microsoft-klantovereenkomst. |

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

Als dit lukt, retourneert deze methode een [ **Agreement-resource**](./agreement-resources.md).

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.

Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
