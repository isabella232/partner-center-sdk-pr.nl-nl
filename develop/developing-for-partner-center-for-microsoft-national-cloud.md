---
title: Ontwikkelen voor Partner Center voor nationale Microsoft-clouds
description: Partnercentrum-SDK verschillen bij het ontwikkelen voor Partner Center voor nationale Microsoft-clouds.
MS-HAID:
- pc\_apiv2.developing\_with\_different\_partner\_center\_versions
- pc\_apiv2.developing\_for\_partner\_center\_for\_microsoft\_national\_cloud
ms.date: 06/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f8b9b3c3b9a1a1173cf8f3e79f60e629e3d34ea13ecce2e7a2c74924bde2b7d1
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994860"
---
# <a name="developing-for-partner-center-for-microsoft-national-clouds"></a>Ontwikkelen voor Partner Center voor nationale Microsoft-clouds

**Van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Partner Center beschikt over één set SDK-documentatie. Sommige functies zijn echter mogelijk niet beschikbaar in de versies van Partner Center voor Microsoft National Clouds.

Ontwikkelaars moeten rekening houden met wijzigingen in de SDK voor de volgende versies van Partner Center:

- [Partnercentrum beheerd door 21Vianet](#partner-center-operated-by-21vianet)
- [Partnercentrum voor Microsoft Cloud Duitsland](#partner-center-for-microsoft-cloud-germany)
- [Partnercentrum voor Microsoft Cloud for US Government](#partner-center-for-microsoft-cloud-for-us-government)

Elk Partnercentrum-SDK vermeldt toepasselijke Partner Center versies. Elk artikel over beheerde verwijzingen bevat ook de toepasselijke Partner Center versies in de **sectie** Vereisten.

## <a name="partner-center-operated-by-21vianet"></a>Partnercentrum beheerd door 21Vianet

De verschillen voor partners tussen *Partner Center* en *Partner Center beheerd door 21Vianet* zijn:

- U kunt een wachtwoord voor een klantgebruiker of volledige partnergebruiker niet programmatisch opnieuw instellen.

- Abonnementen op Azure zijn niet beschikbaar.

- U kunt de licenties voor de gebruiker van uw klant niet beheren. In plaats daarvan moeten uw klanten het Office 365 gebruiken om hun licenties te beheren.

- Alle ondersteuningsaanvragen worden beheerd via Partner Center beheerd door 21Vianet. Serviceaanvragen en service-updates zijn niet van toepassing.

## <a name="partner-center-for-microsoft-cloud-germany"></a>Partnercentrum voor Microsoft Cloud Duitsland

> [!IMPORTANT]
> Op basis van de ontwikkeling van de behoeften van klanten richt onze cloudstrategie voor Duitsland zich op de levering van de nieuwe cloudregio's in Duitsland die consistent zijn met ons wereldwijde cloudaanbod. Vanwege deze focus accepteren we geen nieuwe klanten meer en implementeren we geen nieuwe services meer vanuit de momenteel beschikbare Microsoft Cloud Duitsland. Bestaande klanten kunnen de huidige cloudservices die momenteel beschikbaar zijn, blijven gebruiken, die we onderhouden met de benodigde beveiligingsupdates.
>
> Vanaf nu hebben nieuwe klanten de mogelijkheid om de momenteel beschikbare Europese regio's of de nieuwe regio's in Duitsland te gebruiken wanneer ze beschikbaar komen. Zie [Microsoft gaat cloudservices vanuit nieuwe datacenters in Duitsland leveren](https://news.microsoft.com/europe/2018/08/31/microsoft-to-deliver-cloud-services-from-new-datacentres-in-germany-in-2019-to-meet-evolving-customer-needs/) voor meer informatie.

De verschillen voor partners tussen *Partner Center* en *Partner Center voor Microsoft Cloud Duitsland* zijn:

- Partners kunnen geen gebruikers maken voor de organisatie van hun klant of rollen toewijzen.
  - Partners kunnen velden lezen, maar kunnen ze niet schrijven of bijwerken.
  - Partners moeten handmatig gebruikers van hun klanten maken of bijwerken in het Office 365-beheercentrum of via de Azure Portal. Zie [Azure Active Directory documentatie](/azure/active-directory/).

- U kunt de licenties voor de gebruikers van uw klant niet beheren met behulp van de Partner Center voor de Microsoft Cloud Duitsland-portal of API's. In plaats daarvan moet u het beheercentrum Office 365 azure active-direct groepslicentiebeheer (binnenkort) gebruiken om hun licenties te beheren.
  - (Optioneel) u kunt Azure AD Graph API. Zie [Licenties toewijzen aan een gebruiker.](/graph/api/user-assignlicense) Voor Partner Center voor Microsoft Cloud Duitsland moet u het eindpunt Graph gebruiken `https://graph.cloudapi.de` in plaats van `https://graph.windows.net` .

- U kunt een wachtwoord voor een klantgebruiker of volledige partnergebruiker niet programmatisch opnieuw instellen. Gebruik het Office 365-beheercentrum of Azure Portal. Zie [Het wachtwoord voor een gebruiker opnieuw instellen in Azure Active Directory.](/azure/active-directory/fundamentals/active-directory-users-reset-password-azure-portal) Voor stap 1 moet u zich aanmelden bij de Azure Portal voor Microsoft Cloud Duitsland.

- Ontwikkelaars moeten hun app-id handmatig registreren om Partner Center API/SDK-functionaliteit te integreren in hun app voor Partner Center voor Microsoft Cloud Duitsland. Zie App-details registreren [voor Partner Center voor Microsoft National Cloud voor meer informatie.](create-apps-for-partner-center-for-microsoft-national-clouds.md)

## <a name="partner-center-for-microsoft-cloud-for-us-government"></a>Partnercentrum voor Microsoft Cloud for US Government

De verschillen voor partners tussen *Partner Center* en *Partner Center voor Microsoft Cloud for US Government* zijn:

- Office 365 zijn momenteel niet beschikbaar voor Partner Center voor Microsoft Cloud for US Government.

- Bestaande partners die Microsoft Cloud for US Government, moeten nieuwe accounts maken in Partner Center voor Microsoft Cloud for US Government.

- Microsoft Cloud for US Government klanten moeten een transactie met één partner hebben.
  - Meerdere kanalen en meerdere partner- en aanvraagrelatie met een bestaande klant binnen Microsoft Cloud for US Government scenario's zijn niet van toepassing. Deze beperking is omdat Office 365 momenteel niet beschikbaar is.

- Partners kunnen geen gebruikers maken voor de organisatie van hun klant of rollen toewijzen.
  - Partners kunnen velden lezen, maar kunnen ze niet schrijven of bijwerken. Partners moeten handmatig gebruikers van hun klanten maken of bijwerken in de Azure Portal. Zie [Azure Active Directory documentatie](/azure/active-directory/).

- U kunt een wachtwoord voor een klantgebruiker of volledige partnergebruiker niet programmatisch opnieuw instellen. Gebruik Azure Portal. Zie [Het wachtwoord voor een gebruiker opnieuw instellen in Azure Active Directory.](/azure/active-directory/active-directory-users-reset-password-azure-portal) Voor stap 1 moet u zich aanmelden bij de Azure Portal voor Microsoft Cloud for US Government.

- REST-eindpunten voor Partner Center voor Microsoft Cloud for US Government zijn hetzelfde als voor Partner Center: `https://api.partnercenter.microsoft.com` .

- Ontwikkelaars moeten hun app-id handmatig registreren om Partner Center API/SDK-functionaliteit in hun app te integreren voor Partner Center voor Microsoft Cloud for US Government. Zie App-details registreren [voor Partner Center voor Microsoft National Cloud voor meer informatie.](create-apps-for-partner-center-for-microsoft-national-clouds.md)
