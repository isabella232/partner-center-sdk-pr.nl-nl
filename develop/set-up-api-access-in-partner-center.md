---
title: API-toegang instellen in Partnercentrum
description: Stel accounts in voor de ontwikkeling van de Partner Center-SDK en test in de sandbox voor integratie.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 873ff2ff9cecbfa92429958d3bfe2aa79fc3ad9a
ms.sourcegitcommit: d5de47c08ba661ba5de4935caa6843d7c2c91710
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/28/2020
ms.locfileid: "97767400"
---
# <a name="set-up-api-access-in-partner-center"></a>API-toegang instellen in Partnercentrum

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud for US Government
- Partnercentrum voor Microsoft Cloud Duitsland

In dit artikel worden de accounts beschreven die u nodig hebt om te ontwikkelen met de Partner Center-SDK. In dit artikel wordt ook uitgelegd hoe u een [account voor integratie sandbox](#integration-sandbox-account) maakt en test in de sandbox voor integratie.

>[!NOTE]
>Als u toegang wilt krijgen tot Api's, moet uw Tenant een CSP-Tenant zijn en moet u een indirecte provider of een directe factuur partner zijn.

## <a name="account-definitions"></a>Account definities

Om u te helpen uw API-integratie te integreren en te testen, ondersteunt het partner centrum twee soorten accounts:

### <a name="primary-partner-account"></a>Account voor primaire partner

Met deze account maakt u echte bestellingen voor echte klanten. Als u wijzigingen of trans acties aanbrengt wanneer u bent aangemeld bij het primaire account, wordt het gebruik van de Partner Center SDK of de gebruikers interface van het dash board van de partner beschouwd als officiële orders voor echte klanten. Ze worden weer gegeven in uw factuur en uw bedrijf is verantwoordelijk voor het betalen ervan.

### <a name="integration-sandbox-account"></a>Sandboxaccount voor integratie

Dit account is voor het testen van uw code en de integratie met de partner centrum-Api's voordat u deze breed implementeert. Wijzigingen en trans acties die u aanbrengt wanneer u zich aanmeldt bij het integratie sandbox-account, worden in uw factuur weer gegeven, maar u hoeft het factuur bedrag niet te betalen. Factuur-PDF heeft een disclaimer als ' niet betalen. DIT IS EEN SANDBOX-FACTUUR EN ER IS GEEN ACTIE VEREIST. "

De integratie sandbox-account en het primaire account handelen onafhankelijk en delen geen beheerders accounts, gebruikers accounts, klanten, bestellingen, abonnementen of andere gegevens.

De integratie sandbox ondersteunt trans acties met een beperkt aantal klanten, bestellingen, abonnementen, licenties, enzovoort.

Op basis van beleid worden Sandbox-accounts voor integratie alleen gebruikt voor het testen van de integratie.

Standaard is er geen sandboxaccount voor integratie. U moet er zelf een maken als u van plan bent de Partner Center-SDK te gebruiken.

## <a name="set-up-your-accounts"></a>Uw accounts instellen

In deze sectie wordt beschreven hoe u een account voor een primaire partner en een beveiligingssandbox voor integratie kunt instellen voor de partner centrum-SDK.

### <a name="create-an-integration-sandbox"></a>Een integratie sandbox maken

1. Meld u aan bij het dash board van de partner met een globaal beheerders account (uw primaire partner account.)

2. Kies in het menu **instellingen** (pictogram tandwiel) de optie **partner instellingen**.

3. Kies **integratie sandbox** tabblad.

    >[!NOTE]
    >Als u geen sandbox-optie voor integratie ziet, hebt u mogelijk geen globaal beheerders account. Het is ook mogelijk dat u een sandbox-integratie account gebruikt en dat er al een integratie sandbox is ingesteld.

4. Voer de contact gegevens in voor het account voor de integratie sandbox-beheerder. Kies vervolgens **account maken**. Wacht een paar minuten totdat er een bevestigings bericht wordt gegenereerd dat het account is gemaakt.

5. Nadat u het bevestigings bericht hebt weer gegeven, meldt u zich af bij het dash board van de partner.

6. Meld u weer aan met uw nieuwe integratie sandbox-beheerders account. Zorg ervoor dat u de indeling **username@domain** voor uw referenties gebruikt, samen met het wacht woord dat u zojuist hebt opgegeven.

7. Kies **account instellen** boven **huidige taken** om de instelling van het sandbox-account te volt ooien.

### <a name="enable-api-access"></a>API-toegang inschakelen

Nadat uw account is ingesteld, moet u API-toegang inschakelen voordat u de Partnercentrum-SDK kunt gebruiken met de sandbox voor integratie. U moet de toegang tot de API afzonderlijk inschakelen voor zowel uw primaire partneraccount als uw sandboxaccount voor integratie.

1. Meld u aan bij het partner dashboard met een globaal beheerders account.

2. Selecteer **partner instellingen** in het menu **instellingen** (pictogram tandwiel).

3. Kies op de pagina **account instellingen** de optie **app-beheer**.

4. Als u nog geen app hebt, voegt u een nieuwe web-app toe. Als u een bestaande web-app hebt, kiest u de knop **sleutel toevoegen** .

5. Kopieer de gegevens van de app-registratie, met name de **sleutel** als u een web-app maakt en sla deze op een veilige plaats op.

6. Meld u af bij het dash board van de partner.

7. Meld u weer aan met uw sandbox-account voor integratie. Herhaal de stappen 2-5 om API-toegang in te scha kelen in de sandbox voor integratie.

## <a name="write-and-test-code"></a>Code schrijven en testen

U kunt code en test code schrijven in de integratie sandbox. U hebt de volgende informatie nodig om [Partner Center-verificatie](partner-center-authentication.md) in te stellen met Azure AD.

| Itemnaam | Item locatie |
| --------- | ------------- |
| App-ID/client-ID | Selecteer **partner instellingen** in het menu **instellingen** (pictogram tandwiel). Selecteer op de pagina **account instellingen** de optie **app-beheer**. De App-ID/client-ID wordt vermeld als de **geregistreerde app-id** van de toepassing. |
| Sleutel | Als u een web-app hebt gemaakt in de sectie [API-toegang inschakelen](#enable-api-access), is dit de sleutel die u hebt opgeslagen in stap 5. |
| Domain | Het domein voor de integratie sandbox. |

## <a name="run-tested-code"></a>Geteste code uitvoeren

Als u uw oplossing wilt gebruiken met echte klant gegevens, moet u de referenties van uw integratie sandbox wijzigen naar de referenties van uw primaire partner account.

Wanneer u klaar bent om uw geteste code te gebruiken in uw primaire partner account, moet u een Azure AD-beveiligings token ontvangen. Dit beveiligings token is gebaseerd op uw partner centrum-app, sleutel en domein (in plaats van uw sandbox-app voor integratie, sleutel en domein).

1. Volg de stappen in [Partner Center-verificatie](partner-center-authentication.md) voor het verkrijgen van een Azure AD-beveiligings token met behulp van uw referenties voor het primaire partner centrum. (U hebt deze stappen eerder gevolgd om een Azure AD-beveiligings token op te halen voor uw integratie sandbox.)

2. Vervang het beveiligings token voor integratie in uw code door het nieuwe beveiligings token voor uw account voor primaire partner.
