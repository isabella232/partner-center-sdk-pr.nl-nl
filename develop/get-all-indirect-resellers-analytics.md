---
title: Alle analysegegevens van indirecte resellers ophalen
description: Informatie over het verkrijgen van alle analysegegevens voor indirecte resellers.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 7a38fbf2c94bad5213a65159759ace54b9dd4595d5532ea97f2449f0ac5b41cd
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994061"
---
# <a name="get-all-indirect-resellers-analytics-information"></a>Alle analysegegevens van indirecte resellers ophalen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Informatie over het verkrijgen van alle analysegegevens voor indirecte resellers voor uw klanten.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) In dit scenario wordt verificatie alleen ondersteund met gebruikersreferenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI |
|---------|-------------|
| **Toevoegen** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/indirectresellers HTTP/1.1 |

### <a name="uri-parameters"></a>URI-parameters

| Parameter                             | Type     | Description                              |
|:--------------------------------------|:---------|:-----------------------------------------|
| partnerTenantId                       | tekenreeks   | De tenant-id van de partner waarvoor u gegevens van indirecte resellers wilt ophalen. |
| id                                    | tekenreeks   | Indirecte reseller-id                                                                 |
| naam                                  | tekenreeks   | De naam van de partner waarvoor u gegevens van indirecte resellers wilt ophalen.      |
| markt                                | tekenreeks   | De markt van de partner waarvoor u gegevens van indirecte resellers wilt ophalen.    |
| firstSubscriptionCreationDate         | tekenreeks in UTC-datum/tijd-indeling  | De aanmaakdatum van het eerste abonnement op basis waarvan u gegevens van indirecte resellers wilt ophalen.  |
| latestSubscriptionCreationDate        | tekenreeks in UTC-datum/tijd-indeling  | De aanmaakdatum van het meest recente abonnement.                 |
| firstSubscriptionEndDate              | tekenreeks in UTC-datum/tijd-indeling  | De eerste keer dat een abonnement is beëindigd.                        |
| latestSubscriptionEndDate             | tekenreeks in UTC-datum/tijd-indeling  | De laatste datum waarop een abonnement is beëindigd.                  |
| firstSubscriptionSuspendedDate        | tekenreeks in UTC-datum/tijd         | De eerste keer dat een abonnement is opgeschort.                    |
| latestSubscriptionSuspendedDate       | tekenreeks in UTC-datum/tijd-indeling  | De laatste datum waarop een abonnement is opgeschort.              |
| firstSubscriptionDeprovisionedDate    | tekenreeks in UTC-datum/tijd-indeling  | De eerste keer dat deprovisioning van een abonnement is verwijderd.                |
| latestSubscriptionDeprovisionedDate   | tekenreeks in UTC-datum/tijd-indeling  | De laatste datum waarop een abonnement is verwijderd.          |
| subscriptionCount                     | double   | Aantal abonnementen voor alle toegevoegde waarde resellers                                     |
| licenseCount                          | double   | Aantal licenties voor alle toegevoegde waarde resellers.                                         |
| indirectResellerCount                 | double   | Aantal indirecte resellers                                                             |
|  top                                  | tekenreeks   | Het aantal rijen met gegevens dat in de aanvraag moet worden retourneren. De maximumwaarde en de standaardwaarde als deze niet is opgegeven, is 10000. Als er meer rijen in de query staan, bevat de antwoord-body een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.  |
| skip                                  | int      | Het aantal rijen dat moet worden overgeslagen in de query. Gebruik deze parameter om door grote gegevenssets te gaan. Haalt bijvoorbeeld de eerste 10000 rijen met gegevens op, haalt de volgende **`top=10000 and skip=0`** 10000 rijen met gegevens **`top=10000 and skip=10000`** op, en meer.              |
| filter                                | tekenreeks   | De *filterparameter* van de aanvraag bevat een of meer instructies die de rijen in het antwoord filteren. Elke instructie bevat een veld en waarde die zijn gekoppeld aan de operators of en instructies **`eq`** kunnen worden gecombineerd met behulp van of **`ne`** **`and`** **`or`** . U kunt de volgende velden opgeven:<br/><br/>     *partnerTenantId*<br/> *id*<br/> *Naam*<br/>                *markt*<br/> *firstSubscriptionCreationDate*<br/> *latestSubscriptionCreationDate*<br/>                *firstSubscriptionEndDate*<br/>                *latestSubscriptionEndDate*<br/>                *firstSubscriptionSuspendedDate*<br/>                *latestSubscriptionSuspendedDate*<br/>                *firstSubscriptionDeprovisionedDate*<br/>                *latestSubscriptionDeprovisionedDate*<br/><br/>         **Voorbeeld:**<br/>              `.../indirectresellers?filter=market eq 'US'`<br/><br/>            **Voorbeeld:**<br/>                `.../indirectresellers?filter=market eq 'US' or (firstSubscriptionCreationDate le cast('2018-01-01',Edm.DateTimeOffset) and firstSubscriptionCreationDate le cast('2018-04-01',Edm.DateTimeOffset))` |              
| aggregationLevel                     | tekenreeks    | Hiermee geeft u het tijdsbereik op waarvoor geaggregeerde gegevens moeten worden opgehaald. Kan een van de volgende tekenreeksen zijn: &quot; &quot; dag, &quot; week of &quot; &quot; &quot; maand. Als dit niet is gespecificeerd, is de &quot; standaardwaarde dag &quot; .<br/><br/>                                 `aggregationLevel` wordt niet ondersteund zonder `aggregationLevel` een . `aggregationLevel` is van toepassing **op alle datumvelden die** aanwezig zijn in de `aggregationLevel`                         |
| Orderby                              | tekenreeks    | Een instructie die de resultaatgegevenswaarden voor elke installatie bestelt. De syntaxis is `...&orderby=field[order],field [order],...`. De veldparameter kan een van de volgende tekenreeksen zijn:<br/><br/>                &quot;partnerTenantId&quot;<br/>                &quot;id&quot;<br/>                &quot;Naam&quot;<br/>                &quot;markt&quot;<br/>                &quot;firstSubscriptionCreationDate&quot;<br/>               &quot;latestSubscriptionCreationDate&quot;<br/>                &quot;firstSubscriptionEndDate&quot;<br/>               &quot;latestSubscriptionEndDate&quot;<br/>                &quot;firstSubscriptionSuspendedDate&quot;<br/>                &quot;latestSubscriptionSuspendedDate&quot;<br/>               &quot;firstSubscriptionDeprovisionedDate&quot;<br/>                &quot;latestSubscriptionDeprovisionedDate&quot;<br/>                &quot;subscriptionCount&quot;<br/>                &quot;licenseCount&quot;<br/><br/>   De *orderparameter* is optioneel en kan of zijn om de oplopende of aflopende `asc` volgorde voor elk veld op te `desc` geven. De standaardwaarde is `asc`.<br/><br/>    **Voorbeeld:**<br/>                `...&orderby=market,subscriptionCount`                                       |                   
| groupby                              | tekenreeks    | Een instructie die gegevensaggregatie alleen op de opgegeven velden van toepassing is. U kunt de volgende velden opgeven:<br/><br/>         *partnerTenantId*<br/>    *id*<br/>               *Naam*<br/>                *markt*<br/>                *firstSubscriptionCreationDate*<br/>                *latestSubscriptionCreationDate*<br/>                *firstSubscriptionEndDate*<br/>                *latestSubscriptionEndDate*<br/>                *firstSubscriptionSuspendedDate*<br/>                *latestSubscriptionSuspendedDate*<br/>                *firstSubscriptionDeprovisionedDate*<br/>                *latestSubscriptionDeprovisionedDate*<br/><br/>                 De geretourneerde gegevensrijen bevatten de velden die zijn opgegeven in de `groupby` -component en de volgende velden:<br/><br/>            *indirectResellerCount*<br/>                *licenseCount*<br/>                *subscriptionCount*<br/><br/>            De `groupby` parameter kan worden gebruikt met de parameter `aggregationLevel` .<br/><br/>            **Voorbeeld:**</br>               `...&groupby=ageGroup,market&aggregationLevel=week`                         |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

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

Als dit lukt, bevat de antwoord-body een verzameling [indirecte resellersresources.](partner-center-analytics-resources.md#csp-program-indirect-resellers-analytics)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

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
