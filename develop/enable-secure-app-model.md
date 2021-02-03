---
title: Beveiligd toepassingsmodel inschakelen
description: Beveilig uw partner centrum en apps in het configuratie scherm.
ms.date: 01/20/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-csp
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 3e153e1e7d4e38580d8cb39a3996e56365ff5fbe
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767362"
---
# <a name="enabling-the-secure-application-model-framework"></a><span data-ttu-id="aaeb9-103">Het Secure Application Model-framework inschakelen</span><span class="sxs-lookup"><span data-stu-id="aaeb9-103">Enabling the Secure Application Model framework</span></span>

<span data-ttu-id="aaeb9-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="aaeb9-104">**Applies to:**</span></span>

- <span data-ttu-id="aaeb9-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="aaeb9-105">Partner Center</span></span>

<span data-ttu-id="aaeb9-106">Micro soft introduceert een veilig, schaalbaar Framework voor het verifiëren van de CSP-partners (Cloud Solution Provider) en leveranciers van configuratie schermen (CPV) via de Microsoft Azure multi-factor Authentication-architectuur (MFA).</span><span class="sxs-lookup"><span data-stu-id="aaeb9-106">Microsoft is introducing a secure, scalable framework for authenticating cloud solution provider (CSP) partners and control panel vendors (CPV) through the Microsoft Azure multi-factor authentication (MFA) architecture.</span></span>

<span data-ttu-id="aaeb9-107">U kunt het nieuwe model gebruiken om de beveiliging van partner Center API-integratie aanroepen te verhogen.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-107">You can use the new model to elevate security for Partner Center API integration calls.</span></span> <span data-ttu-id="aaeb9-108">Dit helpt alle partijen (inclusief micro soft, CSP-partners en CPVs) om hun infra structuur en klant gegevens te beschermen tegen beveiligings Risico's.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-108">This will help all parties (including Microsoft, CSP partners, and CPVs) to protect their infrastructure and customer data from security risks.</span></span>

## <a name="scope"></a><span data-ttu-id="aaeb9-109">Bereik</span><span class="sxs-lookup"><span data-stu-id="aaeb9-109">Scope</span></span>

<span data-ttu-id="aaeb9-110">Dit artikel heeft betrekking op de volgende actoren:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-110">This article concerns the following actors:</span></span>

- <span data-ttu-id="aaeb9-111">CPV's (Control Panel Vendors)</span><span class="sxs-lookup"><span data-stu-id="aaeb9-111">CPVs</span></span>
  - <span data-ttu-id="aaeb9-112">Een CPV is een onafhankelijke softwareleverancier die apps ontwikkelt voor gebruik door CSP-partners om te integreren met Partner Center-API's.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-112">A CPV is an independent software vendor that develops apps for use by CSP partners to integrate with Partner Center APIs.</span></span>
  - <span data-ttu-id="aaeb9-113">Een CPV is geen CSP-partner met directe toegang tot het Partner Center-dashboard of API's.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-113">A CPV isn't a CSP partner with direct access to the Partner Center dashboard or APIs.</span></span>

- <span data-ttu-id="aaeb9-114">Indirecte CSP-providers en CSP direct-partners die App-ID + gebruikers authenticatie gebruiken en rechtstreeks integreren met partner Center-Api's.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-114">CSP indirect providers and CSP direct partners who are using app ID + user authentication and directly integrate with Partner Center APIs.</span></span>

## <a name="security-requirements"></a><span data-ttu-id="aaeb9-115">Beveiligingsvereisten</span><span class="sxs-lookup"><span data-stu-id="aaeb9-115">Security requirements</span></span>

<span data-ttu-id="aaeb9-116">Zie vereisten voor de beveiliging van [partners](/partner-center/partner-security-requirements)voor meer informatie over de beveiligings vereisten.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-116">For details on security requirements, see [Partner Security Requirements](/partner-center/partner-security-requirements).</span></span>

## <a name="secure-application-model"></a><span data-ttu-id="aaeb9-117">Model voor beveiligde toepassing</span><span class="sxs-lookup"><span data-stu-id="aaeb9-117">Secure Application Model</span></span>

