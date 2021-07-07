---
title: Console-testapp
description: Deze consoletest-app biedt voorbeeldcode voor alle scenario's die worden ondersteund door Partner Center API's. U kunt deze ook gebruiken voor het testen.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b35167104deeede50107d59fca6112c10dc7b4bf
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974026"
---
# <a name="console-test-app"></a><span data-ttu-id="30eb1-104">Console-testapp</span><span class="sxs-lookup"><span data-stu-id="30eb1-104">Console test app</span></span>

<span data-ttu-id="30eb1-105">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="30eb1-105">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="30eb1-106">De consoletest-app is beschikbaar in C# en Java en bevat voorbeeldcodes voor alle scenario's die worden ondersteund door de Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="30eb1-106">The console test app is provided in C# and Java, it provides sample codes for all of the scenarios supported by the Partner Center APIs.</span></span> <span data-ttu-id="30eb1-107">U kunt deze ook gebruiken voor het testen.</span><span class="sxs-lookup"><span data-stu-id="30eb1-107">You can also use it for testing.</span></span>

## <a name="get-the-code"></a><span data-ttu-id="30eb1-108">Code ophalen</span><span class="sxs-lookup"><span data-stu-id="30eb1-108">Get the code</span></span>

<span data-ttu-id="30eb1-109">Download de voorbeeldcode voor de consoletest-app.</span><span class="sxs-lookup"><span data-stu-id="30eb1-109">Download the sample code for the console test app.</span></span>

## <a name="net"></a><span data-ttu-id="30eb1-110">.NET</span><span class="sxs-lookup"><span data-stu-id="30eb1-110">.NET</span></span>

