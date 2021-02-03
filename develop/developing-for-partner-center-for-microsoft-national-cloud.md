---
title: Ontwikkelen voor Partner Center voor nationale Clouds van micro soft
description: Partner Center SDK verschilt bij het ontwikkelen van het partner centrum voor micro soft National Clouds.
MS-HAID:
- pc\_apiv2.developing\_with\_different\_partner\_center\_versions
- pc\_apiv2.developing\_for\_partner\_center\_for\_microsoft\_national\_cloud
ms.date: 06/11/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7882846de0c591b21fe73345f560613f535d1788
ms.sourcegitcommit: 529b07030a874d644cf947790f4b53cdff438dd4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767398"
---
# <a name="developing-for-partner-center-for-microsoft-national-clouds"></a>Ontwikkelen voor Partner Center voor nationale Clouds van micro soft

**Van toepassing op:**

- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Het partner centrum heeft één set SDK-documentatie. Sommige functies zijn echter mogelijk niet beschikbaar in de versies van partner Center voor nationale Clouds van micro soft.

Ontwikkel aars moeten wijzigingen in de SDK overwegen voor de volgende versies van partner Center:

- [Partner centrum beheerd door 21Vianet](#partner-center-operated-by-21vianet)
- [Partnercentrum voor Microsoft Cloud Duitsland](#partner-center-for-microsoft-cloud-germany)
- [Partnercentrum voor Microsoft Cloud for US Government](#partner-center-for-microsoft-cloud-for-us-government)

Elk Partner Center SDK-artikel vermeldt de toepasselijke partner centrum-versies. In elk artikel met beheerde verwijzingen worden ook de toepasselijke partner centrum-versies vermeld in de sectie **vereisten** .

## <a name="partner-center-operated-by-21vianet"></a>Partner centrum beheerd door 21Vianet

De verschillen voor partners tussen het *partner centrum* en het *partner centrum dat wordt beheerd door 21vianet* zijn:

- U kunt een wacht woord voor een klant gebruiker of een volledige partner gebruiker niet programmatisch opnieuw instellen.

- Abonnementen op Azure zijn niet beschikbaar.

- U kunt de licenties voor de gebruiker van uw klant niet beheren. In plaats daarvan moeten uw klanten het Office 365-beheer centrum gebruiken voor het beheren van hun licenties.

- Alle ondersteunings aanvragen worden beheerd via een partner centrum dat wordt beheerd door 21Vianet. Service aanvragen en service-updates zijn niet van toepassing.

## <a name="partner-center-for-microsoft-cloud-germany"></a>Partnercentrum voor Microsoft Cloud Duitsland

> [!IMPORTANT]
> Op basis van de ontwikkeling van de behoeften van klanten, zullen onze Cloud strategie voor Duitsland zich richten op de levering van de nieuwe Cloud regio's in Duitsland die consistent zijn met onze wereld wijde Cloud aanbieding. Met deze focus zullen we geen nieuwe klanten meer accepteren of nieuwe services implementeren vanaf de momenteel beschik bare Microsoft Cloud Duitsland. Bestaande klanten kunnen vandaag nog blijven gebruikmaken van de huidige Cloud Services, die we onderhouden met de benodigde beveiligings updates.
>
> Nieuwe klanten hebben de mogelijkheid om de momenteel beschik bare Europese regio's of de nieuwe regio's in Duitsland te gebruiken wanneer deze beschikbaar komen. Zie voor meer informatie [micro soft Cloud Services leveren vanuit nieuwe data centers in Duitsland](https://news.microsoft.com/europe/2018/08/31/microsoft-to-deliver-cloud-services-from-new-datacentres-in-germany-in-2019-to-meet-evolving-customer-needs/).

De verschillen voor partners tussen *partner centrum* en *partner centrum voor Microsoft Cloud Duitsland* zijn:

- Partners kunnen geen gebruikers maken voor de organisatie van hun klant of rollen toewijzen.
  - Partners kunnen velden lezen, maar kunnen ze niet schrijven of bijwerken.
  - Partners moeten de gebruikers van hun klanten hand matig maken of bijwerken in het Office 365-beheer centrum of via de Azure Portal. Raadpleeg de [documentatie van Azure Active Directory](/azure/active-directory/).

- U kunt de licenties voor de gebruikers van uw klant niet beheren via het partner centrum voor Microsoft Cloud Duitsland-portal of-Api's. In plaats daarvan moet u het Office 365-beheer centrum of het direct-licentie beheer van Azure Active Group (binnenkort) gebruiken om de licenties te beheren.
  - (Optioneel) u kunt Azure AD Graph API gebruiken. Zie [licenties toewijzen aan een gebruiker](/graph/api/user-assignlicense). Voor Partner Center voor Microsoft Cloud Duitsland moet u het eind punt van de grafiek gebruiken `https://graph.cloudapi.de` in plaats van `https://graph.windows.net` .

- U kunt een wacht woord voor een klant gebruiker of een volledige partner gebruiker niet programmatisch opnieuw instellen. Gebruik het Office 365-beheer centrum of Azure Portal. Zie [het wacht woord voor een gebruiker opnieuw instellen in azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-reset-password-azure-portal). Voor stap 1 moet u zich aanmelden bij de Azure Portal voor Microsoft Cloud Duitsland.

- Ontwikkel aars moeten hun app-ID hand matig registreren om de functionaliteit van de Partner Center API/SDK in hun app voor Partner Center voor Microsoft Cloud Duitsland te integreren. Zie [app-gegevens registreren voor Partner Center voor micro soft National Cloud](create-apps-for-partner-center-for-microsoft-national-clouds.md)voor meer informatie.

## <a name="partner-center-for-microsoft-cloud-for-us-government"></a>Partnercentrum voor Microsoft Cloud for US Government

De verschillen voor partners tussen *partner centrum* en *partner centrum voor Microsoft Cloud voor de Amerikaanse overheid* zijn:

- Er zijn momenteel geen Office 365-abonnementen beschikbaar voor partner centrum voor Microsoft Cloud voor de Amerikaanse overheid.

- Bestaande partners die Microsoft Cloud voor Amerikaanse overheid ondersteunen, moeten nieuwe accounts maken in Partner Center voor Microsoft Cloud voor de Amerikaanse overheid.

- Microsoft Cloud voor klanten van de Amerikaanse overheid moeten trans acties met één partner.
  - Meerdere multi partner-en aanvraag relaties met een bestaande klant in Microsoft Cloud voor Amerikaanse overheids scenario's zijn niet van toepassing. Deze beperking is omdat Office 365 momenteel niet beschikbaar is.

- Partners kunnen geen gebruikers maken voor de organisatie van hun klant of rollen toewijzen.
  - Partners kunnen velden lezen, maar kunnen ze niet schrijven of bijwerken. Partners moeten de gebruikers van hun klanten hand matig maken of bijwerken in de Azure Portal. Raadpleeg de [documentatie van Azure Active Directory](/azure/active-directory/).

- U kunt een wacht woord voor een klant gebruiker of een volledige partner gebruiker niet programmatisch opnieuw instellen. Gebruik de Azure Portal. Zie [het wacht woord voor een gebruiker opnieuw instellen in azure Active Directory](/azure/active-directory/active-directory-users-reset-password-azure-portal). Voor stap 1 moet u zich aanmelden bij de Azure Portal voor Microsoft Cloud voor de Amerikaanse overheid.

- REST-eind punten voor het partner centrum voor Microsoft Cloud voor de Amerikaanse overheid zijn hetzelfde als voor partner centrum: `https://api.partnercenter.microsoft.com` .

- Ontwikkel aars moeten hun app-ID hand matig registreren om de functionaliteit van de Partner Center API/SDK in hun app voor partner centrum te integreren voor Microsoft Cloud voor de Amerikaanse overheid. Zie [app-gegevens registreren voor Partner Center voor micro soft National Cloud](create-apps-for-partner-center-for-microsoft-national-clouds.md)voor meer informatie.
