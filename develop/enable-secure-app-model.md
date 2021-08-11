---
title: Beveiligd toepassingsmodel inschakelen
description: Beveilig uw Partner Center apps en configuratiescherm.
ms.date: 01/20/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 9974237f7d4234b782a5b17a65fd52b9024315f848b721c73f4e1d59b69b2930
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994792"
---
# <a name="enabling-the-secure-application-model-framework"></a>Het Secure Application Model-framework inschakelen

Microsoft introduceert een veilig, schaalbaar framework voor de verificatie van CSP-partners (Cloud Solution Provider) en configuratieschermleveranciers (CPV) via de architectuur van Microsoft Azure Active Directory Multi-Factor Authentication (MFA).

U kunt het nieuwe model gebruiken om de beveiliging voor api-integratie-aanroepen Partner Center verhogen. Hiermee kunnen alle partijen (inclusief Microsoft, CSP-partners en CPV's) hun infrastructuur en klantgegevens beschermen tegen beveiligingsrisico's.

## <a name="scope"></a>Bereik

Dit artikel heeft betrekking op de volgende actoren:

- CPV's (Control Panel Vendors)
  - Een CPV is een onafhankelijke softwareleverancier die apps ontwikkelt voor gebruik door CSP-partners om te integreren met Partner Center-API's.
  - Een CPV is geen CSP-partner met directe toegang tot het Partner Center-dashboard of API's.

- Indirecte CSP-providers en directe CSP-partners die app-id en gebruikersverificatie gebruiken en rechtstreeks integreren met Partner Center API's.

## <a name="security-requirements"></a>Beveiligingsvereisten

Zie Beveiligingsvereisten van partners [voor meer informatie over beveiligingsvereisten.](/partner-center/partner-security-requirements)

## <a name="secure-application-model"></a>veilig toepassingsmodel

Marketplace-toepassingen moeten de bevoegdheden van de CSP-partner imiteren om Microsoft API's aan te roepen. Beveiligingsaanvallen op deze gevoelige toepassingen kunnen leiden tot het compromitteerden van klantgegevens.

Voor een overzicht en details van het nieuwe verificatiekader downloadt u het [document veilig toepassingsmodel framework.](https://assetsprod.microsoft.com/secure-application-model-guide.pdf) Dit document bevat principes en best practices om Marketplace-toepassingen duurzaam en robuust te maken tegen beveiligingsrisico's.

## <a name="samples"></a>Voorbeelden

In de volgende overzichtsdocumenten en voorbeeldcode wordt beschreven hoe partners het veilig toepassingsmodel implementeren:

- [Overzichtsdocument voor CPV](https://assetsprod.microsoft.com/cpv-partner-application-overview.pdf)
- [CSP-overzichtsdocument](https://assetsprod.microsoft.com/csp-partner-application-overview.pdf)
- [.NET-voorbeelden](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model)
- [Java-voorbeelden](https://github.com/microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model)

    [!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

- [REST-instructies en -voorbeelden](#rest)
- [PowerShell-instructies en -voorbeelden](#powershell)

## <a name="rest"></a>REST

Volg deze stappen om REST-aanroepen veilig toepassingsmodel framework met voorbeeldcode te maken:

1. [Een web-app maken](#create-a-web-app)

2. [Een autorisatiecode verkrijgen](#get-authorization-code)

3. [Een vernieuwings token krijgen](#get-refresh-token)

4. [Een toegangstoken opvragen](#get-access-token)

5. [Make a Partner Center API call](#make-partner-center-api-calls) (Partner Center-API-aanroep uitvoeren)

> [!TIP]
> U kunt de PowerShell Partner Center module gebruiken om een autorisatiecode en een vernieuwings token op te halen. U kunt deze optie kiezen in plaats van stap 2 en 3. Zie de sectie [PowerShell](#powershell)en voorbeelden voor meer informatie.

### <a name="create-a-web-app"></a>Een web-app maken

U moet een web-app maken en registreren in Partner Center voordat u REST-aanroepen doet.

1. Meld u aan bij de [Azure-portal](https://portal.azure.com).

2. Maak een Azure Active Directory -app (Azure AD).

3. Geef gedelegeerde toepassingsmachtigingen voor de volgende resources, *afhankelijk van de vereisten van uw toepassing.* Indien nodig kunt u meer gedelegeerde machtigingen toevoegen voor toepassingsresources.

   1. **Microsoft Partner Center** (sommige tenants geven dit weer als **SampleBECApp**)

   2. **Azure Management-API's** (als u azure-API's wilt aanroepen)

   3. **Windows Azure Active Directory**

4. Zorg ervoor dat de start-URL van uw app is ingesteld op een eindpunt waarop een live web-app wordt uitgevoerd. Deze app moet de autorisatiecode [van](#get-authorization-code) de Azure AD-aanmeldingsoproep accepteren. In de voorbeeldcode in de volgende sectie [wordt](#get-authorization-code)de web-app bijvoorbeeld uitgevoerd op `https://localhost:44395/` .

5. Let op de volgende informatie uit de instellingen van uw web-app in Azure AD:

   - Toepassings-id
   - Toepassingsgeheim

> [!NOTE]
> Het wordt aanbevolen om [een certificaat te gebruiken als uw toepassingsgeheim](/azure/active-directory/develop/active-directory-certificate-credentials). U kunt echter ook een toepassingssleutel maken in de Azure Portal. In de voorbeeldcode in [de volgende sectie wordt](#get-authorization-code) een toepassingssleutel gebruikt.

### <a name="get-authorization-code"></a>Autorisatiecode verkrijgen

U moet een autorisatiecode voor uw web-app krijgen die u kunt accepteren via de Azure AD-aanmeldingsoproep:

1. Meld u aan bij Azure AD via de volgende URL: [https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1) . Meld u aan met het gebruikersaccount van waaruit u API-aanroepen Partner Center (zoals een beheerderagent of verkoopagentaccount).

2. Vervang **Application-Id door** uw Azure AD-app-id (GUID).

3. Meld u aan met uw gebruikersaccount waarop MFA is geconfigureerd wanneer u hier om wordt gevraagd.

4. Wanneer u hier om wordt gevraagd, voert u aanvullende MFA-gegevens (telefoonnummer of e-mailadres) in om uw aanmelding te verifiëren.

5. Nadat u bent aangemeld, stuurt de browser de aanroep om naar het eindpunt van uw web-app met uw autorisatiecode. Met de volgende voorbeeldcode wordt bijvoorbeeld omgeleid naar `https://localhost:44395/` .

#### <a name="authorization-code-call-trace"></a>Trace voor aanroepen van autorisatiecode

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

### <a name="get-refresh-token"></a>Vernieuwings token op halen

Vervolgens moet u uw autorisatiecode gebruiken om een vernieuwings token op te halen:

1. Maak een POST-aanroep naar het Azure AD-aanmeldings-eindpunt `https://login.microsoftonline.com/CSPTenantID/oauth2/token` met de autorisatiecode. Zie de volgende voorbeeldoproep voor [een voorbeeld.](#sample-refresh-call)

2. Let op het vernieuwings token dat wordt geretourneerd.

3. Sla het vernieuwingstoken op in Azure Key Vault. Zie de api-documentatie [Key Vault meer informatie.](/rest/api/keyvault/)

> [!IMPORTANT]
> Het vernieuwingstoken moet [als een geheim worden opgeslagen](/rest/api/keyvault/setsecret/setsecret) in Key Vault.

#### <a name="sample-refresh-call"></a>Voorbeeld van vernieuwingsoproep

Aanvraag voor tijdelijke aanduiding:

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 966
Expect: 100-continue
```

Aanvraagtekst:

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id&client_secret=Application-Secret&grant_type=authorization_code&code=AuthorizationCodeValue
```

Tijdelijke aanduiding voor antwoord:

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

Antwoord body:

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3599","ext_expires_in":"3599","expires_on":"1547579127","not_before":"1547575227","resource":"https://api.partnercenter.microsoft.com","access_token":"Access
```

### <a name="get-access-token"></a>Toegangs token krijgen

U moet een toegangs token verkrijgen voordat u de api's van Partner Center aanroepen. U moet een vernieuwingstoken gebruiken om een toegangstoken te verkrijgen, omdat toegangstokens over het algemeen een zeer beperkte levensduur hebben (bijvoorbeeld minder dan een uur).

Aanvraag voor tijdelijke aanduiding:

```http
POST https://login.microsoftonline.com/CSPTenantID/oauth2/token HTTP/1.1
Content-Type: application/x-www-form-urlencoded
Host: login.microsoftonline.com
Content-Length: 1212
Expect: 100-continue
```

Aanvraagtekst:

```http
resource=https%3a%2f%2fapi.partnercenter.microsoft.com&client_id=Application-Id &client_secret= Application-Secret&grant_type=refresh_token&refresh_token=RefreshTokenVlaue&scope=openid
```

Tijdelijke aanduiding voor antwoord:

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

Antwoord body:

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3600","ext_expires_in":"3600","expires_on":"1547581389","not_before":"1547577489","resource":"https://api.partnercenter.microsoft.com","access_token":"AccessTokenValue","id_token":"IDTokenValue"}
```

### <a name="make-partner-center-api-calls"></a>API Partner Center-aanroepen maken

U moet uw toegangs token gebruiken om de api's Partner Center aan te roepen. Zie de volgende voorbeeldoproep.

#### <a name="example-partner-center-api-call"></a>Voorbeeld van Partner Center API-aanroep

```http
GET https://api.partnercenter.microsoft.com/v1/customers/CustomerTenantId/users HTTP/1.1
Authorization: Bearer AccessTokenValue
Accept: application/json
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

U kunt de [PowerShell Partner Center module gebruiken](https://www.powershellgallery.com/packages/PartnerCenter) om de vereiste infrastructuur te verminderen voor het uitwisselen van een autorisatiecode voor een toegangs token. Deze methode is optioneel voor het maken van [Partner Center REST-aanroepen.](#rest)

Zie PowerShell-documentatie voor [Secure App Model](/powershell/partnercenter/secure-app-model) voor meer informatie over dit proces.

1. Installeer de Azure AD- en Partner Center PowerShell-modules.

    ```powershell
    Install-Module AzureAD
    ```

    ```powershell
    Install-Module PartnerCenter
    ```

2. Gebruik de **[opdracht New-PartnerAccessToken om](/powershell/module/partnercenter/new-partneraccesstoken)** het toestemmingsproces uit te voeren en het vereiste vernieuwingstoken vast te leggen.

    ```powershell
    $credential = Get-Credential

    $token = New-PartnerAccessToken -ApplicationId 'xxxx-xxxx-xxxx-xxxx' -Scopes 'https://api.partnercenter.microsoft.com/user_impersonation' -ServicePrincipal -Credential $credential -Tenant 'yyyy-yyyy-yyyy-yyyy' -UseAuthorizationCode
    ```

    > [!NOTE]
    > De **parameter ServicePrincipal** wordt gebruikt met de **opdracht New-PartnerAccessToken** omdat er een Azure AD-app met een type **web/API** wordt gebruikt. Dit type app vereist dat een client-id en -geheim worden opgenomen in de toegangsaanvraag voor een token. Wanneer de **opdracht Get-Credential** wordt aangeroepen, wordt u gevraagd een gebruikersnaam en wachtwoord in te voeren. Voer de toepassings-id in als de gebruikersnaam. Voer het toepassingsgeheim in als het wachtwoord. Wanneer de **opdracht New-PartnerAccessToken** wordt aangeroepen, wordt u opnieuw gevraagd referenties in te voeren. Voer de referenties in voor het serviceaccount dat u gebruikt. Dit serviceaccount moet een partneraccount zijn met de juiste machtigingen.

3. Kopieer de waarde van het vernieuwings token.

    ```powershell
    $token.RefreshToken | clip
    ```

U moet de waarde van het vernieuwingtoken opslaan in een beveiligde opslagplaats, zoals Azure Key Vault. Zie het artikel [Multi-Factor Authentication](/powershell/partnercenter/multi-factor-auth) voor meer informatie over het gebruik van de module voor beveiligde toepassingen met PowerShell.
