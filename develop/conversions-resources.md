---
title: Conversiebronnen
description: Meer informatie over het gebruik Partner Center API Conversion-resources om u te helpen een proefabonnement te converteren naar een betaald abonnement.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9e7f8985fa15f4959f3cb5a729e492bbb9f3f624a5812f5b87fc119f841dc87e
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991868"
---
# <a name="conversion-resources-to-convert-trial-subscriptions-to-paid"></a>Resources converteren om proefabonnementen om te zetten in betaald

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Conversiebronnen ondersteunen de conversie van een proefabonnement naar een betaald abonnement.

## <a name="conversion"></a>Conversie

Bevat informatie die wordt gebruikt om een proefabonnement te converteren naar een betaald abonnement.

| Eigenschap | Type | Description |
| -------- | ---- | ----------- |
| offerId | tekenreeks | De aanbiedings-id van de oorspronkelijke proefversie. |
| targetOfferId | tekenreeks | De aanbiedings-id voor de doelaanbieding. |
| Orderid | tekenreeks | De order-id. |
| quantity | int | Het aantal licenties. De standaardwaarde is het aantal licenties in het proefabonnement. |
| billingCycle | tekenreeks | Geeft aan hoe vaak de partner in rekening wordt gebracht voor het abonnement. Mogelijke waarden: **Maandelijks** (partner wordt maandelijks gefactureerd), **Jaarlijks** (partner wordt jaarlijks gefactureerd) of Geen **(partner** wordt niet gefactureerd. Wordt gebruikt voor proefabonnementen). |

## <a name="conversionerror"></a>ConversionError

Vertegenwoordigt een fout die is opgetreden tijdens de conversie.

| Eigenschap | Type | Description |
| -------- | ---- | ----------- |
| code | tekenreeks | De foutcode die aan het probleem is gekoppeld. Mogelijke waarden: **Overige** (algemene fout), **ConversionsNotFound** (kan geen conversies vinden voor het proefabonnement om naar te converteren).
| beschrijving | tekenreeks | De beschrijvende tekst waarin het probleem wordt beschreven. |

## <a name="conversionresult"></a>ConversionResult

Vertegenwoordigt het resultaat van het uitvoeren van een abonnementsconversie.

| Eigenschap       | Type                                | Description                                                            |
|----------------|-------------------------------------|------------------------------------------------------------------------|
| subscriptionId | tekenreeks                              | De abonnements-id.                                           |
| offerId        | tekenreeks                              | De oorspronkelijke aanbiedings-id.                                         |
| targetOfferId  | tekenreeks                              | De aanbiedings-id voor de doelaanbieding.                             |
| fout          | [ConversionError](#conversionerror) | De fout die is opgetreden bij het proberen van de conversie, indien van toepassing. |