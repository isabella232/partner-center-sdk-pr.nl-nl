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
# <a name="partner-center-authentication"></a>Verificatie in Partnercentrum

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Partner Center maakt gebruik van Azure Active Directory voor verificatie. Bij interactie met de API, SDK of PowerShell-module van Partner Center moet u op de juiste wijze een Azure AD-toepassing configureren en vervolgens een toegangstoken aanvragen. Toegangs tokens die zijn verkregen met behulp van alleen app of app + gebruikers authenticatie, kunnen worden gebruikt met het partner centrum. Er zijn echter twee belang rijke items die moeten worden overwogen

- Gebruik multi-factor Authentication bij het openen van de partner centrum-API met behulp van app + gebruikers authenticatie. Zie voor meer informatie over deze wijziging [veilig toepassings model inschakelen](enable-secure-app-model.md).

- Niet alle bewerkingen van de partner centrum-API ondersteunen alleen app-verificatie. Er zijn bepaalde scenario's waarin u app + gebruikers verificatie moet gebruiken. Onder de kop *vereisten* voor elk [artikel](scenarios.md)vindt u documentatie die aangeeft of alleen app-verificatie, app + gebruikers verificatie of beide worden ondersteund.

## <a name="initial-setup"></a>Eerste configuratie

1. Om te beginnen, moet u ervoor zorgen dat u zowel een primair partner centrum-account als een integratie sandbox-partner centrum-account hebt. Zie voor meer informatie [Partner Center-accounts instellen voor API-toegang](set-up-api-access-in-partner-center.md). Noteer de registratie-ID van de Azure AAD-app en het geheim (client geheim is vereist voor het identificeren van alleen apps) voor zowel uw primaire account als uw sandbox-account voor integratie.

2. Meld u aan bij Azure AD vanuit het Azure Portal. Stel **in machtigingen voor andere toepassingen** machtigingen voor **Windows-Azure Active Directory** in op **gedelegeerde machtigingen** en selecteer beide **toegang tot de map als de aangemelde gebruiker** en meld u aan **en het gebruikers profiel lezen**.

3. Voeg in het Azure Portal **toepassing toe**. Zoek naar ' micro soft Partner Center ', een micro soft Partner Center-toepassing. Stel de **gedelegeerde machtigingen** in op **toegang tot de partner centrum-API**. Als u gebruikmaakt van partner Center voor Microsoft Cloud Duitsland of partner centrum voor Microsoft Cloud voor de Amerikaanse overheid, is deze stap verplicht. Als u het globale exemplaar van partner Center gebruikt, is deze stap optioneel. CSP-partners kunnen de functie voor app-beheer in de partner centrum Portal gebruiken om deze stap over te slaan voor het globale exemplaar van partner Center.

## <a name="app-only-authentication"></a>Alleen app-verificatie

Als u alleen app-verificatie wilt gebruiken om toegang te krijgen tot het partner centrum REST API, .NET API, Java API of Power shell-module, kunt u dit doen door gebruik te maken van de volgende instructies.

## <a name="net-app-only-authentication"></a>.NET (alleen app-verificatie)

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

## <a name="app--user-authentication"></a>App + gebruikers authenticatie

