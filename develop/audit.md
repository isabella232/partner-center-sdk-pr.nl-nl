---
title: Controle bewerkingen van de Partner Center-activiteit
description: Meer informatie over het type partner Center API-audit bewerkingen dat u kunt gebruiken om een record van de Partner Center-activiteit op te halen.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 019bebe40c43f6ee1c2ac7da381a86ca190702d4
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767592"
---
# <a name="audit-operations-available-via-partner-center-api-that-show-a-record-of-partner-center-activity"></a>Audit bewerkingen die beschikbaar zijn via de Partner Center-API waarin een record van de Partner Center-activiteit wordt weer gegeven

De Api's van het partner centrum bieden controle functies, zodat u een record van partner Center-activiteiten kunt ophalen.

U kunt controle records ophalen voor de afgelopen 30 dagen vanaf de huidige datum of voor een datum bereik dat is opgegeven met inbegrip van de begin datum en/of de eind datum. Houd er echter rekening mee dat de beschik baarheid van het activiteiten logboek voor de prestaties beperkt is tot de vorige 90 dagen. Aanvragen met een begin datum die groter is dan 90 dagen vóór de huidige datum worden een ongeldige aanvraag uitzondering ontvangen (fout code: 400) en een geschikt bericht.

## <a name="retrieve-audit-records"></a>Audit records ophalen

Gedetailleerde historische controle records ophalen van bewerkingen die worden uitgevoerd door een gebruiker of toepassing van een partner:

- [Een record van Partnercentrum-activiteiten ophalen](get-a-record-of-partner-center-activity-by-user.md)
- [Controle bronnen](auditing-resources.md)