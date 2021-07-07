---
title: Console-testapp
description: Deze consoletest-app biedt voorbeeldcode voor alle scenario's die worden ondersteund door Partner Center API's. U kunt deze ook gebruiken voor het testen.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: b35167104deeede50107d59fca6112c10dc7b4bf
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974026"
---
# <a name="console-test-app"></a>Console-testapp

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De consoletest-app is beschikbaar in C# en Java en bevat voorbeeldcodes voor alle scenario's die worden ondersteund door de Partner Center API's. U kunt deze ook gebruiken voor het testen.

## <a name="get-the-code"></a>Code ophalen

Download de voorbeeldcode voor de consoletest-app.

## <a name="net"></a>.NET

[Download de voorbeeldcode en](https://go.microsoft.com/fwlink/p/?LinkId=746682) wijzig deze indien nodig.

> [!IMPORTANT]
> Voordat u de toepassing bouwt,  moet u de waarden in hetApp.config-bestand bijwerken om de Azure AD-verificatiegegevens weer te geven die u hebt gemaakt in [Partner Center verificatie.](partner-center-authentication.md) Gebruik met name de instellingen van uw sandbox-account voor integratie tijdens vroege ontwikkeling of voor testen in productie.

Onder **ScenarioSettings** in *hetApp.config* kunt u parameters instellen die automatisch worden doorgegeven aan de scenario's die u wilt uitvoeren.

Als u de lijst met scenario's wilt wijzigen die worden uitgevoerd, maakt u commentaar van regels in **IPartnerScenario \[ \] mainScenarios** of in een afzonderlijke methode **Get Scenarios** in het *bestand Program.cs.*

## <a name="java"></a>Java

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

[Download de voorbeeldcode en](https://go.microsoft.com/fwlink/p/?LinkId=2026887) wijzig deze indien nodig.

> [!IMPORTANT]
> Voordat u de toepassing bouwt, moet u de waarden in het bestand *SamplesConfigurations.js* bijwerken om de Azure AD-verificatiegegevens weer te geven die u hebt gemaakt in [Partner Center verificatie.](partner-center-authentication.md) Gebruik met name de instellingen van uw sandbox-account voor integratie tijdens vroege ontwikkeling of voor testen in productie.

Onder **ScenarioSettings** in *SamplesConfiguration.json* file kunt u parameters instellen die automatisch worden doorgegeven aan de scenario's die u gebruikt.

Als u de lijst met scenario's wilt wijzigen die worden uitgevoerd, maakt u commentaar van regels in **IPartnerScenario \[ \] mainScenarios** of in een afzonderlijke methode **Get Scenarios** in het *bestand Program.java.*

## <a name="what-to-change"></a>Wat u moet wijzigen

Gebruik de volgende lijsten om te bepalen wat er wel of niet moet worden gewijzigd in de voorbeeldcode.

### <a name="partnerservicesettings"></a>PartnerServiceSettings

Voor **PartnerServiceSettings** wijzigt u niet:

- **PartnerServiceApiEndpoint**
- **AuthenticationAuthorityEndpoint**
- **GraphEndpoint**
- **CommonDomain**

Al deze instellingen zijn nodig om de voorbeeld-API-aanroepen goed te laten functioneren.

### <a name="userauthentication"></a>UserAuthentication

Voor **UserAuthentication** moet u het volgende wijzigen:

- **ApplicationId** (uw Azure Active Directory-toepassings-id die wordt gebruikt voor aanmelding)
- **Gebruikersnaam** (gebruikersnaam active directory)
- **Wachtwoord** (uw Active Directory-wachtwoord).

Niet wijzigen:

- **ResourceUrl**
- **RedirectUrl**

### <a name="appauthentication"></a>AppAuthentication

Voor **AppAuthentication** moet u het volgende wijzigen:

- **ApplicationId** (de toepassings-id van uw Active Directory die wordt gebruikt voor aanmelding bij de toepassing)
- **ApplicationSecret (uw** active directory-toepassingsgeheim dat wordt gebruikt voor aanmelding bij de toepassing)
- **Domein** (uw Active Directory-domein waarop de toepassing wordt gehost)

### <a name="scenariosettings"></a>ScenarioSettings

Voor **ScenarioSettings** wijzigt u niet:

- **CustomerDomainSuffix** (het domeinachtervoegsel dat wordt gebruikt bij het maken van een nieuwe klant)

Optionele instellingen. Als u dit leeg laat, moet deze informatie worden ingevoerd bij het uitvoeren van een scenario, indien nodig):

- **CustomerIdToDelete** (de id van de klant die is gebruikt voor verwijdering)
- **DefaultCustomerId** (de klant-id die moet worden gebruikt in klantgerelateerde scenario's)
- **DefaultInvoiceID** (de factuur-id die moet worden gebruikt in factuurscenario's)
- **PartnerMpnId** (de MPN-id van de partner die moet worden gebruikt in indirecte partnerscenario's)
- **DefaultServiceRequestId** (de serviceaanvraag-id voor gebruik in serviceaanvraagscenario's)
- **DefaultSupportTopicID** (de id van het ondersteuningsonderwerp voor gebruik in serviceaanvraagscenario's)
- **DefaultOfferID** (de aanbiedings-id die moet worden gebruikt in aanbiedingsscenario's)
- **DefaultOrderID** (de order-id die moet worden gebruikt in orderscenario's)
- **DefaultSubscriptionID** (de abonnements-id die moet worden gebruikt in abonnementsscenario's)

Optioneel om te wijzigen. Al deze instellingen geven de hoeveelheid vermeldingen per pagina op bij het ophalen van pagina-inhoud:

- **CustomerPageSize**
- **InvoicePageSize**
- **ServiceRequestPageSize**
- **DefaultOfferPageSize**
- **SubscriptionPageSize**
