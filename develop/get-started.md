---
title: Aan de slag
description: De partner centrum-SDK bevat een beheerde API en een REST API voor partners die moeten worden gebruikt voor het beheren van gegevens van klanten, abonnementen en orders.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9c2af1e11dbda19489a27e37c7f3de8ede90fd1c
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767280"
---
# <a name="get-started"></a>Aan de slag

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De partner centrum-SDK bevat een beheerde API en een REST API voor partners die moeten worden gebruikt voor het beheren van gegevens van klanten, abonnementen en orders.

## <a name="get-the-code"></a>Code ophalen

[De Partner Center-SDK downloaden](https://go.microsoft.com/fwlink/p/?LinkId=746681)

> [!NOTE]
> API-toegang tot het partner centrum voor indirecte wederverkopers is geen ondersteund scenario.

## <a name="determine-your-version-of-partner-center"></a>Uw versie van partner centrum bepalen

Voor sommige versies van partner Center is de volledige SDK niet beschikbaar. Zie [ontwikkelen voor Partner Center voor micro soft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md)voor meer informatie.

## <a name="get-the-samples"></a>De voor beelden ophalen

Zie voor meer informatie over C#-fragmenten, REST-voor beelden en de voor beeld-app [Partner Center](partner-center-samples.md)-voor beelden.

## <a name="test-vs-production"></a>Testen versus productie

Terwijl u uw code voor het eerst schrijft en test, moet u uw account voor de integratie sandbox (en de bijbehorende tokens) gebruiken, zodat u niet per ongeluk nieuwe kosten maakt die uw bedrijf verantwoordelijk is voor de betaling. Zie [API-toegang instellen in Partner Center](set-up-api-access-in-partner-center.md)voor meer informatie over deze test omgeving.

Wanneer uw oplossing is getest en gereed is voor gebruik op echte klant accounts, moet u uw tokens bijwerken zodat u een Azure AD-client-app en een geheim gebruikt dat overeenkomt met uw primaire partner centrum-account.

Voor tips en suggesties over testen en fout opsporing, met inbegrip van meer informatie over test-in-productie (TiP) en de integratie sandbox, Zie [testen en fouten opsporen](test-and-debug.md).

## <a name="configure-your-authentication"></a>Uw authenticatie configureren

Zie [Partner Center-verificatie](partner-center-authentication.md)voor meer informatie over het configureren van uw Azure AD-verificatie zodat u de partner centrum-api's kunt gebruiken.

> [!IMPORTANT]
> Micro soft introduceert een veilig, schaalbaar Framework voor het verifiëren van de CSP-partners (Cloud Solution Provider) en leveranciers van configuratie schermen (CPV) via de Microsoft Azure multi-factor Authentication-architectuur (MFA).
Het partner centrum gebruikt Azure AD voor verificatie en voor het gebruik van de Api's van het partner centrum moet u uw verificatie-instellingen op de juiste wijze configureren.
>
> Zie [Enable Secure Application model](enable-secure-app-model.md)(Engelstalig) voor meer informatie.

## <a name="get-help"></a>Hulp vragen

Partners kunnen ondersteuning krijgen via de [Partner Center SDK Yammer-groep](https://go.microsoft.com/fwlink/p/?LinkID=717360). Ontwikkel aars kunnen hun MPN-ondersteunings voordelen of-Premier Support gebruiken om meer persoonlijke hulp te krijgen.

## <a name="join-the-partner-center-api-and-sdk-early-adopter-program"></a>Aanmelden voor het Early Adopter-programma voor API en SDK van Partnercentrum

Zie voor meer informatie over hoe u kunt samen werken met micro soft aan de hand van de functies en mogelijkheden van [de partner de Partner Center API en SDK Early passer Program](early-adopter-program.md).
