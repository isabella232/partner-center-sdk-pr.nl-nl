---
title: Testen en fouten opsporen met integratie sandbox
description: Meer informatie over het gebruik van uw sandbox-account voor integratie met partner centrum (en gerelateerde tokens) om uw code te testen en fouten op te lossen, zodat u niet per ongeluk nieuwe kosten kunt maken.
ms.date: 09/11/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e5b8f6cc2eb239b7a8b8a8722b231f290e768004
ms.sourcegitcommit: a8ebfa97db9e43c6b5ff05bb37ecead6b3565721
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 02/13/2021
ms.locfileid: "100335792"
---
# <a name="test-and-debug-with-your-partner-center-integration-sandbox-to-avoid-paying-unexpected-charges"></a>Testen en fouten opsporen met de sandbox integratie van partner centrum om te voor komen dat er onverwachte kosten worden betaald

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Als u uw code wilt testen, moet u uw account voor integratie sandbox gebruiken in het partner centrum (en de bijbehorende tokens), zodat u niet per ongeluk nieuwe kosten maakt die uw bedrijf verantwoordelijk is voor de betaling. Zie [API-toegang instellen in Partner Center](set-up-api-access-in-partner-center.md)voor meer informatie over deze omgeving van test-in-productie (TiP).

## <a name="integration-sandbox-constraints"></a>Beperkingen voor integratie sandbox

Als u geautomatiseerde compilatie tests uitvoert, testen in productie of hand matige tests uitvoert in de sandbox voor integratie, kunt u de maximum limieten voor de sandbox voor integratie maken. Deze limieten zijn 75 klanten, 5 abonnementen per klant en 25 licenties per abonnement.

- De limiet van 25 licenties betekent dat u geen aanbieding in de sandbox kunt verkrijgen met een minimale licentie vereiste die meer dan 25 licenties overschrijdt. Deze beperking omvat experimenten.


### <a name="azure-plan"></a>Azure-abonnement

Standaard kunnen partners geen Azure-abonnementen inrichten met hun Sandbox-accounts. Partners die dit moeten doen met hun sandbox-account moeten worden toegepast voor toegang. Om toegang te krijgen tot uw Microsoft-account manager of zakelijke contact persoon. Partners die eerder hebben toegepast voor toegang tot het inrichten van Microsoft Azure-abonnementen (MS-AZR-0145P) in hun Sandbox-accounts, hoeven niet opnieuw te worden toegepast voor toegang. Ze krijgen toegang om Azure-abonnementen automatisch in te richten.

Voor partners waarvan de sandbox-accounts zijn goedgekeurd voor het inrichten van Azure-plannen, gelden de volgende limieten:

- Elk sandbox-partner account kan Maxi maal 10 Azure-abonnementen hebben op alle tenants van de klant (ongeacht hoe de plannen worden gedistribueerd tussen de klanten).

- Een directe factuur partner kan Maxi maal één Azure-plan maken per klant Tenant.

- Een indirecte provider kan Maxi maal drie Azure-abonnementen maken per klant Tenant (voor verschillende indirecte wederverkopers die zijn opgegeven als partner-of-record).

- Elk Azure-abonnement kan Maxi maal drie Azure-abonnementen hebben.

- Elk CSP Azure-abonnement onder uw sandbox-account is beperkt tot vier virtuele machine (VM) kernen per Data Center. Daarom kunt u geen VM-Sku's inrichten waarvoor meer dan vier VM-kernen zijn vereist. Bepaalde gespecialiseerde VM-Sku's, zoals GPU-kernen, worden ook uitgesloten.

- Elk sandbox-partner account heeft een bestedings limiet van $2000 (USD) per facturerings cyclus voor alle Azure-abonnementen. Zodra een partner de bestedings limiet bereikt, worden alle Azure-abonnementen tijdelijk uitgeschakeld tot de volgende facturerings cyclus.

