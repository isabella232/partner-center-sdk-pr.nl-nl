---
title: Abonnementsanalyses groeperen op datums of voorwaarden
description: Informatie over abonnementsanalyses groeperen op datums of voorwaarden.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8192a9863d53ec8697a7341cd38c69200614bd4a
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548716"
---
# <a name="get-subscription-analytics-grouped-by-dates-or-terms"></a>Abonnementsanalyses groeperen op datums of voorwaarden

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Informatie over abonnementsanalyses voor uw klanten, gegroepeerd op datums of voorwaarden.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode | Aanvraag-URI |
|--------|-------------|
| **Toevoegen** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/subscriptions?groupby={groupby_queries} |

### <a name="uri-parameters"></a>URI-parameters

Gebruik de volgende vereiste padparameters om uw organisatie te identificeren en de resultaten te groeperen.

| Naam | Type | Vereist | Beschrijving |
|------|------|----------|-------------|
| groupby_queries | paren van tekenreeksen en datum/tijd | Ja | De voorwaarden en datums waarop het resultaat moet worden gefilterd. |

### <a name="groupby-syntax"></a>GroupBy-syntaxis

De groep op parameter moet bestaan uit een reeks door komma's gescheiden veldwaarden.

Een niet-gecodeerd voorbeeld ziet er als volgende uit:

```http
?groupby=termField1,dateField1,termField2
```

In de volgende tabel ziet u een lijst met de ondersteunde velden voor group by.

| Veld | Type | Beschrijving |
|-------|------|-------------|
| customerTenantId | tekenreeks | Een tekenreeks in GUID-indeling die de tenant van de klant identificeert. |
| customerName | tekenreeks | De naam van de klant. |
| customerMarket | tekenreeks | Het land/de regio waarin de klant zaken doet. |
| id | tekenreeks | Een tekenreeks in GUID-indeling die het abonnement identificeert. |
| status | tekenreeks | De abonnementsstatus. Ondersteunde waarden zijn: 'ACTIEF', 'SUSPENDED' of 'DEPROVISIONED'. |
| Productnaam | tekenreeks | De naam van het product. |
| subscriptionType | tekenreeks | Het abonnementstype. Opmerking: Dit veld is casegevoelig. Ondersteunde waarden zijn: 'Office', 'Azure', 'Microsoft365', 'Dynamics', 'EMS'. |
| autoRenewEnabled | Booleaans | Een waarde die aangeeft of het abonnement automatisch wordt verlengd. |
| partnerId  | tekenreeks | De MPN-id. Voor een directe reseller is deze parameter de MPN-id van de partner. Voor een indirecte reseller is deze parameter de MPN-id van de indirecte reseller. |
| Friendlyname | tekenreeks | De naam van het abonnement. |
| partnerName | tekenreeks | Naam van de partner voor wie het abonnement is gekocht |
| providerName | tekenreeks | Wanneer de abonnementstransactie voor de indirecte reseller is, is de providernaam de indirecte provider die het abonnement heeft gekocht.
| creationDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop het abonnement is gemaakt. |
| effectiveStartDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop het abonnement wordt gestart. |
| commitmentEndDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop het abonnement eindigt. |
| currentStateEndDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de huidige status van het abonnement wordt gewijzigd. |
| trialToPaidConversionDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop het abonnement wordt omgezet van proefversie naar betaald. De standaardwaarde is null. |
| trialStartDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de proefperiode voor het abonnement is gestart. De standaardwaarde is null. |
| lastUsageDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop het abonnement voor het laatst is gebruikt. De standaardwaarde is null. |
| deprovisionedDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop het abonnement is verwijderd. De standaardwaarde is null. |
| lastRenewalDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop het abonnement voor het laatst is vernieuwd. De standaardwaarde is null. |

### <a name="filter-fields"></a>Filtervelden

De volgende tabel bevat optionele filtervelden en de bijbehorende beschrijvingen:

| Veld | Type |  Beschrijving |
|-------|------|--------------|
| top | int | Het aantal rijen met gegevens dat in de aanvraag moet worden retourneren. Als de waarde niet is opgegeven, zijn de maximumwaarde en de standaardwaarde 10000. Als er meer rijen in de query staan, bevat de antwoord-body een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen. |
| skip | int | Het aantal rijen dat moet worden overgeslagen in de query. Gebruik deze parameter om door grote gegevenssets te gaan. Top=10000 en skip=0 haalt bijvoorbeeld de eerste 10000 rijen met gegevens op, top=10000 en skip=10000 haalt de volgende 10000 rijen met gegevens op. |
| filter | tekenreeks | Een of meer instructies die de rijen in het antwoord filteren. Elke filter-instructie bevat een veldnaam van de antwoord-body en een waarde die zijn gekoppeld aan de operator , of voor **`eq`** **`ne`** bepaalde **`contains`** velden. Instructies kunnen worden gecombineerd met **`and`** of **`or`** . Tekenreekswaarden moeten tussen enkele aanhalingstekens in de filterparameter staan. Zie de volgende sectie voor een lijst met velden die kunnen worden gefilterd en de operators die worden ondersteund met deze velden. |
| aggregationLevel | tekenreeks | Hiermee geeft u het tijdsbereik op waarvoor geaggregeerde gegevens moeten worden opgehaald. Kan een van de volgende tekenreeksen zijn: **dag,** **week** of **maand.** Als de waarde niet is opgegeven, is de **standaardwaarde dateRange.** **Opmerking:** deze parameter is alleen van toepassing wanneer een datumveld wordt doorgegeven als onderdeel van de parameter groupBy. |
| groupBy | tekenreeks | Een instructie die gegevensaggregatie alleen op de opgegeven velden van toepassing is. |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions?groupBy=subscriptionType
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105123
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body een verzameling [abonnementsresources](partner-center-analytics-resources.md#subscription-resource) gegroepeerd op de opgegeven voorwaarden en datums.

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 177
Content-Type: application/json; charset=utf-8
MS-CorrelationId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3123
MS-RequestId: ec8f62e5-1d92-47e9-8d5d-1924af105123
{
  "Value": [
    {
      "subscriptionType": "Azure",
      "subscriptionCount": "63",
      "licenseCount": "0"
    },
    {
      "subscriptionType": "Dynamics",
      "subscriptionCount": "62",
      "licenseCount": "405"
    },
    {
      "subscriptionType": "EMS",
      "subscriptionCount": "39",
      "licenseCount": "193"
    },
    {
      "subscriptionType": "M365",
      "subscriptionCount": "2",
      "licenseCount": "5"
    },
    {
      "subscriptionType": "Office",
      "subscriptionCount": "906",
      "licenseCount": "7485"
    },
    {
      "subscriptionType": "UNKNOWN",
      "subscriptionCount": "104",
      "licenseCount": "439"
    },
    {
      "subscriptionType": "Windows",
      "subscriptionCount": "2",
      "licenseCount": "2"
    }
  ],
  "@nextLink": null,
  "TotalCount": 7
}
```

## <a name="see-also"></a>Zie ook

[Partnercentrum Analytics - Bronnen](partner-center-analytics-resources.md)
