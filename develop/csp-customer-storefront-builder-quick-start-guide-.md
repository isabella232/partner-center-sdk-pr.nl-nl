---
title: Quick Start-handleiding voor CSP-klant webwinkelbouwer
description: Maak een online marketplace voor het verkopen van CSP-aanbiedingen (Cloud Solution Provider) met behulp van de CSP Customer Storefront Builder.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8550492c7a4201a955c7b051b453103628612f3e
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973346"
---
# <a name="csp-customer-storefront-builder-quick-start-guide"></a>Quick Start-handleiding voor CSP-klant webwinkelbouwer

Maak een online marketplace voor het verkopen van CSP-aanbiedingen (Cloud Solution Provider) met behulp van de CSP Customer Storefront Builder.

## <a name="introduction-to-the-csp-customer-storefront-builder"></a>Inleiding tot de CSP Customer Storefront Builder

Met CSP Customer Storefront Builder kunnen partners eenvoudig een online marketplace maken om CSP-aanbiedingen aan hun klanten te verkopen. De meeste partners en kleine verkooporganisaties willen zich richten op verkopen in plaats van op het ontwikkelen van een online marketplace. De Partnercentrum-SDK-app vereist vaardigheden op het gebied van softwareontwikkeling om een website te maken en te implementeren. Met de CSP Customer Storefront Builder kunt u snel en eenvoudig uw eigen website maken. U kunt de website ook downloaden als voorbeeldcode of rechtstreeks implementeren in uw Azure-abonnement met een Ready to Transact-website.

