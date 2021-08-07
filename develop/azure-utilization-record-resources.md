---
title: Resources voor Azure-gebruiksrecord
description: De Azure-gebruiksrecord bevat details over het gebruik van een Azure-abonnementsresource.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: eb905dd41d5ab177a29bc1bd949c5eb865e4614e204250709d91f1a31304b267
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115992276"
---
# <a name="azure-utilization-record-resources"></a>Resources voor Azure-gebruiksrecord

**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De Azure-gebruiksrecord bevat details over het gebruik van een Azure-abonnementsresource. Als u een cloudserviceproviderpartner bent die eigenaar is van de factureringsrelatie voor de Azure-abonnementen van uw klanten, kunt u deze REST API gebruiken om een schaalbare manier te bieden voor het bijhouden van het gebruik van de abonnementen om aan het einde van elke factureringscyclus een factuur naar uw klanten te verzenden.

Als u het gebruik wilt bijhouden en wilt helpen bij het voorspellen van uw maandelijkse factuur en de facturen voor afzonderlijke klanten, kunt u een Query tariefkaart combineren om prijzen voor Microsoft Azure te krijgen met een aanvraag om de gebruiksrecords van een klant voor Azure [op](get-prices-for-microsoft-azure.md) te [halen.](get-a-customer-s-utilization-record-for-azure.md)

De prijzen verschillen per markt en valuta en deze API houdt rekening met de locatie. De API maakt standaard gebruik van uw partnerprofielinstellingen in Partner Center en uw browsertaal. Deze instellingen kunnen worden aangepast. De locatiebewustheid is vooral relevant als u de verkoop in meerdere markten beheert vanuit één gecentraliseerd kantoor.

## <a name="azureutilizationrecord"></a>AzureUtilizationRecord

Beschrijft de eigenschappen van een Azure-gebruiksrecordresource.

| Eigenschap       | Type                                      | Vereist | Beschrijving                                                                                                                                                                             |
|----------------|-------------------------------------------|----------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| usageStartTime | tekenreeks                                    | Yes      | Het begin van het tijdsbereik van de gebruiksaggregatie. Het antwoord wordt gegroepeerd op het moment van verbruik (wanneer de resource is gebruikt versus wanneer deze is gerapporteerd aan het factureringssysteem). |
| usageEndTime   | tekenreeks                                    | Yes      | Het einde van het tijdsbereik voor gebruiksaggregatie. Het antwoord wordt gegroepeerd op het tijdstip van verbruik. Dat wil zeggen wanneer de resource is gebruikt versus wanneer deze is gerapporteerd aan het factureringssysteem.   |
| resource       | object                                    | Yes      | Bevat een [AzureResource-object.](#azureresource)                                                                                                                                     |
| quantity       | getal                                    | Yes      | De verbruikte hoeveelheid van [de AzureResource.](#azureresource)                                                                                                                           |
| eenheid           | tekenreeks                                    | No       | Het type hoeveelheid (uren, bytes, enzovoort) Deze eigenschap is optioneel                                                                                                                     |
| infoFields     | object                                    | Yes      | Sleutel-waardeparen van details op exemplaarniveau. Dit object is mogelijk leeg.                                                                                                                    |
| instanceData   | object                                    | No       | Bevat een [AzureInstanceData-object](#azureinstancedata) dat sleutel-waardeparen van details op instantieniveau bevat. Deze eigenschap is optioneel en kan niet worden opgenomen.                  |
| kenmerken     | [ResourceAttributes](utility-resources.md#resourceattributes) | Yes      | De metagegevenskenmerken. Bevat 'objectType': 'AzureUtilizationRecord'                                                                                                                |

### <a name="operations-on-the-azureutilizationrecord-resource"></a>Bewerkingen op de AzureUtilizationRecord-resource

- [Gebruiksrecords van een klant ophalen voor Azure](get-a-customer-s-utilization-record-for-azure.md)

## <a name="azureresource"></a>AzureResource

Beschrijft de eigenschappen van een Azure-resource.

| Eigenschap    | Type   | Vereist | Beschrijving                                                                         |
|-------------|--------|----------|-------------------------------------------------------------------------------------|
| id          | tekenreeks | Yes      | De unieke id van de Azure-resource. Dit wordt ook wel resourceID of resource-GUID genoemd. |
| naam        | tekenreeks | No       | Gebruiksvriendelijke naam van de resource die wordt verbruikt. Deze eigenschap is optioneel.            |
| category    | tekenreeks | No       | De categorie van de verbruikte resource. Deze eigenschap is optioneel.                   |
| Subcategorie | tekenreeks | No       | De subcategorie van de verbruikte resource. Deze eigenschap is optioneel.               |
| regio      | tekenreeks | No       | De regio van de verbruikte resource. Deze eigenschap is optioneel.                     |

## <a name="azureinstancedata"></a>AzureInstanceData

Beschrijft de eigenschappen van een Azure Instance Data-resource.

| Eigenschap       | Type             | Vereist | Beschrijving                                                                                                        |
|----------------|------------------|----------|--------------------------------------------------------------------------------------------------------------------|
| resourceUri    | tekenreeks           | Yes      | De volledig gekwalificeerde Azure-resource-id, die de resourcegroepen en de naam van het exemplaar bevat.                   |
| location       | tekenreeks           | Yes      | Regio waarin de service is uitgevoerd.                                                                               |
| partNumber     | object           | Yes      | Unieke naamruimte die wordt gebruikt om de resource te identificeren voor gebruik door derden op de commerciële marketplace. Deze eigenschap kan een lege tekenreeks zijn. |
| orderNumber    | getal           | Yes      | Unieke naamruimte die wordt gebruikt om de bestelling van derden voor de commerciële marketplace te identificeren. Deze eigenschap kan een lege tekenreeks zijn.          |
| tags           | tekenreeksmatrix | No       | Resourcetags die door de gebruiker zijn opgegeven. Deze eigenschap is optioneel en kan niet worden opgenomen.                            |
| additionalInfo | tekenreeksmatrix | No       | Aanvullende gegevens voor een Azure-resource. Deze eigenschap is optioneel en kan niet worden opgenomen.                          |