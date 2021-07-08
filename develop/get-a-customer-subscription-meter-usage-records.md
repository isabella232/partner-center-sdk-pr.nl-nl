---
title: Gebruiksgegevens voor het abonnement per meter ophalen
description: U kunt de MeterUsageRecord-resourceverzameling gebruiken om metergebruiksrecords van een klant op te halen voor specifieke Azure-services of -resources tijdens de huidige factureringsperiode.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0bd6143c80059bd140a4c4332ab4ec19c54d99f1
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874853"
---
# <a name="get-usage-data-for-subscription-by-meter"></a>Gebruiksgegevens voor het abonnement per meter ophalen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

U kunt de **MeterUsageRecord-resourceverzameling** gebruiken om metergebruiksrecords van een klant op te halen voor specifieke Azure-services of -resources tijdens de huidige factureringsperiode. Deze resourceverzameling vertegenwoordigt een geaggregeerd totaal voor elke meter voor de huidige factureringscyclus, voor uw hele Azure-plan.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een abonnements-id

*Deze nieuwe route is gelijk aan , die alleen blijft werken `subscriptions/{subscription-id}/usagerecords/resources` voor Microsoft Azure(MS-AZR-0145P)-abonnementen.* Deze nieuwe route ondersteunt zowel Microsoft Azure-abonnementen (MS-AZR-0145P) als Azure-abonnementen. Als u deze informatie voor uw Azure-plan wilt ontvangen, moet u overschakelen naar deze nieuwe route. Af tegenstelling tot de eigenschappen die in de volgende secties worden vermeld, is het antwoord hetzelfde als de oude route.

## <a name="c"></a>C\#

Gebruiksrecords van een klant voor een specifieke Azure-service of -resource op te halen tijdens de huidige factureringsperiode:

1. Gebruik de **verzameling IAggregatePartner.Customers om** de **methode ById() aan te** roepen.

2. Roep de eigenschap Abonnementen en **UsageRecords** aan en vervolgens de **eigenschap Meters.** Als laatste roept u de methoden Get() of GetAsync() aan.

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;
    // var selectedSubscriptionId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscriptionId).UsageRecords.Meters.Get();
    ```

Zie het volgende voorbeeld voor een voorbeeld:

- Voorbeeld: [Consoletest-app](console-test-app.md)
- Project: **PartnerSDK.FeatureSamples**
- Klasse: **GetSubscriptionUsageRecordsByMeter.cs**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                                             |
|---------|-----------------------------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

Deze tabel bevat de vereiste queryparameters om de beoordeelde gebruiksgegevens van de klant op te halen.

| Naam                   | Type     | Vereist | Beschrijving                               |
|------------------------|----------|----------|-------------------------------------------|
| **customer-tenant-id** | **guid** | J        | Een GUID die overeenkomt met de klant.     |
| **subscription-id**    | **guid** | J        | Een GUID die overeenkomt met de id van een Partner Center-abonnementsresource [die](subscription-resources.md#subscription)een Microsoft Azure-abonnement (MS-AZR-0145P) of een Azure-abonnement vertegenwoordigt. *Geef voor azure-abonnementsbronnen de **plan-id** op als **de abonnements-id** in deze route.* |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/meterusagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een **\<MeterUsageRecord> PagedResourceCollection-resource** in de hoofdgedeelte van het antwoord.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor een [volledige lijst.](error-codes.md)

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a>Voorbeeld van een Microsoft Azure (MS-AZR-0145P)

In dit voorbeeld heeft de klant **145P Azure PayG aangeschaft.**

*Voor klanten met een Microsoft Azure (MS-AZR-0145P) is er geen wijziging in het API-antwoord.*

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 1,
    "items": [
        {
            "status": "active",
            "offerId": "MS-AZR-0145P",
            "resourceId": "11111111-F347-41B6-B02C-187B1B778A43",
            "id": "11111111-F347-41B6-B02C-187B1B778A43",
            "resourceName": "Microsoft Azure",
            "name": "Microsoft Azure",
            "totalCost": 22.861172,
            "currencyLocale": "fr-FR",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-01T23:04:41.193+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/{customer-tenant-id}/subscriptions/usagerecords/",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```

## <a name="rest-response-example-for-azure-plan"></a>REST-antwoordvoorbeeld voor Azure-plan

In dit voorbeeld heeft de klant een Azure-abonnement aangeschaft.

*Voor klanten met Azure-plannen zijn er de volgende wijzigingen in het API-antwoord:*

- **currencyLocale** is vervangen door **currencyCode**
- **usdTotalCost** is een nieuw veld

```http
HTTP/1.1 200 OK
Content-Length: 1120
Content-Type: application/json
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
Date: Fri, 26 Feb 2016 20:31:45 GMT

{
    "totalCount": 4,
    "items": [
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNVX-005J-Data Transfer In (GB)",
            "meterName": "Data Transfer In",
            "category": "Bandwidth",
            "subcategory": "Bandwidth",
            "quantityUsed": 0.01129,
            "unit": "1 GB",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNVX-005J-Data Transfer Out (GB)",
            "meterName": "Data Transfer Out",
            "category": "Bandwidth",
            "subcategory": "Bandwidth",
            "quantityUsed": 0.000224,
            "unit": "1 GB",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNZ5-006G-10K Batch Write Operations",
            "meterName": "Batch Write Operations",
            "category": "Storage",
            "subcategory": "Tables",
            "quantityUsed": 0.2462,
            "unit": "10K",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        },
        {
            "subscriptionId": "{subscription-id}",
            "meterId": "DZH318Z0BNZ5-006G-Data Stored (GB/Month)",
            "meterName": "LRS Data Stored",
            "category": "Storage",
            "subcategory": "Tables",
            "quantityUsed": 0.002632,
            "unit": "1 GB/Month",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-17T21:08:44.2566667+00:00",
            "attributes": {
                "objectType": "MeterUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/<subscription-id>/meterusagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
