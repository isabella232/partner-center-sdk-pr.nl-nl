---
title: Een proefabonnement converteren naar betaald
description: Meer informatie over het gebruik van partner Center-Api's voor het converteren van een proef abonnement op een betaalde versie.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 59dcf6caf21d407b2fba4cc8438bc435fda9dc77
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767616"
---
# <a name="convert-a-trial-subscription-to-paid-using-partner-center-apis"></a>Een proef abonnement converteren naar betaald met partner Center-Api's

**Van toepassing op:**

- Partnercentrum

U kunt een proef abonnement converteren naar betaald.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een abonnements-ID voor een actief proef abonnement.

- Een beschik bare conversie aanbieding.

## <a name="convert-a-trial-subscription-to-paid-through-code"></a>Een proef abonnement converteren naar betaald via code

Als u een proef abonnement wilt omzetten in een betaalde versie, moet u eerst een verzameling van de beschik bare proef versies ophalen. Vervolgens moet u het conversie aanbod kiezen dat u wilt kopen.

In de conversie aanbiedingen wordt een hoeveelheid opgegeven die standaard hetzelfde aantal licenties heeft als het proef abonnement. U kunt dit aantal wijzigen door de eigenschap [**hoeveelheid**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion.quantity) in te stellen op het aantal licenties dat u wilt kopen.

> [!NOTE]
> Ongeacht het aantal aangeschafte licenties, wordt de abonnements-ID van de proef versie opnieuw gebruikt voor de aangeschafte licenties. Als gevolg hiervan verdwijnt de proef versie en wordt deze vervangen door de aankoop.

Voer de volgende stappen uit om een proef abonnement te converteren met behulp van code:

1. Een interface voor de beschik bare abonnements bewerkingen ophalen. U moet de klant identificeren en de abonnements-id van het proef abonnement opgeven.

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2. Een verzameling van de beschik bare conversie aanbiedingen ophalen. Zie voor meer informatie en Details over de aanvraag/reactie voor deze methode [een lijst met aanbiedingen voor proef conversie ophalen](get-a-list-of-trial-conversion-offers.md).

    ``` csharp
    var conversions = subscriptionOperations.Conversions.Get();
    ```

3. Kies een conversie aanbieding. Met de volgende code wordt de eerste conversie aanbieding in de verzameling gekozen.

    ``` csharp
    var selectedConversion = conversions.Items.ToList()[0];
    ```

4. Geef desgewenst het aantal licenties op dat u wilt aanschaffen. De standaard waarde is het aantal licenties in het proef abonnement.

    ``` csharp
    selectedConversion.Quantity = 10;
    ```

5. Roep de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) aan om het proef abonnement te converteren naar betaald.

    ``` csharp
    var convertResult = subscriptionOperations.Conversions.Create(selectedConversion);
    ```

## <a name="c"></a>C\#

U kunt als volgt een proef abonnement omzetten naar een betaalde versie:

1. Gebruik de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.

2. Een interface voor het uitvoeren van abonnementen ophalen door de methode [**abonnementen. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) aan te roepen met de id van het proef abonnement. Sla een verwijzing op naar de operations-interface van het abonnement in een lokale variabele.

3. Gebruik de eigenschap [**conversies**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) om een interface te verkrijgen voor de beschik bare bewerkingen op conversies en roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) aan om een verzameling beschik bare [**conversie**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) aanbiedingen op te halen. U moet er een kiezen. In het volgende voor beeld wordt standaard de eerste conversie beschikbaar.

4. Gebruik de verwijzing naar de operations-interface voor abonnementen die u hebt opgeslagen in een lokale variabele en de eigenschap [**conversies**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) om een interface te verkrijgen voor de beschik bare bewerkingen op conversies.

5. Geef het geselecteerde object voor de conversie aanbieding door aan de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) om de proef versie te converteren.

### <a name="c-example"></a>C- \# voor beeld

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;
// string subscriptionId;

// Get subscription operations for the trial subscription.
var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);

// Get the available conversions.
var conversions = subscriptionOperations.Conversions.Get();

// If there are no conversions available, we&#39;re done.
// Otherwise, convert the trial to the first available conversion offer.
if (conversions.TotalCount <= 0)
{
    System.Console.WriteLine("This subscription has no conversions");
}
else
{
    // Default to the first conversion.
    var selectedConversion = conversions.Items.ToList()[0];

    // Convert the trial and return the result.
    var convertResult = subscriptionOperations.Conversions.Create(selectedConversion);
}
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode   | Aanvraag-URI                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/Subscriptions/{Subscription-id}/conversions http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende Path-para meters om het klant-en proef abonnement te identificeren.

| Naam            | Type   | Vereist | Beschrijving                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| klant-id     | tekenreeks | Yes      | Een teken reeks met een GUID-indeling die de klant identificeert.           |
| abonnement-id | tekenreeks | Yes      | Een teken reeks met een GUID-indeling waarmee het proef abonnement wordt geïdentificeerd. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Een gevulde [conversie](conversions-resources.md#conversion) resource moet worden opgenomen in de hoofd tekst van de aanvraag.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/customers/0c39d6d5-c70d-4c55-bc02-f620844f3fd1/subscriptions/488745B5-2086-4912-802C-6ABB9F7C3638/conversions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bd0cde7f-ba87-4010-8a73-1190b641f2a4
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 234
Expect: 100-continue

{
    "OfferId": "C0BD2E08-11AC-4836-BDC7-3712E744922F",
    "TargetOfferId": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "OrderId": "D51A052E-043C-4A2A-AA37-2BB938CEF6C1",
    "Quantity": 25,
    "BillingCycle": "monthly",
    "Attributes": {
        "ObjectType": "Conversion"
    }
}
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord tekst een [ConversionResult](conversions-resources.md#conversionresult) -resource.

#### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.

#### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 211
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 8daa6d54-72ab-4d6b-9c7d-9266d3734a47
MS-RequestId: bd0cde7f-ba87-4010-8a73-1190b641f2a4
MS-CV: kW4GzmhvHEqCq1ls.0
MS-ServerId: 030020643
Date: Thu, 15 Jun 2017 23:10:40 GMT

 {
    "subscriptionId": "488745B5-2086-4912-802C-6ABB9F7C3638",
    "offerId": "C0BD2E08-11AC-4836-BDC7-3712E744922F",
    "targetOfferId": "031C9E47-4802-4248-838E-778FB1D2CC05",
    "attributes": {
        "objectType": "ConversionResult"
    }
}
```
