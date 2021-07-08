---
title: Verificatie in Partnercentrum
description: Partner Center gebruikt Azure AD voor verificatie en voor het gebruik van de Partner Center API's moet u uw verificatie-instellingen correct configureren.
ms.date: 11/13/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-csp
ms.openlocfilehash: e54feba7ea727bb7f7eff8de76dcdf28c8a453ee
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548070"
---
# <a name="partner-center-authentication"></a><span data-ttu-id="b7c8a-103">Verificatie in Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="b7c8a-103">Partner Center authentication</span></span>

<span data-ttu-id="b7c8a-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b7c8a-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b7c8a-105">Partner Center maakt gebruik van Azure Active Directory voor verificatie.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-105">Partner Center uses Azure Active Directory for authentication.</span></span> <span data-ttu-id="b7c8a-106">Bij interactie met de API, SDK of PowerShell-module van Partner Center moet u op de juiste wijze een Azure AD-toepassing configureren en vervolgens een toegangstoken aanvragen.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-106">When interacting with the Partner Center API, SDK, or PowerShell module you must correctly configure an Azure AD application and then request an access token.</span></span> <span data-ttu-id="b7c8a-107">Toegangstokens die zijn verkregen met behulp van alleen de app of app en gebruikersverificatie kunnen worden gebruikt met de Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-107">Access tokens obtained using app only or app + user authentication can be used with the Partner Center.</span></span> <span data-ttu-id="b7c8a-108">Er zijn echter twee belangrijke items die moeten worden overwogen</span><span class="sxs-lookup"><span data-stu-id="b7c8a-108">However, there are two important items that need to be considered</span></span>

- <span data-ttu-id="b7c8a-109">Gebruik meervoudige verificatie bij het openen van de Partner Center API met behulp van app- en gebruikersverificatie.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-109">Use multi-factor authentication when accessing the Partner Center API using app + user authentication.</span></span> <span data-ttu-id="b7c8a-110">Zie Secure Application Model inschakelen voor meer informatie [over deze wijziging.](enable-secure-app-model.md)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-110">For more information regarding this change, see [Enable secure application model](enable-secure-app-model.md).</span></span>

- <span data-ttu-id="b7c8a-111">Niet alle bewerkingen die de API Partner Center bieden alleen ondersteuning voor verificatie van apps.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-111">Not all of the operations the Partner Center API support app only authentication.</span></span> <span data-ttu-id="b7c8a-112">Er zijn bepaalde scenario's waarin u app- en gebruikersverificatie moet gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-112">There are certain scenarios where you'll be required to use app + user authentication.</span></span> <span data-ttu-id="b7c8a-113">Onder de *kop Vereisten* in elk [artikel](scenarios.md)vindt u documentatie met de vraag of alleen app-verificatie, app- en gebruikersverificatie of beide worden ondersteund.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-113">Under the *Prerequisites* heading on each [article](scenarios.md), you'll find documentation that states whether app only authentication, app + user authentication, or both are supported.</span></span>

## <a name="initial-setup"></a><span data-ttu-id="b7c8a-114">Eerste configuratie</span><span class="sxs-lookup"><span data-stu-id="b7c8a-114">Initial setup</span></span>

1. <span data-ttu-id="b7c8a-115">Om te beginnen moet u ervoor zorgen dat u zowel een primair Partner Center-account als een integratie-sandbox hebt Partner Center account.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-115">To begin, you need to make sure that you have both a primary Partner Center account, and an integration sandbox Partner Center account.</span></span> <span data-ttu-id="b7c8a-116">Zie Set [up Partner Center accounts for API access (Accounts instellen voor API-toegang) voor meer informatie.](set-up-api-access-in-partner-center.md)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-116">For more information, see [Set up Partner Center accounts for API access](set-up-api-access-in-partner-center.md).</span></span> <span data-ttu-id="b7c8a-117">Noteer de registratie-id en het geheim van de Azure AAD-app (clientgeheim is vereist voor alleen-app-identificatie) voor zowel uw primaire account als uw sandbox-account voor integratie.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-117">Make note of the Azure AAD App registration ID and Secret (client secret is required for App only identification) for both your primary account and your integration sandbox account.</span></span>

2. <span data-ttu-id="b7c8a-118">Meld u aan bij Azure AD vanuit de Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-118">Sign in to Azure AD from the Azure portal.</span></span> <span data-ttu-id="b7c8a-119">Stel **in** machtigingen voor andere toepassingen machtigingen voor **Windows Azure Active Directory** in op **Gedelegeerde** machtigingen en selecteer Zowel Toegang tot de **map** als de aangemelde gebruiker als Aanmelden en gebruikersprofiel **lezen.**</span><span class="sxs-lookup"><span data-stu-id="b7c8a-119">In **permissions to other applications**, set permissions for **Windows Azure Active Directory** to **Delegated Permissions**, and select both **Access the directory as the signed-in user** and **Sign in and read user profile**.</span></span>

