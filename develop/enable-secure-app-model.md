---
title: Beveiligd toepassingsmodel inschakelen
description: Beveilig uw Partner Center apps en configuratiescherm.
ms.date: 01/20/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-csp
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 19a1c39576a4f897df2d1205e3501839f6580831
ms.sourcegitcommit: e0077b2724d128ab20cb05696e5e5b1cde8e5214
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/07/2021
ms.locfileid: "113481664"
---
# <a name="enabling-the-secure-application-model-framework"></a><span data-ttu-id="d1286-103">Het Secure Application Model-framework inschakelen</span><span class="sxs-lookup"><span data-stu-id="d1286-103">Enabling the Secure Application Model framework</span></span>

<span data-ttu-id="d1286-104">Microsoft introduceert een veilig, schaalbaar framework voor de verificatie van CSP-partners (Cloud Solution Provider) en configuratieschermleveranciers (CPV) via de architectuur van Microsoft Azure Active Directory Multi-Factor Authentication (MFA).</span><span class="sxs-lookup"><span data-stu-id="d1286-104">Microsoft is introducing a secure, scalable framework for authenticating cloud solution provider (CSP) partners and control panel vendors (CPV) through the Microsoft Azure Active Directory Multi-Factor Authentication (MFA) architecture.</span></span>

