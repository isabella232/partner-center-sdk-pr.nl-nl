---
title: Bevestiging van acceptatie door de klant van Microsoft Cloud-overeenkomst ophalen
description: In dit artikel wordt uitgelegd hoe u bevestiging krijgt van de klantacceptatie van de Microsoft Cloud-overeenkomst.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
aauthor: khakiali
ms.author: alikhaki
ms.openlocfilehash: 1b1a8cbacb667e579bcd218a29c3f553afce26c2
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111549260"
---
# <a name="get-confirmation-of-customer-acceptance-of-microsoft-cloud-agreement"></a>Bevestiging van acceptatie door de klant van Microsoft Cloud-overeenkomst ophalen

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De **overeenkomstresource** wordt momenteel alleen ondersteund door Partner Center in de openbare Cloud van Microsoft.

## <a name="prerequisites"></a>Vereisten

- Als u de .NET SDK Partner Center, is versie 1.9 of nieuwer vereist.

- Als u de Java SDK Partner Center, is versie 1.8 of nieuwer vereist.

- Referenties zoals beschreven in [Partner Center verificatie](./partner-center-authentication.md). Dit scenario biedt alleen ondersteuning voor app- en gebruikersverificatie.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="net-version-14-or-newer"></a>.NET (versie 1.4 of nieuwer)

Bevestiging(en) ophalen van de klantacceptatie die eerder is opgegeven:

- Gebruik de **verzameling IAggregatePartner.Customers en** roep de **methode ById** aan met de opgegeven klant-id.

- Haal de **eigenschap Agreements** op en filter de resultaten naar Microsoft Cloud-overeenkomst door de **methode ByAgreementType aan te** roepen.

- Roep **de methode Get** of **GetAsync aan.**

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

string agreementType = "MicrosoftCloudAgreement";

var cloudAgreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.ByAgreementType(agreementType).Get();
```

Een volledig voorbeeld vindt u in de [klasse GetCustomerAgreements](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples/blob/master/Source/Partner%20Center%20SDK%20Samples/Agreements/GetCustomerAgreements.cs) van het [consoletest-app-project.](https://github.com/PartnerCenterSamples/Partner-Center-SDK-Samples)

## <a name="net-version-19---113"></a>.NET (versie 1.9 - 1.13)

Bevestiging van eerder opgegeven klantacceptatie ophalen:

Gebruik de **verzameling IAggregatePartner.Customers** en roep de **ById-methode** aan met de opgegeven klant-id. Haal vervolgens de eigenschap **Agreements op,** gevolgd door de methoden **Get** of **GetAsync aan te** roepen.

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var agreements = partnerOperations.Customers.ById(selectedCustomerId).Agreements.Get();
```

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

Bevestiging van eerder opgegeven klantacceptatie ophalen:

Gebruik de **functie IAggregatePartner.getCustomers** en roep de **functie byId** aan met de opgegeven klant-id. Haal vervolgens de **functie getAgreements** op, gevolgd door het aanroepen van de **functie get.**

```java
// IAggregatePartner partnerOperations;
// String selectedCustomerId;

ResourceCollection<Agreement> agreements = partnerOperations.getCustomers().byId(selectedCustomerId).getAgreements().get();
```

Een volledig voorbeeld vindt u in de [klasse GetCustomerAgreements](https://github.com/microsoft/Partner-Center-Java-Samples/blob/master/sdk/src/main/java/com/microsoft/store/partnercenter/samples/agreements/GetCustomerAgreements.java) van het [consoletest-app-project.](https://github.com/Microsoft/Partner-Center-Java-Samples)

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Bevestiging van eerder opgegeven klantacceptatie ophalen:

Gebruik de [**opdracht Get-PartnerCustomerAgreement.**](/powershell/module/partnercenter/get-partnercustomeragreement)

```powershell
Get-PartnerCustomerAgreement -CustomerId '14876998-c0dc-46e6-9d0c-65a57a6c32ec'
```

## <a name="rest-request"></a>REST-aanvraag

Zie de volgende instructies om de bevestiging op te halen dat de klant eerder is geaccepteerd.

Maak een nieuwe **Overeenkomst-resource** met de relevante certificeringsinformatie.

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI                                                                                      |
|--------|--------------------------------------------------------------------------------------------------|
| GET    | [*\{ baseURL \}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/agreements HTTP/1.1 |

#### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om de klant op te geven die u wilt bevestigen.

| Naam             | Type | Vereist | Beschrijving                                                                               |
|------------------|------|----------|-------------------------------------------------------------------------------------------|
| CustomerTenantId | GUID | J        | De waarde is een MET GUID **opgemaakte CustomerTenantId** waarmee u een klant kunt opgeven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

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

Als dit lukt, retourneert deze methode een verzameling **Agreement-resources** in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
