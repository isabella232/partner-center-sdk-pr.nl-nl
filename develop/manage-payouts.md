---
title: Uitbetalingen beheren met behulp van de Uitbetalingsservice-API
description: Meer informatie over het gebruik van Partner Center Uitbetalingsservice-API voor toegang tot uitbetalingsgegevens
ms.date: 06/23/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: jasongroce
ms.author: sabaja
ms.openlocfilehash: b9bdc6da64a79f4f35466fb62662b086a8e1ab3cadc99c7ca685303752f9d166
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996289"
---
# <a name="manage-payouts-using-the-payout-service-api"></a>Uitbetalingen beheren met behulp van de Uitbetalingsservice-API

In dit artikel wordt uitgelegd hoe u toegang hebt tot uitbetalingsgegevens via de Uitbetalingsservice-API's in plaats van de Partner Center gebruikersinterface. Deze API's bieden een programmatische manier om de mogelijkheid te bieden van de [functie Gegevens exporteren](https://partner.microsoft.com/dashboard/payouts/reports/incentiveexport) in Partner Center.

## <a name="available-apis"></a>Beschikbare API's

Bekijk alle beschikbare API's op [Uitbetalingen van partners.](/rest/api/partner-center/partner-payouts)

## <a name="prerequisites"></a>Vereisten

- [Registreer een toepassing met AAD/Microsoft Identity](/graph/auth-register-app-v2) in de Azure Portal en voeg de juiste eigenaren en rollen toe aan de toepassing.
- Installeer [Visual Studio](https://visualstudio.microsoft.com/downloads/).

## <a name="register-an-application-with-the-microsoft-identity-platform"></a>Een toepassing registreren bij het Microsoft Identity Platform

De [Microsoft identity platform](/azure/active-directory/develop/v2-overview) helpt u bij het bouwen van toepassingen waarmee uw gebruikers en klanten zich kunnen aanmelden met hun Microsoft-identiteiten of sociale accounts en geautoriseerde toegang bieden tot uw eigen API's of Microsoft-API's zoals Microsoft Graph.

1. Meld u bij de [Azure-portal](https://portal.azure.com/) aan met een werk- of schoolaccount of een persoonlijk Microsoft-account.

   Als u via uw account toegang hebt tot meer dan één tenant, selecteert u uw account in de rechterbovenhoek en stelt u uw portalsessie in op de juiste Azure AD-tenant.

2. Selecteer in het linkernavigatiedeelvenster de Azure Active Directory service, selecteer **App-registraties** en vervolgens **Nieuwe registratie.** De **pagina Een toepassing registreren** wordt weergegeven.

   :::image type="content" source="./images/manage-payouts/new-app-registration.png" alt-text="Schermopname van het scherm Een app registreren in de Azure Portal.":::

3. Voer de registratiegegevens van uw toepassing in:

   - Naam: Voer een betekenisvolle toepassingsnaam in die wordt weergegeven voor gebruikers van de app.
   - Ondersteunde accounttypen: selecteer welke accounts door uw toepassing worden ondersteund.

    | **Ondersteunde accounttypen**                             | **Beschrijving**                                                                                            |
    |---------------------------------------------------------|------------------------------------------------------------------------------------------------------------|
    | Alleen accounts in deze organisatiemap          | Selecteer deze optie als u een LOB-toepassing (Line-Of-Business) bouwt. Deze optie is niet beschikbaar als u de toepassing niet in een map registreert. Deze optie wordt alleen toegewezen aan Azure AD met één tenant.  Deze optie is standaard tenzij u de app registreert buiten een map. In gevallen waarbij de app is geregistreerd buiten een map, is de standaardinstelling Azure AD met meerdere tenants en persoonlijke Microsoft-accounts.             |
    | Accounts in elke organisatiemap                | Selecteer deze optie als u alle zakelijke klanten en onderwijsinstellingen wilt bereiken.  Deze optie wordt alleen toegewezen aan Azure AD met meerdere tenants. Als u de app hebt geregistreerd als een Azure AD met één tenant, kunt u deze bijwerken naar Azure AD met meerdere tenants en later weer teruggaan naar één tenant op de blade Verificatie.                                                                                                                                                  |
    | Accounts in elke organisatiemap en persoonlijke Microsoft-accounts | Selecteer deze optie om de breedste groep klanten te bereiken. Deze optie wordt toegewezen aan Azure AD met meerdere tenants en persoonlijke Microsoft-accounts.  Als u de app hebt geregistreerd als Azure AD-account met meerdere tenants en persoonlijke Microsoft-accounts, kunt u deze selectie niet wijzigen in de gebruikersinterface. In plaats hiervan moet u de editor voor het toepassingsmanifest gebruiken om de ondersteunde accounttypen te wijzigen.                                                                          |

   - *(optioneel)* Omleidings-URI: selecteer het type app dat u bouwt, webclient of openbare client (mobiele & desktop) en voer vervolgens de omleidings-URI (of antwoord-URL) voor uw toepassing in. (De omleidings-URL is waar het verificatie-antwoord wordt verzonden nadat de gebruiker is geverifieerd.) 

      Geef voor webtoepassingen de basis-URL van de app op. `http://localhost:31544` kan bijvoorbeeld de URL zijn van een web-app die op uw lokale machine wordt uitgevoerd. Gebruikers moeten deze URL gebruiken om zich bij een webclienttoepassing aan te melden.
      Geef voor openbare clienttoepassingen de URI op die in Azure Active Directory wordt gebruikt om tokenantwoorden te retourneren. Voer een waarde in die specifiek is voor de toepassing, zoals `myapp://auth`.

4. Selecteer **Registreren**. Azure AD wijst een unieke toepassings-id (client-id) toe aan uw toepassing en de overzichtspagina van de toepassing wordt geladen.

   :::image type="content" source="./images/manage-payouts/register-an-application.png" alt-text="<alt-tekst>":::

5. Als u mogelijkheden aan uw toepassing wilt toevoegen, kunt u andere configuratieopties selecteren, zoals huisstijl, certificaten en geheimen, API-machtigingen en meer.

## <a name="platform-specific-properties"></a>Platformspecifieke eigenschappen

In de volgende tabel ziet u de eigenschappen die u moet configureren en kopiëren voor verschillende soorten apps. **Toegewezen betekent** dat u de waarde moet gebruiken die is toegewezen door Azure AD.

| App-type              | Platform | (Client-)id van de app | Clientgeheim | Omleidings-URI/URL | Impliciete Flow                                                         |
|-----------------------|----------|-------------------------|---------------|------------------|-----------------------------------------------------------------------|
| Native/mobiel         | Systeemeigen   | Toegewezen                | No            | Toegewezen         | No                                                                    |
| Web-app               | Web      | Toegewezen                | Ja           | Ja              | Optionele Open ID Verbinding maken middleware gebruikt standaard hybride stroom (Ja) |
| App met één pagina (SPA) | Web      | Toegewezen                | Ja           | Ja              | Ja, SPA's gebruiken Open ID Verbinding maken impliciete Flow                            |
| Service/Daemon        | Web      | Toegewezen                | Ja           | Ja              | Nee                                                                    |

## <a name="create-a-service-principal"></a>Een service-principal maken

Als u toegang wilt krijgen tot resources in uw abonnement, moet u een rol toewijzen aan de toepassing. Zie Ingebouwde [Azure-rollen](/azure/role-based-access-control/built-in-roles)voor hulp bij het bepalen welke rol de juiste machtigingen voor de toepassing biedt.

> [!NOTE]
> U kunt het bereik instellen op het niveau van het abonnement, de resourcegroep of de resource. Machtigingen worden overgenomen naar lagere bereikniveaus. Als u bijvoorbeeld een toepassing toevoegt aan de rol Lezer voor een resourcegroep, kan deze de resourcegroep en alle resources die deze bevat lezen.

1. Selecteer in Azure Portal het bereikniveau waar u de toepassing aan wilt toewijzen. Als u bijvoorbeeld een rol wilt toewijzen in het **abonnementsbereik,** zoekt en selecteert u Abonnementen of **selecteert** u Abonnementen op de startpagina.

   :::image type="content" source="./images/manage-payouts/search-for-subscriptions.png" alt-text="Schermopname van de zoekopdracht in het scherm Abonnementen.":::

2. Selecteer het abonnement waar u de toepassing aan wilt toewijzen.

   :::image type="content" source="./images/manage-payouts/internal-testing-subscription.png" alt-text="Schermopname van het scherm Abonnementen met de vlag Intern testen ingesteld op true.":::

> [!NOTE]
> Als u het abonnement dat u zoekt niet ziet, selecteert u het algemene abonnementsfilter en zorgt u ervoor dat het gezochte abonnement is geselecteerd voor de portal.

3. Selecteer **Toegangsbeheer (IAM)** en selecteer vervolgens **Roltoewijzing toevoegen**.

4. Selecteer de rol die u aan de toepassing wilt toewijzen. Als u bijvoorbeeld wilt toestaan dat de toepassing acties uitvoert zoals opnieuw opstarten, exemplaren starten en stoppen, selecteert u de rol Inzender. Meer informatie over [beschikbare rollen.](/azure/role-based-access-control/built-in-roles)

   Standaard worden Azure AD-toepassingen niet weergegeven in de beschikbare opties. Als u uw toepassing wilt zoeken, zoekt u op de naam en selecteert u deze in de resultaten. In de onderstaande schermopname `example-app` ziet u de AAD-app die u hebt geregistreerd.

   :::image type="content" source="./images/manage-payouts/add-role-assignment.png" alt-text="Schermopname van de gebruikersinterface voor het toevoegen van een roltoewijzing voor een testtoepassing.":::

5. Selecteer **Opslaan**. Vervolgens ziet u uw toepassing in de lijst met gebruikers met een rol voor dat bereik.

   U kunt beginnen met het gebruik van uw service-principal om uw scripts of apps uit te voeren. Als u de machtigingen van uw service-principal wilt beheren, bekijkt u de gebruikersstatus, controleert u machtigingen, bekijkt u aanmeldingsgegevens en [meer),](https://portal.azure.com)bekijkt u uw Bedrijfstoepassingen in de Azure Portal .

## <a name="set-up-api-permissions"></a>API-machtigingen instellen

Deze sectie bevat instructies voor het instellen van de vereiste API-machtigingen. Zie verificatie voor meer informatie Partner Center het instellen [van API Partner-API machtigingen.](/partner/develop/api-authentication)

**Machtiging verlenen aan Graph API**

1. Open de [App-registraties](https://go.microsoft.com/fwlink/?linkid=2083908) in de Azure Portal.

2. Selecteer een toepassing of [maak een app](/azure/active-directory/develop/quickstart-register-app) als u er nog geen hebt.

3. Selecteer op de pagina Overzicht van de toepassing onder **Beheren** de optie **API-machtigingen** en vervolgens **Een machtiging toevoegen.**

4. Selecteer **Microsoft Graph** in de lijst met beschikbare API's.

5. Selecteer **Gedelegeerde machtigingen en** voeg de vereiste machtigingen toe. Zie App-toegang [configureren voor meer informatie.](/azure/active-directory/develop/quickstart-configure-app-access-web-apis)

   :::image type="content" source="./images/manage-payouts/graph-request-api-permissions.png" alt-text="Schermopname van het scherm voor aanvraagmachtigingen in de Azure Portal met Microsoft Graph geselecteerd.":::

**Toestemming voor API-toegang tot Partner Center API via AAD-app**

6. Selecteer voor uw toepassing **API-machtigingen** en selecteer vervolgens in het scherm API-machtigingen aanvragen de optie **Een** machtiging toevoegen en vervolgens **API's die mijn organisatie gebruikt.**

7. Zoek naar **Microsoft Partner (Microsoft Ontwikkelaarscentrum) API (4990cffe-04e8-4e8b-808a-1175604b879f)**.

   :::image type="content" source="./images/manage-payouts/partner-api-request-permissions.png" alt-text="Schermopname van het scherm API-machtigingen met Microsoft Partner geselecteerd.":::

8. Stel gedelegeerde machtigingen in op **Partner Center**.

   :::image type="content" source="./images/manage-payouts/partner-api-request-permissions.png" alt-text="Schermopname van de gedelegeerde machtigingen die zijn geselecteerd Partner Center in het scherm API-machtigingen aanvragen.":::

9. Verleen **beheerders toestemming** voor de API's.

   :::image type="content" source="./images/manage-payouts/api-permissions.png" alt-text="Schermopname van de schakelknop voor Beheerders toestemming op het scherm API-machtigingen.":::

   Controleer of toestemming van de beheerder is ingeschakeld in het scherm Beheerdersmachtigingsstatus.

   :::image type="content" source="./images/manage-payouts/admin-consent-verification.png" alt-text="Schermopname van het scherm Toestemmingsstatus beheerder":::

10. Zorg ervoor **dat in** de sectie Verificatie de optie **Openbare clientstromen** toestaan is ingesteld op **Ja.**

    :::image type="content" source="./images/manage-payouts/allow-public-client-flows.png" alt-text="Schermopname van het scherm Verificatie met Openbare clientstromen toestaan ingesteld op Ja.":::

## <a name="run-the-sample-code-in-visual-studio"></a>De voorbeeldcode uitvoeren in Visual Studio

Voorbeeldcode die laat zien hoe de API kan worden gebruikt voor betalings- en transactiegeschiedenis, vindt u in de [partnercentrum-uitbetaling-API's](https://github.com/microsoft/Partner-Center-Payout-APIs) GitHub repo.

### <a name="sample-code-notes"></a>Opmerkingen bij voorbeeldcode

- Configuratie van clientgeheimen en certificaten zoals besproken in de sectie Verificatie: twee opties van Een [service-principal maken in](/azure/active-directory/develop/howto-create-service-principal-portal) de Azure Portal is niet vereist.
- Accounts met meervoudige verificatie (MFA) worden momenteel niet ondersteund en veroorzaken een fout.
- Uitbetalings-API ondersteunt alleen referenties op basis van gebruikers/wachtwoorden.

## <a name="next-steps"></a>Volgende stappen

- [Gebruik de portal voor het maken van een Azure AD-toepassing en service-principal die toegang hebben tot resources](/azure/active-directory/develop/howto-create-service-principal-portal)
- [Een toepassing registreren bij het Microsoft Identity Platform](/graph/auth-register-app-v2)
- [Een clienttoepassing configureren voor toegang tot een web-API](/azure/active-directory/develop/quickstart-configure-app-access-web-apis)
