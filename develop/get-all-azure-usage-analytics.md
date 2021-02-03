---
title: Alle gebruiksanalysegegevens van Azure ophalen
description: Alle informatie over Azure Usage Analytics ophalen.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: khpavan
ms.author: sakhanda
ms.openlocfilehash: c281dcdeb93771a69a388ad64e1127b24156c809
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767408"
---
# <a name="get-all-azure-usage-analytics-information"></a>Alle gebruiksanalysegegevens van Azure ophalen

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Hoe u alle informatie over Azure Usage Analytics kunt verkrijgen voor uw klanten.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI |
|---------|-------------|
| **Toevoegen** | [*\{ BASEURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/Usage/Azure http/1.1 |

### <a name="uri-parameters"></a>URI-para meters

|Parameter        |Type                        |Description               |
|:----------------|:---------------------------|:-------------------------|
|top              | tekenreeks                     | Het aantal rijen met gegevens dat in de aanvraag moet worden geretourneerd. De maximum waarde en de standaard waarde als niet wordt opgegeven, zijn 10000. Als er meer rijen in de query staan, bevat de antwoord tekst een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen.                        |
|skip             | int                        | Het aantal rijen dat in de query moet worden overgeslagen. Gebruik deze para meter om door grote gegevens sets te bladeren. Zo `top=10000 and skip=0` haalt de eerste 10000 rijen met gegevens op, `top=10000 and skip=10000` haalt de volgende 10000 rijen met gegevens op, enzovoort.                       |
|filter           | tekenreeks                     | De *filter* parameter van de aanvraag bevat een of meer instructies waarmee de rijen in het antwoord worden gefilterd. Elke instructie bevat een veld en waarde die zijn gekoppeld aan de `eq` or `ne` -Opera tors en instructies kunnen worden gecombineerd met `and` of `or` . U kunt de volgende teken reeksen opgeven:<br/><br/>                                                       `customerTenantId`<br/> `customerName`<br/> `subscriptionId`<br/> `subscriptionName`<br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/>**Voorbeeld:**<br/> `.../usage/azure?filter=meterCategory eq 'Data Management'`<br/><br/> **Voorbeeld:**<br/>`.../usage/azure?filter=meterCategory eq 'Data Management' or (usageDate le cast('2018-01-01', Edm.DateTimeOffset) and usageDate le cast('2018-04-01', Edm.DateTimeOffset))`                        |
|aggregationLevel | tekenreeks                    | Hiermee geeft u het tijds bereik op waarvoor u de samengevoegde gegevens wilt ophalen. Dit kan een van de volgende teken reeksen zijn: `day` , `week` of `month` . Als u dit niet opgeeft, wordt de standaard waarde `day` .<br/><br/>                                              De `aggregationLevel` para meter wordt niet ondersteund zonder een `groupby` . De `aggregationLevel` para meter is van toepassing op alle datum velden in de `groupby` .                                                      |
|OrderBy          |tekenreeks                     | Een instructie waarmee de resultaat gegevens voor elke installatie worden gesorteerd. De syntaxis is `...&orderby=field [order],field [order],...`. De `field` para meter kan een van de volgende teken reeksen zijn:<br/><br/>                    `customerTenantId`<br/>`customerName`<br/>`subscriptionId`<br/>`subscriptionName`<br/>`usageDate`<br/>`resourceLocation`<br/>`meterCategory`<br/>`meterSubcategory`<br/>`meterUnit`<br/> `reservationOrderId` <br/> `reservationId`<br/> `consumptionMeterId` <br/> `serviceType` <br/><br/> De *volg orde* van de para meters is optioneel en kan worden `asc` `desc` opgegeven of om respectievelijk een oplopende of aflopende volg orde voor elk veld op te geven. De standaardwaarde is `asc`.<br/><br/>**Voorbeeld:**<br/> `...&orderby=meterCategory,meterUnit`                                                                                           |
|GroupBy          |tekenreeks                    | Een instructie die alleen gegevens aggregatie toepast op de opgegeven velden. U kunt de volgende velden opgeven:<br/><br/>                                                                                                                     `customerTenantId`<br/>`customerName`<br/> `subscriptionId` <br/> `subscriptionName` <br/> `usageDate` <br/> `resourceLocation` <br/> `meterCategory` <br/> `meterSubcategory` <br/> `meterUnit` <br/> `reservationOrderId` <br/> `reservationId` <br/> `consumptionMeterId` <br/> `serviceType` <br/><br/>De geretourneerde gegevens rijen bevatten de velden die zijn opgegeven in de `groupby`  para meter en de *hoeveelheid*.<br/><br/>De `groupby` para meter kan worden gebruikt met de `aggregationLevel` para meter.<br/><br/>**Voorbeeld:**<br/>`...&groupby=meterCategory,meterUnit` |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

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

Als dit lukt, bevat de antwoord tekst een verzameling [Azure-gebruiks](partner-center-analytics-resources.md#csp-program-azure-usage-analytics) resources.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

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
