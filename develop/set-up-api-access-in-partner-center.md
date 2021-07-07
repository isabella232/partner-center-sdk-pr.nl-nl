---
title: API-toegang instellen in Partnercentrum
description: Accounts instellen voor het ontwikkelen op de Partnercentrum-SDK en testen in de integratie-sandbox.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2c564baa9b626ff6ce21f9bcc517902d7cf99244
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547424"
---
# <a name="set-up-api-access-in-partner-center"></a><span data-ttu-id="349d9-103">API-toegang instellen in Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="349d9-103">Set up API access in Partner Center</span></span>

<span data-ttu-id="349d9-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud for US Government | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="349d9-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud for US Government | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="349d9-105">In dit artikel worden de accounts beschreven die u moet ontwikkelen op Partnercentrum-SDK.</span><span class="sxs-lookup"><span data-stu-id="349d9-105">This article describes the accounts you need to develop against the Partner Center SDK.</span></span> <span data-ttu-id="349d9-106">In dit artikel wordt ook uitgelegd hoe u een [integratie-sandboxaccount maakt en](#integration-sandbox-account) test in de integratie-sandbox.</span><span class="sxs-lookup"><span data-stu-id="349d9-106">This article also explains how to create an [integration sandbox account](#integration-sandbox-account) and test in the integration sandbox.</span></span>

>[!NOTE]
><span data-ttu-id="349d9-107">Als u toegang wilt krijgen tot API's, moet uw tenant een CSP-tenant zijn en moet u een indirecte provider of een directe factuurpartner zijn.</span><span class="sxs-lookup"><span data-stu-id="349d9-107">To get access to APIs, your tenant must be a CSP tenant and you must be either an indirect provider or a Direct bill partner.</span></span>

## <a name="account-definitions"></a><span data-ttu-id="349d9-108">Accountdefinities</span><span class="sxs-lookup"><span data-stu-id="349d9-108">Account definitions</span></span>

<span data-ttu-id="349d9-109">Om u te helpen uw API-integratie te integreren en te testen, Partner Center twee soorten accounts ondersteunen:</span><span class="sxs-lookup"><span data-stu-id="349d9-109">To help you integrate and test your API integration, Partner Center supports two kinds of accounts:</span></span>

### <a name="primary-partner-account"></a><span data-ttu-id="349d9-110">Primaire partneraccount</span><span class="sxs-lookup"><span data-stu-id="349d9-110">Primary Partner account</span></span>

<span data-ttu-id="349d9-111">In dit account maakt u echte orders voor echte klanten.</span><span class="sxs-lookup"><span data-stu-id="349d9-111">This account is where you create real orders for real customers.</span></span> <span data-ttu-id="349d9-112">Als u wijzigingen of transacties aanstelt wanneer u bent aangemeld bij het primaire account, worden deze met behulp van de Partnercentrum-SDK of de gebruikersinterface van het partnerdashboard behandeld als officiële orders voor echte klanten.</span><span class="sxs-lookup"><span data-stu-id="349d9-112">If you make any changes or transactions when you are signed in to the primary account, by using either the Partner Center SDK or the Partner Dashboard UI, they will be treated as official orders for real customers.</span></span> <span data-ttu-id="349d9-113">Ze worden weergegeven in uw factuur en uw bedrijf is verantwoordelijk voor het betalen ervan.</span><span class="sxs-lookup"><span data-stu-id="349d9-113">They will be reflected in your invoice, and your company is responsible for paying for them.</span></span>

### <a name="integration-sandbox-account"></a><span data-ttu-id="349d9-114">Sandboxaccount voor integratie</span><span class="sxs-lookup"><span data-stu-id="349d9-114">Integration sandbox account</span></span>

<span data-ttu-id="349d9-115">Dit account is voor het testen van uw code en de integratie ervan met de Partner Center API's voordat u deze breed implementeert.</span><span class="sxs-lookup"><span data-stu-id="349d9-115">This account is for testing your code and its integration with the Partner Center APIs before you deploy it broadly.</span></span> <span data-ttu-id="349d9-116">Wijzigingen en transacties die u maakt wanneer u bent aangemeld bij het sandbox-account voor integratie worden weergegeven op uw factuur, maar u hoeft het factuurbedrag niet te betalen.</span><span class="sxs-lookup"><span data-stu-id="349d9-116">Changes and transactions you make when you are signed into the integration sandbox account will appear in your invoice, however, you do not have to pay the invoice amount.</span></span> <span data-ttu-id="349d9-117">Factuur pdf heeft een disclaimer als "NIET BETALEN.</span><span class="sxs-lookup"><span data-stu-id="349d9-117">Invoice pdf will have a disclaimer as "DO NOT PAY.</span></span> <span data-ttu-id="349d9-118">DIT IS EEN SANDBOX-FACTUUR EN ER IS GEEN ACTIE VEREIST.</span><span class="sxs-lookup"><span data-stu-id="349d9-118">THIS IS A SANDBOX INVOICE AND NO ACTION IS REQUIRED."</span></span>

<span data-ttu-id="349d9-119">Het sandbox-account voor integratie en het primaire account werken onafhankelijk en delen geen beheerdersaccounts, gebruikersaccounts, klanten, orders, abonnementen of andere gegevens.</span><span class="sxs-lookup"><span data-stu-id="349d9-119">The integration sandbox account and the primary account act independently, and do not share admin accounts, user accounts, customers, orders, subscriptions, or other data.</span></span>

<span data-ttu-id="349d9-120">De integratie-sandbox ondersteunt transacties met een beperkt aantal klanten, orders, abonnementen, licenties, enzovoort.</span><span class="sxs-lookup"><span data-stu-id="349d9-120">The integration sandbox supports transactions with a limited number of customers, orders, subscriptions, licenses, etc.</span></span>

<span data-ttu-id="349d9-121">Op beleid zijn sandbox-accounts voor integratie alleen bedoeld voor testdoeleinden voor integratie.</span><span class="sxs-lookup"><span data-stu-id="349d9-121">By policy, integration sandbox accounts are for integration testing purposes only.</span></span>

<span data-ttu-id="349d9-122">Standaard is er geen sandboxaccount voor integratie.</span><span class="sxs-lookup"><span data-stu-id="349d9-122">By default, there is no integration sandbox account.</span></span> <span data-ttu-id="349d9-123">U moet er zelf een maken als u van plan bent om de Partnercentrum-SDK.</span><span class="sxs-lookup"><span data-stu-id="349d9-123">You must create one yourself if you plan to use the Partner Center SDK.</span></span>

## <a name="set-up-your-accounts"></a><span data-ttu-id="349d9-124">Uw accounts instellen</span><span class="sxs-lookup"><span data-stu-id="349d9-124">Set up your accounts</span></span>

<span data-ttu-id="349d9-125">In deze sectie wordt beschreven hoe u een primair partneraccount en een sandbox-account voor integratie voor de Partnercentrum-SDK.</span><span class="sxs-lookup"><span data-stu-id="349d9-125">This section describes how to set up a primary Partner account and an integration sandbox account for the Partner Center SDK.</span></span>

### <a name="create-an-integration-sandbox"></a><span data-ttu-id="349d9-126">Een integratie-sandbox maken</span><span class="sxs-lookup"><span data-stu-id="349d9-126">Create an integration sandbox</span></span>

1. <span data-ttu-id="349d9-127">Meld u aan bij het partnerdashboard met een globale beheerdersaccount (uw primaire partneraccount).</span><span class="sxs-lookup"><span data-stu-id="349d9-127">Sign in to Partner Dashboard with a global admin account (your primary Partner account.)</span></span>

2. <span data-ttu-id="349d9-128">Kies in **Instellingen** menu (tandwielpictogram) **partnerinstellingen.**</span><span class="sxs-lookup"><span data-stu-id="349d9-128">From the **Settings** menu (gear icon), choose **Partner settings**.</span></span>

3. <span data-ttu-id="349d9-129">Kies het **tabblad Integratie-sandbox.**</span><span class="sxs-lookup"><span data-stu-id="349d9-129">Choose **Integration sandbox** tab.</span></span>

    >[!NOTE]
    ><span data-ttu-id="349d9-130">Als u de optie Integratie-sandbox niet ziet, hebt u mogelijk geen algemeen beheerdersaccount.</span><span class="sxs-lookup"><span data-stu-id="349d9-130">If you don't see an Integration sandbox option, you might not have a global admin account.</span></span> <span data-ttu-id="349d9-131">Mogelijk gebruikt u ook een sandbox-account voor integratie en is er al een integratie-sandbox ingesteld.</span><span class="sxs-lookup"><span data-stu-id="349d9-131">You also might be using an integration sandbox account and an integration sandbox has already been set up.</span></span>

4. <span data-ttu-id="349d9-132">Voer de contactgegevens in voor het beheerdersaccount voor de integratie-sandbox.</span><span class="sxs-lookup"><span data-stu-id="349d9-132">Enter the contact information for the integration sandbox admin account.</span></span> <span data-ttu-id="349d9-133">Kies vervolgens **Account maken.**</span><span class="sxs-lookup"><span data-stu-id="349d9-133">Then, choose **Create account**.</span></span> <span data-ttu-id="349d9-134">Wacht enkele minuten tot er een bevestigingsbericht wordt weergegeven dat het account is gemaakt.</span><span class="sxs-lookup"><span data-stu-id="349d9-134">Wait a few minutes for a confirmation message that the account has been created.</span></span>

5. <span data-ttu-id="349d9-135">Nadat u het bevestigingsbericht hebt weergegeven, meld u zich af bij partnerdashboard.</span><span class="sxs-lookup"><span data-stu-id="349d9-135">After you see the confirmation message, sign out of Partner Dashboard.</span></span>

6. <span data-ttu-id="349d9-136">Meld u weer aan met uw nieuwe sandbox-beheerdersaccount voor integratie.</span><span class="sxs-lookup"><span data-stu-id="349d9-136">Sign back in with your new integration sandbox admin account.</span></span> <span data-ttu-id="349d9-137">Zorg ervoor dat u de indeling voor uw referenties gebruikt, samen **username@domain** met het wachtwoord dat u hebt opgegeven.</span><span class="sxs-lookup"><span data-stu-id="349d9-137">Be sure to use the format **username@domain** for your credentials along with the password that you specified.</span></span>

7. <span data-ttu-id="349d9-138">Kies **Account instellen boven** Huidige taken **om** de installatie van het sandbox-account te voltooien.</span><span class="sxs-lookup"><span data-stu-id="349d9-138">Choose **Set Up Account** above **Current Tasks** to complete the sandbox account setup.</span></span>

### <a name="enable-api-access"></a><span data-ttu-id="349d9-139">API-toegang inschakelen</span><span class="sxs-lookup"><span data-stu-id="349d9-139">Enable API access</span></span>

<span data-ttu-id="349d9-140">Nadat uw account is ingesteld, moet u API-toegang inschakelen voordat u de Partnercentrum-SDK kunt gebruiken met de sandbox voor integratie.</span><span class="sxs-lookup"><span data-stu-id="349d9-140">After your account is set up, you must enable API access before you can use the Partner Center SDK with the integration sandbox.</span></span> <span data-ttu-id="349d9-141">U moet de toegang tot de API afzonderlijk inschakelen voor zowel uw primaire partneraccount als uw sandboxaccount voor integratie.</span><span class="sxs-lookup"><span data-stu-id="349d9-141">You need to enable access to the API separately for both your primary Partner account and your integration sandbox account.</span></span>

1. <span data-ttu-id="349d9-142">Meld u aan bij partnerdashboard met een account voor globale beheerders.</span><span class="sxs-lookup"><span data-stu-id="349d9-142">Sign into Partner Dashboard using a global admin account.</span></span>

2. <span data-ttu-id="349d9-143">Selecteer in **Instellingen** menu (tandwielpictogram) **partnerinstellingen.**</span><span class="sxs-lookup"><span data-stu-id="349d9-143">From the **Settings** menu (gear icon), select **Partner settings**.</span></span>

3. <span data-ttu-id="349d9-144">Kies op **de pagina Accountinstellingen** de optie **App-beheer.**</span><span class="sxs-lookup"><span data-stu-id="349d9-144">On the **Account settings** page, choose **App management**.</span></span>

4. <span data-ttu-id="349d9-145">Als u nog geen bestaande app hebt, voegt u een nieuwe web-app toe.</span><span class="sxs-lookup"><span data-stu-id="349d9-145">If you do not already have an existing app, add a new web app.</span></span> <span data-ttu-id="349d9-146">Als u een bestaande web-app hebt, kiest u de **knop Sleutel** toevoegen.</span><span class="sxs-lookup"><span data-stu-id="349d9-146">If you have an existing web app, choose the **Add key** button.</span></span>

5. <span data-ttu-id="349d9-147">Kopieer de app-registratiegegevens, met name **de** Sleutel als u een web-app maakt, en sla deze op een veilige plaats op.</span><span class="sxs-lookup"><span data-stu-id="349d9-147">Copy the app registration information, especially the **Key** if you're creating a web app, and store it in a safe place.</span></span>

6. <span data-ttu-id="349d9-148">Meld u af bij partnerdashboard.</span><span class="sxs-lookup"><span data-stu-id="349d9-148">Sign out of Partner Dashboard.</span></span>

7. <span data-ttu-id="349d9-149">Meld u weer aan met uw sandbox-account voor integratie.</span><span class="sxs-lookup"><span data-stu-id="349d9-149">Sign back in with your integration sandbox account.</span></span> <span data-ttu-id="349d9-150">Herhaal stap 2-5 om API-toegang in teschakelen in de integratie-sandbox.</span><span class="sxs-lookup"><span data-stu-id="349d9-150">Repeat steps 2-5 to enable API access in the integration sandbox.</span></span>

## <a name="write-and-test-code"></a><span data-ttu-id="349d9-151">Code schrijven en testen</span><span class="sxs-lookup"><span data-stu-id="349d9-151">Write and test code</span></span>

<span data-ttu-id="349d9-152">U kunt code schrijven en code testen in de integratie-sandbox.</span><span class="sxs-lookup"><span data-stu-id="349d9-152">You can write code and test code in the integration sandbox.</span></span> <span data-ttu-id="349d9-153">U hebt de volgende informatie nodig om de [verificatie Partner Center](partner-center-authentication.md) Azure AD in te stellen.</span><span class="sxs-lookup"><span data-stu-id="349d9-153">You'll need the following information to [set up Partner Center authentication](partner-center-authentication.md) with Azure AD.</span></span>

| <span data-ttu-id="349d9-154">Itemnaam</span><span class="sxs-lookup"><span data-stu-id="349d9-154">Item name</span></span> | <span data-ttu-id="349d9-155">Itemlocatie</span><span class="sxs-lookup"><span data-stu-id="349d9-155">Item location</span></span> |
| --------- | ------------- |
| <span data-ttu-id="349d9-156">App-id/client-id</span><span class="sxs-lookup"><span data-stu-id="349d9-156">App ID / Client ID</span></span> | <span data-ttu-id="349d9-157">Selecteer in **Instellingen** menu (tandwielpictogram) **partnerinstellingen.**</span><span class="sxs-lookup"><span data-stu-id="349d9-157">From the **Settings** menu (gear icon), select **Partner settings**.</span></span> <span data-ttu-id="349d9-158">Selecteer **app-beheer** op de pagina **Accountinstellingen.**</span><span class="sxs-lookup"><span data-stu-id="349d9-158">On the **Account settings** page, select **App Management**.</span></span> <span data-ttu-id="349d9-159">De app-id/client-id wordt vermeld als de geregistreerde **toepassings-app-id.**</span><span class="sxs-lookup"><span data-stu-id="349d9-159">The App ID/Client ID is listed as the **Registered application App ID**.</span></span> |
| <span data-ttu-id="349d9-160">Sleutel</span><span class="sxs-lookup"><span data-stu-id="349d9-160">Key</span></span> | <span data-ttu-id="349d9-161">Als u een web-app hebt gemaakt in de sectie [API-toegang inschakelen,](#enable-api-access)is dit de sleutel die u in stap 5 hebt opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="349d9-161">If you created a web app in the section [Enable API access](#enable-api-access), this is the key that you saved in step 5.</span></span> |
| <span data-ttu-id="349d9-162">Domain</span><span class="sxs-lookup"><span data-stu-id="349d9-162">Domain</span></span> | <span data-ttu-id="349d9-163">Het domein voor de integratie-sandbox.</span><span class="sxs-lookup"><span data-stu-id="349d9-163">The domain for the integration sandbox.</span></span> |

## <a name="run-tested-code"></a><span data-ttu-id="349d9-164">Geteste code uitvoeren</span><span class="sxs-lookup"><span data-stu-id="349d9-164">Run tested code</span></span>

<span data-ttu-id="349d9-165">Als u uw oplossing wilt gebruiken met echte klantgegevens, moet u de referenties voor uw integratiesandbox wijzigen in de referenties van uw primaire partneraccount.</span><span class="sxs-lookup"><span data-stu-id="349d9-165">To use your solution with real customer data, you must change from your integration sandbox credentials to your primary Partner account credentials.</span></span>

<span data-ttu-id="349d9-166">Wanneer u klaar bent om de geteste code te gebruiken in uw primaire Partner-account, moet u een Azure AD-beveiliging token krijgen.</span><span class="sxs-lookup"><span data-stu-id="349d9-166">When you're ready to use your tested code in your primary Partner account, you must get an Azure AD security token.</span></span> <span data-ttu-id="349d9-167">Dit beveiliging token is gebaseerd op uw Partner Center app, sleutel en domein (in plaats van uw sandbox-app, sleutel en domein voor integratie).</span><span class="sxs-lookup"><span data-stu-id="349d9-167">This security token is based on your Partner Center app, key, and domain (instead of your integration sandbox app, key, and domain).</span></span>

1. <span data-ttu-id="349d9-168">Volg de stappen in [verificatie Partner Center om](partner-center-authentication.md) een Azure AD-beveiliging token op te halen met behulp van uw primaire Partner Center referenties.</span><span class="sxs-lookup"><span data-stu-id="349d9-168">Follow the steps in [Partner Center authentication](partner-center-authentication.md) to get an Azure AD security token using your primary Partner Center credentials.</span></span> <span data-ttu-id="349d9-169">(U hebt eerder deze stappen uitgevoerd om een Azure AD-beveiliging token voor uw integratie-sandbox op te halen.)</span><span class="sxs-lookup"><span data-stu-id="349d9-169">(You previously followed these steps to get an Azure AD security token for your integration sandbox.)</span></span>

2. <span data-ttu-id="349d9-170">Vervang het beveiliging token voor integratie in uw code door het nieuwe beveiliging token voor uw primaire Partner-account.</span><span class="sxs-lookup"><span data-stu-id="349d9-170">Replace the integration security token in your code with the new security token for your primary Partner account.</span></span>
