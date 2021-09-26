---
title: Promotie-resources
description: Beschrijft de resources voor promoties die worden toegepast op transacties voor nieuwe commerce-abonnementen.
ms.date: 09/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 6a0b38576f5756a127fe6ba787f970db9ac59be3
ms.sourcegitcommit: 7be22de808a10fa2d05577d6497086c8ca3f678a
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/24/2021
ms.locfileid: "128715983"
---
# <a name="promotions-resources"></a>Resources voor promoties

**Van toepassing op**

- Partnercentrum

**Juiste rollen**

- Globale beheerder
- Beheeragent

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de Microsoft 365 en Dynamics 365 New Commerce Experience Technical Preview.

Beschrijft de resources voor promoties die worden toegepast op transacties voor nieuwe commerce-abonnementen.

## <a name="promotion"></a>Promotie

Korting die wordt toegepast bij het kopen van een product-SKU als aan de geschiktheidscriteria wordt voldaan.

| Eigenschap          | Type                    | Beschrijving                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| id | tekenreeks                  | De promotie-id. |
| naam | tekenreeks                  | De gebruiksvriendelijke naam van de promotie. |
| beschrijving | tekenreeks                  | Een beschrijving van de promotie. |
| Startdate | tekenreeks | De begindatum waarop de promotie van toepassing is. |
| Enddate | tekenreeks  | De einddatum voor wanneer de promotie van toepassing is. |
| requiredProducts | lijst met requiredProducts | Product-, SKU-details en prijsbeleid voor de promotie is van toepassing. | 
| properties | lijst met eigenschappen | Eigenschappen voor de promotie, waaronder of de promotie automatisch van toepassing is. | 

## <a name="requiredproducts"></a>RequiredProducts

Product-, SKU-details en prijsbeleid voor de promotie is van toepassing.

| Eigenschap          | Type                    | Beschrijving                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| productId| tekenreeks | Een id van het product waar de promotie voor beschikbaar is. |
| skuId | tekenreeks | Een id van de SKU waar de promotie voor beschikbaar is. |
| Termijn | Termijn | Een termijn met inbegrip van de duur van de termijn en de factureringscyclus voor de promotie is beschikbaar. |
| pricingPolicies| Lijst met pricingPolicies | Een lijst met beleidsregels die de typen en waarden voor promotiekorting definiëren. |

## <a name="term"></a>Termijn

Vertegenwoordigt een periode waarvoor de promotie kan worden aangeschaft.

| Eigenschap          | Type                    | Beschrijving                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| duur          | tekenreeks                  | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn P1M (één maand), P1Y (één jaar) en P3Y (drie jaar). 
| billingCycle      | tekenreeks | Beschrijft hoe vaak de promotie wordt toegepast op de facturering. Waarden kunnen maandelijks, jaarlijks, onetime of onbekend zijn. | 

## <a name="pricingpolicies"></a>PricingPolicies

Beschrijf de typen en waarden voor promotiekorting.

| Eigenschap          | Type               | Beschrijving                                                                  |          
|-------------------|--------------------|------------------------------------------------------------------------------|
| type | tekenreeks | Beschrijf of de korting is gebaseerd op percentages of vast tariefkortingen. |
| waarde | tekenreeks  | Hiermee definieert u de hoeveelheid korting die wordt toegepast. |

## <a name="properties"></a>Eigenschappen

Eigenschappen voor de promotie.

| Eigenschap          | Type               | Beschrijving                                        |
|-------------------|--------------------|----------------------------------------------------|
| isAutoApplicable  | booleaans  | Geeft aan of de promotie automatisch wordt toegepast of dat deze moet worden doorgegeven door de partner. |


## <a name="promotioneligibilitiesrequestitem"></a>PromotionEligibilitiesRequestItem

Eigenschappen die een transactie vertegenwoordigen en de geschiktheid van een promotie.

| Eigenschap          | Type               | Beschrijving                                        |
|-------------------|--------------------|----------------------------------------------------|
| id | int| De item-id voor geschiktheid voor promoties. |
| catalogItemId | tekenreeks | De id van het catalogusitem op de promotie wordt toegepast. Bevat de product-id, SKU-id en beschikbaarheids-id. |
| quantity | int | Het aantal licenties of instanties. |
| termDuration | tekenreeks | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn P1M (één maand), P1Y (één jaar) en P3Y (drie jaar). |
| billingCycle | tekenreeks | Beschrijft hoe vaak de promotie wordt toegepast op de facturering. Waarden kunnen maandelijks, jaarlijks, onetime of onbekend zijn. | 
| promotionID | tekenreeks | De promotie-id. |

