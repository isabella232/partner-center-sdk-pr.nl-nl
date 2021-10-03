---
title: Krijgt de uitvalstatus voor een bepaalde klant
description: Krijgt de uitvalstatus voor een bepaalde klant.
ms.date: 10/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 8dabd811c61583a38f832eae54ce92402bfb5c29
ms.sourcegitcommit: 856c14b6b351697e3b3d33f1fe376adbb80517c5
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/02/2021
ms.locfileid: "129383439"
---
# <a name="get-overage"></a>Uitval

**Van toepassing op**

- Partnercentrum

**Juiste rollen**

- Globale beheerder
- Beheeragent

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van Microsoft 365/Dynamics 365 New Commerce Experience Technical Preview.

Wordt gebruikt om uitval voor een bepaalde klant op te halen. Uitval stelt een klant in staat om services te blijven gebruiken als deze de service buiten de opgegeven limieten gebruikt. Uitval definieert de uitval van het verbruiksabonnement met betalen per gebruik.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Eén abonnements-id voor het overge overgangsabonnement.

## <a name="rest-request"></a>REST-aanvraag
[GET] /customers/{customer-tenant-id}/subscriptions/age
### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **TOEVOEGEN**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/overage HTTP/1.1 |

### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameters om de uitval van een klant te retourneren.

| Naam                    | Type     | Vereist | Beschrijving                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **customer-tenant-id**  | **guid** | J        | Een GUID die overeenkomt met de tenant van de klant.             |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/overage HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode uitval voor een klant.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
    "totalCount": 1,
    "items": [
        {
            "azureEntitlementId": "ea1c26b7-8c99-42bb-ba7d-c535831fae8e",
            "partnerId": "1234",
            "type": "PhoneServices",
            "overageEnabled": true,
            "links": {
                "overage": {
                    "uri": "/customers/f62cf10b-8f76-4fc4-9774-c5291f8faf86/subscriptions/overage",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Overage"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
