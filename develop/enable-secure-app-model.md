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
# <a name="enabling-the-secure-application-model-framework"></a>Het Secure Application Model-framework inschakelen

**Van toepassing op:**

- Partnercentrum

Micro soft introduceert een veilig, schaalbaar Framework voor het verifiëren van de CSP-partners (Cloud Solution Provider) en leveranciers van configuratie schermen (CPV) via de Microsoft Azure multi-factor Authentication-architectuur (MFA).

U kunt het nieuwe model gebruiken om de beveiliging van partner Center API-integratie aanroepen te verhogen. Dit helpt alle partijen (inclusief micro soft, CSP-partners en CPVs) om hun infra structuur en klant gegevens te beschermen tegen beveiligings Risico's.

## <a name="scope"></a>Bereik

Dit artikel heeft betrekking op de volgende actoren:

- CPV's (Control Panel Vendors)
  - Een CPV is een onafhankelijke softwareleverancier die apps ontwikkelt voor gebruik door CSP-partners om te integreren met Partner Center-API's.
  - Een CPV is geen CSP-partner met directe toegang tot het Partner Center-dashboard of API's.

- Indirecte CSP-providers en CSP direct-partners die App-ID + gebruikers authenticatie gebruiken en rechtstreeks integreren met partner Center-Api's.

## <a name="security-requirements"></a>Beveiligingsvereisten

Zie vereisten voor de beveiliging van [partners](/partner-center/partner-security-requirements)voor meer informatie over de beveiligings vereisten.

## <a name="secure-application-model"></a>Model voor beveiligde toepassing

Marketplace-toepassingen moeten de CSP-partner privileges imiteren om micro soft-Api's aan te roepen. Beveiligings aanvallen op deze gevoelige toepassingen kunnen leiden tot inbreuk op klant gegevens.

