---
title: App-gegevens registreren voor Partner Center voor micro soft National Cloud
description: Meer informatie over hoe en waarom app-ontwikkel aars voor partner centrum voor micro soft National Cloud details moeten registreren over hun app met Azure AD via de Azure Portal.
MS-HAID:
- pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_cloud\_germany
- pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_national\_clouds
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 887cb71c752ac5d9c61398536711545c19cc7600
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767642"
---
# <a name="register-app-details-for-partner-center-for-microsoft-national-cloud-through-the-azure-portal"></a><span data-ttu-id="66ad8-103">Registreer app-gegevens voor het partner centrum voor micro soft National Cloud via de Azure Portal</span><span class="sxs-lookup"><span data-stu-id="66ad8-103">Register app details for Partner Center for Microsoft National Cloud through the Azure portal</span></span>

<span data-ttu-id="66ad8-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="66ad8-104">**Applies to:**</span></span>

- <span data-ttu-id="66ad8-105">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="66ad8-105">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="66ad8-106">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="66ad8-106">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="66ad8-107">Ontwikkel aars moeten gegevens over hun app met Azure AD registreren via de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="66ad8-107">Developers must register details about their app with Azure AD through the Azure portal.</span></span> <span data-ttu-id="66ad8-108">Dit helpt ervoor te zorgen dat alleen opgegeven apps verbinding kunnen maken met de partner-en klant gegevens.</span><span class="sxs-lookup"><span data-stu-id="66ad8-108">This helps ensure that only specified apps are able to connect to partner and customer data.</span></span>

