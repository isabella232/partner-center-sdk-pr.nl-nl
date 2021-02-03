---
title: Een klantaccount verwijderen uit de integratie-sandbox
description: Een klant account verwijderen uit de sandbox met Testing in Production (tip) Integration.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e3a1642c0202c174ddd4f65a6aeda2752def9176
ms.sourcegitcommit: b1ff781b67b1d322820bbcac2c583229201a8c07
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/29/2020
ms.locfileid: "97767402"
---
# <a name="delete-a-customer-account-from-the-integration-sandbox"></a>Een klantaccount verwijderen uit de integratie-sandbox

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt uitgelegd hoe u de relatie tussen de partner en het klant account verbreekt en de sandbox-integratie voor Testing in Production (tip) in de quota kunt herstellen.

> [!IMPORTANT]
> Wanneer u een klant account verwijdert, worden alle resources die zijn gekoppeld aan de Tenant van de klant, verwijderd.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een klant-ID ( `customer-tenant-id` ). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).

- Alle Azure Reserved Virtual Machine Instances-en software-inkoop orders moeten worden geannuleerd voordat u een klant verwijdert uit de tip Integration sandbox.

## <a name="c"></a>C\#

Een klant verwijderen uit de tip Integration sandbox:

1. Geef de referenties van uw tip-account door aan de methode [**CreatePartnerOperations**](/dotnet/api/microsoft.store.partnercenter.partnerservice.instance) om een [**IPartner**](/dotnet/api/microsoft.store.partnercenter.ipartner) -interface te verkrijgen voor partner bewerkingen.

2. Gebruik de interface voor partner bewerkingen om de verzameling van rechten op te halen:

    1. Roep de methode [**klanten. ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan bij de klant-id om de klant op te geven.

    2. Roep de eigenschap **rechten** aan.

    3. Roep de methode **Get** of **GetAsync** aan om de [**rechtings**](entitlement-resources.md) verzameling op te halen.

3. Zorg ervoor dat alle Azure Reserved Virtual Machine Instances-en software-inkoop orders voor die klant zijn geannuleerd. Voor elke [**recht**](entitlement-resources.md) in de verzameling:

    1. Gebruik het [**recht. ReferenceOrder.Id**](entitlement-resources.md#referenceorder) voor het ophalen van een lokale kopie van de bijbehorende [order](order-resources.md#order) van de verzameling orders van de klant.

    2. Stel de eigenschap [**order. status**](order-resources.md#order) in op "geannuleerd".

    3. Gebruik de methode **patch ()** om de volg orde bij te werken.

4. Alle orders annuleren. Het volgende code voorbeeld maakt bijvoorbeeld gebruik van een lus om elke volg orde te pollen totdat de status ' geannuleerd ' is.

    ``` csharp
    // IPartnerCredentials tipAccountCredentials;
    // Customer tenant Id to be deleted.
    // string customerTenantId;

    IPartner tipAccountPartnerOperations = PartnerService.Instance.CreatePartnerOperations(tipAccountCredentials);

    // Get all entitlements whose order must be cancelled.
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
        // Check if all the orders were cancelled.
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

5. Zorg ervoor dat alle orders zijn geannuleerd door de **verwijderings** methode voor de klant aan te roepen.

Voor **beeld**: [console test-app](console-test-app.md). **Project**: partner centrum PartnerCenterSDK. FeaturesSamples **klasse**: DeleteCustomerFromTipAccount.cs

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode     | Aanvraag-URI                                                                            |
|------------|----------------------------------------------------------------------------------------|
| DELETE     | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id} http/1.1 |

#### <a name="uri-parameter"></a>URI-para meter

Gebruik de volgende query parameter om een klant te verwijderen.

| Naam                   | Type     | Vereist | Beschrijving                                                                         |
|------------------------|----------|----------|-------------------------------------------------------------------------------------|
| klant-Tenant-id     | GUID     | J        | De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5
Date: Wed, 16 Mar 2016 00:43:02 GMT
```
