---
title: Bevestiging van acceptatie door de klant van Microsoft-klantovereenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u de klantacceptatie van de Microsoft-klantovereenkomst.
ms.date: 09/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 3668a5e510effb533cade311f52513b9a81d40af
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760535"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-customer-agreement"></a>Bevestiging van acceptatie door de klant van Microsoft-klantovereenkomst ophalen

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De **overeenkomstresource** wordt momenteel alleen ondersteund door Partner Center in de openbare cloud van Microsoft.

In dit artikel wordt uitgelegd hoe u bevestiging(en) kunt ophalen van de acceptatie van de Microsoft-klantovereenkomst.

## <a name="prerequisites"></a>Vereisten

- Als u de .NET SDK Partner Center, is versie 1.14 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md). Dit scenario ondersteunt alleen App+Gebruikersverificatie.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="net"></a>.NET

Bevestiging(en) van eerder opgegeven klantacceptatie ophalen:

- Gebruik de **verzameling IAggregatePartner.Customers** en roep de **ById-methode** aan met de opgegeven klant-id.

- Haal de **eigenschap Agreements** op en filter de resultaten naar Microsoft-klantovereenkomst **byAgreementType-methode aan te** roepen.

- Roep **de methode Get** of **GetAsync aan.**

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCustomerAgreement";

var customerAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

Een volledig voorbeeld vindt u in de [klasse GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)

## <a name="rest-request"></a>REST-aanvraag

Om bevestiging op te halen van de klantacceptatie die eerder is opgegeven:

1. Maak een REST-aanvraag om de verzameling [Overeenkomsten voor](./agreement-resources.md) de klant op te halen.

2. Gebruik de **queryparameter agreementType** om de resultaten alleen te Microsoft-klantovereenkomst.

### <a name="request-syntax"></a>Aanvraagsyntaxis

Gebruik de volgende aanvraagsyntaxis:

| Methode | Aanvraag-URI                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements?agreementType={agreement-type} HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

U kunt de volgende URI-parameters gebruiken bij uw aanvraag:

| Naam             | Type | Vereist | Beschrijving                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| customer-tenant-id | GUID | Ja | De waarde is een **CustomerTenantId** met GUID-indeling waarmee u een klant kunt opgeven. |
| agreement-type | tekenreeks | No | Deze parameter retourneert alle metagegevens van de overeenkomst. Gebruik deze parameter om het bereik van de queryreactie te wijzigen in een specifiek overeenkomsttype. De ondersteunde waarden zijn: <br/><br/> **MicrosoftCloudAgreement dat** alleen metagegevens van overeenkomst bevat van het type *MicrosoftCloudAgreement*.<br/><br/> **MicrosoftCustomerAgreement dat** alleen metagegevens van overeenkomst bevat van het type *MicrosoftCustomerAgreement*.<br/><br/> **\**_ die alle metagegevens van de overeenkomst retourneert. (Gebruik niet _* \* *_ tenzij uw code de benodigde logica heeft om onverwachte typen overeenkomst af te handelen.) <br/> <br/> _* Opmerking:** als de URI-parameter niet is opgegeven, wordt de query standaard ingesteld op **MicrosoftCloudAgreement** voor achterwaartse compatibiliteit. Microsoft kan op elk moment metagegevens van overeenkomst met nieuwe typen overeenkomst introduceren.  |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements?agreementType=MicrosoftCustomerAgreement HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een verzameling **overeenkomstresources** in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.

Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 620
Content-Type: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
{
    "totalCount": 2,
    "items":
    [
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@example.com"
                "phoneNumber":"1234567890"
            },
            "templateId":"117a77b0-9360-443b-8795-c6dedc750cf9",
            "dateAgreed":"2019-08-26T00:00:00",
            "type":"MicrosoftCustomerAgreement",
            "agreementLink":"https://aka.ms/customeragreement"
        },
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@example.com"
                "phoneNumber:"1234567890"
            },
            "templateId":"117a77b0-9360-443b-8795-c6dedc750cf9",
            "dateAgreed":"2019-08-27T00:00:00",
            "type":"MicrosoftCustomerAgreement",
            "agreementLink":"https://aka.ms/customeragreement"
        }
    ]
}
```
