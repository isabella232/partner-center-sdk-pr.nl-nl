---
title: Verificatie in Partnercentrum
description: Het partner centrum gebruikt Azure AD voor verificatie en voor het gebruik van de Api's van het partner centrum moet u uw verificatie-instellingen op de juiste wijze configureren.
ms.date: 11/13/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-csp
ms.openlocfilehash: 46ef9c6bc151c368281e943b7d24ebc07e34b66d
ms.sourcegitcommit: 64c498d3571f2287305968890578bc7396779621
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/19/2020
ms.locfileid: "97768689"
---
# <a name="partner-center-authentication"></a><span data-ttu-id="68841-103">Verificatie in Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="68841-103">Partner Center authentication</span></span>

<span data-ttu-id="68841-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="68841-104">**Applies to:**</span></span>

- <span data-ttu-id="68841-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="68841-105">Partner Center</span></span>
- <span data-ttu-id="68841-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="68841-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="68841-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="68841-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="68841-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="68841-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="68841-109">Partner Center maakt gebruik van Azure Active Directory voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="68841-109">Partner Center uses Azure Active Directory for authentication.</span></span> <span data-ttu-id="68841-110">Bij interactie met de API, SDK of PowerShell-module van Partner Center moet u op de juiste wijze een Azure AD-toepassing configureren en vervolgens een toegangstoken aanvragen.</span><span class="sxs-lookup"><span data-stu-id="68841-110">When interacting with the Partner Center API, SDK, or PowerShell module you must correctly configure an Azure AD application and then request an access token.</span></span> <span data-ttu-id="68841-111">Toegangs tokens die zijn verkregen met behulp van alleen app of app + gebruikers authenticatie, kunnen worden gebruikt met het partner centrum.</span><span class="sxs-lookup"><span data-stu-id="68841-111">Access tokens obtained using app only or app + user authentication can be used with the Partner Center.</span></span> <span data-ttu-id="68841-112">Er zijn echter twee belang rijke items die moeten worden overwogen</span><span class="sxs-lookup"><span data-stu-id="68841-112">However, there are two important items that need to be considered</span></span>

- <span data-ttu-id="68841-113">Gebruik multi-factor Authentication bij het openen van de partner centrum-API met behulp van app + gebruikers authenticatie.</span><span class="sxs-lookup"><span data-stu-id="68841-113">Use multi-factor authentication when accessing the Partner Center API using app + user authentication.</span></span> <span data-ttu-id="68841-114">Zie voor meer informatie over deze wijziging [veilig toepassings model inschakelen](enable-secure-app-model.md).</span><span class="sxs-lookup"><span data-stu-id="68841-114">For more information regarding this change, see [Enable secure application model](enable-secure-app-model.md).</span></span>

- <span data-ttu-id="68841-115">Niet alle bewerkingen van de partner centrum-API ondersteunen alleen app-verificatie.</span><span class="sxs-lookup"><span data-stu-id="68841-115">Not all of the operations the Partner Center API support app only authentication.</span></span> <span data-ttu-id="68841-116">Er zijn bepaalde scenario's waarin u app + gebruikers verificatie moet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="68841-116">There are certain scenarios where you'll be required to use app + user authentication.</span></span> <span data-ttu-id="68841-117">Onder de kop *vereisten* voor elk [artikel](scenarios.md)vindt u documentatie die aangeeft of alleen app-verificatie, app + gebruikers verificatie of beide worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="68841-117">Under the *Prerequisites* heading on each [article](scenarios.md), you'll find documentation that states whether app only authentication, app + user authentication, or both are supported.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="68841-118">Eerste configuratie</span><span class="sxs-lookup"><span data-stu-id="68841-118">Initial setup</span></span>

1. <span data-ttu-id="68841-119">Om te beginnen, moet u ervoor zorgen dat u zowel een primair partner centrum-account als een integratie sandbox-partner centrum-account hebt.</span><span class="sxs-lookup"><span data-stu-id="68841-119">To begin, you need to make sure that you have both a primary Partner Center account, and an integration sandbox Partner Center account.</span></span> <span data-ttu-id="68841-120">Zie voor meer informatie [Partner Center-accounts instellen voor API-toegang](set-up-api-access-in-partner-center.md).</span><span class="sxs-lookup"><span data-stu-id="68841-120">For more information, see [Set up Partner Center accounts for API access](set-up-api-access-in-partner-center.md).</span></span> <span data-ttu-id="68841-121">Noteer de registratie-ID van de Azure AAD-app en het geheim (client geheim is vereist voor het identificeren van alleen apps) voor zowel uw primaire account als uw sandbox-account voor integratie.</span><span class="sxs-lookup"><span data-stu-id="68841-121">Make note of the Azure AAD App registration ID and Secret (client secret is required for App only identification) for both your primary account and your integration sandbox account.</span></span>

2. <span data-ttu-id="68841-122">Meld u aan bij Azure AD vanuit het Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="68841-122">Sign in to Azure AD from the Azure portal.</span></span> <span data-ttu-id="68841-123">Stel **in machtigingen voor andere toepassingen** machtigingen voor **Windows-Azure Active Directory** in op **gedelegeerde machtigingen** en selecteer beide **toegang tot de map als de aangemelde gebruiker** en meld u aan **en het gebruikers profiel lezen**.</span><span class="sxs-lookup"><span data-stu-id="68841-123">In **permissions to other applications**, set permissions for **Windows Azure Active Directory** to **Delegated Permissions**, and select both **Access the directory as the signed-in user** and **Sign in and read user profile**.</span></span>

3. <span data-ttu-id="68841-124">Voeg in het Azure Portal **toepassing toe**.</span><span class="sxs-lookup"><span data-stu-id="68841-124">In the Azure portal, **Add application**.</span></span> <span data-ttu-id="68841-125">Zoek naar ' micro soft Partner Center ', een micro soft Partner Center-toepassing.</span><span class="sxs-lookup"><span data-stu-id="68841-125">Search for "Microsoft Partner Center", which is the Microsoft Partner Center application.</span></span> <span data-ttu-id="68841-126">Stel de **gedelegeerde machtigingen** in op **toegang tot de partner centrum-API**.</span><span class="sxs-lookup"><span data-stu-id="68841-126">Set the **Delegated Permissions** to **Access Partner Center API**.</span></span> <span data-ttu-id="68841-127">Als u gebruikmaakt van partner Center voor Microsoft Cloud Duitsland of partner centrum voor Microsoft Cloud voor de Amerikaanse overheid, is deze stap verplicht.</span><span class="sxs-lookup"><span data-stu-id="68841-127">If you are using Partner Center for Microsoft Cloud Germany or Partner Center for Microsoft Cloud for US Government, this step is mandatory.</span></span> <span data-ttu-id="68841-128">Als u het globale exemplaar van partner Center gebruikt, is deze stap optioneel.</span><span class="sxs-lookup"><span data-stu-id="68841-128">If you are using Partner Center global instance, this step is optional.</span></span> <span data-ttu-id="68841-129">CSP-partners kunnen de functie voor app-beheer in de partner centrum Portal gebruiken om deze stap over te slaan voor het globale exemplaar van partner Center.</span><span class="sxs-lookup"><span data-stu-id="68841-129">CSP Partners can use the App Management feature in the Partner Center portal to bypass this step for Partner Center global instance.</span></span>

