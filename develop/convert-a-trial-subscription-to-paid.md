---
title: Een proefabonnement converteren naar betaald
description: Meer informatie over het gebruik Partner Center API's om een proefabonnement te converteren naar een betaald abonnement.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c1876cfc796b683bfff00b7d137bcfe0b7162c78
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973856"
---
# <a name="convert-a-trial-subscription-to-paid-using-partner-center-apis"></a>Een proefabonnement converteren naar betaald met behulp Partner Center API's

U kunt een proefabonnement converteren naar betaald.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een abonnements-id voor een actief proefabonnement.

- Een beschikbare conversieaanbieding.

## <a name="convert-a-trial-subscription-to-a-paid-subscription-through-code"></a>Een proefabonnement converteren naar een betaald abonnement via code

Als u een proefabonnement wilt converteren naar een betaald abonnement, moet u eerst een verzameling van de beschikbare proefversies verkrijgen. Vervolgens moet u de conversieaanbieding kiezen die u wilt kopen.

Met de conversieaanbiedingen wordt een hoeveelheid opgegeven die standaard hetzelfde aantal licenties heeft als het proefabonnement. U kunt deze hoeveelheid wijzigen door de eigenschap [**Quantity**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion.quantity) in te stellen op het aantal licenties dat u wilt kopen.

> [!NOTE]
> Ongeacht het aantal aangeschafte licenties, wordt de abonnements-id van de proefversie opnieuw gebruikt voor de aangeschafte licenties. Als gevolg hiervan verdwijnt de proefversie van kracht en wordt deze vervangen door de aankoop.

Gebruik de volgende stappen om een proefabonnement te converteren via code:

1. Haal een interface op voor de beschikbare abonnementsbewerkingen. U moet de klant identificeren en de abonnements-id van het proefabonnement opgeven.

    ``` csharp
    var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
    ```

2. Een verzameling van de beschikbare conversieaanbiedingen ophalen. Zie Get a list of trial conversion offers (Een lijst met aanbiedingen voor proefconversie verkrijgen) voor meer informatie en details over de aanvraag/reactie [voor deze methode.](get-a-list-of-trial-conversion-offers.md)

    ``` csharp
    var conversions = subscriptionOperations.Conversions.Get();
    ```

3. Kies een conversieaanbieding. Met de volgende code wordt de eerste conversieaanbieding in de verzameling gekozen.

    ``` csharp
    var selectedConversion = conversions.Items.ToList()[0];
    ```

4. Geef desgewenst het aantal licenties op dat moet worden gekocht. De standaardwaarde is het aantal licenties in het proefabonnement.

    ``` csharp
    selectedConversion.Quantity = 10;
    ```

5. Roep de [**methode Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) of [**CreateAsync aan**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) om het proefabonnement te converteren naar betaald.

    ``` csharp
    var convertResult = subscriptionOperations.Conversions.Create(selectedConversion);
    ```

## <a name="c"></a>C\#

Een proefabonnement converteren naar een betaald abonnement:

1. Gebruik de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.

2. Haal een interface op voor abonnementsbewerkingen door de methode [**Subscriptions.ById aan te**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) roepen met de abonnements-id van het proefabonnement. Sla een verwijzing naar de interface voor abonnementsbewerkingen op in een lokale variabele.

3. Gebruik de [**eigenschap Conversies**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) om een interface te verkrijgen voor de beschikbare bewerkingen op conversies en roep vervolgens de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionconversioncollection.getasync) aan om een verzameling beschikbare conversieaanbiedingen [**op te**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.conversion) halen. U moet er een kiezen. In het volgende voorbeeld wordt standaard de eerste beschikbare conversie gebruikt.

4. Gebruik de verwijzing naar de interface voor [**abonnementsbewerkingen**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.conversions) die u hebt opgeslagen in een lokale variabele en de eigenschap Conversies om een interface te verkrijgen voor de beschikbare bewerkingen op conversies.

5. Geef het geselecteerde conversieaanbiedingsobject door aan [**de methode Create**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.create) of [**CreateAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionupgradecollection.createasync) om de conversie van het proefabonnement te proberen.

### <a name="c-example"></a>\#C-voorbeeld

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

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/subscriptions/{subscription-id}/conversions HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende padparameters om de klant en het proefabonnement te identificeren.

| Naam            | Type   | Vereist | Beschrijving                                                     |
|-----------------|--------|----------|-----------------------------------------------------------------|
| customer-id     | tekenreeks | Ja      | Een tekenreeks met GUID-indeling die de klant identificeert.           |
| subscription-id | tekenreeks | Ja      | Een tekenreeks met GUID-indeling die het proefabonnement identificeert. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Een ingevulde [conversieresource](conversions-resources.md#conversion) moet worden opgenomen in de aanvraag body.

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

Als dit lukt, bevat de antwoord-body een [ConversionResult-resource.](conversions-resources.md#conversionresult)

#### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)

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
