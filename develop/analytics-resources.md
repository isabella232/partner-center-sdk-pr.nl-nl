---
title: Analytics-resources
description: Partner Center resources bevatten gegevens over gebruik, implementatie en verbruik. Bevat inzichten over de implementatie en het gebruik van licenties door partners en klanten.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: v-sumukh
ms.author: v-sumukh
ms.openlocfilehash: fc665e8e4468648f71f242992780fbc66a02522a0b8b957a5ce68147ab33eaac
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115993194"
---
# <a name="analytics-api-resources-that-help-you-report-on-license-usage-deployment-and-consumption"></a>Analyse-API-resources die u helpen bij het rapporteren over licentiegebruik, implementatie en verbruik

De hier gedefinieerde resources bevatten gegevens die worden gebruikt om te rapporteren over gebruik, implementatie en verbruik.

## <a name="partnerlicensesdeploymentinsights"></a>PartnerLicensesDeploymentInsights

De **resource PartnerLicensesDeploymentInsights** bevat inzichten op partnerniveau over de implementatie van licenties.

| Eigenschap                  | Type                                                           | Description                                                                         |
|---------------------------|----------------------------------------------------------------|-------------------------------------------------------------------------------------|
| proratedDeploymentPercent | getal                                                         | Het percentage geïmplementeerde licenties.                                                |
| licentiesVerkocht              | getal                                                         | Het aantal verkochte licenties.                                                        |
| processedDateTime         | tekenreeks in UTC-datum/tijd-indeling                                 | De datum en tijd waarop de gegevens zijn geaggregeerd.                                     |
| Servicenaam               | tekenreeks                                                         | De servicenaam (bijvoorbeeld: o365, crm).                                                  |
| Kanaal                   | tekenreeks                                                         | De kanaalnaam van de service (bijvoorbeeld reseller).                                    |
| kenmerken                | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken. Bevat 'objectType': 'PartnerLicensesDeploymentInsights' |

## <a name="partnerlicensesusageinsights"></a>PartnerLicensesUsageInsights

De **resource PartnerLicensesUsageInsights** bevat inzichten op partnerniveau over licentiegebruik.

| Eigenschap                     | Type                                                           | Description                                                                    |
|------------------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------|
| proratedLicensesUsagePercent | getal                                                         | Het percentage geïmplementeerde licenties.                                           |
| workloadName                 | tekenreeks                                                         | De naam van de workload (bijvoorbeeld exchange).                                             |
| processedDateTime            | tekenreeks in UTC-datum/tijd-indeling                                 | De datum en tijd waarop de gegevens zijn geaggregeerd.                                |
| Servicenaam                  | tekenreeks                                                         | De servicenaam (bijvoorbeeld: o365, crm).                                             |
| Kanaal                      | tekenreeks                                                         | De kanaalnaam van de service (bijvoorbeeld reseller).                               |
| kenmerken                   | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken. Bevat 'objectType': 'PartnerLicensesUsageInsights' |

## <a name="customerlicensesdeploymentinsights"></a>CustomerLicensesDeploymentInsights

De **resource CustomerLicensesDeploymentInsights** bevat inzichten op klantniveau over de implementatie van licenties.

| Eigenschap          | Type                                                           | Description                                                                          |
|-------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| licenties Geïmplementeerd  | getal                                                         | Het aantal geïmplementeerde licenties.                                                     |
| licentiesVerkocht      | getal                                                         | Het aantal verkochte licenties.                                                         |
| deploymentPercent | getal                                                         | Het aangepaste percentage geïmplementeerde licenties.                                        |
| customerId        | tekenreeks                                                         | De klant-id.                                                             |
| customerName      | tekenreeks                                                         | De naam van de klant.                                                                   |
| Productnaam       | tekenreeks                                                         | De productnaam.                                                                    |
| serviceCode       | tekenreeks                                                         | De servicecode van de licentie.                                                     |
| processedDateTime | tekenreeks in UTC-datum/tijd-indeling                                 | De datum en tijd waarop de gegevens zijn geaggregeerd.                                      |
| Servicenaam       | tekenreeks                                                         | De servicenaam (bijvoorbeeld: o365, crm).                                                   |
| Kanaal           | tekenreeks                                                         | De kanaalnaam van de service (bijvoorbeeld reseller).                                     |
| kenmerken        | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken. Bevat 'objectType': 'CustomerLicensesDeploymentInsights' |

## <a name="customerlicensesusageinsights"></a>CustomerLicensesUsageInsights

De **resource CustomerLicensesUsageInsights** bevat inzichten op klantniveau over licentiegebruik.

| Eigenschap          | Type                                                           | Description                                                                     |
|-------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| workloadCode      | tekenreeks                                                         | De workloadcode.                                                              |
| workloadName      | getal                                                         | De naam van de workload (bijvoorbeeld: Exchange).                                              |
| usagePercent      | getal                                                         | Het aangepaste percentage gebruikte licenties.                                       |
| licensesActive    | getal                                                         | Het aantal actieve licenties.                                                  |
| licensesQualified | getal                                                         | Het aantal gekwalificeerde licenties.                                               |
| customerId        | tekenreeks                                                         | De klant-id.                                                        |
| customerName      | tekenreeks                                                         | De naam van de klant.                                                              |
| Productnaam       | tekenreeks                                                         | De productnaam.                                                               |
| serviceCode       | tekenreeks                                                         | De servicecode van de licentie.                                                |
| processedDateTime | tekenreeks in UTC-datum/tijd-indeling                                 | De datum en tijd waarop de gegevens zijn geaggregeerd.                                 |
| Servicenaam       | tekenreeks                                                         | De servicenaam (bijvoorbeeld: o365, crm).                                              |
| Kanaal           | tekenreeks                                                         | De kanaalnaam van de service (bijvoorbeeld reseller).                                |
| kenmerken        | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken. Bevat 'objectType': 'CustomerLicensesUsageInsights' |