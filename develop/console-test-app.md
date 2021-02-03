---
title: Console-testapp
description: Deze console test-app bevat voorbeeld code voor alle scenario's die worden ondersteund door de partner centrum-Api's. U kunt dit ook gebruiken voor het testen.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e82bac3ccc22d0e7cf898e5b2d2e002c622584ae
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767321"
---
# <a name="console-test-app"></a><span data-ttu-id="b1718-104">Console-testapp</span><span class="sxs-lookup"><span data-stu-id="b1718-104">Console test app</span></span>

<span data-ttu-id="b1718-105">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="b1718-105">**Applies to:**</span></span>

- <span data-ttu-id="b1718-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="b1718-106">Partner Center</span></span>
- <span data-ttu-id="b1718-107">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="b1718-107">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="b1718-108">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="b1718-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="b1718-109">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b1718-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b1718-110">De console test-app is beschikbaar in C# en Java. Deze bevat voorbeeld codes voor alle scenario's die worden ondersteund door de partner centrum-Api's.</span><span class="sxs-lookup"><span data-stu-id="b1718-110">The console test app is provided in C# and Java, it provides sample codes for all of the scenarios supported by the Partner Center APIs.</span></span> <span data-ttu-id="b1718-111">U kunt dit ook gebruiken voor het testen.</span><span class="sxs-lookup"><span data-stu-id="b1718-111">You can also use it for testing.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="b1718-112">Code ophalen</span><span class="sxs-lookup"><span data-stu-id="b1718-112">Get the code</span></span>

<span data-ttu-id="b1718-113">Down load de voorbeeld code voor de console test-app.</span><span class="sxs-lookup"><span data-stu-id="b1718-113">Download the sample code for the console test app.</span></span>

## <a name="net"></a><span data-ttu-id="b1718-114">.NET</span><span class="sxs-lookup"><span data-stu-id="b1718-114">.NET</span></span>

