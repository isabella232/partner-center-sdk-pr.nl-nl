---
title: Alle analysegegevens van abonnementen ophalen
description: Hoe u de analyse gegevens van het abonnement ophaalt.
ms.date: 08/02/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: f32fb99ad52939ae8e9de26276588d3022f18fbc
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767179"
---
# <a name="get-all-subscription-analytics-information"></a>Alle analysegegevens van abonnementen ophalen

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt beschreven hoe u de analyse gegevens van het abonnement voor uw klanten kunt ophalen.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Dit scenario biedt alleen ondersteuning voor verificatie met gebruikers referenties.

## <a name="rest-request"></a>REST-aanvraag

### <a name="request-syntax"></a>Syntaxis van aanvraag

| Methode | Aanvraag-URI |
|--------|-------------|
| **Toevoegen** | [*\{ BASEURL \}*](partner-center-rest-urls.md)/partner/v1/Analytics/Subscriptions http/1.1 |

#### <a name="uri-parameters"></a>URI-para meters

De volgende tabel bevat optionele para meters en de bijbehorende beschrijvingen:

| Parameter | Type |  Description |
|-----------|------|--------------|
| top | int | Het aantal rijen met gegevens dat in de aanvraag moet worden geretourneerd. Als de waarde niet is opgegeven, zijn de maximum waarde en de standaard waarde `10000` . Als er meer rijen in de query staan, bevat de antwoord tekst een volgende koppeling die u kunt gebruiken om de volgende pagina met gegevens aan te vragen. |
| skip | int | Het aantal rijen dat in de query moet worden overgeslagen. Gebruik deze para meter om door grote gegevens sets te bladeren. U kunt bijvoorbeeld `top=10000` `skip=0` de eerste 10000 rijen met gegevens ophalen en `top=10000` `skip=10000` de volgende 10000 rijen met gegevens ophalen. |
| filter | tekenreeks | Een of meer instructies waarmee de rijen in het antwoord worden gefilterd. Elke filter instructie bevat een veld naam uit de hoofd tekst van het antwoord en een waarde die is gekoppeld aan de **`eq`** , **`ne`** , of voor bepaalde velden, de **`contains`** operator. Instructies kunnen worden gecombineerd met **`and`** of **`or`** . Teken reeks waarden moeten tussen enkele aanhalings tekens in de **filter** parameter worden geplaatst. Zie de volgende sectie voor een lijst met velden die kunnen worden gefilterd en de Opera tors die worden ondersteund door deze velden. |
| aggregationLevel | tekenreeks | Hiermee geeft u het tijds bereik op waarvoor u de samengevoegde gegevens wilt ophalen. Dit kan een van de volgende teken reeksen zijn: **dag**, **week** of **maand**. Als de waarde niet is opgegeven, is de standaard instelling **dateRange**. Deze para meter is alleen van toepassing wanneer een datum veld wordt door gegeven als onderdeel van de para meter **groupBy** . |
| groupBy | tekenreeks | Een instructie die alleen gegevens aggregatie toepast op de opgegeven velden. |

### <a name="request-headers"></a>Aanvraagheaders

Zie voor meer informatie [Partner Center rest headers](headers.md).

### <a name="request-body"></a>Aanvraagbody

Geen.

### <a name="request-example"></a>Voorbeeld van aanvraag

```http
GET https://api.partnercenter.microsoft.com/partner/v1/analytics/subscriptions
Authorization: Bearer <token>
Accept: application/json
Content-Type: application/json
Content-Length: 0
```

## <a name="rest-response"></a>REST-antwoord

Als dit lukt, bevat de antwoord tekst een verzameling [**abonnements**](partner-center-analytics-resources.md#subscription-resource) resources.

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes](error-codes.md)voor de volledige lijst.

### <a name="response-example"></a>Voorbeeld van antwoord

```http
{
    "customerTenantId": "76906668-27FC-4F5B-A35C-75A9823E13AF",
    "customerName": "TESTORG65656565",
    "customerMarket": "US",
    "id": "4BF546B2-8998-4838-BEE2-5F1BBE65A04F",
    "status": "ACTIVE",
    "productName": "OFFICE 365 BUSINESS PREMIUM",
    "subscriptionType": "Office",
    "autoRenewEnabled": true,
    "partnerId": "3B33E682-00C3-41EE-9DD2-A548ADF56438",
    "friendlyName": "FULL OFFICE SUITE",
    "partnerName": "Partner Name",
    "providerName": "Provider Name",
    "creationDate": "2016-02-04T19:29:38.037",
   "effectiveStartDate": "2016-02-04T00:00:00",
    "commitmentEndDate": "2019-02-10T00:00:00",
    "currentStateEndDate": "2019-02-10T00:00:00",
    "trialToPaidConversionDate": null,
    "trialStartDate": null,
    "trialEndDate": null,
    "lastUsageDate": null,
    "deprovisionedDate": null,
    "lastRenewalDate": "2018-02-10T02:39:57.729",
    "licenseCount": 2,
    "churnRisk": "High",
    "billingCycleName": "MONTHLY"

}
```

## <a name="see-also"></a>Zie ook

- [Partnercentrum Analytics - Bronnen](partner-center-analytics-resources.md)
