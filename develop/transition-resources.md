---
title: Resources overstappen
description: Beschrijft de resources die worden gebruikt voor de overgang van nieuwe commerce-abonnementen.
ms.date: 02/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: BrentSerbus
ms.author: brserbus
ms.openlocfilehash: 44867be3823414ab43957e789c0cd29aef44d956
ms.sourcegitcommit: e1db965e8c7b4fe3aaa0ecd6cefea61973ca2232
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/03/2021
ms.locfileid: "123457299"
---
# <a name="transition-resources"></a>Resources overstappen

**Van toepassing op**

- Partnercentrum

**Juiste rollen**

- Globale beheerder
- Beheeragent

> [!Note] 
> Nieuwe commercewijzigingen zijn momenteel alleen beschikbaar voor partners die deel uitmaken van de technical preview van de nieuwe commerce-ervaring M365/D365.

Beschrijft de resources die worden gebruikt om over te gaan van het ene nieuwe commerce-abonnement naar het andere.

## <a name="transitioneliblity"></a>TransitionEliblity

Beschrijft het gedrag van een afzonderlijke resource voor abonnementsovergang.

| Eigenschap          | Type                    | Description                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| CatalogItemId | tekenreeks                  | De id van het catalogusitem dat wordt gecontroleerd. |
| Titel  | tekenreeks                  | De titel van de SKU. |
| Description | tekenreeks                  | De beschrijving van de SKU. |
| Aantal | geheel getal                 | De hoeveelheid van de nieuwe aanbieding die moet worden gekocht. |
| Geschiktheid | lijst met TransitionEligibilityDetail | Een lijst met details over geschiktheid voor overgangen. | 

## <a name="transitioneligibilitydetail"></a>TransitionEligibilityDetail

Beschrijft het gedrag van een resource voor geschiktheidsdetails van een afzonderlijke overgang.

| Eigenschap          | Type                    | Description                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| IsEligible | booleaans | Retourneert de geschiktheid is geldig of niet. |
| TransitionType | TransitionType | Het type overgang. Kan worden transition_with_license_transfer of transition_only. |
| Fouten | Lijst met TransitionErrors | De metagegevenskenmerken die overeenkomen met de fout. |

## <a name="transition"></a>Overgang

Beschrijft het gedrag van een afzonderlijke resource voor abonnementsovergang.

| Eigenschap          | Type                    | Description                                                                                  |
|-------------------|-------------------------|----------------------------------------------------------------------------------------------|
| FromCatalogItemId | tekenreeks                  | De id Van catalogusitem. |
| ToCatalogItemId   | tekenreeks                  | De item-id Voor catalogus. |
| ToSubscriptionId  | tekenreeks                  | De id Naar-abonnement. Dit wordt alleen ingevuld als het abonnement wordt gewijzigd. Op dit moment heeft alleen de verouderde upgrade dit nodig, maar moderne gedeeltelijke overgang zal dit ook doen. |
| Aantal          | geheel getal                 | De hoeveelheid die wordt overgewaardeeerd naar het doelcatalogusitem. |
| TransitionType    | tekenreeks              | Het overgangstype. Mogelijke waarden: transition_only, transition_with_license_transfer.   |
| Gebeurtenissen            | lijst met TransitionEvents | De gebeurtenissen van de overgang. |

## <a name="transitionevent"></a>TransitionEvent

Beschrijft een reden waarom een upgrade niet kan worden uitgevoerd.

| Eigenschap          | Type               | Beschrijving                                                                                                                                                                                                                                                                                                                                                                                     |
|-------------------|--------------------|------------------------------------------------------------------------------|
| Name | tekenreeks | De naam van de overgangsgebeurtenis. Mogelijke waarden Conversie of LicenseReassignment. |
| Status | tekenreeks  | De status van de overgangsgebeurtenis. Mogelijke waarden InProgress, Completed of Failed.  |
| Tijdstempel | DateTime | Het UTC-tijdstempel van de gebeurtenis. |
| Fouten | Lijst met TransitionErrors | De metagegevenskenmerken die overeenkomen met de fout. |

## <a name="transitionerror"></a>TransitionError

Vertegenwoordigt een fout voor geschiktheid voor abonnementsoverdracht. Geeft een reden waarom een overgang niet kan worden uitgevoerd.

| Eigenschap          | Type               | Description                                                                                                                                                                                                                                                                                                                                                                                     |
|-------------------|--------------------|--------------------------------------------------------------|
| Code | TransitionErrorCode | De foutcode die aan het probleem is gekoppeld. |
| Description | tekenreeks  | Beschrijvende tekst die de fout beschrijft. |

