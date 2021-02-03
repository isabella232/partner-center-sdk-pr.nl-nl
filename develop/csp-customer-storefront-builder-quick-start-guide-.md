---
title: Quick Start-handleiding voor CSP-klant webwinkelbouwer
description: Maak een online Marketplace voor het verkopen van CSP-aanbiedingen (Cloud Solution Provider) met behulp van de CSP Customer Marketplace Builder.
ms.date: 05/29/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: d64deff9b002b861c9f48d076feb5841af727e3d
ms.sourcegitcommit: 57620e249e218edc4af7c83c2ce8a3008a4adf4e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/04/2020
ms.locfileid: "97767330"
---
# <a name="csp-customer-storefront-builder-quick-start-guide"></a>Quick Start-handleiding voor CSP-klant webwinkelbouwer

**Van toepassing op:**

- Partnercentrum

Maak een online Marketplace voor het verkopen van CSP-aanbiedingen (Cloud Solution Provider) met behulp van de CSP Customer Marketplace Builder.

## <a name="introduction-to-the-csp-customer-storefront-builder"></a>Inleiding tot de CSP Customer Support Builder

De CSP Customer Marketplace Builder helpt partners bij het eenvoudig maken van een online Marketplace voor het verkopen van CSP-aanbiedingen aan hun klanten. De meeste partners en kleine verkoop organisaties willen zich richten op de verkoop in plaats van een online Marketplace te ontwikkelen. De Partner Center SDK-voor beeld-app vereist vaardig heden voor software ontwikkeling voor het maken en implementeren van een website. Met de cryptografie provider van CSP kunt u snel en eenvoudig uw eigen website maken. U kunt de website ook downloaden als voorbeeld code of rechtstreeks implementeren in uw Azure-abonnement met een kant-en-klare website.