## <a name="app-only-authentication"></a><span data-ttu-id="68841-130">Alleen app-verificatie</span><span class="sxs-lookup"><span data-stu-id="68841-130">App-only authentication</span></span>

<span data-ttu-id="68841-131">Als u alleen app-verificatie wilt gebruiken om toegang te krijgen tot het partner centrum REST API, .NET API, Java API of Power shell-module, kunt u dit doen door gebruik te maken van de volgende instructies.</span><span class="sxs-lookup"><span data-stu-id="68841-131">If you would like to use app-only authentication to access the Partner Center REST API, .NET API, Java API, or PowerShell module then you can do so by leveraging the following instructions.</span></span>

## <a name="net-app-only-authentication"></a><span data-ttu-id="68841-132">.NET (alleen app-verificatie)</span><span class="sxs-lookup"><span data-stu-id="68841-132">.NET (app-only authentication)</span></span>

```csharp
public static IAggregatePartner GetPartnerCenterTokenUsingAppCredentials()
{
    IPartnerCredentials partnerCredentials =
        PartnerCredentials.Instance.GenerateByApplicationCredentials(
            PartnerApplicationConfiguration.ApplicationId,
            PartnerApplicationConfiguration.ApplicationSecret,
            PartnerApplicationConfiguration.ApplicationDomain);

    // Create operations instance with partnerCredentials.
    return PartnerService.Instance.CreatePartnerOperations(partnerCredentials);
}
```

## <a name="java-app-only-authentication"></a><span data-ttu-id="68841-133">Java (alleen app-verificatie)</span><span class="sxs-lookup"><span data-stu-id="68841-133">Java (app-only authentication)</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

```java
public IAggregatePartner getAppPartnerOperations()
{
    IPartnerCredentials appCredentials =
        PartnerCredentials.getInstance().generateByApplicationCredentials(
        PartnerApplicationConfiguration.getApplicationId(),
        PartnerApplicationConfiguration.getApplicationSecret(),
        PartnerApplicationConfiguration.getApplicationDomain());

    return PartnerService.getInstance().createPartnerOperations( appCredentials );
}
```

## <a name="rest-app-only-authentication"></a><span data-ttu-id="68841-134">REST (alleen app-verificatie)</span><span class="sxs-lookup"><span data-stu-id="68841-134">REST (app-only authentication)</span></span>

### <a name="rest-request"></a><span data-ttu-id="68841-135">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="68841-135">REST request</span></span>

```http
POST https://login.microsoftonline.com/{tenantId}/oauth2/token HTTP/1.1
Accept: application/json
return-client-request-id: true
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Host: login.microsoftonline.com
Content-Length: 194
Expect: 100-continue

resource=https%3A%2F%2Fgraph.windows.net&client_id={client-id-here}&client_secret={client-secret-here}&grant_type=client_credentials
```

### <a name="rest-response"></a><span data-ttu-id="68841-136">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="68841-136">REST response</span></span>

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Pragma: no-cache
Content-Type: application/json; charset=utf-8
Expires: -1
Content-Length: 1406

