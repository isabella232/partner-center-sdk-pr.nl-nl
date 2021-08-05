---
title: Verificatie in Partnercentrum
description: Partner Center gebruikt Azure AD voor verificatie en voor het gebruik van de Partner Center API's moet u uw verificatie-instellingen correct configureren.
ms.date: 11/13/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 75d60ca983cd5b8fe53134ec7481319b153e128a
ms.sourcegitcommit: 07b9a11f5c615ed1e716081392032cea2124bd98
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/04/2021
ms.locfileid: "115104190"
---
# <a name="partner-center-authentication"></a>Verificatie in Partnercentrum

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Partner Center maakt gebruik van Azure Active Directory voor verificatie. Bij interactie met de API, SDK of PowerShell-module van Partner Center moet u op de juiste wijze een Azure AD-toepassing configureren en vervolgens een toegangstoken aanvragen. Toegangstokens die zijn verkregen met behulp van alleen de app of app en gebruikersverificatie kunnen worden gebruikt met de Partner Center. Er zijn echter twee belangrijke items die moeten worden overwogen

- Gebruik meervoudige verificatie bij het openen van de Partner Center API met behulp van app- en gebruikersverificatie. Zie Secure Application Model inschakelen voor meer informatie [over deze wijziging.](enable-secure-app-model.md)

- Niet alle bewerkingen die de API Partner Center bieden alleen ondersteuning voor verificatie van apps. Er zijn bepaalde scenario's waarin u app- en gebruikersverificatie moet gebruiken. Onder de *kop Vereisten* in elk [artikel](scenarios.md)vindt u documentatie met de vraag of alleen app-verificatie, app- en gebruikersverificatie of beide worden ondersteund.

## <a name="initial-setup"></a>Eerste configuratie

1. Om te beginnen moet u ervoor zorgen dat u zowel een primair Partner Center-account als een integratie-sandbox hebt Partner Center account. Zie Partner Center instellen voor [API-toegang voor meer informatie.](set-up-api-access-in-partner-center.md) Noteer de registratie-id en het geheim van de Azure AAD-app (clientgeheim is vereist voor alleen app-identificatie) voor zowel uw primaire account als uw sandbox-account voor integratie.

2. Meld u aan bij Azure AD vanuit de Azure Portal. Stel **in** machtigingen voor andere toepassingen machtigingen voor **Windows Azure Active Directory** in op **Gedelegeerde** machtigingen en selecteer zowel Toegang tot de **map** als de aangemelde gebruiker en Aanmelden en gebruikersprofiel **lezen.**

3. Voeg in Azure Portal **toe.** Zoek naar 'Microsoft Partner Center'. Dit is de Microsoft Partner Center toepassing. Stel Delegated **Permissions in op** **Access Partner Center API**. Als u een Partner Center gebruikt voor Microsoft Cloud Duitsland of Partner Center voor Microsoft Cloud for US Government, is deze stap verplicht. Als u een algemeen Partner Center gebruikt, is deze stap optioneel. CSP-partners kunnen de functie App Management in de Partner Center-portal gebruiken om deze stap over te Partner Center globale instantie.

## <a name="app-only-authentication"></a>Verificatie alleen voor apps

Als u alleen-app-verificatie wilt gebruiken voor toegang tot de Partner Center REST API-, .NET API-, Java-API- of PowerShell-module, kunt u dit doen met behulp van de volgende instructies.

## <a name="net-app-only-authentication"></a>.NET (alleen-app-verificatie)

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

## <a name="java-app-only-authentication"></a>Java (alleen app-verificatie)

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

## <a name="rest-app-only-authentication"></a>REST (alleen app-verificatie)

### <a name="rest-request"></a>REST-aanvraag

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

### <a name="rest-response"></a>REST-antwoord

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Pragma: no-cache
Content-Type: application/json; charset=utf-8
Expires: -1
Content-Length: 1406