3. <span data-ttu-id="b7c8a-120">Voeg in Azure Portal **toe.**</span><span class="sxs-lookup"><span data-stu-id="b7c8a-120">In the Azure portal, **Add application**.</span></span> <span data-ttu-id="b7c8a-121">Zoek naar 'Microsoft Partner Center'. Dit is de Microsoft Partner Center toepassing.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-121">Search for "Microsoft Partner Center", which is the Microsoft Partner Center application.</span></span> <span data-ttu-id="b7c8a-122">Stel Delegated **Permissions in op** **Access Partner Center API**.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-122">Set the **Delegated Permissions** to **Access Partner Center API**.</span></span> <span data-ttu-id="b7c8a-123">Als u een Partner Center voor Microsoft Cloud Duitsland of Partner Center for Microsoft Cloud for US Government, is deze stap verplicht.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-123">If you are using Partner Center for Microsoft Cloud Germany or Partner Center for Microsoft Cloud for US Government, this step is mandatory.</span></span> <span data-ttu-id="b7c8a-124">Als u een algemeen Partner Center gebruikt, is deze stap optioneel.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-124">If you are using Partner Center global instance, this step is optional.</span></span> <span data-ttu-id="b7c8a-125">CSP-partners kunnen de functie App Management in de Partner Center-portal gebruiken om deze stap voor Partner Center globale instantie over te nemen.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-125">CSP Partners can use the App Management feature in the Partner Center portal to bypass this step for Partner Center global instance.</span></span>

## <a name="app-only-authentication"></a><span data-ttu-id="b7c8a-126">Verificatie alleen voor apps</span><span class="sxs-lookup"><span data-stu-id="b7c8a-126">App-only authentication</span></span>

<span data-ttu-id="b7c8a-127">Als u alleen-app-verificatie wilt gebruiken voor toegang tot de Partner Center REST API-, .NET API-, Java-API- of PowerShell-module, kunt u dit doen met behulp van de volgende instructies.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-127">If you would like to use app-only authentication to access the Partner Center REST API, .NET API, Java API, or PowerShell module then you can do so by using the following instructions.</span></span>

## <a name="net-app-only-authentication"></a><span data-ttu-id="b7c8a-128">.NET (alleen-app-verificatie)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-128">.NET (app-only authentication)</span></span>

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

## <a name="java-app-only-authentication"></a><span data-ttu-id="b7c8a-129">Java (alleen app-verificatie)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-129">Java (app-only authentication)</span></span>

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

## <a name="rest-app-only-authentication"></a><span data-ttu-id="b7c8a-130">REST (alleen app-verificatie)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-130">REST (app-only authentication)</span></span>

### <a name="rest-request"></a><span data-ttu-id="b7c8a-131">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="b7c8a-131">REST request</span></span>

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

### <a name="rest-response"></a><span data-ttu-id="b7c8a-132">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="b7c8a-132">REST response</span></span>

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Pragma: no-cache
Content-Type: application/json; charset=utf-8
Expires: -1
Content-Length: 1406