In het verleden is de toewijzing van het [wacht woord](https://tools.ietf.org/html/rfc6749#section-4.3) voor de resource-eigenaar gebruikt om een toegangs token aan te vragen voor gebruik met het Partner centrum rest API, .net API, Java API of Power shell-module. Deze methode is gebruikt om een toegangs token aan te vragen bij Azure Active Directory met behulp van een client-id en gebruikers referenties. Deze benadering werkt echter niet meer omdat het partner centrum multi-factor Authentication vereist, wanneer u app + gebruikers authenticatie gebruikt. Om te voldoen aan deze vereiste heeft micro soft een veilig, schaalbaar Framework geïntroduceerd voor het verifiëren van de CSP-partners (Cloud Solution Provider) en leveranciers van het configuratie scherm (CPV) met multi-factor Authentication. Dit framework wordt het beveiligde toepassings model genoemd en bestaat uit een toestemmings proces en een aanvraag voor een toegangs token met behulp van een vernieuwings token.

### <a name="partner-consent"></a>Partner toestemming

Het partner toestemmings proces is een interactief proces waarbij de partner zich verifieert met multi-factor Authentication, wordt gestemd op de toepassing en een vernieuwings token wordt opgeslagen in een beveiligde opslag plaats, zoals Azure Key Vault. U kunt het beste een toegewezen account voor integratie doeleinden gebruiken voor dit proces.

> [!IMPORTANT]
> De juiste multi-factor Authentication-oplossing moet zijn ingeschakeld voor het service account dat wordt gebruikt in het partner toestemmings proces. Als dat niet het geval is, voldoet het resulterende vernieuwings token niet aan de beveiligings vereisten.

### <a name="samples-for-app--user-authentication"></a>Voor beelden voor app + gebruikers verificatie

Het proces voor partner toestemming kan op verschillende manieren worden uitgevoerd. We hebben de volgende voor beelden ontwikkeld om partners te helpen begrijpen hoe ze elke vereiste bewerking uit te voeren. Wanneer u de juiste oplossing in uw omgeving implementeert, is het belang rijk dat u een oplossing ontwikkelt die een klacht vormt voor uw coderings standaarden en beveiligings beleid.

## <a name="net-appuser-authentication"></a>.NET (app + gebruikers verificatie)

Het voorbeeld project van de [partner toestemming](https://github.com/Microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model/keyvault) laat zien hoe u een website kunt gebruiken die is ontwikkeld met ASP.net om toestemming vast te leggen, een vernieuwings token aan te vragen en het veilig op te slaan in azure Key Vault. Voer de volgende stappen uit om de vereiste onderdelen voor dit voor beeld te maken.

1. Maak een instantie van Azure Key Vault met behulp van de Azure Portal of de volgende Power shell-opdrachten. Voordat u de opdracht uitvoert, moet u ervoor zorgen dat u de parameter waarden dienovereenkomstig wijzigt. De naam van de kluis moet uniek zijn.

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    Voor meer informatie over het maken van een Azure Key Vault raadpleegt [u Quick Start: een geheim instellen en ophalen uit Azure Key Vault met behulp van de Azure Portal](/azure/key-vault/quick-create-portal) of [Quick Start: een geheim instellen en ophalen uit Azure Key Vault met behulp van Power shell](/azure/key-vault/quick-create-powershell). Stel vervolgens een geheim in en haal het op.

2. Maak een Azure AD-toepassing en een sleutel met behulp van de Azure Portal of de volgende opdrachten.

    ```azurepowershell-interactive
    Connect-AzureAD

    $SessionInfo = Get-AzureADCurrentSessionInfo

    $app = New-AzureADApplication -DisplayName 'My Vault Access App' -IdentifierUris 'https://$($SessionInfo.TenantDomain)/$((New-Guid).ToString())'
    $password = New-AzureADApplicationPasswordCredential -ObjectId $app.ObjectId

    Write-Host "ApplicationId       = $($app.AppId)"
    Write-Host "ApplicationSecret   = $($password.Value)"
    ```

    Noteer de toepassings-id en geheime waarden, omdat deze worden gebruikt in de onderstaande stappen.

3. Verleen de nieuwe Azure AD-toepassing de machtigingen lezen geheimen met de Azure Portal of de volgende opdrachten.

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. Maak een Azure AD-toepassing die is geconfigureerd voor partner centrum. Voer de volgende acties uit om deze stap te volt ooien.

    - Blader naar de [app Management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) -functie van het dash board van de partner centrum
    - Klik op *nieuwe web-app toevoegen* om een nieuwe Azure AD-toepassing te maken.

    Zorg ervoor dat u de *App-ID*, * account-id * * en *sleutel* waarden documenteert, omdat deze worden gebruikt in de onderstaande stappen.

5. Kloon de opslag plaats [Partner-Center-DotNet-samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met behulp van Visual Studio of de volgende opdracht.

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

6. Open het *PartnerConsent* -project dat in de map is gevonden `Partner-Center-DotNet-Samples\secure-app-model\keyvault` .

7. Vul de toepassings instellingen in de [web.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/PartnerConsent/Web.config)

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
    > Gevoelige informatie, zoals toepassings geheimen, mag niet worden opgeslagen in configuratie bestanden. U hebt dit gedaan omdat dit een voorbeeld toepassing is. Met uw productie toepassing wordt u ten zeerste aangeraden authenticatie op basis van certificaten te gebruiken. Zie [certificaat referenties voor toepassings verificatie]( /azure/active-directory/develop/active-directory-certificate-credentials)voor meer informatie.

8. Wanneer u dit voorbeeld project uitvoert, wordt u gevraagd om te verifiëren. Nadat de verificatie is geslaagd, wordt een toegangs token aangevraagd bij Azure AD. De informatie die wordt geretourneerd door Azure AD bevat een vernieuwings token dat is opgeslagen in het geconfigureerde exemplaar van Azure Key Vault.

## <a name="java-appuser-authentication"></a>Java (app + gebruikers verificatie)

Het voorbeeld project van de [partner toestemming](https://github.com/Microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model/keyvault) laat zien hoe u een website kunt gebruiken die is ontwikkeld met JSP om toestemming vast te leggen, een vernieuwings token aan te vragen en een beveiligde Store te gebruiken in azure Key Vault. Voer de volgende stappen uit om de vereiste onderdelen voor dit voor beeld te maken.

1. Maak een instantie van Azure Key Vault met behulp van de Azure Portal of de volgende Power shell-opdrachten. Voordat u de opdracht uitvoert, moet u ervoor zorgen dat u de parameter waarden dienovereenkomstig wijzigt. De naam van de kluis moet uniek zijn.

    ```azurepowershell-interactive
    Login-AzureRmAccount

    # Create a new resource group
    New-AzureRmResourceGroup -Name ContosoResourceGroup -Location EastUS

    New-AzureRmKeyVault -Name 'Contoso-Vault' -ResourceGroupName 'ContosoResourceGroup' -Location 'East US'
    ```

    Voor meer informatie over het maken van een Azure Key Vault raadpleegt [u Quick Start: een geheim instellen en ophalen uit Azure Key Vault met behulp van de Azure Portal](/azure/key-vault/quick-create-portal) of [Quick Start: een geheim instellen en ophalen uit Azure Key Vault met behulp van Power shell](/azure/key-vault/quick-create-powershell).

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

3. Ken de zojuist gemaakte Azure AD-toepassing de machtigingen lezen geheimen toe met behulp van de Azure Portal of de volgende opdrachten.

    ```azurepowershell-interactive
    $app = Get-AzureADApplication -Filter {AppId -eq 'ENTER-APP-ID-HERE'}

    Set-AzureRmKeyVaultAccessPolicy -VaultName ContosoVault -ObjectId $app.ObjectId -PermissionsToSecrets get
    ```

4. Maak een Azure AD-toepassing die is geconfigureerd voor partner centrum. Voer de volgende stappen uit om deze stap te volt ooien.

    - Blader naar de [app Management](https://partner.microsoft.com/pcv/apiintegration/appmanagement) -functie van het dash board van de partner centrum
    - Klik op *nieuwe web-app toevoegen* om een nieuwe Azure AD-toepassing te maken.

    Zorg ervoor dat u de *App-ID*, * account-id * * en *sleutel* waarden documenteert, omdat deze worden gebruikt in de onderstaande stappen.

5. Kloon de opslag plaats van de [Partner-Center-Java-voor beelden](https://github.com/Microsoft/Partner-Center-Java-Samples) met de volgende opdracht

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

6. Open het *PartnerConsent* -project dat in de map is gevonden `Partner-Center-Java-Samples\secure-app-model\keyvault` .

7. Vul de toepassings instellingen in het [web.xml](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/partnerconsent/src/main/webapp/WEB-INF/web.xml) bestand in

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
    > Gevoelige informatie, zoals toepassings geheimen, mag niet worden opgeslagen in configuratie bestanden. U hebt dit gedaan omdat dit een voorbeeld toepassing is. Met uw productie toepassing wordt u ten zeerste aangeraden authenticatie op basis van certificaten te gebruiken. Zie [Key Vault-certificaat verificatie](https://github.com/Azure-Samples/key-vault-java-certificate-authentication)voor meer informatie.

8. Wanneer u dit voorbeeld project uitvoert, wordt u gevraagd om te verifiëren. Nadat de verificatie is geslaagd, wordt een toegangs token aangevraagd bij Azure AD. De informatie die wordt geretourneerd door Azure AD bevat een vernieuwings token dat is opgeslagen in het geconfigureerde exemplaar van Azure Key Vault.

## <a name="cloud-solution-provider-authentication"></a>Verificatie van Cloud Solution Provider

Partners van Cloud solution providers kunnen het vernieuwings token gebruiken dat is verkregen via het [partner toestemmings](#partner-consent) proces.

### <a name="samples-for-cloud-solution-provider-authentication"></a>Voor beelden voor Cloud Solution Provider-verificatie

We hebben de volgende voor beelden ontwikkeld om partners te helpen begrijpen hoe ze elke vereiste bewerking uit te voeren. Wanneer u de juiste oplossing in uw omgeving implementeert, is het belang rijk dat u een oplossing ontwikkelt die een klacht vormt voor uw coderings standaarden en beveiligings beleid.

## <a name="net-csp-authentication"></a>.NET (CSP-verificatie)

1. Als u dit nog niet hebt gedaan, voert u het [partner toestemmings proces](#partner-consent)uit.

2. Kloon de opslag plaats [Partner-Center-DotNet-samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met Visual Studio of de volgende opdracht

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. Open het `CSPApplication` project dat in de `Partner-Center-DotNet-Samples\secure-app-model\keyvault` map is gevonden.

4. Werk de toepassings instellingen in het [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/App.config) bestand bij.

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

5. Stel de juiste waarden in voor de variabelen **partner** en **CustomerId** in het [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CSPApplication/Program.cs) -bestand.

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. Wanneer u dit voorbeeld project uitvoert, wordt het vernieuwings token opgehaald dat is verkregen tijdens het partner toestemmings proces. Vervolgens wordt een toegangs token aangevraagd om te communiceren met de Partner Center SDK voor de naam van de partner. Ten slotte vraagt het een toegangs token om met Microsoft Graph namens de opgegeven klant te communiceren.

## <a name="java-csp-authentication"></a>Java (CSP-verificatie)

1. Als u dit nog niet hebt gedaan, voert u het [partner toestemmings proces](#partner-consent)uit.

2. Kloon de opslag plaats van de [Partner-Center-Java-voor beelden](https://github.com/Microsoft/Partner-Center-Java-Samples) met Visual Studio of de volgende opdracht

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. Open het `cspsample` project dat in de `Partner-Center-Java-Samples\secure-app-model\keyvault` map is gevonden.

4. Werk de toepassings instellingen in het bestand [Application. Properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cspsample/src/main/resources/application.properties) bij.

     ```java
    azuread.authority=https://login.microsoftonline.com
    keyvault.baseurl=
    keyvault.clientId=
    keyvault.clientSecret=
    partnercenter.accountId=
    partnercenter.clientId=
    partnercenter.clientSecret=
    ```

5. Wanneer u dit voorbeeld project uitvoert, wordt het vernieuwings token opgehaald dat is verkregen tijdens het partner toestemmings proces. Vervolgens wordt een toegangs token aangevraagd om te communiceren met de Partner Center SDK voor de naam van de partner.

6. Optioneel: Verwijder de *RunAzureTask* -en *RunGraphTask* -functie aanroepen als u wilt zien hoe u kunt communiceren met Azure Resource Manager en Microsoft Graph namens de klant.

## <a name="control-panel-provider-authentication"></a>Verificatie van provider van configuratie scherm

Leveranciers van het configuratie scherm moeten elke partner die ze ondersteunen de [partner toestemmings](#partner-consent) procedure uitvoeren. Zodra het vernieuwings token dat is verkregen via dat proces, wordt gebruikt om toegang te krijgen tot het partner centrum REST API en de .NET API.

### <a name="samples-for-cloud-panel-provider-authentication"></a>Voor beelden voor verificatie van provider van Cloud paneel

Om te helpen de leveranciers van het configuratie scherm begrijpen hoe elke vereiste bewerking moet worden uitgevoerd, hebben we de volgende voor beelden ontwikkeld. Wanneer u de juiste oplossing in uw omgeving implementeert, is het belang rijk dat u een oplossing ontwikkelt die een klacht vormt voor uw coderings standaarden en beveiligings beleid.

## <a name="net-cpv-authentication"></a>.NET (CPV-verificatie)

1. Ontwikkel en implementeer een proces voor partners van Cloud solution providers om de juiste toestemming te geven. Zie [partner instemming](#partner-consent)voor meer informatie over een voor beeld.

    > [!IMPORTANT]
    > Gebruikers referenties van een Cloud Solution Provider-partner mogen niet worden opgeslagen. Het vernieuwings token dat is verkregen via het partner toestemming proces moet worden opgeslagen en gebruikt om toegangs tokens aan te vragen voor interactie met een micro soft-API.

2. Kloon de opslag plaats [Partner-Center-DotNet-samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) met Visual Studio of de volgende opdracht

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-DotNet-Samples.git
    ```

3. Open het `CPVApplication` project dat in de `Partner-Center-DotNet-Samples\secure-app-model\keyvault` map is gevonden.

4. Werk de toepassings instellingen in het [App.config](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/App.config) bestand bij.

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

5. Stel de juiste waarden in voor de variabelen **partner** en **CustomerId** in het [Program.cs](https://github.com/Microsoft/Partner-Center-DotNet-Samples/blob/master/secure-app-model/keyvault/CPVApplication/Program.cs) -bestand.

    ```csharp
    // The following properties indicate which partner and customer context the calls are going to be made.
    string PartnerId = "<Partner tenant id>";
    string CustomerId = "<Customer tenant id>";
    ```

6. Wanneer u dit voorbeeld project uitvoert, wordt het vernieuwings token opgehaald voor de opgegeven partner. Vervolgens wordt een toegangs token aangevraagd om toegang te krijgen tot partner Center en Azure AD Graph namens de partner. De volgende taak die wordt uitgevoerd, is het verwijderen en maken van machtigings toekenningen in de Tenant van de klant. Omdat er geen relatie is tussen de leverancier van het configuratie scherm en de klant, moeten deze machtigingen worden toegevoegd met behulp van de partner centrum-API. In het volgende voor beeld ziet u hoe u dit kunt doen.

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

Nadat deze machtigingen zijn vastgesteld, voert het voor beeld bewerkingen uit met Azure AD Graph namens de klant.

## <a name="java-cpv-authentication"></a>Java (CPV-verificatie)

1. Ontwikkel en implementeer een proces voor partners van Cloud solution providers om de juiste toestemming te geven. Zie de [partner toestemming](#partner-consent)voor meer informatie en een voor beeld.

    > [!IMPORTANT]
    > Gebruikers referenties van een Cloud Solution Provider-partner mogen niet worden opgeslagen. Het vernieuwings token dat is verkregen via het partner toestemming proces moet worden opgeslagen en gebruikt om toegangs tokens aan te vragen voor interactie met een micro soft-API.

2. Kloon de opslag plaats van de [Partner-Center-Java-voor beelden](https://github.com/Microsoft/Partner-Center-Java-Samples) met de volgende opdracht

    ```bash
    git clone https://github.com/Microsoft/Partner-Center-Java-Samples.git
    ```

3. Open het `cpvsample` project dat in de `Partner-Center-Java-Samples\secure-app-model\keyvault` map is gevonden.

4. Werk de toepassings instellingen in het bestand [Application. Properties](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/resources/application.properties) bij.

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

    De waarde voor de `partnercenter.displayName` moet de weergave naam van uw Marketplace-toepassing zijn.

5. Stel de juiste waarden in voor de variabelen **partner** en **customerId** in het bestand [Program. java](https://github.com/Microsoft/Partner-Center-Java-Samples/blob/master/secure-app-model/keyvault/cpvsample/src/main/java/com/microsoft/store/samples/secureappmodel/cpvsample/Program.java) .

    ```java
    partnerId = "SPECIFY-THE-PARTNER-TENANT-ID-HERE";
    customerId = "SPECIFY-THE-CUSTOMER-TENANT-ID-HERE";
    ```

6. Wanneer u dit voorbeeld project uitvoert, wordt het vernieuwings token opgehaald voor de opgegeven partner. Vervolgens wordt een toegangs token aangevraagd om toegang te krijgen tot het partner centrum namens de partner. De volgende taak die wordt uitgevoerd, is het verwijderen en maken van machtigings toekenningen in de Tenant van de klant. Omdat er geen relatie is tussen de leverancier van het configuratie scherm en de klant, moeten deze machtigingen worden toegevoegd met behulp van de partner centrum-API. In het volgende voor beeld ziet u hoe u de machtigingen kunt verlenen.

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

Verwijder de opmerking over de functie aanroepen voor *RunAzureTask* en *RunGraphTask* als u wilt zien hoe u met Azure Resource Manager en Microsoft Graph kunt communiceren namens de klant.
