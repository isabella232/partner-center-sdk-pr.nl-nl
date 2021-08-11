---
title: Analytische gegevens voor Partnercentrum
description: Partner Center Analytics-documentatie voor openbare API's.
ms.date: 06/11/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9028d5e2bdeb2637e35133b2c6dda739e0024ccc2838368a5276b1482af78d7f
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115997835"
---
# <a name="partner-center-analytics---resources"></a>Partnercentrum Analytics - Bronnen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Met de Analytics-API kunt u programmatisch toegang krijgen tot gegevens die worden weergegeven in de gebruikerservaring.

## <a name="prerequisites"></a>Vereisten

- Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md). Deze scenario's ondersteunen alleen verificatie met gebruikersreferenties.

## <a name="csp-program-azure-usage-analytics"></a>CSP-programma: Azure-gebruiksanalyse

In het volgende scenario ziet u hoe u de Analyse-API gebruikt om al uw Partner Center azure-gebruiksanalysegegevens op te halen.

- [Alle gebruiksanalysegegevens van Azure ophalen](get-all-azure-usage-analytics.md)

Dit scenario retourneert uw analysegegevens in een verzameling [Azure-gebruiksresources.](#azure-usage-resource)

## <a name="azure-usage-resource"></a>Azure-gebruiksresource

Vertegenwoordigt alle analytische gegevens voor Azure-gebruik.

| Eigenschap | Type | Description |
|----------|------|-------------|
| CustomerTenantId | tekenreeks | De tenant-id van de klant. |
| customerName | tekenreeks | De naam van de klant. |
| subscriptionId | tekenreeks | De abonnements-id. |
| subscriptionName | tekenreeks | De naam van het abonnement. |
| usageDate | tekenreeks | De gebruiksdatum. |
| resourceLocation | tekenreeks | De locatie van het datacenter, bijvoorbeeld West-Europa. |
| meterCategory | tekenreeks | De metercategorie, bijvoorbeeld gegevensbeheer. |
| meterSubcategory | tekenreeks | De subcategorie van de meter, bijvoorbeeld geografisch redundant. |
| meterUnit | tekenreeks | De metereenheid, zoals gigabytes of uren. |
| reservationOrderId | tekenreeks | De reserveringsorder voor een gereserveerde instantie van een Azure-VM. |
| reservationId | tekenreeks | Gereserveerde instanties onder een specifieke RI-bestelling. |
| serviceType | tekenreeks | Geeft het type virtuele machine aan. Bijvoorbeeld: Standard_E4s_v3. |
| quantity | long | Geeft de getallen aan die in de metereenheid worden gebruikt. |

## <a name="csp-program-indirect-resellers-analytics"></a>CSP-programma: analyse van indirecte resellers

In het volgende scenario ziet u hoe u de Analyse-API gebruikt om al uw Partner Center van indirecte resellers op te halen.

- [Alle analysegegevens van indirecte resellers ophalen](get-all-indirect-resellers-analytics.md)

Dit scenario retourneert uw analysegegevens in een verzameling [indirecte resellersresources.](#indirect-resellers-resource)

## <a name="indirect-resellers-resource"></a>Resource voor indirecte resellers

Vertegenwoordigt alle analytische gegevens voor indirecte resellers.

| Eigenschap | Type | Description |
|----------|------|-------------|
| partnerTenantId | tekenreeks | De tenant-id van de partner waarvoor u gegevens van indirecte resellers wilt ophalen. |
| id | tekenreeks | Indirecte reseller-id. |
| naam | tekenreeks | De naam van de partner waarvoor u gegevens van indirecte resellers wilt ophalen. |
| markt | tekenreeks | De markt van de partner waarvoor u gegevens van indirecte resellers wilt ophalen. |
| firstSubscriptionCreationDate | tekenreeks in UTC-datum/tijd-indeling | De aanmaakdatum van het eerste abonnement op basis waarvan u gegevens van indirecte resellers wilt ophalen. |
| latestSubscriptionCreationDate | tekenreeks in UTC-datum/tijd-indeling | De aanmaakdatum van het meest recente abonnement. |
| firstSubscriptionEndDate | tekenreeks in UTC-datum/tijd-indeling | De eerste keer dat een abonnement is beëindigd. |
| latestSubscriptionEndDate | tekenreeks in UTC-datum/tijd-indeling | De laatste datum waarop een abonnement is beëindigd. |
| firstSubscriptionSuspendedDate | tekenreeks in UTC-datum/tijd-indeling | De eerste keer dat een abonnement is opgeschort. |
| latestSubscriptionSuspendedDate | tekenreeks in UTC-datum/tijd-indeling | De laatste datum waarop een abonnement is opgeschort. |
| firstSubscriptionDeprovisionedDate | tekenreeks in UTC-datum/tijd-indeling | De eerste keer dat deprovisioning van een abonnement is verwijderd. |
| latestSubscriptionDeprovisionedDate | tekenreeks in UTC-datum/tijd-indeling | De laatste datum waarop een abonnement is verwijderd. |
| subscriptionCount | double | Aantal abonnementen voor alle toegevoegde waarde resellers |
| licenseCount | double | Aantal licenties voor alle toegevoegde waarde resellers |
| indirectResellerCount | double | Aantal indirecte resellers |

## <a name="csp-program-subscription-analytics"></a>CSP-programma: abonnementsanalyse

In de volgende scenario's ziet u hoe u de Analyse-API gebruikt om al uw Partner Center-abonnementsanalysegegevens op te halen, deze te filteren met een zoekquery of deze te groeperen op datums of termen.

- [Alle analysegegevens van abonnementen ophalen](get-all-subscription-analytics.md)
- [Analysegegevens van abonnementen die is gefilterd met een zoekquery ophalen](get-subscription-analytics-by-search-query.md)
- [Analysegegevens van abonnementen die is gegroepeerd op datum of zoekwoord](get-subscription-analytics-grouped-by-dates-or-terms.md)

Al deze scenario's retourneren uw analysegegevens in een verzameling [abonnementsresources.](#subscription-resource)

## <a name="subscription-resource"></a>Abonnementsresource

Vertegenwoordigt alle analytische gegevens voor een abonnement.

|         Eigenschap          |              Type              |                                                                      Description                                                                       |
|---------------------------|--------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
|     customerTenantId      |             tekenreeks             |                                              Een tekenreeks in GUID-indeling die de tenant van de klant identificeert.                                              |
|       customerName        |             tekenreeks             |                                                               De naam van de klant.                                                                |
|      customerMarket       |             tekenreeks             |                                                 Het land/de regio waarin de klant zaken doet.                                                 |
|            id             |             tekenreeks             |                                                              De abonnements-id.                                                              |
|          status           |             tekenreeks             |                                          De abonnementsstatus: 'ACTIEF', 'TIJDELIJK' of 'DEPROVISIONED'.                                           |
|        Productnaam        |             tekenreeks             |                                                                De naam van het product.                                                                |
|     subscriptionType      |             tekenreeks             |       Het abonnementstype. **Opmerking:** dit veld is casegevoelig. Ondersteunde waarden zijn: 'Office', 'Azure', 'Microsoft365', 'Dynamics', 'EMS'.       |
|     autoRenewEnabled      |            booleaans             |                                         Een waarde die aangeeft of het abonnement automatisch wordt verlengd.                                          |
|         partnerId         |             tekenreeks             | De Microsoft Partner Network(MPN)-id. Voor een directe reseller is deze parameter de MPN-id van de partner. Voor een indirecte reseller is deze parameter de MPN-id van de indirecte reseller. |
|       Friendlyname        |             tekenreeks             |                                                             De naam van het abonnement.                                                              |
|        partnerName        |             tekenreeks             |                                              Naam van de partner voor wie het abonnement is gekocht                                               |
|       providerName        |             tekenreeks             |            Wanneer de abonnementstransactie voor de indirecte reseller is, is de providernaam de indirecte provider die het abonnement heeft gekocht.             |
|    effectiveStartDate     | tekenreeks in UTC-datum/tijd-indeling |                                                           De datum waarop het abonnement wordt gestart.                                                            |
|     commitmentEndDate     | tekenreeks in UTC-datum/tijd-indeling |                                                            De datum waarop het abonnement eindigt.                                                             |
|    currentStateEndDate    | tekenreeks in UTC-datum/tijd-indeling |                                           De datum waarop de huidige status van het abonnement wordt gewijzigd.                                            |
| trialToPaidConversionDate | tekenreeks in UTC-datum/tijd-indeling |                                 De datum waarop het abonnement wordt omgezet van proefversie naar betaald. De standaardwaarde is null.                                 |
|      trialStartDate       | tekenreeks in UTC-datum/tijd-indeling |                                De datum waarop de proefperiode voor het abonnement is gestart. De standaardwaarde is null.                                 |
|       trialEndDate        | tekenreeks in UTC-datum/tijd-indeling |                                  De datum waarop de proefperiode voor het abonnement eindigt. De standaardwaarde is null.                                  |
|       lastUsageDate       | tekenreeks in UTC-datum/tijd-indeling |                                        De datum waarop het abonnement voor het laatst is gebruikt. De standaardwaarde is null.                                        |
|     deprovisionedDate     | tekenreeks in UTC-datum/tijd-indeling |                                      De datum waarop het abonnement is verwijderd. De standaardwaarde is null.                                      |
|      lastRenewalDate      | tekenreeks in UTC-datum/tijd-indeling |                                       De datum waarop het abonnement voor het laatst is vernieuwd. De standaardwaarde is null.                                       |
|       licenseCount        |             getal             |                                                             Het totale aantal licenties.                                                              |
|     subscriptionCount     |             getal             |                        Het aantal abonnementen. Opmerking: deze waarde wordt alleen weergegeven in het antwoord van een aggregatiequery.                         |

## <a name="search-analytics"></a>Zoekanalyse

> [!NOTE]
> Lidmaatschap van het CSP-programma is niet vereist om zoekanalyses op te halen.

In het volgende scenario ziet u hoe u de Analyse-API gebruikt om al uw Partner Center op te halen.

- [Alle analysegegevens van zoeken ophalen](get-all-search-analytics.md)

Dit scenario retourneert uw analysegegevens in een verzameling [zoekresources.](#search-resource)

## <a name="search-resource"></a>Resource zoeken

Vertegenwoordigt alle analytische gegevens voor een zoekopdracht.

| Eigenschap | Type | Description |
|----------|------|-------------|
| companyName | tekenreeks | De naam van het factureringsbedrijf. |
| contactButtonClicked | Booleaans | Geeft aan of op de knop Contact is geklikt. |
| keywordCountry | tekenreeks | Het land dat is opgegeven in de zoekopdracht. |
| detailsWeergave | Booleaans | Geeft aan of zoekdetails zijn bekeken. |
| keywordIn keywordIn keywordFocus | tekenreeks | De branche waar moet worden gezocht, bijvoorbeeld in de gezondheidszorg. |
| mpnId | tekenreeks | De Microsoft Partner Network(MPN)-id. Voor een directe reseller is deze parameter de MPN-id van de partner. Voor een indirecte reseller is deze parameter de MPN-id van de indirecte reseller. |
| partnerMarket | tekenreeks | Land waar de partner zaken doet. |
| keywordProduct | tekenreeks | Het product dat is opgegeven in de zoekopdracht. |
| referralSubmitted | Booleaans | Geeft aan of er een verwijzing is ingediend. |
| searchDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de zoekquery heeft plaatsgevonden. |
| keywordSearchText | tekenreeks | De tekst die is opgegeven in de zoekopdracht. |
| searchResultPageViews | long | Het aantal keren dat de partner in het zoekresultaat is gekomen. Onderdeel van een antwoord alleen bij aggregatie.
| contactClicks | long | Het aantal keren dat op de knop Contact is geklikt. Onderdeel van een antwoord alleen bij aggregatie.
| referralCount | long | Het aantal verwijzingen dat is gegenereerd op basis van de zoekopdracht. Onderdeel van een antwoord alleen bij aggregatie.
| profileViews | long | Het aantal keren dat het partnerprofiel is bekeken. Onderdeel van een antwoord alleen bij aggregatie.

## <a name="referrals-analytics"></a>Verwijzingsanalyse

> [!NOTE]
> Lidmaatschap van het CSP-programma is niet vereist om verwijzingenanalyses op te halen.

In het volgende scenario ziet u hoe u de Analyse-API gebruikt om al uw Partner Center analytics-informatie over verwijzingen op te halen.

- [Alle analysegegevens van verwijzingen ophalen](get-all-referrals-analytics.md)

Dit scenario retourneert uw analysegegevens in een verzameling [verwijzingenresources.](#referrals-resource)

> [!NOTE]
> Verwijzingsanalyses zijn niet beschikbaar voor de Partner Center beheerd door 21Vianet.

## <a name="referrals-resource"></a>Verwijzingsresource

Vertegenwoordigt alle analytische gegevens voor een verwijzing.

| Eigenschap | Type | Beschrijving |
|----------|------|-------------|
| id | tekenreeks | De tenant-id van de klant.  |
| status | tekenreeks | Geeft aan of de verwijzing naar een klant heeft geleid.  |
| customerMarket | tekenreeks | Het land/de regio waarin de klant zaken doet. |
| customerName | tekenreeks | De naam van de klant. |
| customerOrgSize | tekenreeks | Een bereik dat het aantal werknemers in de organisatie van de klant aangeeft. Bijvoorbeeld 10to50employees. |
| acceptedDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de verwijzing is geaccepteerd. |
| acknowledgedDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de verwijzing is bevestigd. |
| archivedDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de verwijzing is gearchiveerd. |
| declinedDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de verwijzing is afgewezen. |
| expiredDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de verwijzing is verlopen. |
| lostDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de verwijzing is verloren gegaan. |
| missedDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de verwijzing is gemist. |
| createdDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de verwijzing is gemaakt. |
| skippedDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de verwijzing is overgeslagen. |
| wonDate | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de verwijzing is gewonnen. |
| partnerMarket | tekenreeks |  Het land/de regio waarin de partner zaken doet. |