<span data-ttu-id="66ad8-109">Voor het partner centrum voor Microsoft Cloud voor de Amerikaanse overheid moet u momenteel apps beheren via Power shell.</span><span class="sxs-lookup"><span data-stu-id="66ad8-109">For Partner Center for Microsoft Cloud for US Government, you currently must manage apps through PowerShell.</span></span> <span data-ttu-id="66ad8-110">Zie de [documentatie over Azure PowerShell](/powershell/module/Azuread/#applications)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="66ad8-110">For more information, see the [Azure PowerShell reference documentation](/powershell/module/Azuread/#applications).</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="66ad8-111">Houd rekening met de volgende aanvullende vereisten wanneer u een app maakt voor partner centrum voor Microsoft Cloud Duitsland of partner centrum voor Microsoft Cloud voor de Amerikaanse overheid.</span><span class="sxs-lookup"><span data-stu-id="66ad8-111">Be aware of the following additional requirements when you create an app for Partner Center for Microsoft Cloud Germany or Partner Center for Microsoft Cloud for US Government.</span></span>

## <a name="web-apps"></a><span data-ttu-id="66ad8-112">Web-apps</span><span class="sxs-lookup"><span data-stu-id="66ad8-112">Web apps</span></span>

<span data-ttu-id="66ad8-113">Gebruik voor web-apps de volgende procedures om uw toepassings-ID te registreren.</span><span class="sxs-lookup"><span data-stu-id="66ad8-113">For web apps, use the following procedures to register your application ID.</span></span>

### <a name="create-or-update-web-app"></a><span data-ttu-id="66ad8-114">Een web-app maken of bijwerken</span><span class="sxs-lookup"><span data-stu-id="66ad8-114">Create or update web app</span></span>

1. <span data-ttu-id="66ad8-115">Ga naar de pagina [Azure Portal-app-registraties](https://go.microsoft.com/fwlink/?linkid=2083908) om uw app te registreren.</span><span class="sxs-lookup"><span data-stu-id="66ad8-115">Navigate to the [Azure portal - App registrations](https://go.microsoft.com/fwlink/?linkid=2083908) page to register your app.</span></span> <span data-ttu-id="66ad8-116">Meld u aan bij de Azure Portal met behulp van een werk-of school account of een persoonlijke Microsoft-account.</span><span class="sxs-lookup"><span data-stu-id="66ad8-116">Sign in to the Azure portal using either a work or school account or a personal Microsoft account.</span></span>

2. <span data-ttu-id="66ad8-117">Selecteer **Nieuwe registratie**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-117">Select **New registration**.</span></span> <span data-ttu-id="66ad8-118">Zie [Quick Start: een toepassing registreren bij het micro soft Identity-platform](/azure/active-directory/develop/quickstart-register-app)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="66ad8-118">For more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).</span></span>

### <a name="configure-api-access-permissions-for-web-app"></a><span data-ttu-id="66ad8-119">API-toegangs machtigingen voor web-app configureren</span><span class="sxs-lookup"><span data-stu-id="66ad8-119">Configure API access permissions for web app</span></span>

1. <span data-ttu-id="66ad8-120">Kies uw app.</span><span class="sxs-lookup"><span data-stu-id="66ad8-120">Choose your app.</span></span> <span data-ttu-id="66ad8-121">Ga naar de **instellingen** van de web-app.</span><span class="sxs-lookup"><span data-stu-id="66ad8-121">Go to **Settings** of the Web app.</span></span>

2. <span data-ttu-id="66ad8-122">Kies in het gedeelte **API-toegang** de optie **vereiste machtigingen**</span><span class="sxs-lookup"><span data-stu-id="66ad8-122">In **API Access** section, choose **Required permissions**</span></span>

3. <span data-ttu-id="66ad8-123">Voor Windows Azure Active Directory-machtigingen:</span><span class="sxs-lookup"><span data-stu-id="66ad8-123">For Windows Azure Active directory permissions:</span></span>

    1. <span data-ttu-id="66ad8-124">Kies **Windows-Azure Active Directory machtigingen**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-124">Choose **Windows Azure Active Directory permissions**.</span></span>

    2. <span data-ttu-id="66ad8-125">Selecteer in **toepassings machtigingen** de optie Directory gegevens lezen.</span><span class="sxs-lookup"><span data-stu-id="66ad8-125">In **Applications permissions**, select Read directory data.</span></span>

    3. <span data-ttu-id="66ad8-126">Sla de machtigingen op.</span><span class="sxs-lookup"><span data-stu-id="66ad8-126">Save the permissions.</span></span>

4. <span data-ttu-id="66ad8-127">Noteer de toepassings-ID in het gedeelte **Eigenschappen** van uw web-app.</span><span class="sxs-lookup"><span data-stu-id="66ad8-127">Note the application ID in the **Properties** section of your web app.</span></span>

### <a name="add-a-secret-key-to-your-app"></a><span data-ttu-id="66ad8-128">Een geheime sleutel toevoegen aan uw app</span><span class="sxs-lookup"><span data-stu-id="66ad8-128">Add a secret key to your app</span></span>

1. <span data-ttu-id="66ad8-129">Ga naar de sectie **sleutels** van uw web-app.</span><span class="sxs-lookup"><span data-stu-id="66ad8-129">Go to the **Keys** section of your web app.</span></span>

2. <span data-ttu-id="66ad8-130">Voer de sleutel beschrijving in en selecteer duur als 1 of 2 jaar, zoals u wilt.</span><span class="sxs-lookup"><span data-stu-id="66ad8-130">Enter key description and select duration as 1 or 2 years, as you need.</span></span>

3. <span data-ttu-id="66ad8-131">Sla de waarde van de geheime sleutel op en kopieer deze.</span><span class="sxs-lookup"><span data-stu-id="66ad8-131">Save and copy the secret key value.</span></span> <span data-ttu-id="66ad8-132">**Deze waarde wordt niet weer gegeven wanneer u deze pagina verlaat.**</span><span class="sxs-lookup"><span data-stu-id="66ad8-132">**This value will not be shown again once you leave this page.**</span></span>

<span data-ttu-id="66ad8-133">U moet de volgende details van de web-app configureren:</span><span class="sxs-lookup"><span data-stu-id="66ad8-133">You should have the following details from the web app configuration:</span></span>

- <span data-ttu-id="66ad8-134">Toepassings-id</span><span class="sxs-lookup"><span data-stu-id="66ad8-134">Application ID</span></span>
- <span data-ttu-id="66ad8-135">Toepassingsgeheim</span><span class="sxs-lookup"><span data-stu-id="66ad8-135">Application secret</span></span>

### <a name="register-the-web-app-in-partner-center"></a><span data-ttu-id="66ad8-136">De web-app registreren in het partner centrum</span><span class="sxs-lookup"><span data-stu-id="66ad8-136">Register the Web app in Partner Center</span></span>

1. <span data-ttu-id="66ad8-137">Meld u aan bij [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com) .</span><span class="sxs-lookup"><span data-stu-id="66ad8-137">Log in to [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com).</span></span>

2. <span data-ttu-id="66ad8-138">Kies **dash board**, kies **account instellingen** en kies vervolgens **app-beheer**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-138">Choose **Dashboard**, then choose **Account Settings**, then choose **App Management**.</span></span>

3. <span data-ttu-id="66ad8-139">Kies **bestaande app registreren** in het gedeelte **Web-app** .</span><span class="sxs-lookup"><span data-stu-id="66ad8-139">In the **Web App** section, choose **Register existing app**.</span></span>

4. <span data-ttu-id="66ad8-140">Selecteer de web-app die u hebt gemaakt in Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="66ad8-140">Select the web app you created in Azure portal.</span></span>

5. <span data-ttu-id="66ad8-141">Kies **uw app registreren**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-141">Choose **register your app**.</span></span>

## <a name="native-apps"></a><span data-ttu-id="66ad8-142">Systeemeigen apps</span><span class="sxs-lookup"><span data-stu-id="66ad8-142">Native apps</span></span>

<span data-ttu-id="66ad8-143">Systeem eigen apps hoeven niet te worden geregistreerd bij het partner centrum.</span><span class="sxs-lookup"><span data-stu-id="66ad8-143">Native apps do not need to be registered to Partner Center.</span></span> <span data-ttu-id="66ad8-144">Maar deze apps moeten worden geconfigureerd om toegang te bieden tot partner Center-Api's.</span><span class="sxs-lookup"><span data-stu-id="66ad8-144">But these apps need to be configured to provide access to Partner Center APIs.</span></span>

>[!NOTE]
><span data-ttu-id="66ad8-145">Voordat u een systeem eigen app maakt in de Azure Portal, meldt u zich aan bij Partner Center met behulp van de gebruikers referenties van de beheerder van de partner-Tenant.</span><span class="sxs-lookup"><span data-stu-id="66ad8-145">Before creating a native app in the Azure portal, log in into Partner Center using the admin user credentials from the partner tenant.</span></span> <span data-ttu-id="66ad8-146">Hiermee maakt u de instellingen op de Tenant om app-machtigingen in te scha kelen.</span><span class="sxs-lookup"><span data-stu-id="66ad8-146">This creates the settings on the tenant to enable app permissions.</span></span>

### <a name="create-native-app"></a><span data-ttu-id="66ad8-147">Systeem eigen app maken</span><span class="sxs-lookup"><span data-stu-id="66ad8-147">Create native app</span></span>

1. <span data-ttu-id="66ad8-148">Ga naar de pagina [Azure Portal-app-registraties](https://go.microsoft.com/fwlink/?linkid=2083908) om uw app te registreren.</span><span class="sxs-lookup"><span data-stu-id="66ad8-148">Navigate to the [Azure portal - App registrations](https://go.microsoft.com/fwlink/?linkid=2083908) page to register your app.</span></span> <span data-ttu-id="66ad8-149">Meld u aan bij de Azure Portal met behulp van een werk-of school account of een persoonlijke Microsoft-account.</span><span class="sxs-lookup"><span data-stu-id="66ad8-149">Sign in to the Azure portal using either a work or school account or a personal Microsoft account.</span></span>

2. <span data-ttu-id="66ad8-150">Selecteer **Nieuwe registratie**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-150">Select **New registration**.</span></span> <span data-ttu-id="66ad8-151">Zie [Quick Start: een toepassing registreren bij het micro soft Identity-platform](/azure/active-directory/develop/quickstart-register-app)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="66ad8-151">For more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).</span></span>

### <a name="configure-api-access-permissions-for-native-app"></a><span data-ttu-id="66ad8-152">API-toegangs machtigingen voor systeem eigen app configureren</span><span class="sxs-lookup"><span data-stu-id="66ad8-152">Configure API access permissions for native app</span></span>

1. <span data-ttu-id="66ad8-153">Kies uw app.</span><span class="sxs-lookup"><span data-stu-id="66ad8-153">Choose your app.</span></span> <span data-ttu-id="66ad8-154">Ga naar **Settings**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-154">Go to **Settings**.</span></span>

2. <span data-ttu-id="66ad8-155">Kies in API-toegang de optie **vereiste machtigingen**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-155">In API Access, choose **Required permissions**.</span></span>

3. <span data-ttu-id="66ad8-156">Kies **Windows-Azure Active Directory machtigingen**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-156">Choose **Windows Azure Active Directory permissions**.</span></span> <span data-ttu-id="66ad8-157">Selecteer in **gedelegeerde machtigingen** de volgende machtigingen:</span><span class="sxs-lookup"><span data-stu-id="66ad8-157">In **Delegated permissions**, select these permissions:</span></span>

    - <span data-ttu-id="66ad8-158">**Aanmelden en gebruikersprofiel lezen**</span><span class="sxs-lookup"><span data-stu-id="66ad8-158">**Sign in and read user profile**</span></span>
    - <span data-ttu-id="66ad8-159">**Mapgegevens lezen**</span><span class="sxs-lookup"><span data-stu-id="66ad8-159">**Read directory data**</span></span>
    - <span data-ttu-id="66ad8-160">**Toegang tot de map als de aangemelde gebruiker**</span><span class="sxs-lookup"><span data-stu-id="66ad8-160">**Access the directory as the signed-in user**</span></span>
    - <span data-ttu-id="66ad8-161">**Alle groepen lezen**</span><span class="sxs-lookup"><span data-stu-id="66ad8-161">**Read all groups**</span></span>

4. <span data-ttu-id="66ad8-162">Sla de machtigingen op.</span><span class="sxs-lookup"><span data-stu-id="66ad8-162">Save the permissions.</span></span>

5. <span data-ttu-id="66ad8-163">Kies **toevoegen** in **vereiste machtigingen**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-163">Choose **Add** in **Required permissions**.</span></span>

6. <span data-ttu-id="66ad8-164">Kies **Een API selecteren**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-164">Choose **Select an API**.</span></span>

    1. <span data-ttu-id="66ad8-165">Voer in het zoekvak **micro soft Partner Center** in en selecteer het in de lijst met resultaten.</span><span class="sxs-lookup"><span data-stu-id="66ad8-165">In the search box, enter **Microsoft Partner Center** and select it from the results list.</span></span>

    2. <span data-ttu-id="66ad8-166">Kies **Selecteren**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-166">Choose **Select**.</span></span>

7. <span data-ttu-id="66ad8-167">Kies **Machtigingen selecteren**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-167">Choose **Select permissions**.</span></span>

    1. <span data-ttu-id="66ad8-168">Selecteer **toegang tot het beschermings partner centrum**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-168">Select **Access Partner Center PPE**.</span></span>
    
    2. <span data-ttu-id="66ad8-169">Kies **Selecteren**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-169">Choose **Select**.</span></span>

8. <span data-ttu-id="66ad8-170">Kies **Gereed**.</span><span class="sxs-lookup"><span data-stu-id="66ad8-170">Choose **Done**.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="66ad8-171">Noteer de toepassings-ID in de eigenschappen van uw app.</span><span class="sxs-lookup"><span data-stu-id="66ad8-171">Note the application ID in the Properties of your app.</span></span>

<span data-ttu-id="66ad8-172">U hoeft geen systeem eigen apps te registreren in het partner centrum, maar de systeem eigen app moet zijn gestemd met de beheerder.</span><span class="sxs-lookup"><span data-stu-id="66ad8-172">You do not need to register native apps in Partner Center, however the native app must be admin consented .</span></span> <span data-ttu-id="66ad8-173">Noteer de toepassings-ID van uw systeem eigen app.</span><span class="sxs-lookup"><span data-stu-id="66ad8-173">Note the application ID of your native app.</span></span>