## <a name="promotioneligibilities"></a>PromotieEligibilities

Een lijst met producten, SKU's en de geschiktheid voor promotie.

| Eigenschap          | Type               | Beschrijving                                        |
|-------------------|--------------------|----------------------------------------------------|
| id | int| De item-id voor de geschiktheid voor promoties. |
| catalogItemId | tekenreeks | De id van het catalogusitem op de promotie wordt toegepast. Bevat de product-id, SKU-id en beschikbaarheids-id. |
| quantity | int | Het aantal licenties of exemplaren. |
| termDuration | tekenreeks | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn P1M (één maand), P1Y (één jaar) en P3Y (drie jaar). |
| billingCycle | tekenreeks | Beschrijft hoe vaak de promotie wordt toegepast op de facturering. Waarden kunnen maandelijks, jaarlijks, onetime of onbekend zijn. | 
| geschiktheid | Lijst met PromotieEligibiliteiten | Vertegenwoordigt een lijst met resultaten die in aanmerking komen voor promotie. |

## <a name="promotioneligibility"></a>NiveaupromotieEligheid

Een lijst met producten, SKU's en de geschiktheid voor promotie.

| Eigenschap          | Type               | Beschrijving                                        |
|-------------------|--------------------|----------------------------------------------------|
| promotionId | tekenreeks | De promotie-id. |
| isEligible | booleaans | Beschrijft of de promotie in aanmerking komt voor het opgegeven aanvraagitem voor geschiktheid. |
| fouten | Lijst met PromotionEligibilityErrors | Fouten die beschrijven waarom een aanvraagitem voor promotie-geschiktheid niet in aanmerking kwam. | 

## <a name="promotioneligibilityerror"></a>PromotionEligibilityError

Legt uit waarom een aanvraagitem voor geschiktheid voor een promotie niet in aanmerking kwam. 

| Eigenschap          | Type               | Beschrijving                                        |
|-------------------|--------------------|----------------------------------------------------|
| type | tekenreeks | De fouttypen voor promotiegegeerdheid kunnen bestaan uit InvalidCatalogItemId, InvalidPromotion, PrerequisiteProductOwnership, RedemptionLimit, SeatCount, OfferPurchasedPreviously of Term. |
| beschrijving | tekenreeks | Beschrijft of de promotie in aanmerking komt voor het opgegeven aanvraagitem voor geschiktheid. |

## <a name="redemptionlimitpromotioneligibilityerror"></a>RedemptionLimitPromotionEligibilityError

Bevat details over waarom de inwissellimiet is overschreden.

| Eigenschap          | Type               | Beschrijving                                        |
|-------------------|--------------------|----------------------------------------------------|
| maxPromotionRedemptionCount | int | Het maximum aantal keren dat een promotie kan worden verkregen. |
| remainingPromotionRedemptionCount| int | Het resterende aantal keren dat een promotie kan worden verkregen. |

## <a name="seatcountpromotioneligibilityerror"></a>SeatCountPromotionEligibilityError

Bevat details over waarom de limiet voor het aantal seat is overschreden. Beide waarden kunnen null zijn.

| Eigenschap          | Type               | Beschrijving                                        |
|-------------------|--------------------|----------------------------------------------------|
| minimumRequiredSeats | Int? | De minimale licenties die door een promotie worden ondersteund. |
| maximumRequiredSeats | Int? | Het maximum aantal licenties dat door een promotie wordt ondersteund. |

## <a name="termpromotioneligibilityerror"></a>TermPromotionEligibilityError

Bevat informatie over waarom de promotietermijn niet is geaccepteerd.

| Eigenschap          | Type               | Beschrijving                                        |
|-------------------|--------------------|----------------------------------------------------|
| eligibleTerms | PromotieTerm | De in aanmerking komende voorwaarden voor een promotie worden ondersteund. |

## <a name="promotionterm"></a>PromotieTerm

Bevat details over waarom de limiet voor het aantal seat is overschreden.

| Eigenschap          | Type               | Beschrijving                                        |
|-------------------|--------------------|----------------------------------------------------|
| billingCycle | tekenreeks | Beschrijft hoe vaak de promotie wordt toegepast op de facturering. Waarden kunnen maandelijks, jaarlijks, onetime of onbekend zijn. |
| duur | tekenreeks | Duur van de periode die wordt gekocht. |




