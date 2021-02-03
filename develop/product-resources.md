---
title: Producten resources
description: Resources die tevense goederen of services vertegenwoordigen. Bevat resources voor het beschrijven van het product type en de vorm (SKU) en voor het controleren van de beschik baarheid van het product in een inventaris.
ms.date: 04/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6a3cfacd3654e85a9824759295f97792ff740d85
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767337"
---
# <a name="products-resources"></a>Producten resources

**Van toepassing op**

- Partnercentrum

Resources die tevense goederen of services vertegenwoordigen. Bevat resources voor het beschrijven van het product type en de vorm (SKU) en voor het controleren van de beschik baarheid van het product in een inventaris.

## <a name="product"></a>Product

Hiermee wordt een tevens-goed of-service aangeduid. Een product zelf is geen tevens-item.

| Eigenschap           | Type                          | Beschrijving                                                              |
|--------------------|-------------------------------|--------------------------------------------------------------------------|
| id                 | tekenreeks                        | De ID voor dit product.                                                 |
| titel              | tekenreeks                        | De titel van het product.                                                       |
| beschrijving        | tekenreeks                        | De product beschrijving.                                                 |
| productType        | [Item type](#itemtype)         | Een object met een beschrijving van het type categorisatie (s) van dit product.     |
| isMicrosoftProduct | booleaans                          | Hiermee wordt aangegeven of dit een micro soft-product is.                          |
| publisherName      | tekenreeks                        | De naam van de uitgever van het product, indien beschikbaar.                          |
| koppelen              | [ProductLinks](#productlinks) | De resource koppelingen in het product.                         |

## <a name="itemtype"></a>ItemType

Hiermee wordt het type van een product aangeduid.

| Eigenschap        | Type                          | Beschrijving                                                                          |
|-----------------|-------------------------------|--------------------------------------------------------------------------------------|
| id              | tekenreeks                        | De type-id.                                                                 |
| displayName     | tekenreeks                        | De weergave naam voor dit type.                                                      |
| subType         | [Item type](#itemtype)         | Optioneel. Een object met een beschrijving van een categorisatie voor het subtype voor dit item type.     |

## <a name="productlinks"></a>ProductLinks

Bevat een lijst met koppelingen voor een [product](#product).

| Eigenschap        | Type                                                          | Description                                          |
|-----------------|---------------------------------------------------------------|------------------------------------------------------|
| voorraad            | [Koppeling](utility-resources.md#link)                             | De koppeling voor toegang tot de onderliggende Sku's.          |
| koppelen           | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen die deel uitmaken van deze resource.   |

## <a name="sku"></a>Sku

Vertegenwoordigt een SKU (Stock Keeping Unit) onder een product. Deze vertegenwoordigen de verschillende vormen van het product.

| Eigenschap               | Type             | Beschrijving                                                                           |
|------------------------|------------------|---------------------------------------------------------------------------------------|
| id                     | tekenreeks           | De ID voor deze SKU. Deze ID is alleen uniek binnen de context van het bovenliggende product. |
| titel                  | tekenreeks           | De titel van de SKU.                                                                 |
| beschrijving            | tekenreeks           | De beschrijving van de SKU.                                                           |
| productId              | tekenreeks           | De ID van het bovenliggende [product](#product) dat deze SKU bevat.                      |
| minimumQuantity        | int              | De minimale toegestane hoeveelheid voor aankoop.                                            |
| maximumQuantity        | int              | De Maxi maal toegestane hoeveelheid voor aankoop.                                            |
| isTrial                | booleaans             | Hiermee wordt aangegeven of deze SKU een proef item is.                                           |
| supportedBillingCycles | tekenreeksmatrix | De lijst met ondersteunde facturerings cycli voor deze SKU. Ondersteunde waarden zijn de lidnamen in [BillingCycleType](#billingcycletype). |
| purchasePrerequisites  | tekenreeksmatrix | De lijst met vereiste stappen of acties die nodig zijn voordat dit item wordt aangeschaft. De ondersteunde waarden zijn:<br/>  "InventoryCheck"-geeft aan dat de inventaris van het item moet worden geëvalueerd voordat u dit item gaat aanschaffen.<br/> "AzureSubscriptionRegistration"-geeft aan dat een Azure-abonnement nodig is en moet worden geregistreerd voordat u dit item kunt aanschaffen.  |
| inventoryVariables     | tekenreeksmatrix | De lijst met variabelen die nodig zijn voor het uitvoeren van een inventarisatie controle voor dit item. De ondersteunde waarden zijn:<br/> KlantId: de ID van de klant voor wie de aankoop geldt.<br/> "AzureSubscriptionId": de ID van het Azure-abonnement dat wordt gebruikt voor een inkoop van Azure-reserve ringen.</br> "ArmRegionName": de regio waarvoor de inventarisatie moet worden gecontroleerd. Deze waarde moet overeenkomen met de "ArmRegionName" van de DynamicAttributes van de SKU. |
| provisioningVariables  | tekenreeksmatrix | De lijst met variabelen die moeten worden verstrekt in de inrichtings context van een [Winkelwagen regel item](cart-resources.md#cartlineitem) bij de aankoop van dit item. De ondersteunde waarden zijn:<br/> Bereik: het bereik voor een inkoop van Azure-reserve ringen: ' single ', ' gedeeld '.<br/> ' SubscriptionId ': de ID van het Azure-abonnement dat wordt gebruikt voor een inkoop van Azure-reserve ringen.<br/> ' Duration ': de duur van de Azure-reserve ring, ' 1Year ', ' 3Year '.  |
| dynamicAttributes      | sleutel/waarde-paren  | De woorden lijst met dynamische eigenschappen die van toepassing zijn op dit item. Houd er rekening mee dat de eigenschappen in deze woorden lijst dynamisch zijn en kunnen zonder kennisgeving worden gewijzigd. U moet geen sterke afhankelijkheden maken voor bepaalde sleutels die in de waarde van deze eigenschap aanwezig zijn.    |
| koppelen                  | [ResourceLinks](utility-resources.md#resourcelinks) | De resource koppelingen in de SKU.                   |

## <a name="availability"></a>Beschikbaarheid

Vertegenwoordigt een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land, valuta en sector segment).

| Eigenschap        | Type                        | Beschrijving                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------------------------------|
| id              | tekenreeks                        | De ID voor deze Beschik baarheid. Deze ID is alleen uniek binnen de context van het bovenliggende [product](#product) en de bijbehorende [SKU](#sku). **Opmerking** Deze ID kan in de loop van de tijd worden gewijzigd. U moet binnen een korte tijds Panne alleen vertrouwen op deze waarde nadat u deze hebt opgehaald.  |
| productId       | tekenreeks                        | De ID van het [product](#product) dat deze Beschik baarheid bevat.           |
| skuId           | tekenreeks                        | De ID van de [SKU](#sku) die deze Beschik baarheid bevat.                   |
| catalogItemId   | tekenreeks                        | De unieke id voor dit item in de catalogus. Dit is de ID die moet worden ingevuld in de eigenschappen [OrderLineItem. OfferId](order-resources.md#orderlineitem) of [CartLineItem. CatalogItemId](cart-resources.md#cartlineitem) bij het aanschaffen van de bovenliggende [SKU](#sku). **Opmerking** Deze ID kan in de loop van de tijd worden gewijzigd. U moet deze waarde alleen binnen korte tijd gebruiken nadat u deze hebt opgehaald. Het mag alleen worden gebruikt voor toegang tot en gebruik op het moment van aankoop.  |
| defaultCurrency | tekenreeks                        | De standaard valuta die voor deze Beschik baarheid wordt ondersteund.                               |
| segment         | tekenreeks                        | Het sector segment voor deze Beschik baarheid. Ondersteunde waarden zijn: commercieel, onderwijs, overheid, non-profit organisatie. |
| country         | tekenreeks                                              | Het land of de regio (in ISO-land code-indeling) waarop deze Beschik baarheid van toepassing is. |
| isPurchasable   | booleaans                                                | Hiermee wordt aangegeven of deze Beschik baarheid tevens is. |
| isRenewable     | booleaans                                                | Hiermee wordt aangegeven of deze Beschik baarheid kan worden verlengd. |
| product      | [Product](#product)               | Het product waaraan deze Beschik baarheid correspondeert. |
| sku          | [SKU](#sku)            | De SKU waaraan deze Beschik baarheid correspondeert. |
| inzake           | matrix van [term](#term) resources  | De verzameling voor waarden die van toepassing zijn op deze Beschik baarheid. |
| koppelen           | [ResourceLinks](utility-resources.md#resourcelinks) | De resource koppelingen zijn opgenomen in de beschik baarheid. |

## <a name="term"></a>Term

Hiermee wordt een periode aangegeven waarvoor de beschik baarheid kan worden aangeschaft.

| Eigenschap              | Type                                        | Description                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| duur              | tekenreeks                                      | Een ISO 8601-representatie van de duur van de term. De huidige ondersteunde waarden zijn P1M (1 maand), P1Y (1 jaar) en P3Y (3 jaar). |
| beschrijving           | tekenreeks                                      | De beschrijving van de term.           |

## <a name="inventorycheckrequest"></a>InventoryCheckRequest

Hiermee wordt een aanvraag voor het controleren van de inventaris op bepaalde catalogus items aangeduid.

| Eigenschap         | Type                                                | Description                                                                                 |
|------------------|-----------------------------------------------------|---------------------------------------------------------------------------------------------|
| targetItems      | matrix van [InventoryItem](#inventoryitem)            | De lijst met catalogus items die door de inventarisatie controle worden geëvalueerd.                           |
| inventoryContext | sleutel/waarde-paren                                     | De woorden lijst met context waarden die nodig zijn om de inventaris controle (s) uit te voeren. Elke [SKU](#sku) van de producten definieert welke waarden (indien van toepassing) nodig zijn om deze bewerking uit te voeren.  |
| koppelen            | [ResourceLinks](utility-resources.md#resourcelinks) | De resource koppelingen zijn opgenomen in de aanvraag voor de controle van de inventaris.                            |

## <a name="inventoryitem"></a>InventoryItem

Hiermee wordt één item in een inventarisatie controle bewerking aangeduid. Deze resource wordt gebruikt voor het opgeven van de doel items in een invoer aanvraag en wordt ook gebruikt om de uitvoer resultaten van de bewerking inventaris controle te vertegenwoordigen.

| Eigenschap         | Type                                                              | Description                                                                      |
|------------------|-------------------------------------------------------------------|----------------------------------------------------------------------------------|
| productId        | tekenreeks                                                            | Lang De ID van het [product](#product).                            |
| skuId            | tekenreeks                                                            | De ID van de [SKU](#sku). Wanneer u deze resource als invoer voor een inventarisatie aanvraag gebruikt, is deze waarde optioneel. Als deze waarde niet wordt vermeld, worden alle Sku's onder het product beschouwd als doel items van de bewerking inventaris controle.      |
| isRestricted     | booleaans                                                              | Hiermee wordt aangegeven of dit item een beperkte inventaris heeft gevonden.            |
| restrictie     | matrix van [InventoryRestriction](#inventoryrestriction)            | De details van de beperkingen die voor dit item zijn gevonden. Deze eigenschap wordt alleen ingevuld als **isRestricted** = ' True ' is. |

## <a name="inventoryrestriction"></a>InventoryRestriction

Hiermee worden de details van een inventarisatie beperking aangegeven. Dit is alleen van toepassing op uitvoer resultaten van de inventarisatie, niet voor invoer aanvragen.

| Eigenschap         | Type                  | Description                                                                                 |
|------------------|-----------------------|---------------------------------------------------------------------------------------------|
| reasonCode       | tekenreeks                | De code waarmee de reden voor de beperking wordt geïdentificeerd.                                    |
| beschrijving      | tekenreeks                | De beschrijving van de inventarisatie beperking.                                               |
| properties       | sleutel/waarde-paren       | De woorden lijst met eigenschappen die mogelijk meer details over de beperking bieden.           |

## <a name="billingcycletype"></a>BillingCycleType

Een [Enum/DotNet/API/System. enum) met waarden die een type facturerings cyclus aangeven.

| Waarde              | Positie     | Beschrijving                                                                                |
|--------------------|--------------|--------------------------------------------------------------------------------------------|
| Onbekend            | 0            | Enum-initialisatie functie.                                                                          |
| Maandelijks            | 1            | Geeft aan dat de partner maandelijks wordt gefactureerd.                                        |
| Jaarlijks             | 2            | Geeft aan dat de partner jaarlijks wordt gefactureerd.                                       |
| Geen               | 3            | Geeft aan dat er geen kosten in rekening worden gebracht voor de partner. Deze waarde kan worden gebruikt voor proef items.    |
| Eenmalige            | 4            | Geeft aan dat de partner één keer wordt gefactureerd.                                       |