<span data-ttu-id="aaeb9-118">Marketplace-toepassingen moeten de CSP-partner privileges imiteren om micro soft-Api's aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-118">Marketplace applications need to impersonate CSP partner privileges to call Microsoft APIs.</span></span> <span data-ttu-id="aaeb9-119">Beveiligings aanvallen op deze gevoelige toepassingen kunnen leiden tot inbreuk op klant gegevens.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-119">Security attacks on these sensitive applications can lead to the compromise of customer data.</span></span>

<span data-ttu-id="aaeb9-120">Down load het document voor het [Framework van beveiligde toepassingen](https://assetsprod.microsoft.com/secure-application-model-guide.pdf) voor een overzicht en Details van het nieuwe verificatie raamwerk.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-120">For an overview and details of the new authentication framework, download the [Secure Application Model framework](https://assetsprod.microsoft.com/secure-application-model-guide.pdf) document.</span></span> <span data-ttu-id="aaeb9-121">Dit document bevat principes en aanbevolen procedures om Marketplace-toepassingen duurzaam en robuust te maken tegen beveiligings problemen.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-121">This document covers principles and best practices to make marketplace applications sustainable and robust from security compromises.</span></span>

## <a name="samples"></a><span data-ttu-id="aaeb9-122">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="aaeb9-122">Samples</span></span>

<span data-ttu-id="aaeb9-123">In de volgende overzichts documenten en voorbeeld code wordt beschreven hoe partners het beveiligde toepassings model Framework kunnen implementeren:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-123">The following overview documents and sample code describe how partners can implement the Secure Application Model framework:</span></span>

- [<span data-ttu-id="aaeb9-124">Overzichts document van de CPV</span><span class="sxs-lookup"><span data-stu-id="aaeb9-124">CPV overview document</span></span>](https://assetsprod.microsoft.com/cpv-partner-application-overview.pdf)
- [<span data-ttu-id="aaeb9-125">CSP-overzichts document</span><span class="sxs-lookup"><span data-stu-id="aaeb9-125">CSP overview document</span></span>](https://assetsprod.microsoft.com/csp-partner-application-overview.pdf)
- [<span data-ttu-id="aaeb9-126">.NET-voor beelden</span><span class="sxs-lookup"><span data-stu-id="aaeb9-126">.NET Samples</span></span>](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model)
- [<span data-ttu-id="aaeb9-127">Java-voor beelden</span><span class="sxs-lookup"><span data-stu-id="aaeb9-127">Java Samples</span></span>](https://github.com/microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model)

    [!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

- [<span data-ttu-id="aaeb9-128">REST-instructies en voor beelden</span><span class="sxs-lookup"><span data-stu-id="aaeb9-128">REST instructions and samples</span></span>](#rest)
- [<span data-ttu-id="aaeb9-129">Power shell-instructies en voor beelden</span><span class="sxs-lookup"><span data-stu-id="aaeb9-129">PowerShell instructions and samples</span></span>](#powershell)

## <a name="rest"></a><span data-ttu-id="aaeb9-130">REST</span><span class="sxs-lookup"><span data-stu-id="aaeb9-130">REST</span></span>

<span data-ttu-id="aaeb9-131">Voer de volgende stappen uit om REST-aanroepen te maken met het Framework van het beveiligde toepassings model met voorbeeld code:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-131">To to make REST calls with the Secure Application Model framework with sample code, follow these steps:</span></span>

1. [<span data-ttu-id="aaeb9-132">Een web-app maken</span><span class="sxs-lookup"><span data-stu-id="aaeb9-132">Create a web app</span></span>](#create-a-web-app)

2. [<span data-ttu-id="aaeb9-133">Een autorisatie code ophalen</span><span class="sxs-lookup"><span data-stu-id="aaeb9-133">Get an authorization code</span></span>](#get-authorization-code)

3. [<span data-ttu-id="aaeb9-134">Een vernieuwings Token ophalen</span><span class="sxs-lookup"><span data-stu-id="aaeb9-134">Get a refresh token</span></span>](#get-refresh-token)

4. [<span data-ttu-id="aaeb9-135">Een toegangstoken opvragen</span><span class="sxs-lookup"><span data-stu-id="aaeb9-135">Get an access token</span></span>](#get-access-token)

5. <span data-ttu-id="aaeb9-136">[Make a Partner Center API call](#make-partner-center-api-calls) (Partner Center-API-aanroep uitvoeren)</span><span class="sxs-lookup"><span data-stu-id="aaeb9-136">[Make a Partner Center API call](#make-partner-center-api-calls)</span></span>

> [!TIP]
> <span data-ttu-id="aaeb9-137">U kunt de Power shell-module van partner Center gebruiken om een autorisatie code en een vernieuwings token op te halen.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-137">You can use the Partner Center PowerShell module to get an authorization code and a refresh token.</span></span> <span data-ttu-id="aaeb9-138">U kunt deze optie kiezen in plaats van stap 2 en 3.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-138">You can choose this option in place of steps 2 and 3.</span></span> <span data-ttu-id="aaeb9-139">Zie de [sectie en voor beelden van Power shell](#powershell)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-139">For more information, see the [PowerShell section and examples](#powershell).</span></span>

### <a name="create-a-web-app"></a><span data-ttu-id="aaeb9-140">Een web-app maken</span><span class="sxs-lookup"><span data-stu-id="aaeb9-140">Create a web app</span></span>

<span data-ttu-id="aaeb9-141">U moet een web-app maken en registreren in het partner centrum voordat u REST-aanroepen maakt.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-141">You must create and register a web app in Partner Center before making REST calls.</span></span>

1. <span data-ttu-id="aaeb9-142">Meld u aan bij de [Azure-portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="aaeb9-142">Sign in to the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="aaeb9-143">Maak een Azure Active Directory-app (Azure AD).</span><span class="sxs-lookup"><span data-stu-id="aaeb9-143">Create an Azure Active Directory (Azure AD) app.</span></span>

3. <span data-ttu-id="aaeb9-144">Geef overgedragen toepassings machtigingen voor de volgende resources, *afhankelijk van de vereisten van uw toepassing*.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-144">Give delegated application permissions to the following resources, *depending on your application's requirements*.</span></span> <span data-ttu-id="aaeb9-145">Indien nodig kunt u meer gedelegeerde machtigingen voor toepassings resources toevoegen.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-145">If necessary, you can add more delegated permissions for application resources.</span></span>

   1. <span data-ttu-id="aaeb9-146">**Micro soft Partner Center** (sommige tenants geven dit weer als **SampleBECApp**)</span><span class="sxs-lookup"><span data-stu-id="aaeb9-146">**Microsoft Partner Center** (some tenants show this as **SampleBECApp**)</span></span>

   2. <span data-ttu-id="aaeb9-147">**Azure-beheer-api's** (als u van plan bent om Azure-api's aan te roepen)</span><span class="sxs-lookup"><span data-stu-id="aaeb9-147">**Azure Management APIs** (if you are planning to call Azure APIs)</span></span>

   3. <span data-ttu-id="aaeb9-148">**Windows Azure Active Directory**</span><span class="sxs-lookup"><span data-stu-id="aaeb9-148">**Windows Azure Active Directory**</span></span>

4. <span data-ttu-id="aaeb9-149">Zorg ervoor dat de Home-URL van uw app is ingesteld op een eind punt waarop een live web-app wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-149">Make sure that the home URL of your app is set to an endpoint where a live web app is running.</span></span> <span data-ttu-id="aaeb9-150">Deze app moet de [autorisatie code](#get-authorization-code) van de Azure AD-aanmeldings oproep accepteren.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-150">This app will need to accept the [authorization code](#get-authorization-code) from the Azure AD login call.</span></span> <span data-ttu-id="aaeb9-151">In de voorbeeld code in [de volgende sectie](#get-authorization-code)wordt de Web-App bijvoorbeeld uitgevoerd op `https://localhost:44395/` .</span><span class="sxs-lookup"><span data-stu-id="aaeb9-151">For example, in the example code in [the following section](#get-authorization-code), the web app is running at `https://localhost:44395/`.</span></span>

5. <span data-ttu-id="aaeb9-152">Houd rekening met de volgende informatie van de instellingen van uw web-app in azure AD:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-152">Note the following information from your web app's settings in Azure AD:</span></span>

   - <span data-ttu-id="aaeb9-153">Toepassings-id</span><span class="sxs-lookup"><span data-stu-id="aaeb9-153">Application ID</span></span>
   - <span data-ttu-id="aaeb9-154">Toepassingsgeheim</span><span class="sxs-lookup"><span data-stu-id="aaeb9-154">Application secret</span></span>

> [!NOTE]
> <span data-ttu-id="aaeb9-155">Het is raadzaam om [een certificaat als uw toepassings geheim te gebruiken](/azure/active-directory/develop/active-directory-certificate-credentials).</span><span class="sxs-lookup"><span data-stu-id="aaeb9-155">It is recommended to [use a certificate as your application secret](/azure/active-directory/develop/active-directory-certificate-credentials).</span></span> <span data-ttu-id="aaeb9-156">U kunt echter ook een toepassings sleutel maken in de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-156">However, you can also create an application key in the Azure portal.</span></span> <span data-ttu-id="aaeb9-157">In de voorbeeld code in [de volgende sectie](#get-authorization-code) wordt een toepassings sleutel gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-157">The sample code in [the following section](#get-authorization-code) uses an application key.</span></span>

### <a name="get-authorization-code"></a><span data-ttu-id="aaeb9-158">Autorisatiecode verkrijgen</span><span class="sxs-lookup"><span data-stu-id="aaeb9-158">Get authorization code</span></span>

<span data-ttu-id="aaeb9-159">U moet een autorisatie code voor uw web-app verkrijgen om te accepteren van de Azure AD-aanmeldings oproep:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-159">You must get an authorization code for your web app to accept from the Azure AD login call:</span></span>

1. <span data-ttu-id="aaeb9-160">Meld u aan bij Azure AD via de volgende URL: [https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1) .</span><span class="sxs-lookup"><span data-stu-id="aaeb9-160">Log in to Azure AD at the following URL: [https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1).</span></span> <span data-ttu-id="aaeb9-161">Zorg ervoor dat u zich aanmeldt met het gebruikers account waarmee u partner Center-API-aanroepen (zoals een beheer agent of een account van een verkoop medewerker) gaat maken.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-161">Be sure to log in with the user account from which you will make Partner Center API calls (such as an admin agent or sales agent account).</span></span>

2. <span data-ttu-id="aaeb9-162">Vervang de **toepassings-id** door uw Azure AD-App-ID (GUID).</span><span class="sxs-lookup"><span data-stu-id="aaeb9-162">Replace **Application-Id** with your Azure AD app ID (GUID).</span></span>

3. <span data-ttu-id="aaeb9-163">Wanneer u hierom wordt gevraagd, meldt u zich aan met uw gebruikers account waarvoor MFA is geconfigureerd.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-163">When prompted, log in with your user account with MFA configured.</span></span>

4. <span data-ttu-id="aaeb9-164">Wanneer u hierom wordt gevraagd, voert u aanvullende MFA-gegevens (telefoon nummer of e-mail adres) in om uw aanmelding te controleren.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-164">When prompted, enter additional MFA information (phone number or email address) to verify your login.</span></span>

5. <span data-ttu-id="aaeb9-165">Nadat u bent aangemeld, stuurt de browser de oproep naar het eind punt van de web-app om met uw autorisatie code.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-165">After you are logged in, the browser will redirect the call to your web app endpoint with your authorization code.</span></span> <span data-ttu-id="aaeb9-166">Met de volgende voorbeeld code wordt bijvoorbeeld omgeleid naar `https://localhost:44395/` .</span><span class="sxs-lookup"><span data-stu-id="aaeb9-166">For example, the following sample code redirects to `https://localhost:44395/`.</span></span>

#### <a name="authorization-code-call-trace"></a><span data-ttu-id="aaeb9-167">Tracering van autorisatie code aanroepen</span><span class="sxs-lookup"><span data-stu-id="aaeb9-167">Authorization code call trace</span></span>

```http
POST https://localhost:44395/ HTTP/1.1
Origin: https://login.microsoftonline.com
Upgrade-Insecure-Requests: 1
Content-Type: application/x-www-form-urlencoded
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8
Referrer: https://login.microsoftonline.com/kmsi
Accept-Encoding: gzip, deflate, br
Accept-Language: en-US,en;q=0.9
Cookie: OpenIdConnect.nonce.hOMjjrivcxzuI4YqAw4uYC%2F%2BILFk4%2FCx3kHTHP3lBvA%3D=dHVyRXdlbk9WVUZFdlFONVdiY01nNEpUc0JRR0RiYWFLTHhQYlRGNl9VeXJqNjdLTGV3cFpIWFg1YmpnWVdQUURtN0dvMkdHS2kzTm02NGdQS09veVNEbTZJMDk1TVVNYkczYmstQmlKUzFQaTBFMEdhNVJGVHlES2d3WGlCSlVlN1c2UE9sd2kzckNrVGN2RFNULWdHY2JET3RDQUxSaXRfLXZQdG00RnlUM0E1TUo1YWNKOWxvQXRwSkhRYklQbmZUV3d3eHVfNEpMUUthMFlQUFgzS01RS2NvMXYtbnV4UVJOYkl4TTN0cw%3D%3D

code=AuthorizationCodeValue&id_token=IdTokenValue&<rest of properties for state>
```

### <a name="get-refresh-token"></a><span data-ttu-id="aaeb9-168">Vernieuwings Token ophalen</span><span class="sxs-lookup"><span data-stu-id="aaeb9-168">Get refresh token</span></span>

<span data-ttu-id="aaeb9-169">U moet vervolgens uw autorisatie code gebruiken om een vernieuwings token op te halen:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-169">You must then use your authorization code to get a refresh token:</span></span>

1. <span data-ttu-id="aaeb9-170">Maak een POST-aanroep naar het Azure AD-aanmeld eindpunt `https://login.microsoftonline.com/CSPTenantID/oauth2/token` met de autorisatie code.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-170">Make a POST call to the Azure AD login endpoint `https://login.microsoftonline.com/CSPTenantID/oauth2/token` with the authorization code.</span></span> <span data-ttu-id="aaeb9-171">Zie de volgende [voorbeeld aanroep](#sample-refresh-call)voor een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-171">For an example, see the following [sample call](#sample-refresh-call).</span></span>

2. <span data-ttu-id="aaeb9-172">Let op het vernieuwings token dat wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-172">Note the refresh token that is returned.</span></span>

3. <span data-ttu-id="aaeb9-173">Sla het vernieuwings token op in Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-173">Store the refresh token in Azure Key Vault.</span></span> <span data-ttu-id="aaeb9-174">Zie de documentatie van de [Key Vault-API](/rest/api/keyvault/)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-174">For more information, see the [Key Vault API documentation](/rest/api/keyvault/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aaeb9-175">Het vernieuwingstoken moet [als een geheim worden opgeslagen](/rest/api/keyvault/setsecret/setsecret) in Key Vault.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-175">The refresh token must be [stored as a secret](/rest/api/keyvault/setsecret/setsecret) in Key Vault.</span></span>

#### <a name="sample-refresh-call"></a><span data-ttu-id="aaeb9-176">Voor beeld van een vernieuwings oproep</span><span class="sxs-lookup"><span data-stu-id="aaeb9-176">Sample refresh call</span></span>

<span data-ttu-id="aaeb9-177">Aanvraag voor tijdelijke aanduiding:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-177">Placeholder request:</span></span>

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 966
Expect: 100-continue
```

<span data-ttu-id="aaeb9-178">Aanvraagtekst:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-178">Request body:</span></span>

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id&client_secret=Application-Secret&grant_type=authorization_code&code=AuthorizationCodeValue
```

<span data-ttu-id="aaeb9-179">Antwoord op tijdelijke aanduiding:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-179">Placeholder response:</span></span>

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

<span data-ttu-id="aaeb9-180">Antwoord tekst:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-180">Response body:</span></span>

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3599","ext_expires_in":"3599","expires_on":"1547579127","not_before":"1547575227","resource":"https://api.partnercenter.microsoft.com","access_token":"Access
```

### <a name="get-access-token"></a><span data-ttu-id="aaeb9-181">Toegangs Token ophalen</span><span class="sxs-lookup"><span data-stu-id="aaeb9-181">Get access token</span></span>

<span data-ttu-id="aaeb9-182">U moet een toegangs token verkrijgen voordat u aanroepen naar de partner centrum-Api's kunt maken.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-182">You must obtain an access token before you can make calls to the Partner Center APIs.</span></span> <span data-ttu-id="aaeb9-183">U moet een vernieuwings token gebruiken om een toegangs token te verkrijgen, omdat het toegangs token over het algemeen een zeer beperkte levens duur heeft (bijvoorbeeld minder dan een uur).</span><span class="sxs-lookup"><span data-stu-id="aaeb9-183">You must use a refresh token to obtain an access token because access token generally have a very limited lifetime (for example, less than an hour).</span></span>

<span data-ttu-id="aaeb9-184">Aanvraag voor tijdelijke aanduiding:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-184">Placeholder request:</span></span>

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 1212
Expect: 100-continue
```

<span data-ttu-id="aaeb9-185">Aanvraagtekst:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-185">Request body:</span></span>

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id &client_secret= Application-Secret&grant_type=refresh_token&refresh_token=RefreshTokenVlaue&scope=openid
```

<span data-ttu-id="aaeb9-186">Antwoord op tijdelijke aanduiding:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-186">Placeholder response:</span></span>

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

<span data-ttu-id="aaeb9-187">Antwoord tekst:</span><span class="sxs-lookup"><span data-stu-id="aaeb9-187">Response body:</span></span>

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3600","ext_expires_in":"3600","expires_on":"1547581389","not_before":"1547577489","resource":"https://api.partnercenter.microsoft.com","access_token":"AccessTokenValue","id_token":"IDTokenValue"}
```

### <a name="make-partner-center-api-calls"></a><span data-ttu-id="aaeb9-188">Partner Center-API-aanroepen maken</span><span class="sxs-lookup"><span data-stu-id="aaeb9-188">Make Partner Center API calls</span></span>

<span data-ttu-id="aaeb9-189">U moet uw toegangs token gebruiken om de Api's van het partner centrum aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-189">You must use your access token to call the Partner Center APIs.</span></span> <span data-ttu-id="aaeb9-190">Raadpleeg de volgende voorbeeld aanroep.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-190">See the following example call.</span></span>

#### <a name="example-partner-center-api-call"></a><span data-ttu-id="aaeb9-191">Voor beeld van partner Center API-aanroep</span><span class="sxs-lookup"><span data-stu-id="aaeb9-191">Example Partner Center API call</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/CustomerTenantId/users HTTP/1.1
Authorization: Bearer AccessTokenValue
Accept: application/json
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="powershell"></a><span data-ttu-id="aaeb9-192">PowerShell</span><span class="sxs-lookup"><span data-stu-id="aaeb9-192">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="aaeb9-193">U kunt de [Power shell-module van partner Center](https://www.powershellgallery.com/packages/PartnerCenter) gebruiken om de vereiste infra structuur te verlagen voor het uitwisselen van een autorisatie code voor een toegangs token.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-193">You can use the [Partner Center PowerShell module](https://www.powershellgallery.com/packages/PartnerCenter) to reduce the required infrastructure to exchange an authorization code for an access token.</span></span> <span data-ttu-id="aaeb9-194">Deze methode is optioneel voor het maken van [rest-aanroepen van het partner centrum](#rest).</span><span class="sxs-lookup"><span data-stu-id="aaeb9-194">This method is optional for making [Partner Center REST calls](#rest).</span></span>

<span data-ttu-id="aaeb9-195">Zie [Secure app model](/powershell/partnercenter/secure-app-model) Power shell Documentation (Engelstalig) voor meer informatie over dit proces.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-195">For more information on this process, see [Secure App Model](/powershell/partnercenter/secure-app-model) PowerShell documentation.</span></span>

1. <span data-ttu-id="aaeb9-196">Installeer de Power shell-modules voor Azure AD en partner Center.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-196">Install the Azure AD and Partner Center PowerShell modules.</span></span>

    ```powershell
    Install-Module AzureAD
    ```

    ```powershell
    Install-Module PartnerCenter
    ```

2. <span data-ttu-id="aaeb9-197">Gebruik de opdracht **[New-PartnerAccessToken](/powershell/module/partnercenter/new-partneraccesstoken)** om het toestemming proces uit te voeren en het vereiste vernieuwings token vast te leggen.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-197">Use the **[New-PartnerAccessToken](/powershell/module/partnercenter/new-partneraccesstoken)** command to perform the consent process and capture the required refresh token.</span></span>

    ```powershell
    $credential = Get-Credential

    New-PartnerAccessToken -ApplicationId 'xxxx-xxxx-xxxx-xxxx' -Scopes 'https://api.partnercenter.microsoft.com/user_impersonation' -ServicePrincipal -Credential $credential -Tenant 'yyyy-yyyy-yyyy-yyyy' -UseAuthorizationCode
    ```

    > [!NOTE]
    > <span data-ttu-id="aaeb9-198">De para meter **ServicePrincipal** wordt gebruikt met de opdracht **New-PartnerAccessToken** , omdat er een Azure AD-app met een type **Web/API** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-198">The **ServicePrincipal** parameter is used with the **New-PartnerAccessToken** command because an Azure AD app with a type of **Web/API** is being used.</span></span> <span data-ttu-id="aaeb9-199">Voor dit type app moeten een client-id en een geheim worden opgenomen in de aanvraag van de toegangs token.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-199">This type of app requires that a client identifier and secret be included in the access token request.</span></span> <span data-ttu-id="aaeb9-200">Wanneer de **Get-Credential-** opdracht wordt aangeroepen, wordt u gevraagd om een gebruikers naam en wacht woord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-200">When the **Get-Credential** command is invoked, you will be prompted to enter a username and password.</span></span> <span data-ttu-id="aaeb9-201">Voer de toepassings-id in als de gebruikers naam.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-201">Enter the application identifier as the username.</span></span> <span data-ttu-id="aaeb9-202">Voer het toepassings geheim in als het wacht woord.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-202">Enter the application secret as the password.</span></span> <span data-ttu-id="aaeb9-203">Wanneer de opdracht **New-PartnerAccessToken** wordt aangeroepen, wordt u gevraagd om de referenties opnieuw in te voeren.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-203">When the **New-PartnerAccessToken** command is invoked, you will be prompted to enter credentials again.</span></span> <span data-ttu-id="aaeb9-204">Voer de referenties in voor het service account dat u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-204">Enter the credentials for the service account that you are using.</span></span> <span data-ttu-id="aaeb9-205">Dit service account moet een partner account zijn met de juiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-205">This service account should be a partner account with appropriate permissions.</span></span>

3. <span data-ttu-id="aaeb9-206">Kopieer de waarde van het vernieuwings token.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-206">Copy the refresh token value.</span></span>

    ```powershell
    $token.RefreshToken | clip
    ```

<span data-ttu-id="aaeb9-207">U moet de waarde van het vernieuwings token opslaan in een beveiligde opslag plaats, zoals Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-207">You should store the refresh token value in a secure repository, such as Azure Key Vault.</span></span> <span data-ttu-id="aaeb9-208">Zie het artikel [multi-factor Authentication](/powershell/partnercenter/multi-factor-auth) voor meer informatie over het gebruik van de module veilige toepassing met Power shell.</span><span class="sxs-lookup"><span data-stu-id="aaeb9-208">For more information on how to leverage the secure application module with PowerShell, see the [multi-factor authentication](/powershell/partnercenter/multi-factor-auth) article.</span></span>
