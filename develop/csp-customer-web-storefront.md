---
title: Webwinkel van CSP-klant
description: Deze voorbeeldwebsitecode toont een werkende online winkel waar klanten abonnementen op Microsoft-producten kunnen kopen.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d68f17d707731f426cb980a566b6478790d3507c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973329"
---
# <a name="csp-customer-web-storefront"></a><span data-ttu-id="bb9d1-103">Webwinkel van CSP-klant</span><span class="sxs-lookup"><span data-stu-id="bb9d1-103">CSP customer web storefront</span></span>

<span data-ttu-id="bb9d1-104">**Van toepassing op**: Partner Center</span><span class="sxs-lookup"><span data-stu-id="bb9d1-104">**Applies to**: Partner Center</span></span>

<span data-ttu-id="bb9d1-105">**Is niet van toepassing op**: Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="bb9d1-105">**Does not apply to**: Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="bb9d1-106">Deze voorbeeld-app is alleen van toepassing op het globale exemplaar van Partner Center.</span><span class="sxs-lookup"><span data-stu-id="bb9d1-106">This sample app applies only to the global instance of Partner Center.</span></span>

<span data-ttu-id="bb9d1-107">De [Partner Center-webwinkel](https://github.com/Microsoft/Partner-Center-Storefront) is een **voorbeeldwebsite** voor een online winkel die klanten kunnen gebruiken om abonnementen op Microsoft-producten te kopen.</span><span class="sxs-lookup"><span data-stu-id="bb9d1-107">The [Partner Center storefront](https://github.com/Microsoft/Partner-Center-Storefront) is a **sample website** for an online store that customers can use to buy subscriptions to Microsoft products.</span></span> <span data-ttu-id="bb9d1-108">U kunt deze **voorbeeldcode voor eigen** gebruik wijzigen om de [aanbiedingen te](#configure-offers)configureren, huisstijl toe te voegen en een [](#configure-branding) [betalingswijze toe te voegen.](#configure-payment-types)</span><span class="sxs-lookup"><span data-stu-id="bb9d1-108">You can modify this **sample code** for your own use to [configure the offers](#configure-offers), [add branding](#configure-branding), and [add a payment method](#configure-payment-types).</span></span>

## <a name="sample-code"></a><span data-ttu-id="bb9d1-109">Voorbeeldcode</span><span class="sxs-lookup"><span data-stu-id="bb9d1-109">Sample code</span></span>

<span data-ttu-id="bb9d1-110">Download de [voorbeeldcode Partner Center webwinkel van](https://github.com/Microsoft/Partner-Center-Storefront) GitHub.</span><span class="sxs-lookup"><span data-stu-id="bb9d1-110">Download the [Partner Center storefront sample code](https://github.com/Microsoft/Partner-Center-Storefront) from GitHub.</span></span>

## <a name="configure-authentication"></a><span data-ttu-id="bb9d1-111">Verificatie configureren</span><span class="sxs-lookup"><span data-stu-id="bb9d1-111">Configure authentication</span></span>

<span data-ttu-id="bb9d1-112">Voordat u de toepassing bouwt, moet u de volgende waarden in het Web.config-bestand bijwerken om de Azure AD-verificatiegegevens weer te geven die u hebt gemaakt in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="bb9d1-112">Before you build the application, update the following values in the Web.config file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bb9d1-113">Gebruik de instellingen van uw sandbox-account voor integratie tijdens vroege ontwikkeling of voor testen in productie (TiP).</span><span class="sxs-lookup"><span data-stu-id="bb9d1-113">You should use your integration sandbox account settings during early development or for testing in production (TiP).</span></span>

- <span data-ttu-id="bb9d1-114">**partnerCenter.applicationId**</span><span class="sxs-lookup"><span data-stu-id="bb9d1-114">**partnerCenter.applicationId**</span></span>
- <span data-ttu-id="bb9d1-115">**partnerCenter.applicationSecret**</span><span class="sxs-lookup"><span data-stu-id="bb9d1-115">**partnerCenter.applicationSecret**</span></span>
- <span data-ttu-id="bb9d1-116">**partnerCenter.domain**</span><span class="sxs-lookup"><span data-stu-id="bb9d1-116">**partnerCenter.domain**</span></span>
- <span data-ttu-id="bb9d1-117">**webPortal.clientId**</span><span class="sxs-lookup"><span data-stu-id="bb9d1-117">**webPortal.clientId**</span></span>
- <span data-ttu-id="bb9d1-118">**webPortal.clientSecret**</span><span class="sxs-lookup"><span data-stu-id="bb9d1-118">**webPortal.clientSecret**</span></span>
- <span data-ttu-id="bb9d1-119">**webPortal.domain**</span><span class="sxs-lookup"><span data-stu-id="bb9d1-119">**webPortal.domain**</span></span>
- <span data-ttu-id="bb9d1-120">**webPortal.azureStorageConnectionString**</span><span class="sxs-lookup"><span data-stu-id="bb9d1-120">**webPortal.azureStorageConnectionString**</span></span>

## <a name="configure-offers"></a><span data-ttu-id="bb9d1-121">Aanbiedingen configureren</span><span class="sxs-lookup"><span data-stu-id="bb9d1-121">Configure offers</span></span>

<span data-ttu-id="bb9d1-122">U kunt de set aanbiedingen (**MicrosoftOffer**) configureren in **OfferCatalogViewModel.**</span><span class="sxs-lookup"><span data-stu-id="bb9d1-122">You can configure the set of offers (**MicrosoftOffer**) in the **OfferCatalogViewModel**.</span></span>

## <a name="configure-branding"></a><span data-ttu-id="bb9d1-123">Huisstijl configureren</span><span class="sxs-lookup"><span data-stu-id="bb9d1-123">Configure branding</span></span>

<span data-ttu-id="bb9d1-124">Deze voorbeeldwebsite houdt de volgende bedrijfs- en merkinformatie bij in *BrandingConfiguration.cs* en *PortalBranding.cs:*</span><span class="sxs-lookup"><span data-stu-id="bb9d1-124">This sample website tracks the following company and brand information in *BrandingConfiguration.cs* and *PortalBranding.cs*:</span></span>

- <span data-ttu-id="bb9d1-125">Organisatienaam</span><span class="sxs-lookup"><span data-stu-id="bb9d1-125">Organization name</span></span>
- <span data-ttu-id="bb9d1-126">Organisatielogo</span><span class="sxs-lookup"><span data-stu-id="bb9d1-126">Organization logo</span></span>
- <span data-ttu-id="bb9d1-127">Koptekstafbeelding</span><span class="sxs-lookup"><span data-stu-id="bb9d1-127">Header image</span></span>
- <span data-ttu-id="bb9d1-128">Privacyovereenkomst</span><span class="sxs-lookup"><span data-stu-id="bb9d1-128">Privacy agreement</span></span>
- <span data-ttu-id="bb9d1-129">E-mailadres van contactpersoon</span><span class="sxs-lookup"><span data-stu-id="bb9d1-129">Contact email</span></span>
- <span data-ttu-id="bb9d1-130">Telefoonnummer van contactpersoon</span><span class="sxs-lookup"><span data-stu-id="bb9d1-130">Contact phone number</span></span>
- <span data-ttu-id="bb9d1-131">Ondersteunings-e-mail</span><span class="sxs-lookup"><span data-stu-id="bb9d1-131">Support email</span></span>
- <span data-ttu-id="bb9d1-132">Ondersteuningstelefoonnummer</span><span class="sxs-lookup"><span data-stu-id="bb9d1-132">Support phone number</span></span>

### <a name="configure-payment-types"></a><span data-ttu-id="bb9d1-133">Betalingstypen configureren</span><span class="sxs-lookup"><span data-stu-id="bb9d1-133">Configure payment types</span></span>

<span data-ttu-id="bb9d1-134">De app gebruikt momenteel een PayPal-gateway, geïmplementeerd in *PayPalGateway.cs.*</span><span class="sxs-lookup"><span data-stu-id="bb9d1-134">The app currently uses a PayPal gateway, implemented in *PayPalGateway.cs*.</span></span>