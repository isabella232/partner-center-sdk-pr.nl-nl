---
title: REST API-verwijzing voor Partnercentrum
description: Meer informatie over hoe CSP-partners Partner Center-REST Api's kunnen gebruiken om hun CRM-en facturerings software te integreren met micro soft-systemen om klanten accounts beter te beheren.
ms.date: 11/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 3f83b2b73c3480f76646cae4fcbbcbacd31d4b3f
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "97767575"
---
# <a name="partner-center-rest-api-reference-to-rest-urls-rest-headers-rest-resources-and-rest-events"></a><span data-ttu-id="e0666-103">Partner centrum REST API referentie naar REST-Url's, REST-headers, REST bronnen en REST-gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="e0666-103">Partner Center REST API reference to REST URLs, REST headers, REST resources, and REST events</span></span>

<span data-ttu-id="e0666-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="e0666-104">**Applies to:**</span></span>

- <span data-ttu-id="e0666-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e0666-105">Partner Center</span></span>
- <span data-ttu-id="e0666-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="e0666-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="e0666-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="e0666-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="e0666-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="e0666-108">Partner Center for Microsoft Cloud for US Government</span></span>

## <a name="partner-center-rest-api"></a><span data-ttu-id="e0666-109">Partner centrum REST API</span><span class="sxs-lookup"><span data-stu-id="e0666-109">Partner Center REST API</span></span>

<span data-ttu-id="e0666-110">Het partner centrum REST API helpt de Cloud Solution Provider (CSP)-partners om hun bestaande CRM-of facturerings software te integreren met de micro soft-systemen die klant accounts beheren, bestellingen plaatsen, abonnementen beheren en ondersteunings aanvragen verwerken.</span><span class="sxs-lookup"><span data-stu-id="e0666-110">The Partner Center REST API helps Cloud Solution Provider (CSP) partners integrate their existing CRM or billing software with the Microsoft systems that manage customer accounts, place orders, manage subscriptions, and handle support requests.</span></span>

<span data-ttu-id="e0666-111">Zie het onderwerp [Scenarios](scenarios.md) , met inbegrip van de achtergrond overzicht, voor meer informatie over wat de API kan doen, inclusief voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="e0666-111">For more information about what the API can do, including sample code, see the [Scenarios](scenarios.md) topic, including the background overview.</span></span>

<span data-ttu-id="e0666-112">Lees het onderwerp [aan de slag](get-started.md) voordat u begint met de code ring.</span><span class="sxs-lookup"><span data-stu-id="e0666-112">Before you begin coding, read the [Get started](get-started.md) topic.</span></span> <span data-ttu-id="e0666-113">Dit artikel bevat informatie over het instellen van uw test-en productie accounts, het verkrijgen van verificatie en het vinden van de voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="e0666-113">This article contains information about setting up your test and production accounts, getting authentication working, and finding the sample code.</span></span>

## <a name="topics"></a><span data-ttu-id="e0666-114">Onderwerpen</span><span class="sxs-lookup"><span data-stu-id="e0666-114">Topics</span></span>

| <span data-ttu-id="e0666-115">Onderwerp</span><span class="sxs-lookup"><span data-stu-id="e0666-115">Topic</span></span> | <span data-ttu-id="e0666-116">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="e0666-116">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="e0666-117">REST-URL’s voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e0666-117">Partner Center REST URLs</span></span>](partner-center-rest-urls.md) | <span data-ttu-id="e0666-118">Hiermee worden de REST API-eind punten voor verschillende versies van partner centrum gedefinieerd.</span><span class="sxs-lookup"><span data-stu-id="e0666-118">Defines the REST API endpoints for different versions of Partner Center.</span></span> |
| [<span data-ttu-id="e0666-119">REST-headers voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e0666-119">Partner Center REST headers</span></span>](headers.md) | <span data-ttu-id="e0666-120">Hiermee worden de aanvraag-en antwoord headers gedefinieerd die worden gebruikt door de REST API.</span><span class="sxs-lookup"><span data-stu-id="e0666-120">Defines the request and response headers used by the REST API.</span></span> |
| [<span data-ttu-id="e0666-121">REST-bronnen voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e0666-121">Partner Center REST resources</span></span>](partner-center-rest-resources.md) | <span data-ttu-id="e0666-122">Hiermee worden de JSON-constructs gedefinieerd die de objecten vertegenwoordigen die nodig zijn om de REST API te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="e0666-122">Defines the JSON constructs that represent the objects needed to use the REST API.</span></span> |
| [<span data-ttu-id="e0666-123">REST-gebeurtenissen voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e0666-123">Partner Center REST events</span></span>](partner-center-webhook-events.md) | <span data-ttu-id="e0666-124">Hiermee worden de wijzigingen in de REST-bron wijziging gedefinieerd die worden ondersteund door de Partner Center-webhooks.</span><span class="sxs-lookup"><span data-stu-id="e0666-124">Defines the REST resource change events that are supported by Partner Center webhooks.</span></span> |
| [<span data-ttu-id="e0666-125">Ondersteunde talen en landinstellingen voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="e0666-125">Partner Center supported languages and locales</span></span>](partner-center-supported-languages-and-locales.md) | <span data-ttu-id="e0666-126">Een lijst met de land instellingen, talen en land-/regiocodes die worden ondersteund in de Api's van het partner centrum.</span><span class="sxs-lookup"><span data-stu-id="e0666-126">Lists the locales, languages, and country/region codes that are supported in the Partner Center APIs.</span></span> |
| [<span data-ttu-id="e0666-127">Partnercentrum-webhooks</span><span class="sxs-lookup"><span data-stu-id="e0666-127">Partner Center webhooks</span></span>](partner-center-webhooks.md) | <span data-ttu-id="e0666-128">Gebeurtenissen ontvangen, een call back verifiëren en de Api's van de webhook van partner Center gebruiken om een gebeurtenis registratie te maken, weer te geven en bij te werken.</span><span class="sxs-lookup"><span data-stu-id="e0666-128">How to receive events, authenticate a callback, and use the Partner Center webhook APIs to create, view, and update an event registration.</span></span> |