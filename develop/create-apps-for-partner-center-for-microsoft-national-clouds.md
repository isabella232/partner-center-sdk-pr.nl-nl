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
# <a name="register-app-details-for-partner-center-for-microsoft-national-cloud-through-the-azure-portal"></a>App-gegevens voor Partner Center voor Microsoft National Cloud registreren via de Azure Portal

**Van toepassing op**: Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Ontwikkelaars moeten details over hun app registreren bij Azure AD via de Azure Portal. Dit zorgt ervoor dat alleen opgegeven apps verbinding kunnen maken met partner- en klantgegevens.

Voor Partner Center voor Microsoft Cloud for US Government moet u momenteel apps beheren via PowerShell. Zie de referentiedocumentatie Azure PowerShell [meer informatie.](/powershell/module/Azuread/#applications)

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Let op de volgende aanvullende vereisten wanneer u een app maakt voor Partner Center voor Microsoft Cloud Duitsland of wanneer Partner Center voor Microsoft Cloud for US Government.

## <a name="web-apps"></a>Web-apps

Gebruik voor web-apps de volgende procedures om uw toepassings-id te registreren.

### <a name="create-or-update-web-app"></a>Web-app maken of bijwerken

1. Navigeer [naar Azure Portal - App-registraties](https://go.microsoft.com/fwlink/?linkid=2083908) om uw app te registreren. Meld u aan bij Azure Portal met een werk- of schoolaccount of een persoonlijk Microsoft-account.

2. Selecteer **Nieuwe registratie**. Zie Snelstart: Een toepassing registreren met de Microsoft identity platform voor [meer Microsoft identity platform.](/azure/active-directory/develop/quickstart-register-app)

### <a name="configure-api-access-permissions-for-web-app"></a>API-toegangsmachtigingen voor web-app configureren

1. Kies uw app. Ga naar **Instellingen** van de web-app.

2. Kies **in de sectie API-toegang** de optie Vereiste **machtigingen**

3. Voor Windows Machtigingen voor Azure Active Directory:

    1. Kies **Windows Azure Active Directory machtigingen**.

    2. Selecteer **in Toepassingsmachtigingen** de optie Mapgegevens lezen.

    3. Sla de machtigingen op.

4. Noteer de toepassings-id in **de sectie** Eigenschappen van uw web-app.

### <a name="add-a-secret-key-to-your-app"></a>Een geheime sleutel toevoegen aan uw app

1. Ga naar de **sectie Sleutels** van uw web-app.

2. Voer een sleutelbeschrijving in en selecteer de duur als 1 of 2 jaar, zoals u dat nodig hebt.

3. Sla de geheime sleutelwaarde op en kopieer deze. **Deze waarde wordt niet meer weergegeven wanneer u deze pagina verlaat.**

U moet de volgende gegevens uit de configuratie van de web-app hebben:

- Toepassings-id
- Toepassingsgeheim

### <a name="register-the-web-app-in-partner-center"></a>De web-app registreren in Partner Center

1. Meld u aan bij [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com).

2. Kies **Dashboard,** kies vervolgens **Account Instellingen** en kies vervolgens App **Management.**

3. Kies in **de sectie Web-app** **de optie Bestaande app registreren.**

4. Selecteer de web-app die u in de Azure Portal.

5. Kies **uw app registreren.**

## <a name="native-apps"></a>Systeemeigen apps

Native apps hoeven niet te worden geregistreerd bij Partner Center. Deze apps moeten echter worden geconfigureerd om toegang te bieden tot Partner Center API's.

>[!NOTE]
>Voordat u een systeemeigen app in de Azure Portal, moet u zich aanmelden bij Partner Center met de gebruikersreferenties van de beheerder van de partnerten tenant. Hiermee maakt u de instellingen op de tenant om app-machtigingen in te kunnenschakelen.

### <a name="create-native-app"></a>Een native app maken

1. Navigeer [naar Azure Portal - App-registraties](https://go.microsoft.com/fwlink/?linkid=2083908) om uw app te registreren. Meld u aan bij Azure Portal met een werk- of schoolaccount of een persoonlijk Microsoft-account.

2. Selecteer **Nieuwe registratie**. Zie Snelstart: Een toepassing registreren met de Microsoft identity platform voor [meer Microsoft identity platform.](/azure/active-directory/develop/quickstart-register-app)

### <a name="configure-api-access-permissions-for-native-app"></a>API-toegangsmachtigingen configureren voor systeemeigen apps

1. Kies uw app. Ga naar **Settings**.

2. Kies vereiste machtigingen **in API-toegang.**

3. Kies **Windows Azure Active Directory machtigingen**. Selecteer **in Gedelegeerde machtigingen** de volgende machtigingen:

    - **Aanmelden en gebruikersprofiel lezen**
    - **Mapgegevens lezen**
    - **Toegang tot de map als de aangemelde gebruiker**
    - **Alle groepen lezen**

4. Sla de machtigingen op.

5. Kies **Toevoegen** in **Vereiste machtigingen.**

6. Kies **Een API selecteren**.

    1. Voer in het zoekvak **Microsoft Partner Center** selecteer deze in de lijst met resultaten.

    2. Kies **Selecteren**.

7. Kies **Machtigingen selecteren**.

    1. Selecteer **Toegang Partner Center PPE.**
    
    2. Kies **Selecteren**.

8. Kies **Gereed**.

>[!IMPORTANT]
> Noteer de toepassings-id in de eigenschappen van uw app.

U hoeft geen systeemeigen apps te registreren in Partner Center, maar de systeemeigen app moet wel beheerdersmachtiging hebben. Noteer de toepassings-id van uw eigen app.