{"token_type":"Bearer","expires_in":"3600","ext_expires_in":"3600","expires_on":"1546469802","not_before":"1546465902","resource":"https://graph.windows.net","access_token":"value-has-been-removed"}
```

## <a name="app--user-authentication"></a><span data-ttu-id="68841-137">App + gebruikers authenticatie</span><span class="sxs-lookup"><span data-stu-id="68841-137">App + User authentication</span></span>

<span data-ttu-id="68841-138">In het verleden is de toewijzing van het [wacht woord](https://tools.ietf.org/html/rfc6749#section-4.3) voor de resource-eigenaar gebruikt om een toegangs token aan te vragen voor gebruik met het Partner centrum rest API, .net API, Java API of Power shell-module.</span><span class="sxs-lookup"><span data-stu-id="68841-138">Historically the [resource owner password credentials grant](https://tools.ietf.org/html/rfc6749#section-4.3) has been used to request an access token for use with the Partner Center REST API, .NET API, Java API, or PowerShell module.</span></span> <span data-ttu-id="68841-139">Deze methode is gebruikt om een toegangs token aan te vragen bij Azure Active Directory met behulp van een client-id en gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="68841-139">That method was used to request an access token from Azure Active Directory using a client identifier and user credentials.</span></span> <span data-ttu-id="68841-140">Deze benadering werkt echter niet meer omdat het partner centrum multi-factor Authentication vereist, wanneer u app + gebruikers authenticatie gebruikt.</span><span class="sxs-lookup"><span data-stu-id="68841-140">However, this approach will no longer work because Partner Center requires multi-factor authentication, when using app + user authentication.</span></span> <span data-ttu-id="68841-141">Om te voldoen aan deze vereiste heeft micro soft een veilig, schaalbaar Framework geïntroduceerd voor het verifiëren van de CSP-partners (Cloud Solution Provider) en leveranciers van het configuratie scherm (CPV) met multi-factor Authentication.</span><span class="sxs-lookup"><span data-stu-id="68841-141">To comply with this requirement Microsoft has introduced a secure, scalable framework for authenticating Cloud Solution Provider (CSP) partners and control panel vendors (CPV) using multi-factor authentication.</span></span> <span data-ttu-id="68841-142">Dit framework wordt het beveiligde toepassings model genoemd en bestaat uit een toestemmings proces en een aanvraag voor een toegangs token met behulp van een vernieuwings token.</span><span class="sxs-lookup"><span data-stu-id="68841-142">This framework is known as the Secure Application Model, and it is composed of a consent process and a request for an access token using a refresh token.</span></span>

### <a name="partner-consent"></a><span data-ttu-id="68841-143">Partner toestemming</span><span class="sxs-lookup"><span data-stu-id="68841-143">Partner consent</span></span>

<span data-ttu-id="68841-144">Het partner toestemmings proces is een interactief proces waarbij de partner zich verifieert met multi-factor Authentication, wordt gestemd op de toepassing en een vernieuwings token wordt opgeslagen in een beveiligde opslag plaats, zoals Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="68841-144">The partner consent process is an interactive process where the partner authenticates using multi-factor authentication, consents to the application, and a refresh token is stored in a secure repository such as Azure Key Vault.</span></span> <span data-ttu-id="68841-145">U kunt het beste een toegewezen account voor integratie doeleinden gebruiken voor dit proces.</span><span class="sxs-lookup"><span data-stu-id="68841-145">We recommend that a dedicated account for integration purposes be used for this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="68841-146">De juiste multi-factor Authentication-oplossing moet zijn ingeschakeld voor het service account dat wordt gebruikt in het partner toestemmings proces.</span><span class="sxs-lookup"><span data-stu-id="68841-146">The appropriate multi-factor authentication solution should be enabled for the service account used in the partner consent process.</span></span> <span data-ttu-id="68841-147">Als dat niet het geval is, voldoet het resulterende vernieuwings token niet aan de beveiligings vereisten.</span><span class="sxs-lookup"><span data-stu-id="68841-147">If it isn't then the resulting refresh token will not be compliant with security requirements.</span></span>

### <a name="samples-for-app--user-authentication"></a><span data-ttu-id="68841-148">Voor beelden voor app + gebruikers verificatie</span><span class="sxs-lookup"><span data-stu-id="68841-148">Samples for App + User authentication</span></span>

<span data-ttu-id="68841-149">Het proces voor partner toestemming kan op verschillende manieren worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="68841-149">The partner consent process can be performed in a number of ways.</span></span> <span data-ttu-id="68841-150">We hebben de volgende voor beelden ontwikkeld om partners te helpen begrijpen hoe ze elke vereiste bewerking uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="68841-150">To help partners understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="68841-151">Wanneer u de juiste oplossing in uw omgeving implementeert, is het belang rijk dat u een oplossing ontwikkelt die een klacht vormt voor uw coderings standaarden en beveiligings beleid.</span><span class="sxs-lookup"><span data-stu-id="68841-151">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-appuser-authentication"></a><span data-ttu-id="68841-152">.NET (app + gebruikers verificatie)</span><span class="sxs-lookup"><span data-stu-id="68841-152">.NET (app+user authentication)</span></span>

<span data-ttu-id="68841-153">Het voorbeeld project van de [partner toestemming](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) laat zien hoe u een website kunt gebruiken die is ontwikkeld met ASP.net om toestemming vast te leggen, een vernieuwings token aan te vragen en het veilig op te slaan in azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="68841-153">The [partner consent](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) sample project demonstrates how to utilize a website developed using ASP.NET to capture consent, request a refresh token, and securely store it in Azure Key Vault.</span></span> <span data-ttu-id="68841-154">Voer de volgende stappen uit om de vereiste onderdelen voor dit voor beeld te maken.</span><span class="sxs-lookup"><span data-stu-id="68841-154">Perform the following steps to create the required prerequisites for this sample.</span></span>

1. <span data-ttu-id="68841-155">Maak een instantie van Azure Key Vault met behulp van de Azure Portal of de volgende Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="68841-155">Create an instance of Azure Key Vault using the Azure portal or the following PowerShell commands.</span></span> <span data-ttu-id="68841-156">Voordat u de opdracht uitvoert, moet u ervoor zorgen dat u de parameter waarden dienovereenkomstig wijzigt.</span><span class="sxs-lookup"><span data-stu-id="68841-156">Before executing the command, be sure to modify the parameter values accordingly.</span></span> <span data-ttu-id="68841-157">De naam van de kluis moet uniek zijn.</span><span class="sxs-lookup"><span data-stu-id="68841-157">The vault name must be unique.</span></span>

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    <span data-ttu-id="68841-158">Voor meer informatie over het maken van een Azure Key Vault raadpleegt [u Quick Start: een geheim instellen en ophalen uit Azure Key Vault met behulp van de Azure Portal](/azure/key-vault/quick-create-portal) of [Quick Start: een geheim instellen en ophalen uit Azure Key Vault met behulp van Power shell](/azure/key-vault/quick-create-powershell).</span><span class="sxs-lookup"><span data-stu-id="68841-158">For more information about creating an Azure Key Vault, see [Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/quick-create-portal) or [Quickstart: Set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span></span> <span data-ttu-id="68841-159">Stel vervolgens een geheim in en haal het op.</span><span class="sxs-lookup"><span data-stu-id="68841-159">Then set and retrieve a secret.</span></span>

2. <span data-ttu-id="68841-160">Maak een Azure AD-toepassing en een sleutel met behulp van de Azure Portal of de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="68841-160">Create an Azure AD Application and a key using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    <span data-ttu-id="68841-161">Noteer de toepassings-id en geheime waarden, omdat deze worden gebruikt in de onderstaande stappen.</span><span class="sxs-lookup"><span data-stu-id="68841-161">Be sure to make note of the application identifier and secret values because they'll be used in the steps below.</span></span>

3. <span data-ttu-id="68841-162">Verleen de nieuwe Azure AD-toepassing de machtigingen lezen geheimen met de Azure Portal of de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="68841-162">Grant the newly create Azure AD application the read secrets permissions using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. <span data-ttu-id="68841-163">Maak een Azure AD-toepassing die is geconfigureerd voor partner centrum.</span><span class="sxs-lookup"><span data-stu-id="68841-163">Create an Azure AD application that is configured for Partner Center.</span></span> <span data-ttu-id="68841-164">Voer de volgende acties uit om deze stap te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="68841-164">Perform the following actions to complete this step.</span></span>

    - <span data-ttu-id="68841-165">Blader naar de [app Management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) -functie van het dash board van de partner centrum</span><span class="sxs-lookup"><span data-stu-id="68841-165">Browse to the [App management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) feature of the Partner Center Dashboard</span></span>
    - <span data-ttu-id="68841-166">Klik op *nieuwe web-app toevoegen* om een nieuwe Azure AD-toepassing te maken.</span><span class="sxs-lookup"><span data-stu-id="68841-166">Click *Add new web app* to create a new Azure AD application.</span></span>

    <span data-ttu-id="68841-167">Zorg ervoor dat u de *App-ID*, \* account-id \* \* en *sleutel* waarden documenteert, omdat deze worden gebruikt in de onderstaande stappen.</span><span class="sxs-lookup"><span data-stu-id="68841-167">Be sure to document the *App ID*, \*Account ID\*\*, and *Key* values because they'll be used in the steps below.</span></span>

5. <span data-ttu-id="68841-168">Kloon de opslag plaats [Partner-Center-DotNet-samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met behulp van Visual Studio of de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="68841-168">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command.</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

6. <span data-ttu-id="68841-169">Open het *PartnerConsent* -project dat in de map is gevonden `Partner-Center-DotNet-Samples\secure-app-model\keyvault` .</span><span class="sxs-lookup"><span data-stu-id="68841-169">Open the *PartnerConsent* project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

7. <span data-ttu-id="68841-170">Vul de toepassings instellingen in de [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)</span><span class="sxs-lookup"><span data-stu-id="68841-170">Populate the application settings found in the [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)</span></span>

    ```xml
    <!-- AppID that represents CSP application -->
    <add key="ida:CSPApplicationId" value="" />
    <!--
        Please use certificate as your client secret and deploy the certificate to your environment.
        The following application secret is for sample application only. please do not use secret directly from the config file.
    -->
    <add key="ida:CSPApplicationSecret" value="" />

    <!--
        Endpoint address for the instance of Azure KeyVault. This is
        the DNS Name for the instance of Key Vault that you provisioned.
     -->
    <add key="KeyVaultEndpoint" value="" />

    <!-- App ID that is given access for KeyVault to store refresh tokens -->
    <add key="ida:KeyVaultClientId" value="" />

    <!--
        Please use certificate as your client secret and deploy the certificate
        to your environment. The following application secret is for sample
        application only. please do not use secret directly from the config file.
    -->
    <add key="ida:KeyVaultClientSecret" value="" />
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="68841-171">Gevoelige informatie, zoals toepassings geheimen, mag niet worden opgeslagen in configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="68841-171">Sensitive information such as application secrets should not be stored in configuration files.</span></span> <span data-ttu-id="68841-172">U hebt dit gedaan omdat dit een voorbeeld toepassing is.</span><span class="sxs-lookup"><span data-stu-id="68841-172">It was done here because this is a sample application.</span></span> <span data-ttu-id="68841-173">Met uw productie toepassing wordt u ten zeerste aangeraden authenticatie op basis van certificaten te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="68841-173">With your production application we strongly recommend that you use certificate-based authentication.</span></span> <span data-ttu-id="68841-174">Zie [certificaat referenties voor toepassings verificatie]( /azure/active-directory/develop/active-directory-certificate-credentials)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="68841-174">For more information, see [Certificate credentials for application authentication]( /azure/active-directory/develop/active-directory-certificate-credentials).</span></span>

