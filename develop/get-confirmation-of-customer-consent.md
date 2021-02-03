---
title: Bevestiging van acceptatie door de klant van Microsoft Cloud-overeenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u de acceptatie van klanten kunt bevestigen van de Microsoft Cloud overeenkomst.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
aauthor: khakiali
ms.author: alikhaki
ms.openlocfilehash: d91f70cbd8bc9b8622b8d41ab9e601e2aee2cfab
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767547"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-cloud-agreement"></a>Bevestiging van acceptatie door de klant van Microsoft Cloud-overeenkomst ophalen

**Van toepassing op**

- Partnercentrum

> [!NOTE]
> De bron van de **overeenkomst** wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft. Het is niet van toepassing op:
>
> - Partner centrum beheerd door 21Vianet
> - Partnercentrum voor Microsoft Cloud Duitsland
> - Partnercentrum voor Microsoft Cloud for US Government

## <a name="prerequisites"></a>Vereisten

- Als u gebruikmaakt van de .NET SDK van partner Center, is versie 1,9 of nieuwer vereist.

- Als u de Java SDK van het partner centrum gebruikt, is versie 1,8 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center-verificatie](./partner-center-authentication.md). Dit scenario ondersteunt alleen app + gebruikers verificatie.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

## <a name="net-version-14-or-newer"></a>.NET (versie 1,4 of nieuwer)

Bevestiging (en) van door de klant geaccepteerde acceptatie ophalen:

- Gebruik de verzameling **IAggregatePartner. Customers** en roep **ById** methode aan met de opgegeven klant-id.

- Haal de eigenschap **overeenkomsten** op en filter de resultaten op Microsoft Cloud overeenkomst door de methode **ByAgreementType** aan te roepen.

- Roep **Get** -of **GetAsync** -methode aan.

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCloudAgreement";

var cloudAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

Een volledig voor beeld vindt u in de [GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) -klasse in het [console test-app](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples) -project.

## <a name="net-version-19---113"></a>.NET (versie 1,9-1,13)

Bevestiging van een eerder gegeven klant acceptatie ophalen:

Gebruik de verzameling **IAggregatePartner. Customers** en roep de methode **ById** aan met de opgegeven klant-id. Vervolgens haalt u de eigenschap **overeenkomsten** op, gevolgd door de methoden **Get** of **GetAsync** aan te roepen.

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var agreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Get();
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Bevestiging van een eerder gegeven klant acceptatie ophalen:

Gebruik de functie **IAggregatePartner. getCustomers** en roep de functie **byId** aan met de opgegeven klant-id. Haal vervolgens de functie **getAgreements** op, gevolgd door de **Get** -functie aan te roepen.

```java
// IAggregatePartner partnerOperations;
// String selectedCustomerId;

ResourceCollection<Agreement> agreements = partnerOperations.getCustomers().byId(selectedCustomerId).getAgreements().get();
```

Een volledig voor beeld vindt u in de [GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) -klasse in het [console test-app](https://github.com/Microsoft/Partner-Center-Java-Samples) -project.

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Bevestiging van een eerder gegeven klant acceptatie ophalen:

Gebruik de opdracht [**Get-PartnerCustomerAgreement**](/powershell/module/partnercenter/get-partnercustomeragreement) .

```powershell
Get-PartnerCustomerAgreement -CustomerId '14876998-c0dc-46e6-9d0c-65a57a6c32ec'
```

## <a name="rest-request"></a>REST-aanvraag

Zie de volgende instructies voor het ophalen van de bevestiging van de klant acceptatie die eerder is verschaft.

Maak een nieuwe **overeenkomst** resource met de relevante certificerings informatie.

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode | Aanvraag-URI                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| GET    | [*\{ BASEURL \}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/agreements http/1.1 |

#### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om de klant op te geven die u bevestigt.

| Naam             | Type | Vereist | Beschrijving                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| CustomerTenantId | GUID | J        | De waarde is een GUID-indeling **CustomerTenantId** waarmee u een klant kunt opgeven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/14876998-c0dc-46e6-9d0c-65a57a6c32ec/agreements HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 94e4e214-6b06-4fb7-96d1-94d559f9b47f
MS-CorrelationId: ab993325-1605-4cf4-bac4-fb584142a31b
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een verzameling **overeenkomst** resources in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

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
                "email":"SomeEmail@Outlook.com"
                "phoneNumber":"1234567890"
            },
            "templateId":"998b88de-aa99-4388-a42c-1b3517d49490",
            "dateAgreed":"2018-07-28T00:00:00",
            "type":"MicrosoftCloudAgreement",
            "agreementLink":"https://docs.microsoft.com/partner-center/agreements"
        },
        {
            "primaryContact":
            {
                "firstName":"Tania",
                "lastName":"Carr",
                "email":"SomeEmail@Outlook.com"
                "phoneNumber:"1234567890"
            },
            "templateId":"998b88de-aa99-4388-a42c-1b3517d49490",
            "dateAgreed":"2017-08-01T00:00:00",
            "type":"MicrosoftCloudAgreement",
            "agreementLink":"https://docs.microsoft.com/partner-center/agreements"
        }
    ]
}
```