Down load het document voor het [Framework van beveiligde toepassingen](https://assetsprod.microsoft.com/secure-application-model-guide.pdf) voor een overzicht en Details van het nieuwe verificatie raamwerk. Dit document bevat principes en aanbevolen procedures om Marketplace-toepassingen duurzaam en robuust te maken tegen beveiligings problemen.

## <a name="samples"></a>Voorbeelden

In de volgende overzichts documenten en voorbeeld code wordt beschreven hoe partners het beveiligde toepassings model Framework kunnen implementeren:

- [Overzichts document van de CPV](https://assetsprod.microsoft.com/cpv-partner-application-overview.pdf)
- [CSP-overzichts document](https://assetsprod.microsoft.com/csp-partner-application-overview.pdf)
- [.NET-voor beelden](https://github.com/microsoft/Partner-Center-DotNet-Samples/tree/master/secure-app-model)
- [Java-voor beelden](https://github.com/microsoft/Partner-Center-Java-Samples/tree/master/secure-app-model)

    [!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

- [REST-instructies en voor beelden](#rest)
- [Power shell-instructies en voor beelden](#powershell)

## <a name="rest"></a>REST

Voer de volgende stappen uit om REST-aanroepen te maken met het Framework van het beveiligde toepassings model met voorbeeld code:

1. [Een web-app maken](#create-a-web-app)

2. [Een autorisatie code ophalen](#get-authorization-code)

3. [Een vernieuwings Token ophalen](#get-refresh-token)

4. [Een toegangstoken opvragen](#get-access-token)

5. [Make a Partner Center API call](#make-partner-center-api-calls) (Partner Center-API-aanroep uitvoeren)

> [!TIP]
> U kunt de Power shell-module van partner Center gebruiken om een autorisatie code en een vernieuwings token op te halen. U kunt deze optie kiezen in plaats van stap 2 en 3. Zie de [sectie en voor beelden van Power shell](#powershell)voor meer informatie.

### <a name="create-a-web-app"></a>Een web-app maken

U moet een web-app maken en registreren in het partner centrum voordat u REST-aanroepen maakt.

1. Meld u aan bij de [Azure-portal](https://portal.azure.com).

2. Maak een Azure Active Directory-app (Azure AD).

3. Geef overgedragen toepassings machtigingen voor de volgende resources, *afhankelijk van de vereisten van uw toepassing*. Indien nodig kunt u meer gedelegeerde machtigingen voor toepassings resources toevoegen.

   1. **Micro soft Partner Center** (sommige tenants geven dit weer als **SampleBECApp**)

   2. **Azure-beheer-api's** (als u van plan bent om Azure-api's aan te roepen)

   3. **Windows Azure Active Directory**

4. Zorg ervoor dat de Home-URL van uw app is ingesteld op een eind punt waarop een live web-app wordt uitgevoerd. Deze app moet de [autorisatie code](#get-authorization-code) van de Azure AD-aanmeldings oproep accepteren. In de voorbeeld code in [de volgende sectie](#get-authorization-code)wordt de Web-App bijvoorbeeld uitgevoerd op `https://localhost:44395/` .

5. Houd rekening met de volgende informatie van de instellingen van uw web-app in azure AD:

   - Toepassings-id
   - Toepassingsgeheim

> [!NOTE]
> Het is raadzaam om [een certificaat als uw toepassings geheim te gebruiken](/azure/active-directory/develop/active-directory-certificate-credentials). U kunt echter ook een toepassings sleutel maken in de Azure Portal. In de voorbeeld code in [de volgende sectie](#get-authorization-code) wordt een toepassings sleutel gebruikt.

### <a name="get-authorization-code"></a>Autorisatiecode verkrijgen

U moet een autorisatie code voor uw web-app verkrijgen om te accepteren van de Azure AD-aanmeldings oproep:

1. Meld u aan bij Azure AD via de volgende URL: [https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1](https://login.microsoftonline.com/common/oauth2/authorize?client_id=Application-Id&response_mode=form_post&response_type=code%20id_token&scope=openid%20profile&nonce=1) . Zorg ervoor dat u zich aanmeldt met het gebruikers account waarmee u partner Center-API-aanroepen (zoals een beheer agent of een account van een verkoop medewerker) gaat maken.

2. Vervang de **toepassings-id** door uw Azure AD-App-ID (GUID).

3. Wanneer u hierom wordt gevraagd, meldt u zich aan met uw gebruikers account waarvoor MFA is geconfigureerd.

4. Wanneer u hierom wordt gevraagd, voert u aanvullende MFA-gegevens (telefoon nummer of e-mail adres) in om uw aanmelding te controleren.

5. Nadat u bent aangemeld, stuurt de browser de oproep naar het eind punt van de web-app om met uw autorisatie code. Met de volgende voorbeeld code wordt bijvoorbeeld omgeleid naar `https://localhost:44395/` .

#### <a name="authorization-code-call-trace"></a>Tracering van autorisatie code aanroepen

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

### <a name="get-refresh-token"></a>Vernieuwings Token ophalen

U moet vervolgens uw autorisatie code gebruiken om een vernieuwings token op te halen:

1. Maak een POST-aanroep naar het Azure AD-aanmeld eindpunt `https://login.microsoftonline.com/CSPTenantID/oauth2/token` met de autorisatie code. Zie de volgende [voorbeeld aanroep](#sample-refresh-call)voor een voor beeld.

2. Let op het vernieuwings token dat wordt geretourneerd.

3. Sla het vernieuwings token op in Azure Key Vault. Zie de documentatie van de [Key Vault-API](/rest/api/keyvault/)voor meer informatie.

> [!IMPORTANT]
> Het vernieuwingstoken moet [als een geheim worden opgeslagen](/rest/api/keyvault/setsecret/setsecret) in Key Vault.

#### <a name="sample-refresh-call"></a>Voor beeld van een vernieuwings oproep

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

Antwoord op tijdelijke aanduiding:

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

Antwoord tekst:

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3599","ext_expires_in":"3599","expires_on":"1547579127","not_before":"1547575227","resource":"https://api.partnercenter.microsoft.com","access_token":"Access
```

### <a name="get-access-token"></a>Toegangs Token ophalen

U moet een toegangs token verkrijgen voordat u aanroepen naar de partner centrum-Api's kunt maken. U moet een vernieuwings token gebruiken om een toegangs token te verkrijgen, omdat het toegangs token over het algemeen een zeer beperkte levens duur heeft (bijvoorbeeld minder dan een uur).

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

Antwoord op tijdelijke aanduiding:

```http
HTTP/1.1 200 OK
Cache-Control: no-cache, no-store
Content-Type: application/json; charset=utf-8
```

Antwoord tekst:

```http
{"token_type":"Bearer","scope":"user_impersonation","expires_in":"3600","ext_expires_in":"3600","expires_on":"1547581389","not_before":"1547577489","resource":"https://api.partnercenter.microsoft.com","access_token":"AccessTokenValue","id_token":"IDTokenValue"}
```

### <a name="make-partner-center-api-calls"></a>Partner Center-API-aanroepen maken

U moet uw toegangs token gebruiken om de Api's van het partner centrum aan te roepen. Raadpleeg de volgende voorbeeld aanroep.

#### <a name="example-partner-center-api-call"></a>Voor beeld van partner Center API-aanroep

```http
GET https://api.partnercenter.microsoft.com/v1/customers/CustomerTenantId/users HTTP/1.1
Authorization: Bearer AccessTokenValue
Accept: application/json
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="powershell"></a>PowerShell

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

U kunt de [Power shell-module van partner Center](https://www.powershellgallery.com/packages/PartnerCenter) gebruiken om de vereiste infra structuur te verlagen voor het uitwisselen van een autorisatie code voor een toegangs token. Deze methode is optioneel voor het maken van [rest-aanroepen van het partner centrum](#rest).

Zie [Secure app model](/powershell/partnercenter/secure-app-model) Power shell Documentation (Engelstalig) voor meer informatie over dit proces.

1. Installeer de Power shell-modules voor Azure AD en partner Center.

    ```powershell
    Install-Module AzureAD
    ```

    ```powershell
    Install-Module PartnerCenter
    ```

2. Gebruik de opdracht **[New-PartnerAccessToken](/powershell/module/partnercenter/new-partneraccesstoken)** om het toestemming proces uit te voeren en het vereiste vernieuwings token vast te leggen.

    ```powershell
    $credential = Get-Credential

    New-PartnerAccessToken -ApplicationId 'xxxx-xxxx-xxxx-xxxx' -Scopes 'https://api.partnercenter.microsoft.com/user_impersonation' -ServicePrincipal -Credential $credential -Tenant 'yyyy-yyyy-yyyy-yyyy' -UseAuthorizationCode
    ```

    > [!NOTE]
    > De para meter **ServicePrincipal** wordt gebruikt met de opdracht **New-PartnerAccessToken** , omdat er een Azure AD-app met een type **Web/API** wordt gebruikt. Voor dit type app moeten een client-id en een geheim worden opgenomen in de aanvraag van de toegangs token. Wanneer de **Get-Credential-** opdracht wordt aangeroepen, wordt u gevraagd om een gebruikers naam en wacht woord in te voeren. Voer de toepassings-id in als de gebruikers naam. Voer het toepassings geheim in als het wacht woord. Wanneer de opdracht **New-PartnerAccessToken** wordt aangeroepen, wordt u gevraagd om de referenties opnieuw in te voeren. Voer de referenties in voor het service account dat u gebruikt. Dit service account moet een partner account zijn met de juiste machtigingen.

3. Kopieer de waarde van het vernieuwings token.

    ```powershell
    $token.RefreshToken | clip
    ```

U moet de waarde van het vernieuwings token opslaan in een beveiligde opslag plaats, zoals Azure Key Vault. Zie het artikel [multi-factor Authentication](/powershell/partnercenter/multi-factor-auth) voor meer informatie over het gebruik van de module veilige toepassing met Power shell.
