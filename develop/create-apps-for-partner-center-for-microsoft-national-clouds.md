---
title: App-gegevens registreren voor Partner Center voor Microsoft National Cloud
description: Ontdek hoe en waarom app-ontwikkelaars voor Partner Center for Microsoft National Cloud details over hun app moeten registreren bij Azure AD via de Azure Portal.
MS-HAID:
- pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_cloud\_germany
- pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_national\_clouds
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 93d46a17bc26e9586e5e773bdf934653a571367f
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973448"
---
# <a name="register-app-details-for-partner-center-for-microsoft-national-cloud-through-the-azure-portal"></a><span data-ttu-id="8fd6c-103">App-gegevens voor Partner Center voor Microsoft National Cloud registreren via de Azure Portal</span><span class="sxs-lookup"><span data-stu-id="8fd6c-103">Register app details for Partner Center for Microsoft National Cloud through the Azure portal</span></span>

<span data-ttu-id="8fd6c-104">**Van toepassing op**: Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="8fd6c-104">**Applies to**: Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="8fd6c-105">Ontwikkelaars moeten details over hun app registreren bij Azure AD via de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-105">Developers must register details about their app with Azure AD through the Azure portal.</span></span> <span data-ttu-id="8fd6c-106">Dit zorgt ervoor dat alleen opgegeven apps verbinding kunnen maken met partner- en klantgegevens.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-106">This helps ensure that only specified apps are able to connect to partner and customer data.</span></span>

<span data-ttu-id="8fd6c-107">Voor Partner Center voor Microsoft Cloud for US Government moet u momenteel apps beheren via PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-107">For Partner Center for Microsoft Cloud for US Government, you currently must manage apps through PowerShell.</span></span> <span data-ttu-id="8fd6c-108">Zie de referentiedocumentatie Azure PowerShell [meer informatie.](/powershell/module/Azuread/#applications)</span><span class="sxs-lookup"><span data-stu-id="8fd6c-108">For more information, see the [Azure PowerShell reference documentation](/powershell/module/Azuread/#applications).</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="8fd6c-109">Let op de volgende aanvullende vereisten wanneer u een app maakt voor Partner Center voor Microsoft Cloud Duitsland of wanneer Partner Center voor Microsoft Cloud for US Government.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-109">Be aware of the following additional requirements when you create an app for Partner Center for Microsoft Cloud Germany or Partner Center for Microsoft Cloud for US Government.</span></span>

## <a name="web-apps"></a><span data-ttu-id="8fd6c-110">Web-apps</span><span class="sxs-lookup"><span data-stu-id="8fd6c-110">Web apps</span></span>

<span data-ttu-id="8fd6c-111">Gebruik voor web-apps de volgende procedures om uw toepassings-id te registreren.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-111">For web apps, use the following procedures to register your application ID.</span></span>

### <a name="create-or-update-web-app"></a><span data-ttu-id="8fd6c-112">Web-app maken of bijwerken</span><span class="sxs-lookup"><span data-stu-id="8fd6c-112">Create or update web app</span></span>

