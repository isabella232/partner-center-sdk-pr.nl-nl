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
# <a name="audit-operations-available-via-partner-center-api-that-show-a-record-of-partner-center-activity"></a><span data-ttu-id="dedbe-103">Audit bewerkingen die beschikbaar zijn via de Partner Center-API waarin een record van de Partner Center-activiteit wordt weer gegeven</span><span class="sxs-lookup"><span data-stu-id="dedbe-103">Audit operations available via Partner Center API that show a record of Partner Center activity</span></span>

<span data-ttu-id="dedbe-104">De Api's van het partner centrum bieden controle functies, zodat u een record van partner Center-activiteiten kunt ophalen.</span><span class="sxs-lookup"><span data-stu-id="dedbe-104">The Partner Center APIs provide auditing features so you can get a record of Partner Center activity.</span></span>

<span data-ttu-id="dedbe-105">U kunt controle records ophalen voor de afgelopen 30 dagen vanaf de huidige datum of voor een datum bereik dat is opgegeven met inbegrip van de begin datum en/of de eind datum.</span><span class="sxs-lookup"><span data-stu-id="dedbe-105">You can retrieve audit records for the previous 30 days from the current date, or for a date range specified by including the start date and/or the end date.</span></span> <span data-ttu-id="dedbe-106">Houd er echter rekening mee dat de beschik baarheid van het activiteiten logboek voor de prestaties beperkt is tot de vorige 90 dagen.</span><span class="sxs-lookup"><span data-stu-id="dedbe-106">Note, however, that for performance reasons activity log data availability is limited to the previous 90 days.</span></span> <span data-ttu-id="dedbe-107">Aanvragen met een begin datum die groter is dan 90 dagen vóór de huidige datum worden een ongeldige aanvraag uitzondering ontvangen (fout code: 400) en een geschikt bericht.</span><span class="sxs-lookup"><span data-stu-id="dedbe-107">Requests with a start date greater than 90 days prior to the current date will receive a bad request exception (error code: 400) and an appropriate message.</span></span>

## <a name="retrieve-audit-records"></a><span data-ttu-id="dedbe-108">Audit records ophalen</span><span class="sxs-lookup"><span data-stu-id="dedbe-108">Retrieve audit records</span></span>

<span data-ttu-id="dedbe-109">Gedetailleerde historische controle records ophalen van bewerkingen die worden uitgevoerd door een gebruiker of toepassing van een partner:</span><span class="sxs-lookup"><span data-stu-id="dedbe-109">Get detailed historical audit records of operations performed by a partner user or application:</span></span>

- [<span data-ttu-id="dedbe-110">Een record van Partnercentrum-activiteiten ophalen</span><span class="sxs-lookup"><span data-stu-id="dedbe-110">Get a record of Partner Center activity</span></span>](get-a-record-of-partner-center-activity-by-user.md)
- [<span data-ttu-id="dedbe-111">Controle bronnen</span><span class="sxs-lookup"><span data-stu-id="dedbe-111">Auditing resources</span></span>](auditing-resources.md)