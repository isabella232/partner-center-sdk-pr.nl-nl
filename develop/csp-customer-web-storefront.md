---
title: Webwinkel van CSP-klant
description: Deze voorbeeld website code toont een werkend online archief voor klanten om abonnementen op micro soft-producten te kopen.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: bd488b9b9bf2c1df4bebc8513d230a02b06b2ce4
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767194"
---
# <a name="csp-customer-web-storefront"></a><span data-ttu-id="efc00-103">Webwinkel van CSP-klant</span><span class="sxs-lookup"><span data-stu-id="efc00-103">CSP customer web storefront</span></span>

<span data-ttu-id="efc00-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="efc00-104">**Applies to:**</span></span>

- <span data-ttu-id="efc00-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="efc00-105">Partner Center</span></span>

> [!NOTE]
> <span data-ttu-id="efc00-106">Deze voor beeld-app is alleen van toepassing op het globale exemplaar van partner centrum.</span><span class="sxs-lookup"><span data-stu-id="efc00-106">This sample app applies only to the global instance of Partner Center.</span></span> <span data-ttu-id="efc00-107">Het is niet van toepassing op het partner centrum voor Microsoft Cloud Duitsland of het partner centrum voor Microsoft Cloud voor de Amerikaanse overheid.</span><span class="sxs-lookup"><span data-stu-id="efc00-107">It does not apply to Partner Center for Microsoft Cloud Germany or to Partner Center for Microsoft Cloud for US Government.</span></span>

