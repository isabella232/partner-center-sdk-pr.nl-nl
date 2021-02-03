---
title: Conversie resources
description: Meer informatie over het gebruik van de API-conversie bronnen van partner Center om een proef abonnement te converteren naar een betaald abonnement.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d3ade5a5af76e7c637962b6bfe076ac806f337bf
ms.sourcegitcommit: a25d4951f25502cdf90cfb974022c5e452205f42
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/04/2020
ms.locfileid: "97767617"
---
# <a name="conversion-resources-to-convert-trial-subscriptions-to-paid"></a>Conversie resources om proef abonnementen te converteren naar betaald

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Conversie resources ondersteunen de conversie van een proef abonnement op een betaald abonnement.

## <a name="conversion"></a>Conversie

Bevat informatie die wordt gebruikt om een proef abonnement te converteren naar een betaald abonnement.

| Eigenschap | Type | Description |
| -------- | ---- | ----------- |
| offerId | tekenreeks | De aanbiedings-id van de oorspronkelijke, proef versie van de aanbieding. |
| targetOfferId | tekenreeks | De aanbiedings-id voor de doel aanbieding. |
| Velden | tekenreeks | De order-id. |
| quantity | int | Het aantal licenties. De standaard waarde is het aantal licenties in het proef abonnement. |
| billingCycle | tekenreeks | Hiermee wordt aangegeven hoe vaak de partner in rekening wordt gebracht voor het abonnement. Mogelijke waarden: **maandelijks** (de partner wordt maandelijks gefactureerd), **jaarlijks** (partner wordt per jaar gefactureerd) of **geen** (partner wordt niet in rekening gebracht. Gebruikt voor proef abonnementen). |

## <a name="conversionerror"></a>ConversionError

Duidt op een fout die is opgetreden tijdens de conversie.

| Eigenschap | Type | Description |
| -------- | ---- | ----------- |
| code | tekenreeks | De fout code die is gekoppeld aan het probleem. Mogelijke waarden: **other** (algemene fout), **ConversionsNotFound** (kan geen conversies vinden voor het proef abonnement om te converteren naar).
| beschrijving | tekenreeks | De beschrijvende tekst die het probleem beschrijft. |

## <a name="conversionresult"></a>ConversionResult

Hiermee wordt het resultaat van het uitvoeren van een abonnements conversie aangegeven.

| Eigenschap       | Type                                | Description                                                            |
|----------------|-------------------------------------|------------------------------------------------------------------------|
| subscriptionId | tekenreeks                              | De abonnements-id.                                           |
| offerId        | tekenreeks                              | De oorspronkelijke aanbiedings-id.                                         |
| targetOfferId  | tekenreeks                              | De aanbiedings-id voor de doel aanbieding.                             |
| fout          | [ConversionError](#conversionerror) | Er is een fout opgetreden bij het uitvoeren van de conversie, indien van toepassing. |