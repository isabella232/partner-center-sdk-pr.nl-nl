---
title: Resources upgraden
description: Beschrijft de resources die worden gebruikt om een gebruiker te upgraden van een bronabonnement naar een doelabonnement.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4c57994d1b1e7659df5e6448578422f6d9c21fee
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111529814"
---
# <a name="upgrade-resources"></a>Resources upgraden

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Beschrijft de resources die worden gebruikt om een gebruiker te upgraden van een bronabonnement naar een doelabonnement.

## <a name="upgrade"></a>Upgraden

Beschrijft het gedrag van een afzonderlijke upgraderesource.

| Eigenschap      | Type                   | Beschrijving                                                                                  |
|---------------|------------------------|----------------------------------------------------------------------------------------------|
| TargetOffer   | Aanbieding                  | De aanbieding van het doelabonnement.                                                        |
| UpgradeType   | tekenreeks                 | Het type upgrade: 'geen', 'alleen \_ upgraden' of \_ 'upgraden met \_ \_ licentieoverdracht'.         |
| IsEligible    | booleaans                | Hiermee wordt aangegeven of de upgrade kan worden uitgevoerd.                                                  |
| Aantal      | geheel getal                | De hoeveelheid van de nieuwe aanbieding die moet worden gekocht. De standaardwaarde is de hoeveelheid bronabonnement. |
| UpgradeErrors | matrix van UpgradeErrors | Redenen waarom de upgrade niet kan worden uitgevoerd, indien van toepassing.                                      |
| Kenmerken    | ResourceAttributes     | De metagegevenskenmerken die overeenkomen met de upgrade.                                        |

## <a name="upgradeerror"></a>UpgradeError

Beschrijft een reden waarom een upgrade niet kan worden uitgevoerd.

| Eigenschap          | Type               | Beschrijving                                                                                                                                                                                                                                                                                                                                                                                     |
|-------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Code              | tekenreeks             | De foutcode die is gekoppeld aan het probleem: 'overig', 'gedelegeerde beheerdersmachtigingen \_ \_ \_ uitgeschakeld', \_ 'abonnementsstatus niet \_ \_ actief', 'conflicterende \_ \_ servicetypen', 'gelijktijdigheidsconflicten', 'gebruikerscontext \_ vereist', \_ 'abonnement \_ \_ \_ \_ \_ \_ \_ \_ \_ \_ \_ \_ \_ \_ \_ \_ toevoegen ons aanwezig', 'abonnement heeft geen upgradepaden', 'abonnementsdoelaanbieding niet gevonden' of 'abonnement niet ingericht'. |
| Description       | tekenreeks             | Beschrijvende tekst waarin de fout wordt beschreven.                                                                                                                                                                                                                                                                                                                                                             |
| AdditionalDetails | tekenreeks             | Aanvullende informatie over de fout.                                                                                                                                                                                                                                                                                                                                                         |
| Kenmerken        | ResourceAttributes | De metagegevenskenmerken die overeenkomen met de fout.                                                                                                                                                                                                                                                                                                                                             |

## <a name="upgraderesult"></a>UpgradeResult

Beschrijft het resultaat van het upgradeproces van het abonnement.

| Eigenschap             | Type                        | Beschrijving                                                                          |
|----------------------|-----------------------------|--------------------------------------------------------------------------------------|
| SourceSubscriptionId | tekenreeks                      | De id van het bronabonnement.                                           |
| TargetSubscriptionID | tekenreeks                      | De id van het doelabonnement.                                           |
| UpgradeType          | tekenreeks                      | Het type upgrade: 'geen', 'alleen \_ upgraden' of \_ 'upgraden met \_ \_ licentieoverdracht'. |
| UpgradeErrors        | matrix van UpgradeErrors      | Fouten die zijn aangetroffen tijdens het uitvoeren van de upgrade, indien van toepassing.           |
| LicenseErrors        | matrix van UserLicenseErrrors | Fouten die zijn aangetroffen bij het migreren van gebruikerslicenties, indien van toepassing.          |
| Kenmerken           | ResourceAttributes          | De metagegevenskenmerken die overeenkomen met de licentie.                                |

## <a name="userlicenseerror"></a>UserLicenseError

Beschrijft fouten die voortvloeien uit een mislukte overdracht van gebruikerslicenties.

| Eigenschap     | Type                   | Beschrijving                                                               |
|--------------|------------------------|---------------------------------------------------------------------------|
| UserObjectId | tekenreeks                 | De unieke geïdentificeerd van het gebruikersobject.                                 |
| Name         | tekenreeks                 | De naam van de gebruiker.                                                     |
| E-mail        | tekenreeks                 | Het e-mailadres van de gebruiker.                                                    |
| Fouten       | matrix van ServiceFaults | Een lijst met uitzonderingen die zijn opgeleverd bij het overdragen van gebruikerslicenties. |
| Kenmerken   | ResourceAttributes     | De metagegevenskenmerken die overeenkomen met de licentie.                     |

