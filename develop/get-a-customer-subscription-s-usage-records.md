---
title: Alle gebruiksrecords voor abonnementen voor een klant ophalen
description: U kunt de resourceverzameling SubscriptionMonthlyUsageRecord gebruiken om in de huidige factureringsperiode abonnementsgebruiksrecords op te halen voor een klant van een specifieke Azure-service of -resource.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 976abd86f34c1c27184f277ffc89fbc65f16bb37
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874683"
---
# <a name="get-subscription-usage-records-for-a-customer"></a>Abonnementsgebruiksrecords voor een klant op halen

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

U kunt de resourceverzameling **SubscriptionMonthlyUsageRecord** gebruiken om in de huidige factureringsperiode abonnementsgebruiksrecords op te halen voor een klant van een specifieke Azure-service of -resource. Deze resource vertegenwoordigt alle abonnementen voor de klant. Voor een klant met een Azure-plan retourneert deze resource een lijst met deze abonnementen (geen afzonderlijke Azure-abonnementen).

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.** Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

## <a name="c"></a>C\#

Als u gebruiksrecords voor abonnementen wilt op halen voor een klant van een specifieke Azure-service of -resource tijdens de huidige factureringsperiode, moet u de volgende stappen uitvoeren:

1. Gebruik de **verzameling IAggregatePartner.Customers** om de **methode ById() aan te** roepen.

2. Roep vervolgens de **eigenschap Abonnementen en** de eigenschap **UsageRecords aan.** Als laatste roept u de methoden Get() of GetAsync() aan.

    ``` csharp
    // IAggregatePartner partnerOperations;
    // var selectedCustomerId as string;

    var usageRecords = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.UsageRecords.Get();
    ```

Zie voor een voorbeeld het volgende:

- Voorbeeld: [Consoletest-app](console-test-app.md)
- Project: **PartnerSDK.FeatureSamples**
- Klasse: **GetSubscriptionUsageRecords.cs**

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                      |
|---------|------------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1 |

#### <a name="uri-parameter"></a>URI-parameter

Deze tabel bevat de vereiste queryparameter om de beoordeelde gebruiksgegevens van de klant op te halen.

| Naam                   | Type     | Vereist | Beschrijving                           |
|------------------------|----------|----------|---------------------------------------|
| **customer-tenant-id** | **guid** | J        | Een GUID die overeenkomt met de klant. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/usagerecords HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e128c8e2-4c33-4940-a3e2-2e59b0abdc67
MS-CorrelationId: 47c36033-af5d-4457-80a4-512c1626fac4
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een **SubscriptionMonthlyUsageRecord-resource** in de hoofd body van het antwoord.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor een [volledige lijst.](error-codes.md)

### <a name="response-example-for-microsoft-azure-ms-azr-0145p-subscriptions"></a>Voorbeeld van een Microsoft Azure (MS-AZR-0145P)

In dit voorbeeld heeft de klant een **Azure PayG-aanbieding van 145P** aangeschaft.

*Voor klanten met Microsoft Azure -abonnementen (MS-AZR-0145P) is er geen wijziging in het API-antwoord.*

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
            "uri": "/customers/<customer-tenant-id>/subscriptions/usagerecords/",
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
Date: Tue, 17 Sep 2019 20:31:45 GMT

{
    "totalCount": 2,
    "items": [
        {
            "status": "active",
            "partnerOnRecord": "some-id",
            "offerId": "DZH318Z0BPS6:0001:DZH318Z0BML6",
            "resourceId": "11111111-7d58-6654-69fa-0797198155d3",
            "id": "11111111-7d58-6654-69fa-0797198155d3",
            "resourceName": "Azure plan",
            "name": "Azure plan",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        },
        {
            "status": "active",
            "partnerOnRecord": "some-id",
            "offerId": "DZH318Z0BPS6:0001:DZH318Z0BML6",
            "resourceId": "11111111-25aa-ebb8-2bb4-fb406307babd",
            "id": "11111111-25aa-ebb8-2bb4-fb406307babd",
            "resourceName": "Azure plan",
            "name": "Azure plan",
            "totalCost": 0,
            "currencyCode": "GBP",
            "usdTotalCost": 0,
            "lastModifiedDate": "2019-09-18T17:09:26.16+00:00",
            "attributes": {
                "objectType": "SubscriptionMonthlyUsageRecord"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/<customer-tenant-id>/subscriptions/usagerecords",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