1. <span data-ttu-id="8fd6c-113">Navigeer [naar Azure Portal - App-registraties](https://go.microsoft.com/fwlink/?linkid=2083908) om uw app te registreren.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-113">Navigate to the [Azure portal - App registrations](https://go.microsoft.com/fwlink/?linkid=2083908) page to register your app.</span></span> <span data-ttu-id="8fd6c-114">Meld u aan bij Azure Portal met een werk- of schoolaccount of een persoonlijk Microsoft-account.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-114">Sign in to the Azure portal using either a work or school account or a personal Microsoft account.</span></span>

2. <span data-ttu-id="8fd6c-115">Selecteer **Nieuwe registratie**.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-115">Select **New registration**.</span></span> <span data-ttu-id="8fd6c-116">Zie Snelstart: Een toepassing registreren met de Microsoft identity platform voor [meer Microsoft identity platform.](/azure/active-directory/develop/quickstart-register-app)</span><span class="sxs-lookup"><span data-stu-id="8fd6c-116">For more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).</span></span>

### <a name="configure-api-access-permissions-for-web-app"></a><span data-ttu-id="8fd6c-117">API-toegangsmachtigingen voor web-app configureren</span><span class="sxs-lookup"><span data-stu-id="8fd6c-117">Configure API access permissions for web app</span></span>

1. <span data-ttu-id="8fd6c-118">Kies uw app.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-118">Choose your app.</span></span> <span data-ttu-id="8fd6c-119">Ga naar **Instellingen** van de web-app.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-119">Go to **Settings** of the Web app.</span></span>

2. <span data-ttu-id="8fd6c-120">Kies **in de sectie API-toegang** de optie Vereiste **machtigingen**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-120">In **API Access** section, choose **Required permissions**</span></span>

3. <span data-ttu-id="8fd6c-121">Voor Windows Machtigingen voor Azure Active Directory:</span><span class="sxs-lookup"><span data-stu-id="8fd6c-121">For Windows Azure Active directory permissions:</span></span>

    1. <span data-ttu-id="8fd6c-122">Kies **Windows Azure Active Directory machtigingen**.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-122">Choose **Windows Azure Active Directory permissions**.</span></span>

    2. <span data-ttu-id="8fd6c-123">Selecteer **in Toepassingsmachtigingen** de optie Mapgegevens lezen.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-123">In **Applications permissions**, select Read directory data.</span></span>

    3. <span data-ttu-id="8fd6c-124">Sla de machtigingen op.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-124">Save the permissions.</span></span>

4. <span data-ttu-id="8fd6c-125">Noteer de toepassings-id in **de sectie** Eigenschappen van uw web-app.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-125">Note the application ID in the **Properties** section of your web app.</span></span>

### <a name="add-a-secret-key-to-your-app"></a><span data-ttu-id="8fd6c-126">Een geheime sleutel toevoegen aan uw app</span><span class="sxs-lookup"><span data-stu-id="8fd6c-126">Add a secret key to your app</span></span>

1. <span data-ttu-id="8fd6c-127">Ga naar de **sectie Sleutels** van uw web-app.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-127">Go to the **Keys** section of your web app.</span></span>

2. <span data-ttu-id="8fd6c-128">Voer een sleutelbeschrijving in en selecteer de duur als 1 of 2 jaar, zoals u dat nodig hebt.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-128">Enter key description and select duration as 1 or 2 years, as you need.</span></span>

3. <span data-ttu-id="8fd6c-129">Sla de geheime sleutelwaarde op en kopieer deze.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-129">Save and copy the secret key value.</span></span> <span data-ttu-id="8fd6c-130">**Deze waarde wordt niet meer weergegeven wanneer u deze pagina verlaat.**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-130">**This value will not be shown again once you leave this page.**</span></span>

<span data-ttu-id="8fd6c-131">U moet de volgende gegevens uit de configuratie van de web-app hebben:</span><span class="sxs-lookup"><span data-stu-id="8fd6c-131">You should have the following details from the web app configuration:</span></span>

- <span data-ttu-id="8fd6c-132">Toepassings-id</span><span class="sxs-lookup"><span data-stu-id="8fd6c-132">Application ID</span></span>
- <span data-ttu-id="8fd6c-133">Toepassingsgeheim</span><span class="sxs-lookup"><span data-stu-id="8fd6c-133">Application secret</span></span>

### <a name="register-the-web-app-in-partner-center"></a><span data-ttu-id="8fd6c-134">De web-app registreren in Partner Center</span><span class="sxs-lookup"><span data-stu-id="8fd6c-134">Register the Web app in Partner Center</span></span>

1. <span data-ttu-id="8fd6c-135">Meld u aan bij [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com).</span><span class="sxs-lookup"><span data-stu-id="8fd6c-135">Sign in to [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com).</span></span>

2. <span data-ttu-id="8fd6c-136">Kies **Dashboard,** kies vervolgens **Account Instellingen** en kies vervolgens App **Management.**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-136">Choose **Dashboard**, then choose **Account Settings**, then choose **App Management**.</span></span>

3. <span data-ttu-id="8fd6c-137">Kies in **de sectie Web-app** **de optie Bestaande app registreren.**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-137">In the **Web App** section, choose **Register existing app**.</span></span>

4. <span data-ttu-id="8fd6c-138">Selecteer de web-app die u in de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-138">Select the web app you created in Azure portal.</span></span>

5. <span data-ttu-id="8fd6c-139">Kies **uw app registreren.**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-139">Choose **register your app**.</span></span>

## <a name="native-apps"></a><span data-ttu-id="8fd6c-140">Systeemeigen apps</span><span class="sxs-lookup"><span data-stu-id="8fd6c-140">Native apps</span></span>

<span data-ttu-id="8fd6c-141">Native apps hoeven niet te worden geregistreerd bij Partner Center.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-141">Native apps do not need to be registered to Partner Center.</span></span> <span data-ttu-id="8fd6c-142">Deze apps moeten echter worden geconfigureerd om toegang te bieden tot Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-142">But these apps need to be configured to provide access to Partner Center APIs.</span></span>

>[!NOTE]
><span data-ttu-id="8fd6c-143">Voordat u een systeemeigen app in de Azure Portal, moet u zich aanmelden bij Partner Center met de gebruikersreferenties van de beheerder van de partnerten tenant.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-143">Before creating a native app in the Azure portal, log in into Partner Center using the admin user credentials from the partner tenant.</span></span> <span data-ttu-id="8fd6c-144">Hiermee maakt u de instellingen op de tenant om app-machtigingen in te kunnenschakelen.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-144">This creates the settings on the tenant to enable app permissions.</span></span>

### <a name="create-native-app"></a><span data-ttu-id="8fd6c-145">Een native app maken</span><span class="sxs-lookup"><span data-stu-id="8fd6c-145">Create native app</span></span>

1. <span data-ttu-id="8fd6c-146">Navigeer [naar Azure Portal - App-registraties](https://go.microsoft.com/fwlink/?linkid=2083908) om uw app te registreren.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-146">Navigate to the [Azure portal - App registrations](https://go.microsoft.com/fwlink/?linkid=2083908) page to register your app.</span></span> <span data-ttu-id="8fd6c-147">Meld u aan bij Azure Portal met een werk- of schoolaccount of een persoonlijk Microsoft-account.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-147">Sign in to the Azure portal using either a work or school account or a personal Microsoft account.</span></span>

2. <span data-ttu-id="8fd6c-148">Selecteer **Nieuwe registratie**.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-148">Select **New registration**.</span></span> <span data-ttu-id="8fd6c-149">Zie Snelstart: Een toepassing registreren met de Microsoft identity platform voor [meer Microsoft identity platform.](/azure/active-directory/develop/quickstart-register-app)</span><span class="sxs-lookup"><span data-stu-id="8fd6c-149">For more information, see [Quickstart: Register an application with the Microsoft identity platform](/azure/active-directory/develop/quickstart-register-app).</span></span>

### <a name="configure-api-access-permissions-for-native-app"></a><span data-ttu-id="8fd6c-150">API-toegangsmachtigingen configureren voor systeemeigen apps</span><span class="sxs-lookup"><span data-stu-id="8fd6c-150">Configure API access permissions for native app</span></span>

1. <span data-ttu-id="8fd6c-151">Kies uw app.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-151">Choose your app.</span></span> <span data-ttu-id="8fd6c-152">Ga naar **Settings**.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-152">Go to **Settings**.</span></span>

2. <span data-ttu-id="8fd6c-153">Kies vereiste machtigingen **in API-toegang.**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-153">In API Access, choose **Required permissions**.</span></span>

3. <span data-ttu-id="8fd6c-154">Kies **Windows Azure Active Directory machtigingen**.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-154">Choose **Windows Azure Active Directory permissions**.</span></span> <span data-ttu-id="8fd6c-155">Selecteer **in Gedelegeerde machtigingen** de volgende machtigingen:</span><span class="sxs-lookup"><span data-stu-id="8fd6c-155">In **Delegated permissions**, select these permissions:</span></span>

    - <span data-ttu-id="8fd6c-156">**Aanmelden en gebruikersprofiel lezen**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-156">**Sign in and read user profile**</span></span>
    - <span data-ttu-id="8fd6c-157">**Mapgegevens lezen**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-157">**Read directory data**</span></span>
    - <span data-ttu-id="8fd6c-158">**Toegang tot de map als de aangemelde gebruiker**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-158">**Access the directory as the signed-in user**</span></span>
    - <span data-ttu-id="8fd6c-159">**Alle groepen lezen**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-159">**Read all groups**</span></span>

4. <span data-ttu-id="8fd6c-160">Sla de machtigingen op.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-160">Save the permissions.</span></span>

5. <span data-ttu-id="8fd6c-161">Kies **Toevoegen** in **Vereiste machtigingen.**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-161">Choose **Add** in **Required permissions**.</span></span>

6. <span data-ttu-id="8fd6c-162">Kies **Een API selecteren**.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-162">Choose **Select an API**.</span></span>

    1. <span data-ttu-id="8fd6c-163">Voer in het zoekvak **Microsoft Partner Center** selecteer deze in de lijst met resultaten.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-163">In the search box, enter **Microsoft Partner Center** and select it from the results list.</span></span>

    2. <span data-ttu-id="8fd6c-164">Kies **Selecteren**.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-164">Choose **Select**.</span></span>

7. <span data-ttu-id="8fd6c-165">Kies **Machtigingen selecteren**.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-165">Choose **Select permissions**.</span></span>

    1. <span data-ttu-id="8fd6c-166">Selecteer **Toegang Partner Center PPE.**</span><span class="sxs-lookup"><span data-stu-id="8fd6c-166">Select **Access Partner Center PPE**.</span></span>
    
    2. <span data-ttu-id="8fd6c-167">Kies **Selecteren**.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-167">Choose **Select**.</span></span>

8. <span data-ttu-id="8fd6c-168">Kies **Gereed**.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-168">Choose **Done**.</span></span>

>[!IMPORTANT]
> <span data-ttu-id="8fd6c-169">Noteer de toepassings-id in de eigenschappen van uw app.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-169">Note the application ID in the Properties of your app.</span></span>

<span data-ttu-id="8fd6c-170">U hoeft geen systeemeigen apps te registreren in Partner Center, maar de systeemeigen app moet wel beheerdersmachtiging hebben.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-170">You do not need to register native apps in Partner Center, however the native app must be admin consented.</span></span> <span data-ttu-id="8fd6c-171">Noteer de toepassings-id van uw eigen app.</span><span class="sxs-lookup"><span data-stu-id="8fd6c-171">Note the application ID of your native app.</span></span>