Deze website is volledig eigendom van, wordt ondersteund en wordt beheerd door partners, en micro soft verzamelt geen gegevens of telemetrie van de website. De provider voor het maken van de CSP-klant en maakt een website voor de partner die volledig compatibel is met de [Payment Card Industry Data Security Standard](https://www.pcisecuritystandards.org/) (PCI DSS).

De provider van de CSP-klanten-winkel bouwer is onderhevig aan de licentie die beschikbaar is in de [gebruiksrecht overeenkomst voor de SDK van partner Center](https://partnercenter.microsoft.com/partner/EULA_Partner_Center_SDK).

>[!NOTE]
>U bent verantwoordelijk voor het beheer, onderhoud en eventuele problemen van de winkel website die kunnen ontstaan door het maken van een website. Lees de voor waarden in de [gebruiksrecht overeenkomst van de Partner Center-SDK](https://partnercenter.microsoft.com/partner/EULA_Partner_Center_SDK).

Raadpleeg de volgende artikelen voor meer informatie: CSP- [klant webwinkel](csp-customer-web-storefront.md) en [console test-app](console-test-app.md).

## <a name="considerations"></a>Overwegingen

De provider van de CSP-klant en-ondersteuning is bedoeld als snelle manier om een website te maken. Houd rekening met de volgende overwegingen tijdens uw planning:

- Zodra micro soft en partner Center eenmaal zijn geïmplementeerd, wordt er geen kopie van de partner website bijgehouden of worden de gegevens toegevoegd aan de provider van de klanten winkel van de CSP.

- In het partner centrum kan alleen een CSP-klant van een website worden geïmplementeerd voor Azure-abonnementen van een partner.

- Deze website is eenmaal geïmplementeerd en is volledig eigendom van en wordt beheerd door de partner. Micro soft heeft geen toegang tot deze website of geen gegevens met betrekking tot de website. Partners zijn verantwoordelijk voor onderhoud en beheer van de website. Micro soft biedt geen enkele live website of andere ondersteuning met betrekking tot de CSP Customer Online Builder of een website die is gemaakt met behulp van de CSP Customer Online Builder.

- Partner centrum kan deze website niet rechtstreeks openen of bijwerken met nieuwe of gewijzigde SDK-of API-functies. Nieuwe functies of verbeteringen moeten eigendom zijn van en worden beheerd door partners, waaronder het toevoegen van nieuwe functies van de SDK of API van de Partner Center.

- Deze CSP Customer Support Builder biedt momenteel de mogelijkheid om de betaling te configureren voor een PayPal Pro/PayU Money (voor India)-account. Als partners de betalings processor moeten wijzigen, moeten ze de code wijzigen zodat ze hun voorkeurs betalings methode kunnen ondersteunen.

- Alle betaling gerelateerde informatie die is toegevoegd aan de CSP Customer Support Builder, wordt niet opgeslagen of onderhouden in het partner centrum.

- De configuratie van PayPal-betalingen werkt in alle geografische gebieden waar PayPal beschikbaar is. De beschik baarheid en ondersteuning van PayPal wordt uitsluitend beheerd door PayPal en kan op elk moment door PayPal worden stopgezet.

- PayU-betalings configuratie werkt momenteel alleen in India. De beschik baarheid en ondersteuning van PayU worden uitsluitend bepaald door PayU en kunnen op elk moment worden stopgezet door PayU.

- Lees de voor waarden in de [gebruiksrecht overeenkomst van de Partner Center-SDK](https://partnercenter.microsoft.com/partner/EULA_Partner_Center_SDK).

## <a name="using-the-csp-customer-storefront-builder"></a>De CSP Customer Support Builder gebruiken

CSP-partner beheerders in het partner centrum kunnen een CSP-klanten winkel rechtstreeks vanuit het partner centrum implementeren. Met minimale inspanning kan een nieuwe website worden geïmplementeerd op de Tenant van de partner. Na de implementatie kunnen partners de website gebruiken om huis stijl, aanbiedingen en informatie over de betaling te configureren en vervolgens het URL-adres van de website met klanten te delen.

Het proces voor het maken van een winkel website bestaat uit het volgende:

1. [De website implementeren](#deploy)

2. [De winkel configureren](#configure)

3. [Trans acties op de winkel](#transact)

### <a name="deploy"></a>Implementeren

Implementatie opties:

- De [voorbeeld code van het Partner Center-winkel](https://github.com/Microsoft/Partner-Center-Storefront) pakket downloaden van github
- Integreren met Azure om de geconfigureerde website te implementeren
- Implementeren in een bestaand abonnement of uw eigen abonnement nemen

### <a name="configure"></a>Configureren

Er zijn geen ontwikkel vaardigheden vereist om een winkel aan te passen.

Meld u aan met de beheerders referenties van uw partner centrum om het volgende te configureren:

- **Branding**: Bedrijfs naam, logo, contact personen en meer.

- **Aanbiedingen**: alle CSP-aanbiedingen weer geven. U kunt selecteren welke aanbiedingen uw klanten kunnen bekijken en kopen. Je kunt ook aanbiedings gegevens personaliseren en je prijs toevoegen.

- **Configuratie van PayPal**-betalingen: Voeg de gegevens van uw PayPal-betalings account toe. Als u geen PayPal-account hebt, kunt u [https://www.paypal.com](https://www.paypal.com) een nieuw account bezoeken en maken. Dit account wordt gebruikt voor PayPal om de door klanten gemaakte betalingen te crediteren. *Micro soft is niet verantwoordelijk voor de relatie tussen partners en PayPal. Het gebruik van PayPal vereist mogelijk dat de partner of partner van de klant akkoord gaat met aanvullende voor waarden.*

- (*Voor India*) **PayU-betalings configuratie**: Voeg de gegevens van uw PayU Money-betalings account toe. Als u geen PayU Money-account hebt, kunt u [https://www.payumoney.com/](https://www.payumoney.com/) een nieuw account bezoeken en maken. Dit account wordt gebruikt voor PayU om de betalingen te crediteren die door klanten worden gedaan. *Micro soft is niet verantwoordelijk voor de relatie tussen partners en PayU. Voor het gebruik van PayU kunnen de klanten van de partner of de partner instemmen met aanvullende voor waarden.*

### <a name="transact"></a>Transact

- Na de implementatie kunnen klanten onmiddellijk kopen en trans acties uitvoeren.

- Klanten kunnen rechtstreeks kopen via de partner portal die is geïntegreerd met de Partner Center-SDK.

#### <a name="customer-countries"></a>Klant landen

Klanten kunnen deel uitmaken van deze landen:

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
| Bestel           | Polen         |
| PT           | Portugal       |
| RO           | Roemenië        |
| SK           | Slowakije       |
| SL           | Slovenië       |
| ES           | Spanje          |
| SE           | Zweden         |
| CH           | Zwitserland    |
| GB           | Verenigd Koninkrijk |
| VS           | Verenigde Staten  |

## <a name="partner-experience-scenarios"></a>Scenario's voor partner ervaring

### <a name="deployment-scenario"></a>Implementatiescenario

Een uitgebreide of aangepaste CSP-klant-winkel implementeren:

- Down load de [voorbeeld code van het Partner Center-winkel programma](https://github.com/Microsoft/Partner-Center-Storefront) om extra aanpassingen aan te brengen.

- Gebruik micro soft Visual Studio 2015 (of hoger) om te ontwikkelen.

- Bouwen voor aanvullende wijzigingen en verbeteringen (inclusief autorisaties, certificeringen, manifest wijzigingen en andere items).

### <a name="configuration-scenario"></a>Configuratiescenario

- De zojuist gemaakte website is gekoppeld aan een partner-Tenant en heeft toegang tot alle beheerders accounts van deze partner Tenant.

  - Partners kunnen zich aanmelden bij deze nieuwe website met behulp van de referenties van de Partner Center-beheerder.

- De winkel toepassing biedt momenteel ondersteuning voor Frans, Spaans, Nederlands, Duits, Japans en Engels. (Engels fungeert als de terugval taal.)

  - Op de winkel wordt de land instelling geconfigureerd met de standaard land instelling van de partner van het Partner profiel in het partner centrum. Deze land instelling wordt gebruikt voor het configureren van valuta's, datum notaties en gelokaliseerde aanbiedingen in de opslag plaats.

- Partners kunnen de betalings gegevens voor huis stijl, aanbiedingen en PayPal of PayU (voor India) configureren.

- Partners kunnen de bedrijfs naam, het bedrijfs logo, de koptekst afbeelding, de verkoop-en ondersteunings contacten, en meer, bijwerken.

- Partners kunnen alle CSP-aanbiedingen zien die beschikbaar zijn op basis van hun eigen gebied.

  - Partners kunnen kiezen welke aanbiedingen ze willen weer geven aan al hun klanten.

  - Een CSP-partner kan een of meer aanbiedingen selecteren en de naam, hoeveelheid, functie beschrijving en prijs bijwerken.
  - De prijs is de prijs per jaar. Klanten nemen jaarlijks een abonnement.

- Partners kunnen op elk moment vooraf goedgekeurde trans acties configureren voor (a) alle huidige en toekomstige klanten of (b) specifieke klanten.

  - Vooraf goedgekeurde klanten hoeven niet te betalen op de Portal wanneer ze nieuwe abonnementen toevoegen, extra licenties aan bestaande abonnementen aanschaffen of een abonnement verlengen.

  - Vooraf goedgekeurde klanten worden niet omgeleid naar PayPal of PayU (voor India) voor betaling tijdens deze trans acties.

  - Met vooraf goedgekeurde klant transacties kan een partner offline facturering uitvoeren en factureren aan hun vooraf goedgekeurde klanten.

- Een CSP-partner kan hun PayPal-account gegevens invoeren, zoals PayPal-client-ID en geheim. Een CSP-partner kan ook selecteren of ze willen testen met behulp van een sandbox of een Live-account.

  - Partners kunnen deze informatie vinden [https://developer.paypal.com/](https://developer.paypal.com/) in **mijn apps & referenties**. U kunt deze informatie ook ophalen uit een huidige app of door een nieuwe app te maken in PayPal.
  - Maak een nieuwe PayPal-account als u er nog geen hebt. Dit account wordt gebruikt voor PayPal om de door klanten gemaakte betalingen te crediteren.

    - Zie voor meer informatie over het openen van een PayPal-bedrijfs account [https://developer.paypal.com/docs/classic/lifecycle/goingLive/#register](https://developer.paypal.com/docs/classic/lifecycle/goingLive/#register) .

    - Zie voor het maken van een PayPal sandbox-account [https://developer.paypal.com/docs/classic/lifecycle/ug_sandbox/](https://developer.paypal.com/docs/classic/lifecycle/ug_sandbox/) .

- (Voor India) een CSP-partner kan hun PayU Money-account gegevens invoeren, zoals PayU-client-ID en wacht woord. Partners kunnen meer informatie vinden over [https://developer.payumoney.com/](https://developer.payumoney.com/) .

  - Maak een nieuw PayU Money-account als u er nog geen hebt. Als u een PayU Money-account wilt openen, gaat u naar [https://www.payumoney.com/merchant-account/#/](https://www.payumoney.com/merchant-account/#/) . Dit account wordt gebruikt voor PayU om de betalingen te crediteren die door klanten worden gedaan.

## <a name="customer-experience-scenarios"></a>Scenario's voor gebruikers ervaring

### <a name="new-customer-sign-up-scenario"></a>Scenario voor een nieuwe klant aanmelding

- Standaard is de website openbaar beschikbaar en wordt de catalogus van de partner weer gegeven op de start pagina.

- Klanten kunnen nu deel uitmaken van een groot aantal [klant landen](#customer-countries).

- De nadruk ligt op de Europese landen voor gratis handels associatie (EVA), Noord-Amerika, Japan, India, Australië en Nieuw-Zeeland.
  - Deze functie maakt gebruik van de regionale autorisatie ondersteuning in de Partner Center-SDK.

- Klanten kunnen een aanbieding uit de catalogus selecteren om deze aan te schaffen.
  - Ze kunnen hun klant naam, adres en aan het domein gerelateerde informatie toevoegen.

- Klanten worden omgeleid naar de kassa-ervaring van PayPal of PayU (voor India). Klanten kunnen een betaling bieden met behulp van:
  - Hun bestaande PayPal-of PayU-account (voor India)
  - Financierings instrumenten die in hun land worden ondersteund door PayPal of PayU (voor India). Dit kunnen credit cards, betaal kaarten en bank accounts zijn, indien van toepassing.

- Er wordt een Tenant voor klanten gemaakt voor deze klant. Nadat de Tenant volgorde is gemaakt, worden klanten de gebruikers naam, het wacht woord en de abonnements gegevens opgegeven.
  - Klanten kunnen de gebruikers naam en het wacht woord opslaan om aangemeld te blijven voor verdere aankopen.
  - Elk abonnement wordt een jaar gekocht en klanten kunnen binnen 30 dagen vóór de eind datum van het abonnement verlengen.

### <a name="view-prior-purchases-scenario"></a>Scenario voor eerdere aankopen weer geven

- Klant meldt zich aan met de gebruikers naam en het wacht woord van de Tenant van de klant en gaat naar het gedeelte **mijn orders** .

- Klanten kunnen naar de pagina **Mijn bestellingen** navigeren waar ze gekochte abonnementen kunnen bekijken en zo nodig updates moeten aanbrengen.

- Klanten kunnen naar de pagina **Mijn abonnementen** navigeren, waar ze alle abonnementen kunnen bekijken (op basis van de licentie en op basis van gebruik), inclusief die in het partner centrum.

### <a name="add-licenses-to-existing-subscriptions-scenario"></a>Licenties toevoegen aan het scenario bestaande abonnementen

- In de sectie **mijn orders** kunnen klanten meer licenties toevoegen aan bestaande abonnementen. Klanten kunnen op elk gewenst moment tijdens een abonnements jaar meer licenties toevoegen.

- Elke toegevoegde licentie heeft geen invloed op de eind datum van het abonnement. De prijs van het abonnement wordt echter gewijzigd op basis van de datum waarop u de licentie toevoegt en de datum waarop deze in het jaar valt. Prijzen worden dagelijks evenredig berekend tot alleen de resterende dagen van het jaar.

### <a name="add-more-subscriptions-scenario"></a>Meer abonnementen scenario toevoegen

- Klanten kunnen op elk gewenst moment een wille keurig aantal abonnementen kopen via de sectie **abonnementen toevoegen** onder **mijn orders**.

- Een klant kan een abonnement selecteren, een hoeveelheid toevoegen en betalen om de trans actie te volt ooien en het abonnement direct te gebruiken. Als een klant een vooraf goedgekeurde klant is, is het abonnement direct beschikbaar voor gebruik en wordt er een factuur naar de klant verzonden voor betaling.

### <a name="renew-subscription-scenario"></a>Scenario abonnement verlengen

- Een klant kan een abonnement vernieuwen tijdens de laatste 30 dagen vóór de eind datum van het abonnement.

- Dit is alleen beschikbaar in de afgelopen 30 dagen.

- Als dit niet in de afgelopen 30 dagen wordt vernieuwd, wordt het abonnement verwijderd uit de lijst met abonnementen voor deze klant Tenant.

- U kunt de hoeveelheid niet bijwerken tijdens de verlenging.

### <a name="payments-scenario"></a>Betalings scenario

- Als de klant vooraf is goedgekeurd voor trans acties door de beheerder, wordt de betalings ervaring niet weer gegeven voor de bovenstaande scenario's. In plaats daarvan kan de partner de factuur voor betaling verzenden naar de vooraf goedgekeurde klant.

- Voor alle nieuwe aankopen kunt u meer licenties toevoegen, abonnementen toevoegen en vernieuwen. Een klant kan een partner met behulp van deze website betalen via PayPal of PayU (voor India).

- Deze website is geïntegreerd met PayPal of PayU (voor India) en stelt partners in staat om betalingen van hun klanten te accepteren. PayPal of PayU (voor India) verantwoordt deze hoeveelheid in het account van een partner. Het bankrekening beheer van PayPal of PayU (voor India) bevindt zich buiten deze website en wordt respectievelijk op PayPal.com of PayUmoney.com beheerd.

- Dit is afhankelijk van partners die hun Betalings configuratie van PayPal orPayU (voor India) configureren op PayPal.com of PayUmoney.com. Micro soft slaat deze informatie niet op of de werkelijke betalings transacties als gevolg van het gebruik van deze optie.

### <a name="prorated-pricing-scenario"></a>Scenario met profactorieve prijzen

- Op deze website worden prijzen met een evenredige prijs ondersteund wanneer klanten meer licenties toevoegen aan een bestaand abonnement.

- Elk abonnement verloopt na één jaar en kan niet meer worden gewijzigd nadat het abonnement is gekocht.

- De eind datum van het abonnement wordt niet gewijzigd door extra licenties toe te voegen. Klanten worden in rekening gebracht voor het resterende aantal dagen tot de eind datum. Als bijvoorbeeld op de dag één van de abonnements kosten $365 is, en u nog één licentie toevoegt op dag twee, is de prijs voor de nieuwe licentie $364. Als u nog 10 dagen later een licentie toevoegt, wordt de prijs $354.
