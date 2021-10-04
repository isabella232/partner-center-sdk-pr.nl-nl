---
title: Een nieuw commerce-abonnement overstappen
description: Hiermee wordt het nieuwe commerce-abonnement van een klant geupgraded naar een opgegeven doelabonnement.
ms.date: 02/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 97ecb104de68b6da0a0588d3b60671de756af5a2
ms.sourcegitcommit: 3ee00d9fe9da6b9df0fb7027ae506e2abe722770
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/04/2021
ms.locfileid: "129417216"
---
# <a name="transition-a-new-commerce-subscription"></a>Een nieuw commerce-abonnement overstappen

**Van toepassing op**: Partner Center

**Juiste rollen**

- Globale beheerder
- Beheeragent

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de technical preview van de nieuwe commerce-ervaring M365/D365.

Wordt gebruikt om het nieuwe commerce-abonnement van een klant te upgraden naar een doelabonnement. Als u een abonnement wilt overstappen, moeten er twee API-aanvragen worden gedaan. Haal **eerst in aanmerking komende overgangen op om** de SKU's op te halen die beschikbaar zijn voor de upgrade. Vervolgens **wordt POST-overgang** uitgevoerd om de overgang uit te voeren. Deze methoden ondersteunen zowel traditionele als nieuwe commerce-bronabonnementen.  

## <a name="get-transition-eligibilities"></a>Geschiktheid voor overgangen

Retourneert een lijst met in aanmerking komende overgangen voor een bepaalde klant, het abonnement en het aangevraagde type.

### <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze ops zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Eén abonnements-id voor het eerste abonnement.

### <a name="rest-request"></a>REST-aanvraag

#### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **TOEVOEGEN**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/transitionEligibilities?eligibilityType={immediate, scheduled} HTTP/1.1 |

#### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameters om in aanmerking komende overgangen te retourneren.

| Naam                    | Type     | Vereist | Beschrijving                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **customer-tenant-id**  | **guid** | J        | Een GUID die overeenkomt met de tenant van de klant.             |
| **subscription-id** | **guid** | J        | Een GUID die overeenkomt met het eerste abonnement. |
| **eligibilityType**       | **tekenreeks** | N        | Beschrijft wanneer de overgang moet worden uitgevoerd; kan direct of gepland zijn. De standaardinstelling is `Immediate`.  |

#### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

#### <a name="request-body"></a>Aanvraagbody

Geen

#### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/transitionEligibilities?eligibilityType=immediate HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US
```

### <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een lijst met de in aanmerking komende overgangen voor het opgegeven abonnement in de antwoord-body.

#### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

#### <a name="eligibility-errors"></a>Geschiktheidsfouten

Foutbeschrijvingen en betekenis.

| Foutbeschrijving | Betekenis  |
|-------------------------|----------|
|Abonnement kan niet worden overge transitioned: bronabonnement is niet actief. | Oorspronkelijke substatus niet actief |
|Abonnement kan niet worden overge transitioned: het bronabonnement is nog niet ingericht. | Oorspronkelijke sub FulfillmentState is niet geslaagd |
|Overgangstype is niet compatibel- AzureAD-abonnementstoewijzing is vereist. | LegacyCannotConvertSubscriptionId-fout bij het aanroepen van GetSubscriptionUpgradeConflicts |
|Overgangstype is niet compatibel: er bestaan conflicterende abonnementen voor licentieoverdracht. | Als een AAD-service abonnements-id's van een ander abonnement heeft, voegt u deze toe aan de conflictlijst (inclusief aankopen die zijn gedaan met een verouderde of moderne aankoopstroom) |

#### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
    "totalCount": 2,
    "items": [
        {
            "catalogItemId": "CFQ7TTC0KZCR:0001:CFQ7TTC0K71H",
            "title": "Microsoft 365 E5 Test Sku Title",
            "description": "Microsoft 365 E5 Test Sku Description",
            "quantity": 1,
            "eligibilities": [
{
                    "isEligible": true,
                    "transitionType": "transition_only",
                    "errors": []
                },
                
{
                    "isEligible": false,
                    "transitionType": "transition_with_license_transfer",
                    "errors": [
                        {
                            "code": 3,
                            "description": "Subscription cannot be transitioned because there are conflicting services."
                        }
                    ]
                }
            ],
            "attributes": {
                "objectType": "TransitionEligibility"
            }
        },
        {
            "catalogItemId": "CFQ7TTC0L4M3:0001:CFQ7TTC0K78T",
            "title": "Business Premium Test Sku Title",
            "description": "Business Premium Test Sku Description",
            "quantity": 1,
            "eligibilities": [
                {
                    "isEligible": false,
                    "transitionType": "transition_with_license_transfer",
                    "errors": [
                        {
                            "code": 3,
                            "description": "Subscription cannot be transitioned because there are conflicting services."
                        }
                    ]
                }
            ],
            "attributes": {
                "objectType": "TransitionEligibility"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```

## <a name="post-transition"></a>Na de overgang

Plaatst een overgangsaanvraag voor een bepaalde klant en een bepaald abonnement. Retourneert de overgang met de initiële status.

### <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.

- Een klant-id ( `customer-tenant-id` ). Als u de id van de klant niet weet, kunt u deze ops zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).

- Eén abonnements-id voor het eerste abonnement.

### <a name="rest-request"></a>REST-aanvraag

#### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode   | Aanvraag-URI                                                                                                                         |
|----------|-------------------------------------------------------------------------------------------------------------------------------------|
| **VERZENDEN**  | [*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{subscription-id}/transitions HTTP/1.1 |


#### <a name="uri-parameter"></a>URI-parameter

Gebruik de volgende queryparameters om een overgang uit te voeren.

| Naam                    | Type     | Vereist | Beschrijving                                       |
|-------------------------|----------|----------|---------------------------------------------------|
| **customer-tenant-id**  | **guid** | J        | Een GUID die overeenkomt met de tenant van de klant.             |
| **subscription-id** | **guid** | J        | Een GUID die overeenkomt met het eerste abonnement. |

#### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

#### <a name="request-body"></a>Aanvraagbody

Een volledige **overgangsresource** is vereist in de aanvraag body.

#### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customerId}/subscriptions/{subscriptionId}/transitions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
X-Locale: en-US

{
    "toCatalogItemId": "CFQ7TTC0KZ59:0001:CFQ7TTC0KZ59",
    "quantity": 5,
    "transitionType": "transition_with_license_transfer",
    "events": []
}
```

### <a name="rest-response"></a>REST-antwoord

Als dit lukt, retourneert deze methode een overgangsresource met de initiële status.

#### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

#### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 138
Content-Type: application/json
MS-CorrelationId: 81b08ffe-4cf8-49cd-82db-5c2fb0a8e132
MS-RequestId: 18752a69-1aa1-4ef7-8f9d-eb3681b2d70a
Date: Fri, 26 Feb 2021 20:42:26 GMT

{
    "FromCatalogItemId": "CFQ7TTC0LDPB:0001:CFQ7TTC0LGNT",
    "ToCatalogItemId": "CFQ7TTC0LF8S:0001:CFQ7TTC0K9G9",
    "quantity": 1,
    "transitionType": "transition_with_license_transfer",
    "Events": [
        {
            "name": "Conversion",
            "status": "Started ",
            "timestamp": "2021-01-08T18:01:14.7488618Z",
            "attributes":
            {
                "objectType": "TransitionEvent"
            }
        }
    ],
    "attributes":
    {
        "objectType": "Transition"
    }
}
```