### <a name="cloud-solution-provider-csp-azure-subscription-offers"></a>Aanbiedingen van het Azure-abonnement voor de Cloud Solution Provider (CSP)

De aanbiedingen voor de CSP Azure-abonnement zijn niet meer standaard beschikbaar in Sandbox-accounts. Dit zijn onder andere MS-AZR-0146P, MS-AZR-DE-0146P en MS-AZR-USGOV-0146P voor CSP Azure-abonnementen in respectievelijk micro soft Public Cloud, Duitse Cloud en Government Cloud. Partners die toegang nodig hebben tot deze aanbiedingen met hun sandbox-account, moeten een aanvraag indienen voor toegang. Bespreek met uw Microsoft-account manager of zakelijke contact persoon om de toegang toe te passen.

Voor partners waarvan de sandbox-accounts zijn goedgekeurd voor CSP Azure-abonnements aanbiedingen, gelden de volgende limieten:

- U kunt Maxi maal 375 actieve abonnementen hebben (75 klanten x 5 abonnementen per klant). Maar 10 van kan CSP Azure-abonnementen zijn.

- Wanneer een CSP Azure-abonnement $200 van het Azure-gebruik bereikt, worden de bijbehorende resources tijdelijk uitgeschakeld tot de volgende facturerings cyclus. Het wordt nog steeds beschouwd als een actief abonnement en wordt meegeteld bij de limiet van 10 actieve Azure-abonnementen.

- Elk CSP Azure-abonnement onder uw sandbox-account is beperkt tot vier virtuele machine (VM) kernen per Data Center. Daarom kunt u geen VM-Sku's inrichten waarvoor meer dan vier VM-kernen zijn vereist. Bepaalde gespecialiseerde VM-Sku's, zoals GPU-kernen, worden ook uitgesloten.

> [!Important]
> Alle bestaande CSP Azure-abonnementen die zijn ingericht met Sandbox-accounts vóór 1 augustus 2018, worden niet meer ondersteund en worden door micro soft ongedaan gemaakt tussen 16 oktober tot en met 31 oktober 2018. Wanneer de inrichting van de abonnementen ongedaan is gemaakt, kan deze niet opnieuw worden ingeschakeld en zijn de bijbehorende gegevens niet meer toegankelijk. Partners die waardevolle gegevens hebben opgeslagen onder deze abonnementen, moeten een back-up van de gegevens maken vóór 16 oktober 2018.

### <a name="azure-reserved-vm-instance"></a>Voor Azure gereserveerde VM-instantie

Als u [een gereserveerde VM-instantie van Azure aanschaft](purchase-azure-reservations.md) met uw sandbox-account, bent u beperkt tot twee VM-exemplaren per klant. U bent ook beperkt tot het selecteren van alleen de volgende Azure reserved VM-exemplaar product-Sku's:

| Product titel  | Ingangs datum  | SKU-titel                                               | Regio [ArmRegionName] | Instantie sleutel [ArmSkuName] | Duur | Verbruiks meter-id       |
|----------------|-----------------|---------------------------------------------------------|------------------------|--------------|----------|----------------------------|
| B-serie       | 12/1/2017 0:00  | Gereserveerde VM-instantie, Standard_B1s, KR-zuid, 1 jaar    | KoreaSouth             | `Standard_B1s` | `1Year`    | 3f913071-0dd7-4258-8ec4-6fad05bd976d |
| B-serie       | 12/1/2017 0:00  | Gereserveerde VM-instantie, Standard_B1s, VS Oost, 1 jaar     | eastus                 | `Standard_B1s` | `1Year`    | f4d7a5a5-1b67-45ea-b1a0-282fbdd34b05 |
| B-serie       | 12/1/2017 0:00  | Gereserveerde VM-instantie, Standard_B1s, VS West 2, 1 jaar   | westus2                | `Standard_B1s` | `1Year`    | 222e39f5-e99f-4fa3-a323-f46402977888 |
| B-serie       | 12/1/2017 0:00  | Gereserveerde VM-instantie, Standard_B1s, VS Noord-Centraal, 1 jaar    | northcentralus | `Standard_B1s` | `1Year`    | 4e1716fc-4842-43f1-aa96-7c1b1b1395a7 |
| B-serie       | 12/1/2017 0:00  | Gereserveerde VM-instantie, Standard_B1s, CA-oost, 1 jaar     | CanadaEast             | `Standard_B1s` | `1Year`    | ab8a5993-5db7-47c8-b3b1-2e1365b353fb |

