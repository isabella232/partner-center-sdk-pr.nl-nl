---
title: Bevestiging van acceptatie door de klant van Microsoft-klantovereenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u de acceptatie van klanten kunt bevestigen van de klant overeenkomst van micro soft.
ms.date: 09/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 55f63311e7bb1857fdc6c4b3d68446674542ba98
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767407"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-customer-agreement"></a>Bevestiging van acceptatie door de klant van Microsoft-klantovereenkomst ophalen

**Van toepassing op:**

- Partnercentrum

De **overeenkomst** resource wordt momenteel alleen ondersteund door het partner centrum in de *open bare cloud van micro soft*. Deze resource is niet van toepassing op:

- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt uitgelegd hoe u bevestiging (en) kunt ophalen van de acceptatie van de klant overeenkomst van micro soft.

## <a name="prerequisites"></a>Vereisten

- Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,14 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md). Dit scenario ondersteunt alleen app + gebruikers verificatie.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="net"></a>.NET

Bevestiging (en) van door de klant geaccepteerde acceptatie ophalen:

- Gebruik de verzameling **IAggregatePartner. Customers** en roep **ById** methode aan met de opgegeven klant-id.

- Haal de eigenschap **overeenkomsten** op en filter de resultaten met de klant overeenkomst van micro soft door de methode **ByAgreementType** aan te roepen.

- Roep **Get** -of **GetAsync** -methode aan.

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCustomerAgreement";

var customerAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

Een volledig voor beeld vindt u in de [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.

## <a name="rest-request"></a>REST-aanvraag

Bevestiging van acceptatie van klant ophalen die eerder is gegeven:

1. Maak een REST-aanvraag om de verzameling [overeenkomsten](./agreement-resources.md) voor de klant op te halen.

2. Gebruik de query parameter **Agreement type** om de resultaten te beperken tot alleen de micro soft-klant overeenkomst.

### <a name="request-syntax"></a>Syntaxis van aanvraag

Gebruik de volgende aanvraag syntaxis:

| Methode | Aanvraag-URI                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/agreements? Agreement type = {Agreement-type} HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-para meters

U kunt de volgende URI-para meters met uw aanvraag gebruiken:

| Naam             | Type | Vereist | Beschrijving                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| klant-Tenant-id | GUID | Yes | De waarde is een GUID-indeling **CustomerTenantId** waarmee u een klant kunt opgeven. |
| overeenkomst-type | tekenreeks | No | Deze para meter retourneert alle meta gegevens van de overeenkomst. Gebruik deze para meter om het query-antwoord op een specifiek overeenkomst type te bereiken. De ondersteunde waarden zijn: <br/><br/> **MicrosoftCloudAgreement** die alleen de overeenkomst met de meta gegevens van het type *MicrosoftCloudAgreement* bevat.<br/><br/> **MicrosoftCustomerAgreement** die alleen de overeenkomst met de meta gegevens van het type *MicrosoftCustomerAgreement* bevat.<br/><br/> **\*** Hiermee worden alle meta gegevens van de overeenkomst geretourneerd. (Gebruik **\*** alleen als uw code de benodigde logica heeft voor het afhandelen van onverwachte overeenkomst typen.)<br/><br/> **Opmerking:** Als de URI-para meter niet is opgegeven, wordt de query standaard ingesteld op **MicrosoftCloudAgreement** voor achterwaartse compatibiliteit. Micro soft kan op elk moment overeenkomst meta gegevens introduceren met nieuwe overeenkomst typen.  |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, retourneert deze methode een verzameling **overeenkomst** resources in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.

Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

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