<span data-ttu-id="b1718-115">[Down load de voorbeeld code](https://go.microsoft.com/fwlink/p/?LinkId=746682) en wijzig deze indien nodig.</span><span class="sxs-lookup"><span data-stu-id="b1718-115">[Download the sample code](https://go.microsoft.com/fwlink/p/?LinkId=746682) and modify it as necessary.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1718-116">Voordat u de toepassing bouwt, werkt u de waarden in het *App.config* -bestand bij om de Azure AD-verificatie gegevens weer te geven die u hebt gemaakt in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b1718-116">Before you build the application, update the values in the *App.config* file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b1718-117">U moet in het bijzonder uw account instellingen voor de integratie sandbox gebruiken tijdens vroegtijdige ontwikkeling of voor het testen van de productie.</span><span class="sxs-lookup"><span data-stu-id="b1718-117">Specifically, you should use your integration sandbox account settings during early development or for testing in production.</span></span>

<span data-ttu-id="b1718-118">Onder **ScenarioSettings** in het *App.config* -bestand kunt u para meters instellen die automatisch worden door gegeven aan de scenario's die u uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b1718-118">Under **ScenarioSettings** in the *App.config* file, you can set parameters that will be automatically passed into the scenarios that you run.</span></span>

<span data-ttu-id="b1718-119">Als u de lijst met scenario's wilt wijzigen die worden uitgevoerd, kunt u regels voor commentaar in **IPartnerScenario \[ \] mainScenarios** of in een afzonderlijke **Get scenarios** -methode vinden in het bestand *Program.cs* .</span><span class="sxs-lookup"><span data-stu-id="b1718-119">To modify the list of scenarios that are run, comment out lines in **IPartnerScenario\[\] mainScenarios** or in an individual **Get Scenarios** method found in the *Program.cs* file.</span></span>

## <a name="java"></a><span data-ttu-id="b1718-120">Java</span><span class="sxs-lookup"><span data-stu-id="b1718-120">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="b1718-121">[Down load de voorbeeld code](https://go.microsoft.com/fwlink/p/?LinkId=2026887) en wijzig deze indien nodig.</span><span class="sxs-lookup"><span data-stu-id="b1718-121">[Download the sample code](https://go.microsoft.com/fwlink/p/?LinkId=2026887) and modify it as necessary.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b1718-122">Voordat u de toepassing bouwt, werkt u de waarden in het *SamplesConfigurations.js* bestand bij om de Azure AD-verificatie gegevens weer te geven die u in [Partner Center-verificatie](partner-center-authentication.md)hebt gemaakt.</span><span class="sxs-lookup"><span data-stu-id="b1718-122">Before you build the application, update the values in the *SamplesConfigurations.json* file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b1718-123">U moet in het bijzonder uw account instellingen voor de integratie sandbox gebruiken tijdens vroegtijdige ontwikkeling of voor het testen van de productie.</span><span class="sxs-lookup"><span data-stu-id="b1718-123">Specifically, you should use your integration sandbox account settings during early development or for testing in production.</span></span>

<span data-ttu-id="b1718-124">Onder **ScenarioSettings** in het *SamplesConfiguration.js* bestand kunt u para meters instellen die automatisch worden door gegeven aan de scenario's die u uitvoert.</span><span class="sxs-lookup"><span data-stu-id="b1718-124">Under **ScenarioSettings** in the *SamplesConfiguration.json* file, you can set parameters that will be automatically passed into the scenarios that you run.</span></span>

<span data-ttu-id="b1718-125">Als u de lijst met scenario's wilt wijzigen die worden uitgevoerd, kunt u regels voor opmerkingen maken in **IPartnerScenario \[ \] mainScenarios** of in een afzonderlijke **Get scenarios** -methode in het bestand *Program. java* .</span><span class="sxs-lookup"><span data-stu-id="b1718-125">To modify the list of scenarios that are run, comment out lines in **IPartnerScenario\[\] mainScenarios** or in an individual **Get Scenarios** method found in the *Program.java* file.</span></span>

## <a name="what-to-change"></a><span data-ttu-id="b1718-126">Wat u kunt wijzigen</span><span class="sxs-lookup"><span data-stu-id="b1718-126">What to change</span></span>

<span data-ttu-id="b1718-127">Gebruik de volgende lijsten om te bepalen wat u wilt wijzigen of niet wijzigen in de voorbeeld code.</span><span class="sxs-lookup"><span data-stu-id="b1718-127">Use the following lists to determine what to change or not change in the sample code.</span></span>

### <a name="partnerservicesettings"></a><span data-ttu-id="b1718-128">PartnerServiceSettings</span><span class="sxs-lookup"><span data-stu-id="b1718-128">PartnerServiceSettings</span></span>

<span data-ttu-id="b1718-129">Wijzig voor **PartnerServiceSettings** niet:</span><span class="sxs-lookup"><span data-stu-id="b1718-129">For **PartnerServiceSettings**, don't change:</span></span>

- <span data-ttu-id="b1718-130">**PartnerServiceApiEndpoint**</span><span class="sxs-lookup"><span data-stu-id="b1718-130">**PartnerServiceApiEndpoint**</span></span>
- <span data-ttu-id="b1718-131">**AuthenticationAuthorityEndpoint**</span><span class="sxs-lookup"><span data-stu-id="b1718-131">**AuthenticationAuthorityEndpoint**</span></span>
- <span data-ttu-id="b1718-132">**GraphEndpoint**</span><span class="sxs-lookup"><span data-stu-id="b1718-132">**GraphEndpoint**</span></span>
- <span data-ttu-id="b1718-133">**CommonDomain**</span><span class="sxs-lookup"><span data-stu-id="b1718-133">**CommonDomain**</span></span>

<span data-ttu-id="b1718-134">Al deze instellingen zijn nodig om de voor beeld-API-aanroepen goed te laten functioneren.</span><span class="sxs-lookup"><span data-stu-id="b1718-134">All of these settings are necessary for the sample API calls to properly function.</span></span>

### <a name="userauthentication"></a><span data-ttu-id="b1718-135">UserAuthentication</span><span class="sxs-lookup"><span data-stu-id="b1718-135">UserAuthentication</span></span>

<span data-ttu-id="b1718-136">Voor **UserAuthentication** moet u de volgende wijzigingen aanbrengen:</span><span class="sxs-lookup"><span data-stu-id="b1718-136">For **UserAuthentication**, you're required to change:</span></span>

- <span data-ttu-id="b1718-137">**ApplicationId** (uw Azure Active Directory toepassings-id die wordt gebruikt voor aanmelding)</span><span class="sxs-lookup"><span data-stu-id="b1718-137">**ApplicationId** (your Azure Active Directory application ID used for login)</span></span>
- <span data-ttu-id="b1718-138">**Gebruikers naam** (uw Active Directory-gebruikers naam)</span><span class="sxs-lookup"><span data-stu-id="b1718-138">**UserName** (your active directory username)</span></span>
- <span data-ttu-id="b1718-139">**Wacht woord** (uw Active Directory-wacht woord).</span><span class="sxs-lookup"><span data-stu-id="b1718-139">**Password** (your active directory password).</span></span>

<span data-ttu-id="b1718-140">Niet wijzigen:</span><span class="sxs-lookup"><span data-stu-id="b1718-140">Don't change:</span></span>

- <span data-ttu-id="b1718-141">**ResourceUrl**</span><span class="sxs-lookup"><span data-stu-id="b1718-141">**ResourceUrl**</span></span>
- <span data-ttu-id="b1718-142">**RedirectUrl**</span><span class="sxs-lookup"><span data-stu-id="b1718-142">**RedirectUrl**</span></span>

### <a name="appauthentication"></a><span data-ttu-id="b1718-143">AppAuthentication</span><span class="sxs-lookup"><span data-stu-id="b1718-143">AppAuthentication</span></span>

<span data-ttu-id="b1718-144">Voor **AppAuthentication** moet u de volgende wijzigingen aanbrengen:</span><span class="sxs-lookup"><span data-stu-id="b1718-144">For **AppAuthentication**, you're required to change:</span></span>

- <span data-ttu-id="b1718-145">**ApplicationId** (uw Active Directory-toepassings-id die wordt gebruikt voor het aanmelden van de toepassing)</span><span class="sxs-lookup"><span data-stu-id="b1718-145">**ApplicationId** (your active directory application ID used for application login)</span></span>
- <span data-ttu-id="b1718-146">**ApplicationSecret** (uw Active Directory-toepassings geheim gebruikt voor het aanmelden van de toepassing)</span><span class="sxs-lookup"><span data-stu-id="b1718-146">**ApplicationSecret** (your active directory application secret used for application login)</span></span>
- <span data-ttu-id="b1718-147">**Domein** (uw Active Directory-domein waarop de toepassing wordt gehost)</span><span class="sxs-lookup"><span data-stu-id="b1718-147">**Domain** (your active directory domain on which the application is hosted)</span></span>

### <a name="scenariosettings"></a><span data-ttu-id="b1718-148">ScenarioSettings</span><span class="sxs-lookup"><span data-stu-id="b1718-148">ScenarioSettings</span></span>

<span data-ttu-id="b1718-149">Wijzig voor **ScenarioSettings** niet:</span><span class="sxs-lookup"><span data-stu-id="b1718-149">For **ScenarioSettings**, don't change:</span></span>

- <span data-ttu-id="b1718-150">**CustomerDomainSuffix** (het domein achtervoegsel dat wordt gebruikt bij het maken van een nieuwe klant)</span><span class="sxs-lookup"><span data-stu-id="b1718-150">**CustomerDomainSuffix** (the domain suffix used when creating a new customer)</span></span>

<span data-ttu-id="b1718-151">Optionele instellingen.</span><span class="sxs-lookup"><span data-stu-id="b1718-151">Optional settings.</span></span> <span data-ttu-id="b1718-152">Als dit veld leeg blijft, moet deze informatie worden gegenereerd wanneer een scenario wordt uitgevoerd, waar nodig):</span><span class="sxs-lookup"><span data-stu-id="b1718-152">If left blank, this information will need to be inputted when running a scenario where necessary):</span></span>