8. <span data-ttu-id="68841-175">Wanneer u dit voorbeeld project uitvoert, wordt u gevraagd om te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="68841-175">When you run this sample project, it will prompt you for authentication.</span></span> <span data-ttu-id="68841-176">Nadat de verificatie is geslaagd, wordt een toegangs token aangevraagd bij Azure AD.</span><span class="sxs-lookup"><span data-stu-id="68841-176">After successfully authenticating, an access token is requested from Azure AD.</span></span> <span data-ttu-id="68841-177">De informatie die wordt geretourneerd door Azure AD bevat een vernieuwings token dat is opgeslagen in het geconfigureerde exemplaar van Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="68841-177">The information returned from Azure AD includes a refresh token that is stored in the configured instance of Azure Key Vault.</span></span>

## <a name="java-appuser-authentication"></a><span data-ttu-id="68841-178">Java (app + gebruikers verificatie)</span><span class="sxs-lookup"><span data-stu-id="68841-178">Java (app+user authentication)</span></span>

<span data-ttu-id="68841-179">Het voorbeeld project van de [partner toestemming](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) laat zien hoe u een website kunt gebruiken die is ontwikkeld met JSP om toestemming vast te leggen, een vernieuwings token aan te vragen en een beveiligde Store te gebruiken in azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="68841-179">The [partner consent](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) sample project demonstrates how to utilize a website developed using JSP to capture consent, request a refresh token, and secure store in Azure Key Vault.</span></span> <span data-ttu-id="68841-180">Voer de volgende stappen uit om de vereiste onderdelen voor dit voor beeld te maken.</span><span class="sxs-lookup"><span data-stu-id="68841-180">Perform the following to create the required prerequisites for this sample.</span></span>

