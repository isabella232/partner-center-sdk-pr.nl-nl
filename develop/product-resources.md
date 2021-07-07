---
title: Resources voor producten
description: Resources die opschatbare goederen of services vertegenwoordigen. Bevat resources voor het beschrijven van het producttype en de vorm (SKU) en voor het controleren van de beschikbaarheid van het product in een inventaris.
ms.date: 04/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1d536cb78c070bd06f4ab9434e066e51fb4c008c
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445881"
---
# <a name="products-resources"></a>Resources voor producten

Resources die opschatbare goederen of services vertegenwoordigen. Bevat resources voor het beschrijven van het producttype en de vorm (SKU) en voor het controleren van de beschikbaarheid van het product in een inventaris.

## <a name="product"></a>Product

Vertegenwoordigt een opschatbare goede of service. Een product op zichzelf is geen opschatbaar item.

| Eigenschap           | Type                          | Beschrijving                                                              |
|--------------------|-------------------------------|--------------------------------------------------------------------------|
| id                 | tekenreeks                        | De id voor dit product.                                                 |
| titel              | tekenreeks                        | De producttitel.                                                       |
| beschrijving        | tekenreeks                        | De productbeschrijving.                                                 |
| productType        | [ItemType](#itemtype)         | Een object dat de typecategorisatie(en) van dit product beschrijft.     |
| isMicrosoftProduct | booleaans                          | Geeft aan of dit een Microsoft-product is.                          |
| publisherName      | tekenreeks                        | De naam van de uitgever van het product, indien beschikbaar.                          |
| Verwijzigingen              | [ProductLinks](#productlinks) | De resourcekoppelingen in het product.                         |

## <a name="itemtype"></a>ItemType

Vertegenwoordigt het type product.

| Eigenschap        | Type                          | Beschrijving                                                                          |
|-----------------|-------------------------------|--------------------------------------------------------------------------------------|
| id              | tekenreeks                        | De type-id.                                                                 |
| displayName     | tekenreeks                        | De weergavenaam voor dit type.                                                      |
| Subtype         | [ItemType](#itemtype)         | Optioneel. Een object dat een subtypecategorisatie voor dit itemtype beschrijft.     |

## <a name="productlinks"></a>ProductLinks

Bevat een lijst met koppelingen voor een [Product](#product).

| Eigenschap        | Type                                                          | Beschrijving                                          |
|-----------------|---------------------------------------------------------------|------------------------------------------------------|
| Sku 's            | [Koppeling](utility-resources.md#link)                             | De koppeling voor toegang tot de onderliggende SKU's.          |
| Verwijzigingen           | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen in deze resource.   |

## <a name="sku"></a>Sku

Vertegenwoordigt een afneembare Stock Keeping Unit (SKU) onder een product. Deze vertegenwoordigen de verschillende vormen van het product.

| Eigenschap               | Type             | Beschrijving                                                                           |
|------------------------|------------------|---------------------------------------------------------------------------------------|
| id                     | tekenreeks           | De id voor deze SKU. Deze id is alleen uniek binnen de context van het bovenliggende product. |
| titel                  | tekenreeks           | De titel van de SKU.                                                                 |
| beschrijving            | tekenreeks           | De beschrijving van de SKU.                                                           |
| productId              | tekenreeks           | De id van het bovenliggende [product](#product) dat deze SKU bevat.                      |
| minimumQuantity        | int              | De minimaal toegestane hoeveelheid voor aankoop.                                            |
| maximumQuantity        | int              | De maximale hoeveelheid die is toegestaan voor aankoop.                                            |
| isTrial                | booleaans             | Geeft aan of deze SKU een proefversie is.                                           |
| supportedBillingCycles | tekenreeksmatrix | De lijst met ondersteunde factureringscycli voor deze SKU. Ondersteunde waarden zijn de ledennamen in [BillingCycleType.](#billingcycletype) |
| purchasePrerequisites  | tekenreeksmatrix | De lijst met vereiste stappen of acties die nodig zijn voordat u dit item aanschaft. De ondersteunde waarden zijn:<br/>  'InventoryCheck': geeft aan dat de inventaris van het item moet worden geëvalueerd voordat u dit item probeert aan te schaffen.<br/> AzureSubscriptionRegistration: geeft aan dat een Azure-abonnement nodig is en moet worden geregistreerd voordat u dit item aanschaft.  |
| inventoryVariables     | tekenreeksmatrix | De lijst met variabelen die nodig zijn voor het uitvoeren van een inventariscontrole op dit item. De ondersteunde waarden zijn:<br/> CustomerId: de id van de klant voor de aankoop.<br/> AzureSubscriptionId: de id van het Azure-abonnement dat wordt gebruikt voor een aankoop van een Azure-reservering.</br> 'ArmRegionName': de regio waarvoor de inventaris moet worden gecontroleerd. Deze waarde moet overeenkomen met de 'ArmRegionName' van de DynamicAttributes van de SKU. |
| provisioningVariables  | tekenreeksmatrix | De lijst met variabelen die moeten worden opgegeven in de inrichtingscontext van een [winkelwagenlijnitem](cart-resources.md#cartlineitem) bij de aankoop van dit item. De ondersteunde waarden zijn:<br/> Bereik: het bereik voor een aankoop van een Azure-reservering: 'Single', 'Shared'.<br/> SubscriptionId: de id van het Azure-abonnement dat wordt gebruikt voor de aankoop van een Azure-reservering.<br/> "Duration" : de duur van de Azure-reservering: "1Year", "3Year".  |
| dynamicAttributes      | sleutel-waardeparen  | De woordenlijst met dynamische eigenschappen die van toepassing zijn op dit item. De eigenschappen in deze woordenlijst zijn dynamisch en kunnen zonder kennisgeving worden gewijzigd. Maak geen sterke afhankelijkheden van bepaalde sleutels die in de waarde van deze eigenschap bestaan.    |
| Verwijzigingen                  | [ResourceLinks](utility-resources.md#resourcelinks) | De resourcekoppelingen in de SKU.                   |

## <a name="availability"></a>Beschikbaarheid

Vertegenwoordigt een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land, valuta en branchesegment).

| Eigenschap        | Type                        | Beschrijving                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------------------------------|
| id              | tekenreeks                        | De id voor deze beschikbaarheid. Deze id is alleen uniek binnen de context van het bovenliggende [product](#product) en [de SKU](#sku). **Opmerking** Deze id kan na een periode worden gewijzigd. U moet slechts binnen een korte periode na het ophalen van deze waarde vertrouwen op deze waarde.  |
| productId       | tekenreeks                        | De id van het [product](#product) dat deze beschikbaarheid bevat.           |
| skuId           | tekenreeks                        | De id van de [SKU](#sku) die deze beschikbaarheid bevat.                   |
| catalogItemId   | tekenreeks                        | De unieke id voor dit item in de catalogus. Dit is de id die moet worden ingevuld in de eigenschappen [OrderLineItem.OfferId](order-resources.md#orderlineitem) of [CartLineItem.CatalogItemId](cart-resources.md#cartlineitem) wanneer u de bovenliggende [SKU aanschaft.](#sku) **Opmerking** Deze id kan na een periode worden gewijzigd. U moet slechts binnen een korte tijd na het ophalen van deze waarde op deze waarde vertrouwen. Deze mag alleen worden gebruikt en gebruikt op het moment van aankoop.  |
| defaultCurrency | tekenreeks                        | De standaardvaluta die wordt ondersteund voor deze beschikbaarheid.                               |
| segment         | tekenreeks                        | Het branchesegment voor deze beschikbaarheid. Ondersteunde waarden zijn: Commercieel, Onderwijs, Overheid, NonProfit. |
| country         | tekenreeks                                              | Het land of de regio (in de ISO-landcodeindeling) waar deze beschikbaarheid van toepassing is. |
| isAankoopbaar   | booleaans                                                | Geeft aan of deze beschikbaarheid opschatbaar is. |
| isRenewable     | booleaans                                                | Geeft aan of deze beschikbaarheid verlengbaar is. |
| product      | [Product](#product)               | Het product waar deze beschikbaarheid mee overeenkomt. |
| sku          | [SKU](#sku)            | De SKU waar deze beschikbaarheid mee overeenkomt. |
| Voorwaarden           | matrix met [Term-resources](#term)  | De verzameling termen die van toepassing zijn op deze beschikbaarheid. |
| Verwijzigingen           | [ResourceLinks](utility-resources.md#resourcelinks) | De resourcekoppelingen die zijn opgenomen in de beschikbaarheid. |

## <a name="term"></a>Termijn

Vertegenwoordigt een periode waarvoor de beschikbaarheid kan worden aangeschaft.

| Eigenschap              | Type                                        | Beschrijving                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| duur              | tekenreeks                                      | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn P1M (1 maand), P1Y (1 jaar) en P3Y (3 jaar). |
| beschrijving           | tekenreeks                                      | De beschrijving van de term.           |

## <a name="inventorycheckrequest"></a>InventoryCheckRequest

Vertegenwoordigt een aanvraag om de inventaris te controleren op bepaalde catalogusitems.

| Eigenschap         | Type                                                | Beschrijving                                                                                 |
|------------------|-----------------------------------------------------|---------------------------------------------------------------------------------------------|
| targetItems      | matrix van [InventoryItem](#inventoryitem)            | De lijst met catalogusitems die door de inventariscontrole worden geëvalueerd.                           |
| inventoryContext | sleutel-waardeparen                                     | De woordenlijst met contextwaarden die nodig zijn om de inventariscontrole(s) uit te voeren. Elke [SKU](#sku) van de producten definieert welke waarden (indien van) nodig zijn om deze bewerking uit te voeren.  |
| Verwijzigingen            | [ResourceLinks](utility-resources.md#resourcelinks) | De resourcekoppelingen in de inventariscontroleaanvraag.                            |

## <a name="inventoryitem"></a>InventoryItem

Vertegenwoordigt één item in een inventariscontrolebewerking. Deze resource wordt gebruikt voor het opgeven van de doelitems in een invoeraanvraag en wordt ook gebruikt om de uitvoerresultaten van de inventariscontrolebewerking weer te geven.

| Eigenschap         | Type                                                              | Beschrijving                                                                      |
|------------------|-------------------------------------------------------------------|----------------------------------------------------------------------------------|
| productId        | tekenreeks                                                            | (vereist) De id van het [product](#product).                            |
| skuId            | tekenreeks                                                            | De id van de [SKU](#sku). Wanneer u deze resource als invoer voor een inventarisaanvraag gebruikt, is deze waarde optioneel. Als deze waarde niet is opgegeven, worden alle SKU's onder het product beschouwd als doelitems van de inventariscontrolebewerking.      |
| isRestricted     | booleaans                                                              | Geeft aan of dit item een beperkte inventaris heeft.            |
| Beperkingen     | matrix van [InventoryRestriction](#inventoryrestriction)            | De details van eventuele beperkingen die voor dit item worden gevonden. Deze eigenschap wordt alleen ingevuld als **isRestricted** = "true". |

## <a name="inventoryrestriction"></a>InventoryRestriction

Vertegenwoordigt de details van een inventarisbeperking. Dit is alleen van toepassing op uitvoerresultaten van inventariscontrole, niet voor invoeraanvragen.

| Eigenschap         | Type                  | Beschrijving                                                                                 |
|------------------|-----------------------|---------------------------------------------------------------------------------------------|
| reasonCode       | tekenreeks                | De code die de reden voor de beperking aangeeft.                                    |
| beschrijving      | tekenreeks                | De beschrijving van de inventarisbeperking.                                               |
| properties       | sleutel-waardeparen       | De woordenlijst met eigenschappen die mogelijk meer informatie over de beperking bieden.           |

## <a name="billingcycletype"></a>BillingCycleType

Een [Enum/dotnet/api/system.enum) met waarden die een type factureringscyclus aangeven.

| Waarde              | Positie     | Beschrijving                                                                                |
|--------------------|--------------|--------------------------------------------------------------------------------------------|
| Onbekend            | 0            | Enum initializer.                                                                          |
| Maandelijks            | 1            | Geeft aan dat er maandelijks kosten in rekening worden gebracht voor de partner.                                        |
| Jaarlijks             | 2            | Geeft aan dat er jaarlijks kosten in rekening worden gebracht voor de partner.                                       |
| Geen               | 3            | Geeft aan dat er geen kosten in rekening worden gebracht voor de partner. Deze waarde kan worden gebruikt voor proefitems.    |
| Onetime            | 4            | Geeft aan dat er één keer kosten in rekening worden gebracht voor de partner.                                       |
