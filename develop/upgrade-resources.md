---
title: Resources bijwerken
description: Beschrijft de resources die worden gebruikt om een gebruiker bij te werken van een bron abonnement naar een doel abonnement.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bdbef383370761a01eb462f90284ad826a38ddaa
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767258"
---
# <a name="upgrade-resources"></a>Resources bijwerken

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Beschrijft de resources die worden gebruikt om een gebruiker bij te werken van een bron abonnement naar een doel abonnement.

## <a name="upgrade"></a>Upgraden

Hierin wordt het gedrag van een afzonderlijke upgrade resource beschreven.

| Eigenschap      | Type                   | Description                                                                                  |
|---------------|------------------------|----------------------------------------------------------------------------------------------|
| TargetOffer   | Aanbieding                  | De aanbieding van het doel abonnement.                                                        |
| UpgradeType   | tekenreeks                 | Het type upgrade: ' geen ', ' alleen bijwerken \_ ' of ' bijwerken \_ met \_ licentie \_ overdracht '.         |
| IsEligible    | booleaans                | Hiermee wordt aangegeven of de upgrade kan worden uitgevoerd.                                                  |
| Aantal      | geheel getal                | De kwantificering van de nieuwe aanbieding die moet worden gekocht. Wordt standaard ingesteld op de hoeveelheid van het bron abonnement. |
| UpgradeErrors | matrix van UpgradeErrors | Redenen waarom de upgrade niet kan worden uitgevoerd, indien van toepassing.                                      |
| Kenmerken    | ResourceAttributes     | De meta gegevens kenmerken die overeenkomen met de upgrade.                                        |

## <a name="upgradeerror"></a>UpgradeError

Beschrijft een reden waarom een upgrade niet kan worden uitgevoerd.

| Eigenschap          | Type               | Description                                                                                                                                                                                                                                                                                                                                                                                     |
|-------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code              | tekenreeks             | De fout code die is gekoppeld aan het probleem: andere ' ', ' gedelegeerde \_ beheerders \_ machtigingen \_ uitgeschakeld ', ' abonnements \_ status is \_ niet \_ actief ', ' conflicterende \_ service \_ typen ', ' gelijktijdigheids \_ conflicten ', ' gebruikers \_ context \_ vereist ', ' abonnement \_ toevoegen \_ \_ aanwezig ', ' het abonnement heeft geen \_ \_ \_ \_ \_ upgrade \_ paden ', ' abonnements \_ \_ aanbieding \_ niet \_ gevonden ' of ' abonnement \_ niet \_ ingericht '. |
| Description       | tekenreeks             | Beschrijvende tekst voor het beschrijven van de fout.                                                                                                                                                                                                                                                                                                                                                             |
| AdditionalDetails | tekenreeks             | Meer informatie over de fout.                                                                                                                                                                                                                                                                                                                                                         |
| Kenmerken        | ResourceAttributes | De meta gegevens kenmerken die overeenkomen met de fout.                                                                                                                                                                                                                                                                                                                                             |

## <a name="upgraderesult"></a>UpgradeResult

Beschrijft een resultaat van het upgrade proces van het abonnement.

| Eigenschap             | Type                        | Description                                                                          |
|----------------------|-----------------------------|--------------------------------------------------------------------------------------|
| SourceSubscriptionId | tekenreeks                      | De id van het bron abonnement.                                           |
| TargetSubscriptionID | tekenreeks                      | De id van het doel abonnement.                                           |
| UpgradeType          | tekenreeks                      | Het type upgrade: ' geen ', ' alleen bijwerken \_ ' of ' bijwerken \_ met \_ licentie \_ overdracht '. |
| UpgradeErrors        | matrix van UpgradeErrors      | Er zijn fouten opgetreden tijdens de poging om de upgrade uit te voeren, indien van toepassing.           |
| LicenseErrors        | matrix van UserLicenseErrrors | Er zijn fouten opgetreden bij een poging om gebruikers licenties te migreren, indien van toepassing.          |
| Kenmerken           | ResourceAttributes          | De meta gegevens kenmerken die overeenkomen met de licentie.                                |

## <a name="userlicenseerror"></a>UserLicenseError

Hierin worden fouten beschreven die voortvloeien uit mislukte overdracht van de gebruikers licentie.

| Eigenschap     | Type                   | Description                                                               |
|--------------|------------------------|---------------------------------------------------------------------------|
| UserObjectId | tekenreeks                 | De unieke geïdentificeerde van het gebruikers object.                                 |
| Name         | tekenreeks                 | De naam van de gebruiker.                                                     |
| E-mail        | tekenreeks                 | Het e-mailadres van de gebruiker.                                                    |
| Fouten       | matrix van ServiceFaults | Een lijst met uitzonde ringen die zijn opgetreden bij het uitvoeren van de overdracht van de gebruikers licentie. |
| Kenmerken   | ResourceAttributes     | De meta gegevens kenmerken die overeenkomen met de licentie.                     |

