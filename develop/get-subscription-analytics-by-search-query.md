---
title: Abonnementsanalyses opvragen per zoekquery
description: Analytische gegevens van abonnementen filteren op een zoekquery.
ms.date: 05/10/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8df777b9a88206f8b22579f0f445c54d80f7cd64
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548733"
---
# <a name="get-subscription-analytics-information-filtered-by-a-search-query"></a>Analysegegevens van abonnementen die is gefilterd met een zoekquery ophalen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Informatie over abonnementsanalyses voor uw klanten filteren op basis van een zoekquery.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI |
|--------|-------------|
| **Toevoegen** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?filter={filter_string} |

### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende vereiste padparameter om uw organisatie te identificeren en de zoekopdracht te filteren.

| Naam | Type | Vereist | Beschrijving |
|------|------|----------|-------------|
| filter_string | tekenreeks | Ja | Het filter dat moet worden toegepast op de abonnementsanalyses. Zie de secties Filtersyntaxis en Filtervelden voor de syntaxis, velden en operators die u in deze parameter kunt gebruiken. |

### <a name="filter-syntax"></a>Filtersyntaxis

De filterparameter moet bestaan uit een reeks combinaties van velden, waarden en operatoren. Meerdere combinaties kunnen worden gecombineerd met - **`and`** of **`or`** -operators.

Een niet-gecodeerd voorbeeld ziet er als volgende uit:

- Tekenreeks: `?filter=Field operator 'Value'`
- Booleaanse: `?filter=Field operator Value`
- Bevat `?filter=contains(field,'value')`

### <a name="filter-fields"></a>Filtervelden

De filterparameter van de aanvraag bevat een of meer instructies die de rijen in het antwoord filteren. Elke instructie bevat een veld en waarde die zijn gekoppeld aan de **`eq`** operators of **`ne`** . Sommige velden ondersteunen ook de **`contains`** operators , , , en **`gt`** **`lt`** **`ge`** **`le`** . Instructies kunnen worden gecombineerd met behulp van **`and`** - of **`or`** -operators.

Hier volgen enkele voorbeelden van filterreeksen:

```http
autoRenewEnabled eq true

autoRenewEnabled eq true and customerMarket eq 'US'
```

In de volgende tabel ziet u een lijst met de ondersteunde velden en ondersteuningsoperators voor de filterparameter. Tekenreekswaarden moeten tussen enkele aanhalingstekens staan.

| Parameter | Ondersteunde operators | Beschrijving |
|-----------|---------------------|-------------|
| autoRenewEnabled | `eq`, `ne` | Een waarde die aangeeft of het abonnement automatisch wordt verlengd. |
| commitmentEndDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | De datum waarop het abonnement eindigt. |
| creationDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | De datum waarop het abonnement is gemaakt. |
| currentStateEndDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop de huidige status van het abonnement wordt gewijzigd. |
| customerMarket | `eq`, `ne` | Het land/de regio waarin de klant zaken doet. |
| customerName | `contains` | De naam van de klant. |
| customerTenantId | `eq`, `ne` | Een tekenreeks in GUID-indeling die de tenant van de klant identificeert. |
| deprovisionedDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop het abonnement is uitprovisioned. De standaardwaarde is null. |
| effectiveStartDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop het abonnement wordt gestart. |
| Friendlyname | `contains` | De naam van het abonnement. |
| id | `eq`, `ne` | Een tekenreeks in GUID-indeling die het abonnement identificeert. |
| lastRenewalDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop het abonnement voor het laatst is vernieuwd. De standaardwaarde is null. |
| lastUsageDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop het abonnement voor het laatst is gebruikt. De standaardwaarde is null. |
| partnerId | `eq`, `ne` | De MPN-id. Voor een directe reseller is deze waarde de MPN-id van de partner. Voor een indirecte reseller is deze waarde de MPN-id van de indirecte reseller. |
| partnerName | tekenreeks | Naam van de partner voor wie het abonnement is gekocht |
| Productnaam | `contains`, `eq`, `ne` | De naam van het product. |
| providerName | tekenreeks | Wanneer de abonnementstransactie voor de indirecte reseller is, is de providernaam de indirecte provider die het abonnement heeft gekocht.|
| status | `eq`, `ne` | De abonnementsstatus. Ondersteunde waarden zijn: 'ACTIEF', 'SUSPENDED' of 'DEPROVISIONED'. |
| subscriptionType | `eq`, `ne` | Het abonnementstype. **Opmerking:** dit veld is casegevoelig. Ondersteunde waarden zijn: 'Office', 'Azure', 'Microsoft365', 'Dynamics', 'EMS'. |
| trialStartDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop de proefperiode voor het abonnement is gestart. De standaardwaarde is null. |
| trialToPaidConversionDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | De datum waarop het abonnement wordt omgezet van proefversie naar betaald. De standaardwaarde is null. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?filter=autoRenewEnabled eq true
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body een verzameling [abonnementsresources](partner-center-analytics-resources.md#subscription-resource) die voldoen aan de filtercriteria.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123

{
    "customerTenantId": "735920EB-A564-4C72-9FE5-52632562712C",
    "customerName": "SURFACE TEST2",
    "customerMarket": "US",
    "id": "B76412DA-D382-4688-A6A4-711A207C1C2E",
    "status": "ACTIVE",
    "productName": "UNKNOWN",
    "subscriptionType": "Azure",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "MICROSOFT AZURE",
    "creationDate": "2017-06-02T23:11:58.747",
    "effectiveStartDate": "2017-06-02T00:00:00",
    "commitmentEndDate": null,
    "currentStateEndDate": null,
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": null,
    "licenseCount": 0
}
```

## <a name="see-also"></a>Zie ook

- [Partnercentrum Analytics - Bronnen](partner-center-analytics-resources.md)
