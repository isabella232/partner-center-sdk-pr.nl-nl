---
title: Abonnements analyse ophalen via zoek query
description: Abonnements analyserapporten filteren op basis van een zoek query.
ms.date: 05/10/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c1046ea3c7e813eedae4890eebf6356337c80ede
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767279"
---
# <a name="get-subscription-analytics-information-filtered-by-a-search-query"></a>Analysegegevens van abonnementen die is gefilterd met een zoekquery ophalen

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Informatie over abonnements analyse ophalen voor uw klanten, gefilterd op een zoek query.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode | Aanvraag-URI |
|--------|-------------|
| **Toevoegen** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/Subscriptions? filter = {filter_string} |

### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende vereiste para meter voor het identificeren van uw organisatie en het filteren van de zoek opdracht.

| Naam | Type | Vereist | Beschrijving |
|------|------|----------|-------------|
| filter_string | tekenreeks | Yes | Het filter dat moet worden toegepast op de abonnements analyse. Zie de secties filter syntaxis en filter Fields voor de syntaxis, velden en Opera tors voor gebruik in deze para meter. |

### <a name="filter-syntax"></a>Filter syntaxis

De filter parameter moet worden samengesteld als een reeks combi Naties van velden, waarden en operators. Meerdere combi Naties kunnen worden gecombineerd met **`and`** of- **`or`** Opera tors.

Een niet-gecodeerd voor beeld ziet er als volgt uit:

- Tekenreeksexpressie `?filter=Field operator 'Value'`
- True `?filter=Field operator Value`
- Daarin `?filter=contains(field,'value')`

### <a name="filter-fields"></a>Filter velden

De filter parameter van de aanvraag bevat een of meer instructies waarmee de rijen in het antwoord worden gefilterd. Elke instructie bevat een veld en waarde die zijn gekoppeld aan de **`eq`** or- **`ne`** Opera tors. Sommige velden bieden ook ondersteuning voor de **`contains`** **`gt`** **`lt`** Opera Tors,,, **`ge`** en **`le`** . Instructies kunnen worden gecombineerd met behulp van **`and`** or- **`or`** Opera tors.

Hier volgen enkele voor beelden van filter reeksen:

```http
autoRenewEnabled eq true

autoRenewEnabled eq true and customerMarket eq 'US'
```

De volgende tabel bevat een lijst met de ondersteunde velden en ondersteunings operatoren voor de filter parameter. Teken reeks waarden moeten tussen enkele aanhalings tekens worden geplaatst.

| Parameter | Ondersteunde Opera tors | Description |
|-----------|---------------------|-------------|
| autoRenewEnabled | `eq`, `ne` | Een waarde die aangeeft of het abonnement automatisch wordt vernieuwd. |
| commitmentEndDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | De datum waarop het abonnement eindigt. |
| creationDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | De datum waarop het abonnement is gemaakt. |
| currentStateEndDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop de huidige status van het abonnement wordt gewijzigd. |
| customerMarket | `eq`, `ne` | Het land/de regio waarin de klant zaken doet. |
| customerName | `contains` | De naam van de klant. |
| customerTenantId | `eq`, `ne` | Een teken reeks met een GUID-indeling die de Tenant van de klant identificeert. |
| deprovisionedDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop het abonnement is ongedaan gemaakt. De standaardwaarde is null. |
| effectiveStartDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop het abonnement wordt gestart. |
| friendlyName | `contains` | De naam van het abonnement. |
| id | `eq`, `ne` | Een teken reeks met een GUID-indeling waarmee het abonnement wordt geïdentificeerd. |
| lastRenewalDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop het abonnement voor het laatst is vernieuwd. De standaardwaarde is null. |
| lastUsageDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop het abonnement voor het laatst is gebruikt. De standaardwaarde is null. |
| Partner | `eq`, `ne` | De MPN-ID. Voor een rechtstreekse wederverkoper is deze waarde de MPN-ID van de partner. Voor een indirecte wederverkoper is deze waarde de MPN-ID van de indirecte wederverkoper. |
| partnerName | tekenreeks | De naam van de partner voor wie het abonnement is aangeschaft |
| Product | `contains`, `eq`, `ne` | De naam van het product. |
| providerName | tekenreeks | Wanneer abonnements transactie voor de indirecte wederverkoper is, is de naam van de provider de indirecte provider die het abonnement heeft gekocht.|
| status | `eq`, `ne` | De abonnements status. Ondersteunde waarden zijn: ' Active ', ' Suspended ' of ' provisioned '. |
| subscriptionType | `eq`, `ne` | Het type abonnement. **Opmerking**: dit veld is hoofdletter gevoelig. Ondersteunde waarden zijn: ' Office ', ' Azure ', ' Microsoft365 ', ' Dynamics ', ' EMS '. |
| trialStartDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le` | De datum waarop de proef periode voor het abonnement is gestart. De standaardwaarde is null. |
| trialToPaidConversionDate | `eq`, `ne`, `gt`, `lt`, `ge`, `le`  | De datum waarop het abonnement wordt geconverteerd van een proef versie naar betaald. De standaardwaarde is null. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, bevat de antwoord tekst een verzameling [abonnements](partner-center-analytics-resources.md#subscription-resource) resources die voldoen aan de filter criteria.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

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
