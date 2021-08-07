---
title: Gebruiksgegevens van licenties ophalen
description: Informatie over het gebruik van licenties op workloadniveau voor Office en Dynamics.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a93c59c8c2a4c82ad7f3e81e814386e1ac0c046c3b0bada80eaaac40d9179d93
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115990423"
---
# <a name="get-licenses-usage-information"></a>Gebruiksgegevens van licenties ophalen

Informatie over het gebruik van licenties op workloadniveau voor Office en Dynamics.

## <a name="prerequisites"></a>Vereisten

Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met app- en gebruikersreferenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Aanvraagsyntaxis

| Methode  | Aanvraag-URI                                                                                |
|---------|--------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/analytics/commercial/usage/license/ HTTP/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie REST-headers Partner Center [meer informatie.](headers.md)

### <a name="uri-parameters"></a>URI-parameters

| Parameter         | Type     | Beschrijving | Vereist |
|-------------------|----------|-------------|----------|
| top               | tekenreeks   | Het aantal rijen met gegevens dat in de aanvraag moet worden retourneren. De maximumwaarde en de standaardwaarde als deze niet is opgegeven, is 10.000. Als er meer rijen in de query staan, bevat de hoofdpagina van het antwoord een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen. | No |
| skip              | int      | Het aantal rijen dat moet worden overgeslagen in de query. Gebruik deze parameter om grote gegevenssets te bekijken. Top=10000 en skip=0 haalt bijvoorbeeld de eerste 10000 rijen met gegevens op, top=10000 en skip=10000 haalt de volgende 10000 rijen met gegevens op, bijvoorbeeld. | No |
| filter            | tekenreeks   | De *filterparameter* van de aanvraag bevat een of meer instructies die de rijen in het antwoord filteren. Elke instructie bevat een veld en waarde die zijn gekoppeld aan de operators of en instructies **`eq`** kunnen worden gecombineerd met of **`ne`** **`and`** **`or`** . Hier volgen enkele *voorbeeldfilterparameters:*<br/><br/>*filter=workloadCode eq 'SFB'*<br/><br/>*filter=workloadCode eq 'SFB'* of (*kanaal eq 'Reseller'*)<br/><br/>U kunt de volgende velden opgeven:<br/><br/>**workloadCode**<br/>**workloadName**<br/>**serviceCode**<br/>**Servicenaam**<br/>**Kanaal**<br/>**customerTenantId**<br/>**customerName**<br/>**Productid**<br/>**Productnaam** | No |
| groupby           | tekenreeks   | Een instructie die gegevensaggregatie alleen op de opgegeven velden van toepassing is. U kunt de volgende velden opgeven:<br/><br/>**workloadCode**<br/>**workloadName**<br/>**serviceCode**<br/>**Servicenaam**<br/>**channelcustomerTenantId**<br/>**customerName**<br/>**Productid**<br/>**Productnaam**<br/><br/>De geretourneerde gegevensrijen bevatten de velden die zijn opgegeven in de parameter *groupby* en het volgende:<br/><br/>**licensesActive**<br/>**licensesQualified** | No |
| processedDateTime | DateTime | U kunt de datum opgeven vanaf welke gebruiksgegevens zijn verwerkt. De standaardwaarde is de laatste datum waarop de gegevens zijn verwerkt | No |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/usage/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord-body de volgende velden met gegevens over het gebruik van licenties.

| Veld             | Type     | Description                                   |
|-------------------|----------|-----------------------------------------------|
| workloadCode      | tekenreeks   | Workloadcode                                 |
| workloadName      | tekenreeks   | Workloadnaam                                 |
| serviceCode       | tekenreeks   | Servicecode                                  |
| Servicenaam       | tekenreeks   | Servicenaam                                  |
| Kanaal           | tekenreeks   | Kanaalnaam, reseller                        |
| customerTenantId  | tekenreeks   | Unieke id voor de klant            |
| customerName      | tekenreeks   | Klantnaam                                 |
| productId         | tekenreeks   | Unieke id voor het product             |
| Productnaam       | tekenreeks   | Productnaam                                  |
| licensesActive    | long     | Aantal actieve licenties per workload        |
| licensesQualified | long     | Aantal gekwalificeerde licenties voor de workload |
| processedDateTime | DateTime | De datum waarop de gegevens voor het laatst zijn verwerkt         |

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)

### <a name="response-example"></a>Voorbeeld van antwoord

```http
HTTP/1.1 200 OK
Content-Length: 487
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CV: f0trvmq8mEScHcFS.0
MS-ServerId: 4
Date: Wed, 24 Oct 2018 22:37:18 GMT

{
"Value": [
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "workloadCode": "SPO",
      "workloadName": "SharePoint",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "6FD2C87F-B296-42F0-B197-1E91E994B900",
      "productName": "OFFICE 365 ENTERPRISE E3",
      "licenseActive": 0,
      "licensesQualified": 1
    },
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "workloadCode": "EXO",
      "workloadName": "Exchange",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "45A2423B-E884-448D-A831-D9E139C52D2F",
      "productName": "EXCHANGE ONLINE PROTECTION",
      "licenseActive": 0,
      "licensesQualified": 1
    }
}
```
