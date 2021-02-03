---
title: Console-testapp
description: Deze console test-app bevat voorbeeld code voor alle scenario's die worden ondersteund door de partner centrum-Api's. U kunt dit ook gebruiken voor het testen.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e82bac3ccc22d0e7cf898e5b2d2e002c622584ae
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767321"
---
# <a name="console-test-app"></a>Console-testapp

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De console test-app is beschikbaar in C# en Java. Deze bevat voorbeeld codes voor alle scenario's die worden ondersteund door de partner centrum-Api's. U kunt dit ook gebruiken voor het testen.

## <a name="get-the-code"></a>Code ophalen

Down load de voorbeeld code voor de console test-app.

## <a name="net"></a>.NET

[Down load de voorbeeld code](https://go.microsoft.com/fwlink/p/?LinkId=746682) en wijzig deze indien nodig.

> [!IMPORTANT]
> Voordat u de toepassing bouwt, werkt u de waarden in het *App.config* -bestand bij om de Azure AD-verificatie gegevens weer te geven die u hebt gemaakt in [Partner Center-verificatie](partner-center-authentication.md). U moet in het bijzonder uw account instellingen voor de integratie sandbox gebruiken tijdens vroegtijdige ontwikkeling of voor het testen van de productie.

Onder **ScenarioSettings** in het *App.config* -bestand kunt u para meters instellen die automatisch worden door gegeven aan de scenario's die u uitvoert.

Als u de lijst met scenario's wilt wijzigen die worden uitgevoerd, kunt u regels voor commentaar in **IPartnerScenario \[ \] mainScenarios** of in een afzonderlijke **Get scenarios** -methode vinden in het bestand *Program.cs* .

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

[Down load de voorbeeld code](https://go.microsoft.com/fwlink/p/?LinkId=2026887) en wijzig deze indien nodig.

> [!IMPORTANT]
> Voordat u de toepassing bouwt, werkt u de waarden in het *SamplesConfigurations.js* bestand bij om de Azure AD-verificatie gegevens weer te geven die u in [Partner Center-verificatie](partner-center-authentication.md)hebt gemaakt. U moet in het bijzonder uw account instellingen voor de integratie sandbox gebruiken tijdens vroegtijdige ontwikkeling of voor het testen van de productie.

Onder **ScenarioSettings** in het *SamplesConfiguration.js* bestand kunt u para meters instellen die automatisch worden door gegeven aan de scenario's die u uitvoert.

Als u de lijst met scenario's wilt wijzigen die worden uitgevoerd, kunt u regels voor opmerkingen maken in **IPartnerScenario \[ \] mainScenarios** of in een afzonderlijke **Get scenarios** -methode in het bestand *Program. java* .

## <a name="what-to-change"></a>Wat u kunt wijzigen

Gebruik de volgende lijsten om te bepalen wat u wilt wijzigen of niet wijzigen in de voorbeeld code.

### <a name="partnerservicesettings"></a>PartnerServiceSettings

Wijzig voor **PartnerServiceSettings** niet:

- **PartnerServiceApiEndpoint**
- **AuthenticationAuthorityEndpoint**
- **GraphEndpoint**
- **CommonDomain**

Al deze instellingen zijn nodig om de voor beeld-API-aanroepen goed te laten functioneren.

### <a name="userauthentication"></a>UserAuthentication

Voor **UserAuthentication** moet u de volgende wijzigingen aanbrengen:

- **ApplicationId** (uw Azure Active Directory toepassings-id die wordt gebruikt voor aanmelding)
- **Gebruikers naam** (uw Active Directory-gebruikers naam)
- **Wacht woord** (uw Active Directory-wacht woord).

Niet wijzigen:

- **ResourceUrl**
- **RedirectUrl**

### <a name="appauthentication"></a>AppAuthentication

Voor **AppAuthentication** moet u de volgende wijzigingen aanbrengen:

- **ApplicationId** (uw Active Directory-toepassings-id die wordt gebruikt voor het aanmelden van de toepassing)
- **ApplicationSecret** (uw Active Directory-toepassings geheim gebruikt voor het aanmelden van de toepassing)
- **Domein** (uw Active Directory-domein waarop de toepassing wordt gehost)

### <a name="scenariosettings"></a>ScenarioSettings

Wijzig voor **ScenarioSettings** niet:

- **CustomerDomainSuffix** (het domein achtervoegsel dat wordt gebruikt bij het maken van een nieuwe klant)

Optionele instellingen. Als dit veld leeg blijft, moet deze informatie worden gegenereerd wanneer een scenario wordt uitgevoerd, waar nodig):

- **CustomerIdToDelete** (de id van de klant die wordt gebruikt voor verwijdering)
- **DefaultCustomerId** (de klant-id die moet worden gebruikt in aan klanten gerelateerde scenario's)
- **DefaultInvoiceID** (de factuur-ID die moet worden gebruikt in factuur scenario's)
- **PartnerMpnId** (de MPN-id van de partner die moet worden gebruikt in scenario's met indirecte partners)
- **DefaultServiceRequestId** (de service aanvraag-id die in service-aanvraag scenario's moet worden gebruikt)
- **DefaultSupportTopicID** (de ondersteunings onderwerp-id die moet worden gebruikt in service-aanvraag scenario's)
- **DefaultOfferID** (de AANBIEDINGS-id die moet worden gebruikt in aanbod scenario's)
- **DefaultOrderID** (de order-id die in order scenario's moet worden gebruikt)
- **DefaultSubscriptionID** (de abonnements-id die moet worden gebruikt in scenario's voor abonnementen)

Optioneel om te wijzigen. Met al deze instellingen geeft u de hoeveelheid items per pagina op tijdens het ophalen van de pagina-inhoud:

- **CustomerPageSize**
- **InvoicePageSize**
- **ServiceRequestPageSize**
- **DefaultOfferPageSize**
- **SubscriptionPageSize**
