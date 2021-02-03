---
title: Alle analysegegevens van indirecte resellers ophalen
description: Hoe u alle gegevens van de indirecte reseller-analyse kunt ophalen.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 9f9c030278ba8fef9090f7be89064ac6054129ef
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767409"
---
# <a name="get-all-indirect-resellers-analytics-information"></a>Alle analysegegevens van indirecte resellers ophalen

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Hoe u alle informatie over indirecte wederverkopers voor uw klanten kunt ophalen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI |
|---------|-------------|
| **Toevoegen** | [*\{ BASEURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/indirectresellers http/1.1 |

### <a name="uri-parameters"></a>URI-para meters

| Parameter                             | Type     | Description                              |
|:--------------------------------------|:---------|:-----------------------------------------|
| partnerTenantId                       | tekenreeks   | De Tenant-ID van de partner waarvoor u gegevens van indirecte wederverkopers wilt ophalen. |
| id                                    | tekenreeks   | ID van de indirecte wederverkoper                                                                 |
| naam                                  | tekenreeks   | De naam van de partner waarvoor u gegevens van indirecte wederverkopers wilt ophalen.      |
| markt                                | tekenreeks   | De markt van de partner waarvoor u gegevens van indirecte wederverkopers wilt ophalen.    |
| firstSubscriptionCreationDate         | teken reeks in UTC-datum tijd notatie  | De aanmaak datum van het eerste abonnement op basis waarvan u de gegevens van indirecte wederverkopers wilt ophalen.  |
| latestSubscriptionCreationDate        | teken reeks in UTC-datum tijd notatie  | De aanmaak datum van het laatste abonnement.                 |
| firstSubscriptionEndDate              | teken reeks in UTC-datum tijd notatie  | De eerste keer dat een abonnement is beëindigd.                        |
| latestSubscriptionEndDate             | teken reeks in UTC-datum tijd notatie  | De laatste datum waarop een abonnement is beëindigd.                  |
| firstSubscriptionSuspendedDate        | teken reeks in UTC-datum tijd         | De eerste keer dat een abonnement is onderbroken.                    |
| latestSubscriptionSuspendedDate       | teken reeks in UTC-datum tijd notatie  | De laatste datum waarop een abonnement is onderbroken.              |
| firstSubscriptionDeprovisionedDate    | teken reeks in UTC-datum tijd notatie  | De inrichting van het abonnement is voor het eerst ongedaan gemaakt.                |
| latestSubscriptionDeprovisionedDate   | teken reeks in UTC-datum tijd notatie  | De laatste datum waarop een abonnement is ongedaan gemaakt.          |
| subscriptionCount                     | double   | Aantal abonnementen voor alle resellers met toegevoegde waarde                                     |
| licenseCount                          | double   | Aantal licenties voor alle resellers met toegevoegde waarde.                                         |
| indirectResellerCount                 | double   | Aantal indirecte wederverkopers                                                             |
|  top                                  | tekenreeks   | Het aantal rijen met gegevens dat in de aanvraag moet worden geretourneerd. De maximum waarde en de standaard waarde als niet wordt opgegeven, zijn 10000. Als er meer rijen in de query staan, bevat de antwoord tekst een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.  |
| skip                                  | int      | Het aantal rijen dat in de query moet worden overgeslagen. Gebruik deze para meter om door grote gegevens sets te bladeren. Zo **`top=10000 and skip=0`** haalt de eerste 10000 rijen met gegevens op, **`top=10000 and skip=10000`** haalt de volgende 10000 rijen met gegevens op, enzovoort.              |
| filter                                | tekenreeks   | De *filter* parameter van de aanvraag bevat een of meer instructies waarmee de rijen in het antwoord worden gefilterd. Elke instructie bevat een veld en waarde die zijn gekoppeld aan de **`eq`** or **`ne`** -Opera tors en instructies kunnen worden gecombineerd met **`and`** of **`or`** . U kunt de volgende velden opgeven:<br/><br/>     *partnerTenantId*<br/> *id*<br/> *Naam*<br/>                *markt*<br/> *firstSubscriptionCreationDate*<br/> *latestSubscriptionCreationDate*<br/>                *firstSubscriptionEndDate*<br/>                *latestSubscriptionEndDate*<br/>                *firstSubscriptionSuspendedDate*<br/>                *latestSubscriptionSuspendedDate*<br/>                *firstSubscriptionDeprovisionedDate*<br/>                *latestSubscriptionDeprovisionedDate*<br/><br/>         **Voorbeeld:**<br/>              `.../indirectresellers?filter=market eq 'US'`<br/><br/>            **Voorbeeld:**<br/>                `.../indirectresellers?filter=market eq 'US' or (firstSubscriptionCreationDate le cast('2018-01-01',Edm.DateTimeOffset) and firstSubscriptionCreationDate le cast('2018-04-01',Edm.DateTimeOffset))` |              
| aggregationLevel                     | tekenreeks    | Hiermee geeft u het tijds bereik op waarvoor u de samengevoegde gegevens wilt ophalen. Dit kan een van de volgende teken reeksen zijn: &quot; dag &quot; , &quot; week &quot; of &quot; maand &quot; . Als u geen waarde opgeeft, is de standaard &quot; dag &quot; .<br/><br/>                                 `aggregationLevel` wordt niet ondersteund zonder een `aggregationLevel` . `aggregationLevel` is van toepassing op alle **datefields** die aanwezig zijn in de `aggregationLevel`                         |
| OrderBy                              | tekenreeks    | Een instructie waarmee de resultaat gegevens voor elke installatie worden gesorteerd. De syntaxis is `...&orderby=field[order],field [order],...`. De para meter Field kan een van de volgende teken reeksen zijn:<br/><br/>                &quot;partnerTenantId&quot;<br/>                &quot;id&quot;<br/>                &quot;naam&quot;<br/>                &quot;markt&quot;<br/>                &quot;firstSubscriptionCreationDate&quot;<br/>               &quot;latestSubscriptionCreationDate&quot;<br/>                &quot;firstSubscriptionEndDate&quot;<br/>               &quot;latestSubscriptionEndDate&quot;<br/>                &quot;firstSubscriptionSuspendedDate&quot;<br/>                &quot;latestSubscriptionSuspendedDate&quot;<br/>               &quot;firstSubscriptionDeprovisionedDate&quot;<br/>                &quot;latestSubscriptionDeprovisionedDate&quot;<br/>                &quot;subscriptionCount&quot;<br/>                &quot;licenseCount&quot;<br/><br/>   De *volg orde* van de para meters is optioneel en kan `asc` of `desc` ; om een oplopende of aflopende volg orde voor elk veld op te geven. De standaardwaarde is `asc`.<br/><br/>    **Voorbeeld:**<br/>                `...&orderby=market,subscriptionCount`                                       |                   
| GroupBy                              | tekenreeks    | Een instructie die alleen gegevens aggregatie toepast op de opgegeven velden. U kunt de volgende velden opgeven:<br/><br/>         *partnerTenantId*<br/>    *id*<br/>               *Naam*<br/>                *markt*<br/>                *firstSubscriptionCreationDate*<br/>                *latestSubscriptionCreationDate*<br/>                *firstSubscriptionEndDate*<br/>                *latestSubscriptionEndDate*<br/>                *firstSubscriptionSuspendedDate*<br/>                *latestSubscriptionSuspendedDate*<br/>                *firstSubscriptionDeprovisionedDate*<br/>                *latestSubscriptionDeprovisionedDate*<br/><br/>                 De geretourneerde gegevens rijen bevatten de velden die zijn opgegeven in de `groupby` component en de volgende velden:<br/><br/>            *indirectResellerCount*<br/>                *licenseCount*<br/>                *subscriptionCount*<br/><br/>            De `groupby` para meter kan worden gebruikt met de `aggregationLevel` para meter.<br/><br/>            **Voorbeeld:**</br>               `...&groupby=ageGroup,market&aggregationLevel=week`                         |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/indirectresellers HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord tekst een verzameling [indirecte leveranciers](partner-center-analytics-resources.md#csp-program-indirect-resellers-analytics) resources.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
{
    "partnerTenantId": "AAAAAAAA-BBBB-CCCC-DDDD-EEEEEEEEEEEE",
    "id": "1111111",
    "name": "RESELLER NAME",
    "market": "US",
    "firstSubscriptionCreationDate": "2016-10-18T19:16:25.107",
    "latestSubscriptionCreationDate": "2016-10-18T19:16:25.107",
    "firstSubscriptionEndDate": "2018-11-07T00:00:00",
    "latestSubscriptionEndDate": "2018-11-07T00:00:00",
    "firstSubscriptionSuspendedDate": "0001-01-01T00:00:00",
    "latestSubscriptionSuspendedDate": "0001-01-01T00:00:00",
    "firstSubscriptionDeprovisionedDate": "0001-01-01T00:00:00",
    "latestSubscriptionDeprovisionedEndDate": "0001-01-01T00:00:00",
    "subscriptionCount": 10,
    "licenseCount": 20
}
```

## <a name="see-also"></a>Zie ook

- [Partnercentrum Analytics - Bronnen](partner-center-analytics-resources.md)
