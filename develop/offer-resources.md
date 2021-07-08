---
title: Resources aanbieden
description: Beschrijft een product dat wordt vermeld in de resellercatalogus dat ze aan hun klanten kunnen aanbieden.
ms.date: 03/15/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 704e5580f2cdf84fc82b627e3b2ca165b81a3af5
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548104"
---
# <a name="offer-resources"></a>Resources aanbieden

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Beschrijft een product dat wordt vermeld in de resellercatalogus dat ze aan hun klanten kunnen aanbieden.

## <a name="offer"></a>Aanbieding

| Eigenschap                    | Type                      | Beschrijving                                                                                                                                                                |
|-----------------------------|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                          | tekenreeks                    | De aanbiedings-id.                                                                                           |
| naam                        | tekenreeks                    | De naam van de aanbieding.                                                                                                 |
| beschrijving                 | tekenreeks                    | Een beschrijving van de aanbieding.                                                                                     |
| minimumQuantity             | int                       | De minimumhoeveelheid die beschikbaar is.                                                                                 |
| maximumQuantity             | int                       | De maximale hoeveelheid die beschikbaar is.                                                                                 |
| positie                        | int                       | De positie of prioriteit van de aanbieding vergeleken met andere categorieën in dezelfde productlijn. Deze eigenschap moet alleen worden ingesteld als er meer dan één aanbieding voor een bepaalde productlijn is.  |
| Uri                         | tekenreeks                    | De aanbiedings-URI.                                                                                                  |
| landinstelling                      | tekenreeks                    | De plaats waar de aanbieding van toepassing is.                                                                          |
| country                     | tekenreeks                    | Het land/de regio waar de aanbieding van toepassing is.                                                                    |
| category                    | [OfferCategory](#offercategory)           | De categorie van de aanbieding.                                                                   |
| limitUnitOfMeasure          | tekenreeks                    | Een waarde die het type aankoopbeperking aangeeft. Mogelijke waarden zijn:<br/> Geen: er zijn geen beperkingen voor het aantal abonnementen op basis van de aangeschafte aanbieding.<br/> Gelijktijdig: het aantal abonnementen dat op een bepaald moment kan bestaan in de tenant van de klant. Dit omvat abonnementen die actief of geannuleerd zijn. Deze waarde geldt vooral voor aanbiedingen van kleine bedrijven waarbij het aantal licenties kleiner is dan 300. Uit inrichting verwijderde abonnementen worden niet meegetelde.<br/> LifeTime: het aantal abonnementen dat kan bestaan voor de levensduur van de tenant van de klant. Deze waarde is het meest van toepassing op proefversies. Uit inrichting verwijderde abonnementen worden niet meegetelde.      |
| limiet                       | int                       | Het aantal abonnementen dat van deze aanbieding kan worden gekocht op basis van de limitUnitOfMeasure.                |
| prerequisiteOffers          | tekenreeks                    | De vereiste aanbiedingen.                                                                                        |
| isAddOn                     | booleaans                   | Een waarde die aangeeft of dit exemplaar een invoegvoeging is.                                                           |
| hasAddOns                   | booleaans                   | Een waarde die aangeeft of deze aanbieding addons heeft.                                                           |
| isAvailableForPurchase      | booleaans                   | Een waarde die aangeeft of dit exemplaar beschikbaar is voor aankoop.                                             |
| facturering                     | tekenreeks                    | Hiermee geeft u het factureringstype op voor de aankoop van het regelitem: 'none', 'usage' of 'license'.                           |
| supportedBillingCycles      | tekenreeksmatrix          | Geeft de factureringscycli aan die worden ondersteund voor deze aanbieding. Ondersteunde waarden zijn de ledennamen in [BillingCycleType](product-resources.md#billingcycletype)   |
| isAutoRenewable             | booleaans                   | Een waarde die aangeeft of de aanbieding automatisch wordt verlengd.                                                      |
| upgradeTargetOffers         | tekenreeksmatrix          | De lijst met aanbiedingen waar deze aanbieding naar kan worden geüpgraded.                                                          |
| conversionTargetOffers      | tekenreeksmatrix          | De lijst met aanbiedingen waar deze aanbieding naar kan worden geconverteerd.                                                         |
| reselleeQualifications      | tekenreeksmatrix          | De kwalificaties die de klant nodig heeft om een partner de aanbieding voor die klant te laten kopen.     |
| resellerQualifications      | tekenreeksmatrix          | De kwalificaties die de partner nodig heeft om de aanbieding voor een klant aan te schaffen.                       |
| salesGroupId                | tekenreeks                    | Een tekenreeks die wordt gebruikt om aanbiedingen in afzonderlijke orders te groepen.                                                             |
| isTrial                     | booleaans                   | Een waarde die aangeeft of dit een proefaanbieding is.                                                               |
| product                     | [OfferProduct](#offerproduct)           | Haalt het product van de aanbieding op.                                                                           |
| unitType                    | tekenreeks                    | Het type van de eenheid.                                                                                      |
| Verwijzigingen                       | [OfferLinks](#offerlinks)               | De koppeling 'Meer informatie' van de aanbieding.                                                                    |
| kenmerken                  | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met de aanbieding.                         |

## <a name="offercategory"></a>OfferCategory

Beschrijft de categorisatie van een aanbieding. Dit omvat de rangschikking of prioriteit van deze aanbiedingscategorie vergeleken met andere producten in dezelfde productlijn.

| Eigenschap   | Type                                                           | Beschrijving                                                                                                                                                                |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id         | tekenreeks                                                         | De categorie-id.                                                                                                                                                   |
| naam       | tekenreeks                                                         | De naam van de categorie.                                                                                                                                                         |
| positie       | int                                                            | De categorierangschikking of prioriteit in vergelijking met andere categorieën in dezelfde aanbieding. Deze eigenschap moet alleen worden ingesteld als er meer dan één aanbiedingscategorie voor een bepaalde aanbieding is. |
| landinstelling     | tekenreeks                                                         | De locale waarin de aanbieding van toepassing is.                                                                                                                        |
| country    | tekenreeks                                                         | Het land of de regio waar de aanbieding van toepassing is.                                                                                                                   |
| Verwijzigingen      | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen die overeenkomen met de OfferCategory.                                                                                                                     |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met de OfferCategory.                                                                                                                |

## <a name="offerlinks"></a>OfferLinks

Bevat koppelingen voor meer informatie over de aanbieding.

| Eigenschap  | Type | Beschrijving                 |
|-----------|------|-----------------------------|
| learnMore | Koppeling | De koppeling 'meer informatie'.      |
| Zelf      | Koppeling | De zelf-URI                |
| volgende      | Koppeling | De volgende pagina met items.     |
| Vorige  | Koppeling | De vorige pagina met items. |

## <a name="offerproduct"></a>OfferProduct

Een product of service waar meer dan één aanbieding aan kan zijn gekoppeld, elk met verschillende functies en gericht op verschillende klantbehoeften.

| Eigenschap | Type   | Beschrijving              |
|----------|--------|--------------------------|
| Id       | tekenreeks | De categorie-id. |
| Name     | tekenreeks | De naam van de categorie.       |
| Eenheid     | tekenreeks | De producteenheid.        |
