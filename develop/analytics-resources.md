---
title: Analyse bronnen
description: Partner Center-bronnen bevatten gegevens over gebruik, implementatie en verbruik. Bevat inzichten over de implementatie en het gebruik van licenties door partners en klanten.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: v-sumukh
ms.author: v-sumukh
ms.openlocfilehash: 9bd47b99f0abaa181e5f255dd6e46151363917e7
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767595"
---
# <a name="analytics-api-resources-that-help-you-report-on-license-usage-deployment-and-consumption"></a>Analytische API-bronnen waarmee u kunt rapporteren over het gebruik van licenties, implementatie en verbruik

**Van toepassing op:**

- Partnercentrum

De hier gedefinieerde resources bevatten gegevens die worden gebruikt voor rapportage over gebruik, implementatie en verbruik.

## <a name="partnerlicensesdeploymentinsights"></a>PartnerLicensesDeploymentInsights

De **PartnerLicensesDeploymentInsights** -resource bevat inzichten op partner niveau over licentie-implementatie.

| Eigenschap                  | Type                                                           | Description                                                                         |
|---------------------------|----------------------------------------------------------------|-------------------------------------------------------------------------------------|
| proratedDeploymentPercent | getal                                                         | Het percentage geïmplementeerde licenties.                                                |
| licensesSold              | getal                                                         | Het aantal verkochte licenties.                                                        |
| processedDateTime         | teken reeks in UTC-datum-tijd notatie                                 | De datum en tijd waarop de gegevens zijn samengevoegd.                                     |
| serviceName               | tekenreeks                                                         | De naam van de service (bijvoorbeeld: o365, CRM).                                                  |
| kanalen                   | tekenreeks                                                         | De kanaal naam van de service (bijvoorbeeld: reseller).                                    |
| kenmerken                | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken. Bevat "object type": "PartnerLicensesDeploymentInsights" |

## <a name="partnerlicensesusageinsights"></a>PartnerLicensesUsageInsights

De **PartnerLicensesUsageInsights** -resource bevat inzichten op partner niveau over het gebruik van licenties.

| Eigenschap                     | Type                                                           | Description                                                                    |
|------------------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------|
| proratedLicensesUsagePercent | getal                                                         | Het percentage geïmplementeerde licenties.                                           |
| workload                 | tekenreeks                                                         | De naam van de werk belasting (bijvoorbeeld: Exchange).                                             |
| processedDateTime            | teken reeks in UTC-datum-tijd notatie                                 | De datum en tijd waarop de gegevens zijn samengevoegd.                                |
| serviceName                  | tekenreeks                                                         | De naam van de service (bijvoorbeeld: o365, CRM).                                             |
| kanalen                      | tekenreeks                                                         | De kanaal naam van de service (bijvoorbeeld: reseller).                               |
| kenmerken                   | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken. Bevat "object type": "PartnerLicensesUsageInsights" |

## <a name="customerlicensesdeploymentinsights"></a>CustomerLicensesDeploymentInsights

De **CustomerLicensesDeploymentInsights** -resource bevat inzichten op klant niveau over licentie-implementatie.

| Eigenschap          | Type                                                           | Description                                                                          |
|-------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| licensesDeployed  | getal                                                         | Het aantal geïmplementeerde licenties.                                                     |
| licensesSold      | getal                                                         | Het aantal verkochte licenties.                                                         |
| deploymentPercent | getal                                                         | Het aangepaste percentage geïmplementeerde licenties.                                        |
| customerId        | tekenreeks                                                         | De klant-id.                                                             |
| customerName      | tekenreeks                                                         | De naam van de klant.                                                                   |
| Product       | tekenreeks                                                         | De product naam.                                                                    |
| serviceCode       | tekenreeks                                                         | De service code van de licentie.                                                     |
| processedDateTime | teken reeks in UTC-datum-tijd notatie                                 | De datum en tijd waarop de gegevens zijn samengevoegd.                                      |
| serviceName       | tekenreeks                                                         | De naam van de service (bijvoorbeeld: o365, CRM).                                                   |
| kanalen           | tekenreeks                                                         | De kanaal naam van de service (bijvoorbeeld: reseller).                                     |
| kenmerken        | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken. Bevat "object type": "CustomerLicensesDeploymentInsights" |

## <a name="customerlicensesusageinsights"></a>CustomerLicensesUsageInsights

De **CustomerLicensesUsageInsights** -resource bevat inzichten op klant niveau over het gebruik van licenties.

| Eigenschap          | Type                                                           | Description                                                                     |
|-------------------|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| workloadCode      | tekenreeks                                                         | De werkbelasting code.                                                              |
| workload      | getal                                                         | De naam van de werk belasting (bijvoorbeeld: Exchange).                                              |
| usagePercent      | getal                                                         | Het aangepaste percentage gebruikte licenties.                                       |
| licensesActive    | getal                                                         | Het aantal actieve licenties.                                                  |
| licensesQualified | getal                                                         | Het aantal gekwalificeerde licenties.                                               |
| customerId        | tekenreeks                                                         | De klant-id.                                                        |
| customerName      | tekenreeks                                                         | De naam van de klant.                                                              |
| Product       | tekenreeks                                                         | De product naam.                                                               |
| serviceCode       | tekenreeks                                                         | De service code van de licentie.                                                |
| processedDateTime | teken reeks in UTC-datum-tijd notatie                                 | De datum en tijd waarop de gegevens zijn samengevoegd.                                 |
| serviceName       | tekenreeks                                                         | De naam van de service (bijvoorbeeld: o365, CRM).                                              |
| kanalen           | tekenreeks                                                         | De kanaal naam van de service (bijvoorbeeld: reseller).                                |
| kenmerken        | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken. Bevat "object type": "CustomerLicensesUsageInsights" |