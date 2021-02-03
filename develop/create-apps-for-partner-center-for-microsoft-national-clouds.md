---
title: App-gegevens registreren voor Partner Center voor micro soft National Cloud
description: Meer informatie over hoe en waarom app-ontwikkel aars voor partner centrum voor micro soft National Cloud details moeten registreren over hun app met Azure AD via de Azure Portal.
MS-HAID:
- pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_cloud\_germany
- pc\_apiv2.create\_apps\_for\_partner\_center\_for\_microsoft\_national\_clouds
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 887cb71c752ac5d9c61398536711545c19cc7600
ms.sourcegitcommit: 4c253abb24140a6e00b0aea8e79a08823ea5a623
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 12/07/2020
ms.locfileid: "97767642"
---
# <a name="register-app-details-for-partner-center-for-microsoft-national-cloud-through-the-azure-portal"></a>Registreer app-gegevens voor het partner centrum voor micro soft National Cloud via de Azure Portal

**Van toepassing op:**

- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Ontwikkel aars moeten gegevens over hun app met Azure AD registreren via de Azure Portal. Dit helpt ervoor te zorgen dat alleen opgegeven apps verbinding kunnen maken met de partner-en klant gegevens.

Voor het partner centrum voor Microsoft Cloud voor de Amerikaanse overheid moet u momenteel apps beheren via Power shell. Zie de [documentatie over Azure PowerShell](/powershell/module/Azuread/#applications)voor meer informatie.

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

Houd rekening met de volgende aanvullende vereisten wanneer u een app maakt voor partner centrum voor Microsoft Cloud Duitsland of partner centrum voor Microsoft Cloud voor de Amerikaanse overheid.

## <a name="web-apps"></a>Web-apps

Gebruik voor web-apps de volgende procedures om uw toepassings-ID te registreren.

### <a name="create-or-update-web-app"></a>Een web-app maken of bijwerken

1. Ga naar de pagina [Azure Portal-app-registraties](https://go.microsoft.com/fwlink/?linkid=2083908) om uw app te registreren. Meld u aan bij de Azure Portal met behulp van een werk-of school account of een persoonlijke Microsoft-account.

2. Selecteer **Nieuwe registratie**. Zie [Quick Start: een toepassing registreren bij het micro soft Identity-platform](/azure/active-directory/develop/quickstart-register-app)voor meer informatie.

### <a name="configure-api-access-permissions-for-web-app"></a>API-toegangs machtigingen voor web-app configureren

1. Kies uw app. Ga naar de **instellingen** van de web-app.

2. Kies in het gedeelte **API-toegang** de optie **vereiste machtigingen**

3. Voor Windows Azure Active Directory-machtigingen:

    1. Kies **Windows-Azure Active Directory machtigingen**.

    2. Selecteer in **toepassings machtigingen** de optie Directory gegevens lezen.

    3. Sla de machtigingen op.

4. Noteer de toepassings-ID in het gedeelte **Eigenschappen** van uw web-app.

### <a name="add-a-secret-key-to-your-app"></a>Een geheime sleutel toevoegen aan uw app

1. Ga naar de sectie **sleutels** van uw web-app.

2. Voer de sleutel beschrijving in en selecteer duur als 1 of 2 jaar, zoals u wilt.

3. Sla de waarde van de geheime sleutel op en kopieer deze. **Deze waarde wordt niet weer gegeven wanneer u deze pagina verlaat.**

U moet de volgende details van de web-app configureren:

- Toepassings-id
- Toepassingsgeheim

### <a name="register-the-web-app-in-partner-center"></a>De web-app registreren in het partner centrum

1. Meld u aan bij [https://partnercenter.microsoft.com](https://partnercenter.microsoft.com) .

2. Kies **dash board**, kies **account instellingen** en kies vervolgens **app-beheer**.

3. Kies **bestaande app registreren** in het gedeelte **Web-app** .

4. Selecteer de web-app die u hebt gemaakt in Azure Portal.

5. Kies **uw app registreren**.

## <a name="native-apps"></a>Systeemeigen apps

Systeem eigen apps hoeven niet te worden geregistreerd bij het partner centrum. Maar deze apps moeten worden geconfigureerd om toegang te bieden tot partner Center-Api's.

>[!NOTE]
>Voordat u een systeem eigen app maakt in de Azure Portal, meldt u zich aan bij Partner Center met behulp van de gebruikers referenties van de beheerder van de partner-Tenant. Hiermee maakt u de instellingen op de Tenant om app-machtigingen in te scha kelen.

### <a name="create-native-app"></a>Systeem eigen app maken

1. Ga naar de pagina [Azure Portal-app-registraties](https://go.microsoft.com/fwlink/?linkid=2083908) om uw app te registreren. Meld u aan bij de Azure Portal met behulp van een werk-of school account of een persoonlijke Microsoft-account.

2. Selecteer **Nieuwe registratie**. Zie [Quick Start: een toepassing registreren bij het micro soft Identity-platform](/azure/active-directory/develop/quickstart-register-app)voor meer informatie.

### <a name="configure-api-access-permissions-for-native-app"></a>API-toegangs machtigingen voor systeem eigen app configureren

1. Kies uw app. Ga naar **Settings**.

2. Kies in API-toegang de optie **vereiste machtigingen**.

3. Kies **Windows-Azure Active Directory machtigingen**. Selecteer in **gedelegeerde machtigingen** de volgende machtigingen:

    - **Aanmelden en gebruikersprofiel lezen**
    - **Mapgegevens lezen**
    - **Toegang tot de map als de aangemelde gebruiker**
    - **Alle groepen lezen**

4. Sla de machtigingen op.

5. Kies **toevoegen** in **vereiste machtigingen**.

6. Kies **Een API selecteren**.

    1. Voer in het zoekvak **micro soft Partner Center** in en selecteer het in de lijst met resultaten.

    2. Kies **Selecteren**.

7. Kies **Machtigingen selecteren**.

    1. Selecteer **toegang tot het beschermings partner centrum**.
    
    2. Kies **Selecteren**.

8. Kies **Gereed**.

>[!IMPORTANT]
> Noteer de toepassings-ID in de eigenschappen van uw app.

U hoeft geen systeem eigen apps te registreren in het partner centrum, maar de systeem eigen app moet zijn gestemd met de beheerder. Noteer de toepassings-ID van uw systeem eigen app.