{"token_type":"Bearer","expires_in":"3600","ext_expires_in":"3600","expires_on":"1546469802","not_before":"1546465902","resource":"https://graph.windows.net","access_token":"value-has-been-removed"}
```

## <a name="app--user-authentication"></a><span data-ttu-id="b7c8a-133">App en gebruikersverificatie</span><span class="sxs-lookup"><span data-stu-id="b7c8a-133">App + User authentication</span></span>

<span data-ttu-id="b7c8a-134">In het verleden is de toekenning van de [wachtwoordreferenties](https://tools.ietf.org/html/rfc6749#section-4.3) van de resource-eigenaar gebruikt om een toegangs token aan te vragen voor gebruik met de module Partner Center REST API, .NET API, Java API of PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-134">Historically, the [resource owner password credentials grant](https://tools.ietf.org/html/rfc6749#section-4.3) has been used to request an access token for use with the Partner Center REST API, .NET API, Java API, or PowerShell module.</span></span> <span data-ttu-id="b7c8a-135">Deze methode is gebruikt om een toegangsken aan te vragen bij Azure Active Directory client-id en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-135">That method was used to request an access token from Azure Active Directory using a client identifier and user credentials.</span></span> <span data-ttu-id="b7c8a-136">Deze aanpak werkt echter niet meer omdat Partner Center meervoudige verificatie vereist bij het gebruik van app- en gebruikersverificatie.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-136">However, this approach will no longer work because Partner Center requires multi-factor authentication, when using app + user authentication.</span></span> <span data-ttu-id="b7c8a-137">Om aan deze vereiste te voldoen, heeft Microsoft een veilig, schaalbaar framework geïntroduceerd voor de verificatie van Cloud Solution Provider-partners (CSP) en panelleveranciers (CPV) met behulp van meervoudige verificatie.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-137">To comply with this requirement Microsoft has introduced a secure, scalable framework for authenticating Cloud Solution Provider (CSP) partners and control panel vendors (CPV) using multi-factor authentication.</span></span> <span data-ttu-id="b7c8a-138">Dit framework wordt de veilig toepassingsmodel en bestaat uit een toestemmingsproces en een aanvraag voor een toegangsken met behulp van een vernieuwings token.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-138">This framework is known as the Secure Application Model, and it is composed of a consent process and a request for an access token using a refresh token.</span></span>

### <a name="partner-consent"></a><span data-ttu-id="b7c8a-139">Toestemming van partner</span><span class="sxs-lookup"><span data-stu-id="b7c8a-139">Partner consent</span></span>

<span data-ttu-id="b7c8a-140">Het toestemmingsproces van de partner is een interactief proces waarbij de partner wordt geverifieerd met meervoudige verificatie, toestemming geeft voor de toepassing en een vernieuwingstoken wordt opgeslagen in een beveiligde opslagplaats zoals Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-140">The partner consent process is an interactive process where the partner authenticates using multi-factor authentication, consents to the application, and a refresh token is stored in a secure repository such as Azure Key Vault.</span></span> <span data-ttu-id="b7c8a-141">We raden u aan voor dit proces een toegewezen account te gebruiken voor integratiedoeleinden.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-141">We recommend that a dedicated account for integration purposes be used for this process.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b7c8a-142">De juiste multi-factor authentication-oplossing moet zijn ingeschakeld voor het serviceaccount dat wordt gebruikt in het toestemmingsproces van de partner.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-142">The appropriate multi-factor authentication solution should be enabled for the service account used in the partner consent process.</span></span> <span data-ttu-id="b7c8a-143">Als dit niet het is, voldoet het resulterende vernieuwings token niet aan de beveiligingsvereisten.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-143">If it isn't then the resulting refresh token will not be compliant with security requirements.</span></span>

### <a name="samples-for-app--user-authentication"></a><span data-ttu-id="b7c8a-144">Voorbeelden voor app- en gebruikersverificatie</span><span class="sxs-lookup"><span data-stu-id="b7c8a-144">Samples for App + User authentication</span></span>

<span data-ttu-id="b7c8a-145">Het toestemmingsproces van de partner kan op een aantal manieren worden uitgevoerd.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-145">The partner consent process can be performed in a number of ways.</span></span> <span data-ttu-id="b7c8a-146">Om partners te helpen begrijpen hoe elke vereiste bewerking moet worden uitgevoerd, hebben we de volgende voorbeelden ontwikkeld.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-146">To help partners understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="b7c8a-147">Wanneer u de juiste oplossing in uw omgeving implementeert, is het belangrijk dat u een oplossing ontwikkelt die geschikt is voor uw coderingsstandaarden en beveiligingsbeleid.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-147">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-appuser-authentication"></a><span data-ttu-id="b7c8a-148">.NET (app+ gebruikersverificatie)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-148">.NET (app+user authentication)</span></span>

<span data-ttu-id="b7c8a-149">Het [voorbeeldproject](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) voor toestemming van de partner laat zien hoe u een website gebruikt die is ontwikkeld met behulp van ASP.NET om toestemming vast te leggen, een vernieuwingstoken aan te vragen en deze veilig op te slaan in Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-149">The [partner consent](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) sample project demonstrates how to utilize a website developed using ASP.NET to capture consent, request a refresh token, and securely store it in Azure Key Vault.</span></span> <span data-ttu-id="b7c8a-150">Voer de volgende stappen uit om de vereiste vereisten voor dit voorbeeld te maken.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-150">Perform the following steps to create the required prerequisites for this sample.</span></span>

1. <span data-ttu-id="b7c8a-151">Maak een exemplaar van Azure Key Vault met behulp van de Azure Portal of de volgende PowerShell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-151">Create an instance of Azure Key Vault using the Azure portal or the following PowerShell commands.</span></span> <span data-ttu-id="b7c8a-152">Voordat u de opdracht gaat uitvoeren, moet u de parameterwaarden dienovereenkomstig wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-152">Before executing the command, be sure to modify the parameter values accordingly.</span></span> <span data-ttu-id="b7c8a-153">De kluisnaam moet uniek zijn.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-153">The vault name must be unique.</span></span>

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    <span data-ttu-id="b7c8a-154">Zie Azure Key Vault [Quickstart:](/azure/key-vault/quick-create-portal) Set and retrieve a secret from Azure Key Vault using the Azure Portal or Quickstart: Set and retrieve a secret from Azure Key Vault using PowerShell (Snelstart: een geheim instellen en ophalen uit Azure Key Vault met behulp van [PowerShell)](/azure/key-vault/quick-create-powershell)voor meer informatie over het maken van een Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-154">For more information about creating an Azure Key Vault, see [Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/quick-create-portal) or [Quickstart: Set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span></span> <span data-ttu-id="b7c8a-155">Stel vervolgens een geheim in en haal het op.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-155">Then set and retrieve a secret.</span></span>

2. <span data-ttu-id="b7c8a-156">Maak een Azure AD-toepassing en een sleutel met behulp van de Azure Portal of de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-156">Create an Azure AD Application and a key using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    <span data-ttu-id="b7c8a-157">Noteer de waarden voor de toepassings-id en het geheim, omdat deze worden gebruikt in de onderstaande stappen.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-157">Be sure to make note of the application identifier and secret values because they'll be used in the steps below.</span></span>

3. <span data-ttu-id="b7c8a-158">Verleen de nieuwe Azure AD-toepassing de machtigingen voor het lezen van geheimen met behulp van de Azure Portal of de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-158">Grant the newly create Azure AD application the read secrets permissions using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. <span data-ttu-id="b7c8a-159">Maak een Azure AD-toepassing die is geconfigureerd voor Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-159">Create an Azure AD application that is configured for Partner Center.</span></span> <span data-ttu-id="b7c8a-160">Voer de volgende acties uit om deze stap te voltooien.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-160">Perform the following actions to complete this step.</span></span>

    - <span data-ttu-id="b7c8a-161">Blader naar de [functie App-beheer](https://partner.microsoft.com/pcv/apiintegration/appmanagement) van het Partner Center Dashboard</span><span class="sxs-lookup"><span data-stu-id="b7c8a-161">Browse to the [App management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) feature of the Partner Center Dashboard</span></span>
    - <span data-ttu-id="b7c8a-162">Selecteer *Nieuwe web-app toevoegen* om een nieuwe Azure AD-toepassing te maken.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-162">Select *Add new web app* to create a new Azure AD application.</span></span>

    <span data-ttu-id="b7c8a-163">Zorg ervoor dat u de *waarden voor app-id,\*\*account-id*\* en sleutel documenteert, omdat deze worden gebruikt in de onderstaande stappen. </span><span class="sxs-lookup"><span data-stu-id="b7c8a-163">Be sure to document the *App ID*, \*Account ID\*\*, and *Key* values because they'll be used in the steps below.</span></span>

5. <span data-ttu-id="b7c8a-164">Kloon [de opslagplaats Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met behulp Visual Studio of de volgende opdracht.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-164">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command.</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

6. <span data-ttu-id="b7c8a-165">Open het *project PartnerConsent* in de `Partner-Center-DotNet-Samples\secure-app-model\keyvault` map .</span><span class="sxs-lookup"><span data-stu-id="b7c8a-165">Open the *PartnerConsent* project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

7. <span data-ttu-id="b7c8a-166">Vul de toepassingsinstellingen in de [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-166">Populate the application settings found in the [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)</span></span>

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
    > <span data-ttu-id="b7c8a-167">Gevoelige informatie, zoals toepassingsgeheimen, mag niet worden opgeslagen in configuratiebestanden.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-167">Sensitive information such as application secrets should not be stored in configuration files.</span></span> <span data-ttu-id="b7c8a-168">Dit is hier gedaan omdat dit een voorbeeldtoepassing is.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-168">It was done here because this is a sample application.</span></span> <span data-ttu-id="b7c8a-169">Met uw productietoepassing raden we u ten zeerste aan verificatie op basis van certificaten te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-169">With your production application we strongly recommend that you use certificate-based authentication.</span></span> <span data-ttu-id="b7c8a-170">Zie Certificaatreferenties voor [toepassingsverificatie voor meer informatie.]( /azure/active-directory/develop/active-directory-certificate-credentials)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-170">For more information, see [Certificate credentials for application authentication]( /azure/active-directory/develop/active-directory-certificate-credentials).</span></span>

8. <span data-ttu-id="b7c8a-171">Wanneer u dit voorbeeldproject gaat uitvoeren, wordt u gevraagd om verificatie.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-171">When you run this sample project, it will prompt you for authentication.</span></span> <span data-ttu-id="b7c8a-172">Nadat de authenticatie is geslaagd, wordt een toegangsteken aangevraagd bij Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-172">After successfully authenticating, an access token is requested from Azure AD.</span></span> <span data-ttu-id="b7c8a-173">De informatie die door Azure AD wordt geretourneerd, bevat een vernieuwingstoken dat is opgeslagen in het geconfigureerde exemplaar van Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-173">The information returned from Azure AD includes a refresh token that is stored in the configured instance of Azure Key Vault.</span></span>

## <a name="java-appuser-authentication"></a><span data-ttu-id="b7c8a-174">Java (app+ gebruikersverificatie)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-174">Java (app+user authentication)</span></span>

<span data-ttu-id="b7c8a-175">In [het voorbeeldproject met](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) toestemming van de partner wordt gedemonstreerd hoe u een website gebruikt die is ontwikkeld met behulp van JSP om toestemming vast te leggen, een vernieuwingstoken aan te vragen en een beveiligde opslag in een Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-175">The [partner consent](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) sample project demonstrates how to utilize a website developed using JSP to capture consent, request a refresh token, and secure store in Azure Key Vault.</span></span> <span data-ttu-id="b7c8a-176">Voer de volgende stappen uit om de vereiste vereisten voor dit voorbeeld te maken.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-176">Perform the following to create the required prerequisites for this sample.</span></span>

1. <span data-ttu-id="b7c8a-177">Maak een exemplaar van Azure Key Vault met behulp van de Azure Portal of de volgende PowerShell-opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-177">Create an instance of Azure Key Vault using the Azure portal or the following PowerShell commands.</span></span> <span data-ttu-id="b7c8a-178">Voordat u de opdracht gaat uitvoeren, moet u de parameterwaarden dienovereenkomstig wijzigen.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-178">Before executing the command, be sure to modify the parameter values accordingly.</span></span> <span data-ttu-id="b7c8a-179">De kluisnaam moet uniek zijn.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-179">The vault name must be unique.</span></span>

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    <span data-ttu-id="b7c8a-180">Zie Azure Key Vault [Quickstart:](/azure/key-vault/quick-create-portal) Set and retrieve a secret from Azure Key Vault using the Azure Portal or Quickstart: Set and retrieve a secret from Azure Key Vault using PowerShell (Snelstart: een geheim instellen en ophalen uit Azure Key Vault met behulp van [PowerShell)](/azure/key-vault/quick-create-powershell)voor meer informatie over het maken van een Azure Portal.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-180">For more information about creating an Azure Key Vault, see [Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure portal](/azure/key-vault/quick-create-portal) or [Quickstart: Set and retrieve a secret from Azure Key Vault using PowerShell](/azure/key-vault/quick-create-powershell).</span></span>

2. <span data-ttu-id="b7c8a-181">Maak een Azure AD-toepassing en een sleutel met behulp van de Azure Portal of de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-181">Create an Azure AD Application and a key using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    <span data-ttu-id="b7c8a-182">Zorg ervoor dat u de toepassings-id en geheime waarden documenteert, omdat deze worden gebruikt in de onderstaande stappen.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-182">Be sure to document the application identifier and secret values because they'll be used in the steps below.</span></span>

3. <span data-ttu-id="b7c8a-183">Verleen de zojuist gemaakte Azure AD-toepassing de machtigingen voor het lezen van geheimen met behulp Azure Portal of de volgende opdrachten.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-183">Grant the newly created Azure AD application the read secrets permissions using the Azure portal or the following commands.</span></span>

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. <span data-ttu-id="b7c8a-184">Maak een Azure AD-toepassing die is geconfigureerd voor Partner Center.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-184">Create an Azure AD application that is configured for Partner Center.</span></span> <span data-ttu-id="b7c8a-185">Voer de volgende stappen uit om deze stap te voltooien.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-185">Perform the following to complete this step.</span></span>

    - <span data-ttu-id="b7c8a-186">Blader naar de [functie App-beheer](https://partner.microsoft.com/pcv/apiintegration/appmanagement) van het Partner Center Dashboard</span><span class="sxs-lookup"><span data-stu-id="b7c8a-186">Browse to the [App management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) feature of the Partner Center Dashboard</span></span>
    - <span data-ttu-id="b7c8a-187">Selecteer *Nieuwe web-app toevoegen* om een nieuwe Azure AD-toepassing te maken.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-187">Select *Add new web app* to create a new Azure AD application.</span></span>

    <span data-ttu-id="b7c8a-188">Zorg ervoor dat u de *waarden voor app-id,\*\*account-id*\* en sleutel documenteert, omdat deze worden gebruikt in de onderstaande stappen. </span><span class="sxs-lookup"><span data-stu-id="b7c8a-188">Be sure to document the *App ID*, \*Account ID\*\*, and *Key* values because they'll be used in the steps below.</span></span>

5. <span data-ttu-id="b7c8a-189">Kloon de [opslagplaats Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) met behulp van de volgende opdracht</span><span class="sxs-lookup"><span data-stu-id="b7c8a-189">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

6. <span data-ttu-id="b7c8a-190">Open het *project PartnerConsent* in de `Partner-Center-Java-Samples\secure-app-model\keyvault` map .</span><span class="sxs-lookup"><span data-stu-id="b7c8a-190">Open the *PartnerConsent* project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

7. <span data-ttu-id="b7c8a-191">Vul de toepassingsinstellingen [](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml) in hetweb.xmlbestand</span><span class="sxs-lookup"><span data-stu-id="b7c8a-191">Populate the application settings found in the [web.xml](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml) file</span></span>

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
    > <span data-ttu-id="b7c8a-192">Gevoelige informatie, zoals toepassingsgeheimen, mag niet worden opgeslagen in configuratiebestanden.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-192">Sensitive information such as application secrets should not be stored in configurations files.</span></span> <span data-ttu-id="b7c8a-193">Dit is hier gedaan omdat dit een voorbeeldtoepassing is.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-193">It was done here because this is a sample application.</span></span> <span data-ttu-id="b7c8a-194">Met uw productietoepassing raden we u ten zeerste aan verificatie op basis van certificaten te gebruiken.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-194">With your production application, we strongly recommend that you use certificate based authenticate.</span></span> <span data-ttu-id="b7c8a-195">Zie Certificaatverificatie voor [Key Vault meer informatie.](https://github.com/Azure-Samples/key-vault-java-certificate-authentication)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-195">For more information, see [Key Vault Certificate authentication](https://github.com/Azure-Samples/key-vault-java-certificate-authentication).</span></span>

8. <span data-ttu-id="b7c8a-196">Wanneer u dit voorbeeldproject gaat uitvoeren, wordt u gevraagd om verificatie.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-196">When you run this sample project, it will prompt you for authentication.</span></span> <span data-ttu-id="b7c8a-197">Nadat de authenticatie is geslaagd, wordt een toegangsteken aangevraagd bij Azure AD.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-197">After successfully authenticating, an access token is requested from Azure AD.</span></span> <span data-ttu-id="b7c8a-198">De informatie die door Azure AD wordt geretourneerd, bevat een vernieuwingstoken dat is opgeslagen in het geconfigureerde exemplaar van Azure Key Vault.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-198">The information returned from Azure AD includes a refresh token that is stored in the configured instance of Azure Key Vault.</span></span>

## <a name="cloud-solution-provider-authentication"></a><span data-ttu-id="b7c8a-199">Cloud Solution Provider verificatie</span><span class="sxs-lookup"><span data-stu-id="b7c8a-199">Cloud Solution Provider authentication</span></span>

<span data-ttu-id="b7c8a-200">Cloud Solution Provider kunnen het vernieuwings token gebruiken dat is verkregen via het [toestemmingsproces van de](#partner-consent) partner.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-200">Cloud Solution Provider partners can use the refresh token obtained through the [partner consent](#partner-consent) process.</span></span>

### <a name="samples-for-cloud-solution-provider-authentication"></a><span data-ttu-id="b7c8a-201">Voorbeelden voor Cloud Solution Provider verificatie</span><span class="sxs-lookup"><span data-stu-id="b7c8a-201">Samples for Cloud Solution Provider authentication</span></span>

<span data-ttu-id="b7c8a-202">Om partners te helpen begrijpen hoe elke vereiste bewerking moet worden uitgevoerd, hebben we de volgende voorbeelden ontwikkeld.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-202">To help partners understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="b7c8a-203">Wanneer u de juiste oplossing in uw omgeving implementeert, is het belangrijk dat u een oplossing ontwikkelt die geschikt is voor uw coderingsstandaarden en beveiligingsbeleid.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-203">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-csp-authentication"></a><span data-ttu-id="b7c8a-204">.NET (CSP-verificatie)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-204">.NET (CSP authentication)</span></span>

1. <span data-ttu-id="b7c8a-205">Als u dit nog niet hebt gedaan, voert u het [partner toestemmingsproces uit.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-205">If you have not already done so, perform the [partner consent process](#partner-consent).</span></span>

2. <span data-ttu-id="b7c8a-206">Kloon [de opslagplaats Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met behulp Visual Studio of de volgende opdracht</span><span class="sxs-lookup"><span data-stu-id="b7c8a-206">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. <span data-ttu-id="b7c8a-207">Open het `CSPApplication` project in de map `Partner-Center-DotNet-Samples\secure-app-model\keyvault` .</span><span class="sxs-lookup"><span data-stu-id="b7c8a-207">Open the `CSPApplication` project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="b7c8a-208">Werk de toepassingsinstellingen in het [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config) bij.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-208">Update the application settings found in the [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config) file.</span></span>

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

5. <span data-ttu-id="b7c8a-209">Stel de juiste waarden in voor de **variabelen PartnerId** en **CustomerId** in het [bestand Program.cs.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-209">Set the appropriate values for the **PartnerId** and **CustomerId** variables found in the [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs) file.</span></span>

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. <span data-ttu-id="b7c8a-210">Wanneer u dit voorbeeldproject gaat uitvoeren, wordt het vernieuwings token verkregen tijdens het toestemmingsproces van de partner.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-210">When you run this sample project, it obtains the refresh token obtained during the partner consent process.</span></span> <span data-ttu-id="b7c8a-211">Vervolgens wordt een toegangs token voor interactie met de Partnercentrum-SDK namens de partner gevraagd.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-211">Then, it requests an access token to interact with the Partner Center SDK on the partner's behalf.</span></span> <span data-ttu-id="b7c8a-212">Ten slotte wordt een toegangs token gevraagd om te communiceren met Microsoft Graph namens de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-212">Finally, it requests an access token to interact with Microsoft Graph on behalf of the specified customer.</span></span>

## <a name="java-csp-authentication"></a><span data-ttu-id="b7c8a-213">Java (CSP-verificatie)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-213">Java (CSP authentication)</span></span>

1. <span data-ttu-id="b7c8a-214">Als u dit nog niet hebt gedaan, voert u het [partner toestemmingsproces uit.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-214">If you have not done so already, perform the [partner consent process](#partner-consent).</span></span>

2. <span data-ttu-id="b7c8a-215">Kloon [de opslagplaats Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) met behulp Visual Studio of de volgende opdracht</span><span class="sxs-lookup"><span data-stu-id="b7c8a-215">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. <span data-ttu-id="b7c8a-216">Open het `cspsample` project in de map `Partner-Center-Java-Samples\secure-app-model\keyvault` .</span><span class="sxs-lookup"><span data-stu-id="b7c8a-216">Open the `cspsample` project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="b7c8a-217">Werk de toepassingsinstellingen in het bestand [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties) bij.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-217">Update the application settings found in the [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties) file.</span></span>

     ```java
    azuread.authority=https://login.microsoftonline.com
    keyvault.baseurl=
    keyvault.clientId=
    keyvault.clientSecret=
    partnercenter.accountId=
    partnercenter.clientId=
    partnercenter.clientSecret=
    ```

5. <span data-ttu-id="b7c8a-218">Wanneer u dit voorbeeldproject gaat uitvoeren, wordt het vernieuwings token verkregen tijdens het toestemmingsproces van de partner.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-218">When you run this sample project, it obtains the refresh token obtained during the partner consent process.</span></span> <span data-ttu-id="b7c8a-219">Vervolgens wordt een toegangs token voor interactie met de Partnercentrum-SDK namens de partner gevraagd.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-219">Then, it requests an access token to interact with the Partner Center SDK on the partner's behalf.</span></span>

6. <span data-ttu-id="b7c8a-220">Optioneel: u kunt de aanroepen van de *functie RunAzureTask* en *RunGraphTask* als u wilt zien hoe u namens de klant kunt communiceren met Azure Resource Manager en Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-220">Optional - uncomment the *RunAzureTask* and *RunGraphTask* function calls if you want to see how to interact with Azure Resource Manager and Microsoft Graph on behalf of the customer.</span></span>

## <a name="control-panel-provider-authentication"></a><span data-ttu-id="b7c8a-221">Configuratiescherm providerverificatie</span><span class="sxs-lookup"><span data-stu-id="b7c8a-221">Control Panel Provider authentication</span></span>

<span data-ttu-id="b7c8a-222">Leveranciers van configuratiescherm moeten elke partner die ze ondersteunen, het [toestemmingsproces van de partner](#partner-consent) laten uitvoeren.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-222">Control panel vendors need to have each partner they support perform the [partner consent](#partner-consent) process.</span></span> <span data-ttu-id="b7c8a-223">Zodra dit is voltooid, wordt het vernieuwings token dat via dat proces is verkregen, gebruikt om toegang te krijgen tot Partner Center REST API .NET API.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-223">Once that is completed the refresh token obtained through that process is used to access the Partner Center REST API and .NET API.</span></span>

### <a name="samples-for-cloud-panel-provider-authentication"></a><span data-ttu-id="b7c8a-224">Voorbeelden voor verificatie van cloudpaneelproviders</span><span class="sxs-lookup"><span data-stu-id="b7c8a-224">Samples for Cloud Panel Provider authentication</span></span>

<span data-ttu-id="b7c8a-225">Om panelleveranciers te helpen begrijpen hoe elke vereiste bewerking moet worden uitgevoerd, hebben we de volgende voorbeelden ontwikkeld.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-225">To help control panel vendors understand how to perform each required operation, we have developed the following samples.</span></span> <span data-ttu-id="b7c8a-226">Wanneer u de juiste oplossing in uw omgeving implementeert, is het belangrijk dat u een oplossing ontwikkelt die geschikt is voor uw coderingsstandaarden en beveiligingsbeleid.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-226">When you implement the appropriate solution in your environment, it is important that you develop a solution that is complaint with your coding standards and security policies.</span></span>

## <a name="net-cpv-authentication"></a><span data-ttu-id="b7c8a-227">.NET (CPV-verificatie)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-227">.NET (CPV authentication)</span></span>

1. <span data-ttu-id="b7c8a-228">Ontwikkel en implementeer een proces voor Cloud Solution Provider partners om de juiste toestemming te geven.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-228">Develop and deploy a process for Cloud Solution Provider partners to provide the appropriate consent.</span></span> <span data-ttu-id="b7c8a-229">Zie partner consent (Toestemming van [partner) voor meer informatie.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-229">For more information an example, see [partner consent](#partner-consent).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b7c8a-230">Gebruikersreferenties van een Cloud Solution Provider partner mogen niet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-230">User credentials from a Cloud Solution Provider partner should not be stored.</span></span> <span data-ttu-id="b7c8a-231">Het vernieuwingstoken dat is verkregen via het toestemmingsproces van de partner, moet worden opgeslagen en gebruikt om toegangstokens aan te vragen voor interactie met elke Microsoft-API.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-231">The refresh token obtained through the partner consent process should be stored and used to request access tokens for interacting with any Microsoft API.</span></span>

2. <span data-ttu-id="b7c8a-232">Kloon [de opslagplaats Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met behulp Visual Studio of de volgende opdracht</span><span class="sxs-lookup"><span data-stu-id="b7c8a-232">Clone the [Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) repository using Visual Studio or the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. <span data-ttu-id="b7c8a-233">Open het `CPVApplication` project in de map `Partner-Center-DotNet-Samples\secure-app-model\keyvault` .</span><span class="sxs-lookup"><span data-stu-id="b7c8a-233">Open the `CPVApplication` project found in the `Partner-Center-DotNet-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="b7c8a-234">Werk de toepassingsinstellingen in het [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config) bij.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-234">Update the application settings found in the [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config) file.</span></span>

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

