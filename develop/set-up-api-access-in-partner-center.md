---
title: API-toegang instellen in Partnercentrum
description: Accounts instellen voor het ontwikkelen op de Partnercentrum-SDK en testen in de integratie-sandbox.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: db7d9bba34abadc907910c68c4a5583ed1f530f4
ms.sourcegitcommit: de1e68545d37d7fa1862788f7fa8c84a9c4f2795
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/16/2021
ms.locfileid: "114282091"
---
# <a name="set-up-api-access-in-partner-center"></a>API-toegang instellen in Partnercentrum

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud for US Government | Partner Center voor Microsoft Cloud Duitsland

In dit artikel worden de accounts beschreven die u moet ontwikkelen op de Partnercentrum-SDK. In dit artikel wordt ook uitgelegd hoe u een [integratie-sandboxaccount maakt en](#integration-sandbox-account) test in de integratie-sandbox.

>[!NOTE]
>Als u toegang wilt krijgen tot API's, moet uw tenant een CSP-tenant zijn en moet u een indirecte provider of een directe factuurpartner zijn.

## <a name="account-definitions"></a>Accountdefinities

Om u te helpen uw API-integratie te integreren en te testen, Partner Center twee soorten accounts ondersteunen:

### <a name="primary-partner-account"></a>Primaire partneraccount

In dit account maakt u echte orders voor echte klanten. Als u wijzigingen of transacties aanstelt wanneer u bent aangemeld bij het primaire account, worden deze met behulp van de Partnercentrum-SDK of de gebruikersinterface van het partnerdashboard behandeld als officiële orders voor echte klanten. Deze worden weergegeven in uw factuur en uw bedrijf is verantwoordelijk voor het betalen ervan.

### <a name="integration-sandbox-account"></a>Sandboxaccount voor integratie

Dit account is voor het testen van uw code en de integratie ervan met de Partner Center API's voordat u deze breed implementeert. Wijzigingen en transacties die u maakt wanneer u bent aangemeld bij het sandbox-account voor integratie worden weergegeven op uw factuur, maar u hoeft het factuurbedrag niet te betalen. Factuur pdf heeft een disclaimer als "NIET BETALEN. DIT IS EEN SANDBOX-FACTUUR EN ER IS GEEN ACTIE VEREIST.

Het sandbox-account voor integratie en het primaire account werken onafhankelijk en delen geen beheerdersaccounts, gebruikersaccounts, klanten, orders, abonnementen of andere gegevens.

De integratie-sandbox ondersteunt transacties met een beperkt aantal klanten, orders, abonnementen, licenties, enzovoort.

Op beleid zijn sandbox-accounts voor integratie alleen bedoeld voor testdoeleinden voor integratie.

Standaard is er geen sandboxaccount voor integratie. U moet er zelf een maken als u van plan bent om de Partnercentrum-SDK.

## <a name="set-up-your-accounts"></a>Uw accounts instellen

In deze sectie wordt beschreven hoe u een primair partneraccount en een sandbox-account voor integratie voor de Partnercentrum-SDK.

### <a name="create-an-integration-sandbox"></a>Een integratie-sandbox maken

1. Meld u aan bij partnerdashboard met een globale beheerdersaccount (uw primaire partneraccount).

2. Kies in **Instellingen** menu (tandwielpictogram) de optie **Accountinstellingen.**

3. Kies het **tabblad Integratie-sandbox.**

    >[!NOTE]
    >Als u de optie Integratie-sandbox niet ziet, hebt u mogelijk geen globale beheerdersaccount. Mogelijk gebruikt u ook een sandbox-account voor integratie en is er al een integratie-sandbox ingesteld.

4. Voer de contactgegevens in voor het beheerdersaccount van de sandbox voor integratie. Kies vervolgens **Account maken.** Wacht enkele minuten tot er een bevestigingsbericht wordt weergegeven dat het account is gemaakt.

5. Nadat u het bevestigingsbericht hebt weergegeven, meld u zich af bij partnerdashboard.

6. Meld u opnieuw aan met uw nieuwe beheerdersaccount voor de integratie-sandbox. Zorg ervoor dat u de indeling **username@domain** voor uw referenties gebruikt, samen met het wachtwoord dat u hebt opgegeven.

7. Kies **Account instellen boven** Huidige taken **om** de installatie van het sandbox-account te voltooien.

### <a name="enable-api-access"></a>API-toegang inschakelen

Nadat uw account is ingesteld, moet u API-toegang inschakelen voordat u de Partnercentrum-SDK kunt gebruiken met de sandbox voor integratie. U moet de toegang tot de API afzonderlijk inschakelen voor zowel uw primaire partneraccount als uw sandboxaccount voor integratie.

1. Meld u aan bij partnerdashboard met een account voor globale beheerders.

2. Selecteer in **Instellingen** menu (tandwielpictogram) **accountinstellingen.**

3. Kies op **de pagina Accountinstellingen** de optie **App-beheer.**

4. Als u nog geen bestaande app hebt, voegt u een nieuwe web-app toe. Als u een bestaande web-app hebt, kiest u de **knop Sleutel** toevoegen.

5. Kopieer de app-registratiegegevens, met **name** de Sleutel als u een web-app maakt, en sla deze op een veilige plaats op.

6. Meld u af bij partnerdashboard.

7. Meld u opnieuw aan met uw sandbox-account voor integratie. Herhaal stap 2-5 om API-toegang in te stellen in de integratie-sandbox.

## <a name="write-and-test-code"></a>Code schrijven en testen

U kunt code schrijven en code testen in de integratie-sandbox. U hebt de volgende informatie nodig om verificatie [Partner Center](partner-center-authentication.md) Azure AD in te stellen.

| Itemnaam | Itemlocatie |
| --------- | ------------- |
| App-id/client-id | Selecteer in **Instellingen** menu (tandwielpictogram) **accountinstellingen.** Selecteer **app-beheer** op de pagina **Accountinstellingen.** De app-id/client-id wordt vermeld als de geregistreerde **toepassings-app-id.** |
| Sleutel | Als u een web-app hebt gemaakt in de sectie [API-toegang](#enable-api-access)inschakelen, is dit de sleutel die u in stap 5 hebt opgeslagen. |
| Domain | Het domein voor de integratie-sandbox. |

## <a name="run-tested-code"></a>Geteste code uitvoeren

Als u uw oplossing wilt gebruiken met echte klantgegevens, moet u de referenties van uw integratiesandbox wijzigen in de referenties van uw primaire partneraccount.

Wanneer u klaar bent om uw geteste code te gebruiken in uw primaire partneraccount, moet u een Azure AD-beveiliging token krijgen. Dit beveiliging token is gebaseerd op uw Partner Center app, sleutel en domein (in plaats van uw integratie-sandbox-app, -sleutel en -domein).

1. Volg de stappen in [Partner Center om](partner-center-authentication.md) een Azure AD-beveiliging token op te halen met behulp van uw Partner Center referenties. (U hebt deze stappen eerder gevolgd om een Azure AD-beveiliging token voor uw integratie-sandbox op te halen.)

2. Vervang het integratiebeveiliging token in uw code door het nieuwe beveiliging token voor uw primaire Partner-account.
