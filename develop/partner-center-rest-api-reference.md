---
title: REST API-verwijzing voor Partnercentrum
description: Meer informatie over hoe CSP-partners Partner Center REST API's kunnen gebruiken om hun CRM- en factureringssoftware te integreren met Microsoft-systemen om klantaccounts beter te beheren.
ms.date: 11/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 18621fdb94f91f066b69a11f7d557410d653787e
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548036"
---
# <a name="partner-center-rest-api-reference-to-rest-urls-rest-headers-rest-resources-and-rest-events"></a><span data-ttu-id="11b6a-103">Partner Center REST API naar REST-URL's, REST-headers, REST-resources en REST-gebeurtenissen</span><span class="sxs-lookup"><span data-stu-id="11b6a-103">Partner Center REST API reference to REST URLs, REST headers, REST resources, and REST events</span></span>

<span data-ttu-id="11b6a-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="11b6a-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

## <a name="partner-center-rest-api"></a><span data-ttu-id="11b6a-105">Partner Center REST API</span><span class="sxs-lookup"><span data-stu-id="11b6a-105">Partner Center REST API</span></span>

<span data-ttu-id="11b6a-106">De Partner Center REST API helpt Cloud Solution Provider (CSP)-partners hun bestaande CRM- of factureringssoftware te integreren met de Microsoft-systemen die klantaccounts beheren, orders plaatsen, abonnementen beheren en ondersteuningsaanvragen verwerken.</span><span class="sxs-lookup"><span data-stu-id="11b6a-106">The Partner Center REST API helps Cloud Solution Provider (CSP) partners integrate their existing CRM or billing software with the Microsoft systems that manage customer accounts, place orders, manage subscriptions, and handle support requests.</span></span>

<span data-ttu-id="11b6a-107">Zie het onderwerp Scenario's, inclusief het achtergrondoverzicht, voor meer informatie over wat de API kan doen, inclusief voorbeeldcode. [](scenarios.md)</span><span class="sxs-lookup"><span data-stu-id="11b6a-107">For more information about what the API can do, including sample code, see the [Scenarios](scenarios.md) topic, including the background overview.</span></span>

<span data-ttu-id="11b6a-108">Lees het onderwerp Aan de slag voordat u begint [met](get-started.md) coderen.</span><span class="sxs-lookup"><span data-stu-id="11b6a-108">Before you begin coding, read the [Get started](get-started.md) topic.</span></span> <span data-ttu-id="11b6a-109">Dit artikel bevat informatie over het instellen van uw test- en productieaccounts, het verkrijgen van verificatie en het vinden van de voorbeeldcode.</span><span class="sxs-lookup"><span data-stu-id="11b6a-109">This article contains information about setting up your test and production accounts, getting authentication working, and finding the sample code.</span></span>

<span data-ttu-id="11b6a-110">Zie voor een referentiegids waarin elke API wordt [uitgelegd Partner Center REST API.](/rest/api/partner-center-rest/)</span><span class="sxs-lookup"><span data-stu-id="11b6a-110">For a reference guide explaining each API, see [Partner Center REST API](/rest/api/partner-center-rest/).</span></span>

## <a name="topics"></a><span data-ttu-id="11b6a-111">Onderwerpen</span><span class="sxs-lookup"><span data-stu-id="11b6a-111">Topics</span></span>

| <span data-ttu-id="11b6a-112">Onderwerp</span><span class="sxs-lookup"><span data-stu-id="11b6a-112">Topic</span></span> | <span data-ttu-id="11b6a-113">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="11b6a-113">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="11b6a-114">Partner Center REST API</span><span class="sxs-lookup"><span data-stu-id="11b6a-114">Partner Center REST API</span></span>](/rest/api/partner-center-rest/) | <span data-ttu-id="11b6a-115">Verwijzing naar elk REST API beschikbaar voor Partner Center.</span><span class="sxs-lookup"><span data-stu-id="11b6a-115">Reference of each REST API available for Partner Center.</span></span> |
| [<span data-ttu-id="11b6a-116">REST-URL’s voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="11b6a-116">Partner Center REST URLs</span></span>](partner-center-rest-urls.md) | <span data-ttu-id="11b6a-117">Definieert REST API eindpunten voor verschillende versies van Partner Center.</span><span class="sxs-lookup"><span data-stu-id="11b6a-117">Defines the REST API endpoints for different versions of Partner Center.</span></span> |
| [<span data-ttu-id="11b6a-118">REST-headers voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="11b6a-118">Partner Center REST headers</span></span>](headers.md) | <span data-ttu-id="11b6a-119">Definieert de aanvraag- en antwoordheaders die door de REST API.</span><span class="sxs-lookup"><span data-stu-id="11b6a-119">Defines the request and response headers used by the REST API.</span></span> |
| [<span data-ttu-id="11b6a-120">REST-bronnen voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="11b6a-120">Partner Center REST resources</span></span>](partner-center-rest-resources.md) | <span data-ttu-id="11b6a-121">Definieert de JSON-constructies die de objecten vertegenwoordigen die nodig zijn om de REST API.</span><span class="sxs-lookup"><span data-stu-id="11b6a-121">Defines the JSON constructs that represent the objects needed to use the REST API.</span></span> |
| [<span data-ttu-id="11b6a-122">REST-gebeurtenissen voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="11b6a-122">Partner Center REST events</span></span>](partner-center-webhook-events.md) | <span data-ttu-id="11b6a-123">Hiermee definieert u de gebeurtenissen voor het wijzigen van de REST-resource die door Partner Center webhooks worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="11b6a-123">Defines the REST resource change events that are supported by Partner Center webhooks.</span></span> |
| [<span data-ttu-id="11b6a-124">Ondersteunde talen en landinstellingen voor Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="11b6a-124">Partner Center supported languages and locales</span></span>](partner-center-supported-languages-and-locales.md) | <span data-ttu-id="11b6a-125">Hier vindt u de land- en land-/regiocodes die worden ondersteund in de api's Partner Center land/regio.</span><span class="sxs-lookup"><span data-stu-id="11b6a-125">Lists the locales, languages, and country/region codes that are supported in the Partner Center APIs.</span></span> |
| [<span data-ttu-id="11b6a-126">Partnercentrum-webhooks</span><span class="sxs-lookup"><span data-stu-id="11b6a-126">Partner Center webhooks</span></span>](partner-center-webhooks.md) | <span data-ttu-id="11b6a-127">Gebeurtenissen ontvangen, een callback verifiëren en de webhook-API's van Partner Center gebruiken om een gebeurtenisregistratie te maken, weer te geven en bij te werken.</span><span class="sxs-lookup"><span data-stu-id="11b6a-127">How to receive events, authenticate a callback, and use the Partner Center webhook APIs to create, view, and update an event registration.</span></span> |
