---
title: Resources aanbieden
description: Beschrijft een product dat wordt vermeld in de resellercatalogus dat ze aan hun klanten kunnen aanbieden.
ms.date: 03/15/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9a7a0dd2dccc59536797c3ce533d9d8829a04f96
ms.sourcegitcommit: 59950cf131440786779c8926be518c2dc4bc4030
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/31/2021
ms.locfileid: "115009219"
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
| minimumQuantity             | int                       | De minimale hoeveelheid die beschikbaar is.                                                                                 |
| maximumQuantity             | int                       | De maximale hoeveelheid die beschikbaar is.                                                                                 |
| positie                        | int                       | De positie of prioriteit van de aanbieding in vergelijking met andere categorieën in dezelfde productlijn. Deze eigenschap moet alleen worden ingesteld als er meer dan één aanbieding voor een bepaalde productlijn is.  |
| Uri                         | tekenreeks                    | De aanbiedings-URI.                                                                                                  |
| landinstelling                      | tekenreeks                    | De locale waarin de aanbieding van toepassing is.                                                                          |
| country                     | tekenreeks                    | Het land/de regio waar de aanbieding van toepassing is.                                                                    |
| category                    | [OfferCategory](#offercategory)           | De categorie van de aanbieding.                                                                   |
| limitUnitOfMeasure          | tekenreeks                    | Een waarde die het type aankoopbeperking aangeeft. Mogelijke waarden zijn:<br/> Geen: er zijn geen beperkingen voor het aantal abonnementen op basis van de aangeschafte aanbieding.<br/> Gelijktijdig: het aantal abonnementen dat op een bepaald moment op de tenant van de klant kan bestaan. Dit omvat abonnementen die actief of geannuleerd zijn. Deze waarde geldt vooral voor aanbiedingen voor kleine bedrijven waarbij het aantal licenties kleiner is dan 300. Uit de inrichting verwijderde abonnementen worden niet meegetelde.<br/> LifeTime: het aantal abonnementen dat kan bestaan voor de levensduur van de tenant van de klant. Deze waarde is het meest van toepassing op proefversies. Uit de inrichting verwijderde abonnementen worden niet meegetelde.      |
| limiet                       | int                       | Het aantal abonnementen dat van deze aanbieding kan worden gekocht op basis van de limitUnitOfMeasure.                |
| prerequisiteOffers          | tekenreeks                    | De vereiste aanbiedingen.                                                                                        |
| isAddOn                     | booleaans                   | Een waarde die aangeeft of dit exemplaar een invoegvoeging is.                                                           |
| hasAddOns                   | booleaans                   | Een waarde die aangeeft of deze aanbieding addons heeft.                                                           |
| isAvailableForPurchase      | booleaans                   | Een waarde die aangeeft of dit exemplaar beschikbaar is voor aankoop.                                             |
| facturering                     | tekenreeks                    | Hiermee geeft u het factureringstype voor de aankoop van het regelitem op: 'geen', 'gebruik' of 'licentie'.                           |
| supportedBillingCycles      | tekenreeksmatrix          | Geeft de factureringscycli aan die worden ondersteund voor deze aanbieding. Ondersteunde waarden zijn de ledennamen in [BillingCycleType](product-resources.md#billingcycletype)   |
| isAutoRenewable             | booleaans                   | Een waarde die aangeeft of de aanbieding automatisch wordt verlengd.                                                      |
| upgradeTargetOffers         | tekenreeksmatrix          | De lijst met aanbiedingen waar deze aanbieding naar kan worden geüpgraded.                                                          |
| conversionTargetOffers      | tekenreeksmatrix          | De lijst met aanbiedingen waar deze aanbieding naar kan worden geconverteerd.                                                         |
| reselleeQualifications      | tekenreeksmatrix          | De kwalificaties die de klant nodig heeft om een partner de aanbieding voor die klant te laten kopen.     |
| resellerQualifications      | tekenreeksmatrix          | De kwalificaties die de partner nodig heeft om de aanbieding voor een klant te kopen.                       |
| salesGroupId                | tekenreeks                    | Een tekenreeks die wordt gebruikt om aanbiedingen te groepen in afzonderlijke orders.                                                             |
| isTrial                     | booleaans                   | Een waarde die aangeeft of dit een proefabonnement is.                                                               |
| product                     | [OfferProduct](#offerproduct)           | Haalt het aanbiedingsproduct op.                                                                           |
| unitType                    | tekenreeks                    | Het type van de eenheid.                                                                                      |
| Verwijzigingen                       | [OfferLinks](#offerlinks)               | De koppeling 'Meer informatie' van de aanbieding.                                                                    |
| kenmerken                  | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met de aanbieding.                         |
| AttestationProperties       | [AttestationProperties](#attestationproperties) | De attestation-eigenschappen voor een SKU.                   |

## <a name="offercategory"></a>OfferCategory

Beschrijft de categorisatie van een aanbieding. Dit omvat de rangschikking of prioriteit van deze aanbiedingscategorie vergeleken met andere producten in dezelfde productlijn.

| Eigenschap   | Type                                                           | Beschrijving                                                                                                                                                                |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id         | tekenreeks                                                         | De categorie-id.                                                                                                                                                   |
| naam       | tekenreeks                                                         | De categorienaam.                                                                                                                                                         |
| positie       | int                                                            | De categorierangschikking of prioriteit in vergelijking met andere categorieën in dezelfde aanbieding. Deze eigenschap moet alleen worden ingesteld als er meer dan één aanbiedingscategorie voor een bepaalde aanbieding is. |
| landinstelling     | tekenreeks                                                         | De locale waarin de aanbieding van toepassing is.                                                                                                                        |
| country    | tekenreeks                                                         | Het land/de regio waar de aanbieding van toepassing is.                                                                                                                   |
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
| Naam     | tekenreeks | De categorienaam.       |
| Eenheid     | tekenreeks | De producteenheid.        |

## <a name="attestationproperties"></a>AttestationProperties

Vertegenwoordigt een attestation-type en als dit vereist is voor aankoop.

| Eigenschap              | Type                                        | Beschrijving                                                                         |
|-----------------------|-----------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|
| attestationType              | tekenreeks                                      | Geeft het attestation-type aan. Voor Windows 365 is de waarde Windows365. Windows 365 Attestation is de tekst 'Ik begrijp dat elke persoon die Windows 365 Business gebruikt met Windows Hybrid Benefit ook een geldige kopie van Windows 10/11 Pro moet hebben geïnstalleerd op hun primaire werkapparaat.' |
| enforceAttestation           | booleaans                                      | Geeft aan of attestation vereist is voor aankoop.           |

