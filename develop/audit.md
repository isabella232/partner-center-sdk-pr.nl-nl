---
title: Bewerkingen van Partner Center controleren
description: Meer informatie over het type Partner Center API-auditbewerkingen dat u kunt gebruiken om een record van Partner Center op te halen.
ms.date: 05/21/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 0e8010bde75bee4c4954034d8f61f19b076d96349e4a05807e272ca88efbc2fa
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994265"
---
# <a name="audit-operations-available-via-partner-center-api-that-show-a-record-of-partner-center-activity"></a>Controlebewerkingen die beschikbaar zijn via Partner Center API die een record van de Partner Center tonen

De Partner Center-API's bieden controlefuncties, zodat u een record van de Partner Center kunt krijgen.

U kunt controlerecords voor de afgelopen 30 dagen ophalen vanaf de huidige datum of voor een datumbereik dat is opgegeven door de begindatum en/of einddatum op te neemt. Houd er echter rekening mee dat de beschikbaarheid van activiteitenlogboekgegevens om prestatieredenen beperkt is tot de afgelopen 90 dagen. Aanvragen met een begindatum die langer is dan 90 dagen vóór de huidige datum, ontvangen een uitzondering met een slechte aanvraag (foutcode: 400) en een geschikt bericht.

## <a name="retrieve-audit-records"></a>Controlerecords ophalen

Haal gedetailleerde historische controlerecords op van bewerkingen die worden uitgevoerd door een partnergebruiker of -toepassing:

- [Een record van Partnercentrum-activiteiten ophalen](get-a-record-of-partner-center-activity-by-user.md)
- [Resources controleren](auditing-resources.md)