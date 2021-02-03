---
title: Factuur resources
description: Er zijn meerdere factuur resources beschikbaar via de partner centrum-Api's. Deze resources zijn gerelateerd aan factuur-en Details van regel items.
ms.date: 01/27/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bd2caefe4ae18c81a31083d084f1e87da1288dd9
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767229"
---
# <a name="invoice-resources"></a>Factuur resources

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De volgende factuur-gerelateerde resources zijn beschikbaar via de partner centrum-Api's.

## <a name="invoice"></a>Factuur

| Eigenschap | Type | Beschrijving |
| -------- | ---- | ----------- |
| id | tekenreeks | De factuur-ID. |
| invoiceDate | teken reeks in UTC-datum-tijd notatie | De datum waarop de factuur is gegenereerd. |
| billingPeriodStartDate | teken reeks in UTC-datum-tijd notatie | Begin datum facturerings periode in UTC. |
| billingPeriodEndDate | teken reeks in UTC-datum-tijd notatie   | Eind datum van facturerings periode in UTC. |
| totalCharges | getal | De totale kosten. Inclusief kosten voor trans acties en eventuele aanpassingen.     |
| paidAmount | getal  | Het bedrag dat door de partner wordt betaald. Negatief als er een betaling is ontvangen.  |
| currencyCode | tekenreeks  | Een code die de gebruikte valuta voor alle bedragen en totalen van factuur items aangeeft. |
| currencySymbol  | tekenreeks | Het valuta symbool dat wordt gebruikt voor alle bedragen en totalen van factuur items. |
| pdfDownloadLink | tekenreeks  | Een koppeling voor het downloaden van de factuur in PDF-indeling. Deze koppeling wordt niet geretourneerd als onderdeel van de zoek resultaten en wordt alleen ingevuld als de factuur wordt geopend met de ID. Deze koppeling is in 30 minuten automatisch verloopt. |
| invoiceDetails  | matrix van [InvoiceDetail](#invoicedetail) -objecten  | De factuur Details.  |
| gewijzigd      | matrix van [factuur](#invoice) objecten   | De wijzigingen in deze factuur.  |
| Document type    | tekenreeks | Het document type van de factuur: credit nota, invoice. |
| amendsOf        | tekenreeks | Het referentie nummer van het document waarvan dit document een wijziging is.  |
| invoiceType     | tekenreeks  | Het type factuur: ' terugkerend ', ' eenmalig ' \_ .   |
| koppelen           | [ResourceLinks](utility-resources.md#resourcelinks)  | De resource koppelingen.  |
| kenmerken      | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.  |

## <a name="invoicedetail"></a>InvoiceDetail

Een factuur bevat een verzameling gefactureerde items en elk item wordt vertegenwoordigd door een InvoiceDetail-resource.

| Eigenschap            | Type                                                           | Description                                                                       |
|---------------------|----------------------------------------------------------------|-----------------------------------------------------------------------------------|
| invoiceLineItemType | tekenreeks                                                         | Het type factuur Details: ' geen ', ' Gebruik \_ regel \_ items ', ' facturerings \_ regel \_ items '. |
| billingProvider     | tekenreeks                                                         | De facturerings provider: ' none ', ' Office ', ' Azure ' of ' Azure \_ Data \_ Market '.         |
| koppelen               | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen.                                                               |
| kenmerken          | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.                                                          |

## <a name="invoicelineitem"></a>InvoiceLineItem

Elke afzonderlijke kosten binnen een factuur worden weer gegeven als een InvoiceLineItem.

| Eigenschap            | Type                                                           | Description                                                                          |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| invoiceLineItemType | tekenreeks                                                         | Het type factuur regel item: ' geen ', ' Gebruik \_ regel \_ items ', ' facturerings \_ regel \_ items '. |
| billingProvider     | tekenreeks                                                         | De facturerings provider: ' none ', ' Office ', ' Azure ' of ' Azure \_ Data \_ Market '.            |
| kenmerken          | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken.                                                             |

## <a name="invoicesummary"></a>InvoiceSummary

Hierin wordt een overzicht van het saldo en de totale kosten van een factuur beschreven.

| Eigenschap                 | Type                                                           | Description                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| balanceAmount            | getal                                                         | Het saldo van de factuur. Dit is de totale hoeveelheid niet-betaalde rekeningen. |
| currencyCode             | tekenreeks                                                         | Een code die de gebruikte valuta voor het saldo bedrag aangeeft.       |
| currencySymbol           | tekenreeks                                                         | Het valuta symbool dat wordt gebruikt.                                             |
| accountingDate           | teken reeks in UTC-datum-tijd notatie                                 | De datum waarop het saldo bedrag voor het laatst is bijgewerkt.                         |
| firstInvoiceCreationDate | teken reeks in UTC-datum-tijd notatie                                 | De datum waarop de eerste factuur voor de klant is gemaakt.              |
| lastPaymentDate          | teken reeks in UTC-datum-tijd notatie                                 | De datum van de laatste betaling.                                         |
| lastPaymentAmount        | getal                                                         | Het bedrag van de laatste betaling.                                       |
| latestInvoiceDate        | teken reeks in UTC-datum-tijd notatie                                 | De datum waarop de laatste factuur voor de klant is gemaakt.               |
| nadere                  | matrix van [InvoiceSummaryDetail](#invoicesummarydetail) -objecten | De details van het factuur overzicht.                                           |
| koppelen                    | [ResourceLinks](utility-resources.md#resourcelinks)            | De resource koppelingen.                                                   |
| kenmerken               | [ResourceAttributes](utility-resources.md#resourceattributes)  | De meta gegevens kenmerken.                                              |

## <a name="invoicesummarydetail"></a>InvoiceSummaryDetail

Vertegenwoordigen een samen vatting van de afzonderlijke gegevens voor een factuur type (bijvoorbeeld terugkerende, eenmalige \_ tijd).

| Eigenschap            | Type                                                           | Description                                                                          |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| invoiceType         | tekenreeks                                                         | Het type factuur: ' terugkerend ', ' eenmalig ' \_ .                                       |
| samenvatting             | [InvoiceSummary](#invoicesummary) -object                       | De samen vatting van de factuur per factuur type.                                         |

## <a name="invoicesummaries"></a>InvoiceSummaries

Vertegenwoordigen een verzameling van het type [InvoiceSummary](#invoicesummary) die de afzonderlijke Details voor een factuur type per valuta bevatten.

| Eigenschap            | Type                                                           | Description                                                                          |
|---------------------|----------------------------------------------------------------|--------------------------------------------------------------------------------------|
| collectionOfSummary | matrix van [InvoiceSummary](#invoicesummary) -objecten             | De samen vatting van de factuur per factuur type per valuta.                            |

## <a name="licensebasedlineitem"></a>LicenseBasedLineItem

Vertegenwoordigt een factuur facturerings regel item voor op licenties gebaseerde abonnementen.

| Eigenschap                 | Type                                                           | Description                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| bedrag                   | tekenreeks                                                         | Hiermee wordt het totaal bedrag opgehaald of ingesteld. Totaal bedrag = eenheids prijs * aantal.  |
| kenmerken               | tekenreeks                                                         | Hiermee worden de kenmerken opgehaald.                                                  |
| billingCycleType         | tekenreeks                                                         | Hiermee wordt het type facturerings cyclus opgehaald of ingesteld.                                  |
| billingProvider          | tekenreeks                                                         | Hiermee wordt de facturerings provider opgehaald.                                            |
| chargeEndDate            | teken reeks in UTC-datum-tijd notatie                                 | Hiermee wordt de eind datum voor de kosten opgehaald of ingesteld.                             |
| chargeStartDate          | teken reeks in UTC-datum-tijd notatie                                 | Hiermee wordt de begin datum voor de kosten opgehaald of ingesteld.                           |
| chargeType               | tekenreeks                                                         | Hiermee wordt het type kosten opgehaald of ingesteld.                                      |
| currency                 | tekenreeks                                                         | Hiermee wordt de valuta opgehaald of ingesteld die voor dit regel item wordt gebruikt.                    |
| customerId               | tekenreeks                                                         | Hiermee wordt de unieke id van de klant opgehaald of ingesteld in het micro soft-factuur platform.  |
| customerName             | teken reeks in UTC-datum-tijd notatie                                 | Hiermee wordt de naam van de klant opgehaald of ingesteld.                                       |
| domainName               | tekenreeks                                                         | Hiermee wordt de domein naam opgehaald of ingesteld.                                             |
| durableOfferId           | tekenreeks                                                         | Hiermee wordt de unieke id van de duurzame aanbieding opgehaald of ingesteld.                     |
| invoiceLineItemType      | tekenreeks                                                         | Hiermee wordt het type van het factuur regel item opgehaald.                                   |
| mpnId                    | getal                                                         | Hiermee wordt de MPN-ID opgehaald of ingesteld die aan dit regel item is gekoppeld. Voor directe wederverkopers is dit de MPN-id van de wederverkoper. Voor indirecte wederverkopers is dit de MPN-ID van de waarde added reseller (VAR).                                   |
| offerId                  | tekenreeks                                                         | Hiermee wordt de unieke id van de aanbieding opgehaald of ingesteld.                             |
| offerName                | tekenreeks                                                         | Hiermee wordt de naam van het aanbod opgehaald of ingesteld.                                          |
| Velden                  | tekenreeks                                                         | Hiermee wordt de unieke id van de order opgehaald of ingesteld.                             |
| Partner                | tekenreeks                                                         | Hiermee wordt de Tenant-ID van de partner-Azure Active Directory opgehaald of ingesteld.            |
| quantity                 | getal                                                         | Hiermee wordt het aantal eenheden opgehaald of ingesteld dat aan dit regel item is gekoppeld.      |
| subscriptionDescription  | tekenreeks                                                         | Hiermee wordt de beschrijving van het abonnement opgehaald of ingesteld.                            |
| subscriptionEndDate      | teken reeks in UTC-datum-tijd notatie                                 | Hiermee wordt de datum opgehaald of ingesteld waarop het abonnement verloopt.                      |
| subscriptionId           | tekenreeks                                                         | Hiermee wordt de unieke id van het abonnement opgehaald of ingesteld.                      |
| subscriptionName         | tekenreeks                                                         | Hiermee wordt de naam van het abonnement opgehaald of ingesteld.                                   |
| Subscription    | teken reeks in UTC-datum-tijd notatie                                 | Hiermee wordt de datum opgehaald of ingesteld waarop het abonnement wordt gestart.                   |
| Subtotaal                 | getal                                                         | Hiermee wordt de hoeveelheid na de korting opgehaald of ingesteld.                               |
| syndicationPartnerSubscriptionNumber | tekenreeks                                             | Hiermee wordt het abonnements nummer van de syndicatie partner opgehaald of ingesteld.             |
| belasting                      | getal                                                         | Hiermee worden de gefactureerde BTW opgehaald of ingesteld.                                       |
| tier2MpnId               | getal                                                         | Hiermee wordt de MPN-ID opgehaald of ingesteld van de laag 2-partner die aan dit regel item is gekoppeld. |
| totalForCustomer         | getal                                                         | Hiermee wordt het totaal bedrag na de korting en belasting opgehaald of ingesteld.                 |
| totalOtherDiscount       | getal                                                         | Hiermee wordt de korting opgehaald of ingesteld die is gekoppeld aan deze aankoop.              |
| unitPrice                | getal                                                         | Hiermee wordt de eenheids prijs opgehaald of ingesteld.                                          |

## <a name="usagebasedlineitem"></a>UsageBasedLineItem

Vertegenwoordigt een facturerings regel item voor het factureren van op gebruik gebaseerde abonnementen.

| Eigenschap                 | Type                                                           | Description                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| kenmerken               | tekenreeks                                                         | Hiermee worden de kenmerken opgehaald.                                                  |
| billingCycleType         | tekenreeks                                                         | Hiermee wordt het type facturerings cyclus opgehaald of ingesteld.                                  |
| billingProvider          | tekenreeks                                                         | Hiermee wordt de facturerings provider opgehaald.                                            |
| chargeEndDate            | teken reeks in UTC-datum-tijd notatie                                 | Hiermee wordt de eind datum voor de kosten opgehaald of ingesteld.                             |
| chargeStartDate          | teken reeks in UTC-datum-tijd notatie                                 | Hiermee wordt de begin datum voor de kosten opgehaald of ingesteld.                           |
| chargeType               | tekenreeks                                                         | Hiermee wordt het type kosten opgehaald of ingesteld.                                      |
| consumedQuantity         | getal                                                         | Hiermee wordt het totale aantal verbruikte eenheden opgehaald of ingesteld.                                |
| consumptionDiscount      | tekenreeks                                                         | Hiermee wordt de korting op verbruik opgehaald of ingesteld.                             |
| consumptionPrice         | tekenreeks                                                         | Hiermee wordt de prijs van verbruikte hoeveelheid opgehaald of ingesteld.                          |
| currency                 | tekenreeks                                                         | Hiermee wordt de valuta opgehaald of ingesteld die is gekoppeld aan de prijzen.                 |
| customerName             | tekenreeks                                                         | Hiermee wordt de naam van de klant opgehaald of ingesteld.                                       |
| customerId               | tekenreeks                                                         | Hiermee wordt de unieke id van de klant opgehaald of ingesteld.                          |
| detailLineItemId         | getal                                                         | Hiermee wordt de item-ID van de detail regel opgehaald of ingesteld. Unieke identificatie van de regel items voor gevallen waarin de berekening afwijkt van de verbruikte eenheden. Voor beeld: totaal verbruikt = 1338, 1024 wordt in rekening gebracht met één tarief, het bedrag van 314 wordt gefactureerd met een ander tarief.        |
| domainName               | tekenreeks                                                         | Hiermee wordt de domein naam opgehaald of ingesteld.                                             |
| includedQuantity         | getal                                                         | Hiermee worden de eenheden opgehaald of ingesteld die in de order zijn opgenomen.                         |
| invoiceLineItemType      | tekenreeks                                                         | Hiermee wordt het type van het factuur regel item opgehaald.                                   |
| invoiceNumber            | tekenreeks                                                         | Hiermee wordt het factuur nummer opgehaald of ingesteld.                                      |
| listPrice                | getal                                                         | Hiermee wordt de prijs van elke eenheid opgehaald of ingesteld.                                  |
| mpnId                    | getal                                                         | Hiermee wordt de MPN-ID opgehaald of ingesteld die aan dit regel item is gekoppeld. Voor directe wederverkopers is dit de MPN-ID van de wederverkoper. Voor indirecte wederverkopers is dit de MPN-ID van de waarde added reseller (VAR).                                   |
| Velden                  | tekenreeks                                                         | Hiermee wordt de unieke id van de order opgehaald of ingesteld.                             |
| overageQuantity          | getal                                                         | Hiermee wordt de hoeveelheid verbruikt of ingesteld die het toegestane gebruik overschrijdt.               |
| partnerBillableAccountId | tekenreeks                                                         | Hiermee wordt de factureer bare account-ID van de partner opgehaald of ingesteld.                         |
| Partner                | tekenreeks                                                         | Hiermee wordt de Tenant-ID van de partner-Azure Active Directory opgehaald of ingesteld.            |
| partnerName              | tekenreeks                                                         | Hiermee wordt de naam van de partner opgehaald of ingesteld.                                      |
| postTaxEffectiveRate     | getal                                                         | Hiermee wordt de werkelijke prijs na belastingen opgehaald of ingesteld.                         |
| postTaxTotal             | getal                                                         | Hiermee worden de totale kosten na belasting opgehaald of ingesteld. Pretax kosten + BTW-bedrag |
| preTaxCharges            | getal                                                         | Hiermee wordt de prijs voor belastingen opgehaald of ingesteld.                          |
| preTaxEffectiveRate      | getal                                                         | Hiermee wordt de werkelijke prijs voor belastingen opgehaald of ingesteld.                        |
| regio                   | tekenreeks                                                         | Hiermee wordt de regio opgehaald of ingesteld die is gekoppeld aan het bron exemplaar.        |
| GUID             | tekenreeks                                                         | Hiermee wordt de resource-id opgehaald of ingesteld.                                 |
| resourceName             | tekenreeks                                                         | Hiermee wordt de naam van de resource opgehaald of ingesteld. Voor beeld: data base (GB/maand).         |
| serviceName              | tekenreeks                                                         | Hiermee wordt de service naam opgehaald of ingesteld. Voor beeld: Azure data service.           |
| Service              | tekenreeks                                                         | Hiermee wordt het Service type opgehaald of ingesteld. Voor beeld: Azure SQL Azure DB.           |
| sku                      | tekenreeks                                                         | Hiermee wordt de Service-SKU opgehaald of ingesteld.                                         |
| subscriptionDescription  | tekenreeks                                                         | Hiermee wordt de beschrijving van het abonnement opgehaald of ingesteld.                            |
| subscriptionId           | tekenreeks                                                         | Hiermee wordt de unieke id van het abonnement opgehaald of ingesteld.                      |
| subscriptionName         | tekenreeks                                                         | Hiermee wordt de naam van het abonnement opgehaald of ingesteld.                                   |
| taxAmount                | getal                                                         | Hiermee wordt de gefactureerde hoeveelheid belasting opgehaald of ingesteld.                               |
| tier2MpnId               | getal                                                         | Hiermee wordt de MPN-ID opgehaald of ingesteld van de laag 2-partner die aan dit regel item is gekoppeld. |
| eenheid                     | tekenreeks                                                         | Hiermee wordt de maat eenheid voor Azure-gebruik opgehaald of ingesteld.                     |

## <a name="invoicestatement"></a>InvoiceStatement

Hiermee wordt de beschik bare bewerkingen in een factuur overzicht in Application/PDF aangegeven.

| Eigenschap                 | Type                                                           | Description                                                           |
|--------------------------|----------------------------------------------------------------|-----------------------------------------------------------------------|
| httpResponseMessage      | object                                                         | ByteArrayContent met content type = Application/PDF.                  |

## <a name="onetimeinvoicelineitem"></a>OneTimeInvoiceLineItem

Vertegenwoordigt een factuur facturerings regel item voor abonnementen op basis van licenties.

| Eigenschap | Type | Description |
| --- | --- | --- |
| Partner | tekenreeks | Hiermee wordt de Tenant-ID van de partner opgehaald of ingesteld. |
| CustomerId | tekenreeks | Hiermee wordt de Tenant-ID van de klant opgehaald of ingesteld. |
| CustomerName | tekenreeks | Hiermee wordt de naam van de klant opgehaald of ingesteld. |
| CustomerDomainName | tekenreeks | Hiermee wordt de domein naam van de klant opgehaald of ingesteld. |
| CustomerCountry | tekenreeks | Hiermee wordt het land van de klant opgehaald of ingesteld. |
| InvoiceNumber | tekenreeks | Hiermee wordt het factuur nummer opgehaald of ingesteld. |
| MpnId | tekenreeks | Hiermee wordt de MPN-ID opgehaald of ingesteld die aan dit regel item is gekoppeld. |
| ResellerMpnId | int | Hiermee wordt de unieke id van de order opgehaald of ingesteld. |
| OrderDate | DateTime | Hiermee wordt de datum opgehaald of ingesteld waarop de order is gemaakt. |
| ProductId | tekenreeks | Hiermee wordt de unieke product-id opgehaald of ingesteld. |
| SkuId | tekenreeks | Hiermee wordt de unieke id van de SKU opgehaald of ingesteld. |
| AvailabilityId | tekenreeks | Hiermee wordt de unieke id van de beschik baarheid opgehaald of ingesteld. |
| ProductName | tekenreeks | Hiermee wordt de product naam opgehaald of ingesteld. |
| SkuName | tekenreeks | Hiermee wordt de SKU-naam opgehaald of ingesteld. |
| ChargeType | tekenreeks | Hiermee wordt het type kosten opgehaald of ingesteld. |
| UnitPrice | decimal | Hiermee wordt de eenheids prijs opgehaald of ingesteld. |
| EffectiveUnitPrice | decimal | Hiermee wordt de werkelijke eenheids prijs opgehaald of ingesteld. |
| Unit type | tekenreeks | Hiermee wordt het eenheids type opgehaald of ingesteld. |
| Aantal | int | Hiermee wordt het aantal eenheden opgehaald of ingesteld dat aan dit regel item is gekoppeld. |
| Subtotaal | decimal | Hiermee wordt de hoeveelheid na de korting opgehaald of ingesteld. |
| TaxTotal | decimal | Hiermee worden de gefactureerde BTW opgehaald of ingesteld. |
| TotalForCustomer | decimal | Hiermee wordt het totaal bedrag na de korting en belasting opgehaald of ingesteld. |
| Valuta | tekenreeks | Hiermee wordt de valuta opgehaald of ingesteld die voor dit regel item wordt gebruikt. |
| PublisherName | tekenreeks | Hiermee wordt de naam van de uitgever opgehaald of ingesteld die aan deze aankoop is gekoppeld. |
| PublisherId | tekenreeks | Hiermee wordt de uitgevers-ID opgehaald of ingesteld die aan deze aankoop is gekoppeld. |
| SubscriptionDescription | tekenreeks | Hiermee wordt de beschrijving van het abonnement opgehaald of ingesteld die aan deze aankoop is gekoppeld. |
| SubscriptionId | tekenreeks | Hiermee wordt de abonnements-ID opgehaald of ingesteld die is gekoppeld aan deze aankoop. |
| ChargeStartDate | DateTime | Hiermee wordt de begin datum voor de kosten van deze aankoop opgehaald of ingesteld. |
| ChargeEndDate | DateTime | Hiermee wordt de eind datum van de kosten voor deze aankoop opgehaald of ingesteld. |
| TermAndBillingCycle | tekenreeks | Hiermee wordt de periode en facturerings cyclus opgehaald of ingesteld die aan deze aankoop is gekoppeld. |
| AlternateId | tekenreeks | Hiermee wordt de alternatieve ID (Quote-ID) opgehaald of ingesteld. |
| PriceAdjustmentDescription | tekenreeks | Hiermee wordt de beschrijving van de prijs correctie opgehaald of ingesteld. |
| DiscountDetails | tekenreeks |  **Afgeschaft**. Hiermee worden de kortings gegevens opgehaald of ingesteld die zijn gekoppeld aan deze aankoop. |
| PricingCurrency | tekenreeks | Hiermee wordt de valuta code voor prijzen opgehaald of ingesteld. |
| PCToBCExchangeRate | decimal | Hiermee wordt de prijs valuta opgehaald of ingesteld op basis van de valuta wisselkoers. |
| PCToBCExchangeRateDate | DateTime | Hiermee wordt de wisselkoers datum opgehaald of ingesteld waarmee de prijs valuta voor de wissel koers van de facturerings valuta werd bepaald. |
| BillableQuantity | decimal | Hiermee worden de aangeschafte eenheden opgehaald of ingesteld. Voor elke ontwerp kolom met de naam **BillableQuantity**. |
| MeterDescription | tekenreeks | Hiermee wordt de meter beschrijving voor het verbruik van het regel item opgehaald of ingesteld. |
| ReservationOrderId | tekenreeks | Hiermee wordt de reserverings order-id voor een Azure RI-aankoop opgehaald of ingesteld. |
| BillingFrequency | tekenreeks | Hiermee wordt de facturerings frequentie opgehaald of ingesteld. |
| InvoiceLineItemType | InvoiceLineItemType | Hiermee wordt het type van het factuur regel item geretourneerd. |
| BillingProvider | BillingProvider | Hiermee wordt de facturerings provider geretourneerd. |

## <a name="dailyratedusagelineitem"></a>DailyRatedUsageLineItem

Vertegenwoordigt niet-gefactureerde, gefactureerde afstemmings regel items voor dagelijks geclassificeerd gebruik.

| Eigenschap | Type | Description |
| --- | --- | --- |
| Partner | tekenreeks | Hiermee wordt de Tenant-ID van de partner opgehaald of ingesteld. |
| PartnerName | tekenreeks | Hiermee wordt de naam van de partner opgehaald of ingesteld. |
| CustomerId | tekenreeks | Hiermee wordt de Tenant-ID opgehaald of ingesteld van de klant waarbij het gebruik behoort. |
| CustomerName | tekenreeks | Hiermee wordt de naam opgehaald of ingesteld van het bedrijf van de klant waarbij gebruik wordt uitmaakt. |
| CustomerDomainName | tekenreeks | Hiermee wordt de domein naam opgehaald of ingesteld van de klant waarbij het gebruik behoort. |
| InvoiceNumber | tekenreeks | Hiermee wordt de ID opgehaald of ingesteld van de factuur waarvan het gebruik deel uitmaakt. |
| ProductId | tekenreeks | Hiermee wordt de unieke product-id opgehaald of ingesteld. |
| SkuId | tekenreeks | Hiermee wordt de unieke id van de SKU opgehaald of ingesteld. |
| AvailabilityId | tekenreeks | Hiermee wordt de unieke id van de beschik baarheid opgehaald of ingesteld. |
| SkuName | tekenreeks | Hiermee wordt de SKU-naam voor de service opgehaald of ingesteld. |
| ProductName | tekenreeks | Hiermee wordt de naam van het product opgehaald of ingesteld. |
| PublisherName | tekenreeks | Hiermee wordt de naam van de uitgever opgehaald of ingesteld. |
| PublisherId | tekenreeks | Hiermee wordt de ID van de uitgever opgehaald of ingesteld. |
| SubscriptionId | tekenreeks | Hiermee wordt de abonnements-ID opgehaald of ingesteld. |
| SubscriptionDescription | tekenreeks | Hiermee wordt de beschrijving van het abonnement opgehaald of ingesteld. |
| ChargeStartDate | DateTime | Hiermee wordt de begin datum van de lading opgehaald of ingesteld. |
| ChargeEndDate | DateTime | Hiermee wordt de eind datum van de lading opgehaald of ingesteld. |
| UsageDate | DateTime | Hiermee wordt de gebruiks datum opgehaald of ingesteld. |
| MeterType | tekenreeks | Hiermee wordt het meter type opgehaald of ingesteld. |
| MeterCategory | tekenreeks | Hiermee wordt de meter categorie opgehaald of ingesteld. |
| MeterId | tekenreeks | Hiermee wordt de meter-ID (GUID) opgehaald of ingesteld. |
| MeterSubCategory | tekenreeks | Hiermee wordt de subcategorie van de meter opgehaald of ingesteld. |
| MeterName | tekenreeks | Hiermee wordt de naam van de meter opgehaald of ingesteld. |
| MeterRegion | tekenreeks | Hiermee wordt de meter regio opgehaald of ingesteld. |
| UnitOfMeasure | tekenreeks | Hiermee wordt de maat eenheid opgehaald of ingesteld. |
| ResourceLocation | tekenreeks | Hiermee wordt de locatie van de resource opgehaald of ingesteld. |
| ConsumedService | tekenreeks | Hiermee wordt de verbruikte service naam opgehaald of ingesteld. |
| ResourceGroup | tekenreeks | Hiermee wordt de naam van de resource groep opgehaald of ingesteld. |
| ResourceUri | tekenreeks | Hiermee wordt de URI opgehaald of ingesteld van het resource-exemplaar waarvoor het gebruik wordt gebruikt. |
| Tags | tekenreeks | Hiermee wordt de door de klant toegevoegde Tags opgehaald of ingesteld. |
| AdditionalInfo | tekenreeks | Hiermee worden de servicespecifieke meta gegevens opgehaald of ingesteld. Bijvoorbeeld een installatiekopie voor een virtuele machine. |
| ServiceInfo1 | tekenreeks | Hiermee worden de interne meta gegevens van Azure-service opgehaald of ingesteld. |
| ServiceInfo2 | tekenreeks | Hiermee worden service gegevens opgehaald of ingesteld, bijvoorbeeld een installatie kopie type voor de naam van een virtuele machine en ISP voor ExpressRoute. |
| CustomerCountry | tekenreeks | Hiermee wordt het land van de klant opgehaald of ingesteld. |
| MpnId | tekenreeks | Hiermee wordt de MPN-ID opgehaald of ingesteld die aan dit regel item is gekoppeld. |
| ResellerMpnId | tekenreeks | Hiermee wordt de reseller MPN-ID opgehaald of ingesteld van de laag 2-partner die aan dit regel item is gekoppeld. |
| ChargeType | tekenreeks | Hiermee wordt het type kosten opgehaald of ingesteld. |
| UnitPrice | decimal | Hiermee wordt de prijs van de eenheid opgehaald of ingesteld. |
| Aantal | decimal | Hiermee wordt het aantal gebruik opgehaald of ingesteld. |
| Unit type | tekenreeks | Hiermee wordt het eenheids type (zoals 1 uur) opgehaald of ingesteld. |
| BillingPreTaxTotal | decimal | Hiermee worden de berekende kosten of de totale kosten voor de belasting in de lokale valuta van de klant of facturerings valuta opgehaald of ingesteld. |
| BillingCurrency | tekenreeks | Hiermee wordt de ISO-valuta opgehaald of ingesteld waarin de meter wordt gefactureerd in de lokale valuta van de klant of facturerings valuta. |
| PricingPreTaxTotal | decimal | Hiermee worden de berekende kosten of de totale kosten voor de belasting in USD of de catalogus valuta die voor de beoordeling wordt gebruikt, opgehaald of ingesteld. |
| PricingCurrency | tekenreeks | Hiermee wordt de ISO-valuta opgehaald of ingesteld waarin de meter wordt gefactureerd in USD of catalogus valuta die voor beoordeling wordt gebruikt. |
| EntitlementId | tekenreeks | Hiermee wordt de recht-ID (Azure-abonnement) opgehaald of ingesteld. |
| EntitlementDescription | tekenreeks | Hiermee wordt de beschrijving van het recht (Azure-abonnement) opgehaald of ingesteld. |
| PCToBCExchangeRate | tekenreeks | Hiermee wordt de prijs valuta opgehaald of ingesteld op basis van de valuta wisselkoers. |
| PCToBCExchangeRateDate | DateTime | Hiermee wordt de prijs valuta opgehaald of ingesteld op basis van de valuta wisselkoers datum. |
| EffectiveUnitPrice | decimal | Hiermee wordt de werkelijke eenheids prijs opgehaald of ingesteld. |
| RateOfPartnerEarnedCredit | decimal | Hiermee wordt de frequentie van het tegoed van de partner opgehaald of ingesteld. |
| hasPartnerEarnedCredit | booleaans | Hiermee wordt opgehaald of ingesteld dat het tegoed van de partner is toegepast. |
| InvoiceLineItemType | InvoiceLineItemType | Hiermee wordt het type van het factuur regel item geretourneerd. |
| BillingProvider | BillingProvider | Hiermee wordt de facturerings provider geretourneerd. |
