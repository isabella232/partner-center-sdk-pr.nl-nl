---
title: API-toegang instellen in Partnercentrum
description: Stel accounts in voor de ontwikkeling van de Partner Center-SDK en test in de sandbox voor integratie.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 873ff2ff9cecbfa92429958d3bfe2aa79fc3ad9a
ms.sourcegitcommit: d5de47c08ba661ba5de4935caa6843d7c2c91710
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/28/2020
ms.locfileid: "97767400"
---
# <a name="set-up-api-access-in-partner-center"></a><span data-ttu-id="6b67f-103">API-toegang instellen in Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="6b67f-103">Set up API access in Partner Center</span></span>

<span data-ttu-id="6b67f-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="6b67f-104">**Applies to:**</span></span>

- <span data-ttu-id="6b67f-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="6b67f-105">Partner Center</span></span>
- <span data-ttu-id="6b67f-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="6b67f-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="6b67f-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6b67f-107">Partner Center for Microsoft Cloud for US Government</span></span>
- <span data-ttu-id="6b67f-108">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="6b67f-108">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="6b67f-109">In dit artikel worden de accounts beschreven die u nodig hebt om te ontwikkelen met de Partner Center-SDK.</span><span class="sxs-lookup"><span data-stu-id="6b67f-109">This article describes the accounts you need to develop against the Partner Center SDK.</span></span> <span data-ttu-id="6b67f-110">In dit artikel wordt ook uitgelegd hoe u een [account voor integratie sandbox](#integration-sandbox-account) maakt en test in de sandbox voor integratie.</span><span class="sxs-lookup"><span data-stu-id="6b67f-110">This article also explains how to create an [integration sandbox account](#integration-sandbox-account) and test in the integration sandbox.</span></span>

>[!NOTE]
><span data-ttu-id="6b67f-111">Als u toegang wilt krijgen tot Api's, moet uw Tenant een CSP-Tenant zijn en moet u een indirecte provider of een directe factuur partner zijn.</span><span class="sxs-lookup"><span data-stu-id="6b67f-111">To get access to APIs, your tenant must be a CSP tenant and you must be either an indirect provider or a Direct bill partner.</span></span>

## <a name="account-definitions"></a><span data-ttu-id="6b67f-112">Account definities</span><span class="sxs-lookup"><span data-stu-id="6b67f-112">Account definitions</span></span>

<span data-ttu-id="6b67f-113">Om u te helpen uw API-integratie te integreren en te testen, ondersteunt het partner centrum twee soorten accounts:</span><span class="sxs-lookup"><span data-stu-id="6b67f-113">To help you integrate and test your API integration, Partner Center supports two kinds of accounts:</span></span>

### <a name="primary-partner-account"></a><span data-ttu-id="6b67f-114">Account voor primaire partner</span><span class="sxs-lookup"><span data-stu-id="6b67f-114">Primary Partner account</span></span>

<span data-ttu-id="6b67f-115">Met deze account maakt u echte bestellingen voor echte klanten.</span><span class="sxs-lookup"><span data-stu-id="6b67f-115">This account is where you create real orders for real customers.</span></span> <span data-ttu-id="6b67f-116">Als u wijzigingen of trans acties aanbrengt wanneer u bent aangemeld bij het primaire account, wordt het gebruik van de Partner Center SDK of de gebruikers interface van het dash board van de partner beschouwd als officiële orders voor echte klanten.</span><span class="sxs-lookup"><span data-stu-id="6b67f-116">If you make any changes or transactions when you are signed in to the primary account, by using either the Partner Center SDK or the Partner Dashboard UI, they will be treated as official orders for real customers.</span></span> <span data-ttu-id="6b67f-117">Ze worden weer gegeven in uw factuur en uw bedrijf is verantwoordelijk voor het betalen ervan.</span><span class="sxs-lookup"><span data-stu-id="6b67f-117">They will be reflected in your invoice, and your company is responsible for paying for them.</span></span>

### <a name="integration-sandbox-account"></a><span data-ttu-id="6b67f-118">Sandboxaccount voor integratie</span><span class="sxs-lookup"><span data-stu-id="6b67f-118">Integration sandbox account</span></span>

<span data-ttu-id="6b67f-119">Dit account is voor het testen van uw code en de integratie met de partner centrum-Api's voordat u deze breed implementeert.</span><span class="sxs-lookup"><span data-stu-id="6b67f-119">This account is for testing your code and its integration with the Partner Center APIs before you deploy it broadly.</span></span> <span data-ttu-id="6b67f-120">Wijzigingen en trans acties die u aanbrengt wanneer u zich aanmeldt bij het integratie sandbox-account, worden in uw factuur weer gegeven, maar u hoeft het factuur bedrag niet te betalen.</span><span class="sxs-lookup"><span data-stu-id="6b67f-120">Changes and transactions you make when you are signed into the integration sandbox account will appear in your invoice, however, you do not have to pay the invoice amount.</span></span> <span data-ttu-id="6b67f-121">Factuur-PDF heeft een disclaimer als ' niet betalen.</span><span class="sxs-lookup"><span data-stu-id="6b67f-121">Invoice pdf will have a disclaimer as "DO NOT PAY.</span></span> <span data-ttu-id="6b67f-122">DIT IS EEN SANDBOX-FACTUUR EN ER IS GEEN ACTIE VEREIST. "</span><span class="sxs-lookup"><span data-stu-id="6b67f-122">THIS IS A SANDBOX INVOICE AND NO ACTION IS REQUIRED."</span></span>

<span data-ttu-id="6b67f-123">De integratie sandbox-account en het primaire account handelen onafhankelijk en delen geen beheerders accounts, gebruikers accounts, klanten, bestellingen, abonnementen of andere gegevens.</span><span class="sxs-lookup"><span data-stu-id="6b67f-123">The integration sandbox account and the primary account act independently, and do not share admin accounts, user accounts, customers, orders, subscriptions, or other data.</span></span>

<span data-ttu-id="6b67f-124">De integratie sandbox ondersteunt trans acties met een beperkt aantal klanten, bestellingen, abonnementen, licenties, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="6b67f-124">The integration sandbox supports transactions with a limited number of customers, orders, subscriptions, licenses, etc.</span></span>

<span data-ttu-id="6b67f-125">Op basis van beleid worden Sandbox-accounts voor integratie alleen gebruikt voor het testen van de integratie.</span><span class="sxs-lookup"><span data-stu-id="6b67f-125">By policy, integration sandbox accounts are for integration testing purposes only.</span></span>

<span data-ttu-id="6b67f-126">Standaard is er geen sandboxaccount voor integratie.</span><span class="sxs-lookup"><span data-stu-id="6b67f-126">By default, there is no integration sandbox account.</span></span> <span data-ttu-id="6b67f-127">U moet er zelf een maken als u van plan bent de Partner Center-SDK te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="6b67f-127">You must create one yourself if you plan to use the Partner Center SDK.</span></span>

## <a name="set-up-your-accounts"></a><span data-ttu-id="6b67f-128">Uw accounts instellen</span><span class="sxs-lookup"><span data-stu-id="6b67f-128">Set up your accounts</span></span>

<span data-ttu-id="6b67f-129">In deze sectie wordt beschreven hoe u een account voor een primaire partner en een beveiligingssandbox voor integratie kunt instellen voor de partner centrum-SDK.</span><span class="sxs-lookup"><span data-stu-id="6b67f-129">This section describes how to set up a primary Partner account and an integration sandbox account for the Partner Center SDK.</span></span>

### <a name="create-an-integration-sandbox"></a><span data-ttu-id="6b67f-130">Een integratie sandbox maken</span><span class="sxs-lookup"><span data-stu-id="6b67f-130">Create an integration sandbox</span></span>

1. <span data-ttu-id="6b67f-131">Meld u aan bij het dash board van de partner met een globaal beheerders account (uw primaire partner account.)</span><span class="sxs-lookup"><span data-stu-id="6b67f-131">Sign in to Partner Dashboard with a global admin account (your primary Partner account.)</span></span>

2. <span data-ttu-id="6b67f-132">Kies in het menu **instellingen** (pictogram tandwiel) de optie **partner instellingen**.</span><span class="sxs-lookup"><span data-stu-id="6b67f-132">From the **Settings** menu (gear icon), choose **Partner settings**.</span></span>

3. <span data-ttu-id="6b67f-133">Kies **integratie sandbox** tabblad.</span><span class="sxs-lookup"><span data-stu-id="6b67f-133">Choose **Integration sandbox** tab.</span></span>

    >[!NOTE]
    ><span data-ttu-id="6b67f-134">Als u geen sandbox-optie voor integratie ziet, hebt u mogelijk geen globaal beheerders account.</span><span class="sxs-lookup"><span data-stu-id="6b67f-134">If you don't see an Integration sandbox option, you might not have a global admin account.</span></span> <span data-ttu-id="6b67f-135">Het is ook mogelijk dat u een sandbox-integratie account gebruikt en dat er al een integratie sandbox is ingesteld.</span><span class="sxs-lookup"><span data-stu-id="6b67f-135">You also might be using an integration sandbox account and an integration sandbox has already been set up.</span></span>

4. <span data-ttu-id="6b67f-136">Voer de contact gegevens in voor het account voor de integratie sandbox-beheerder.</span><span class="sxs-lookup"><span data-stu-id="6b67f-136">Enter the contact information for the integration sandbox admin account.</span></span> <span data-ttu-id="6b67f-137">Kies vervolgens **account maken**.</span><span class="sxs-lookup"><span data-stu-id="6b67f-137">Then, choose **Create account**.</span></span> <span data-ttu-id="6b67f-138">Wacht een paar minuten totdat er een bevestigings bericht wordt gegenereerd dat het account is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="6b67f-138">Wait a few minutes for a confirmation message that the account has been created.</span></span>

5. <span data-ttu-id="6b67f-139">Nadat u het bevestigings bericht hebt weer gegeven, meldt u zich af bij het dash board van de partner.</span><span class="sxs-lookup"><span data-stu-id="6b67f-139">After you see the confirmation message, sign out of Partner Dashboard.</span></span>

6. <span data-ttu-id="6b67f-140">Meld u weer aan met uw nieuwe integratie sandbox-beheerders account.</span><span class="sxs-lookup"><span data-stu-id="6b67f-140">Sign back in with your new integration sandbox admin account.</span></span> <span data-ttu-id="6b67f-141">Zorg ervoor dat u de indeling **username@domain** voor uw referenties gebruikt, samen met het wacht woord dat u zojuist hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="6b67f-141">Be sure to use the format **username@domain** for your credentials along with the password that you just specified.</span></span>

7. <span data-ttu-id="6b67f-142">Kies **account instellen** boven **huidige taken** om de instelling van het sandbox-account te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="6b67f-142">Choose **Set Up Account** above **Current Tasks** to complete the sandbox account setup.</span></span>

### <a name="enable-api-access"></a><span data-ttu-id="6b67f-143">API-toegang inschakelen</span><span class="sxs-lookup"><span data-stu-id="6b67f-143">Enable API access</span></span>

<span data-ttu-id="6b67f-144">Nadat uw account is ingesteld, moet u API-toegang inschakelen voordat u de Partnercentrum-SDK kunt gebruiken met de sandbox voor integratie.</span><span class="sxs-lookup"><span data-stu-id="6b67f-144">After your account is set up, you must enable API access before you can use the Partner Center SDK with the integration sandbox.</span></span> <span data-ttu-id="6b67f-145">U moet de toegang tot de API afzonderlijk inschakelen voor zowel uw primaire partneraccount als uw sandboxaccount voor integratie.</span><span class="sxs-lookup"><span data-stu-id="6b67f-145">You need to enable access to the API separately for both your primary Partner account and your integration sandbox account.</span></span>

1. <span data-ttu-id="6b67f-146">Meld u aan bij het partner dashboard met een globaal beheerders account.</span><span class="sxs-lookup"><span data-stu-id="6b67f-146">Sign into Partner Dashboard using a global admin account.</span></span>

2. <span data-ttu-id="6b67f-147">Selecteer **partner instellingen** in het menu **instellingen** (pictogram tandwiel).</span><span class="sxs-lookup"><span data-stu-id="6b67f-147">From the **Settings** menu (gear icon), select **Partner settings**.</span></span>

3. <span data-ttu-id="6b67f-148">Kies op de pagina **account instellingen** de optie **app-beheer**.</span><span class="sxs-lookup"><span data-stu-id="6b67f-148">On the **Account settings** page, choose **App management**.</span></span>

4. <span data-ttu-id="6b67f-149">Als u nog geen app hebt, voegt u een nieuwe web-app toe.</span><span class="sxs-lookup"><span data-stu-id="6b67f-149">If you do not already have an existing app, add a new web app.</span></span> <span data-ttu-id="6b67f-150">Als u een bestaande web-app hebt, kiest u de knop **sleutel toevoegen** .</span><span class="sxs-lookup"><span data-stu-id="6b67f-150">If you have an existing web app, choose the **Add key** button.</span></span>

5. <span data-ttu-id="6b67f-151">Kopieer de gegevens van de app-registratie, met name de **sleutel** als u een web-app maakt en sla deze op een veilige plaats op.</span><span class="sxs-lookup"><span data-stu-id="6b67f-151">Copy the app registration information, especially the **Key** if you're creating a web app, and store it in a safe place.</span></span>

6. <span data-ttu-id="6b67f-152">Meld u af bij het dash board van de partner.</span><span class="sxs-lookup"><span data-stu-id="6b67f-152">Sign out of Partner Dashboard.</span></span>

7. <span data-ttu-id="6b67f-153">Meld u weer aan met uw sandbox-account voor integratie.</span><span class="sxs-lookup"><span data-stu-id="6b67f-153">Sign back in with your integration sandbox account.</span></span> <span data-ttu-id="6b67f-154">Herhaal de stappen 2-5 om API-toegang in te scha kelen in de sandbox voor integratie.</span><span class="sxs-lookup"><span data-stu-id="6b67f-154">Repeat steps 2-5 to enable API access in the integration sandbox.</span></span>

## <a name="write-and-test-code"></a><span data-ttu-id="6b67f-155">Code schrijven en testen</span><span class="sxs-lookup"><span data-stu-id="6b67f-155">Write and test code</span></span>

<span data-ttu-id="6b67f-156">U kunt code en test code schrijven in de integratie sandbox.</span><span class="sxs-lookup"><span data-stu-id="6b67f-156">You can write code and test code in the integration sandbox.</span></span> <span data-ttu-id="6b67f-157">U hebt de volgende informatie nodig om [Partner Center-verificatie](partner-center-authentication.md) in te stellen met Azure AD.</span><span class="sxs-lookup"><span data-stu-id="6b67f-157">You'll need the following information to [set up Partner Center authentication](partner-center-authentication.md) with Azure AD.</span></span>

| <span data-ttu-id="6b67f-158">Itemnaam</span><span class="sxs-lookup"><span data-stu-id="6b67f-158">Item name</span></span> | <span data-ttu-id="6b67f-159">Item locatie</span><span class="sxs-lookup"><span data-stu-id="6b67f-159">Item location</span></span> |
| --------- | ------------- |
| <span data-ttu-id="6b67f-160">App-ID/client-ID</span><span class="sxs-lookup"><span data-stu-id="6b67f-160">App ID / Client ID</span></span> | <span data-ttu-id="6b67f-161">Selecteer **partner instellingen** in het menu **instellingen** (pictogram tandwiel).</span><span class="sxs-lookup"><span data-stu-id="6b67f-161">From the **Settings** menu (gear icon), select **Partner settings**.</span></span> <span data-ttu-id="6b67f-162">Selecteer op de pagina **account instellingen** de optie **app-beheer**.</span><span class="sxs-lookup"><span data-stu-id="6b67f-162">On the **Account settings** page, select **App Management**.</span></span> <span data-ttu-id="6b67f-163">De App-ID/client-ID wordt vermeld als de **geregistreerde app-id** van de toepassing.</span><span class="sxs-lookup"><span data-stu-id="6b67f-163">The App ID/Client ID is listed as the **Registered application App ID**.</span></span> |
| <span data-ttu-id="6b67f-164">Sleutel</span><span class="sxs-lookup"><span data-stu-id="6b67f-164">Key</span></span> | <span data-ttu-id="6b67f-165">Als u een web-app hebt gemaakt in de sectie [API-toegang inschakelen](#enable-api-access), is dit de sleutel die u hebt opgeslagen in stap 5.</span><span class="sxs-lookup"><span data-stu-id="6b67f-165">If you created a web app in the section [Enable API access](#enable-api-access), this is the key that you saved in step 5.</span></span> |
| <span data-ttu-id="6b67f-166">Domain</span><span class="sxs-lookup"><span data-stu-id="6b67f-166">Domain</span></span> | <span data-ttu-id="6b67f-167">Het domein voor de integratie sandbox.</span><span class="sxs-lookup"><span data-stu-id="6b67f-167">The domain for the integration sandbox.</span></span> |

## <a name="run-tested-code"></a><span data-ttu-id="6b67f-168">Geteste code uitvoeren</span><span class="sxs-lookup"><span data-stu-id="6b67f-168">Run tested code</span></span>

<span data-ttu-id="6b67f-169">Als u uw oplossing wilt gebruiken met echte klant gegevens, moet u de referenties van uw integratie sandbox wijzigen naar de referenties van uw primaire partner account.</span><span class="sxs-lookup"><span data-stu-id="6b67f-169">To use your solution with real customer data, you must change from your integration sandbox credentials to your primary Partner account credentials.</span></span>

<span data-ttu-id="6b67f-170">Wanneer u klaar bent om uw geteste code te gebruiken in uw primaire partner account, moet u een Azure AD-beveiligings token ontvangen.</span><span class="sxs-lookup"><span data-stu-id="6b67f-170">When you're ready to use your tested code in your primary Partner account, you must get an Azure AD security token.</span></span> <span data-ttu-id="6b67f-171">Dit beveiligings token is gebaseerd op uw partner centrum-app, sleutel en domein (in plaats van uw sandbox-app voor integratie, sleutel en domein).</span><span class="sxs-lookup"><span data-stu-id="6b67f-171">This security token is based on your Partner Center app, key and domain (instead of your integration sandbox app, key and domain).</span></span>

1. <span data-ttu-id="6b67f-172">Volg de stappen in [Partner Center-verificatie](partner-center-authentication.md) voor het verkrijgen van een Azure AD-beveiligings token met behulp van uw referenties voor het primaire partner centrum.</span><span class="sxs-lookup"><span data-stu-id="6b67f-172">Follow the steps in [Partner Center authentication](partner-center-authentication.md) to get an Azure AD security token using your primary Partner Center credentials.</span></span> <span data-ttu-id="6b67f-173">(U hebt deze stappen eerder gevolgd om een Azure AD-beveiligings token op te halen voor uw integratie sandbox.)</span><span class="sxs-lookup"><span data-stu-id="6b67f-173">(You previously followed these steps to get an Azure AD security token for your integration sandbox.)</span></span>

2. <span data-ttu-id="6b67f-174">Vervang het beveiligings token voor integratie in uw code door het nieuwe beveiligings token voor uw account voor primaire partner.</span><span class="sxs-lookup"><span data-stu-id="6b67f-174">Replace the integration security token in your code with the new security token for your primary Partner account.</span></span>
