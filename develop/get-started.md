---
title: Aan de slag
description: De Partnercentrum-SDK bevat een beheerde API en een REST API die partners kunnen gebruiken om klant-, abonnements- en ordergegevens te beheren.
ms.date: 09/29/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 340b46978d71bdf5fa6f6795d69fe0721d808c4eb2650744e82510c208dd5b8f
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115989692"
---
# <a name="get-started"></a>Aan de slag

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De Partnercentrum-SDK bevat een beheerde API en een REST API die partners kunnen gebruiken om klant-, abonnements- en ordergegevens te beheren.

## <a name="get-the-code"></a>Code ophalen

[Download de Partnercentrum-SDK](https://go.microsoft.com/fwlink/p/?LinkId=746681)

> [!NOTE]
> API-toegang Partner Center voor indirecte resellers is geen ondersteund scenario.

## <a name="determine-your-version-of-partner-center"></a>Uw versie van de Partner Center

Sommige versies van Partner Center hebben niet de volledige SDK beschikbaar. Zie Developing for Partner Center for Microsoft National Cloud (Ontwikkelen Partner Center [voor Microsoft National Cloud) voor meer informatie.](developing-for-partner-center-for-microsoft-national-cloud.md)

## <a name="get-the-samples"></a>De voorbeelden op te halen

Zie voorbeelden voor meer informatie over C#-fragmenten, REST-voorbeelden en de [voorbeeld-app Partner Center voorbeelden.](partner-center-samples.md)

## <a name="test-vs-production"></a>Testen versus productie

Terwijl u uw code in eerste instantie schrijft en test, moet u uw sandbox-account voor integratie (en de bijbehorende tokens) gebruiken, zodat er niet per ongeluk nieuwe kosten in rekening worden gebracht die uw bedrijf moet betalen. Zie API-toegang instellen in Partner Center voor meer informatie [over deze testomgeving.](set-up-api-access-in-partner-center.md)

Wanneer uw oplossing is getest en klaar is voor gebruik in echte klantaccounts, moet u uw tokens bijwerken zodat u een Azure AD-client-app en -geheim gebruikt die overeenkomen met uw primaire Partner Center-account.

Zie Testen en fouten opsporen voor tips en suggesties over testen en foutopsporing, [](test-and-debug.md)waaronder meer informatie over Test-in-Production (TiP) en de Integratie-sandbox.

## <a name="configure-your-authentication"></a>Uw verificatie configureren

Als u uw Azure AD-verificatie wilt configureren zodat u de Partner Center API's kunt gebruiken, Partner Center [verificatie.](partner-center-authentication.md)

> [!IMPORTANT]
> Microsoft introduceert een veilig, schaalbaar framework voor de verificatie van CSP-partners (Cloud Solution Provider) en configuratieschermleveranciers (CPV) via de architectuur van Microsoft Azure Multi-Factor Authentication (MFA).
Partner Center gebruikt Azure AD voor verificatie en voor het gebruik van de Partner Center API's moet u uw verificatie-instellingen correct configureren.
>
> Zie Secure Application Model inschakelen [voor meer informatie.](enable-secure-app-model.md)

## <a name="get-help"></a>Hulp vragen

Partners kunnen ondersteuning krijgen in de [Partnercentrum-SDK Yammer groep](https://go.microsoft.com/fwlink/p/?LinkID=717360). Voor persoonlijkere hulp kunnen ontwikkelaars gebruikmaken van hun MPN-ondersteuningsvoordelen of Premier Support.

## <a name="join-the-partner-center-api-and-sdk-early-adopter-program"></a>Aanmelden voor het Early Adopter-programma voor API en SDK van Partnercentrum

Zie Deelnemen aan de Partner Center API en [SDK Early Adopter Program](early-adopter-program.md)voor meer informatie over hoe u met Microsoft kunt samenwerken aan de ontwikkeling van partnerfuncties en -mogelijkheden.
