---
title: Een sandbox-abonnement activeren voor commerciële marketplace-producten
description: Meer informatie over het gebruik van C/# en Partner Center REST API's om een sandbox-abonnement te activeren voor commerciële marketplace-producten.
ms.date: 09/10/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b32c3e87462f58218771fc5da7da56ed177489cb
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025697"
---
# <a name="activate-a-sandbox-subscription-for-commercial-marketplace-saas-products-to-enable-billing"></a>Een sandbox-abonnement activeren voor SaaS-producten op de commerciële marketplace om facturering mogelijk te maken

Een abonnement activeren voor SaaS-producten (Software as a Service) op de commerciële marketplace vanuit sandbox-accounts voor integratie om facturering mogelijk te maken.

> [!NOTE]
> Het is alleen mogelijk om een abonnement voor SaaS-producten op de commerciële marketplace te activeren vanuit sandbox-accounts voor integratie. Als u een productieabonnement hebt, moet u naar de site van de uitgever gaan om het installatieproces te voltooien. Abonnementsfacturering begint pas nadat de installatie is voltooid.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een sandbox-partneraccount voor integratie met een klant met een actief abonnement voor SaaS-producten op de commerciële marketplace.

- Voor partners die Partner Center .NET SDK gebruiken, moet u SDK versie 1.14.0 of hoger gebruiken om toegang te krijgen tot deze mogelijkheid.

## <a name="c"></a>C\#

Gebruik de volgende stappen om een abonnement te activeren voor SaaS-producten op de commerciële marketplace:

1. Maak een interface voor de abonnementsbewerkingen beschikbaar. U moet de klant identificeren en de abonnements-id van het proefabonnement opgeven.

   ```csharp
   var subscriptionOperations = partnerOperations.Customers.ById(customerId).Subscriptions.ById(subscriptionId);
   ```

2. Activeer het abonnement met behulp van **de bewerking Activate.**

   ```csharp
   var subscriptionActivationResult = subscriptionOperations.Activate();
   ```

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode     | Aanvraag-URI                                                                            |
|------------|----------------------------------------------------------------------------------------|
| **Verzenden** | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/activate HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

| Naam                   | Type     | Vereist | Beschrijving                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| **customer-tenant-id** | **guid** | J | De waarde is een tenant-id in GUID-indeling **(customer-tenant-id),** waarmee u een klant kunt opgeven. |
| **subscription-id** | **guid** | J | De waarde is een abonnements-id met **GUID-indeling (abonnements-id),** waarmee u een abonnement kunt opgeven. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

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

Deze methode retourneert de **eigenschappen subscription-id** **en status.**

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

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
