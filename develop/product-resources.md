---
title: Resources voor producten
description: Resources die opschatbare goederen of services vertegenwoordigen. Bevat resources voor het beschrijven van het producttype en de vorm (SKU) en voor het controleren van de beschikbaarheid van het product in een inventaris.
ms.date: 02/16/2016
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 3790d8f5ef154c637dfd3f3d014322d314757f26
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/03/2021
ms.locfileid: "123456066"
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

| Eigenschap        | Type                                                          | Description                                          |
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
| purchasePrerequisites  | tekenreeksmatrix | De lijst met vereiste stappen of acties die nodig zijn voordat u dit item aanschaft. De ondersteunde waarden zijn:<br/>  InventoryCheck: geeft aan dat de inventaris van het item moet worden geëvalueerd voordat u dit item aanschaft.<br/> AzureSubscriptionRegistration: geeft aan dat een Azure-abonnement nodig is en moet worden geregistreerd voordat u dit item aanschaft.  |
| inventoryVariables     | tekenreeksmatrix | De lijst met variabelen die nodig zijn voor het uitvoeren van een inventariscontrole op dit item. De ondersteunde waarden zijn:<br/> CustomerId: de id van de klant voor de aankoop.<br/> 'AzureSubscriptionId': de id van het Azure-abonnement dat wordt gebruikt voor een azure-reserveringsaankoop.</br> 'ArmRegionName': de regio waarvoor de inventaris moet worden gecontroleerd. Deze waarde moet overeenkomen met de 'ArmRegionName' van de DynamicAttributes van de SKU. |
| provisioningVariables  | tekenreeksmatrix | De lijst met variabelen die moeten worden opgegeven in de inrichtingscontext van een [winkelwagenlijnitem](cart-resources.md#cartlineitem) bij het kopen van dit item. De ondersteunde waarden zijn:<br/> Bereik: het bereik voor een Azure-reserveringsaankoop: 'Single', 'Shared'.<br/> SubscriptionId: de id van het Azure-abonnement dat wordt gebruikt voor een azure-reserveringsaankoop.<br/> "Duur" : de duur van de Azure-reservering: "1Year", "3Year".  |
| dynamicAttributes      | sleutel-waardeparen  | De woordenlijst met dynamische eigenschappen die van toepassing zijn op dit item. De eigenschappen in deze woordenlijst zijn dynamisch en kunnen zonder kennisgeving worden gewijzigd. U moet geen sterke afhankelijkheden maken van bepaalde sleutels die bestaan in de waarde van deze eigenschap.    |
| Verwijzigingen                  | [ResourceLinks](utility-resources.md#resourcelinks) | De resourcekoppelingen in de SKU.                   |
| AttestationProperties                  | [AttestationProperties](#attestationproperties) | De attestation-eigenschappen voor een SKU.                   |

## <a name="dynamic-sku-attributes"></a>Dynamische SKU-kenmerken

Belangrijke eigenschappen die relevant zijn voor nieuwe producten en services op basis van handelslicenties.

> [!Note] 
> Nieuwe handelswijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de technical preview van de nieuwe commerce-ervaring M365/D365

| Eigenschap        | Type                        | Description                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------------------------------|
|hasConstraints|booleaans|Beschrijft of de SKU assetContraints bevat|
|isAddon|booleaans|Beschrijft of de SKU een add-on is|
|prerequisiteSkus|tekenreeksmatrix|Beschrijft producten en SKU's waar de invoeging mee kan werken|
|upgradeTargetOffers|tekenreeksmatrix|Een lijst met producten en SKU's waar het item naar kan worden geupgraded|
|perstionInstructions|lijst met opsommingenInstructies|Lijst met instructies die van toepassing zijn op deat-bewerkingen|

## <a name="availability"></a>Beschikbaarheid

Vertegenwoordigt een configuratie waarin een SKU beschikbaar is voor aankoop (zoals land, valuta en branchesegment).

| Eigenschap        | Type                        | Beschrijving                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------------------------------|
| id              | tekenreeks                        | De id voor deze beschikbaarheid. Deze id is alleen uniek binnen de context van het bovenliggende [product](#product) en [de SKU](#sku). **Opmerking** Deze id kan na een periode worden gewijzigd. U moet alleen vertrouwen op deze waarde binnen een korte periode nadat u deze hebt opgehaald.  |
| productId       | tekenreeks                        | De id van het [product](#product) dat deze beschikbaarheid bevat.           |
| skuId           | tekenreeks                        | De id van de [SKU](#sku) die deze beschikbaarheid bevat.                   |
| catalogItemId   | tekenreeks                        | De unieke id voor dit item in de catalogus. Dit is de id die moet worden ingevuld in de eigenschappen [OrderLineItem.OfferId](order-resources.md#orderlineitem) of [CartLineItem.CatalogItemId](cart-resources.md#cartlineitem) bij het kopen van de bovenliggende [SKU.](#sku) **Opmerking** Deze id kan na een periode worden gewijzigd. U moet slechts binnen een korte tijd na het ophalen van deze waarde op deze waarde vertrouwen. Deze mag alleen worden gebruikt en gebruikt op het moment van aankoop.  |
| defaultCurrency | tekenreeks                        | De standaardvaluta die wordt ondersteund voor deze beschikbaarheid.                               |
| segment         | tekenreeks                        | Het segment branche voor deze beschikbaarheid. Ondersteunde waarden zijn: Commercieel, Onderwijs, Overheid, NonProfit. |
| country         | tekenreeks                                              | Het land of de regio (in de ISO-landcodeindeling) waar deze beschikbaarheid van toepassing is. |
| isAankoopbaar   | booleaans                                                | Geeft aan of deze beschikbaarheid opschatbaar is. |
| isRenewable     | booleaans                                                | Geeft aan of deze beschikbaarheid kan worden verlengd. |
| RenewalInstructions     | RenewalInstruction                                              | Vertegenwoordigt vernieuwingsinstructies voor een bepaalde beschikbaarheid. |
| product      | [Product](#product)               | Het product waar deze beschikbaarheid mee overeenkomt. |
| sku          | [SKU](#sku)            | De SKU waar deze beschikbaarheid mee overeenkomt. |
| Voorwaarden           | matrix van [Term-resources](#term)  | De verzameling termen die van toepassing zijn op deze beschikbaarheid. |
| Verwijzigingen           | [ResourceLinks](utility-resources.md#resourcelinks) | De resourcekoppelingen die zijn opgenomen in de beschikbaarheid. |

## <a name="renewal-instruction"></a>Verlengingsinstructie

> [!Note] 
> Nieuwe handelswijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de technical preview van de nieuwe commerce-ervaring M365/D365
> 

Vertegenwoordigt vernieuwingsinstructies voor een bepaalde beschikbaarheid.

| Eigenschap        | Type                        | Description                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------|
| applicableTermIds       | tekenreeksmatrix                       | Term-ID's waar de instructies op van toepassing zijn |
| RenewalOptions       | matrix van RenewalOption                     | Opties voor het definiëren van vernieuwingen |

## <a name="renewaloption"></a>RenewalOption    

> [!Note] 
> Nieuwe handelswijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de technical preview van de nieuwe commerce-ervaring M365/D365
> 

Vertegenwoordigt vernieuwingsinstructies voor een bepaalde beschikbaarheid.

| Eigenschap        | Type                        | Description                                                                         |
|-----------------|-----------------------------------------------------|-------------------------------------------------------------|
| renewToId       | Tekenreeks       | Vertegenwoordigt het product en de SKU om te vernieuwen |
| isAutoRenewable       | Booleaanse waarde       | Of de beschikbaarheid automatisch kan worden vernieuwd |

## <a name="term"></a>Termijn

Vertegenwoordigt een term waarvoor de beschikbaarheid kan worden aangeschaft.

| Eigenschap              | Type                                        | Description                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| duur              | tekenreeks                                      | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn P1M (1 maand), P1Y (1 jaar) en P3Y (3 jaar). |
| beschrijving           | tekenreeks                                      | De beschrijving van de term.           |

## <a name="inventorycheckrequest"></a>InventoryCheckRequest

Vertegenwoordigt een aanvraag om de inventaris te controleren op bepaalde catalogusitems.

| Eigenschap         | Type                                                | Description                                                                                 |
|------------------|-----------------------------------------------------|---------------------------------------------------------------------------------------------|
| targetItems      | matrix van [InventoryItem](#inventoryitem)            | De lijst met catalogusitems die tijdens de inventarisatiecontrole worden geëvalueerd.                           |
| inventoryContext | sleutel-waardeparen                                     | De woordenlijst met contextwaarden die nodig zijn om de inventariscontrole(s) uit te voeren. Elke [SKU](#sku) van de producten definieert welke waarden (indien van beide) nodig zijn om deze bewerking uit te voeren.  |
| Verwijzigingen            | [ResourceLinks](utility-resources.md#resourcelinks) | De resourcekoppelingen in de inventariscontroleaanvraag.                            |

## <a name="inventoryitem"></a>InventoryItem

Vertegenwoordigt één item in een inventariscontrolebewerking. Deze resource wordt gebruikt voor het opgeven van de doelitems in een invoeraanvraag en wordt ook gebruikt om de uitvoerresultaten van de inventariscontrolebewerking weer te geven.

| Eigenschap         | Type                                                              | Description                                                                      |
|------------------|-------------------------------------------------------------------|----------------------------------------------------------------------------------|
| productId        | tekenreeks                                                            | (Vereist) De id van het [product](#product).                            |
| skuId            | tekenreeks                                                            | De id van de [SKU](#sku). Wanneer u deze resource gebruikt als invoer voor een inventarisaanvraag, is deze waarde optioneel. Als deze waarde niet is opgegeven, worden alle SKU's onder het product beschouwd als doelitems van de inventariscontrolebewerking.      |
| isRestricted     | booleaans                                                              | Geeft aan of dit item een beperkte inventaris heeft.            |
| Beperkingen     | matrix van [InventoryRestriction](#inventoryrestriction)            | De details van eventuele beperkingen die voor dit item zijn gevonden. Deze eigenschap wordt alleen ingevuld als **isRestricted** = "true". |

## <a name="inventoryrestriction"></a>InventoryRestriction

Vertegenwoordigt de details van een inventarisbeperking. Dit is alleen van toepassing op uitvoerresultaten van inventariscontrole, niet voor invoeraanvragen.

| Eigenschap         | Type                  | Description                                                                                 |
|------------------|-----------------------|---------------------------------------------------------------------------------------------|
| reasonCode       | tekenreeks                | De code die de reden voor de beperking aangeeft.                                    |
| beschrijving      | tekenreeks                | De beschrijving van de inventarisbeperking.                                               |
| properties       | sleutel-waardeparen       | De woordenlijst met eigenschappen die mogelijk meer informatie over de beperking biedt.           |

## <a name="billingcycletype"></a>BillingCycleType

Een [Enum/dotnet/api/system.enum) met waarden die een type factureringscyclus aangeven.

| Waarde              | Positie     | Beschrijving                                                                                |
|--------------------|--------------|--------------------------------------------------------------------------------------------|
| Onbekend            | 0            | Initialisatie van de enum.                                                                          |
| Maandelijks            | 1            | Geeft aan dat er maandelijks kosten in rekening worden gebracht voor de partner.                                        |
| Jaarlijks             | 2            | Geeft aan dat er jaarlijks kosten in rekening worden gebracht voor de partner.                                       |
| Geen               | 3            | Geeft aan dat er geen kosten in rekening worden gebracht voor de partner. Deze waarde kan worden gebruikt voor proefitems.    |
| Onetime            | 4            | Geeft aan dat er één keer kosten in rekening worden gebracht voor de partner.                                       |

## <a name="attestationproperties"></a>AttestationProperties

Vertegenwoordigt een attestation-type en als dit vereist is voor aankoop.

| Eigenschap              | Type                                        | Description                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| attestationType              | tekenreeks                                      | Geeft het attestation-type aan. Voor Windows 365 is de waarde Windows365. Windows 365 Attestation is de tekst 'Ik begrijp dat elke persoon die Windows 365 Business met Windows Hybrid Benefit gebruikt, ook een geldige kopie van Windows 10/11 Pro moet hebben geïnstalleerd op het primaire werkapparaat.' |
| enforceAttestation           | booleaans                                      | Geeft aan of attestation vereist is voor aankoop.           |
