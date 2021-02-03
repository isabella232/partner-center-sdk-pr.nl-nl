---
title: Softwareaankopen annuleren
description: U kunt kiezen voor het annuleren van software-abonnementen en aankopen met een permanente software met behulp van partner Center-Api's.
ms.date: 12/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 25fd10a171fa6ca01f3442d49145443f2382cc18
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767370"
---
# <a name="cancel-software-purchases"></a>Softwareaankopen annuleren

**Van toepassing op:**

- Partnercentrum

U kunt de Api's van het partner centrum gebruiken om software-abonnementen en aankopen met een permanente software te annuleren (zolang de aankopen zijn gedaan in het annulerings venster vanaf de aankoop datum). U hoeft geen ondersteunings ticket te maken om dergelijke annuleringen te maken en u kunt in plaats daarvan de volgende self-service methoden gebruiken.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

## <a name="c"></a>C\#

Als u een software order wilt annuleren,

1. Geef uw account referenties door aan de [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) -methode om een [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) -interface te verkrijgen om partner bewerkingen te verkrijgen.

2. Selecteer een bepaalde [order](order-resources.md#order) die u wilt annuleren. Roep de methode [**klanten. ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id, gevolgd door **Orders. ById ()** met Order-id.

3. Roep de methode **Get** of **GetAsync** aan om de volg orde op te halen.

4. Stel de eigenschap [**order. status**](order-resources.md#order) in op `cancelled` .

5. Beschrijving Als u bepaalde regel items voor annulering wilt opgeven, stelt u de [**order. regel items**](order-resources.md#order) in op een lijst met regel items die u wilt annuleren.

6. Gebruik de methode **patch ()** om de volg orde bij te werken.

``` csharp
// IPartnerCredentials accountCredentials;
// Customer tenant Id to be deleted.
// string customerTenantId;

IPartner accountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(accountCredentials);

// Cancel order
var order = accountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Get();
order.Status = "cancelled";
order.LineItems = new List<OrderLineItem> {
    order.LineItems.First()
};
order = accountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(orderId).Patch(order);

```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode     | Aanvraag-URI                                                                            |
|------------|----------------------------------------------------------------------------------------|
| **VERZENDEN** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/orders/{order-id} http/1.1 |

### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende query parameters om een klant te verwijderen.

| Naam                   | Type     | Vereist | Beschrijving                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **klant-Tenant-id** | **guid** | J        | De waarde is een id voor de identiteit van een klant die de wederverkoper toestaat de resultaten te filteren voor een bepaalde klant die bij de wederverkoper hoort. |
| **order-id** | **tekenreeksexpressie** | J        | De waarde is een teken reeks waarmee de id wordt aangegeven van de order die u wilt annuleren. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

```http
{
    “id”: “2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
    status": "cancelled",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0FKZV:0003:DG7GMGF0DWMS"
        }
    ]
}
```

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/orders/<order-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd

{
    "id": "2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
    "status": "cancelled",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0FKZV:0003:DG7GMGF0DWMS"
        }
    ]
}
```

## <a name="rest-response"></a>REST-antwoord

Als deze methode is geslaagd, wordt de volg orde met Geannuleerde regel items geretourneerd.

De status van de bestelling wordt gemarkeerd als **geannuleerd** als alle regel items in de order worden geannuleerd of worden **voltooid** als niet alle regel items in de order worden geannuleerd.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

In het volgende voor beeld kunt u zien dat de hoeveelheid van het regel item met de aanbiedings-id **`DG7GMGF0FKZV:0003:DG7GMGF0DWMS`** nul (0) is geworden. Deze wijziging betekent dat het regel item dat is gemarkeerd voor annulering, is geannuleerd. De voorbeeld volgorde bevat andere regel items die niet zijn geannuleerd. Dit betekent dat de status van de algemene order wordt gemarkeerd als **voltooid**, en niet wordt **geannuleerd**.

```http
HTTP/1.1 200 OK
Content-Length: 866
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "id": "2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
    "alternateId": "c403d91b21d2",
    "referenceCustomerId": "45411344-b09d-47e7-9653-542006bf9766",
    "billingCycle": "one_time",
    "currencyCode": "USD",
    "currencySymbol": "$",
    "lineItems": [
        {
            "lineItemNumber": 0,
            "offerId": "DG7GMGF0FKZV:0003:DG7GMGF0DWMS",
            "termDuration": "P3Y",
            "transactionType": "New",
            "friendlyName": "SQL Server Enterprise - 2 Core License Pack - 3 year",
            "quantity": 0,
            "links": {
                "product": {
                    "uri": "/products/DG7GMGF0FKZV?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DG7GMGF0FKZV/skus/0003?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DG7GMGF0FKZV/skus/0003/availabilities/DG7GMGF0DWMS?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        },
        {
            "lineItemNumber": 1,
            "offerId": "DG7GMGF0DVT7:000C:DG7GMGF0FVZM",
            "termDuration": "P3Y",
            "transactionType": "New",
            "friendlyName": "Windows Server CAL - 1 Device CAL - 3 year",
            "quantity": 1,
            "links": {
                "product": {
                    "uri": "/products/DG7GMGF0DVT7?country=US",
                    "method": "GET",
                    "headers": []
                },
                "sku": {
                    "uri": "/products/DG7GMGF0DVT7/skus/000C?country=US",
                    "method": "GET",
                    "headers": []
                },
                "availability": {
                    "uri": "/products/DG7GMGF0DVT7/skus/000C/availabilities/DG7GMGF0FVZM?country=US",
                    "method": "GET",
                    "headers": []
                }
            }
        }
    ],
    "creationDate": "2019-12-12T17:33:56.1306495Z",
    "status": "completed",
    "transactionType": "UserPurchase",
    "links": {
        "self": {
            "uri": "/customers/45411344-b09d-47e7-9653-542006bf9766/orders/2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
            "method": "GET",
            "headers": []
        },
        "provisioningStatus": {
            "uri": "/customers/45411344-b09d-47e7-9653-542006bf9766/orders/2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "patchOperation": {
            "uri": "/customers/45411344-b09d-47e7-9653-542006bf9766/orders/2y6dF_rVgDAXMxypQPPnTquuXhKVK_3N1",
            "method": "PATCH",
            "headers": []
        }
    },
    "client": {
        "marketplaceCountry": "US",
        "deviceFamily": "UniversalStore-PartnerCenter",
        "name": "Partner Center API"
    },
    "attributes": {
        "objectType": "Order"
    }
}
```
