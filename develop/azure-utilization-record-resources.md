---
title: Azure-gebruiks record bronnen
description: Het Azure-gebruiks record bevat details over het gebruik van een Azure-abonnements resource.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 21d39c4497c00f5abeeeb771dfe20cd1e2b1c13a
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767205"
---
# <a name="azure-utilization-record-resources"></a>Azure-gebruiks record bronnen

**Van toepassing op:**

- Partnercentrum
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Het Azure-gebruiks record bevat details over het gebruik van een Azure-abonnements resource. Als u een Cloud service provider bent die eigenaar is van de facturerings relatie voor Azure-abonnementen van uw klanten, kunt u deze REST API gebruiken om een schaal bare manier te bieden voor het bijhouden van het gebruik dat in de abonnementen wordt gemaakt om een factuur aan uw klanten te sturen aan het einde van elke facturerings cyclus.

Om het gebruik bij te houden en te helpen uw maandelijkse factuur en de facturen voor afzonderlijke klanten te voors pellen, kunt u een tarief kaart query combi neren om [prijzen voor Microsoft Azure](get-prices-for-microsoft-azure.md) op te halen met een aanvraag voor [het ophalen van de gebruiks gegevens van een klant voor Azure](get-a-customer-s-utilization-record-for-azure.md).

De prijzen zijn afhankelijk van de markt en valuta en deze API houdt rekening met de locatie. De API maakt standaard gebruik van uw partner Profiel instellingen in partner centrum en uw browser taal, en deze instellingen zijn aanpasbaar. De locatie van het bewustzijn is vooral relevant als u de verkoop op meerdere markten beheert vanuit één gecentraliseerd kantoor.

## <a name="azureutilizationrecord"></a>AzureUtilizationRecord

Beschrijft de eigenschappen van een Azure-resource voor het gebruik van records.

| Eigenschap       | Type                                      | Vereist | Beschrijving                                                                                                                                                                             |
|----------------|-------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| usageStartTime | tekenreeks                                    | Yes      | Het begin van het tijds bereik voor het samen voegen van gebruik. Het antwoord wordt gegroepeerd op het moment van verbruik (wanneer de resource werkelijk is gebruikt en wanneer het is gerapporteerd aan het facturerings systeem). |
| usageEndTime   | tekenreeks                                    | Yes      | Het einde van het tijds bereik voor het samen voegen van gebruik. Het antwoord wordt gegroepeerd op het moment van verbruik. Dat wil zeggen, wanneer de resource werkelijk wordt gebruikt, en wanneer deze is gerapporteerd aan het facturerings systeem.   |
| resource       | object                                    | Yes      | Bevat een [bronnen](#azureresource) -object.                                                                                                                                     |
| quantity       | getal                                    | Yes      | De hoeveelheid die is verbruikt van de [bronnen.](#azureresource)                                                                                                                           |
| eenheid           | tekenreeks                                    | No       | Het type hoeveelheid (uren, bytes, enz.) Deze eigenschap is optioneel                                                                                                                     |
| infoFields     | object                                    | Yes      | Sleutel-waardeparen van Details van instantie niveau. Dit object kan leeg zijn.                                                                                                                    |
| instanceData   | object                                    | No       | Bevat een [AzureInstanceData](#azureinstancedata) -object dat sleutel-waardeparen van Details van het exemplaar niveau bevat. Deze eigenschap is optioneel en kan niet worden opgenomen.                  |
| kenmerken     | [ResourceAttributes](utility-resources.md#resourceattributes) | Yes      | De meta gegevens kenmerken. Bevat "object type": "AzureUtilizationRecord"                                                                                                                |

### <a name="operations-on-the-azureutilizationrecord-resource"></a>Bewerkingen op de AzureUtilizationRecord-resource

- [Gebruiksrecords van een klant ophalen voor Azure](get-a-customer-s-utilization-record-for-azure.md)

## <a name="azureresource"></a>Bronnen

Beschrijft de eigenschappen van een Azure-resource.

| Eigenschap    | Type   | Vereist | Beschrijving                                                                         |
|-------------|--------|----------|-------------------------------------------------------------------------------------|
| id          | tekenreeks | Yes      | De unieke id van de Azure-resource. Ook wel resourceID of resource-GUID genoemd. |
| naam        | tekenreeks | No       | Beschrijvende naam van de bron die wordt verbruikt. Deze eigenschap is optioneel.            |
| category    | tekenreeks | No       | De categorie van de verbruikte resource. Deze eigenschap is optioneel.                   |
| subcategorie | tekenreeks | No       | De subcategorie van de verbruikte resource. Deze eigenschap is optioneel.               |
| regio      | tekenreeks | No       | De regio van de verbruikte resource. Deze eigenschap is optioneel.                     |

## <a name="azureinstancedata"></a>AzureInstanceData

Beschrijft de eigenschappen van een Azure instance-gegevens bron.

| Eigenschap       | Type             | Vereist | Beschrijving                                                                                                        |
|----------------|------------------|----------|--------------------------------------------------------------------------------------------------------------------|
| resourceUri    | tekenreeks           | Yes      | De volledig gekwalificeerde Azure-Resource-ID, die de resource groepen en de naam van het exemplaar bevat.                   |
| location       | tekenreeks           | Yes      | De regio waarin de service is uitgevoerd.                                                                               |
| partNumber     | object           | Yes      | Unieke naam ruimte die wordt gebruikt voor het identificeren van de resource voor commerciële Marketplace van het gebruik van derden. Deze eigenschap kan een lege teken reeks zijn. |
| orderNumber    | getal           | Yes      | Unieke naam ruimte die wordt gebruikt om de volg orde van de externe partij voor commerciële Marketplace te identificeren. Deze eigenschap kan een lege teken reeks zijn.          |
| tags           | tekenreeksmatrix | No       | De resource Tags die zijn opgegeven door de gebruiker. Deze eigenschap is optioneel en kan niet worden opgenomen.                            |
| additionalInfo | tekenreeksmatrix | No       | Aanvullende gegevens voor een Azure-resource. Deze eigenschap is optioneel en kan niet worden opgenomen.                          |