Deze website is volledig eigendom van, wordt ondersteund en wordt onderhouden door partners en Microsoft verzamelt geen gegevens of telemetrie van de website. De CSP Customer Storefront Builder maakt een website voor de partner die volledig compatibel is met de [Payment Card Industry Data Security Standard](https://www.pcisecuritystandards.org/) (PCI DSS).

De code van CSP Customer Storefront Builder is onderhevig aan de licentie die beschikbaar is in [de Partnercentrum-SDK EULA.](/legal/partner-center/eula-partner-center-sdk)

>[!NOTE]
>U bent verantwoordelijk voor het beheer van de webwinkelwebsite, het onderhoud en eventuele problemen die het gevolg kunnen zijn van het maken van de website. Lees en begrijp de termen in de [Partnercentrum-SDK EULA](/legal/partner-center/eula-partner-center-sdk).

Zie voor meer informatie ook de volgende artikelen: webwinkel van [CSP-klant](csp-customer-web-storefront.md) en [consoletest-app.](console-test-app.md)

## <a name="considerations"></a>Overwegingen

De CSP Customer Storefront Builder is bedoeld als een snelle manier om een website te maken. Let tijdens de planning op de volgende overwegingen:

- Na de geïmplementeerde service onderhouden Microsoft en Partner Center geen kopie van de partnerwebsite of informatie die is toegevoegd aan de CSP Customer Storefront Builder.

- Partner Center kan alleen een CSP Customer Storefront-website implementeren in de Azure-abonnementen van een partner.

- Nadat deze website is geïmplementeerd, is deze volledig eigendom van en wordt deze beheerd door de partner. Microsoft heeft geen toegang tot deze website of tot gegevens met betrekking tot de website. Partners zijn verantwoordelijk voor het onderhoud en beheer van de website. Microsoft biedt geen livewebsites of andere ondersteuning met betrekking tot de CSP Customer Storefront Builder of een website die is gemaakt met behulp van de CSP Customer Storefront Builder.

- Partner Center kan deze website niet rechtstreeks openen of upgraden met nieuwe of gewijzigde SDK- of API-functies. Nieuwe functies of verbeteringen moeten eigendom zijn, worden ontwikkeld en beheerd door partners, inclusief het toevoegen van nieuwe Partnercentrum-SDK of API-functies.

- Deze CSP Customer Storefront Builder biedt momenteel de mogelijkheid om betaling naar een PayPal Pro/PayU Money-account (voor India) te configureren. Als partners de betalingsverwerker moeten wijzigen, moeten ze de code wijzigen om de betalingswijze van hun voorkeur te ondersteunen.

- Alle betalingsgerelateerde informatie die is toegevoegd in de CSP Customer Storefront Builder wordt niet opgeslagen of onderhouden in Partner Center.

- PayPal betalingsconfiguratie werkt in alle geografische gebieden waar PayPal beschikbaar is. PayPal beschikbaarheid en ondersteuning worden uitsluitend bepaald door PayPal en kunnen op elk moment worden stopgezet door PayPal.

- PayU-betalingsconfiguratie werkt momenteel alleen in India. PayU-beschikbaarheid en -ondersteuning worden uitsluitend beheerd door PayU en kunnen op elk moment door PayU worden stopgezet.

- Lees en begrijp de termen in de [Partnercentrum-SDK EULA](/legal/partner-center/eula-partner-center-sdk).

## <a name="using-the-csp-customer-storefront-builder"></a>De CSP Customer Storefront Builder gebruiken

CSP-partnerbeheerders op Partner Center kunnen een CSP Customer Storefront rechtstreeks vanuit Partner Center. Met minimale inspanning kan een nieuwe website worden geïmplementeerd op de tenant van de partner. Na de configuratie kunnen partners de website gebruiken om huisstijl, aanbiedingen en betalingsgerelateerde informatie te configureren en vervolgens het URL-adres van de website te delen met klanten.

Het proces voor het maken van een webwinkelwebsite is:

1. [De website implementeren](#deploy)

2. [De webwinkel configureren](#configure)

3. [Transact op de webwinkel](#transact)

### <a name="deploy"></a>Implementeren

Implementatieopties:

- Download de [voorbeeldcode Partner Center webwinkel van](https://github.com/Microsoft/Partner-Center-Storefront) GitHub
- Integreren met Azure om de geconfigureerde website te implementeren
- Implementeren in een bestaand abonnement of uw eigen abonnement gebruiken

### <a name="configure"></a>Configureren

Er zijn geen ontwikkelvaardigheden vereist om een webwinkel aan te passen.

Meld u aan met uw Partner Center beheerdersreferenties om het volgende te configureren:

- **Huisstijl:** bedrijfsnaam, logo, contactpersonen en meer.

- **Aanbiedingen:** alle CSP-aanbiedingen weergeven. U kunt selecteren welke aanbiedingen uw klanten kunnen bekijken en kopen. U kunt ook de aanbiedingsgegevens personaliseren en uw prijs toevoegen.

- **PayPal betalingsconfiguratie:** voeg de gegevens van PayPal betalingsaccount toe. Als u geen account voor PayPal hebt, kunt u naar gaan [https://www.paypal.com](https://www.paypal.com) en een nieuw account maken. Dit account wordt gebruikt voor het PayPal van de betalingen van klanten. *Microsoft is niet verantwoordelijk voor de relatie tussen partners en PayPal. Het gebruik PayPal kan vereisen dat de klanten van de partner of partner akkoord gaan met aanvullende voorwaarden.*

- (*Voor India*) **PayU-betalingsconfiguratie:** voeg uw payu money-betalingsaccountgegevens toe. Als u geen PayU Money-account hebt, kunt u naar gaan [https://www.payumoney.com/](https://www.payumoney.com/) en een nieuw account maken. Dit account wordt gebruikt voor betalen per gebruik om de betalingen van klanten bij te betalen. *Microsoft is niet verantwoordelijk voor de relatie tussen partners en PayU. Voor het gebruik van PayU moeten de klanten van de partner of partner mogelijk akkoord gaan met aanvullende voorwaarden.*

### <a name="transact"></a>Transact

- Na de implementatie kunnen klanten direct aankopen doen en een transact-aankoop doen.

- Klanten kunnen rechtstreeks kopen via de partnerportal die is geïntegreerd met de Partnercentrum-SDK.

#### <a name="customer-countries"></a>Klant landen

Klanten kunnen tot deze landen behoren:

| Landnummer | Naam van land/regio   |
|--------------|----------------|
| AU           | Australië      |
| AT           | Oostenrijk        |
| BE           | België        |
| BG           | Bulgarije       |
| CA (consistentie en beschikbaarheid)           | Canada         |
| HR           | Kroatië        |
| CY           | Cyprus         |
| CZ           | Tsjechische Republiek |
| DK           | Denemarken        |
| EE           | Estland        |
| FI           | Finland        |
| FR           | Frankrijk         |
| DE           | Duitsland        |
| GR           | Griekenland         |
| HU           | Hongarije        |
| IS           | IJsland        |
| IN           | India          |
| IE           | Ierland        |
| IT           | Italië          |
| JP           | Japan          |
| LV           | Letland         |
| LI           | Liechtenstein  |
| LT           | Litouwen      |
| LU           | Luxemburg     |
| MT           | Malta          |
| MC           | Monaco         |
| NL           | Nederland    |
| NZ           | Nieuw-Zeeland    |
| NO           | Noorwegen         |
| Po           | Polen         |
| PT           | Portugal       |
| RO           | Roemenië        |
| SK           | Slowakije       |
| SL           | Slovenië       |
| ES           | Spanje          |
| SE           | Zweden         |
| CH           | Zwitserland    |
| GB           | Verenigd Koninkrijk |
| VS           | Verenigde Staten  |

## <a name="partner-experience-scenarios"></a>Partnerervaringsscenario's

### <a name="deployment-scenario"></a>Implementatiescenario

Een verbeterde of aangepaste CSP Customer Storefront implementeren:

- Download de [voorbeeldcode Partner Center webwinkel om](https://github.com/Microsoft/Partner-Center-Storefront) aanvullende aanpassingen te maken.

- Gebruik Microsoft Visual Studio 2015 (of hoger) om te ontwikkelen.

- Bouw voor aanvullende wijzigingen en verbeteringen (inclusief autorisaties, certificeringen, manifestwijzigingen en andere items).

### <a name="configuration-scenario"></a>Configuratiescenario

- De zojuist gemaakte website is gekoppeld aan een partner-tenant en heeft toegang tot alle beheerdersaccounts van deze partner-tenant.

  - Partners kunnen zich aanmelden bij deze nieuwe website met hun Partner Center beheerdersreferenties.

- De webwinkeltoepassing ondersteunt momenteel Frans, Spaans, Nederlands, Duits, Japans en Engels. (Engels fungeert als de terugvaltaal.)

  - De webwinkel configureert de locale met behulp van de standaardinstelling van de partner uit het profiel van de partner in de Partner Center. Deze landen worden gebruikt voor het configureren van valuta's, datumindelingen en gelokaliseerde aanbiedingen in de opslagplaats.

- Partners kunnen de huisstijl, aanbiedingen en PayPal betalingsgegevens van PayU (voor India) configureren.

- Partners kunnen onder andere de bedrijfsnaam, het bedrijfslogo, de koptekstafbeelding, verkoop- en ondersteuningscontacten bijwerken.

- Partners kunnen alle CSP-aanbiedingen zien die beschikbaar zijn op basis van hun gebied.

  - Partners kunnen kiezen welke aanbiedingen ze aan al hun klanten willen laten zien.

  - Een CSP-partner kan een of meer aanbiedingen selecteren en de naam, hoeveelheid, functiebeschrijving en prijs bijwerken.
  - De prijs is de jaarlijkse prijs. Klanten abonneren zich jaarlijks.

- Partners kunnen op elk moment vooraf goedgekeurde transacties configureren voor (a) alle huidige en toekomstige klanten OF (b) specifieke klanten.

  - Vooraf goedgekeurde klanten zijn niet verplicht om te betalen via de portal wanneer ze nieuwe abonnementen toevoegen, extra licenties aanschaffen voor bestaande abonnementen of een abonnement verlengen.

  - Vooraf goedgekeurde klanten worden niet omgeleid naar PayPal of PayU (voor India) voor betaling tijdens deze transacties.

  - Met vooraf goedgekeurde klanttransacties kan een partner offline facturering en facturering uitvoeren voor zijn vooraf goedgekeurde klanten.

- Een CSP-partner kan de accountgegevens PayPal, zoals de client PayPal-id en het geheim. Een CSP-partner kan ook selecteren of ze willen testen met behulp van een sandbox of een live-account.

  - Partners kunnen deze informatie vinden [https://developer.paypal.com/](https://developer.paypal.com/) in mijn apps & **referenties**. U kunt deze informatie ook verkrijgen van een huidige app of door een nieuwe app te maken in PayPal.
  - Maak een PayPal account als u er nog geen hebt. Dit account wordt gebruikt voor het PayPal van de betalingen van klanten.

    - Zie voor het openen PayPal [https://developer.paypal.com/docs/classic/lifecycle/goingLive/#register](https://developer.paypal.com/docs/classic/lifecycle/goingLive/#register) bedrijfsaccount.

    - Zie voor het maken PayPal [https://developer.paypal.com/docs/classic/lifecycle/ug_sandbox/](https://developer.paypal.com/docs/classic/lifecycle/ug_sandbox/) sandbox-account.

- (Voor India) kan een CSP-partner de gegevens van de payu-geldrekening invoeren, zoals de payu-client-id en het wachtwoord. Partners kunnen meer informatie vinden over [https://developer.payumoney.com/](https://developer.payumoney.com/) .

  - Maak een nieuw payu money-account als u er nog geen hebt. Als u een payu money-account wilt openen, gaat u naar [https://www.payumoney.com/merchant-account/#/](https://www.payumoney.com/merchant-account/#/) . Dit account wordt gebruikt voor betalen per gebruik om de betalingen van klanten bij te betalen.

## <a name="customer-experience-scenarios"></a>Scenario's voor klantervaring

### <a name="new-customer-sign-up-scenario"></a>Aanmeldingsscenario voor nieuwe klant

- De website is standaard openbaar beschikbaar en toont de catalogus van de partner op de startpagina.

- Klanten kunnen nu deel uitmaken van een groot aantal [klant-landen.](#customer-countries)

- De focus ligt op de landen van de Europese Free Trade Association (EFTA), Noord-Amerika, Japan, India, Australië en Nieuw-Zeeland.
  - Deze functie maakt gebruik van de regionale autorisatieondersteuning in de Partnercentrum-SDK.

- Klanten kunnen een aanbieding in de catalogus selecteren om aan te schaffen.
  - Ze kunnen hun klantnaam, adres en domeingerelateerde informatie toevoegen.

- Klanten worden omgeleid naar de PayPal betalen per e-mail of betaling (voor India). Klanten kunnen betalen met behulp van een van de volgende:
  - Hun bestaande PayPal of PayU-account (voor India)
  - Financiële middelen die in hun land worden ondersteund door PayPal of PayU (voor India). Dit kunnen creditcards, debitcards en bankrekeningen zijn, indien van toepassing.

- Er wordt een klant-tenant gemaakt voor deze klant. Nadat de tenantorder is gemaakt, krijgen klanten de gebruikersnaam, het wachtwoord en de abonnementsgegevens van het account.
  - Klanten kunnen de gebruikersnaam en het wachtwoord opslaan om aangemeld te blijven voor verdere aankopen.
  - Elk abonnement wordt een jaar aangeschaft en klanten kunnen 30 dagen vóór de einddatum van het abonnement verlengen.

### <a name="view-prior-purchases-scenario"></a>Scenario voor eerdere aankopen bekijken

- De klant meldt zich aan met de gebruikersnaam en het wachtwoord van de tenant van de klant en gaat naar **de sectie Mijn orders.**

- Klanten kunnen naar de pagina **Mijn orders** navigeren waar ze aangeschafte abonnementen kunnen bekijken en indien nodig updates kunnen uitvoeren.

- Klanten kunnen naar de **pagina Mijn** abonnementen navigeren waar ze alle abonnementen (op licentie gebaseerd en op basis van gebruik) kunnen bekijken, met inbegrip van de abonnementen die worden onderhouden in Partner Center.

### <a name="add-licenses-to-existing-subscriptions-scenario"></a>Licenties toevoegen aan bestaand abonnementsscenario

- In de **sectie Mijn** orders kunnen klanten meer licenties toevoegen aan bestaande abonnementen. Klanten kunnen op elk gewenst moment tijdens een abonnementsjaar meer licenties toevoegen.

- Elke toegevoegde licentie wijzigt de einddatum van het abonnement niet. De prijs van het abonnement wordt echter gewijzigd op basis van de datum waarop u de licentie toevoegt en waar die datum in het jaar valt. De prijzen worden per dag pro 2018 naar meer dan de resterende dagen van het jaar in rekening brengen.

### <a name="add-more-subscriptions-scenario"></a>Scenario voor meer abonnementen toevoegen

- Klanten kunnen elk aantal abonnementen op elk moment kopen via de sectie **Abonnementen toevoegen** onder **Mijn orders.**

- Een klant kan een abonnement selecteren, een hoeveelheid toevoegen en betalen om de transactie te voltooien en direct aan de slag te gaan met het abonnement. Als een klant een vooraf goedgekeurde klant is, is het abonnement onmiddellijk beschikbaar voor gebruik en wordt er een factuur naar de klant verzonden voor betaling.

### <a name="renew-subscription-scenario"></a>Abonnementsscenario verlengen

- Een klant kan een abonnement verlengen in de afgelopen 30 dagen vóór de einddatum van het abonnement.

- Dit is alleen beschikbaar in de afgelopen 30 dagen.

- Als het abonnement in de afgelopen 30 dagen niet is vernieuwd, wordt het verwijderd uit de lijst met abonnementen voor deze klantten tenant.

- U kunt de hoeveelheid niet bijwerken tijdens de verlenging.

### <a name="payments-scenario"></a>Betalingsscenario

- Als de klant vooraf is goedgekeurd voor transacties door de beheerder, wordt de betalingservaring niet weergegeven voor de bovenstaande scenario's. In plaats daarvan kan de partner de factuur voor betaling verzenden naar de vooraf goedgekeurde klant.

- Voor alle nieuwe aankopen kunt u meer licenties toevoegen, abonnementen toevoegen en verlengen. Een klant kan een partner betalen via deze website via PayPal of PayU (voor India).

- Deze website is geïntegreerd met PayPal of PayU (voor India) en biedt partners de mogelijkheid om betalingen van hun klanten te accepteren. PayPal of PayU -tegoed (voor India) dit bedrag in het account van een partner. PayPal of PayU (voor India) Bankaccountbeheer is buiten deze website en wordt beheerd op PayPal.com of PayUmoney.com.

- Dit is afhankelijk van partners die hun betalingsconfiguratie voor PayPal ofBetalen (voor India) configureren op PayPal.com of PayUmoney.com. Microsoft sla deze informatie of de werkelijke betalingstransacties die het gevolg zijn van het gebruik van deze optie, niet op.

### <a name="prorated-pricing-scenario"></a>Scenario met naar prijsstelling

- Deze website ondersteunt naar meer prijzen wanneer klanten meer licenties toevoegen aan een bestaand abonnement.

- Elk abonnement verloopt na één jaar en kan niet worden gewijzigd nadat het abonnement is aangeschaft.

- De einddatum van het abonnement wordt niet gewijzigd door extra licenties toe te voegen. Er worden kosten in rekening gebracht voor het resterende aantal dagen tot de einddatum. Als de abonnementskosten bijvoorbeeld op dag één $ 365 zijn en u op dag twee nog een licentie toevoegt, is de prijs voor de nieuwe licentie $ 364. Als u tien dagen later nog een licentie toevoegt, is de prijs $ 354.
