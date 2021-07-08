---
title: Factureringsprofiel van een partner ophalen
description: Haalt een -object op dat het factureringsprofiel van de partner vertegenwoordigt.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 225d8ea2d92933838ae47eaf3308276aa1f1684c
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548971"
---
# <a name="get-partner-billing-profile"></a>Factureringsprofiel van een partner ophalen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Haalt een -object op dat het factureringsprofiel van de partner vertegenwoordigt.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.

## <a name="c"></a>C\#

Als u een partnerfactureringsprofiel wilt ophalen, gebruikt u de verzameling **IAggregatePartner.Profiles** en roept u de **eigenschap BillingProfile aan.** Roep ten slotte de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.profiles.ibillingprofile.getasync) aan.

``` csharp
// IAggregatePartner partnerOperations;

BillingProfile billingProfile = partnerOperations.Profiles.BillingProfile.Get();
```

**Voorbeeld:** [consoletest-app](console-test-app.md). **Project:** PartnerCenterSDK.FeaturesKlasse: GetBillingProfile.cs 

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                              |
|---------|--------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/profiles/billing HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/profiles/billing HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a0dd6cde-b24c-413c-af24-416446dc5599
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een **BillingProfile-object** in de antwoord-body.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 568
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 1bb03149-88d2-4bc2-9cc1-d6e83890fa9e
MS-RequestId: a0dd6cde-b24c-413c-af24-416446dc5599
Date: Tue, 22 Mar 2016 17:10:02 GMT

{
    "companyName":"TEST_TEST_BugBash1",
    "address":{
        "country":"US",
        "city":"Redmond",
        "state":"WA",
        "addressLine1":"1 Microsoft Way",
        "addressLine2":"","postalCode":"98052"
    },
    "primaryContact":{
        "firstName":"James",
        "lastName":"Burk",
        "phoneNumber":"2066017143"
    },
    "purchaseOrderNumber":"9888",
    "taxId":"12-345678",
    "billingCurrency":"USD",
    "profileType":"BillingProfile",
    "links":{
        "self":{
            "uri":"/profiles/billing",
            "method":"GET",
            "headers":[]
        }
    },
    "attributes":{
        "etag":<etag>,
        "objectType":"BillingProfile"
    }
}
```