<span data-ttu-id="efc00-108">Het [Partner Center-winkel](https://github.com/Microsoft/Partner-Center-Storefront) is een voor beeld van een **website** voor een online winkel die klanten kunnen gebruiken om abonnementen op micro soft-producten te kopen.</span><span class="sxs-lookup"><span data-stu-id="efc00-108">The [Partner Center storefront](https://github.com/Microsoft/Partner-Center-Storefront) is a **sample website** for an online store that customers can use to buy subscriptions to Microsoft products.</span></span> <span data-ttu-id="efc00-109">U kunt deze **voorbeeld code** voor eigen gebruik wijzigen om [de aanbiedingen te configureren](#configure-offers), een [huis stijl toe te voegen](#configure-branding) en [een betalings methode toe te voegen](#configure-payment-types).</span><span class="sxs-lookup"><span data-stu-id="efc00-109">You can modify this **sample code** for your own use to [configure the offers](#configure-offers), [add branding](#configure-branding) and [add a payment method](#configure-payment-types).</span></span>

## <a name="sample-code"></a><span data-ttu-id="efc00-110">Voorbeeldcode</span><span class="sxs-lookup"><span data-stu-id="efc00-110">Sample code</span></span>

<span data-ttu-id="efc00-111">Down load de [voorbeeld code van het Partner Center-winkel programma](https://github.com/Microsoft/Partner-Center-Storefront) vanuit github.</span><span class="sxs-lookup"><span data-stu-id="efc00-111">Download the [Partner Center storefront sample code](https://github.com/Microsoft/Partner-Center-Storefront) from GitHub.</span></span>

## <a name="configure-authentication"></a><span data-ttu-id="efc00-112">Verificatie configureren</span><span class="sxs-lookup"><span data-stu-id="efc00-112">Configure authentication</span></span>

<span data-ttu-id="efc00-113">Voordat u de toepassing bouwt, moet u de volgende waarden bijwerken in het Web.config-bestand om de Azure AD-verificatie gegevens weer te geven die u hebt gemaakt in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="efc00-113">Before you build the application, update the following values in the Web.config file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="efc00-114">U moet uw account instellingen voor de integratie sandbox gebruiken tijdens vroegtijdige ontwikkeling of voor testen in productie (TiP).</span><span class="sxs-lookup"><span data-stu-id="efc00-114">You should use your integration sandbox account settings during early development or for testing in production (TiP).</span></span>

- <span data-ttu-id="efc00-115">**partnerCenter. applicationId**</span><span class="sxs-lookup"><span data-stu-id="efc00-115">**partnerCenter.applicationId**</span></span>
- <span data-ttu-id="efc00-116">**partnerCenter.applicationSecret**</span><span class="sxs-lookup"><span data-stu-id="efc00-116">**partnerCenter.applicationSecret**</span></span>
- <span data-ttu-id="efc00-117">**partnerCenter. Domain**</span><span class="sxs-lookup"><span data-stu-id="efc00-117">**partnerCenter.domain**</span></span>
- <span data-ttu-id="efc00-118">**webportal. clientId**</span><span class="sxs-lookup"><span data-stu-id="efc00-118">**webPortal.clientId**</span></span>
- <span data-ttu-id="efc00-119">**webportal. clientSecret**</span><span class="sxs-lookup"><span data-stu-id="efc00-119">**webPortal.clientSecret**</span></span>
- <span data-ttu-id="efc00-120">**webportal. domein**</span><span class="sxs-lookup"><span data-stu-id="efc00-120">**webPortal.domain**</span></span>
- <span data-ttu-id="efc00-121">**webportal. azureStorageConnectionString**</span><span class="sxs-lookup"><span data-stu-id="efc00-121">**webPortal.azureStorageConnectionString**</span></span>

## <a name="configure-offers"></a><span data-ttu-id="efc00-122">Aanbiedingen configureren</span><span class="sxs-lookup"><span data-stu-id="efc00-122">Configure offers</span></span>

<span data-ttu-id="efc00-123">U kunt de set met aanbiedingen (**MicrosoftOffer**) configureren in de **OfferCatalogViewModel**.</span><span class="sxs-lookup"><span data-stu-id="efc00-123">You can configure the set of offers (**MicrosoftOffer**) in the **OfferCatalogViewModel**.</span></span>

## <a name="configure-branding"></a><span data-ttu-id="efc00-124">Huis stijl configureren</span><span class="sxs-lookup"><span data-stu-id="efc00-124">Configure branding</span></span>

<span data-ttu-id="efc00-125">Deze voorbeeld website houdt de volgende bedrijfs-en merk gegevens bij in *BrandingConfiguration.cs* en *PortalBranding.cs*:</span><span class="sxs-lookup"><span data-stu-id="efc00-125">This sample website tracks the following company and brand information in *BrandingConfiguration.cs* and *PortalBranding.cs*:</span></span>

- <span data-ttu-id="efc00-126">Organisatienaam</span><span class="sxs-lookup"><span data-stu-id="efc00-126">Organization name</span></span>
- <span data-ttu-id="efc00-127">Logo van organisatie</span><span class="sxs-lookup"><span data-stu-id="efc00-127">Organization logo</span></span>
- <span data-ttu-id="efc00-128">Afbeelding van koptekst</span><span class="sxs-lookup"><span data-stu-id="efc00-128">Header image</span></span>
- <span data-ttu-id="efc00-129">Privacyverklaring</span><span class="sxs-lookup"><span data-stu-id="efc00-129">Privacy agreement</span></span>
- <span data-ttu-id="efc00-130">E-mailadres van contactpersoon</span><span class="sxs-lookup"><span data-stu-id="efc00-130">Contact email</span></span>
- <span data-ttu-id="efc00-131">Telefoon nummer contact persoon</span><span class="sxs-lookup"><span data-stu-id="efc00-131">Contact phone number</span></span>
- <span data-ttu-id="efc00-132">E-mail voor ondersteuning</span><span class="sxs-lookup"><span data-stu-id="efc00-132">Support email</span></span>
- <span data-ttu-id="efc00-133">Telefoon nummer voor ondersteuning</span><span class="sxs-lookup"><span data-stu-id="efc00-133">Support phone number</span></span>

### <a name="configure-payment-types"></a><span data-ttu-id="efc00-134">Betalings typen configureren</span><span class="sxs-lookup"><span data-stu-id="efc00-134">Configure payment types</span></span>

<span data-ttu-id="efc00-135">De app maakt momenteel gebruik van een PayPal-gateway, geïmplementeerd in *PayPalGateway.cs*.</span><span class="sxs-lookup"><span data-stu-id="efc00-135">The app currently uses a PayPal gateway, implemented in *PayPalGateway.cs*.</span></span>