---
title: Implementatiegegevens van licenties ophalen
description: Implementatie-informatie over Office-en Dynamics-licenties ophalen.
ms.date: 10/25/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ef0e5d73d34bc51e4cc58143db6c9fc49cb58fcb
ms.sourcegitcommit: d53d300dc7fb01aeb4ef85bf2e3a6b80f868dc57
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/14/2020
ms.locfileid: "97767406"
---
# <a name="get-licenses-deployment-information"></a>Implementatiegegevens van licenties ophalen

**Van toepassing op**

- Partnercentrum

Implementatie-informatie over Office-en Dynamics-licenties ophalen.

## <a name="prerequisites"></a>Vereisten

Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario ondersteunt verificatie met app + gebruikers referenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode  | Aanvraag-URI                                                                                     |
|---------|-------------------------------------------------------------------------------------------------|
| **Toevoegen** | [*{baseURL}*](partner-center-rest-urls.md)/v1/Analytics/Commercial/Deployment/License/http/1.1 |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="uri-parameters"></a>URI-para meters

| Parameter         | Type     | Beschrijving | Vereist |
|-------------------|----------|-------------|----------|
| top               | tekenreeks   | Het aantal rijen met gegevens dat in de aanvraag moet worden geretourneerd. De maximum waarde en de standaard waarde als niet wordt opgegeven, zijn 10000. Als er meer rijen in de query staan, bevat de antwoord tekst een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen. | No |
| skip              | int      | Het aantal rijen dat in de query moet worden overgeslagen. Gebruik deze para meter om door grote gegevens sets te bladeren. Bijvoorbeeld Top = 10000 en skip = 0 haalt de eerste 10000 rijen met gegevens op, Top = 10000 en skip = 10000 de volgende 10000 rijen met gegevens ophalen, enzovoort. | No |
| filter            | tekenreeks   | De *filter* parameter van de aanvraag bevat een of meer instructies waarmee de rijen in het antwoord worden gefilterd. Elke instructie bevat een veld en waarde die zijn gekoppeld aan de `eq` or `ne` -Opera tors en instructies kunnen worden gecombineerd met `and` of `or` . Hier volgen enkele voor beelden van *filter* parameters:<br/><br/> *filter = serviceCode EQ ' O365 '*<br/> *filter = serviceCode EQ ' O365 '* of (*Channel EQ ' wederverkoper*')<br/><br/> U kunt de volgende velden opgeven:<br/><br/>**serviceCode**<br/>**serviceName**<br/>**kanalen**<br/>**customerTenantId**<br/>**customerName**<br/>**productId**<br/>**Product**  | No |
| GroupBy           | tekenreeks   | Een instructie die alleen gegevens aggregatie toepast op de opgegeven velden. U kunt de volgende velden opgeven:<br/><br/>**serviceCode**<br/>**serviceName**<br/>**kanalen**<br/>**customerTenantId**<br/>**customerName**<br/>**productId**<br/>**Product**<br/><br/> De geretourneerde gegevens rijen bevatten de velden die zijn opgegeven in de para meter *GroupBy* , evenals de volgende:<br/><br/>**licensesDeployed**<br/>**licensesSold**  | No |
| processedDateTime | DateTime | De ene kan de datum opgeven waarop de gebruiks gegevens zijn verwerkt. Wordt standaard ingesteld op de laatste datum waarop de gegevens zijn verwerkt | No |

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/commercial/deployment/license?filter=customerTenantId%20eq%20%270112A436-B14E-4888-967B-CA4BB2CF1234%27 HTTP 1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: bad5f75f-fd44-43ab-9325-bbc79dcba9da
MS-CorrelationId: 9cbdf63c-2608-4ad8-b0a9-abae27d859d9
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord tekst de volgende velden met gegevens over de geïmplementeerde licenties.

| Veld             | Type     | Description                           |
|-------------------|----------|---------------------------------------|
| serviceCode       | tekenreeks   | Service code                          |
| serviceName       | tekenreeks   | Servicenaam                          |
| kanalen           | tekenreeks   | Kanaal naam, wederverkoper                |
| customerTenantId  | tekenreeks   | De unieke id voor de klant    |
| customerName      | tekenreeks   | Klantnaam                         |
| productId         | tekenreeks   | De unieke id voor het product     |
| Product       | tekenreeks   | Productnaam                          |
| licensesDeployed  | long     | Aantal geïmplementeerde licenties           |
| licensesSold      | long     | Aantal verkochte licenties               |
| processedDateTime | DateTime | Datum waarop de gegevens voor het laatst zijn verwerkt |

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.

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
      "serviceCode": "crm",
      "serviceName": "Microsoft Dynamics",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "54B84594-9C77-4499-8D65-5E0D5F410E78",
      "productName": "DYNAMICS AX TASK",
      "licensesDeployed": 0,
      "licensesSold": 9
    },
    {
      "processedDateTime": "2018-10-14T00:00:00",
      "serviceCode": "o365",
      "serviceName": "Microsoft Office 365",
      "channel": "reseller",
      "customerTenantId": "0112A436-B14E-4888-967B-CA4BB2CF1234",
      "customerName": "TEST COMPANY",
      "productId": "D3B4FE1F-9992-4930-8ACB-CA6EC609365E",
      "productName": "DOMESTIC AND INTERNATIONAL CALLING PLAN",
      "licensesDeployed": 0,
      "licensesSold": 5
    }
],
  "@nextLink": null,
  "TotalCount": 2
}
```
