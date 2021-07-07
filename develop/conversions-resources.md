---
title: Conversiebronnen
description: Meer informatie over het gebruik Partner Center API Conversion-resources om u te helpen een proefabonnement te converteren naar een betaald abonnement.
ms.date: 05/23/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1863c365627807d8de2534a2d3116807a5de70e1
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973890"
---
# <a name="conversion-resources-to-convert-trial-subscriptions-to-paid"></a>Conversie van resources om proefabonnementen om te zetten in betaald

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Conversiebronnen ondersteunen de conversie van een proefabonnement naar een betaald abonnement.

## <a name="conversion"></a>Conversie

Bevat informatie die wordt gebruikt om een proefabonnement te converteren naar een betaald abonnement.

| Eigenschap | Type | Beschrijving |
| -------- | ---- | ----------- |
| offerId | tekenreeks | De aanbiedings-id van de oorspronkelijke proefversie. |
| targetOfferId | tekenreeks | De aanbiedings-id voor de doelaanbieding. |
| Orderid | tekenreeks | De order-id. |
| quantity | int | Het aantal licenties. De standaardwaarde is het aantal licenties in het proefabonnement. |
| billingCycle | tekenreeks | Geeft aan hoe vaak de partner in rekening wordt gebracht voor het abonnement. Mogelijke waarden: **Maandelijks** (partner wordt maandelijks gefactureerd), **Jaarlijks** (partner wordt jaarlijks gefactureerd) of Geen **(partner** wordt niet gefactureerd. Wordt gebruikt voor proefabonnementen). |

## <a name="conversionerror"></a>ConversionError

Vertegenwoordigt een fout die is opgetreden tijdens de conversie.

| Eigenschap | Type | Beschrijving |
| -------- | ---- | ----------- |
| code | tekenreeks | De foutcode die aan het probleem is gekoppeld. Mogelijke waarden: **Overige** (algemene fout), **ConversionsNotFound** (kan geen conversies vinden voor het proefabonnement om naar te converteren).
| beschrijving | tekenreeks | De beschrijvende tekst waarin het probleem wordt beschreven. |

## <a name="conversionresult"></a>ConversionResult

Vertegenwoordigt het resultaat van het uitvoeren van een abonnementsconversie.

| Eigenschap       | Type                                | Beschrijving                                                            |
|----------------|-------------------------------------|------------------------------------------------------------------------|
| subscriptionId | tekenreeks                              | De abonnements-id.                                           |
| offerId        | tekenreeks                              | De oorspronkelijke aanbiedings-id.                                         |
| targetOfferId  | tekenreeks                              | De aanbiedings-id voor de doelaanbieding.                             |
| fout          | [ConversionError](#conversionerror) | De fout die is opgetreden bij het proberen van de conversie, indien van toepassing. |