- <span data-ttu-id="b1718-153">**CustomerIdToDelete** (de id van de klant die wordt gebruikt voor verwijdering)</span><span class="sxs-lookup"><span data-stu-id="b1718-153">**CustomerIdToDelete** (the ID of the customer used for deletion)</span></span>
- <span data-ttu-id="b1718-154">**DefaultCustomerId** (de klant-id die moet worden gebruikt in aan klanten gerelateerde scenario's)</span><span class="sxs-lookup"><span data-stu-id="b1718-154">**DefaultCustomerId** (the customer ID to use in customer-related scenarios)</span></span>
- <span data-ttu-id="b1718-155">**DefaultInvoiceID** (de factuur-ID die moet worden gebruikt in factuur scenario's)</span><span class="sxs-lookup"><span data-stu-id="b1718-155">**DefaultInvoiceID** (the invoice ID to use in invoice scenarios)</span></span>
- <span data-ttu-id="b1718-156">**PartnerMpnId** (de MPN-id van de partner die moet worden gebruikt in scenario's met indirecte partners)</span><span class="sxs-lookup"><span data-stu-id="b1718-156">**PartnerMpnId** (the partner MPN ID to use in indirect partner scenarios)</span></span>
- <span data-ttu-id="b1718-157">**DefaultServiceRequestId** (de service aanvraag-id die in service-aanvraag scenario's moet worden gebruikt)</span><span class="sxs-lookup"><span data-stu-id="b1718-157">**DefaultServiceRequestId** (the service request ID to use in service request scenarios)</span></span>
- <span data-ttu-id="b1718-158">**DefaultSupportTopicID** (de ondersteunings onderwerp-id die moet worden gebruikt in service-aanvraag scenario's)</span><span class="sxs-lookup"><span data-stu-id="b1718-158">**DefaultSupportTopicID** (the support topic ID to use in service request scenarios)</span></span>
- <span data-ttu-id="b1718-159">**DefaultOfferID** (de AANBIEDINGS-id die moet worden gebruikt in aanbod scenario's)</span><span class="sxs-lookup"><span data-stu-id="b1718-159">**DefaultOfferID** (the offer ID to use in offer scenarios)</span></span>
- <span data-ttu-id="b1718-160">**DefaultOrderID** (de order-id die in order scenario's moet worden gebruikt)</span><span class="sxs-lookup"><span data-stu-id="b1718-160">**DefaultOrderID** (the order ID to use in order scenarios)</span></span>
- <span data-ttu-id="b1718-161">**DefaultSubscriptionID** (de abonnements-id die moet worden gebruikt in scenario's voor abonnementen)</span><span class="sxs-lookup"><span data-stu-id="b1718-161">**DefaultSubscriptionID** (the subscription ID to use in subscription scenarios)</span></span>

<span data-ttu-id="b1718-162">Optioneel om te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b1718-162">Optional to change.</span></span> <span data-ttu-id="b1718-163">Met al deze instellingen geeft u de hoeveelheid items per pagina op tijdens het ophalen van de pagina-inhoud:</span><span class="sxs-lookup"><span data-stu-id="b1718-163">All of these settings specify the amount of entries per page when retrieving paged content:</span></span>

- <span data-ttu-id="b1718-164">**CustomerPageSize**</span><span class="sxs-lookup"><span data-stu-id="b1718-164">**CustomerPageSize**</span></span>
- <span data-ttu-id="b1718-165">**InvoicePageSize**</span><span class="sxs-lookup"><span data-stu-id="b1718-165">**InvoicePageSize**</span></span>
- <span data-ttu-id="b1718-166">**ServiceRequestPageSize**</span><span class="sxs-lookup"><span data-stu-id="b1718-166">**ServiceRequestPageSize**</span></span>
- <span data-ttu-id="b1718-167">**DefaultOfferPageSize**</span><span class="sxs-lookup"><span data-stu-id="b1718-167">**DefaultOfferPageSize**</span></span>
- <span data-ttu-id="b1718-168">**SubscriptionPageSize**</span><span class="sxs-lookup"><span data-stu-id="b1718-168">**SubscriptionPageSize**</span></span>
