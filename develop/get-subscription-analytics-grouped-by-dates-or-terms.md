---
title: Abonnements analyse gegroepeerd op datum of voor waarden ophalen
description: Informatie over abonnements analyse weer geven gegroepeerd op datum of voor waarden.
ms.date: 06/27/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4a9946027fa89f5a93fff5eede86e36a6be5b721
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767278"
---
# <a name="get-subscription-analytics-grouped-by-dates-or-terms"></a>Abonnements analyse gegroepeerd op datum of voor waarden ophalen

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Informatie over abonnements analyse ophalen voor uw klanten, gegroepeerd op datum of voor waarden.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode | Aanvraag-URI |
|--------|-------------|
| **Toevoegen** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/Subscriptions? GroupBy = {groupby_queries} |

### <a name="uri-parameters"></a>URI-para meters

Gebruik de volgende vereiste para meters voor het identificeren van uw organisatie en het groeperen van de resultaten.

| Naam | Type | Vereist | Beschrijving |
|------|------|----------|-------------|
| groupby_queries | paren teken reeksen en datum/tijd | Yes | De voor waarden en datums waarop het resultaat moet worden gefilterd. |

### <a name="groupby-syntax"></a>De syntaxis GroupBy

De Group by-para meter moet zijn samengesteld als een reeks door komma's gescheiden, veld waarden.

Een niet-gecodeerd voor beeld ziet er als volgt uit:

```http
?groupby=termField1,dateField1,termField2
```

In de volgende tabel ziet u een lijst met de ondersteunde velden voor Group by.

| Veld | Type | Description |
|-------|------|-------------|
| customerTenantId | tekenreeks | Een teken reeks met een GUID-indeling die de Tenant van de klant identificeert. |
| customerName | tekenreeks | De naam van de klant. |
| customerMarket | tekenreeks | Het land/de regio waarin de klant zaken doet. |
| id | tekenreeks | Een teken reeks met een GUID-indeling waarmee het abonnement wordt geïdentificeerd. |
| status | tekenreeks | De abonnements status. Ondersteunde waarden zijn: ' Active ', ' Suspended ' of ' provisioned '. |
| Product | tekenreeks | De naam van het product. |
| subscriptionType | tekenreeks | Het type abonnement. Opmerking: dit veld is hoofdletter gevoelig. Ondersteunde waarden zijn: ' Office ', ' Azure ', ' Microsoft365 ', ' Dynamics ', ' EMS '. |
| autoRenewEnabled | Booleaans | Een waarde die aangeeft of het abonnement automatisch wordt vernieuwd. |
| Partner  | tekenreeks | De MPN-ID. Voor een rechtstreekse wederverkoper is deze para meter de MPN-ID van de partner. Voor een indirecte wederverkoper is deze para meter de MPN-ID van de indirecte wederverkoper. |
| friendlyName | tekenreeks | De naam van het abonnement. |
| partnerName | tekenreeks | De naam van de partner voor wie het abonnement is aangeschaft |
| providerName | tekenreeks | Wanneer abonnements transactie voor de indirecte wederverkoper is, is de naam van de provider de indirecte provider die het abonnement heeft gekocht.
| creationDate | teken reeks in UTC-datum tijd notatie | De datum waarop het abonnement is gemaakt. |
| effectiveStartDate | teken reeks in UTC-datum tijd notatie | De datum waarop het abonnement wordt gestart. |
| commitmentEndDate | teken reeks in UTC-datum tijd notatie | De datum waarop het abonnement eindigt. |
| currentStateEndDate | teken reeks in UTC-datum tijd notatie | De datum waarop de huidige status van het abonnement wordt gewijzigd. |
| trialToPaidConversionDate | teken reeks in UTC-datum tijd notatie | De datum waarop het abonnement wordt geconverteerd van een proef versie naar betaald. De standaardwaarde is null. |
| trialStartDate | teken reeks in UTC-datum tijd notatie | De datum waarop de proef periode voor het abonnement is gestart. De standaardwaarde is null. |
| lastUsageDate | teken reeks in UTC-datum tijd notatie | De datum waarop het abonnement voor het laatst is gebruikt. De standaardwaarde is null. |
| deprovisionedDate | teken reeks in UTC-datum tijd notatie | De datum waarop het abonnement is ongedaan gemaakt. De standaardwaarde is null. |
| lastRenewalDate | teken reeks in UTC-datum tijd notatie | De datum waarop het abonnement voor het laatst is vernieuwd. De standaardwaarde is null. |

### <a name="filter-fields"></a>Filter velden

De volgende tabel bevat de optionele filter velden en de bijbehorende beschrijvingen:

| Veld | Type |  Description |
|-------|------|--------------|
| top | int | Het aantal rijen met gegevens dat in de aanvraag moet worden geretourneerd. Als de waarde niet is opgegeven, zijn de maximum waarde en de standaard waarde 10000. Als er meer rijen in de query staan, bevat de antwoord tekst een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen. |
| skip | int | Het aantal rijen dat in de query moet worden overgeslagen. Gebruik deze para meter om door grote gegevens sets te bladeren. Bijvoorbeeld Top = 10000 en skip = 0 haalt de eerste 10000 rijen met gegevens op, Top = 10000 en skip = 10000 de volgende 10000 rijen met gegevens ophalen. |
| filter | tekenreeks | Een of meer instructies waarmee de rijen in het antwoord worden gefilterd. Elke filter instructie bevat een veld naam uit de hoofd tekst van het antwoord en een waarde die is gekoppeld aan de **`eq`** , **`ne`** , of voor bepaalde velden, de **`contains`** operator. Instructies kunnen worden gecombineerd met **`and`** of **`or`** . Teken reeks waarden moeten tussen enkele aanhalings tekens in de filter parameter worden geplaatst. Zie de volgende sectie voor een lijst met velden die kunnen worden gefilterd en de Opera tors die worden ondersteund door deze velden. |
| aggregationLevel | tekenreeks | Hiermee geeft u het tijds bereik op waarvoor u de samengevoegde gegevens wilt ophalen. Dit kan een van de volgende teken reeksen zijn: **dag**, **week** of **maand**. Als de waarde niet is opgegeven, is de standaard instelling **dateRange**. **Opmerking**: deze para meter is alleen van toepassing wanneer een datum veld wordt door gegeven als onderdeel van de para meter groupBy. |
| groupBy | tekenreeks | Een instructie die alleen gegevens aggregatie toepast op de opgegeven velden. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, bevat de antwoord tekst een verzameling [abonnements](partner-center-analytics-resources.md#subscription-resource) resources gegroepeerd op basis van de opgegeven voor waarden en datums.

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