5. <span data-ttu-id="b7c8a-235">Stel de juiste waarden in voor de **variabelen PartnerId** en **CustomerId** in het [bestand Program.cs.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-235">Set the appropriate values for the **PartnerId** and **CustomerId** variables found in the [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs) file.</span></span>

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. <span data-ttu-id="b7c8a-236">Wanneer u dit voorbeeldproject uit te voeren, wordt het vernieuwing token voor de opgegeven partner.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-236">When you run this sample project, it obtains the refresh token for the specified partner.</span></span> <span data-ttu-id="b7c8a-237">Vervolgens wordt een toegangsken voor toegang tot Partner Center en Azure AD-Graph namens de partner gevraagd.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-237">Then, it requests an access token to access Partner Center and Azure AD Graph on behalf of the partner.</span></span> <span data-ttu-id="b7c8a-238">De volgende taak die wordt uitgevoerd, is het verwijderen en maken van machtigingsrechten in de tenant van de klant.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-238">The next task it performs is the deletion and creation of permission grants into the customer tenant.</span></span> <span data-ttu-id="b7c8a-239">Omdat er geen relatie is tussen de leverancier van het configuratiescherm en de klant, moeten deze machtigingen worden toegevoegd met behulp van de Partner Center API.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-239">Since there's no relationship between the control panel vendor and the customer, these permissions need to be added using the Partner Center API.</span></span> <span data-ttu-id="b7c8a-240">In het volgende voorbeeld ziet u hoe u dat doet.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-240">The following example shows how to accomplish that.</span></span>

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

<span data-ttu-id="b7c8a-241">Nadat deze machtigingen zijn ingesteld, voert het voorbeeld bewerkingen uit met behulp van Azure AD Graph namens de klant.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-241">After these permissions have been established, the sample performs operations using Azure AD Graph on behalf of the customer.</span></span>

## <a name="java-cpv-authentication"></a><span data-ttu-id="b7c8a-242">Java (CPV-verificatie)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-242">Java (CPV authentication)</span></span>

1. <span data-ttu-id="b7c8a-243">Ontwikkel en implementeer een proces voor Cloud Solution Provider partners om de juiste toestemming te geven.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-243">Develop and deploy a process for Cloud Solution Provider partners to provide the appropriate consent.</span></span> <span data-ttu-id="b7c8a-244">Zie de toestemming van de partner voor meer informatie [en een voorbeeld.](#partner-consent)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-244">For more information and an example, see the [partner consent](#partner-consent).</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="b7c8a-245">Gebruikersreferenties van een Cloud Solution Provider partner mogen niet worden opgeslagen.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-245">User credentials from a Cloud Solution Provider partner should not be stored.</span></span> <span data-ttu-id="b7c8a-246">Het vernieuwingstoken dat is verkregen via het toestemmingsproces van de partner, moet worden opgeslagen en gebruikt om toegangstokens aan te vragen voor interactie met elke Microsoft-API.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-246">The refresh token obtained through the partner consent process should be stored and used to request access tokens for interacting with any Microsoft API.</span></span>

2. <span data-ttu-id="b7c8a-247">Kloon de [opslagplaats Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) met behulp van de volgende opdracht</span><span class="sxs-lookup"><span data-stu-id="b7c8a-247">Clone the [Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) repository using the following command</span></span>

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. <span data-ttu-id="b7c8a-248">Open het `cpvsample` project in de map `Partner-Center-Java-Samples\secure-app-model\keyvault` .</span><span class="sxs-lookup"><span data-stu-id="b7c8a-248">Open the `cpvsample` project found in the `Partner-Center-Java-Samples\secure-app-model\keyvault` directory.</span></span>

4. <span data-ttu-id="b7c8a-249">Werk de toepassingsinstellingen in het bestand [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties) bij.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-249">Update the application settings found in the [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties) file.</span></span>

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

    <span data-ttu-id="b7c8a-250">De waarde voor moet `partnercenter.displayName` de weergavenaam van uw Marketplace-toepassing zijn.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-250">The value for the `partnercenter.displayName` should be the display name of your marketplace application.</span></span>

5. <span data-ttu-id="b7c8a-251">Stel de juiste waarden in voor de **variabelen partnerId** en **customerId** in het [bestand Program.java.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java)</span><span class="sxs-lookup"><span data-stu-id="b7c8a-251">Set the appropriate values for the **partnerId** and **customerId** variables found in the [Program.java](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java) file.</span></span>

    ```java
    partnerId = "SPECIFY-THE-PARTNER-TENANT-ID-HERE";
    customerId = "SPECIFY-THE-CUSTOMER-TENANT-ID-HERE";
    ```

6. <span data-ttu-id="b7c8a-252">Wanneer u dit voorbeeldproject uit te voeren, wordt het vernieuwing token voor de opgegeven partner.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-252">When you run this sample project, it obtains the refresh token for the specified partner.</span></span> <span data-ttu-id="b7c8a-253">Vervolgens wordt een toegangs token gevraagd voor toegang Partner Center namens de partner.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-253">Then, it requests an access token to access Partner Center on behalf of the partner.</span></span> <span data-ttu-id="b7c8a-254">De volgende taak die wordt uitgevoerd, is het verwijderen en maken van machtigingsrechten in de tenant van de klant.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-254">The next task it performs is the deletion and creation of permission grants into the customer tenant.</span></span> <span data-ttu-id="b7c8a-255">Omdat er geen relatie is tussen de leverancier van het configuratiescherm en de klant, moeten deze machtigingen worden toegevoegd met behulp van de Partner Center API.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-255">Since there's no relationship between the control panel vendor and the customer, these permissions need to be added using the Partner Center API.</span></span> <span data-ttu-id="b7c8a-256">In het volgende voorbeeld ziet u hoe u de machtigingen verleent.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-256">The following example shows how to grant the permissions.</span></span>

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

<span data-ttu-id="b7c8a-257">Hef de aanroepen van de *functie RunAzureTask* en *RunGraphTask* op als u wilt zien hoe u namens de klant kunt communiceren met Azure Resource Manager en Microsoft Graph.</span><span class="sxs-lookup"><span data-stu-id="b7c8a-257">Uncomment the *RunAzureTask* and *RunGraphTask* function calls if you want to see how to interact with Azure Resource Manager and Microsoft Graph on behalf of the customer.</span></span>
