---
title: Resources voor servicekosten
description: Beschrijft resources met betrekking tot services die zijn gekocht door een klant.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8c1e3a05be89eee12d708a3a37e008ec7fa42358eaec7e1f020aaa47e44b452c
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996135"
---
# <a name="service-costs-resources"></a>Resources voor servicekosten

Beschrijft resources met betrekking tot services die zijn gekocht door een klant.

## <a name="servicecostssummary"></a>ServiceCostsSummary

**ServiceCostsSummary** bevat een samenvatting waarin alle services worden geaggregeerd die tijdens de factureringsperiode zijn gekocht door de opgegeven klant.

| Eigenschap | Type | Description |
| -------- | ---- | ----------- |
| Details | matrix van [ServiceCostsSummaryDetail-objecten](#servicecostssummarydetail) | De overzichtslijst met servicekosten, onderscheiden op factuurtype.|
| Verwijzigingen | [ResourceLinks](utility-resources.md#resourcelinks) | De resourcekoppelingen. |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken. |

> [!IMPORTANT]
> **De velden in de volgende tabel worden afgeschaft.** Als u terugkerende en eenmalige samenvattingen van servicekosten wilt ophalen, gebruikt u in **plaats daarvan het veld Details.** Het **detailveld** wordt beschreven in de vorige tabel. Raadpleeg de **bijbehorende gegevenswaarden** van het detailveld, maar niet de velden op hoofdniveau.

| Eigenschap | Type | Description |
| -------- | ---- | ----------- |
| billingStartDate | date | Het begin van de factureringsperiode. |
| billingEndDate | date | Het einde van de factureringsperiode. |
| pretaxTotal | double | Het totaal vóór belasting van alle kosten voor de klant. |
| Belasting  | double | De totale belasting die wordt gemaakt voor alle items die door de klant zijn gekocht. |
| afterTaxTotal | double | De netto totale kosten voor alle items die door de klant zijn gekocht. |
| currencyCode | tekenreeks | Vertegenwoordigt de valuta die wordt gebruikt voor de kosten. |
| currencySymbol | tekenreeks | Het valutasymbool dat wordt gebruikt voor de kosten. |
| customerId | tekenreeks | De id van de klant die de aankoop heeft gedaan. |

## <a name="servicecostssummarydetail"></a>ServiceCostsSummaryDetail

**ServiceCostsSummaryDetail** beschrijft een overzicht van servicekosten waarin alle services worden geaggregeerd die tijdens de factureringsperiode zijn gekocht door de opgegeven klant (van terugkerende of eenmalige facturen).

| Eigenschap | Type | Description |
| -------- | ---- | ----------- |
| invoiceType | tekenreeks | Het invoiceType dat servicekostenoverzicht is gegenereerd. |
| samenvatting | [ServiceCostsSummary](#servicecostssummary) | Het overzicht van servicekosten, geaggregeerd door een klant onder één factuurtype. |

## <a name="servicecostlineitem"></a>ServiceCostLineItem

**ServiceCostLineItem beschrijft** één item dat door de klant is gekocht.

> [!IMPORTANT]
> De volgende  eigenschappen zijn alleen van toepassing op servicekostenregelitems waarbij het product een een *time-aankoop* is: **productId**, **productName**, **skuId**, **skuName**, **availabilityId**, **publisherId**, **publisherName**, **termAndBillingCycle**, **discountDetails**. Deze eigenschappen *zijn niet van toepassing op* serviceregelitems waarbij het product een terugkerende aankoop *is.* Deze eigenschappen zijn bijvoorbeeld *niet van toepassing op* abonnementsgebaseerde Office 365 en Azure.

| Eigenschap                 | Type                           | Description                                                          |
|--------------------------|--------------------------------|----------------------------------------------------------------------|
| Startdate                | tekenreeks in UTC-datum/tijd-indeling | De begindatum voor de kosten.                                       |
| Enddate                  | tekenreeks in UTC-datum/tijd-indeling | De einddatum voor de kosten.                                         |
| subscriptionFriendlyName | tekenreeks                         | De gebruiksvriendelijke naam voor het abonnement.                              |
| subscriptionId           | tekenreeks                         | De abonnements-id.                                         |
| Orderid                  | tekenreeks                         | De order-id.                                                |
| offerId                  | tekenreeks                         | De aanbiedings-id.                                                |
| offerName                | tekenreeks                         | De naam van de aanbieding.                                                      |
| resellerMPNId            | tekenreeks                         | Alleen gebruikt in partnerscenario's met twee lagen. Verwijst naar de MPN-id. |
| chargeType               | tekenreeks                         | Het bijbehorende kostentype.                                          |
| quantity                 | getal                         | Het aantal gebruikte of aangeschafte eenheden.                             |
| unitPrice                | getal                         | De prijs per eenheid.                                                  |
| pretaxTotal              | getal                         | De totale kosten voor dit item vóór belastingen.                         |
| Belasting                      | getal                         | De totale btw-kosten voor dit item.                         |
| afterTaxTotal            | getal                         | De netto totale kosten voor dit item.                                    |
| currencyCode             | tekenreeks                         | Vertegenwoordigt de valuta die wordt gebruikt voor de kosten.                          |
| currencySymbol           | tekenreeks                         | Het valutasymbool dat wordt gebruikt voor de kosten.                              |
| customerId               | tekenreeks                         | De id van de klant die de aankoop heeft gedaan.                          |
| customerName             | tekenreeks                         | De naam van de klant die de aankoop doet.                        |
| invoiceNumber            | tekenreeks                         | Het factuurnummer waar dit regelitem bij hoort.                   |
| productId                | tekenreeks                         | De product-id.                                              |
| skuId                    | tekenreeks                         | De SKU-id.                                                  |
| availabilityId           | tekenreeks                         | De beschikbaarheids-id.                                         |
| Productnaam              | tekenreeks                         | De productnaam.                                                    |
| skuName                  | tekenreeks                         | De naam van de SKU.                                                        |
| publisherName            | tekenreeks                         | De naam van de uitgever.                                                  |
| publisherId              | tekenreeks                         | De uitgever-id.                                            |
| termAndBillingCycle      | tekenreeks                         | De periode en factureringscyclus.                                          |
| discountDetails          | tekenreeks                         | De kortingsdetails.                                                |

## <a name="servicecostssummarylinks"></a>ServiceCostsSummaryLinks

| Eigenschap             | Type                               | Description                         |
|----------------------|------------------------------------|-------------------------------------|
| serviceCostLineItems | [Koppeling](utility-resources.md#link) | De URI voor het ophalen van de regelitems. |
| Zelf                 | [Koppeling](utility-resources.md#link) | De zelf-URI.                       |
