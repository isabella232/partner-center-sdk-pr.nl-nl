---
title: Aanbiedings resources
description: Hierin wordt een product beschreven dat wordt vermeld in de wederverkoper-catalogus en dat aan hun klanten kan worden aangeboden.
ms.date: 03/15/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 45af02705d2a03c7586ba6bf3a5537c3e4eec3c7
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767211"
---
# <a name="offer-resources"></a>Aanbiedings resources

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Hierin wordt een product beschreven dat wordt vermeld in de wederverkoper-catalogus en dat aan hun klanten kan worden aangeboden.

## <a name="offer"></a>Aanbieding

| Eigenschap                    | Type                      | Beschrijving                                                                                                                                                                |
|-----------------------------|---------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                          | tekenreeks                    | De aanbiedings-id.                                                                                           |
| naam                        | tekenreeks                    | De naam van de aanbieding.                                                                                                 |
| beschrijving                 | tekenreeks                    | Een beschrijving van de aanbieding.                                                                                     |
| minimumQuantity             | int                       | De minimale beschik bare hoeveelheid.                                                                                 |
| maximumQuantity             | int                       | De Maxi maal beschik bare hoeveelheid.                                                                                 |
| positie                        | int                       | De rang orde van de aanbieding of de prioriteit in vergelijking met andere categorieën in dezelfde product lijn. Deze eigenschap moet alleen worden ingesteld als er meer dan één aanbieding voor een bepaalde product lijn is.  |
| URI                         | tekenreeks                    | De aanbiedings-URI.                                                                                                  |
| landinstelling                      | tekenreeks                    | De land instelling waarin de aanbieding van toepassing is.                                                                          |
| country                     | tekenreeks                    | Het land of de regio waar de aanbieding van toepassing is.                                                                    |
| category                    | [OfferCategory](#offercategory)           | De categorie van de aanbieding.                                                                   |
| limitUnitOfMeasure          | tekenreeks                    | Een waarde die het type aankoop beperking aangeeft. Mogelijke waarden zijn:<br/> Geen: er zijn geen beperkingen voor het aantal abonnementen op basis van de gekochte aanbieding.<br/> ' Gelijktijdig ': het aantal abonnementen dat op een bepaald moment kan bestaan op de Tenant van de klant, inclusief abonnementen die actief of geannuleerd zijn. Deze waarde is vooral van toepassing op kleine bedrijven, waarbij het aantal licenties kleiner is dan 300. De provisionioned-abonnementen tellen niet mee.<br/> ' Levens duur ': het aantal abonnementen dat kan bestaan voor de levens duur van de Tenant van de klant. Deze waarde is het meest van toepassing op experimenten. De provisionioned-abonnementen tellen niet mee.      |
| limiet                       | int                       | Het aantal abonnementen dat kan worden gekocht van deze aanbieding op basis van de limitUnitOfMeasure.                |
| prerequisiteOffers          | tekenreeks                    | De vereiste aanbiedingen.                                                                                        |
| isAddOn                     | booleaans                   | Een waarde die aangeeft of deze instantie een invoeg toepassing is.                                                           |
| hasAddOns                   | booleaans                   | Een waarde die aangeeft of deze aanbieding invoeg toepassingen bevat.                                                           |
| isAvailableForPurchase      | booleaans                   | Een waarde die aangeeft of deze instantie beschikbaar is voor aankoop.                                             |
| facturering                     | tekenreeks                    | Hiermee geeft u het facturerings type voor de aankoop van het regel item op: "geen", "gebruik" of "licentie".                           |
| supportedBillingCycles      | tekenreeksmatrix          | Hiermee worden de facturerings cycli aangegeven die voor deze aanbieding worden ondersteund. Ondersteunde waarden zijn de lidnamen in [BillingCycleType](product-resources.md#billingcycletype)   |
| isAutoRenewable             | booleaans                   | Een waarde die aangeeft of de aanbieding automatisch wordt vernieuwd.                                                      |
| upgradeTargetOffers         | tekenreeksmatrix          | De lijst met aanbiedingen waarvoor deze aanbieding kan worden bijgewerkt.                                                          |
| conversionTargetOffers      | tekenreeksmatrix          | De lijst met aanbiedingen waarnaar deze aanbieding kan worden geconverteerd.                                                         |
| reselleeQualifications      | tekenreeksmatrix          | De kwalificaties die de klant nodig heeft om een partner de aanbieding voor die klant te kunnen kopen.     |
| resellerQualifications      | tekenreeksmatrix          | De kwalificaties die de partner nodig heeft om de aanbieding voor een klant te kunnen kopen.                       |
| salesGroupId                | tekenreeks                    | Een teken reeks die wordt gebruikt om aanbiedingen in afzonderlijke orders te groeperen.                                                             |
| isTrial                     | booleaans                   | Een waarde die aangeeft of dit een proef aanbod is.                                                               |
| product                     | [OfferProduct](#offerproduct)           | Hiermee haalt u het aanbiedings product.                                                                           |
| Unit type                    | tekenreeks                    | Het type eenheid.                                                                                      |
| koppelen                       | [OfferLinks](#offerlinks)               | De koppeling "meer informatie" van de aanbieding.                                                                    |
| kenmerken                  | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met de aanbieding.                         |

## <a name="offercategory"></a>OfferCategory

Hierin wordt de categorisatie van een aanbieding beschreven. Dit omvat de rang of prioriteit van deze aanbiedings categorie vergeleken met andere in dezelfde product lijn.

| Eigenschap   | Type                                                           | Beschrijving                                                                                                                                                                |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id         | tekenreeks                                                         | De categorie-id.                                                                                                                                                   |
| naam       | tekenreeks                                                         | De naam van de categorie.                                                                                                                                                         |
| positie       | int                                                            | De rang orde van de categorie of de prioriteit in vergelijking met andere categorieën in dezelfde aanbieding. Deze eigenschap moet alleen worden ingesteld als er meer dan één aanbiedings categorie is voor een bepaalde aanbieding. |
| landinstelling     | tekenreeks                                                         | De land instelling waarin de aanbieding van toepassing is.                                                                                                                        |
| country    | tekenreeks                                                         | Het land of de regio waar de aanbieding van toepassing is.                                                                                                                   |
| koppelen      | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen die overeenkomen met de OfferCategory.                                                                                                                     |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met de OfferCategory.                                                                                                                |

## <a name="offerlinks"></a>OfferLinks

Bevat koppelingen voor meer informatie over de aanbieding.

| Eigenschap  | Type | Description                 |
|-----------|------|-----------------------------|
| learnMore | Koppeling | De koppeling meer informatie.      |
| Online      | Koppeling | De zelf-URI                |
| volgende      | Koppeling | De volgende pagina met items.     |
| bestaande  | Koppeling | De vorige pagina met items. |

## <a name="offerproduct"></a>OfferProduct

Een product of service waaraan meer dan één aanbieding is gekoppeld, elk met verschillende soorten functies en gericht op verschillende behoeften van de klant.

| Eigenschap | Type   | Description              |
|----------|--------|--------------------------|
| Id       | tekenreeks | De categorie-id. |
| Name     | tekenreeks | De naam van de categorie.       |
| Eenheid     | tekenreeks | De product eenheid.        |
