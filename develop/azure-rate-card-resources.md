---
title: Azure-tariefkaart - huidige Azure-prijzen
description: Meer informatie over het gebruik van de Azure-tariefkaart om realtime, actuele prijzen voor Azure-aanbiedingen in uw regio te krijgen. Azure Rate Card is toegankelijk via Partner Center REST API.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 52b9a9bea59690a8185a381647498de69a1476b1a4d4e8d632c5d13382776114
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991206"
---
# <a name="azure-rate-card-resources-to-get-real-time-current-azure-prices-on-azure-offers-in-your-region"></a>Resources voor Azure-tariefkaarten voor het in realtime ontvangen van actuele Azure-prijzen voor Azure-aanbiedingen in uw regio

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De Azure-tariefkaart biedt realtime prijzen voor Azure-aanbiedingen. Azure-prijzen zijn dynamisch en veranderen regelmatig. Microsoft publiceert updates op Partner Center, maar de REST API de snelste manier voor Cloud Solution Provider partners om de huidige prijzen te krijgen.

Als u het gebruik wilt bijhouden en wilt helpen bij het voorspellen van uw maandelijkse factuur en de facturen voor afzonderlijke klanten, kunt u een Query tariefkaart combineren om prijzen voor Microsoft Azure te krijgen met een aanvraag om de gebruiksrecords van een klant voor Azure [op](get-prices-for-microsoft-azure.md) te [halen.](get-a-customer-s-utilization-record-for-azure.md)

Prijzen verschillen per markt en valuta en deze API houdt rekening met de locatie. De API maakt standaard gebruik van uw partnerprofielinstellingen in Partner Center en uw browsertaal. Deze instellingen kunnen worden aangepast. De locatiebewustheid is vooral relevant als u de verkoop in meerdere markten beheert vanuit één gecentraliseerd kantoor.

## <a name="azureratecard"></a>AzureRateCard

Beschrijft de eigenschappen van een Azure Rate Card-resource.

| Eigenschap      | Type                                      | Description                                                       |
|---------------|-------------------------------------------|-------------------------------------------------------------------|
| currency      | tekenreeks                                    | De valuta waarin de tarieven worden opgegeven.                     |
| isTaxIncluded | booleaans                                   | Alle tarieven zijn vóór belasting, dus deze eigenschap retourneert als `false` . |
| landinstelling        | tekenreeks                                    | De cultuur waarin de resourcegegevens worden gelokaliseerd.       |
| Meter        | matrix van objecten                          | Matrix van [AzureMeter-objecten.](#azuremeter)                       |
| offerTerms    | matrix van objecten                          | Matrix van [AzureOfferTerm-objecten.](#azureofferterm)               |
| kenmerken    | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken. Bevat `"objectType": "AzureRateCard"`   |

### <a name="operations-on-the-azureratecard-resource"></a>Bewerkingen op de AzureRateCard-resource

- [Prijzen voor Microsoft Azure ophalen](get-prices-for-microsoft-azure.md)

## <a name="azuremeter"></a>AzureMeter

| Eigenschap         | Type             | Beschrijving                                                                                   |
|------------------|------------------|-----------------------------------------------------------------------------------------------|
| id               | tekenreeks           | De unieke id van de meter.                                                                    |
| naam             | tekenreeks           | Gebruiksvriendelijke naam van de meter.                                                                   |
| Tarieven            | object           | Metertarieven. De sleutel is de meterhoeveelheid (tekenreeks) en de waarde is het metertarief (getal). |
| tags             | tekenreeksmatrix | Optionele metertags. Deze matrix kan leeg zijn.                                                 |
| category         | tekenreeks           | Categorie van de resource.                                                                     |
| Subcategorie      | tekenreeks           | Subcategorie van de resource.                                                                 |
| regio           | tekenreeks           | Regio van de id.                                                                             |
| eenheid             | tekenreeks           | Het type hoeveelheid (uren, bytes, enzovoort)                                                     |
| includedQuantity | getal           | Meterhoeveelheid die gratis is inbegrepen.                                               |
| effectiveDate    | tekenreeks           | De datum waarop deze meter van kracht is.                                                             |

## <a name="azureofferterm"></a>AzureOfferTerm

| Eigenschap         | Type             | Beschrijving                             |
|------------------|------------------|-----------------------------------------|
| naam             | tekenreeks           | Gebruiksvriendelijke naam van de aanbiedingstermijn.        |
| discount         | getal           | De toegepaste korting, indien van toepassing.           |
| excludedMeterIds | tekenreeksmatrix | Meters die zijn uitgesloten van de aanbieding, indien van u. |
| effectiveDate    | tekenreeks           | De datum waarop de aanbieding van kracht is.        |