1. <span data-ttu-id="68841-181">Maak een instantie van Azure Key Vault met behulp van de Azure Portal of de volgende Power shell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="68841-181">Create an instance of Azure Key Vault using the Azure portal or the following PowerShell commands.</span></span> <span data-ttu-id="68841-182">Voordat u de opdracht uitvoert, moet u ervoor zorgen dat u de parameter waarden dienovereenkomstig wijzigt.</span><span class="sxs-lookup"><span data-stu-id="68841-182">Before executing the command, be sure to modify the parameter values accordingly.</span></span> <span data-ttu-id="68841-183">De naam van de kluis moet uniek zijn.</span><span class="sxs-lookup"><span data-stu-id="68841-183">The vault name must be unique.</span></span>

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    <span data-ttu-id="68841-184">Voor meer informatie over het maken van een Azure Key Vault raadpleegt [u Quick Start: een geheim instellen en ophalen uit Azure Key Vault met behulp van de Azure Portal](/azure/key-vault/quick-create-portal) of [Quick Start: een geheim instellen en ophalen uit Azure Key Vault met behulp van Power shell](/azure/key-vault/quick-create-powershell).</span><span class="sxs-lookup"><span data-stu-id="68841-184">For more information about creating an Azure Key Vault, see [Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/quick-create-portal) or [Quickstart: Set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span></span>

2. <span data-ttu-id="68841-185">Maak een Azure AD-toepassing en een sleutel met behulp van de Azure Portal of de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="68841-185">Create an Azure AD Application and a key using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    <span data-ttu-id="68841-186">Zorg ervoor dat u de toepassings-id en geheime waarden documenteert, omdat deze worden gebruikt in de onderstaande stappen.</span><span class="sxs-lookup"><span data-stu-id="68841-186">Be sure to document the application identifier and secret values because they'll be used in the steps below.</span></span>

3. <span data-ttu-id="68841-187">Ken de zojuist gemaakte Azure AD-toepassing de machtigingen lezen geheimen toe met behulp van de Azure Portal of de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="68841-187">Grant the newly created Azure AD application the read secrets permissions using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. <span data-ttu-id="68841-188">Maak een Azure AD-toepassing die is geconfigureerd voor partner centrum.</span><span class="sxs-lookup"><span data-stu-id="68841-188">Create an Azure AD application that is configured for Partner Center.</span></span> <span data-ttu-id="68841-189">Voer de volgende stappen uit om deze stap te volt ooien.</span><span class="sxs-lookup"><span data-stu-id="68841-189">Perform the following to complete this step.</span></span>

    - <span data-ttu-id="68841-190">Blader naar de [app Management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) -functie van het dash board van de partner centrum</span><span class="sxs-lookup"><span data-stu-id="68841-190">Browse to the [App management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) feature of the Partner Center Dashboard</span></span>
    - <span data-ttu-id="68841-191">Klik op *nieuwe web-app toevoegen* om een nieuwe Azure AD-toepassing te maken.</span><span class="sxs-lookup"><span data-stu-id="68841-191">Click *Add new web app* to create a new Azure AD application.</span></span>

    <span data-ttu-id="68841-192">Zorg ervoor dat u de *App-ID*, \* account-id \* \* en *sleutel* waarden documenteert, omdat deze worden gebruikt in de onderstaande stappen.</span><span class="sxs-lookup"><span data-stu-id="68841-192">Be sure to document the *App ID*, \*Account ID\*\*, and *Key* values because they'll be used in the steps below.</span></span>

5. <span data-ttu-id="68841-193">Kloon de opslag plaats van de [Partner-Center-Java-voor beelden](https://github.com/Microsoft/Partner-Center-Java-Samples) met de volgende opdracht</span><span class="sxs-lookup"><span data-stu-id="68841-193">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

6. <span data-ttu-id="68841-194">Open het *PartnerConsent* -project dat in de map is gevonden `Partner-Center-Java-Samples\secure-app-model\keyvault` .</span><span class="sxs-lookup"><span data-stu-id="68841-194">Open the *PartnerConsent* project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

7. <span data-ttu-id="68841-195">Vul de toepassings instellingen in het [web.xml](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml) bestand in</span><span class="sxs-lookup"><span data-stu-id="68841-195">Populate the application settings found in the [web.xml](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml) file</span></span>

    ```xml
    <filter>
        <filter-name>AuthenticationFilter</filter-name>
        <filter-class>com.microsoft.store.samples.partnerconsent.security.AuthenticationFilter</filter-class>
        <init-param>
            <param-name>client_id</param-name>
            <param-value></param-value>
        </init-param>
        <init-param>
            <param-name>client_secret</param-name>
            <param-value></param-value>
        </init-param>
        <init-param>
            <param-name>keyvault_base_url</param-name>
            <param-value></param-value>
        </init-param>
        <init-param>
            <param-name>keyvault_client_id</param-name>
            <param-value></param-value>
        </init-param>
        <init-param>
            <param-name>keyvault_client_secret</param-name>
            <param-value></param-value>
        </init-param>
        <init-param>
            <param-name>keyvault_certifcate_path</param-name>
            <param-value></param-value>
        </init-param>
    </filter>
    ```

    > [!IMPORTANT]
    > <span data-ttu-id="68841-196">Gevoelige informatie, zoals toepassings geheimen, mag niet worden opgeslagen in configuratie bestanden.</span><span class="sxs-lookup"><span data-stu-id="68841-196">Sensitive information such as application secrets should not be stored in configurations files.</span></span> <span data-ttu-id="68841-197">U hebt dit gedaan omdat dit een voorbeeld toepassing is.</span><span class="sxs-lookup"><span data-stu-id="68841-197">It was done here because this is a sample application.</span></span> <span data-ttu-id="68841-198">Met uw productie toepassing wordt u ten zeerste aangeraden authenticatie op basis van certificaten te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="68841-198">With your production application, we strongly recommend that you use certificate based authenticate.</span></span> <span data-ttu-id="68841-199">Zie [Key Vault-certificaat verificatie](https://github.com/Azure-Samples/key-vault-java-certificate-authentication)voor meer informatie.</span><span class="sxs-lookup"><span data-stu-id="68841-199">For more information, see [Key Vault Certificate authentication](https://github.com/Azure-Samples/key-vault-java-certificate-authentication).</span></span>

8. <span data-ttu-id="68841-200">Wanneer u dit voorbeeld project uitvoert, wordt u gevraagd om te verifiëren.</span><span class="sxs-lookup"><span data-stu-id="68841-200">When you run this sample project, it will prompt you for authentication.</span></span> <span data-ttu-id="68841-201">Nadat de verificatie is geslaagd, wordt een toegangs token aangevraagd bij Azure AD.</span><span class="sxs-lookup"><span data-stu-id="68841-201">After successfully authenticating, an access token is requested from Azure AD.</span></span> <span data-ttu-id="68841-202">De informatie die wordt geretourneerd door Azure AD bevat een vernieuwings token dat is opgeslagen in het geconfigureerde exemplaar van Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="68841-202">The information returned from Azure AD includes a refresh token that is stored in the configured instance of Azure Key Vault.</span></span>

## <a name="cloud-solution-provider-authentication"></a><span data-ttu-id="68841-203">Verificatie van Cloud Solution Provider</span><span class="sxs-lookup"><span data-stu-id="68841-203">Cloud Solution Provider authentication</span></span>

<span data-ttu-id="68841-204">Partners van Cloud solution providers kunnen het vernieuwings token gebruiken dat is verkregen via het [partner toestemmings](#partner-consent) proces.</span><span class="sxs-lookup"><span data-stu-id="68841-204">Cloud Solution Provider partners can use the refresh token obtained through the [partner consent](#partner-consent) process.</span></span>

### <a name="samples-for-cloud-solution-provider-authentication"></a><span data-ttu-id="68841-205">Voor beelden voor Cloud Solution Provider-verificatie</span><span class="sxs-lookup"><span data-stu-id="68841-205">Samples for Cloud Solution Provider authentication</span></span>

<span data-ttu-id="68841-206">We hebben de volgende voor beelden ontwikkeld om partners te helpen begrijpen hoe ze elke vereiste bewerking uit te voeren.</span><span class="sxs-lookup"><span data-stu-id="68841-206">To help partners understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="68841-207">Wanneer u de juiste oplossing in uw omgeving implementeert, is het belang rijk dat u een oplossing ontwikkelt die een klacht vormt voor uw coderings standaarden en beveiligings beleid.</span><span class="sxs-lookup"><span data-stu-id="68841-207">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-csp-authentication"></a><span data-ttu-id="68841-208">.NET (CSP-verificatie)</span><span class="sxs-lookup"><span data-stu-id="68841-208">.NET (CSP authentication)</span></span>

1. <span data-ttu-id="68841-209">Als u dit nog niet hebt gedaan, voert u het [partner toestemmings proces](#partner-consent)uit.</span><span class="sxs-lookup"><span data-stu-id="68841-209">If you have not already done so, perform the [partner consent process](#partner-consent).</span></span>

2. <span data-ttu-id="68841-210">Kloon de opslag plaats [Partner-Center-DotNet-samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met Visual Studio of de volgende opdracht</span><span class="sxs-lookup"><span data-stu-id="68841-210">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. <span data-ttu-id="68841-211">Open het `CSPApplication` project dat in de `Partner-Center-DotNet-Samples\secure-app-model\keyvault` map is gevonden.</span><span class="sxs-lookup"><span data-stu-id="68841-211">Open the `CSPApplication` project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="68841-212">Werk de toepassings instellingen in het [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config) bestand bij.</span><span class="sxs-lookup"><span data-stu-id="68841-212">Update the application settings found in the [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config) file.</span></span>

    ```xml
    <!-- AppID that represents CSP application -->
    <add key="ida:CSPApplicationId" value="" />
    <!--
        Please use certificate as your client secret and deploy the certificate to your environment.
        The following application secret is for sample application only. please do not use secret directly from the config file.
    -->
    <add key="ida:CSPApplicationSecret" value="" />

    <!-- Endpoint address for the instance of Azure KeyVault -->
    <add key="KeyVaultEndpoint" value="" />

    <!-- AppID that is given access for keyvault to store the refresh tokens -->
    <add key="ida:KeyVaultClientId" value="" />

    <!--
        Please use certificate as your client secret and deploy the certificate to your environment.
        The following application secret is for sample application only. please do not use secret directly from the config file.
    -->
    <add key="ida:KeyVaultClientSecret" value="" />
    ```

5. <span data-ttu-id="68841-213">Stel de juiste waarden in voor de variabelen **partner** en **CustomerId** in het [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs) -bestand.</span><span class="sxs-lookup"><span data-stu-id="68841-213">Set the appropriate values for the **PartnerId** and **CustomerId** variables found in the [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs) file.</span></span>

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. <span data-ttu-id="68841-214">Wanneer u dit voorbeeld project uitvoert, wordt het vernieuwings token opgehaald dat is verkregen tijdens het partner toestemmings proces.</span><span class="sxs-lookup"><span data-stu-id="68841-214">When you run this sample project, it obtains the refresh token obtained during the partner consent process.</span></span> <span data-ttu-id="68841-215">Vervolgens wordt een toegangs token aangevraagd om te communiceren met de Partner Center SDK voor de naam van de partner.</span><span class="sxs-lookup"><span data-stu-id="68841-215">Then, it requests an access token to interact with the Partner Center SDK on the partner's behalf.</span></span> <span data-ttu-id="68841-216">Ten slotte vraagt het een toegangs token om met Microsoft Graph namens de opgegeven klant te communiceren.</span><span class="sxs-lookup"><span data-stu-id="68841-216">Finally, it requests an access token to interact with Microsoft Graph on behalf of the specified customer.</span></span>

## <a name="java-csp-authentication"></a><span data-ttu-id="68841-217">Java (CSP-verificatie)</span><span class="sxs-lookup"><span data-stu-id="68841-217">Java (CSP authentication)</span></span>

1. <span data-ttu-id="68841-218">Als u dit nog niet hebt gedaan, voert u het [partner toestemmings proces](#partner-consent)uit.</span><span class="sxs-lookup"><span data-stu-id="68841-218">If you have not done so already, perform the [partner consent process](#partner-consent).</span></span>

2. <span data-ttu-id="68841-219">Kloon de opslag plaats van de [Partner-Center-Java-voor beelden](https://github.com/Microsoft/Partner-Center-Java-Samples) met Visual Studio of de volgende opdracht</span><span class="sxs-lookup"><span data-stu-id="68841-219">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. <span data-ttu-id="68841-220">Open het `cspsample` project dat in de `Partner-Center-Java-Samples\secure-app-model\keyvault` map is gevonden.</span><span class="sxs-lookup"><span data-stu-id="68841-220">Open the `cspsample` project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="68841-221">Werk de toepassings instellingen in het bestand [Application. Properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties) bij.</span><span class="sxs-lookup"><span data-stu-id="68841-221">Update the application settings found in the [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties) file.</span></span>

     ```java
    azuread.authority=https://login.microsoftonline.com
    keyvault.baseurl=
    keyvault.clientId=
    keyvault.clientSecret=
    partnercenter.accountId=
    partnercenter.clientId=
    partnercenter.clientSecret=
    ```

5. <span data-ttu-id="68841-222">Wanneer u dit voorbeeld project uitvoert, wordt het vernieuwings token opgehaald dat is verkregen tijdens het partner toestemmings proces.</span><span class="sxs-lookup"><span data-stu-id="68841-222">When you run this sample project, it obtains the refresh token obtained during the partner consent process.</span></span> <span data-ttu-id="68841-223">Vervolgens wordt een toegangs token aangevraagd om te communiceren met de Partner Center SDK voor de naam van de partner.</span><span class="sxs-lookup"><span data-stu-id="68841-223">Then, it requests an access token to interact with the Partner Center SDK on the partner's behalf.</span></span>

6. <span data-ttu-id="68841-224">Optioneel: Verwijder de *RunAzureTask* -en *RunGraphTask* -functie aanroepen als u wilt zien hoe u kunt communiceren met Azure Resource Manager en Microsoft Graph namens de klant.</span><span class="sxs-lookup"><span data-stu-id="68841-224">Optional - uncomment the *RunAzureTask* and *RunGraphTask* function calls if you want to see how to interact with Azure Resource Manager and Microsoft Graph on behalf of the customer.</span></span>

## <a name="control-panel-provider-authentication"></a><span data-ttu-id="68841-225">Verificatie van provider van configuratie scherm</span><span class="sxs-lookup"><span data-stu-id="68841-225">Control Panel Provider authentication</span></span>

<span data-ttu-id="68841-226">Leveranciers van het configuratie scherm moeten elke partner die ze ondersteunen de [partner toestemmings](#partner-consent) procedure uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="68841-226">Control panel vendors need to have each partner they support perform the [partner consent](#partner-consent) process.</span></span> <span data-ttu-id="68841-227">Zodra het vernieuwings token dat is verkregen via dat proces, wordt gebruikt om toegang te krijgen tot het partner centrum REST API en de .NET API.</span><span class="sxs-lookup"><span data-stu-id="68841-227">Once that is completed the refresh token obtained through that process is used to access the Partner Center REST API and .NET API.</span></span>

### <a name="samples-for-cloud-panel-provider-authentication"></a><span data-ttu-id="68841-228">Voor beelden voor verificatie van provider van Cloud paneel</span><span class="sxs-lookup"><span data-stu-id="68841-228">Samples for Cloud Panel Provider authentication</span></span>

<span data-ttu-id="68841-229">Om te helpen de leveranciers van het configuratie scherm begrijpen hoe elke vereiste bewerking moet worden uitgevoerd, hebben we de volgende voor beelden ontwikkeld.</span><span class="sxs-lookup"><span data-stu-id="68841-229">To help control panel vendors understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="68841-230">Wanneer u de juiste oplossing in uw omgeving implementeert, is het belang rijk dat u een oplossing ontwikkelt die een klacht vormt voor uw coderings standaarden en beveiligings beleid.</span><span class="sxs-lookup"><span data-stu-id="68841-230">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-cpv-authentication"></a><span data-ttu-id="68841-231">.NET (CPV-verificatie)</span><span class="sxs-lookup"><span data-stu-id="68841-231">.NET (CPV authentication)</span></span>

1. <span data-ttu-id="68841-232">Ontwikkel en implementeer een proces voor partners van Cloud solution providers om de juiste toestemming te geven.</span><span class="sxs-lookup"><span data-stu-id="68841-232">Develop and deploy a process for Cloud Solution Provider partners to provide the appropriate consent.</span></span> <span data-ttu-id="68841-233">Zie [partner instemming](#partner-consent)voor meer informatie over een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="68841-233">For more information an example, see [partner consent](#partner-consent).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="68841-234">Gebruikers referenties van een Cloud Solution Provider-partner mogen niet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="68841-234">User credentials from a Cloud Solution Provider partner should not be stored.</span></span> <span data-ttu-id="68841-235">Het vernieuwings token dat is verkregen via het partner toestemming proces moet worden opgeslagen en gebruikt om toegangs tokens aan te vragen voor interactie met een micro soft-API.</span><span class="sxs-lookup"><span data-stu-id="68841-235">The refresh token obtained through the partner consent process should be stored and used to request access tokens for interacting with any Microsoft API.</span></span>

2. <span data-ttu-id="68841-236">Kloon de opslag plaats [Partner-Center-DotNet-samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met Visual Studio of de volgende opdracht</span><span class="sxs-lookup"><span data-stu-id="68841-236">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. <span data-ttu-id="68841-237">Open het `CPVApplication` project dat in de `Partner-Center-DotNet-Samples\secure-app-model\keyvault` map is gevonden.</span><span class="sxs-lookup"><span data-stu-id="68841-237">Open the `CPVApplication` project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="68841-238">Werk de toepassings instellingen in het [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config) bestand bij.</span><span class="sxs-lookup"><span data-stu-id="68841-238">Update the application settings found in the [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config) file.</span></span>

    ```xml
    <!-- AppID that represents Control panel vendor application -->
    <add key="ida:CPVApplicationId" value="" />

    <!--
        Please use certificate as your client secret and deploy the certificate to your environment.
        The following application secret is for sample application only. please do not use secret directly from the config file.
    -->
    <add key="ida:CPVApplicationSecret" value="" />

    <!-- Endpoint address for the instance of Azure KeyVault -->
    <add key="KeyVaultEndpoint" value="" />

    <!-- AppID that is given access for keyvault to store the refresh tokens -->
    <add key="ida:KeyVaultClientId" value="" />

    <!--
        Please use certificate as your client secret and deploy the certificate to your environment.
        The following application secret is for sample application only. please do not use secret directly from the config file.
    -->
    <add key="ida:KeyVaultClientSecret" value="" />
    ```

5. <span data-ttu-id="68841-239">Stel de juiste waarden in voor de variabelen **partner** en **CustomerId** in het [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs) -bestand.</span><span class="sxs-lookup"><span data-stu-id="68841-239">Set the appropriate values for the **PartnerId** and **CustomerId** variables found in the [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs) file.</span></span>

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. <span data-ttu-id="68841-240">Wanneer u dit voorbeeld project uitvoert, wordt het vernieuwings token opgehaald voor de opgegeven partner.</span><span class="sxs-lookup"><span data-stu-id="68841-240">When you run this sample project, it obtains the refresh token for the specified partner.</span></span> <span data-ttu-id="68841-241">Vervolgens wordt een toegangs token aangevraagd om toegang te krijgen tot partner Center en Azure AD Graph namens de partner.</span><span class="sxs-lookup"><span data-stu-id="68841-241">Then, it requests an access token to access Partner Center and Azure AD Graph on behalf of the partner.</span></span> <span data-ttu-id="68841-242">De volgende taak die wordt uitgevoerd, is het verwijderen en maken van machtigings toekenningen in de Tenant van de klant.</span><span class="sxs-lookup"><span data-stu-id="68841-242">The next task it performs is the deletion and creation of permission grants into the customer tenant.</span></span> <span data-ttu-id="68841-243">Omdat er geen relatie is tussen de leverancier van het configuratie scherm en de klant, moeten deze machtigingen worden toegevoegd met behulp van de partner centrum-API.</span><span class="sxs-lookup"><span data-stu-id="68841-243">Since there's no relationship between the control panel vendor and the customer, these permissions need to be added using the Partner Center API.</span></span> <span data-ttu-id="68841-244">In het volgende voor beeld ziet u hoe u dit kunt doen.</span><span class="sxs-lookup"><span data-stu-id="68841-244">The following example shows how to accomplish that.</span></span>

    ```csharp
    JObject contents = new JObject
    {
        // Provide your application display name
        ["displayName"] = "CPV Marketplace",

        // Provide your application id
        ["applicationId"] = CPVApplicationId,

        // Provide your application grants
        ["applicationGrants"] = new JArray(
            JObject.Parse("{\"enterpriseApplicationId\": \"00000002-0000-0000-c000-000000000000\", \"scope\":\"Domain.ReadWrite.All,User.ReadWrite.All,Directory.Read.All\"}"), // for Azure AD Graph access,  Directory.Read.All
            JObject.Parse("{\"enterpriseApplicationId\": \"797f4846-ba00-4fd7-ba43-dac1f8f63013\", \"scope\":\"user_impersonation\"}")) // for Azure Resource Manager access
    };

    /**
     * The following steps have to be performed once per customer tenant if your application is
     * a control panel vendor application and requires customer tenant Azure AD Graph access.
     **/

    // delete the previous grant into customer tenant
    JObject consentDeletion = await ApiCalls.DeleteAsync(
        tokenPartnerResult.Item1,
        string.Format("https://api.partnercenter.microsoft.com/v1/customers/{0}/applicationconsents/{1}", CustomerId, CPVApplicationId));

    // create new grants for the application given the setting in application grants payload.
    JObject consentCreation = await ApiCalls.PostAsync(
        tokenPartnerResult.Item1,
        string.Format("https://api.partnercenter.microsoft.com/v1/customers/{0}/applicationconsents", CustomerId),
        contents.ToString());
    ```

<span data-ttu-id="68841-245">Nadat deze machtigingen zijn vastgesteld, voert het voor beeld bewerkingen uit met Azure AD Graph namens de klant.</span><span class="sxs-lookup"><span data-stu-id="68841-245">After these permissions have been established, the sample performs operations using Azure AD Graph on behalf of the customer.</span></span>

## <a name="java-cpv-authentication"></a><span data-ttu-id="68841-246">Java (CPV-verificatie)</span><span class="sxs-lookup"><span data-stu-id="68841-246">Java (CPV authentication)</span></span>

1. <span data-ttu-id="68841-247">Ontwikkel en implementeer een proces voor partners van Cloud solution providers om de juiste toestemming te geven.</span><span class="sxs-lookup"><span data-stu-id="68841-247">Develop and deploy a process for Cloud Solution Provider partners to provide the appropriate consent.</span></span> <span data-ttu-id="68841-248">Zie de [partner toestemming](#partner-consent)voor meer informatie en een voor beeld.</span><span class="sxs-lookup"><span data-stu-id="68841-248">For more information and an example, see the [partner consent](#partner-consent).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="68841-249">Gebruikers referenties van een Cloud Solution Provider-partner mogen niet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="68841-249">User credentials from a Cloud Solution Provider partner should not be stored.</span></span> <span data-ttu-id="68841-250">Het vernieuwings token dat is verkregen via het partner toestemming proces moet worden opgeslagen en gebruikt om toegangs tokens aan te vragen voor interactie met een micro soft-API.</span><span class="sxs-lookup"><span data-stu-id="68841-250">The refresh token obtained through the partner consent process should be stored and used to request access tokens for interacting with any Microsoft API.</span></span>

2. <span data-ttu-id="68841-251">Kloon de opslag plaats van de [Partner-Center-Java-voor beelden](https://github.com/Microsoft/Partner-Center-Java-Samples) met de volgende opdracht</span><span class="sxs-lookup"><span data-stu-id="68841-251">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. <span data-ttu-id="68841-252">Open het `cpvsample` project dat in de `Partner-Center-Java-Samples\secure-app-model\keyvault` map is gevonden.</span><span class="sxs-lookup"><span data-stu-id="68841-252">Open the `cpvsample` project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="68841-253">Werk de toepassings instellingen in het bestand [Application. Properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties) bij.</span><span class="sxs-lookup"><span data-stu-id="68841-253">Update the application settings found in the [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties) file.</span></span>

    ```java
    azuread.authority=https://login.microsoftonline.com
    keyvault.baseurl=
    keyvault.clientId=
    keyvault.clientSecret=
    partnercenter.accountId=
    partnercenter.clientId=
    partnercenter.clientSecret=
    partnercenter.displayName=
    ```

    <span data-ttu-id="68841-254">De waarde voor de `partnercenter.displayName` moet de weergave naam van uw Marketplace-toepassing zijn.</span><span class="sxs-lookup"><span data-stu-id="68841-254">The value for the `partnercenter.displayName` should be the display name of your marketplace application.</span></span>

5. <span data-ttu-id="68841-255">Stel de juiste waarden in voor de variabelen **partner** en **customerId** in het bestand [Program. java](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java) .</span><span class="sxs-lookup"><span data-stu-id="68841-255">Set the appropriate values for the **partnerId** and **customerId** variables found in the [Program.java](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java) file.</span></span>

    ```java
    partnerId = "SPECIFY-THE-PARTNER-TENANT-ID-HERE";
    customerId = "SPECIFY-THE-CUSTOMER-TENANT-ID-HERE";
    ```

6. <span data-ttu-id="68841-256">Wanneer u dit voorbeeld project uitvoert, wordt het vernieuwings token opgehaald voor de opgegeven partner.</span><span class="sxs-lookup"><span data-stu-id="68841-256">When you run this sample project, it obtains the refresh token for the specified partner.</span></span> <span data-ttu-id="68841-257">Vervolgens wordt een toegangs token aangevraagd om toegang te krijgen tot het partner centrum namens de partner.</span><span class="sxs-lookup"><span data-stu-id="68841-257">Then, it requests an access token to access Partner Center on behalf of the partner.</span></span> <span data-ttu-id="68841-258">De volgende taak die wordt uitgevoerd, is het verwijderen en maken van machtigings toekenningen in de Tenant van de klant.</span><span class="sxs-lookup"><span data-stu-id="68841-258">The next task it performs is the deletion and creation of permission grants into the customer tenant.</span></span> <span data-ttu-id="68841-259">Omdat er geen relatie is tussen de leverancier van het configuratie scherm en de klant, moeten deze machtigingen worden toegevoegd met behulp van de partner centrum-API.</span><span class="sxs-lookup"><span data-stu-id="68841-259">Since there's no relationship between the control panel vendor and the customer, these permissions need to be added using the Partner Center API.</span></span> <span data-ttu-id="68841-260">In het volgende voor beeld ziet u hoe u de machtigingen kunt verlenen.</span><span class="sxs-lookup"><span data-stu-id="68841-260">The following example shows how to grant the permissions.</span></span>

    ```java
    ApplicationGrant azureAppGrant = new ApplicationGrant();

    azureAppGrant.setEnterpriseApplication("797f4846-ba00-4fd7-ba43-dac1f8f63013");
    azureAppGrant.setScope("user_impersonation");

    ApplicationGrant graphAppGrant = new ApplicationGrant();

    graphAppGrant.setEnterpriseApplication("00000002-0000-0000-c000-000000000000");
    graphAppGrant.setScope("Domain.ReadWrite.All,User.ReadWrite.All,Directory.Read.All");

    ApplicationConsent consent = new ApplicationConsent();

    consent.setApplicationGrants(Arrays.asList(azureAppGrant, graphAppGrant));
    consent.setApplicationId(properties.getProperty(PropertyName.PARTNER_CENTER_CLIENT_ID));
    consent.setDisplayName(properties.getProperty(PropertyName.PARTNER_CENTER_DISPLAY_NAME));

    // Deletes the existing grant into the customer it is present.
    partnerOperations.getServiceClient().delete(
        partnerOperations,
        new TypeReference<ApplicationConsent>(){},
        MessageFormat.format(
            "customers/{0}/applicationconsents/{1}",
            customerId,
            properties.getProperty(PropertyName.PARTNER_CENTER_CLIENT_ID)));

    // Consent to the defined applications and the respective scopes.
    partnerOperations.getServiceClient().post(
        partnerOperations,
        new TypeReference<ApplicationConsent>(){},
        MessageFormat.format(
            "customers/{0}/applicationconsents",
            customerId),
        consent);
    ```

<span data-ttu-id="68841-261">Verwijder de opmerking over de functie aanroepen voor *RunAzureTask* en *RunGraphTask* als u wilt zien hoe u met Azure Resource Manager en Microsoft Graph kunt communiceren namens de klant.</span><span class="sxs-lookup"><span data-stu-id="68841-261">Uncomment the *RunAzureTask* and *RunGraphTask* function calls if you want to see how to interact with Azure Resource Manager and Microsoft Graph on behalf of the customer.</span></span>
