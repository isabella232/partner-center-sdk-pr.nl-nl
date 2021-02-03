---
title: Analytische gegevens voor Partnercentrum
description: Documentatie voor de open bare API voor Partner Center Analytics.
ms.date: 06/11/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4b14ee929f3020079f409be8817e077673d3219f
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767210"
---
# <a name="partner-center-analytics---resources"></a>Partnercentrum Analytics - Bronnen

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Met de analyse-API kunt u programmatisch toegang krijgen tot gegevens die in de gebruikers ervaring worden weer gegeven.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md). Deze scenario's ondersteunen alleen verificatie met gebruikers referenties.

## <a name="csp-program-azure-usage-analytics"></a>CSP-programma: Azure Usage Analytics

In het volgende scenario ziet u hoe u de analyse-API gebruikt om alle gegevens van het Azure-gebruik van uw partner centrum op te halen.

- [Alle gebruiksanalysegegevens van Azure ophalen](get-all-azure-usage-analytics.md)

Dit scenario retourneert uw analyse-informatie in een verzameling [Azure-gebruiks](#azure-usage-resource) resources.

## <a name="azure-usage-resource"></a>Azure-gebruiks resource

Vertegenwoordigt alle analytische gegevens voor Azure-gebruik.

| Eigenschap | Type | Description |
|----------|------|-------------|
| CustomerTenantId | tekenreeks | De Tenant-id van de klant. |
| customerName | tekenreeks | De naam van de klant. |
| subscriptionId | tekenreeks | De abonnements-id. |
| subscriptionName | tekenreeks | De naam van het abonnement. |
| usageDate | tekenreeks | De gebruiks datum. |
| resourceLocation | tekenreeks | De locatie van het Data Center, West-Europa, bijvoorbeeld. |
| meterCategory | tekenreeks | De meter categorie, gegevens beheer, bijvoorbeeld. |
| meterSubcategory | tekenreeks | De subcategorie van de meter, bijvoorbeeld geo redundant. |
| meterUnit | tekenreeks | De eenheid van de meter, zoals gigabytes of uren. |
| reservationOrderId | tekenreeks | De reserverings volgorde voor een gereserveerde Azure VM-instantie. |
| reservationId | tekenreeks | Gereserveerde instanties onder een specifieke RI-volg orde. |
| Service | tekenreeks | Hiermee wordt het type virtuele machine aangegeven. Bijvoorbeeld Standard_E4s_v3. |
| quantity | long | Hiermee worden de getallen aangegeven die in de meter eenheid worden gebruikt. |

## <a name="csp-program-indirect-resellers-analytics"></a>CSP-programma: analyse van indirecte wederverkopers

In het volgende scenario ziet u hoe u de analyse-API gebruikt om alle Analytics-gegevens van uw partner centrum indirecte wederverkopers op te halen.

- [Alle analysegegevens van indirecte resellers ophalen](get-all-indirect-resellers-analytics.md)

Dit scenario retourneert uw analyse-informatie in een verzameling van [indirecte wederverkopers](#indirect-resellers-resource) -resources.

## <a name="indirect-resellers-resource"></a>Resource voor indirecte wederverkopers

Vertegenwoordigt alle analytische gegevens voor indirecte wederverkopers.

| Eigenschap | Type | Description |
|----------|------|-------------|
| partnerTenantId | tekenreeks | De Tenant-ID van de partner waarvoor u gegevens van indirecte wederverkopers wilt ophalen. |
| id | tekenreeks | ID van de indirecte wederverkoper. |
| naam | tekenreeks | De naam van de partner waarvoor u gegevens van indirecte wederverkopers wilt ophalen. |
| markt | tekenreeks | De markt van de partner waarvoor u gegevens van indirecte wederverkopers wilt ophalen. |
| firstSubscriptionCreationDate | teken reeks in UTC-datum tijd notatie | De aanmaak datum van het eerste abonnement op basis waarvan u de gegevens van indirecte wederverkopers wilt ophalen. |
| latestSubscriptionCreationDate | teken reeks in UTC-datum tijd notatie | De aanmaak datum van het laatste abonnement. |
| firstSubscriptionEndDate | teken reeks in UTC-datum tijd notatie | De eerste keer dat een abonnement is beëindigd. |
| latestSubscriptionEndDate | teken reeks in UTC-datum tijd notatie | De laatste datum waarop een abonnement is beëindigd. |
| firstSubscriptionSuspendedDate | teken reeks in UTC-datum tijd notatie | De eerste keer dat een abonnement is onderbroken. |
| latestSubscriptionSuspendedDate | teken reeks in UTC-datum tijd notatie | De laatste datum waarop een abonnement is onderbroken. |
| firstSubscriptionDeprovisionedDate | teken reeks in UTC-datum tijd notatie | De inrichting van het abonnement is voor het eerst ongedaan gemaakt. |
| latestSubscriptionDeprovisionedDate | teken reeks in UTC-datum tijd notatie | De laatste datum waarop een abonnement is ongedaan gemaakt. |
| subscriptionCount | double | Aantal abonnementen voor alle resellers met toegevoegde waarde |
| licenseCount | double | Aantal licenties voor alle wederverkopers met toegevoegde waarde |
| indirectResellerCount | double | Aantal indirecte wederverkopers |

## <a name="csp-program-subscription-analytics"></a>CSP-programma: abonnements analyse

In de volgende scenario's ziet u hoe u de analyse-API kunt gebruiken om al uw partner centrum-informatie over het abonnement op te halen, deze te filteren met een zoek opdracht of deze te groeperen op datum of voor waarden.

- [Alle analysegegevens van abonnementen ophalen](get-all-subscription-analytics.md)
- [Analysegegevens van abonnementen die is gefilterd met een zoekquery ophalen](get-subscription-analytics-by-search-query.md)
- [Analysegegevens van abonnementen die is gegroepeerd op datum of zoekwoord](get-subscription-analytics-grouped-by-dates-or-terms.md)

Al deze scenario's geven uw analyse-informatie weer in een verzameling [abonnements](#subscription-resource) resources.

## <a name="subscription-resource"></a>Abonnements resource

Vertegenwoordigt alle analytische gegevens voor een abonnement.

|         Eigenschap          |              Type              |                                                                      Description                                                                       |
|---------------------------|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|     customerTenantId      |             tekenreeks             |                                              Een teken reeks met een GUID-indeling die de Tenant van de klant identificeert.                                              |
|       customerName        |             tekenreeks             |                                                               De naam van de klant.                                                                |
|      customerMarket       |             tekenreeks             |                                                 Het land/de regio waarin de klant zaken doet.                                                 |
|            id             |             tekenreeks             |                                                              De abonnements-id.                                                              |
|          status           |             tekenreeks             |                                          De status van het abonnement: actief, OPGESCHORT of oningericht.                                           |
|        Product        |             tekenreeks             |                                                                De naam van het product.                                                                |
|     subscriptionType      |             tekenreeks             |       Het type abonnement. **Opmerking**: dit veld is hoofdletter gevoelig. Ondersteunde waarden zijn: ' Office ', ' Azure ', ' Microsoft365 ', ' Dynamics ', ' EMS '.       |
|     autoRenewEnabled      |            booleaans             |                                         Een waarde die aangeeft of het abonnement automatisch wordt vernieuwd.                                          |
|         Partner         |             tekenreeks             | De MPN-ID. Voor een rechtstreekse wederverkoper is deze para meter de MPN-ID van de partner. Voor een indirecte wederverkoper is deze para meter de MPN-ID van de indirecte wederverkoper. |
|       friendlyName        |             tekenreeks             |                                                             De naam van het abonnement.                                                              |
|        partnerName        |             tekenreeks             |                                              De naam van de partner voor wie het abonnement is aangeschaft                                               |
|       providerName        |             tekenreeks             |            Wanneer abonnements transactie voor de indirecte wederverkoper is, is de naam van de provider de indirecte provider die het abonnement heeft gekocht.             |
|    effectiveStartDate     | teken reeks in UTC-datum tijd notatie |                                                           De datum waarop het abonnement wordt gestart.                                                            |
|     commitmentEndDate     | teken reeks in UTC-datum tijd notatie |                                                            De datum waarop het abonnement eindigt.                                                             |
|    currentStateEndDate    | teken reeks in UTC-datum tijd notatie |                                           De datum waarop de huidige status van het abonnement wordt gewijzigd.                                            |
| trialToPaidConversionDate | teken reeks in UTC-datum tijd notatie |                                 De datum waarop het abonnement wordt geconverteerd van een proef versie naar betaald. De standaardwaarde is null.                                 |
|      trialStartDate       | teken reeks in UTC-datum tijd notatie |                                De datum waarop de proef periode voor het abonnement is gestart. De standaardwaarde is null.                                 |
|       trialEndDate        | teken reeks in UTC-datum tijd notatie |                                  De datum waarop de proef periode voor het abonnement eindigt. De standaardwaarde is null.                                  |
|       lastUsageDate       | teken reeks in UTC-datum tijd notatie |                                        De datum waarop het abonnement voor het laatst is gebruikt. De standaardwaarde is null.                                        |
|     deprovisionedDate     | teken reeks in UTC-datum tijd notatie |                                      De datum waarop het abonnement is ongedaan gemaakt. De standaardwaarde is null.                                      |
|      lastRenewalDate      | teken reeks in UTC-datum tijd notatie |                                       De datum waarop het abonnement voor het laatst is vernieuwd de standaard waarde is null.                                       |
|       licenseCount        |             getal             |                                                             Het totale aantal licenties.                                                              |
|     subscriptionCount     |             getal             |                        Het aantal abonnementen. Opmerking: deze waarde wordt alleen weer gegeven in het antwoord van een aggregatie query.                         |

## <a name="search-analytics"></a>Analyse zoeken

> [!NOTE]
> Er is geen lidmaatschap van het CSP-programma vereist om Zoek analyses op te halen.

In het volgende scenario ziet u hoe u de analyse-API kunt gebruiken om al uw partner centrum-Zoek analyse gegevens op te halen.

- [Alle analysegegevens van zoeken ophalen](get-all-search-analytics.md)

Dit scenario retourneert uw analyse-informatie in een verzameling [Zoek](#search-resource) bronnen.

## <a name="search-resource"></a>Resource zoeken

Hiermee worden alle analytische gegevens voor een zoek opdracht aangeduid.

| Eigenschap | Type | Description |
|----------|------|-------------|
| companyName | tekenreeks | De naam van het facturerings bedrijf. |
| contactButtonClicked | Booleaans | Hiermee wordt aangegeven of op de knop contact wordt geklikt. |
| keywordCountry | tekenreeks | Het land dat is opgegeven in de zoek opdracht. |
| detailsViewed | Booleaans | Hiermee wordt aangegeven of Zoek gegevens zijn weer gegeven. |
| keywordIndustryFocus | tekenreeks | De branche waarin u wilt zoeken, bijvoorbeeld gezondheids zorg. |
| mpnId | tekenreeks | De ID van de Microsoft Partner Network (MPN). Voor een rechtstreekse wederverkoper is deze para meter de MPN-ID van de partner. Voor een indirecte wederverkoper is deze para meter de MPN-ID van de indirecte wederverkoper. |
| partnerMarket | tekenreeks | De locatie waar de partner zaken doet. |
| keywordProduct | tekenreeks | Het product dat is opgegeven in de zoek opdracht. |
| referralSubmitted | Booleaans | Hiermee wordt aangegeven of een referral is verzonden. |
| searchDate | teken reeks in UTC-datum tijd notatie | De datum waarop de zoek query heeft plaatsgevonden. |
| keywordSearchText | tekenreeks | De tekst die in de zoek opdracht is opgegeven. |
| searchResultPageViews | long | Het aantal keren dat de partner bij het Zoek resultaat kwam. Onderdeel van een antwoord alleen op aggregatie.
| contactClicks | long | Aantal keren dat op de knop contact persoon is geklikt. Onderdeel van een antwoord alleen op aggregatie.
| referralCount | long | Het aantal verwijzingen dat is gegenereerd op basis van de zoek opdracht. Onderdeel van een antwoord alleen op aggregatie.
| profileViews | long | Het aantal keren dat het Partner profiel is bekeken. Onderdeel van een antwoord alleen op aggregatie.

## <a name="referrals-analytics"></a>Analyse van verwijzingen

> [!NOTE]
> Er is geen lidmaatschap van het CSP-programma vereist voor het ophalen van verwijzings analyses.

In het volgende scenario ziet u hoe u de analyse-API kunt gebruiken om al uw partner Center-verwijzingen Analytics-gegevens op te halen.

- [Alle analysegegevens van verwijzingen ophalen](get-all-referrals-analytics.md)

Dit scenario retourneert uw analyse-informatie in een verzameling [verwijzingen](#referrals-resource) -resources.

> [!NOTE]
> Verwijzings analyses zijn niet beschikbaar voor het partner centrum dat wordt beheerd door 21Vianet.

## <a name="referrals-resource"></a>Resource met verwijzingen

Vertegenwoordigt alle analytische gegevens voor een verwijzing.

| Eigenschap | Type | Beschrijving |
|----------|------|-------------|
| id | tekenreeks | De Tenant-id van de klant.  |
| status | tekenreeks | Hiermee wordt aangegeven of de verwijzing naar een klant heeft geleid.  |
| customerMarket | tekenreeks | Het land/de regio waarin de klant zaken doet. |
| customerName | tekenreeks | De naam van de klant. |
| customerOrgSize | tekenreeks | Een bereik dat het aantal werk nemers in de organisatie van de klant aangeeft. Bijvoorbeeld ' 10to50employees '. |
| acceptedDate | teken reeks in UTC-datum tijd notatie | De datum waarop de verwijzing is geaccepteerd. |
| acknowledgedDate | teken reeks in UTC-datum tijd notatie | De datum waarop de verwijzing is bevestigd. |
| archivedDate | teken reeks in UTC-datum tijd notatie | De datum waarop de verwijzing is gearchiveerd. |
| declinedDate | teken reeks in UTC-datum tijd notatie | De datum waarop de verwijzing is afgewezen. |
| expiredDate | teken reeks in UTC-datum tijd notatie | De datum waarop de verwijzing is verlopen. |
| lostDate | teken reeks in UTC-datum tijd notatie | De datum waarop de verwijzing is verbroken. |
| missedDate | teken reeks in UTC-datum tijd notatie | De datum waarop de verwijzing is gemist. |
| createdDate | teken reeks in UTC-datum tijd notatie | De datum waarop de verwijzing is gemaakt. |
| skippedDate | teken reeks in UTC-datum tijd notatie | De datum waarop de verwijzing is overgeslagen. |
| wonDate | teken reeks in UTC-datum tijd notatie | De datum waarop de Referral is binnengehaald. |
| partnerMarket | tekenreeks |  Het land of de regio waar de partner zaken mee doet. |
