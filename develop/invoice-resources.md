---
title: Factuurbronnen
description: Er zijn meerdere factuurresources beschikbaar via de Partner Center API's. Deze resources zijn gerelateerd aan factuur- en regelitemgegevens.
ms.date: 01/27/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d2e801dc3b082411e140b88cd495807b1381ef915e8f5f06803d64ca2cca1c6b
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996543"
---
# <a name="invoice-resources"></a>Factuurbronnen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De volgende factuurresources zijn beschikbaar via de Partner Center API's.

## <a name="invoice"></a>Factuur

| Eigenschap | Type | Beschrijving |
| -------- | ---- | ----------- |
| id | tekenreeks | De factuur-id. |
| invoiceDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de factuur is gegenereerd. |
| billingPeriodStartDate | tekenreeks in UTC-datum/tijd-indeling | Begindatum factureringsperiode in UTC. |
| billingPeriodEndDate | tekenreeks in UTC-datum/tijd-indeling   | Einddatum van factureringsperiode in UTC. |
| totalCharges | getal | De totale kosten. Omvat kosten voor transacties en eventuele aanpassingen.     |
| paidAmount | getal  | Het bedrag dat is betaald door de partner. Negatief als er een betaling is ontvangen.  |
| currencyCode | tekenreeks  | Een code die de valuta aangeeft die wordt gebruikt voor alle factuuritembedragen en totalen. |
| currencySymbol  | tekenreeks | Het valutasymbool dat wordt gebruikt voor alle factuuritembedragen en totalen. |
| pdfDownloadLink | tekenreeks  | Een koppeling om de factuur in PDF-indeling te downloaden. Deze koppeling wordt niet geretourneerd als onderdeel van de zoekresultaten en wordt alleen ingevuld als de factuur wordt gebruikt op id. Deze koppeling verloopt automatisch binnen 30 minuten. |
| invoiceDetails  | matrix van [InvoiceDetail-objecten](#invoicedetail)  | De factuurgegevens.  |
| Amendementen      | matrix met [factuurobjecten](#invoice)   | De wijzigingen in deze factuur.  |
| documentType    | tekenreeks | Het documenttype van de factuur: "Tegoednota", "Factuur". |
| wijzigtOf        | tekenreeks | Het referentienummer van het document waarvan dit document een wijziging is.  |
| invoiceType     | tekenreeks  | Het type factuur: "recurring", "one \_ time".   |
| Verwijzigingen           | [ResourceLinks](utility-resources.md#resourcelinks)  | De resourcekoppelingen.  |
| kenmerken      | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.  |

## <a name="invoicedetail"></a>InvoiceDetail

Een factuur bevat een verzameling gefactureerde items en elk item wordt vertegenwoordigd door een InvoiceDetail-resource.

| Eigenschap            | Type                                                           | Description                                                                       |
|---------------------|----------------------------------------------------------------|-----------------------------------------------------------------------------------|
| invoiceLineItemType | tekenreeks                                                         | Het type factuurgegevens: 'geen', \_ \_ 'gebruiksregelitems', \_ 'factureringsregelitems'. \_ |
| billingProvider     | tekenreeks                                                         | De factureringsprovider: 'none', 'office', 'azure' of 'azure \_ data \_ market'.         |
| Verwijzigingen               | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen.                                                               |
| kenmerken          | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                                                          |

## <a name="invoicelineitem"></a>InvoiceLineItem

Elke afzonderlijke kosten in een factuur worden weergegeven als een InvoiceLineItem.

| Eigenschap            | Type                                                           | Description                                                                          |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| invoiceLineItemType | tekenreeks                                                         | Het type factuurregelitem: 'geen', \_ \_ 'gebruiksregelitems', \_ 'factureringsregelitems'. \_ |
| billingProvider     | tekenreeks                                                         | De factureringsprovider: 'none', 'office', 'azure' of 'azure \_ data \_ market'.            |
| kenmerken          | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken.                                                             |

## <a name="invoicesummary"></a>InvoiceSummary

Beschrijft een overzicht van het saldo en de totale kosten van een factuur.

| Eigenschap                 | Type                                                           | Description                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| balanceAmount            | getal                                                         | Het saldo van de factuur. Dit is het totale bedrag aan niet-betaalde facturen. |
| currencyCode             | tekenreeks                                                         | Een code die de valuta aangeeft die wordt gebruikt voor het saldo.       |
| currencySymbol           | tekenreeks                                                         | Het valutasymbool dat wordt gebruikt.                                             |
| accountingDate           | tekenreeks in UTC-datum/tijd-indeling                                 | De datum waarop het saldo voor het laatst is bijgewerkt.                         |
| firstInvoiceCreationDate | tekenreeks in UTC-datum/tijd-indeling                                 | De datum waarop de eerste factuur voor de klant is gemaakt.              |
| lastPaymentDate          | tekenreeks in UTC-datum/tijd-indeling                                 | De datum van de laatste betaling.                                         |
| lastPaymentAmount        | getal                                                         | Het bedrag van de laatste betaling.                                       |
| latestInvoiceDate        | tekenreeks in UTC-datum/tijd-indeling                                 | De datum waarop de laatste factuur voor de klant is gemaakt.               |
| Details                  | matrix van [InvoiceSummaryDetail-objecten](#invoicesummarydetail) | De details van het factuuroverzicht.                                           |
| Verwijzigingen                    | [ResourceLinks](utility-resources.md#resourcelinks)            | De resourcekoppelingen.                                                   |
| kenmerken               | [ResourceAttributes](utility-resources.md#resourceattributes)  | De metagegevenskenmerken.                                              |

## <a name="invoicesummarydetail"></a>InvoiceSummaryDetail

Vertegenwoordigen een samenvatting van de afzonderlijke gegevens voor een factuurtype (bijvoorbeeld terugkerend, één \_ keer).

| Eigenschap            | Type                                                           | Description                                                                          |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| invoiceType         | tekenreeks                                                         | Het type factuur: 'terugkerend', 'één \_ keer'.                                       |
| samenvatting             | [Object InvoiceSummary](#invoicesummary)                       | Het overzicht van de factuur per factuurtype.                                         |

## <a name="invoicesummaries"></a>InvoiceSummaries

Vertegenwoordigen een verzameling van het type [InvoiceSummary](#invoicesummary) die de afzonderlijke details voor een factuurtype per valuta bevat.

| Eigenschap            | Type                                                           | Description                                                                          |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| collectionOfSummary | matrix van [InvoiceSummary-objecten](#invoicesummary)             | Het overzicht van de factuur per factuurtype per valuta.                            |

## <a name="licensebasedlineitem"></a>LicenseBasedLineItem

Vertegenwoordigt een factuurfactureringsregelitem voor gelicentieerde abonnementen.

| Eigenschap                 | Type                                                           | Description                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| bedrag                   | tekenreeks                                                         | Hiermee haalt u het totale bedrag op of stelt u dit in. Totaal bedrag = eenheidsprijs * hoeveelheid.  |
| kenmerken               | tekenreeks                                                         | Haalt de kenmerken op.                                                  |
| billingCycleType         | tekenreeks                                                         | Hiermee haalt u het type factureringscyclus op of stelt u dit in.                                  |
| billingProvider          | tekenreeks                                                         | Haalt de factureringsprovider op.                                            |
| chargeEndDate            | tekenreeks in UTC-datum/tijd-indeling                                 | Hiermee haalt u de einddatum voor de kosten op of stelt u deze in.                             |
| chargeStartDate          | tekenreeks in UTC-datum/tijd-indeling                                 | Hiermee haalt u de begindatum voor de kosten op of stelt u deze in.                           |
| chargeType               | tekenreeks                                                         | Hiermee haalt u het type kosten op of stelt u dit in.                                      |
| currency                 | tekenreeks                                                         | Hiermee haalt u de valuta op die wordt gebruikt voor dit regelitem of stelt u deze in.                    |
| customerId               | tekenreeks                                                         | Hiermee wordt de unieke id van de klant in het Microsoft-factureringsplatform op of stelt u deze in.  |
| customerName             | tekenreeks in UTC-datum/tijd-indeling                                 | Hiermee haalt u de naam van de klant op of stelt u deze in.                                       |
| domainName               | tekenreeks                                                         | Hiermee haalt u de domeinnaam op of stelt u deze in.                                             |
| durableOfferId           | tekenreeks                                                         | Hiermee haalt u de unieke id van de Duurzame aanbieding op of stelt u deze in.                     |
| invoiceLineItemType      | tekenreeks                                                         | Haalt het type factuurregelitem op.                                   |
| mpnId                    | getal                                                         | Hiermee haalt u de MPN-id op die aan dit regelitem is gekoppeld of stelt u deze in. Voor directe resellers is dit de MPN-id van de reseller. Voor indirecte resellers is dit de MPN-id van de Value Added Reseller (VAR).                                   |
| offerId                  | tekenreeks                                                         | Hiermee haalt u de unieke id van de aanbieding op of stelt u deze in.                             |
| offerName                | tekenreeks                                                         | Hiermee haalt u de naam van de aanbieding op of stelt u deze in.                                          |
| Orderid                  | tekenreeks                                                         | Hiermee haalt u de unieke id van de bestelling op of stelt u deze in.                             |
| partnerId                | tekenreeks                                                         | Hiermee haalt u de tenant-id van de Azure Active Directory-partner op of stelt u deze in.            |
| quantity                 | getal                                                         | Hiermee haalt of stelt u het aantal eenheden dat is gekoppeld aan dit regelitem.      |
| subscriptionDescription  | tekenreeks                                                         | Hiermee haalt u de beschrijving van het abonnement op of stelt u deze in.                            |
| subscriptionEndDate      | tekenreeks in UTC-datum/tijd-indeling                                 | Hiermee wordt de datum waarop het abonnement verloopt, op halen of in een abonnement in stellen.                      |
| subscriptionId           | tekenreeks                                                         | Hiermee haalt u de unieke id van het abonnement op of stelt u deze in.                      |
| subscriptionName         | tekenreeks                                                         | Hiermee haalt u de naam van het abonnement op of stelt u deze in.                                   |
| subscriptionStartDate    | tekenreeks in UTC-datum/tijd-indeling                                 | Hiermee haalt u de datum op waarop het abonnement wordt gestart of stelt u deze in.                   |
| Subtotaal                 | getal                                                         | Haalt het bedrag op of stelt het in na korting.                               |
| syndicationPartnerSubscriptionNumber | tekenreeks                                             | Hiermee wordt het abonnementsnummer van de syndicatiepartner op halen ofsets.             |
| Belasting                      | getal                                                         | Hiermee worden de in rekening gebrachte belastingen in rekening gebracht of in rekening gebracht.                                       |
| tier2MpnId               | getal                                                         | Hiermee wordt de MPN-id van de Laag 2-partner die aan dit regelitem is gekoppeld, of deze id in of stelt deze in. |
| totalForCustomer         | getal                                                         | Haalt het totale bedrag op na korting en belasting of stelt het in.                 |
| totalOtherDiscount       | getal                                                         | Hiermee wordt de korting die aan deze aankoop is gekoppeld, ontvangen of stelt.              |
| unitPrice                | getal                                                         | Hiermee haalt u de eenheidsprijs op of stelt u deze in.                                          |

## <a name="usagebasedlineitem"></a>UsageBasedLineItem

Vertegenwoordigt een factuurfactureringsregelitem voor abonnementen op basis van gebruik.

| Eigenschap                 | Type                                                           | Description                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| kenmerken               | tekenreeks                                                         | Haalt de kenmerken op.                                                  |
| billingCycleType         | tekenreeks                                                         | Hiermee haalt u het type factureringscyclus op of stelt u dit in.                                  |
| billingProvider          | tekenreeks                                                         | Haalt de factureringsprovider op.                                            |
| chargeEndDate            | tekenreeks in UTC-datum/tijd-indeling                                 | Hiermee haalt u de einddatum voor de kosten op of stelt u deze in.                             |
| chargeStartDate          | tekenreeks in UTC-datum/tijd-indeling                                 | Hiermee haalt u de begindatum voor de kosten op of stelt u deze in.                           |
| chargeType               | tekenreeks                                                         | Hiermee haalt u het type kosten op of stelt u dit in.                                      |
| consumedQuantity         | getal                                                         | Haalt het totale aantal verbruikte eenheden op of stelt deze in.                                |
| consumptionDiscount      | tekenreeks                                                         | Hiermee wordt de korting op het verbruik ontvangen of stelt u deze in.                             |
| consumptionPrice         | tekenreeks                                                         | Hiermee wordt de prijs van de verbruikte hoeveelheid opgeslagen of stelt deze in.                          |
| currency                 | tekenreeks                                                         | Hiermee haalt u de valuta op die is gekoppeld aan de prijzen of stelt u deze in.                 |
| customerName             | tekenreeks                                                         | Hiermee haalt u de naam van de klant op of stelt u deze in.                                       |
| customerId               | tekenreeks                                                         | Hiermee haalt u de unieke klant-id op of stelt u deze in.                          |
| detailLineItemId         | getal                                                         | Hiermee haalt u de detailregelitem-id op of stelt u deze in. Hiermee worden de regelitems uniek geïdentificeerd voor gevallen waarin de berekening verschilt voor verbruikte eenheden. Voorbeeld: Totaal verbruikt = 1338, 1024 wordt in rekening gebracht met één tarief, 314 wordt in rekening gebracht met een ander tarief.        |
| domainName               | tekenreeks                                                         | Hiermee haalt u de domeinnaam op of stelt u deze in.                                             |
| includedQuantity         | getal                                                         | Hiermee haalt u de eenheden op die zijn opgenomen in de volgorde of stelt u deze in.                         |
| invoiceLineItemType      | tekenreeks                                                         | Haalt het type factuurregelitem op.                                   |
| invoiceNumber            | tekenreeks                                                         | Hiermee haalt u het factuurnummer op of stelt u dit in.                                      |
| listPrice                | getal                                                         | Hiermee haalt u de prijs van elke eenheid op of stelt u deze in.                                  |
| mpnId                    | getal                                                         | Hiermee haalt u de MPN-id op die is gekoppeld aan dit regelitem of stelt u deze in. Voor directe resellers is dit de MPN-id van de reseller. Voor indirecte resellers is dit de MPN-id van de Value Added Reseller (VAR).                                   |
| Orderid                  | tekenreeks                                                         | Hiermee wordt de unieke id van de bestelling of de unieke id van de bestelling.                             |
| overageQuantity          | getal                                                         | Hiermee wordt de hoeveelheid die boven het toegestane gebruik is verbruikt, opgeslagen of stelt u deze in.               |
| partnerBillableAccountId | tekenreeks                                                         | Hiermee haalt u de factureerbare account-id van de partner op of stelt u deze in.                         |
| partnerId                | tekenreeks                                                         | Hiermee haalt u de tenant-id van de Azure Active Directory-partner op of stelt u deze in.            |
| partnerName              | tekenreeks                                                         | Hiermee haalt u de naam van de partner op of stelt u deze in.                                      |
| postTaxEffectiveRate     | getal                                                         | Haalt de effectieve prijs op of stelt deze in na belastingen.                         |
| postTaxTotal             | getal                                                         | Hiermee worden de totale kosten na belasting in rekening gebracht of in rekening gebracht. Kosten vóór belasting + btw-bedrag |
| preTaxCharges            | getal                                                         | Hiermee wordt de prijs in rekening gebracht vóór belastingen of deze in rekening gebracht.                          |
| preTaxEffectiveRate      | getal                                                         | Haalt of stelt de effectieve prijs vóór belastingen.                        |
| regio                   | tekenreeks                                                         | Hiermee wordt de regio die is gekoppeld aan het resource-exemplaar, op haalt of in.        |
| resourceGuid             | tekenreeks                                                         | Hiermee haalt u de resource-id op of stelt u deze in.                                 |
| resourceName             | tekenreeks                                                         | Hiermee haalt u de resourcenaam op of stelt u deze in. Voorbeeld: Database (GB/maand).         |
| Servicenaam              | tekenreeks                                                         | Hiermee haalt u de servicenaam op of stelt u deze in. Voorbeeld: Azure Data Service.           |
| serviceType              | tekenreeks                                                         | Hiermee haalt u het servicetype op of stelt u dit in. Voorbeeld: Azure SQL Azure DB.           |
| sku                      | tekenreeks                                                         | Hiermee haalt u de service-SKU op of stelt u deze in.                                         |
| subscriptionDescription  | tekenreeks                                                         | Hiermee haalt u de beschrijving van het abonnement op of stelt u deze in.                            |
| subscriptionId           | tekenreeks                                                         | Hiermee haalt u de unieke id van het abonnement op of stelt u deze in.                      |
| subscriptionName         | tekenreeks                                                         | Hiermee haalt u de naam van het abonnement op of stelt u deze in.                                   |
| taxAmount                | getal                                                         | Hiermee wordt het in rekening gebrachte btw-bedrag in rekening gebracht of in rekening gebracht.                               |
| tier2MpnId               | getal                                                         | Hiermee wordt de MPN-id van de Laag 2-partner die aan dit regelitem is gekoppeld, opgehouden of stelt u deze in. |
| eenheid                     | tekenreeks                                                         | Hiermee wordt de maateenheid voor Azure-gebruik in- of uitgevoerd.                     |

## <a name="invoicestatement"></a>InvoiceStatement

Vertegenwoordigt de bewerkingen die beschikbaar zijn op een factuuroverzicht in toepassing/pdf.

| Eigenschap                 | Type                                                           | Description                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| httpResponseMessage      | object                                                         | ByteArrayContent met contentType = application/pdf.                  |

## <a name="onetimeinvoicelineitem"></a>OneTimeInvoiceLineItem

Vertegenwoordigt een factuurfactureringsregelitem voor abonnementen op basis van een licentie.

| Eigenschap | Type | Description |
| --- | --- | --- |
| PartnerId | tekenreeks | Hiermee haalt u de tenant-id van de partner op of stelt u deze in. |
| CustomerId | tekenreeks | Hiermee haalt u de tenant-id van de klant op of stelt u deze in. |
| CustomerName | tekenreeks | Hiermee haalt u de naam van de klant op of stelt u deze in. |
| CustomerDomainName | tekenreeks | Hiermee haalt u de domeinnaam van de klant op of stelt u deze in. |
| CustomerCountry | tekenreeks | Hiermee haalt u het land van de klant op of stelt u het in. |
| InvoiceNumber | tekenreeks | Hiermee haalt u het factuurnummer op of stelt u dit in. |
| MpnId | tekenreeks | Hiermee haalt u de MPN-id op die is gekoppeld aan dit regelitem of stelt u deze in. |
| ResellerMpnId | int | Hiermee wordt de unieke id van de bestelling of de unieke id van de bestelling. |
| OrderDate | DateTime | Hiermee wordt de datum van het maken van de order op of instelt. |
| ProductId | tekenreeks | Hiermee haalt u de unieke id van het product op of stelt u deze in. |
| SkuId | tekenreeks | Hiermee haalt u de unieke SKU-id op of stelt u deze in. |
| AvailabilityId | tekenreeks | Hiermee haalt u de unieke beschikbaarheids-id op of stelt u deze in. |
| ProductName | tekenreeks | Hiermee haalt u de productnaam op of stelt u deze in. |
| SkuName | tekenreeks | Hiermee haalt u de SKU-naam op of stelt u deze in. |
| ChargeType | tekenreeks | Hiermee haalt u het type kosten op of stelt u dit in. |
| UnitPrice | decimal | Hiermee haalt u de eenheidsprijs op of stelt u deze in. |
| EffectiveUnitPrice | decimal | Hiermee haalt u de effectieve eenheidsprijs op of stelt u deze in. |
| UnitType | tekenreeks | Hiermee haalt u het eenheidstype op of stelt u dit in. |
| Aantal | int | Hiermee wordt het aantal eenheden dat aan dit regelitem is gekoppeld, op haalt of in. |
| Subtotaal | decimal | Hiermee wordt het bedrag na korting ontvangen of stelt u dit in. |
| TaxTotal | decimal | Hiermee worden de in rekening gebrachte belastingen in rekening gebracht of in rekening gebracht. |
| TotalForCustomer | decimal | Haalt of stelt het totale bedrag na korting en belasting. |
| Valuta | tekenreeks | Hiermee haalt u de valuta op die wordt gebruikt voor dit regelitem of stelt u deze in. |
| PublisherName | tekenreeks | Hiermee haalt u de naam van de uitgever op die is gekoppeld aan deze aankoop of stelt u deze in. |
| PublisherId | tekenreeks | Hiermee haalt u de uitgevers-id op die is gekoppeld aan deze aankoop of stelt u deze in. |
| SubscriptionDescription | tekenreeks | Hiermee wordt de abonnementsbeschrijving die aan deze aankoop is gekoppeld, op halen of in stellen. |
| SubscriptionId | tekenreeks | Hiermee haalt u de abonnements-id op die is gekoppeld aan deze aankoop of stelt u deze in. |
| ChargeStartDate | DateTime | Hiermee wordt de begindatum van de kosten die aan deze aankoop is gekoppeld, op de hoogte gebracht of stelt u deze in. |
| ChargeEndDate | DateTime | Hiermee wordt de einddatum van de kosten die aan deze aankoop is gekoppeld, op de hoogte gebracht of stelt u deze in. |
| TermAndBillingCycle | tekenreeks | Hiermee worden de termijn en factureringscyclus die aan deze aankoop zijn gekoppeld, in- ofset. |
| AlternateId | tekenreeks | Hiermee haalt u de alternatieve id (prijsopgave-id) op of stelt u deze in. |
| PriceAdjustmentDescription | tekenreeks | Hiermee haalt u de beschrijving van de prijscorrectie op of stelt u deze in. |
| CreditReasonCode | tekenreeks | Hiermee wordt de redencode van het tegoed ontvangen of stelt u deze in. |
| DiscountDetails | tekenreeks |  **Afgeschaft.** Hiermee worden de kortingsdetails voor deze aankoop ontvangen of stelt u deze in. |
| PricingCurrency | tekenreeks | Hiermee haalt u de prijsvalutacode op of stelt u deze in. |
| PCToBCExchangeRate | decimal | Haalt de prijsvaluta op of stelt deze in op de wisselkoers van de factureringsvaluta. |
| PCToBCExchangeRateDate | DateTime | Hiermee wordt de datum van de wisselkoers waarop de prijsvaluta is bepaald, op de wisselkoers van de factureringsvaluta bepaald of bepaald. |
| BillableQuantity | decimal | Hiermee haalt u de aangeschafte eenheden op of stelt u deze in. Voor elke ontwerpkolom met de naam **BillableQuantity**. |
| MeterDescription | tekenreeks | Hiermee wordt de meterbeschrijving voor het verbruiksregelitem op of stelt u deze in. |
| ReservationOrderId | tekenreeks | Hiermee wordt de reserveringsorder-id voor een Azure RI-aankoop in- of uitgevoerd. |
| BillingFrequency | tekenreeks | Hiermee haalt u de factureringsfrequentie op of stelt u deze in. |
| InvoiceLineItemType | InvoiceLineItemType | Retourneert het type factuurregelitem. |
| BillingProvider | BillingProvider | Retourneert de factureringsprovider. |

## <a name="dailyratedusagelineitem"></a>DailyRatedUsageLineItem

Vertegenwoordigt niet-gefactureerde afstemmingslijnitems voor dagelijks beoordeeld gebruik.

| Eigenschap | Type | Description |
| --- | --- | --- |
| PartnerId | tekenreeks | Hiermee haalt u de tenant-id van de partner op of stelt u deze in. |
| PartnerName | tekenreeks | Hiermee haalt u de naam van de partner op of stelt u deze in. |
| CustomerId | tekenreeks | Hiermee wordt de tenant-id van de klant waar het gebruik bij hoort, op haalt of in. |
| CustomerName | tekenreeks | Hiermee wordt de naam van het klantbedrijf waar het gebruik van deel van is, in- of uit. |
| CustomerDomainName | tekenreeks | Hiermee wordt de domeinnaam van de klant waar het gebruik van deel van is, op de naam van de klant of stelt deze in. |
| InvoiceNumber | tekenreeks | Hiermee wordt de id van de factuur waar het gebruik bij hoort, ontvangen of stelt u deze in. |
| ProductId | tekenreeks | Hiermee haalt u de unieke id van het product op of stelt u deze in. |
| SkuId | tekenreeks | Hiermee haalt u de unieke SKU-id op of stelt u deze in. |
| AvailabilityId | tekenreeks | Hiermee haalt u de unieke beschikbaarheids-id op of stelt u deze in. |
| SkuName | tekenreeks | Hiermee haalt u de SKU-naam voor de service op of stelt u deze in. |
| ProductName | tekenreeks | Hiermee haalt u de naam van het product op of stelt u deze in. |
| PublisherName | tekenreeks | Hiermee haalt u de naam van de uitgever op of stelt u deze in. |
| PublisherId | tekenreeks | Hiermee haalt u de id van de uitgever op of stelt u deze in. |
| SubscriptionId | tekenreeks | Hiermee haalt u de abonnements-id op of stelt u deze in. |
| SubscriptionDescription | tekenreeks | Hiermee haalt u de beschrijving van het abonnement op of stelt u deze in. |
| ChargeStartDate | DateTime | Hiermee haalt u de begindatum van de kosten op of stelt u deze in. |
| ChargeEndDate | DateTime | Hiermee haalt u de einddatum van de kosten op of stelt u deze in. |
| UsageDate | DateTime | Hiermee haalt u de gebruiksdatum op of stelt u deze in. |
| MeterType | tekenreeks | Hiermee haalt u het metertype op of stelt u dit in. |
| MeterCategory | tekenreeks | Hiermee haalt u de metercategorie op of stelt u deze in. |
| MeterId | tekenreeks | Hiermee haalt u de meter-id (GUID) op of stelt u deze in. |
| MeterSubCategory | tekenreeks | Hiermee haalt u de subcategorie van de meter op of stelt u deze in. |
| MeterName | tekenreeks | Hiermee haalt u de meternaam op of stelt u deze in. |
| MeterRegion | tekenreeks | Hiermee haalt u de meterregio op of stelt u deze in. |
| UnitOfMeasure | tekenreeks | Hiermee haalt u de maateenheid op of stelt u deze in. |
| ResourceLocation | tekenreeks | Hiermee haalt u de locatie van de resource op of stelt u deze in. |
| ConsumedService | tekenreeks | Hiermee haalt u de naam van de verbruikte service op of stelt u deze in. |
| ResourceGroup | tekenreeks | Hiermee haalt u de naam van de resourcegroep op of stelt u deze in. |
| ResourceUri | tekenreeks | Hiermee wordt de URI van het resource-exemplaar waar het gebruik over gaat, op de URI van de resource-instantie in of stelt deze in. |
| Tags | tekenreeks | Hiermee haalt u tags op of stelt u de tags in die de klant heeft toegevoegd. |
| AdditionalInfo | tekenreeks | Haalt de servicespecifieke metagegevens op of stelt deze in. Bijvoorbeeld een installatiekopie voor een virtuele machine. |
| ServiceInfo1 | tekenreeks | Hiermee worden interne Azure-servicemetagegevens opgeslagen ofsets. |
| ServiceInfo2 | tekenreeks | Haalt servicegegevens op of stelt deze in, bijvoorbeeld een afbeeldingstype voor een virtuele machine en isp-naam voor ExpressRoute. |
| CustomerCountry | tekenreeks | Hiermee haalt u het land van de klant op of stelt u dit in. |
| MpnId | tekenreeks | Hiermee haalt u de MPN-id op die is gekoppeld aan dit regelitem of stelt u deze in. |
| ResellerMpnId | tekenreeks | Hiermee wordt de MPN-id van de reseller van de Partner op laag 2 die aan dit regelitem is gekoppeld, of stelt deze in. |
| ChargeType | tekenreeks | Hiermee haalt u het type kosten op of stelt u dit in. |
| UnitPrice | decimal | Hiermee haalt u de prijs van de eenheid op of stelt u deze in. |
| Aantal | decimal | Hiermee wordt de hoeveelheid gebruik in- ofsets. |
| UnitType | tekenreeks | Hiermee wordt het eenheidstype (zoals 1 uur) getypt of bepaald. |
| BillingPreTaxTotal | decimal | Hiermee worden de uitgebreide kosten of de totale kosten vóór belasting in de lokale valuta van de klant of factureringsvaluta in- ofsets. |
| BillingCurrency | tekenreeks | Hiermee wordt iso-valuta in rekening gebracht of in rekening gebracht in lokale valuta van de klant of factureringsvaluta. |
| PricingPreTaxTotal | decimal | Hiermee worden de uitgebreide kosten of de totale kosten vóór belasting in USD of catalogusvaluta voor classificatie in- ofsets. |
| PricingCurrency | tekenreeks | Hiermee wordt iso-valuta in rekening gebracht of in rekening gebracht in USD of catalogusvaluta die wordt gebruikt voor classificatie. |
| EntitlementId | tekenreeks | Hiermee haalt u de rechten-id (Azure-abonnement) op of stelt u deze in. |
| EntitlementDescription | tekenreeks | Hiermee haalt u de beschrijving van het recht (Azure-abonnement) op of stelt u deze in. |
| PCToBCExchangeRate | tekenreeks | Haalt de prijsvaluta op of stelt deze in op de wisselkoers van de factureringsvaluta. |
| PCToBCExchangeRateDate | DateTime | Haalt de prijsvaluta op of stelt deze in op de datum van de factureringsvaluta. |
| EffectiveUnitPrice | decimal | Haalt de effectieve eenheidsprijs op of stelt deze in. |
| RateOfPartnerEarnedCredit | decimal | Hiermee wordt het tarief van partnertegoeden of -tegoeden in- ofsets. |
| HasPartnerEarnedCredit | booleaans | Hiermee wordt het partnertegoed toegepast of wordt het tegoed van de partner toegepast. |
| RateOfCredit | decimal | Hiermee wordt het tarief van het tegoed voor het opgegeven tegoedtype in- of bepaald. |
| CreditType | tekenreeks | Haalt het type tegoed op of stelt dit in. |
| InvoiceLineItemType | InvoiceLineItemType | Retourneert het type factuurregelitem. |
| BillingProvider | BillingProvider | Retourneert de factureringsprovider. |
