---
title: Tarieven kaart van Azure-huidige Azure-prijzen
description: Meer informatie over het gebruik van de Azure-tarief kaart voor real-time, actuele prijzen voor Azure-aanbiedingen in uw regio. De tarieven kaart van Azure wordt geopend via partner Center REST API.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 2d011153f508ea0a745413b88003333452d0af24
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767599"
---
# <a name="azure-rate-card-resources-to-get-real-time-current-azure-prices-on-azure-offers-in-your-region"></a>Azure-tarieven voor het beoordelen van real-time, actuele Azure-prijzen op Azure-aanbiedingen in uw regio

**Van toepassing op:**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De Azure-tarief kaart biedt real-time prijzen voor Azure-aanbiedingen. Prijzen voor Azure zijn vaak dynamisch en worden gewijzigd. Micro soft publiceert updates op partner centrum, maar de REST API biedt de snelste manier voor partners van de Cloud solution provider om actuele prijzen te verkrijgen.

Om het gebruik bij te houden en te helpen uw maandelijkse factuur en de facturen voor afzonderlijke klanten te voors pellen, kunt u een tarief kaart query combi neren om [prijzen voor Microsoft Azure](get-prices-for-microsoft-azure.md) op te halen met een aanvraag voor [het ophalen van de gebruiks gegevens van een klant voor Azure](get-a-customer-s-utilization-record-for-azure.md).

De prijzen zijn afhankelijk van de markt en valuta en deze API houdt rekening met de locatie. De API maakt standaard gebruik van uw partner Profiel instellingen in partner centrum en uw browser taal, en deze instellingen zijn aanpasbaar. De locatie van het bewustzijn is vooral relevant als u de verkoop op meerdere markten beheert vanuit één gecentraliseerd kantoor.

## <a name="azureratecard"></a>AzureRateCard

Beschrijft de eigenschappen van een Azure-tarieven resource.

| Eigenschap      | Type                                      | Description                                                       |
|---------------|-------------------------------------------|-------------------------------------------------------------------|
| currency      | tekenreeks                                    | De valuta waarin de tarieven zijn opgenomen.                     |
| isTaxIncluded | booleaans                                   | Alle tarieven zijn Pretax, dus deze eigenschap retourneert als `false` . |
| landinstelling        | tekenreeks                                    | De cultuur waarin de resource gegevens worden gelokaliseerd.       |
| meet        | matrix van objecten                          | Matrix van [AzureMeter](#azuremeter) -objecten.                       |
| offerTerms    | matrix van objecten                          | Matrix van [AzureOfferTerm](#azureofferterm) -objecten.               |
| kenmerken    | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken. Daarin `"objectType": "AzureRateCard"`   |

### <a name="operations-on-the-azureratecard-resource"></a>Bewerkingen op de AzureRateCard-resource

- [Prijzen voor Microsoft Azure ophalen](get-prices-for-microsoft-azure.md)

## <a name="azuremeter"></a>AzureMeter

| Eigenschap         | Type             | Beschrijving                                                                                   |
|------------------|------------------|-----------------------------------------------------------------------------------------------|
| id               | tekenreeks           | Unieke id van de meter.                                                                    |
| naam             | tekenreeks           | Beschrijvende naam van de meter.                                                                   |
| kosten            | object           | Meter frequenties. De sleutel is de meter hoeveelheid (teken reeks) en de waarde is de meter frequentie (getal). |
| tags             | tekenreeksmatrix | Optionele meter Tags. Deze matrix kan leeg zijn.                                                 |
| category         | tekenreeks           | De categorie van de resource.                                                                     |
| subcategorie      | tekenreeks           | De subcategorie van de resource.                                                                 |
| regio           | tekenreeks           | De regio van de id.                                                                             |
| eenheid             | tekenreeks           | Het type hoeveelheid (uren, bytes, enz.)                                                     |
| includedQuantity | getal           | Het aantal beschik bare meters.                                               |
| effectiveDate    | tekenreeks           | De datum waarop deze meter actief is.                                                             |

## <a name="azureofferterm"></a>AzureOfferTerm

| Eigenschap         | Type             | Beschrijving                             |
|------------------|------------------|-----------------------------------------|
| naam             | tekenreeks           | Beschrijvende naam van de aanbiedings voorwaarde.        |
| discount         | getal           | De korting toegepast, indien van toepassing.           |
| excludedMeterIds | tekenreeksmatrix | Meters die zijn uitgesloten van de aanbieding, indien van toepassing. |
| effectiveDate    | tekenreeks           | De datum waarop de aanbieding van kracht is.        |
