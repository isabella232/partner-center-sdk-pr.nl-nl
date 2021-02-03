---
title: Service kosten resources
description: Hierin worden de resources beschreven die zijn gerelateerd aan services die door een klant zijn gekocht.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c0236329d93d8ddc9019a15fb67a81a3af3e7620
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767327"
---
# <a name="service-costs-resources"></a>Service kosten resources

**Van toepassing op:**

- Partnercentrum

Hierin worden de resources beschreven die zijn gerelateerd aan services die door een klant zijn gekocht.

## <a name="servicecostssummary"></a>ServiceCostsSummary

**ServiceCostsSummary** bevat een samen vatting waarin alle services die door de opgegeven klant zijn gekocht tijdens de facturerings periode, worden geaggregeerd.

| Eigenschap | Type | Description |
| -------- | ---- | ----------- |
| nadere | matrix van [ServiceCostsSummaryDetail](#servicecostssummarydetail) -objecten | De lijst met samenvattings gegevens voor service kosten, onderscheiden per factuur type.|
| koppelen | [ResourceLinks](utility-resources.md#resourcelinks) | De resource koppelingen. |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken. |

> [!IMPORTANT]
> **De velden in de volgende tabel worden afgeschaft.** Als u terugkerende en eenmalige service kosten samen vattingen wilt ophalen, gebruikt u in plaats daarvan het veld **Details** . Het veld **Details** wordt beschreven in de vorige tabel. Raadpleeg de bijbehorende gegevens waarden van het veld **Details** , maar niet van de velden op het hoofd niveau.

| Eigenschap | Type | Description |
| -------- | ---- | ----------- |
| billingStartDate | date | Het begin van de facturerings periode. |
| billingEndDate | date | Het einde van de facturerings periode. |
| pretaxTotal | double | Het totaal van de kosten voor de klant. |
| belasting  | double | De totale belasting die is gemaakt voor alle items die de klant heeft gekocht. |
| afterTaxTotal | double | De netto totale kosten voor alle items die door de klant zijn gekocht. |
| currencyCode | tekenreeks | Hiermee wordt de valuta aangegeven die wordt gebruikt voor de kosten. |
| currencySymbol | tekenreeks | Het valuta symbool dat wordt gebruikt voor de kosten. |
| customerId | tekenreeks | De ID van de klant die de aankoop doet. |

## <a name="servicecostssummarydetail"></a>ServiceCostsSummaryDetail

In **ServiceCostsSummaryDetail** wordt een samen vatting van service kosten beschreven waarmee alle services die door de opgegeven klant zijn gekocht tijdens de facturerings periode, worden geaggregeerd (vanuit terugkerende of eenmalige facturen).

| Eigenschap | Type | Description |
| -------- | ---- | ----------- |
| invoiceType | tekenreeks | De invoiceType waarvoor een service kosten overzicht is gegenereerd. |
| samenvatting | [ServiceCostsSummary](#servicecostssummary) | Het overzicht van service kosten dat is geaggregeerd door een klant onder één factuur type. |

## <a name="servicecostlineitem"></a>ServiceCostLineItem

**ServiceCostLineItem** beschrijft een enkel item dat door de klant is gekocht.

> [!IMPORTANT]
> De volgende eigenschappen *gelden alleen voor* service kosten regel items waarbij het product een *eenmalige aankoop* is: **ProductID**, **productName**, **skuId**, **skuName**, **availabilityId**, **publisherId**, naam **Uitgever**, **termAndBillingCycle**, **discountDetails**. Deze eigenschappen *zijn niet van toepassing op* service regel items waarbij het product een *terugkerende aankoop* is. Deze eigenschappen *zijn bijvoorbeeld niet van toepassing* op op abonnementen gebaseerde Office 365 en Azure.

| Eigenschap                 | Type                           | Description                                                          |
|--------------------------|--------------------------------|----------------------------------------------------------------------|
| Begin                | teken reeks in UTC-datum-tijd notatie | De begin datum voor de kosten.                                       |
| endDate                  | teken reeks in UTC-datum-tijd notatie | De eind datum voor de kosten.                                         |
| subscriptionFriendlyName | tekenreeks                         | De beschrijvende naam voor het abonnement.                              |
| subscriptionId           | tekenreeks                         | De abonnements-id.                                         |
| Velden                  | tekenreeks                         | De order-id.                                                |
| offerId                  | tekenreeks                         | De aanbiedings-id.                                                |
| offerName                | tekenreeks                         | De naam van de aanbieding.                                                      |
| resellerMPNId            | tekenreeks                         | Wordt alleen gebruikt in scenario's met twee lagen. Verwijst naar de MPN-id. |
| chargeType               | tekenreeks                         | Het gekoppelde kosten type.                                          |
| quantity                 | getal                         | Het aantal gebruikte eenheden of de aangeschafte hoeveelheid.                             |
| unitPrice                | getal                         | De prijs per eenheid.                                                  |
| pretaxTotal              | getal                         | De totale kosten voor dit item vóór belastingen.                         |
| belasting                      | getal                         | De totale belasting kosten voor dit artikel.                         |
| afterTaxTotal            | getal                         | De totale kosten voor dit item in het netwerk.                                    |
| currencyCode             | tekenreeks                         | Hiermee wordt de valuta aangegeven die wordt gebruikt voor de kosten.                          |
| currencySymbol           | tekenreeks                         | Het valuta symbool dat wordt gebruikt voor de kosten.                              |
| customerId               | tekenreeks                         | De ID van de klant die de aankoop doet.                          |
| customerName             | tekenreeks                         | De naam van de klant die de aankoop maakt.                        |
| invoiceNumber            | tekenreeks                         | Het factuur nummer waarvan dit regel item deel uitmaakt.                   |
| productId                | tekenreeks                         | De product-id.                                              |
| skuId                    | tekenreeks                         | De SKU-id.                                                  |
| availabilityId           | tekenreeks                         | De beschikbaarheids identificatie.                                         |
| Product              | tekenreeks                         | De product naam.                                                    |
| skuName                  | tekenreeks                         | De naam van de SKU.                                                        |
| publisherName            | tekenreeks                         | De naam van de uitgever.                                                  |
| publisherId              | tekenreeks                         | De uitgevers-id.                                            |
| termAndBillingCycle      | tekenreeks                         | De term en facturerings cyclus.                                          |
| discountDetails          | tekenreeks                         | De kortings gegevens.                                                |

## <a name="servicecostssummarylinks"></a>ServiceCostsSummaryLinks

| Eigenschap             | Type                               | Description                         |
|----------------------|------------------------------------|-------------------------------------|
| serviceCostLineItems | [Koppeling](utility-resources.md#link) | De URI voor het ophalen van de regel items. |
| Online                 | [Koppeling](utility-resources.md#link) | De zelf-URI.                       |
