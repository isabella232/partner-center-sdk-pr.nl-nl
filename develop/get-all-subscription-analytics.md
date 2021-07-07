---
title: Alle analysegegevens van abonnementen ophalen
description: Informatie over het verkrijgen van alle analysegegevens van het abonnement.
ms.date: 08/02/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: e1f16c92569a02bc51c96a85ecb642fbeb76a9a7
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760246"
---
# <a name="get-all-subscription-analytics-information"></a>Alle analysegegevens van abonnementen ophalen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

In dit artikel wordt beschreven hoe u alle analysegegevens voor abonnementen voor uw klanten op kunt halen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI |
|--------|-------------|
| **Toevoegen** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions HTTP/1.1 |

#### <a name="uri-parameters"></a>URI-parameters

De volgende tabel bevat optionele parameters en de bijbehorende beschrijvingen:

| Parameter | Type |  Beschrijving |
|-----------|------|--------------|
| top | int | Het aantal rijen met gegevens dat in de aanvraag moet worden retourneren. Als de waarde niet is opgegeven, zijn de maximumwaarde en de standaardwaarde `10000` . Als er meer rijen in de query staan, bevat de hoofdpagina van het antwoord een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen. |
| skip | int | Het aantal rijen dat moet worden overgeslagen in de query. Gebruik deze parameter om grote gegevenssets te bekijken. En haalt bijvoorbeeld de eerste 10000 rijen met gegevens op en haalt de volgende `top=10000` `skip=0` `top=10000` `skip=10000` 10.000 rijen met gegevens op. |
| filter | tekenreeks | Een of meer instructies die de rijen in het antwoord filteren. Elke filter-instructie bevat een veldnaam uit de antwoord-body en een waarde die zijn gekoppeld aan de operator , of voor **`eq`** **`ne`** bepaalde **`contains`** velden. Instructies kunnen worden gecombineerd met **`and`** of **`or`** . Tekenreekswaarden moeten tussen enkele aanhalingstekens in de **filterparameter staan.** Zie de volgende sectie voor een lijst met velden die kunnen worden gefilterd en de operators die worden ondersteund met deze velden. |
| aggregationLevel | tekenreeks | Hiermee geeft u het tijdsbereik op waarvoor geaggregeerde gegevens moeten worden opgehaald. Kan een van de volgende tekenreeksen zijn: **dag,** **week** of **maand.** Als de waarde niet is opgegeven, is de **standaardwaarde dateRange.** Deze parameter is alleen van toepassing wanneer een datumveld wordt doorgegeven als onderdeel van de **groupBy-parameter.** |
| groupBy | tekenreeks | Een instructie die gegevensaggregatie alleen op de opgegeven velden van toepassing is. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body een verzameling [**abonnementsresources.**](partner-center-analytics-resources.md#subscription-resource)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
{
    "customerTenantId": "76906668-27FC-4F5B-A35C-75A9823E13AF",
    "customerName": "TESTORG65656565",
    "customerMarket": "US",
    "id": "4BF546B2-8998-4838-BEE2-5F1BBE65A04F",
    "status": "ACTIVE",
    "productName": "OFFICE 365 BUSINESS PREMIUM",
    "subscriptionType": "Office",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "FULL OFFICE SUITE",
    "partnerName": "Partner Name",
    "providerName": "Provider Name",
    "creationDate": "2016-02-04T19:29:38.037",
   "effectiveStartDate": "2016-02-04T00:00:00",
    "commitmentEndDate": "2019-02-10T00:00:00",
    "currentStateEndDate": "2019-02-10T00:00:00",
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": "2018-02-10T02:39:57.729",
    "licenseCount": 2,
    "churnRisk": "High",
    "billingCycleName": "MONTHLY"

}
```

## <a name="see-also"></a>Zie ook

- [Partnercentrum Analytics - Bronnen](partner-center-analytics-resources.md)
