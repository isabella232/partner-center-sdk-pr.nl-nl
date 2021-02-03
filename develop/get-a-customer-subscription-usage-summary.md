---
title: Gebruiks overzicht van het abonnement van de klant ophalen
description: U kunt de SubscriptionUsageSummary-Resource gebruiken om een samen vatting van het gebruik van een specifieke Azure-service of resource te verkrijgen tijdens de huidige facturerings periode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 30334b6f08829eccf0693b566c11f94cb3ece976
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767307"
---
# <a name="get-usage-summary-for-customers-subscription"></a>Gebruiks overzicht van het abonnement van de klant ophalen

**Van toepassing op:**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

U kunt de **SubscriptionUsageSummary** -Resource gebruiken om een samen vatting van het gebruik van een abonnement voor een klant te verkrijgen. Deze resource vertegenwoordigt de samen vatting van het abonnements gebruik van een specifieke Azure-service of resource tijdens de huidige facturerings periode.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Een abonnements-id

## <a name="c"></a>C\#

Voor een overzicht van het gebruik van een abonnement voor het abonnement van een klant:

1. Gebruik uw verzameling **IAggregatePartner. Customers** om de methode **ById ()** aan te roepen.

2. Roep vervolgens de eigenschap abonnementen aan, evenals de eigenschap **UsageSummary** . Voltooi door de methoden Get () of GetAsync () aan te roepen.

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var subscriptionUsageSummary = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageSummary.Get();
    ```

Voor een voor beeld ziet u het volgende:

- Voor beeld: [console test-app](console-test-app.md)
- Project: **PartnerSDK. FeatureSamples**
- Klasse: **GetSubscriptionUsageSummary.cs**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                                                        |
|---------|------------------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{Subscription-id}/usagesummary http/1.1 |

#### <a name="uri-parameters"></a>URI-para meters

Deze tabel bevat de vereiste query parameters voor het ophalen van de geclassificeerde gebruiks gegevens van de klant.

| Naam                   | Type     | Vereist | Beschrijving                               |
|------------------------|----------|----------|-------------------------------------------|
| **klant-Tenant-id** | **guid** | J        | Een GUID die overeenkomt met de klant.     |
| **abonnement-id**    | **guid** | J        | Een GUID die overeenkomt met de id van een abonnement. Voor een Azure-abonnement is dit de id van het bijbehorende partner centrum- [abonnements resource](subscription-resources.md#subscription), dat het Azure-plan vertegenwoordigt. *Geef voor Azure-plannen voor abonnements abonnementen het **plan-id** op als de **abonnements-id** in deze route.* |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/usagesummary HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een **SubscriptionUsageSummary** -resource in de hoofd tekst van het antwoord.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor een volledige lijst.

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a>Antwoord voorbeeld voor Microsoft Azure-abonnementen (MS-AZR-0145P)

In dit voor beeld heeft de klant een **145P Azure PayG** -aanbieding aangeschaft.

*Voor klanten met Microsoft Azure-abonnementen (MS-AZR-0145P) is er geen wijziging in de API-reactie.*

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "resourceId": "ABCDEFGH-F347-41B6-B02C-187B1B778A43",
    "id": "ABCDEFGH-F347-41B6-B02C-187B1B778A43",
    "resourceName": "Microsoft Azure",
    "name": "Microsoft Azure",
    "billingStartDate": "2019-08-28T00:00:00-07:00",
    "billingEndDate": "2019-09-27T00:00:00-07:00",
    "totalCost": 22.861172,
    "currencyLocale": "fr-FR",
    "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SubscriptionUsageSummary"
    }
}
```

## <a name="rest-response-example-for-azure-plan"></a>Voor beeld van REST Response voor Azure-abonnement

In dit voor beeld heeft de klant een Azure-abonnement aangeschaft.

*Voor klanten met Azure-abonnementen zijn de volgende wijzigingen van de API-reactie:*

- **currencyLocale** wordt vervangen door **currencyCode**
- **usdTotalCost** is een nieuw veld

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac1
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "resourceId": "11111111-dca5-6f31-d3a6-dbbfad9be0fc",
    "resourceName": "Azure plan",
    "billingStartDate": "2019-09-01T00:00:00+00:00",
    "billingEndDate": "2019-10-01T00:00:00+00:00",
    "totalCost": 28.82860766744404945074,
    "currencyCode": "GBP",
    "usdTotalCost": 35.23000000000000362337,
    "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/usagesummary",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "SubscriptionUsageSummary"
    }
}
```
