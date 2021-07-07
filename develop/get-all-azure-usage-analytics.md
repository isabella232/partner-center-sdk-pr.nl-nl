---
title: Alle gebruiksanalysegegevens van Azure ophalen
description: Informatie over het verkrijgen van alle azure-gebruiksanalysegegevens.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: 7fe987c7dc50d55b26cd72d5aead52963eb1cfbe
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760212"
---
# <a name="get-all-azure-usage-analytics-information"></a>Alle gebruiksanalysegegevens van Azure ophalen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Informatie over het verkrijgen van alle Azure-gebruiksanalysegegevens voor uw klanten.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md) Dit scenario ondersteunt alleen verificatie met gebruikersreferenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI |
|---------|-------------|
| **Toevoegen** | [*\{ baseURL \}*](partner-center-rest-urls.md)/partner/v1/analytics/usage/azure HTTP/1.1 |

### <a name="uri-parameters"></a>URI-parameters

|Parameter        |Type                        |Beschrijving               |
|:----------------|:---------------------------|:-------------------------|
|top              | tekenreeks                     | Het aantal rijen met gegevens dat in de aanvraag moet worden retourneren. De maximumwaarde en de standaardwaarde als deze niet is opgegeven, is 10000. Als er meer rijen in de query staan, bevat de antwoord-body een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.                        |
|skip             | int                        | Het aantal rijen dat moet worden overgeslagen in de query. Gebruik deze parameter om door grote gegevenssets te gaan. Haalt bijvoorbeeld de eerste 10000 rijen met gegevens op, haalt de volgende `top=10000 and skip=0` 10000 rijen met gegevens `top=10000 and skip=10000` op, en meer.                       |
|filter           | tekenreeks                     | De *filterparameter* van de aanvraag bevat een of meer instructies die de rijen in het antwoord filteren. Elke instructie bevat een veld en waarde die zijn gekoppeld aan de operators of en instructies `eq` kunnen worden gecombineerd met behulp van of `ne` `and` `or` . U kunt de volgende tekenreeksen opgeven:<br/><br/>                                                       `customerTenantId`<br/> `customerName`<br/> `subscriptionId`<br/> `subscriptionName`<br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/>**Voorbeeld:**<br/> `.../usage/azure?filter=meterCategory eq 'Data Management'`<br/><br/> **Voorbeeld:**<br/>`.../usage/azure?filter=meterCategory eq 'Data Management' or (usageDate le cast('2018-01-01', Edm.DateTimeOffset) and usageDate le cast('2018-04-01', Edm.DateTimeOffset))`                        |
|aggregationLevel | tekenreeks                    | Hiermee geeft u het tijdsbereik op waarvoor geaggregeerde gegevens moeten worden opgehaald. Kan een van de volgende tekenreeksen zijn: `day` `week` , of `month` . Als dit niet is gespecificeerd, is de standaardwaarde `day` .<br/><br/>                                              De `aggregationLevel` parameter wordt niet ondersteund zonder een `groupby` . De `aggregationLevel` parameter is van toepassing op alle datumvelden die aanwezig zijn in de `groupby` .                                                      |
|Orderby          |tekenreeks                     | Een instructie die de resultaatgegevenswaarden voor elke installatie bestelt. De syntaxis is `...&orderby=field [order],field [order],...`. De `field` parameter kan een van de volgende tekenreeksen zijn:<br/><br/>                    `customerTenantId`<br/>`customerName`<br/>`subscriptionId`<br/>`subscriptionName`<br/>`usageDate`<br/>`resourceLocation`<br/>`meterCategory`<br/>`meterSubcategory`<br/>`meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/> De *orderparameter* is optioneel en kan of zijn om respectievelijk de oplopende of aflopende volgorde voor `asc` elk veld op te `desc` geven. De standaardwaarde is `asc`.<br/><br/>**Voorbeeld:**<br/> `...&orderby=meterCategory,meterUnit`                                                                                           |
|groupby          |tekenreeks                    | Een instructie die gegevensaggregatie alleen op de opgegeven velden van toepassing is. U kunt de volgende velden opgeven:<br/><br/>                                                                                                                     `customerTenantId`<br/>`customerName`<br/> `subscriptionId` <br/> `subscriptionName` <br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit` <br/> `reservationOrderId` <br/> `reservationId` <br/> `consumptionMeterId` <br/> `serviceType` <br/><br/>De geretourneerde gegevensrijen bevatten de velden die zijn opgegeven in de `groupby`  parameter en de *Hoeveelheid*.<br/><br/>De `groupby` parameter kan worden gebruikt met de parameter `aggregationLevel` .<br/><br/>**Voorbeeld:**<br/>`...&groupby=meterCategory,meterUnit` |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers [Partner Center meer informatie.](headers.md)

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/usage/azure HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body een verzameling [Azure-gebruiksresources.](partner-center-analytics-resources.md#csp-program-azure-usage-analytics)

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie Foutcodes voor de [volledige lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
{
  "customerTenantId": "39A1DFAC-4969-4F31-AF94-D76588189CFE",
  "customerName": "A",
  "subscriptionId": "EC649980-D623-49F5-B7C1-80CC772B83A8",
  "subscriptionName": "AZURE PURCHSE SAMPLE APP",
  "usageDate": "2018-05-27T00:00:00",
  "resourceLocation": "useast",
  "meterCategory": "Data Management",
  "meterSubcategory": "None",
  "meterUnit": "10,000s",
  "reservationOrderId": "",
  "reservationId": "",
  "consumptionMeterId": "",
  "serviceType": "",
  "quantity": 20
}
```

## <a name="see-also"></a>Zie ook

- [Partnercentrum Analytics - Bronnen](partner-center-analytics-resources.md)