<span data-ttu-id="d1286-105">U kunt het nieuwe model gebruiken om de beveiliging voor aanroepen van Partner Center API-integratie uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="d1286-105">You can use the new model to elevate security for Partner Center API integration calls.</span></span> <span data-ttu-id="d1286-106">Hiermee kunnen alle partijen (inclusief Microsoft, CSP-partners en CPV's) hun infrastructuur en klantgegevens beschermen tegen beveiligingsrisico's.</span><span class="sxs-lookup"><span data-stu-id="d1286-106">This will help all parties (including Microsoft, CSP partners, and CPVs) to protect their infrastructure and customer data from security risks.</span></span>

## <a name="scope"></a><span data-ttu-id="d1286-107">Bereik</span><span class="sxs-lookup"><span data-stu-id="d1286-107">Scope</span></span>

<span data-ttu-id="d1286-108">Dit artikel heeft betrekking op de volgende actoren:</span><span class="sxs-lookup"><span data-stu-id="d1286-108">This article concerns the following actors:</span></span>

- <span data-ttu-id="d1286-109">CPV's (Control Panel Vendors)</span><span class="sxs-lookup"><span data-stu-id="d1286-109">CPVs</span></span>
  - <span data-ttu-id="d1286-110">Een CPV is een onafhankelijke softwareleverancier die apps ontwikkelt voor gebruik door CSP-partners om te integreren met Partner Center-API's.</span><span class="sxs-lookup"><span data-stu-id="d1286-110">A CPV is an independent software vendor that develops apps for use by CSP partners to integrate with Partner Center APIs.</span></span>
  - <span data-ttu-id="d1286-111">Een CPV is geen CSP-partner met directe toegang tot het Partner Center-dashboard of API's.</span><span class="sxs-lookup"><span data-stu-id="d1286-111">A CPV isn't a CSP partner with direct access to the Partner Center dashboard or APIs.</span></span>

- <span data-ttu-id="d1286-112">Indirecte CSP-providers en directe CSP-partners die app-id en gebruikersverificatie gebruiken en rechtstreeks integreren met Partner Center API's.</span><span class="sxs-lookup"><span data-stu-id="d1286-112">CSP indirect providers and CSP direct partners who are using app ID + user authentication and directly integrate with Partner Center APIs.</span></span>

## <a name="security-requirements"></a><span data-ttu-id="d1286-113">Beveiligingsvereisten</span><span class="sxs-lookup"><span data-stu-id="d1286-113">Security requirements</span></span>

<span data-ttu-id="d1286-114">Zie Beveiligingsvereisten van partners voor [meer informatie over beveiligingsvereisten.](/partner-center/partner-security-requirements)</span><span class="sxs-lookup"><span data-stu-id="d1286-114">For details on security requirements, see [Partner Security Requirements](/partner-center/partner-security-requirements).</span></span>

## <a name="secure-application-model"></a><span data-ttu-id="d1286-115">veilig toepassingsmodel</span><span class="sxs-lookup"><span data-stu-id="d1286-115">Secure Application Model</span></span>

<span data-ttu-id="d1286-116">Marketplace-toepassingen moeten CSP-partnerbevoegdheden imiteren om Microsoft API's aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="d1286-116">Marketplace applications need to impersonate CSP partner privileges to call Microsoft APIs.</span></span> <span data-ttu-id="d1286-117">Beveiligingsaanvallen op deze gevoelige toepassingen kunnen leiden tot het compromitteerd van klantgegevens.</span><span class="sxs-lookup"><span data-stu-id="d1286-117">Security attacks on these sensitive applications can lead to the compromise of customer data.</span></span>

<span data-ttu-id="d1286-118">Download het document veilig toepassingsmodel framework voor een overzicht [en details van het nieuwe veilig toepassingsmodel framework.](https://assetsprod.microsoft.com/secure-application-model-guide.pdf)</span><span class="sxs-lookup"><span data-stu-id="d1286-118">For an overview and details of the new authentication framework, download the [Secure Application Model framework](https://assetsprod.microsoft.com/secure-application-model-guide.pdf) document.</span></span> <span data-ttu-id="d1286-119">Dit document bevat principes en best practices om Marketplace-toepassingen duurzaam en robuust te maken tegen beveiligingsrisico's.</span><span class="sxs-lookup"><span data-stu-id="d1286-119">This document covers principles and best practices to make marketplace applications sustainable and robust from security compromises.</span></span>

## <a name="samples"></a><span data-ttu-id="d1286-120">Voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d1286-120">Samples</span></span>

<span data-ttu-id="d1286-121">In de volgende overzichtsdocumenten en voorbeeldcode wordt beschreven hoe partners het veilig toepassingsmodel implementeren:</span><span class="sxs-lookup"><span data-stu-id="d1286-121">The following overview documents and sample code describe how partners can implement the Secure Application Model framework:</span></span>

- [<span data-ttu-id="d1286-122">CpV-overzichtsdocument</span><span class="sxs-lookup"><span data-stu-id="d1286-122">CPV overview document</span></span>](https://assetsprod.microsoft.com/cpv-partner-application-overview.pdf)
- [<span data-ttu-id="d1286-123">CSP-overzichtsdocument</span><span class="sxs-lookup"><span data-stu-id="d1286-123">CSP overview document</span></span>](https://assetsprod.microsoft.com/csp-partner-application-overview.pdf)
- [<span data-ttu-id="d1286-124">.NET-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d1286-124">.NET Samples</span></span>](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model)
- [<span data-ttu-id="d1286-125">Java-voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d1286-125">Java Samples</span></span>](https://github.com/microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model)

    [!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

- [<span data-ttu-id="d1286-126">REST-instructies en -voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d1286-126">REST instructions and samples</span></span>](#rest)
- [<span data-ttu-id="d1286-127">PowerShell-instructies en -voorbeelden</span><span class="sxs-lookup"><span data-stu-id="d1286-127">PowerShell instructions and samples</span></span>](#powershell)

## <a name="rest"></a><span data-ttu-id="d1286-128">REST</span><span class="sxs-lookup"><span data-stu-id="d1286-128">REST</span></span>

<span data-ttu-id="d1286-129">Volg deze stappen om REST-aanroepen veilig toepassingsmodel framework met voorbeeldcode te maken:</span><span class="sxs-lookup"><span data-stu-id="d1286-129">To to make REST calls with the Secure Application Model framework with sample code, follow these steps:</span></span>

1. [<span data-ttu-id="d1286-130">Een web-app maken</span><span class="sxs-lookup"><span data-stu-id="d1286-130">Create a web app</span></span>](#create-a-web-app)

2. [<span data-ttu-id="d1286-131">Een autorisatiecode verkrijgen</span><span class="sxs-lookup"><span data-stu-id="d1286-131">Get an authorization code</span></span>](#get-authorization-code)

3. [<span data-ttu-id="d1286-132">Een vernieuwings token op halen</span><span class="sxs-lookup"><span data-stu-id="d1286-132">Get a refresh token</span></span>](#get-refresh-token)

4. [<span data-ttu-id="d1286-133">Een toegangstoken opvragen</span><span class="sxs-lookup"><span data-stu-id="d1286-133">Get an access token</span></span>](#get-access-token)

5. <span data-ttu-id="d1286-134">[Make a Partner Center API call](#make-partner-center-api-calls) (Partner Center-API-aanroep uitvoeren)</span><span class="sxs-lookup"><span data-stu-id="d1286-134">[Make a Partner Center API call](#make-partner-center-api-calls)</span></span>

> [!TIP]
> <span data-ttu-id="d1286-135">U kunt de PowerShell Partner Center module gebruiken om een autorisatiecode en een vernieuwings token op te halen.</span><span class="sxs-lookup"><span data-stu-id="d1286-135">You can use the Partner Center PowerShell module to get an authorization code and a refresh token.</span></span> <span data-ttu-id="d1286-136">U kunt deze optie kiezen in plaats van stap 2 en 3.</span><span class="sxs-lookup"><span data-stu-id="d1286-136">You can choose this option in place of steps 2 and 3.</span></span> <span data-ttu-id="d1286-137">Zie de sectie [PowerShell](#powershell)en voorbeelden voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="d1286-137">For more information, see the [PowerShell section and examples](#powershell).</span></span>

### <a name="create-a-web-app"></a><span data-ttu-id="d1286-138">Een web-app maken</span><span class="sxs-lookup"><span data-stu-id="d1286-138">Create a web app</span></span>

<span data-ttu-id="d1286-139">U moet een web-app maken en registreren in Partner Center voordat u REST-aanroepen doet.</span><span class="sxs-lookup"><span data-stu-id="d1286-139">You must create and register a web app in Partner Center before making REST calls.</span></span>

1. <span data-ttu-id="d1286-140">Meld u aan bij de [Azure-portal](https://portal.azure.com).</span><span class="sxs-lookup"><span data-stu-id="d1286-140">Sign in to the [Azure portal](https://portal.azure.com).</span></span>

2. <span data-ttu-id="d1286-141">Maak een Azure Active Directory (Azure AD)-app.</span><span class="sxs-lookup"><span data-stu-id="d1286-141">Create an Azure Active Directory (Azure AD) app.</span></span>

3. <span data-ttu-id="d1286-142">Geef gedelegeerde toepassingsmachtigingen voor de volgende resources, afhankelijk van de vereisten *van uw toepassing.*</span><span class="sxs-lookup"><span data-stu-id="d1286-142">Give delegated application permissions to the following resources, *depending on your application's requirements*.</span></span> <span data-ttu-id="d1286-143">Indien nodig kunt u meer gedelegeerde machtigingen toevoegen voor toepassingsresources.</span><span class="sxs-lookup"><span data-stu-id="d1286-143">If necessary, you can add more delegated permissions for application resources.</span></span>

   1. <span data-ttu-id="d1286-144">**Microsoft Partner Center** (sommige tenants laten dit zien als **SampleBECApp**)</span><span class="sxs-lookup"><span data-stu-id="d1286-144">**Microsoft Partner Center** (some tenants show this as **SampleBECApp**)</span></span>

   2. <span data-ttu-id="d1286-145">**Azure Management-API's** (als u azure-API's wilt aanroepen)</span><span class="sxs-lookup"><span data-stu-id="d1286-145">**Azure Management APIs** (if you are planning to call Azure APIs)</span></span>

   3. <span data-ttu-id="d1286-146">**Windows Azure Active Directory**</span><span class="sxs-lookup"><span data-stu-id="d1286-146">**Windows Azure Active Directory**</span></span>

4. <span data-ttu-id="d1286-147">Zorg ervoor dat de start-URL van uw app is ingesteld op een eindpunt waarop een live web-app wordt uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="d1286-147">Make sure that the home URL of your app is set to an endpoint where a live web app is running.</span></span> <span data-ttu-id="d1286-148">Deze app moet de [](#get-authorization-code) autorisatiecode van de Azure AD-aanmeldingsoproep accepteren.</span><span class="sxs-lookup"><span data-stu-id="d1286-148">This app will need to accept the [authorization code](#get-authorization-code) from the Azure AD login call.</span></span> <span data-ttu-id="d1286-149">In de voorbeeldcode in de [volgende](#get-authorization-code)sectie wordt de web-app bijvoorbeeld uitgevoerd op `https://localhost:44395/` .</span><span class="sxs-lookup"><span data-stu-id="d1286-149">For example, in the example code in [the following section](#get-authorization-code), the web app is running at `https://localhost:44395/`.</span></span>

5. <span data-ttu-id="d1286-150">Let op de volgende informatie uit de instellingen van uw web-app in Azure AD:</span><span class="sxs-lookup"><span data-stu-id="d1286-150">Note the following information from your web app's settings in Azure AD:</span></span>

   - <span data-ttu-id="d1286-151">Toepassings-id</span><span class="sxs-lookup"><span data-stu-id="d1286-151">Application ID</span></span>
   - <span data-ttu-id="d1286-152">Toepassingsgeheim</span><span class="sxs-lookup"><span data-stu-id="d1286-152">Application secret</span></span>

> [!NOTE]
> <span data-ttu-id="d1286-153">Het wordt aanbevolen om [een certificaat te gebruiken als uw toepassingsgeheim.](/azure/active-directory/develop/active-directory-certificate-credentials)</span><span class="sxs-lookup"><span data-stu-id="d1286-153">It is recommended to [use a certificate as your application secret](/azure/active-directory/develop/active-directory-certificate-credentials).</span></span> <span data-ttu-id="d1286-154">U kunt echter ook een toepassingssleutel maken in de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="d1286-154">However, you can also create an application key in the Azure portal.</span></span> <span data-ttu-id="d1286-155">In de voorbeeldcode in [de volgende sectie wordt](#get-authorization-code) een toepassingssleutel gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d1286-155">The sample code in [the following section](#get-authorization-code) uses an application key.</span></span>

### <a name="get-authorization-code"></a><span data-ttu-id="d1286-156">Autorisatiecode verkrijgen</span><span class="sxs-lookup"><span data-stu-id="d1286-156">Get authorization code</span></span>

<span data-ttu-id="d1286-157">U moet een autorisatiecode voor uw web-app verkrijgen die u kunt accepteren via de Azure AD-aanmeldingsoproep:</span><span class="sxs-lookup"><span data-stu-id="d1286-157">You must get an authorization code for your web app to accept from the Azure AD login call:</span></span>

1. <span data-ttu-id="d1286-158">Meld u aan bij Azure AD via de volgende URL: [https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1) .</span><span class="sxs-lookup"><span data-stu-id="d1286-158">Log in to Azure AD at the following URL: [https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1).</span></span> <span data-ttu-id="d1286-159">Meld u aan met het gebruikersaccount van waaruit u API-aanroepen Partner Center (zoals een beheerderagent of verkoopagentaccount).</span><span class="sxs-lookup"><span data-stu-id="d1286-159">Be sure to log in with the user account from which you will make Partner Center API calls (such as an admin agent or sales agent account).</span></span>

2. <span data-ttu-id="d1286-160">Vervang **Application-Id door** uw Azure AD-app-id (GUID).</span><span class="sxs-lookup"><span data-stu-id="d1286-160">Replace **Application-Id** with your Azure AD app ID (GUID).</span></span>

3. <span data-ttu-id="d1286-161">Meld u aan met uw gebruikersaccount terwijl MFA is geconfigureerd wanneer u hier om wordt gevraagd.</span><span class="sxs-lookup"><span data-stu-id="d1286-161">When prompted, log in with your user account with MFA configured.</span></span>

4. <span data-ttu-id="d1286-162">Wanneer u hier om wordt gevraagd, voert u aanvullende MFA-gegevens (telefoonnummer of e-mailadres) in om uw aanmelding te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="d1286-162">When prompted, enter additional MFA information (phone number or email address) to verify your login.</span></span>

5. <span data-ttu-id="d1286-163">Nadat u bent aangemeld, leidt de browser de aanroep om naar het eindpunt van uw web-app met uw autorisatiecode.</span><span class="sxs-lookup"><span data-stu-id="d1286-163">After you are logged in, the browser will redirect the call to your web app endpoint with your authorization code.</span></span> <span data-ttu-id="d1286-164">Met de volgende voorbeeldcode wordt bijvoorbeeld omgeleid naar `https://localhost:44395/` .</span><span class="sxs-lookup"><span data-stu-id="d1286-164">For example, the following sample code redirects to `https://localhost:44395/`.</span></span>

#### <a name="authorization-code-call-trace"></a><span data-ttu-id="d1286-165">Trace aanroep van autorisatiecode</span><span class="sxs-lookup"><span data-stu-id="d1286-165">Authorization code call trace</span></span>

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

### <a name="get-refresh-token"></a><span data-ttu-id="d1286-166">Vernieuwings token op halen</span><span class="sxs-lookup"><span data-stu-id="d1286-166">Get refresh token</span></span>

<span data-ttu-id="d1286-167">Vervolgens moet u uw autorisatiecode gebruiken om een vernieuwings token op te halen:</span><span class="sxs-lookup"><span data-stu-id="d1286-167">You must then use your authorization code to get a refresh token:</span></span>

1. <span data-ttu-id="d1286-168">Maak een POST-aanroep naar het Azure AD-aanmeldings-eindpunt `https://login.microsoftonline.com/CSPTenantID/oauth2/token` met de autorisatiecode.</span><span class="sxs-lookup"><span data-stu-id="d1286-168">Make a POST call to the Azure AD login endpoint `https://login.microsoftonline.com/CSPTenantID/oauth2/token` with the authorization code.</span></span> <span data-ttu-id="d1286-169">Zie de volgende voorbeeldoproep voor [een voorbeeld.](#sample-refresh-call)</span><span class="sxs-lookup"><span data-stu-id="d1286-169">For an example, see the following [sample call](#sample-refresh-call).</span></span>

2. <span data-ttu-id="d1286-170">Let op het vernieuwings token dat wordt geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="d1286-170">Note the refresh token that is returned.</span></span>

3. <span data-ttu-id="d1286-171">Sla het vernieuwingstoken op in Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="d1286-171">Store the refresh token in Azure Key Vault.</span></span> <span data-ttu-id="d1286-172">Zie de API-documentatie [Key Vault meer informatie.](/rest/api/keyvault/)</span><span class="sxs-lookup"><span data-stu-id="d1286-172">For more information, see the [Key Vault API documentation](/rest/api/keyvault/).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d1286-173">Het vernieuwingstoken moet [als een geheim worden opgeslagen](/rest/api/keyvault/setsecret/setsecret) in Key Vault.</span><span class="sxs-lookup"><span data-stu-id="d1286-173">The refresh token must be [stored as a secret](/rest/api/keyvault/setsecret/setsecret) in Key Vault.</span></span>

#### <a name="sample-refresh-call"></a><span data-ttu-id="d1286-174">Voorbeeld van vernieuwingsoproep</span><span class="sxs-lookup"><span data-stu-id="d1286-174">Sample refresh call</span></span>

<span data-ttu-id="d1286-175">Aanvraag voor tijdelijke aanduiding:</span><span class="sxs-lookup"><span data-stu-id="d1286-175">Placeholder request:</span></span>

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 966
Expect: 100-continue
```

<span data-ttu-id="d1286-176">Aanvraagtekst:</span><span class="sxs-lookup"><span data-stu-id="d1286-176">Request body:</span></span>

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id&client_secret=Application-Secret&grant_type=authorization_code&code=AuthorizationCodeValue
```

<span data-ttu-id="d1286-177">Tijdelijke aanduiding voor antwoord:</span><span class="sxs-lookup"><span data-stu-id="d1286-177">Placeholder response:</span></span>

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

<span data-ttu-id="d1286-178">Antwoord body:</span><span class="sxs-lookup"><span data-stu-id="d1286-178">Response body:</span></span>

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3599","ext_expires_in":"3599","expires_on":"1547579127","not_before":"1547575227","resource":"https://api.partnercenter.microsoft.com","access_token":"Access
```

### <a name="get-access-token"></a><span data-ttu-id="d1286-179">Toegangs token op halen</span><span class="sxs-lookup"><span data-stu-id="d1286-179">Get access token</span></span>

<span data-ttu-id="d1286-180">U moet een toegangs token verkrijgen voordat u aanroepen naar de Partner Center API's kunt maken.</span><span class="sxs-lookup"><span data-stu-id="d1286-180">You must obtain an access token before you can make calls to the Partner Center APIs.</span></span> <span data-ttu-id="d1286-181">U moet een vernieuwingstoken gebruiken om een toegangstoken te verkrijgen, omdat toegangstokens doorgaans een zeer beperkte levensduur hebben (bijvoorbeeld minder dan een uur).</span><span class="sxs-lookup"><span data-stu-id="d1286-181">You must use a refresh token to obtain an access token because access tokens generally have a very limited lifetime (for example, less than an hour).</span></span>

<span data-ttu-id="d1286-182">Aanvraag voor tijdelijke aanduiding:</span><span class="sxs-lookup"><span data-stu-id="d1286-182">Placeholder request:</span></span>

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 1212
Expect: 100-continue
```

<span data-ttu-id="d1286-183">Aanvraagtekst:</span><span class="sxs-lookup"><span data-stu-id="d1286-183">Request body:</span></span>

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id &client_secret= Application-Secret&grant_type=refresh_token&refresh_token=RefreshTokenVlaue&scope=openid
```

<span data-ttu-id="d1286-184">Tijdelijke aanduiding voor antwoord:</span><span class="sxs-lookup"><span data-stu-id="d1286-184">Placeholder response:</span></span>

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

<span data-ttu-id="d1286-185">Antwoord body:</span><span class="sxs-lookup"><span data-stu-id="d1286-185">Response body:</span></span>

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3600","ext_expires_in":"3600","expires_on":"1547581389","not_before":"1547577489","resource":"https://api.partnercenter.microsoft.com","access_token":"AccessTokenValue","id_token":"IDTokenValue"}
```

### <a name="make-partner-center-api-calls"></a><span data-ttu-id="d1286-186">API Partner Center aanroepen</span><span class="sxs-lookup"><span data-stu-id="d1286-186">Make Partner Center API calls</span></span>

<span data-ttu-id="d1286-187">U moet uw toegangs token gebruiken om de api'Partner Center aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="d1286-187">You must use your access token to call the Partner Center APIs.</span></span> <span data-ttu-id="d1286-188">Zie de volgende voorbeeldoproep.</span><span class="sxs-lookup"><span data-stu-id="d1286-188">See the following example call.</span></span>

#### <a name="example-partner-center-api-call"></a><span data-ttu-id="d1286-189">Voorbeeld van Partner Center API-aanroep</span><span class="sxs-lookup"><span data-stu-id="d1286-189">Example Partner Center API call</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/CustomerTenantId/users HTTP/1.1
Authorization: Bearer AccessTokenValue
Accept: application/json
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="powershell"></a><span data-ttu-id="d1286-190">PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1286-190">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="d1286-191">U kunt de [PowerShell Partner Center module gebruiken om](https://www.powershellgallery.com/packages/PartnerCenter) de vereiste infrastructuur te verminderen voor het uitwisselen van een autorisatiecode voor een toegangs token.</span><span class="sxs-lookup"><span data-stu-id="d1286-191">You can use the [Partner Center PowerShell module](https://www.powershellgallery.com/packages/PartnerCenter) to reduce the required infrastructure to exchange an authorization code for an access token.</span></span> <span data-ttu-id="d1286-192">Deze methode is optioneel voor het maken van [Partner Center REST-aanroepen.](#rest)</span><span class="sxs-lookup"><span data-stu-id="d1286-192">This method is optional for making [Partner Center REST calls](#rest).</span></span>

<span data-ttu-id="d1286-193">Zie PowerShell-documentatie voor [Secure App Model](/powershell/partnercenter/secure-app-model) voor meer informatie over dit proces.</span><span class="sxs-lookup"><span data-stu-id="d1286-193">For more information on this process, see [Secure App Model](/powershell/partnercenter/secure-app-model) PowerShell documentation.</span></span>

1. <span data-ttu-id="d1286-194">Installeer de Azure AD- en Partner Center PowerShell-modules.</span><span class="sxs-lookup"><span data-stu-id="d1286-194">Install the Azure AD and Partner Center PowerShell modules.</span></span>

    ```powershell
    Install-Module AzureAD
    ```

    ```powershell
    Install-Module PartnerCenter
    ```

2. <span data-ttu-id="d1286-195">Gebruik de **[opdracht New-PartnerAccessToken](/powershell/module/partnercenter/new-partneraccesstoken)** om het toestemmingsproces uit te voeren en het vereiste vernieuwingstoken vast te leggen.</span><span class="sxs-lookup"><span data-stu-id="d1286-195">Use the **[New-PartnerAccessToken](/powershell/module/partnercenter/new-partneraccesstoken)** command to perform the consent process and capture the required refresh token.</span></span>

    ```powershell
    $credential = Get-Credential

    $token = New-PartnerAccessToken -ApplicationId 'xxxx-xxxx-xxxx-xxxx' -Scopes 'https://api.partnercenter.microsoft.com/user_impersonation' -ServicePrincipal -Credential $credential -Tenant 'yyyy-yyyy-yyyy-yyyy' -UseAuthorizationCode
    ```

    > [!NOTE]
    > <span data-ttu-id="d1286-196">De **parameter ServicePrincipal** wordt gebruikt met de **opdracht New-PartnerAccessToken** omdat er een Azure AD-app met een type **web/API** wordt gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d1286-196">The **ServicePrincipal** parameter is used with the **New-PartnerAccessToken** command because an Azure AD app with a type of **Web/API** is being used.</span></span> <span data-ttu-id="d1286-197">Dit type app vereist dat een client-id en -geheim worden opgenomen in de toegangs-tokenaanvraag.</span><span class="sxs-lookup"><span data-stu-id="d1286-197">This type of app requires that a client identifier and secret be included in the access token request.</span></span> <span data-ttu-id="d1286-198">Wanneer de **opdracht Get-Credential** wordt aangeroepen, wordt u gevraagd een gebruikersnaam en wachtwoord in te voeren.</span><span class="sxs-lookup"><span data-stu-id="d1286-198">When the **Get-Credential** command is invoked, you will be prompted to enter a username and password.</span></span> <span data-ttu-id="d1286-199">Voer de toepassings-id in als de gebruikersnaam.</span><span class="sxs-lookup"><span data-stu-id="d1286-199">Enter the application identifier as the username.</span></span> <span data-ttu-id="d1286-200">Voer het toepassingsgeheim in als het wachtwoord.</span><span class="sxs-lookup"><span data-stu-id="d1286-200">Enter the application secret as the password.</span></span> <span data-ttu-id="d1286-201">Wanneer de **opdracht New-PartnerAccessToken** wordt aangeroepen, wordt u opnieuw gevraagd referenties in te voeren.</span><span class="sxs-lookup"><span data-stu-id="d1286-201">When the **New-PartnerAccessToken** command is invoked, you will be prompted to enter credentials again.</span></span> <span data-ttu-id="d1286-202">Voer de referenties in voor het serviceaccount dat u gebruikt.</span><span class="sxs-lookup"><span data-stu-id="d1286-202">Enter the credentials for the service account that you are using.</span></span> <span data-ttu-id="d1286-203">Dit serviceaccount moet een partneraccount zijn met de juiste machtigingen.</span><span class="sxs-lookup"><span data-stu-id="d1286-203">This service account should be a partner account with appropriate permissions.</span></span>

3. <span data-ttu-id="d1286-204">Kopieer de waarde van het vernieuwings token.</span><span class="sxs-lookup"><span data-stu-id="d1286-204">Copy the refresh token value.</span></span>

    ```powershell
    $token.RefreshToken | clip
    ```

<span data-ttu-id="d1286-205">U moet de waarde van het vernieuwingtoken opslaan in een beveiligde opslagplaats, zoals Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="d1286-205">You should store the refresh token value in a secure repository, such as Azure Key Vault.</span></span> <span data-ttu-id="d1286-206">Zie het artikel [Multi-Factor Authentication](/powershell/partnercenter/multi-factor-auth) voor meer informatie over het gebruik van de module voor beveiligde toepassingen met PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1286-206">For more information on how to leverage the secure application module with PowerShell, see the [multi-factor authentication](/powershell/partnercenter/multi-factor-auth) article.</span></span>
