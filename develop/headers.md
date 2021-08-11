---
title: REST-headers voor Partnercentrum
description: Meer informatie over de HTTP REST-aanvraagheaders en REST-antwoordheaders die worden ondersteund door de Partner Center REST API.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9c9483e761465be1a60003dcd44cef46af3e99634d99d804d43d101d6b8ef700
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115993811"
---
# <a name="partner-center-rest-and-response-headers-supported-by-the-partner-center-rest-api"></a>Partner Center REST en antwoordheaders die worden ondersteund door de Partner Center REST API 

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De volgende HTTP-aanvraag- en antwoordheaders worden ondersteund door de Partner Center REST API. Niet alle API-aanroepen accepteren alle headers.

## <a name="rest-request-headers"></a>REST-aanvraagheaders

De volgende HTTP-aanvraagheaders worden ondersteund door de Partner Center REST API.

| Header                       | Description                                                                                                                                                                                                                                                                            | Waardetype |
|------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Vergunning:               | Vereist. Het autorisatie-token in het formulier &lt; Bearer-token &gt; .                                                                                                                                                                                                                    | tekenreeks     |
| Accepteren:                      | Hiermee geeft u het aanvraag- en antwoordtype 'application/json' op.                                                                                                                                                                                                                           | tekenreeks     |
| MS-RequestId:                | Een unieke id voor de aanroep, die wordt gebruikt om te zorgen voor id-cy. Als er een time-out is, moet de aanroep voor opnieuw proberen dezelfde waarde bevatten. Wanneer u een antwoord ontvangt (geslaagd of mislukt), moet de waarde opnieuw worden ingesteld voor de volgende aanroep.                                            | GUID       |
| MS-CorrelationId:            | Een unieke id voor de aanroep, handig in logboeken en netwerk traceringen voor het oplossen van fouten. De waarde moet voor elke aanroep opnieuw worden ingesteld. Alle bewerkingen moeten deze header bevatten. Zie de correlatie-id in Testen en fouten opsporen voor [meer informatie.](test-and-debug.md) | GUID       |
| MS-Contract-Version:         | Vereist. Hiermee geeft u de gevraagde versie van de API op; over het algemeen API-versie: v1, tenzij anders aangegeven in de [sectie Scenario's.](scenarios.md)                                                                                                                                  | tekenreeks     |
| If-Match:                    | Wordt gebruikt voor gelijktijdigheidsbeheer. Voor sommige API-aanroepen moet de ETag worden doorgeven via If-Match header. De ETag is meestal op de resource en vereist daarom get-ting de meest recente. Zie de ETag-informatie in Testen en fouten opsporen [voor meer informatie.](test-and-debug.md)                | tekenreeks     |
| MS-PartnerCenter-Application | Optioneel. Hiermee geeft u de naam van de toepassing die gebruik maakt van de Partner Center REST API.                                                                                                                                                                                             | tekenreeks     |
| X-Locale:                    | Optioneel. Hiermee geeft u de taal waarin de tarieven worden geretourneerd. De standaardwaarde is en-US. Zie ondersteunde talen en Partner Center voor een lijst met [ondersteunde waarden.](partner-center-supported-languages-and-locales.md)                                                                                                                                                                                                  | tekenreeks     |

## <a name="rest-response-headers"></a>REST-antwoordheaders

De volgende HTTP-antwoordheaders kunnen worden geretourneerd door de Partner Center REST API.

| Header            | Description                                                                                                                                                                                                                                 | Waardetype |
|-------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------|
| Accepteren:           | Hiermee geeft u het aanvraag- en antwoordtype 'application/json' op.                                                                                                                                                                                | tekenreeks     |
| MS-RequestId:     | Een unieke id voor de aanroep, die wordt gebruikt om te zorgen voor id-cy. Als er een time-out is, moet de aanroep voor opnieuw proberen dezelfde waarde bevatten. Wanneer u een antwoord ontvangt (geslaagd of mislukt), moet de waarde opnieuw worden ingesteld voor de volgende aanroep. | GUID       |
| MS-CorrelationId: | Een unieke id voor de aanroep. Deze waarde is handig voor het oplossen van problemen met logboeken en netwerk traceringen om de fout te vinden. De waarde moet voor elke aanroep opnieuw worden ingesteld. Alle bewerkingen moeten deze header bevatten.                                                       | GUID       |