{"token_type":"Bearer","expires_in":"3600","ext_expires_in":"3600","expires_on":"1546469802","not_before":"1546465902","resource":"https://graph.windows.net","access_token":"value-has-been-removed"}
```

## <a name="app--user-authentication"></a>App en gebruikersverificatie

In het verleden is de toewijzing van de [wachtwoordreferenties](https://tools.ietf.org/html/rfc6749#section-4.3) van de resource-eigenaar gebruikt om een toegangs token aan te vragen voor gebruik met de module Partner Center REST API, .NET API, Java API of PowerShell. Deze methode is gebruikt om een toegangsken aan te vragen bij Azure Active Directory client-id en gebruikersreferenties. Deze methode werkt echter niet meer omdat Partner Center meervoudige verificatie vereist bij het gebruik van app- en gebruikersverificatie. Om aan deze vereiste te voldoen, heeft Microsoft een veilig, schaalbaar framework geïntroduceerd voor de verificatie van Cloud Solution Provider-partners (CSP) en panelleveranciers (CPV) met behulp van meervoudige verificatie. Dit framework wordt de veilig toepassingsmodel en bestaat uit een toestemmingsproces en een aanvraag voor een toegangsken met behulp van een vernieuwings token.

### <a name="partner-consent"></a>Toestemming van partner

Het toestemmingsproces van de partner is een interactief proces waarbij de partner wordt geverifieerd met meervoudige verificatie, toestemming geeft voor de toepassing en een vernieuwingstoken wordt opgeslagen in een beveiligde opslagplaats zoals Azure Key Vault. We raden u aan voor dit proces een toegewezen account te gebruiken voor integratiedoeleinden.

> [!IMPORTANT]
> De juiste multi-factor authentication-oplossing moet zijn ingeschakeld voor het serviceaccount dat wordt gebruikt in het toestemmingsproces van de partner. Als dit niet het is, voldoet het resulterende vernieuwings token niet aan de beveiligingsvereisten.

### <a name="samples-for-app--user-authentication"></a>Voorbeelden voor app- en gebruikersverificatie

Het toestemmingsproces van de partner kan op een aantal manieren worden uitgevoerd. Om partners te helpen begrijpen hoe elke vereiste bewerking moet worden uitgevoerd, hebben we de volgende voorbeelden ontwikkeld. Wanneer u de juiste oplossing in uw omgeving implementeert, is het belangrijk dat u een oplossing ontwikkelt die geschikt is voor uw coderingsstandaarden en beveiligingsbeleid.

## <a name="net-appuser-authentication"></a>.NET (app+ gebruikersverificatie)

Het [voorbeeldproject](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) voor toestemming van de partner laat zien hoe u een website gebruikt die is ontwikkeld met behulp van ASP.NET om toestemming vast te leggen, een vernieuwingstoken aan te vragen en deze veilig op te slaan in Azure Key Vault. Voer de volgende stappen uit om de vereiste vereisten voor dit voorbeeld te maken.

1. Maak een exemplaar van Azure Key Vault met behulp van de Azure Portal of de volgende PowerShell-opdrachten. Voordat u de opdracht gaat uitvoeren, moet u de parameterwaarden dienovereenkomstig wijzigen. De kluisnaam moet uniek zijn.

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    Voor meer informatie over het maken van een Azure Key Vault, zie Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure Portal or Quickstart: Set and retrieve [a secret from Azure Key Vault using PowerShell (Snelstart:](/azure/key-vault/quick-create-powershell)een geheim instellen en ophalen uit [Azure Key Vault](/azure/key-vault/quick-create-portal) met behulp van PowerShell). Stel vervolgens een geheim in en haal het op.

2. Maak een Azure AD-toepassing en een sleutel met behulp van de Azure Portal of de volgende opdrachten.

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    Noteer de waarden voor de toepassings-id en het geheim, omdat deze worden gebruikt in de onderstaande stappen.

3. Verleen de nieuwe Azure AD-toepassing de machtigingen voor het lezen van geheimen met behulp van Azure Portal of de volgende opdrachten.

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. Maak een Azure AD-toepassing die is geconfigureerd voor Partner Center. Voer de volgende acties uit om deze stap te voltooien.

    - Blader naar de [functie App-beheer](https://partner.microsoft.com/pcv/apiintegration/appmanagement) van het Partner Center Dashboard
    - Selecteer *Nieuwe web-app toevoegen om* een nieuwe Azure AD-toepassing te maken.

    Zorg ervoor dat u de *waarden voor app-id,**account-id** en sleutel documenteert, omdat deze worden gebruikt in de onderstaande stappen. 

5. Kloon [de opslagplaats Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met behulp Visual Studio of de volgende opdracht.

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

6. Open het *project PartnerConsent* in de `Partner-Center-DotNet-Samples\secure-app-model\keyvault` map .

7. Vul de toepassingsinstellingen in de [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)

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
    > Gevoelige informatie, zoals toepassingsgeheimen, mag niet worden opgeslagen in configuratiebestanden. Dit is hier gedaan omdat dit een voorbeeldtoepassing is. Met uw productietoepassing raden we u ten zeerste aan verificatie op basis van certificaten te gebruiken. Zie [Certificaatreferenties voor toepassingsverificatie voor meer informatie.]( /azure/active-directory/develop/active-directory-certificate-credentials)

8. Wanneer u dit voorbeeldproject gaat uitvoeren, wordt u gevraagd om verificatie. Nadat de authenticatie is geslaagd, wordt een toegangsteken aangevraagd bij Azure AD. De informatie die door Azure AD wordt geretourneerd, bevat een vernieuwingstoken dat is opgeslagen in het geconfigureerde exemplaar van Azure Key Vault.

## <a name="java-appuser-authentication"></a>Java (app+ gebruikersverificatie)

In [het voorbeeldproject met](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) toestemming van de partner wordt gedemonstreerd hoe u een website gebruikt die is ontwikkeld met behulp van JSP om toestemming vast te leggen, een vernieuwingstoken aan te vragen en een beveiligde opslag in een Azure Key Vault. Voer de volgende stappen uit om de vereiste vereisten voor dit voorbeeld te maken.

1. Maak een exemplaar van Azure Key Vault met behulp van de Azure Portal of de volgende PowerShell-opdrachten. Voordat u de opdracht gaat uitvoeren, moet u de parameterwaarden dienovereenkomstig wijzigen. De kluisnaam moet uniek zijn.

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    Voor meer informatie over het maken van een Azure Key Vault, zie Quickstart: Set and retrieve a secret from Azure Key Vault using the Azure Portal or Quickstart: Set and retrieve [a secret from Azure Key Vault using PowerShell (Snelstart:](/azure/key-vault/quick-create-powershell)een geheim instellen en ophalen uit [Azure Key Vault](/azure/key-vault/quick-create-portal) met behulp van PowerShell).

2. Maak een Azure AD-toepassing en een sleutel met behulp van de Azure Portal of de volgende opdrachten.

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    Zorg ervoor dat u de toepassings-id en geheime waarden documenteert, omdat deze worden gebruikt in de onderstaande stappen.

3. Verleen de zojuist gemaakte Azure AD-toepassing de machtigingen voor het lezen van geheimen met behulp Azure Portal of de volgende opdrachten.

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. Maak een Azure AD-toepassing die is geconfigureerd voor Partner Center. Voer de volgende stappen uit om deze stap te voltooien.

    - Blader naar de [functie App-beheer](https://partner.microsoft.com/pcv/apiintegration/appmanagement) van het Partner Center Dashboard
    - Selecteer *Nieuwe web-app toevoegen om* een nieuwe Azure AD-toepassing te maken.

    Zorg ervoor dat u de *waarden voor app-id,**account-id** en sleutel documenteert, omdat deze worden gebruikt in de onderstaande stappen. 

5. Kloon de [opslagplaats Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) met behulp van de volgende opdracht

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

6. Open het *project PartnerConsent* in de `Partner-Center-Java-Samples\secure-app-model\keyvault` map .

7. Vul de toepassingsinstellingen [](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml) in hetweb.xmlbestand

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
    > Gevoelige informatie, zoals toepassingsgeheimen, mag niet worden opgeslagen in configuratiebestanden. Dit is hier gedaan omdat dit een voorbeeldtoepassing is. Met uw productietoepassing raden we u ten zeerste aan verificatie op basis van certificaten te gebruiken. Zie Certificaatverificatie voor [Key Vault meer informatie.](https://github.com/Azure-Samples/key-vault-java-certificate-authentication)

8. Wanneer u dit voorbeeldproject gaat uitvoeren, wordt u gevraagd om verificatie. Nadat de authenticatie is geslaagd, wordt een toegangsteken aangevraagd bij Azure AD. De informatie die door Azure AD wordt geretourneerd, bevat een vernieuwingstoken dat is opgeslagen in het geconfigureerde exemplaar van Azure Key Vault.

## <a name="cloud-solution-provider-authentication"></a>Cloud Solution Provider verificatie

Cloud Solution Provider kunnen het vernieuwings token gebruiken dat is verkregen via het [toestemmingsproces van de](#partner-consent) partner.

### <a name="samples-for-cloud-solution-provider-authentication"></a>Voorbeelden voor Cloud Solution Provider verificatie

Om partners te helpen begrijpen hoe ze elke vereiste bewerking moeten uitvoeren, hebben we de volgende voorbeelden ontwikkeld. Wanneer u de juiste oplossing in uw omgeving implementeert, is het belangrijk dat u een oplossing ontwikkelt die geschikt is voor uw coderingsstandaarden en beveiligingsbeleid.

## <a name="net-csp-authentication"></a>.NET (CSP-verificatie)

1. Als u dit nog niet hebt gedaan, voert u het [toestemmingsproces van de partner uit.](#partner-consent)

2. Kloon [de opslagplaats Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met behulp Visual Studio of de volgende opdracht

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. Open het `CSPApplication` project in de map `Partner-Center-DotNet-Samples\secure-app-model\keyvault` .

4. Werk de toepassingsinstellingen in het [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config) bij.

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

5. Stel de juiste waarden in voor de **variabelen PartnerId** en **CustomerId** in het [bestand Program.cs.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs)

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. Wanneer u dit voorbeeldproject gaat uitvoeren, wordt het vernieuwings token verkregen tijdens het toestemmingsproces van de partner. Vervolgens wordt een toegang token voor interactie met de Partnercentrum-SDK namens de partner gevraagd. Ten slotte wordt een toegang token gevraagd om te communiceren met Microsoft Graph namens de opgegeven klant.

## <a name="java-csp-authentication"></a>Java (CSP-verificatie)

1. Als u dit nog niet hebt gedaan, voert u het [toestemmingsproces van de partner uit.](#partner-consent)

2. Kloon [de opslagplaats Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) met behulp Visual Studio of de volgende opdracht

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. Open het `cspsample` project in de map `Partner-Center-Java-Samples\secure-app-model\keyvault` .

4. Werk de toepassingsinstellingen in het bestand [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties) bij.

     ```java
    azuread.authority=https://login.microsoftonline.com
    keyvault.baseurl=
    keyvault.clientId=
    keyvault.clientSecret=
    partnercenter.accountId=
    partnercenter.clientId=
    partnercenter.clientSecret=
    ```

5. Wanneer u dit voorbeeldproject gaat uitvoeren, wordt het vernieuwings token verkregen tijdens het toestemmingsproces van de partner. Vervolgens wordt een toegang token voor interactie met de Partnercentrum-SDK namens de partner gevraagd.

6. Optioneel: hef de aanroepen van de functie *RunAzureTask* en *RunGraphTask* op als u wilt zien hoe u namens de klant kunt communiceren met Azure Resource Manager en Microsoft Graph.

## <a name="control-panel-provider-authentication"></a>Configuratiescherm providerverificatie

Leveranciers van configuratiescherm moeten elke partner die ze ondersteunen, het [toestemmingsproces van de partner](#partner-consent) laten uitvoeren. Zodra dit is voltooid, wordt het vernieuwings-token dat via dat proces is verkregen, gebruikt om toegang te krijgen tot Partner Center REST API en .NET API.

### <a name="samples-for-cloud-panel-provider-authentication"></a>Voorbeelden voor verificatie van cloudpaneelproviders

Om configuratieschermleveranciers te helpen begrijpen hoe ze elke vereiste bewerking moeten uitvoeren, hebben we de volgende voorbeelden ontwikkeld. Wanneer u de juiste oplossing in uw omgeving implementeert, is het belangrijk dat u een oplossing ontwikkelt die geschikt is voor uw coderingsstandaarden en beveiligingsbeleid.

## <a name="net-cpv-authentication"></a>.NET (CPV-verificatie)

1. Ontwikkel en implementeer een proces voor Cloud Solution Provider partners om de juiste toestemming te geven. Zie partner consent (Toestemming van [partner) voor meer informatie over een voorbeeld.](#partner-consent)

    > [!IMPORTANT]
    > Gebruikersreferenties van een Cloud Solution Provider partner mogen niet worden opgeslagen. Het vernieuwingstoken dat is verkregen via het toestemmingsproces van de partner, moet worden opgeslagen en gebruikt om toegangstokens aan te vragen voor interactie met een Microsoft-API.

2. Kloon [de opslagplaats Partner-Center-DotNet-Samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met behulp Visual Studio of de volgende opdracht

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. Open het `CPVApplication` project in de map `Partner-Center-DotNet-Samples\secure-app-model\keyvault` .

4. Werk de toepassingsinstellingen in het [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config) bij.

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

5. Stel de juiste waarden in voor de **variabelen PartnerId** en **CustomerId** in het [bestand Program.cs.](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs)

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. Wanneer u dit voorbeeldproject uit te voeren, wordt het vernieuwings-token voor de opgegeven partner. Vervolgens wordt een toegangs token voor toegang tot Partner Center en Azure AD-Graph namens de partner gevraagd. De volgende taak die wordt uitgevoerd, is het verwijderen en maken van machtigingen aan de tenant van de klant. Omdat er geen relatie is tussen de leverancier van het configuratiescherm en de klant, moeten deze machtigingen worden toegevoegd met behulp van Partner Center API. In het volgende voorbeeld ziet u hoe u dat doet.

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

Nadat deze machtigingen zijn ingesteld, voert het voorbeeld bewerkingen uit met behulp van Azure AD Graph namens de klant.

## <a name="java-cpv-authentication"></a>Java (CPV-verificatie)

1. Ontwikkel en implementeer een proces voor Cloud Solution Provider partners om de juiste toestemming te geven. Zie de toestemming van de partner voor meer [informatie en een voorbeeld.](#partner-consent)

    > [!IMPORTANT]
    > Gebruikersreferenties van een Cloud Solution Provider partner mogen niet worden opgeslagen. Het vernieuwingstoken dat is verkregen via het toestemmingsproces van de partner, moet worden opgeslagen en gebruikt om toegangstokens aan te vragen voor interactie met een Microsoft-API.

2. Kloon [de opslagplaats Partner-Center-Java-Samples](https://github.com/Microsoft/Partner-Center-Java-Samples) met behulp van de volgende opdracht

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. Open het `cpvsample` project in de map `Partner-Center-Java-Samples\secure-app-model\keyvault` .

4. Werk de toepassingsinstellingen in het bestand [application.properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties) bij.

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

    De waarde voor moet `partnercenter.displayName` de weergavenaam van uw Marketplace-toepassing zijn.

5. Stel de juiste waarden in voor de **variabelen partnerId** en **customerId** in het [bestand Program.java.](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java)

    ```java
    partnerId = "SPECIFY-THE-PARTNER-TENANT-ID-HERE";
    customerId = "SPECIFY-THE-CUSTOMER-TENANT-ID-HERE";
    ```

6. Wanneer u dit voorbeeldproject uit te voeren, wordt het vernieuwings-token voor de opgegeven partner. Vervolgens wordt een toegangs token gevraagd voor toegang Partner Center namens de partner. De volgende taak die wordt uitgevoerd, is het verwijderen en maken van machtigingen aan de tenant van de klant. Omdat er geen relatie is tussen de leverancier van het configuratiescherm en de klant, moeten deze machtigingen worden toegevoegd met behulp van Partner Center API. In het volgende voorbeeld ziet u hoe u de machtigingen verleent.

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

Hef de aanroepen van de functie *RunAzureTask* en *RunGraphTask* op als u wilt zien hoe u namens de klant kunt communiceren met Azure Resource Manager en Microsoft Graph.
