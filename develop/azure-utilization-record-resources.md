---
title: Resources voor Azure-gebruiksrecord
description: De Azure-gebruiksrecord bevat details over het gebruik van een Azure-abonnementsresource.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 868381fcb29eb1391efcdf79154f7b998e3032e5
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974298"
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
| usageStartTime | tekenreeks                                    | Ja      | Het begin van het tijdsbereik van de gebruiksaggregatie. Het antwoord wordt gegroepeerd op het moment van verbruik (wanneer de resource is gebruikt versus wanneer deze is gerapporteerd aan het factureringssysteem). |
| usageEndTime   | tekenreeks                                    | Ja      | Het einde van het tijdsbereik voor gebruiksaggregatie. Het antwoord wordt gegroepeerd op het tijdstip van verbruik. Dat wil zeggen wanneer de resource is gebruikt versus wanneer deze is gerapporteerd aan het factureringssysteem.   |
| resource       | object                                    | Ja      | Bevat een [AzureResource-object.](#azureresource)                                                                                                                                     |
| quantity       | getal                                    | Ja      | De verbruikte hoeveelheid van [de AzureResource.](#azureresource)                                                                                                                           |
| eenheid           | tekenreeks                                    | No       | Het type hoeveelheid (uren, bytes, enzovoort) Deze eigenschap is optioneel                                                                                                                     |
| infoFields     | object                                    | Ja      | Sleutel-waardeparen van details op exemplaarniveau. Dit object is mogelijk leeg.                                                                                                                    |
| instanceData   | object                                    | Nee       | Bevat een [AzureInstanceData-object](#azureinstancedata) dat sleutel-waardeparen van details op instantieniveau bevat. Deze eigenschap is optioneel en kan niet worden opgenomen.                  |
| kenmerken     | [ResourceAttributes](utility-resources.md#resourceattributes) | Ja      | De metagegevenskenmerken. Bevat 'objectType': 'AzureUtilizationRecord'                                                                                                                |

### <a name="operations-on-the-azureutilizationrecord-resource"></a>Bewerkingen op de AzureUtilizationRecord-resource

- [Gebruiksrecords van een klant ophalen voor Azure](get-a-customer-s-utilization-record-for-azure.md)

## <a name="azureresource"></a>AzureResource

Beschrijft de eigenschappen van een Azure-resource.

| Eigenschap    | Type   | Vereist | Beschrijving                                                                         |
|-------------|--------|----------|-------------------------------------------------------------------------------------|
| id          | tekenreeks | Ja      | De unieke id van de Azure-resource. Dit wordt ook wel resourceID of resource-GUID genoemd. |
| naam        | tekenreeks | No       | Gebruiksvriendelijke naam van de resource die wordt verbruikt. Deze eigenschap is optioneel.            |
| category    | tekenreeks | No       | De categorie van de verbruikte resource. Deze eigenschap is optioneel.                   |
| Subcategorie | tekenreeks | No       | De subcategorie van de verbruikte resource. Deze eigenschap is optioneel.               |
| regio      | tekenreeks | No       | De regio van de verbruikte resource. Deze eigenschap is optioneel.                     |

## <a name="azureinstancedata"></a>AzureInstanceData

Beschrijft de eigenschappen van een Azure Instance Data-resource.

| Eigenschap       | Type             | Vereist | Beschrijving                                                                                                        |
|----------------|------------------|----------|--------------------------------------------------------------------------------------------------------------------|
| resourceUri    | tekenreeks           | Ja      | De volledig gekwalificeerde Azure-resource-id, die de resourcegroepen en de naam van het exemplaar bevat.                   |
| location       | tekenreeks           | Ja      | Regio waarin de service is uitgevoerd.                                                                               |
| partNumber     | object           | Ja      | Unieke naamruimte die wordt gebruikt om de resource te identificeren voor gebruik door derden op de commerciële marketplace. Deze eigenschap kan een lege tekenreeks zijn. |
| orderNumber    | getal           | Ja      | Unieke naamruimte die wordt gebruikt om de bestelling van derden voor de commerciële marketplace te identificeren. Deze eigenschap kan een lege tekenreeks zijn.          |
| tags           | tekenreeksmatrix | Nee       | Resourcetags die door de gebruiker zijn opgegeven. Deze eigenschap is optioneel en kan niet worden opgenomen.                            |
| additionalInfo | tekenreeksmatrix | Nee       | Aanvullende gegevens voor een Azure-resource. Deze eigenschap is optioneel en kan niet worden opgenomen.                          |