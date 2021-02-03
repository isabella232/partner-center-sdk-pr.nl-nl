---
title: REST-headers voor Partnercentrum
description: Meer informatie over de headers van de HTTP REST-aanvraag en REST response-headers die worden ondersteund door het partner centrum REST API.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9f506c8c610c2584912c24453288d0f3578b84e3
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "97767579"
---
# <a name="partner-center-rest-and-response-headers-supported-by-the-partner-center-rest-api"></a>De REST-en reactie headers van partner Center worden ondersteund door het partner centrum REST API 

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De volgende HTTP-aanvraag-en-antwoord headers worden ondersteund door het partner centrum-REST API. Niet alle API-aanroepen accepteren alle headers.

## <a name="rest-request-headers"></a>Kopteksten REST-aanvraag

De volgende HTTP-aanvraag headers worden ondersteund door het partner centrum-REST API.

| Header                       | Description                                                                                                                                                                                                                                                                            | Waardetype |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Autorisatie               | Vereist. Het autorisatie token in de vorm Bearer- &lt; token &gt; .                                                                                                                                                                                                                    | tekenreeks     |
| Zodat                      | Hiermee geeft u de aanvraag en het antwoord type ' application/json ' op.                                                                                                                                                                                                                           | tekenreeks     |
| MS-aanvraag:                | Een unieke id voor de oproep die wordt gebruikt om id-potentie te garanderen. Als er een time-out is, moet de aanroep dezelfde waarde bevatten. Wanneer er een reactie wordt ontvangen (geslaagd of mislukt), moet de waarde opnieuw worden ingesteld voor de volgende aanroep.                                            | GUID       |
| MS-CorrelationId:            | Een unieke id voor de aanroep, die nuttig is in Logboeken en netwerk traceringen voor het oplossen van problemen. De waarde moet opnieuw worden ingesteld voor elke aanroep. Alle bewerkingen moeten deze header bevatten. Zie voor meer informatie de correlatie-ID-informatie in [testen en fout opsporing](test-and-debug.md). | GUID       |
| MS-contract-versie:         | Vereist. Hiermee geeft u de versie van de aangevraagde API op. over het algemeen API-Version: v1 tenzij anders vermeld in de sectie [Scenarios](scenarios.md) .                                                                                                                                  | tekenreeks     |
| If-match:                    | Wordt gebruikt voor gelijktijdigheids beheer. Voor sommige API-aanroepen moet de ETag worden door gegeven via de If-Match-header. De ETag bevindt zich doorgaans in de resource en vereist daarom de meest recente versie. Zie voor meer informatie de ETag-informatie in [testen en fout opsporing](test-and-debug.md).                | tekenreeks     |
| MS-PartnerCenter-toepassing | Optioneel. Hiermee geeft u de naam op van de toepassing die gebruikmaakt van het partner centrum REST API.                                                                                                                                                                                             | tekenreeks     |
| X-land instelling:                    | Optioneel. Hiermee geeft u de taal waarin de tarieven worden geretourneerd. De standaard waarde is "en-US". Zie voor een lijst met ondersteunde waarden [partner centrum ondersteunde talen en land instellingen](partner-center-supported-languages-and-locales.md).                                                                                                                                                                                                  | tekenreeks     |

## <a name="rest-response-headers"></a>REST-reactie headers

De volgende HTTP-antwoord headers kunnen worden geretourneerd door het partner centrum REST API.

| Header            | Description                                                                                                                                                                                                                                 | Waardetype |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Zodat           | Hiermee geeft u de aanvraag en het antwoord type ' application/json ' op.                                                                                                                                                                                | tekenreeks     |
| MS-aanvraag:     | Een unieke id voor de oproep die wordt gebruikt om id-potentie te garanderen. Als er een time-out is, moet de aanroep dezelfde waarde bevatten. Wanneer er een reactie wordt ontvangen (geslaagd of mislukt), moet de waarde opnieuw worden ingesteld voor de volgende aanroep. | GUID       |
| MS-CorrelationId: | Een unieke id voor de aanroep. Deze waarde is handig voor het oplossen van problemen met Logboeken en netwerk traceringen. De waarde moet opnieuw worden ingesteld voor elke aanroep. Alle bewerkingen moeten deze header bevatten.                                                       | GUID       |