<span data-ttu-id="30eb1-111">[Download de voorbeeldcode en](https://go.microsoft.com/fwlink/p/?LinkId=746682) wijzig deze indien nodig.</span><span class="sxs-lookup"><span data-stu-id="30eb1-111">[Download the sample code](https://go.microsoft.com/fwlink/p/?LinkId=746682) and modify it as necessary.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30eb1-112">Voordat u de toepassing bouwt,  moet u de waarden in hetApp.config-bestand bijwerken om de Azure AD-verificatiegegevens weer te geven die u hebt gemaakt in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="30eb1-112">Before you build the application, update the values in the *App.config* file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="30eb1-113">Gebruik met name de instellingen van uw sandbox-account voor integratie tijdens vroege ontwikkeling of voor testen in productie.</span><span class="sxs-lookup"><span data-stu-id="30eb1-113">Specifically, you should use your integration sandbox account settings during early development or for testing in production.</span></span>

<span data-ttu-id="30eb1-114">Onder **ScenarioSettings** in *hetApp.config* kunt u parameters instellen die automatisch worden doorgegeven aan de scenario's die u wilt uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="30eb1-114">Under **ScenarioSettings** in the *App.config* file, you can set parameters that will be automatically passed into the scenarios that you run.</span></span>

<span data-ttu-id="30eb1-115">Als u de lijst met scenario's wilt wijzigen die worden uitgevoerd, maakt u commentaar van regels in **IPartnerScenario \[ \] mainScenarios** of in een afzonderlijke methode **Get Scenarios** in het *bestand Program.cs.*</span><span class="sxs-lookup"><span data-stu-id="30eb1-115">To modify the list of scenarios that are run, comment out lines in **IPartnerScenario\[\] mainScenarios** or in an individual **Get Scenarios** method found in the *Program.cs* file.</span></span>

## <a name="java"></a><span data-ttu-id="30eb1-116">Java</span><span class="sxs-lookup"><span data-stu-id="30eb1-116">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="30eb1-117">[Download de voorbeeldcode en](https://go.microsoft.com/fwlink/p/?LinkId=2026887) wijzig deze indien nodig.</span><span class="sxs-lookup"><span data-stu-id="30eb1-117">[Download the sample code](https://go.microsoft.com/fwlink/p/?LinkId=2026887) and modify it as necessary.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="30eb1-118">Voordat u de toepassing bouwt, moet u de waarden in het bestand *SamplesConfigurations.js* bijwerken om de Azure AD-verificatiegegevens weer te geven die u hebt gemaakt in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="30eb1-118">Before you build the application, update the values in the *SamplesConfigurations.json* file to reflect the Azure AD authentication information you created in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="30eb1-119">Gebruik met name de instellingen van uw sandbox-account voor integratie tijdens vroege ontwikkeling of voor testen in productie.</span><span class="sxs-lookup"><span data-stu-id="30eb1-119">Specifically, you should use your integration sandbox account settings during early development or for testing in production.</span></span>

<span data-ttu-id="30eb1-120">Onder **ScenarioSettings** in *SamplesConfiguration.json* file kunt u parameters instellen die automatisch worden doorgegeven aan de scenario's die u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="30eb1-120">Under **ScenarioSettings** in the *SamplesConfiguration.json* file, you can set parameters that will be automatically passed into the scenarios that you run.</span></span>

<span data-ttu-id="30eb1-121">Als u de lijst met scenario's wilt wijzigen die worden uitgevoerd, maakt u commentaar van regels in **IPartnerScenario \[ \] mainScenarios** of in een afzonderlijke methode **Get Scenarios** in het *bestand Program.java.*</span><span class="sxs-lookup"><span data-stu-id="30eb1-121">To modify the list of scenarios that are run, comment out lines in **IPartnerScenario\[\] mainScenarios** or in an individual **Get Scenarios** method found in the *Program.java* file.</span></span>

## <a name="what-to-change"></a><span data-ttu-id="30eb1-122">Wat u moet wijzigen</span><span class="sxs-lookup"><span data-stu-id="30eb1-122">What to change</span></span>

<span data-ttu-id="30eb1-123">Gebruik de volgende lijsten om te bepalen wat er wel of niet moet worden gewijzigd in de voorbeeldcode.</span><span class="sxs-lookup"><span data-stu-id="30eb1-123">Use the following lists to determine what to change or not change in the sample code.</span></span>

### <a name="partnerservicesettings"></a><span data-ttu-id="30eb1-124">PartnerServiceSettings</span><span class="sxs-lookup"><span data-stu-id="30eb1-124">PartnerServiceSettings</span></span>

<span data-ttu-id="30eb1-125">Voor **PartnerServiceSettings** wijzigt u niet:</span><span class="sxs-lookup"><span data-stu-id="30eb1-125">For **PartnerServiceSettings**, don't change:</span></span>

- <span data-ttu-id="30eb1-126">**PartnerServiceApiEndpoint**</span><span class="sxs-lookup"><span data-stu-id="30eb1-126">**PartnerServiceApiEndpoint**</span></span>
- <span data-ttu-id="30eb1-127">**AuthenticationAuthorityEndpoint**</span><span class="sxs-lookup"><span data-stu-id="30eb1-127">**AuthenticationAuthorityEndpoint**</span></span>
- <span data-ttu-id="30eb1-128">**GraphEndpoint**</span><span class="sxs-lookup"><span data-stu-id="30eb1-128">**GraphEndpoint**</span></span>
- <span data-ttu-id="30eb1-129">**CommonDomain**</span><span class="sxs-lookup"><span data-stu-id="30eb1-129">**CommonDomain**</span></span>

<span data-ttu-id="30eb1-130">Al deze instellingen zijn nodig om de voorbeeld-API-aanroepen goed te laten functioneren.</span><span class="sxs-lookup"><span data-stu-id="30eb1-130">All of these settings are necessary for the sample API calls to properly function.</span></span>

### <a name="userauthentication"></a><span data-ttu-id="30eb1-131">UserAuthentication</span><span class="sxs-lookup"><span data-stu-id="30eb1-131">UserAuthentication</span></span>

<span data-ttu-id="30eb1-132">Voor **UserAuthentication** moet u het volgende wijzigen:</span><span class="sxs-lookup"><span data-stu-id="30eb1-132">For **UserAuthentication**, you're required to change:</span></span>

- <span data-ttu-id="30eb1-133">**ApplicationId** (uw Azure Active Directory-toepassings-id die wordt gebruikt voor aanmelding)</span><span class="sxs-lookup"><span data-stu-id="30eb1-133">**ApplicationId** (your Azure Active Directory application ID used for login)</span></span>
- <span data-ttu-id="30eb1-134">**Gebruikersnaam** (gebruikersnaam active directory)</span><span class="sxs-lookup"><span data-stu-id="30eb1-134">**UserName** (your active directory username)</span></span>
- <span data-ttu-id="30eb1-135">**Wachtwoord** (uw Active Directory-wachtwoord).</span><span class="sxs-lookup"><span data-stu-id="30eb1-135">**Password** (your active directory password).</span></span>

<span data-ttu-id="30eb1-136">Niet wijzigen:</span><span class="sxs-lookup"><span data-stu-id="30eb1-136">Don't change:</span></span>

- <span data-ttu-id="30eb1-137">**ResourceUrl**</span><span class="sxs-lookup"><span data-stu-id="30eb1-137">**ResourceUrl**</span></span>
- <span data-ttu-id="30eb1-138">**RedirectUrl**</span><span class="sxs-lookup"><span data-stu-id="30eb1-138">**RedirectUrl**</span></span>

### <a name="appauthentication"></a><span data-ttu-id="30eb1-139">AppAuthentication</span><span class="sxs-lookup"><span data-stu-id="30eb1-139">AppAuthentication</span></span>

<span data-ttu-id="30eb1-140">Voor **AppAuthentication** moet u het volgende wijzigen:</span><span class="sxs-lookup"><span data-stu-id="30eb1-140">For **AppAuthentication**, you're required to change:</span></span>

- <span data-ttu-id="30eb1-141">**ApplicationId** (de toepassings-id van uw Active Directory die wordt gebruikt voor aanmelding bij de toepassing)</span><span class="sxs-lookup"><span data-stu-id="30eb1-141">**ApplicationId** (your active directory application ID used for application login)</span></span>
- <span data-ttu-id="30eb1-142">**ApplicationSecret (uw** active directory-toepassingsgeheim dat wordt gebruikt voor aanmelding bij de toepassing)</span><span class="sxs-lookup"><span data-stu-id="30eb1-142">**ApplicationSecret** (your active directory application secret used for application login)</span></span>
- <span data-ttu-id="30eb1-143">**Domein** (uw Active Directory-domein waarop de toepassing wordt gehost)</span><span class="sxs-lookup"><span data-stu-id="30eb1-143">**Domain** (your active directory domain on which the application is hosted)</span></span>

### <a name="scenariosettings"></a><span data-ttu-id="30eb1-144">ScenarioSettings</span><span class="sxs-lookup"><span data-stu-id="30eb1-144">ScenarioSettings</span></span>

<span data-ttu-id="30eb1-145">Voor **ScenarioSettings** wijzigt u niet:</span><span class="sxs-lookup"><span data-stu-id="30eb1-145">For **ScenarioSettings**, don't change:</span></span>

- <span data-ttu-id="30eb1-146">**CustomerDomainSuffix** (het domeinachtervoegsel dat wordt gebruikt bij het maken van een nieuwe klant)</span><span class="sxs-lookup"><span data-stu-id="30eb1-146">**CustomerDomainSuffix** (the domain suffix used when creating a new customer)</span></span>

<span data-ttu-id="30eb1-147">Optionele instellingen.</span><span class="sxs-lookup"><span data-stu-id="30eb1-147">Optional settings.</span></span> <span data-ttu-id="30eb1-148">Als u dit leeg laat, moet deze informatie worden ingevoerd bij het uitvoeren van een scenario, indien nodig):</span><span class="sxs-lookup"><span data-stu-id="30eb1-148">If left blank, this information will need to be inputted when running a scenario where necessary):</span></span>

