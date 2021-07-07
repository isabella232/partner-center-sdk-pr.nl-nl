---
title: Een klantaccount verwijderen uit de integratie-sandbox
description: Een klantaccount verwijderen uit de sandbox voor Testing in Production -integratie (Tip).
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b9d9e44ac9c40bd4e3c7e1a9e04253f853dfd96c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973125"
---
# <a name="delete-a-customer-account-from-the-integration-sandbox"></a>Een klantaccount verwijderen uit de integratie-sandbox

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

In dit artikel wordt uitgelegd hoe u de relatie tussen de partner en het klantaccount verbreekt en het quotum voor de sandbox voor Testing in Production -integratie (Tip) opnieuw kunt krijgen.

> [!IMPORTANT]
> Wanneer u een klantaccount verwijdert, worden alle resources verwijderd die zijn gekoppeld aan die klantten tenant.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Alle Azure Reserved Virtual Machine Instances en software-aankooporders moeten worden geannuleerd voordat u een klant uit de Sandbox voor tipintegratie kunt verwijderen.

## <a name="c"></a>C\#

Een klant verwijderen uit de Sandbox voor Tip-integratie:

1. Geef uw Tip-accountreferenties door aan [**de methode CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) om een [**IPartner-interface**](/dotnet/api/microsoft.store.partnercenter.ipartner) voor partnerbewerkingen op te halen.

2. Gebruik de interface voor partnerbewerkingen om de verzameling rechten op te halen:

    1. Roep de [**methode Customers.ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant op te geven.

    2. Roep de **eigenschap Rechten aan.**

    3. Roep de **methode Get** of **GetAsync aan** om de rechtenverzameling op [**te**](entitlement-resources.md) halen.

3. Zorg ervoor dat alle Azure Reserved Virtual Machine Instances- en softwareaankooporders voor die klant worden geannuleerd. Voor elk [**recht**](entitlement-resources.md) in de verzameling:

    1. Gebruik het [**recht. ReferenceOrder.Id**](entitlement-resources.md#referenceorder) lokale kopie van de bijbehorende order [ophalen](order-resources.md#order) uit de verzameling orders van de klant.

    2. Stel de [**eigenschap Order.Status**](order-resources.md#order) in op Geannuleerd.

    3. Gebruik de **methode Patch()** om de volgorde bij te werken.

4. Annuleer alle orders. In het volgende codevoorbeeld wordt bijvoorbeeld een lus gebruikt om elke bestelling te peilen totdat de status 'Geannuleerd' is.

    ``` csharp
    // IPartnerCredentials tipAccountCredentials;
    // Customer tenant Id to be deleted.
    // string customerTenantId;

    IPartner tipAccountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(tipAccountCredentials);

    // Get all entitlements whose order must be canceled.
    ResourceCollection<Entitlement> entitlements = tipAccountPartnerOperations.Customers.ById(customerTenantId).Entitlements.Get();

    // Cancel all orders
    foreach (var entitlement in entitlements)
    {
        var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(entitlement.ReferenceOrder.Id).Get();
        order.Status = "Cancelled";
        order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(order.Id).Patch(order);
    }

    // Keep polling until the status of all orders is "Cancelled".
    bool proceed = true;
    do
    {
        // Check if all the orders were canceled.
        foreach (var entitlement in entitlements)
        {
            var order = tipAccountPartnerOperations.Customers.ById(customerTenantId).Orders.ById(entitlement.ReferenceOrder.Id).Get();
            if (!order.Status.Equals("Cancelled", StringComparison.OrdinalIgnoreCase))
            {
                proceed = false;
            }
        }

        // Wait for a few seconds.
        Thread.Sleep(5000);
    }
    while (proceed == false);

    tipAccountPartnerOperations.Customers.ById(customerTenantId).Delete();
    ```

5. Zorg ervoor dat alle orders worden geannuleerd door de methode **Delete voor** de klant aan te roepen.

**Voorbeeld:** [Consoletest-app](console-test-app.md). **Project:** Partner Center PartnerCenterSDK.FeaturesSamples-klasse: DeleteCustomerFromTipAccount.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode     | Aanvraag-URI                                                                            |
|------------|----------------------------------------------------------------------------------------|
| DELETE     | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id} HTTP/1.1 |

#### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameter om een klant te verwijderen.

| Naam                   | Type     | Vereist | Beschrijving                                                                         |
|------------------------|----------|----------|-------------------------------------------------------------------------------------|
| customer-tenant-id     | GUID     | J        | De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Accept: application/json
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een leeg antwoord.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Mar 2016 00:43:02 GMT
```
