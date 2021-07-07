---
title: Mogelijkheden van indirecte CSP-provider in de sandbox
description: Indirecte providers kunnen indirecte resellers in de sandbox maken voor testdoeleinden.
ms.date: 05/20/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: vinayks-ms
ms.author: vinayks
ms.openlocfilehash: da35dadd4e13247e923259a1cf3a67852f4b9e00
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445898"
---
# <a name="csp-indirect-provider-sandbox-capabilities-for-creating-indirect-reseller-accounts"></a>Sandbox-mogelijkheden van indirecte CSP-provider voor het maken van indirecte reselleraccounts 

**Juiste rollen:** Indirecte provider

Indirecte CSP-providers kunnen een CSP Indirect Reseller Sandbox-account maken via hun eigen Sandbox-account op laag 2 in Partner Center portal.


## <a name="prerequisites"></a>Vereisten 

Partner Center sandboxreferenties voor indirecte provider (laag 2). Het sandboxscenario ondersteunt verificatie met zowel de zelfstandige app- als app+gebruikersreferenties. 
 

## <a name="sandbox-indirect-provider--create-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a>Indirecte sandboxprovider: indirecte sandbox-reseller maken met behulp van Partner Center gebruikersinterface 

 Dit is een sandbox-functie waarmee indirecte sandboxproviders via de portal een sandbox-account voor indirecte resellers Partner Center maken.

De volgende scenario's zijn wat indirecte providers kunnen doen voor indirecte resellers in Sandbox via Partner Center gebruikersinterface: 

1. Indirecte CSP-providers kunnen een CSP Indirect Reseller Sandbox-account maken via hun eigen Sandbox-account op laag 2 in Partner Center portal.
2. Indirecte CSP-resellers kunnen klanten weergeven op indirecte providers. 

1. Indirecte CSP-resellers kunnen het klantaccount beheren met gedelegeerde beheerdersmachtigingen.

1. Indirecte CSP-providers kunnen indirecte CSP-resellers uitnodigen.
 
1. Indirecte CSP-providers kunnen een CSP Indirect Reseller Sandbox-account verwijderen via hun eigen Sandbox-account op laag 2 in Partner Center portal.

    a.  Wanneer de indirecte sandboxprovider de relatie met de indirecte sandbox-reseller verwijdert, controleert u of de indirecte reseller een andere relatie heeft met andere providers. Als dat het zo is, wordt alleen de relatie met die specifieke indirecte provider verwijderd.

    c. Als dit de enige relatie voor de indirecte reseller is, wordt de indirecte reseller verwijderd.

1. Indirecte CSP-providers kunnen een CSP Indirect Reseller.

    a. Dit is een functie alleen voor sandboxs waarmee indirecte sandboxproviders sandbox-indirecte resellers kunnen verwijderen.
     
1. Vereisten voor het verwijderen van een indirecte sandbox-reseller:

    1. De abonnementen voor elke klant van de indirecte sandbox-reseller opschorten.

    1. Verwijder alle klanten van indirecte reseller.

1. Limiet van vijf indirecte sandbox-resellers die zijn toegestaan per indirecte sandboxprovider. Zodra de indirecte sandbox-reseller is verwijderd, wordt het quotum opnieuw ingesteld.

### <a name="pre-requisites"></a>Vereisten

- Limiet van vijf indirecte sandbox-resellers die zijn toegestaan per indirecte sandboxprovider. 

- Dezelfde MPN-id kan worden gebruikt om meerdere Sandbox-accounts voor indirecte resellers te maken als het land van de MPN-id en het land van de sandbox voor indirecte resellers hetzelfde zijn. Als u een MPN-test-id beschikbaar hebt, kunt u deze gebruiken of een lijst met MPN-id's krijgen via ons [Yammer kanaal]( https://www.yammer.com/cloudpartnercommunity/#/files/929991598080 ). Als u geen toegang hebt tot Yammer, Yammer u om toegang aan te vragen.
 
- Slechts 75 klanten zijn toegestaan per indirecte sandboxprovider

## <a name="create-csp-indirect-reseller-sandbox-account"></a>Een sandbox CSP Indirect Reseller account maken

1. Meld u aan Partner Center via uw Sandbox-account op laag 2. 

2. Navigeer in het linkermenu naar Indirecte resellers. 

3. Selecteer de **knop Sandbox voor reseller** toevoegen. 

4. Vul het formulier voor accountinschrijving in. Het spreekt voor zich, maar vergeet niet dat u een Sandbox-account maakt voor een indirecte reseller. Dit account wordt niet gekeurd en wordt geactiveerd zodra u de accountinschrijving hebt voltooien.  

5. Zodra het account is gemaakt, krijgt u de globale beheerdersreferenties voor het sandbox-account voor indirecte resellers in de portal. Vergeet niet om het onmiddellijk op te slaan, anders kunt u zich niet aanmelden als een sandbox voor indirecte resellers. 

6. Meld u af en meld u opnieuw aan Partner Center met de nieuwe referenties voor de Sandbox voor indirecte resellers. Verken de mogelijkheden die u als indirecte reseller kunt doen. Dit zijn enkele dingen:  

    - Profielen beheren  

    - Gebruikers en rollen beheren 

    - Indirecte providers beheren 

    - CSP Sandbox-klanten beheren 

    - Relaties beheren
    
     
## <a name="sandbox-indirect-provider--delete-sandbox-indirect-reseller-using-the-partner-center-user-interface"></a>Indirecte sandboxprovider: indirecte sandbox-reseller verwijderen met behulp van Partner Center gebruikersinterface

 Dit is een sandbox-functie waarmee indirecte sandboxproviders een bestaand sandbox-account voor indirecte resellers kunnen verwijderen via Partner Center portal. 

### <a name="pre-requisites-to-delete-sandbox-indirect-reseller"></a>Vereisten voor het verwijderen van indirecte sandbox-reseller:

Een bestaand CSP Indirect Reseller Sandbox-account dat is gekoppeld aan uw CSP Indirect Provider Sandbox-account op laag 2.  
 

## <a name="delete-csp-indirect-reseller-sandbox-account"></a>Een sandbox CSP Indirect Reseller account verwijderen

1. Meld u Partner Center aan met uw Sandbox-account op laag 2. 

2. Navigeer in het linkermenu naar Indirecte resellers. 

3. Selecteer de **koppeling Sandbox voor reseller** verwijderen naast het Sandbox-account voor indirecte resellers dat u wilt verwijderen. Het Sandbox-account voor indirecte resellers wordt permanent verwijderd en kan niet worden hersteld. 

## <a name="api-references"></a>API-referenties

- Indirecte reseller maken 
- Indirecte reseller verwijderen 

 

 