### <a name="subscriptions-for-commercial-marketplace-products"></a>Abonnementen voor commerciële Marketplace-Producten

Nadat u in productie [een abonnement hebt gemaakt op een commerciële Marketplace SaaS-producten](create-subscription-azure-marketplace-products.md), moet u een persoonlijke activerings koppeling ophalen van het partner centrum en de site van de uitgever bezoeken om het installatie proces te volt ooien. De facturering van het abonnement wordt pas gestart nadat de installatie is voltooid.

In de CSP-sandbox-omgeving is er geen integratie met Isv's. Als u probeert een activerings koppeling op te halen van het partner centrum, wordt een dummy-koppeling geretourneerd. U kunt deze dummy koppeling niet gebruiken om het installatie proces te volt ooien op de site van de uitgever. Zie [een sandbox-abonnement voor commerciële Marketplace-producten activeren](activate-sandbox-subscription-azure-marketplace-products.md) als u het account voor integratie sandbox wilt gebruiken om de facturering te testen voor abonnementen op de SaaS-producten van de commerciële markt plaats. De facturering van het abonnement wordt gestart nadat de activering is voltooid.

Als u aan het einde van de test uitvoering wilt opschonen, moet u de volgende artikelen gebruiken om ruimte te maken voor de volgende ronde van tests:

- [Een klantaccount verwijderen uit de integratie-sandbox](delete-a-customer-account-from-the-integration-sandbox.md)

- [Het aantal van een abonnement verlagen](change-the-quantity-of-a-subscription.md)

- [Een abonnement opschorten](suspend-a-subscription.md) zodat u het kunt verwijderen.

## <a name="best-practices-for-rest-development"></a>Aanbevolen procedures voor REST-ontwikkeling

- Gebruik een hulp programma voor netwerk tracering zodat u uw aanvraag kunt zien, het antwoord en als er fouten zijn opgetreden in de HTTP-status code in het antwoord. Zie voor meer informatie over het afhandelen van de fout [Partner Center rest-fout codes](error-codes.md).

- Gebruik een nieuwe correlatie-ID voor elke aanroep die u hebt gemaakt in het partner centrum REST API. Deze procedure zorgt voor betere logboek registratie en helpt tijdens het opsporen van fouten. Zie voor meer informatie [Partner Center rest headers](headers.md).

## <a name="troubleshooting-tips-for-common-rest-problems"></a>Tips voor probleemoplossing voor algemene problemen met REST

- Alle eigenschappen van de header controleren, met inbegrip van de URL en API-versie.

- Zorg ervoor dat de eigenschappen worden opgenomen als dat nodig is en correct is opgemaakt.

- Onjuiste matrix opmaak is een veelvoorkomende fout.

- **ETags** zijn tijdelijk en als resultaat, mag niet worden opgeslagen. Wanneer een functie aanroep een **ETags** vereist, gebruikt u de meest recente **ETags** -waarde door de bron opnieuw op te halen. **ETags** -waarden moeten worden opgenomen tussen dubbele aanhalings tekens, zoals een teken reeks:

   ```rest
   If-Match : "eyJpZCI6IjUwMWE4NjBjLTE2OTgtNDQyYi04MDhjLTRiNjEyY2NmMzVmMiIsInZlcnNpb24iOjF9"
   ```
