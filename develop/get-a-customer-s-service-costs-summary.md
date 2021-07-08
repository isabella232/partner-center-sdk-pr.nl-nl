---
title: Een samenvatting van de servicekosten van een klant ophalen
description: Hiermee worden de servicekosten van een klant voor de opgegeven factureringsperiode opgeslagen.
ms.date: 06/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1cab23238b5f62a02a5f7368f626648d5b1b5b7e
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874904"
---
# <a name="get-a-customers-service-costs-summary"></a>Een samenvatting van de servicekosten van een klant ophalen

Hiermee worden de servicekosten van een klant voor de opgegeven factureringsperiode opgeslagen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Een factureringsperiode-indicator ( **`mostrecent`** ).

## <a name="c"></a>C\#

Een samenvatting van de servicekosten voor de opgegeven klant ophalen:

1. Roep de [**methode IAggregatePartner.Customers.ById aan**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.

2. Gebruik de [**eigenschap ServiceCosts om**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicecosts) een interface te krijgen voor het verzamelen van kosten van de klantenservice.

3. Roep de [**methode ByBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.icustomerservicecostscollection.bybillingperiod) aan met een lid van de enumeratie [**ServiceCostsBillingPeriod**](/dotnet/api/microsoft.store.partnercenter.models.servicecosts.servicecostsbillingperiod) om een [**IServiceCostsCollection te retourneren.**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostscollection)

4. Gebruik de [**methode IServiceCostsCollection.Summary.Get**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostsummary.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customers.servicecosts.iservicecostsummary.getasync) om het overzicht van de servicekosten van de klant op te halen.

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var serviceCostsSummary = partnerOperations.Customers.ById(selectedCustomerId).ServiceCosts.ByBillingPeriod(ServiceCostsBillingPeriod.MostRecent).Summary.Get();
```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                                   |
|---------|---------------------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/servicecosts/{billing-period} HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende padparameters om de klant en de factureringsperiode te identificeren.

| Naam           | Type   | Vereist | Beschrijving                                                                                                                      |
|----------------|--------|----------|----------------------------------------------------------------------------------------------------------------------------------|
| customer-id    | guid   | Ja      | Een klant-id met GUID-indeling die de klant identificeert.                                                                       |
| factureringsperiode | tekenreeks | Ja      | Een indicator die de factureringsperiode vertegenwoordigt. De enige ondersteunde waarde is MostRecent. Het geval van de tekenreeks maakt niet uit. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/65726577-c208-40fd-9735-8c85ac9cac68/servicecosts/mostrecent HTTP/1.1
Authorization: Bearer <authorization token>
Accept: application/json
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body een [ServiceCostsSummary-resource](service-costs-resources.md) met informatie over de servicekosten.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 766
Content-Type: application/json; charset=utf-8
MS-CorrelationId: a687bc47-8d08-4b78-aff6-5a59aa2055c2
MS-RequestId: e6a3b6b2-230a-4813-999d-57f883b60d38
MS-CV: gPPoyNX1X0asAAcw.0
MS-ServerId: 101112202
Date: Fri, 02 Dec 2016 18: 54: 38 GMT

{
    "billingStartDate": "2015-12-12T00:00:00Z",
    "billingEndDate": "2016-01-11T00:00:00Z",
    "pretaxTotal": 17.22,
    "tax": 0.0,
    "afterTaxTotal": 17.22,
    "currencySymbol": "$",
    "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
    "details":
     [
        {
            "invoiceType": "Recurring",
            "summary": {
                "billingStartDate": "2015-12-12T00:00:00Z",
                "billingEndDate": "2016-01-11T00:00:00Z",
                "pretaxTotal": 17.22,
                "tax": 0.0,
                "afterTaxTotal": 17.22,
                "currencyCode": "USD",
                "currencySymbol": "$",
                "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
                "links": {},
                "attributes": {
                    "objectType": "ServiceCostsSummary"
                }
            }
        },
        {
            "invoiceType": "OneTime",
            "summary": {
                "billingStartDate": "2019-04-01T00:00:00Z",
                "billingEndDate": "2019-04-30T23:59:59.9999999Z",
                "pretaxTotal": 2,
                "tax": 0.2,
                "afterTaxTotal": 2.2,
                "currencyCode": "USD",
                "currencySymbol": "$",
                "customerId": "ae1d5b32-f9ff-4252-b2bf-40e21937a51a",
                "links": {},
                "attributes": {
                    "objectType": "ServiceCostsSummary"
                }
            }
        }
    ],
    "links": {
        "serviceCostLineItems": {
            "uri": "/customers/ae1d5b32-f9ff-4252-b2bf-40e21937a51a/servicecosts/MostRecent/lineitems",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/ae1d5b32-f9ff-4252-b2bf-40e21937a51a/servicecosts/MostRecent",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "ServiceCostsSummary"
    }
}
```
