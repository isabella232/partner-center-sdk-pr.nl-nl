---
title: Een sandbox-abonnement voor commerciële Marketplace-producten activeren
description: Meer informatie over het gebruik van C/# en de REST Api's van het Partner Center om een sandbox-abonnement voor commerciële Marketplace-producten te activeren.
ms.date: 09/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a78b2c84368b29f1378f46971c4814929094e299
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "97767578"
---
# <a name="activate-a-sandbox-subscription-for-commercial-marketplace-saas-products-to-enable-billing"></a>Een sandbox-abonnement voor SaaS-producten voor commerciële Marketplace activeren om facturering mogelijk te maken

**Van toepassing op:**

- Partnercentrum

Het activeren van een abonnement voor software als een service (SaaS) voor commerciële Marketplace vanuit integratie Sandbox-accounts om facturering mogelijk te maken.

> [!NOTE]
> Het is alleen mogelijk om een abonnement te activeren voor commerciële Marketplace SaaS-producten vanuit integratie Sandbox-accounts. Als u een productie abonnement hebt, moet u de site van de uitgever bezoeken om het installatie proces te volt ooien. De facturering van het abonnement wordt pas gestart nadat de installatie is voltooid.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.

- Een integratie sandbox-partner account met een klant die beschikt over een actief abonnement voor producten van de commerciële Marketplace SaaS.

- Voor partners die gebruikmaken van partner Center .NET SDK, moet u SDK-versie 1.14.0 of hoger gebruiken om toegang te krijgen tot deze mogelijkheid.

## <a name="c"></a>C\#

Gebruik de volgende stappen om een abonnement te activeren voor producten voor commerciële Marketplace SaaS:

1. Maak een interface voor de beschik bare abonnements bewerkingen. U moet de klant identificeren en de abonnements-id van het proef abonnement opgeven.

   ```csharp
   var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
   ```

2. Activeer het abonnement met de bewerking **Activate** .

   ```csharp
   var subscriptionActivationResult = subscriptionOperations.Activate();
   ```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode     | Aanvraag-URI                                                                            |
|------------|----------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{Subscription-id}/Activate http/1.1 |

### <a name="uri-parameter"></a>URI-para meter

| Naam                   | Type     | Vereist | Beschrijving                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **klant-Tenant-id** | **guid** | J | De waarde is een Tenant-id voor de GUID-indeling (**klant-Tenant-id**), waarmee u een klant kunt opgeven. |
| **abonnement-id** | **guid** | J | De waarde is een abonnements-id met een GUID-indeling (**abonnements-id**) waarmee u een abonnement kunt opgeven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
POST https://api.partnercenter.microsoft.com/v1/customers/42b5f772-5c5c-4bce-b9d7-bdadeecca411/subscriptions/87363db7-39ab-dd25-d371-94340aaa2f97/activate HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

```

## <a name="rest-response"></a>REST-antwoord

Met deze methode worden de eigenschappen van de **abonnements-id** en de **status** geretourneerd.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 79
Content-Type: application/json
MS-CorrelationId: 1438ea3d-b515-45c7-9ec1-27ee0cc8e6bd
MS-RequestId: 655890ba-4d2b-4d09-a95f-4ea1348686a5

{
    "subscriptionId":"87363db7-39ab-dd25-d371-94340aaa2f97",
    "status":"Success"
}
```