- <span data-ttu-id="30eb1-149">**CustomerIdToDelete** (de id van de klant die is gebruikt voor verwijdering)</span><span class="sxs-lookup"><span data-stu-id="30eb1-149">**CustomerIdToDelete** (the ID of the customer used for deletion)</span></span>
- <span data-ttu-id="30eb1-150">**DefaultCustomerId** (de klant-id die moet worden gebruikt in klantgerelateerde scenario's)</span><span class="sxs-lookup"><span data-stu-id="30eb1-150">**DefaultCustomerId** (the customer ID to use in customer-related scenarios)</span></span>
- <span data-ttu-id="30eb1-151">**DefaultInvoiceID** (de factuur-id die moet worden gebruikt in factuurscenario's)</span><span class="sxs-lookup"><span data-stu-id="30eb1-151">**DefaultInvoiceID** (the invoice ID to use in invoice scenarios)</span></span>
- <span data-ttu-id="30eb1-152">**PartnerMpnId** (de MPN-id van de partner die moet worden gebruikt in indirecte partnerscenario's)</span><span class="sxs-lookup"><span data-stu-id="30eb1-152">**PartnerMpnId** (the partner MPN ID to use in indirect partner scenarios)</span></span>
- <span data-ttu-id="30eb1-153">**DefaultServiceRequestId** (de serviceaanvraag-id voor gebruik in serviceaanvraagscenario's)</span><span class="sxs-lookup"><span data-stu-id="30eb1-153">**DefaultServiceRequestId** (the service request ID to use in service request scenarios)</span></span>
- <span data-ttu-id="30eb1-154">**DefaultSupportTopicID** (de id van het ondersteuningsonderwerp voor gebruik in serviceaanvraagscenario's)</span><span class="sxs-lookup"><span data-stu-id="30eb1-154">**DefaultSupportTopicID** (the support topic ID to use in service request scenarios)</span></span>
- <span data-ttu-id="30eb1-155">**DefaultOfferID** (de aanbiedings-id die moet worden gebruikt in aanbiedingsscenario's)</span><span class="sxs-lookup"><span data-stu-id="30eb1-155">**DefaultOfferID** (the offer ID to use in offer scenarios)</span></span>
- <span data-ttu-id="30eb1-156">**DefaultOrderID** (de order-id die moet worden gebruikt in orderscenario's)</span><span class="sxs-lookup"><span data-stu-id="30eb1-156">**DefaultOrderID** (the order ID to use in order scenarios)</span></span>
- <span data-ttu-id="30eb1-157">**DefaultSubscriptionID** (de abonnements-id die moet worden gebruikt in abonnementsscenario's)</span><span class="sxs-lookup"><span data-stu-id="30eb1-157">**DefaultSubscriptionID** (the subscription ID to use in subscription scenarios)</span></span>

<span data-ttu-id="30eb1-158">Optioneel om te wijzigen.</span><span class="sxs-lookup"><span data-stu-id="30eb1-158">Optional to change.</span></span> <span data-ttu-id="30eb1-159">Al deze instellingen geven de hoeveelheid vermeldingen per pagina op bij het ophalen van pagina-inhoud:</span><span class="sxs-lookup"><span data-stu-id="30eb1-159">All of these settings specify the amount of entries per page when retrieving paged content:</span></span>

- <span data-ttu-id="30eb1-160">**CustomerPageSize**</span><span class="sxs-lookup"><span data-stu-id="30eb1-160">**CustomerPageSize**</span></span>
- <span data-ttu-id="30eb1-161">**InvoicePageSize**</span><span class="sxs-lookup"><span data-stu-id="30eb1-161">**InvoicePageSize**</span></span>
- <span data-ttu-id="30eb1-162">**ServiceRequestPageSize**</span><span class="sxs-lookup"><span data-stu-id="30eb1-162">**ServiceRequestPageSize**</span></span>
- <span data-ttu-id="30eb1-163">**DefaultOfferPageSize**</span><span class="sxs-lookup"><span data-stu-id="30eb1-163">**DefaultOfferPageSize**</span></span>
- <span data-ttu-id="30eb1-164">**SubscriptionPageSize**</span><span class="sxs-lookup"><span data-stu-id="30eb1-164">**SubscriptionPageSize**</span></span>
