---
title: Testen en fouten opsporen met integratie-sandbox
description: Meer informatie over het gebruik van Partner Center sandbox-account voor integratie (en gerelateerde tokens) om uw code te testen en fouten op te sporen, zodat er niet per ongeluk nieuwe kosten in rekening worden gebracht.
ms.date: 09/11/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 7a9d7755cd9f493f44f9a7bbf613e0f80cf7b4ac
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530103"
---
# <a name="test-and-debug-with-your-partner-center-integration-sandbox-to-avoid-paying-unexpected-charges"></a>Test en foutopsporing met uw Partner Center-integratie-sandbox om te voorkomen dat u onverwachte kosten betaalt

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Als u uw code wilt testen, moet u uw sandbox-account voor integratie gebruiken in Partner Center (en de bijbehorende tokens), zodat er niet per ongeluk nieuwe kosten in rekening worden gebracht die uw bedrijf moet betalen. Zie API-toegang instellen in Partner Center voor meer informatie over deze [Test-In-Production-omgeving (TiP).](set-up-api-access-in-partner-center.md)

## <a name="integration-sandbox-constraints"></a>Beperkingen voor de integratie-sandbox

Als u geautomatiseerde buildverificatietests hebt uitgevoerd, tests in productie wilt uitvoeren of handmatige tests in de integratie-sandbox wilt uitvoeren, kunt u de maximumlimieten voor de integratie-sandbox bereiken. Deze limieten zijn 75 klanten, 5 abonnementen per klant en 25 licenties per abonnement.

De limiet van 25 licenties betekent dat u geen aanbieding kunt verkrijgen in de sandbox met een minimale licentievereiste die groter is dan 25 licenties. Deze beperking geldt ook voor proefversies.

Er zijn verschillende factuur- en afstemmingsbestanden beschikbaar in de Sandbox-omgevingen, maar deze zijn niet allemaal beschikbaar op verouderde of moderne platforms. Controleer de onderstaande tabel voor meer informatie.

| **Bestanden**                    | **Beschikbaar in verouderd** | **Beschikbaar in Modern** |
| ---------------------------- | ------------------------ | ------------------------ |
| Factuur (PDF)                  | Nee                       | Ja                      |
| Factuurafstemmingsbestand | Nee                       | Ja                      |
| Factuurschattingsbestand       | Nee                       | Ja                      |
| Dagelijks gefactureerd gebruiksbestand     | Nee                       | Ja                      |
| Dagelijks bestand met niet-gebild gebruik   | Nee                       | Ja                      |


### <a name="azure-plan"></a>Azure-abonnement

Standaard kunnen partners geen Azure-abonnementen inrichten met behulp van hun sandbox-accounts. Partners die dit willen doen met hun sandbox-account, moeten toegang aanvragen. Als u toegang wilt aanvragen, neem dan contact op met Microsoft-account manager of zakelijke contactpersoon. Partners die eerder toegang hebben aangevraagd voor het inrichten van Microsoft Azure-abonnementen (MS-AZR-0145P) in hun sandbox-accounts, hoeven geen toegang opnieuw aan te melden. Ze krijgen toegang tot het automatisch inrichten van Azure-abonnementen.

Voor partners waarvan de sandbox-accounts zijn goedgekeurd voor het inrichten van Azure-plannen, gelden de volgende limieten:

- Elk sandbox-partneraccount kan maximaal 10 Azure-abonnementen hebben voor alle tenants van klanten (ongeacht hoe de plannen worden verdeeld over de klanten).

- Een directe factuurpartner kan maximaal één Azure-plan per klant-tenant maken.

- Een indirecte provider kan maximaal drie Azure-abonnementen per klantten tenant maken (voor verschillende indirecte resellers die zijn opgegeven als de Partner-of-Record).

- Elk Azure-plan kan maximaal drie Azure-abonnementen hebben.

- Elk CSP Azure-abonnement onder uw sandbox-account is beperkt tot vier kernen van virtuele machines (VM's) per datacenter. Daarom kunt u geen VM-SKU's inrichten waarvoor meer dan vier VM-kernen zijn vereist. Bepaalde gespecialiseerde VM-SKU's, zoals GPU-kernen, worden ook uitgesloten.

- Elk sandbox-partneraccount heeft een bestedingslimiet van $ 2000 (USD) per factureringscyclus voor alle Azure-abonnementen. Zodra een partner de uitgavenlimiet heeft bereikt, worden alle Azure-abonnementen tijdelijk uitgeschakeld tot de volgende factureringscyclus.

### <a name="cloud-solution-provider-csp-azure-subscription-offers"></a>azure Cloud Solution Provider abonnementaanbiedingen (CSP)

Aanbiedingen voor CSP Azure-abonnementen zijn niet meer standaard beschikbaar voor sandbox-accounts. Dit zijn respectievelijk MS-AZR-0146P, MS-AZR-DE-0146P en MS-AZR-USGOV-0146P voor CSP Azure-abonnementen in microsoft public cloud, Duitse cloud en government cloud. Partners die toegang tot deze aanbiedingen nodig hebben met hun sandbox-account, moeten toegang aanvragen. Als u toegang wilt aanvragen, kunt u contact opnemen met Microsoft-account manager of zakelijke contactpersoon.

Voor partners waarvan de sandbox-accounts zijn goedgekeurd voor aanbiedingen van CSP Azure-abonnementen, gelden de volgende limieten:

- U kunt maximaal 375 actieve abonnementen hebben (75 klanten x 5 abonnementen per klant). Slechts 10 van deze abonnementen kunnen echter CSP Azure-abonnementen zijn.

- Wanneer een CSP Azure-abonnement $ 200 aan Azure-gebruik bereikt, worden de resources tijdelijk uitgeschakeld tot de volgende factureringscyclus. Het wordt nog steeds beschouwd als een actief abonnement en wordt meegetelde voor de limiet van 10 actieve Azure-abonnementen.

- Elk CSP Azure-abonnement onder uw sandbox-account is beperkt tot vier kernen van virtuele machines (VM's) per datacenter. Daarom kunt u geen VM-SKU's inrichten waarvoor meer dan vier VM-kernen zijn vereist. Bepaalde gespecialiseerde VM-SKU's, zoals GPU-kernen, worden ook uitgesloten.

> [!Important]
> Alle bestaande CSP Azure-abonnementen die zijn ingericht met sandbox-accounts vóór 1 augustus 2018 worden niet meer ondersteund en worden van 16 oktober tot 31 oktober 2018 door Microsoft in de inrichting verwijderd. Nadat de abonnementen zijn verwijderd, kunnen ze niet opnieuw worden ingeschakeld en zijn gekoppelde gegevens niet meer toegankelijk. Partners die waardevolle gegevens hebben opgeslagen onder deze abonnementen, moeten vóór 16 oktober 2018 een back-up van de gegevens maken.

### <a name="azure-reserved-vm-instance"></a>Gereserveerde VM-instantie van Azure

Als u een [gereserveerde VM-instantie](purchase-azure-reservations.md) van Azure koopt met uw sandbox-account, bent u beperkt tot twee VM-exemplaren per klant. U kunt ook alleen selecteren uit de volgende product-SKU's voor gereserveerde Azure-VM-instanties:

| Producttitel  | Ingangsdatum  | SKU-titel                                               | Regio [ArmRegionName] | Exemplaarsleutel [ArmSkuName] | Duur | Verbruiksmeter-id       |
|----------------|-----------------|---------------------------------------------------------|------------------------|--------------|----------|----------------------------|
| B-serie       | 12/1/2017 0:00  | Gereserveerde VM-instantie, Standard_B1s, KR - zuid, 1 jaar    | KoreaSouth             | `Standard_B1s` | `1Year`    | 3f913071-0dd7-4258-8ec4-6fad05bd976d |
| B-serie       | 12/1/2017 0:00  | Gereserveerde VM-instantie, Standard_B1s, US - oost, 1 jaar     | eastus                 | `Standard_B1s` | `1Year`    | f4d7a5a5-1b67-45ea-b1a0-282fbdd34b05 |
| B-serie       | 12/1/2017 0:00  | Gereserveerde VM-instantie, Standard_B1s, US - west 2, 1 jaar   | westus2                | `Standard_B1s` | `1Year`    | 222e39f5-e99f-4fa3-a323-f464029778888 |
| B-serie       | 12/1/2017 0:00  | Gereserveerde VM-instantie, Standard_B1s, US - noord-centraal, 1 jaar    | northcentralus | `Standard_B1s` | `1Year`    | 4e1716fc-4842-43f1-aa96-7c1b1b1395a7 |
| B-serie       | 12/1/2017 0:00  | Gereserveerde VM-instantie, Standard_B1s, CA - oost, 1 jaar     | Canada -ast             | `Standard_B1s` | `1Year`    | ab8a5993-5db7-47c8-b3b1-2e1365b353fb |

### <a name="subscriptions-for-commercial-marketplace-products"></a>Abonnementen voor commerciële marketplace-producten

Nadat u in productie een abonnement op [Commerciële Marketplace SaaS-producten](create-subscription-azure-marketplace-products.md)hebt gemaakt, moet u een gepersonaliseerde activeringskoppeling ophalen van Partner Center en naar de site van de uitgever gaan om het installatieproces te voltooien. Abonnementsfacturering begint pas nadat de installatie is voltooid.

In de CSP-sandboxomgeving is er geen integratie met ISV's. Als u een activeringskoppeling probeert op te halen Partner Center, wordt er een dummykoppeling geretourneerd. U kunt deze dummykoppeling niet gebruiken om het installatieproces op de site van de uitgever te voltooien. Zie Activate [a sandbox subscription for commercial marketplace products](activate-sandbox-subscription-azure-marketplace-products.md) (Een sandbox-abonnement activeren voor commerciële marketplace-producten) als u het sandboxaccount voor integratie wilt gebruiken om de facturering voor abonnementen op SaaS-producten op de commerciële marketplace te testen. Abonnementsfacturering begint na een geslaagde activering.

Zie de volgende artikelen om op te schonen aan het einde van de test, zodat er ruimte is voor de volgende testronde:

- [Een klantaccount verwijderen uit de integratie-sandbox](delete-a-customer-account-from-the-integration-sandbox.md)

- [De hoeveelheid van een abonnement verlagen](change-the-quantity-of-a-subscription.md)

- [Een abonnement opschorten](suspend-a-subscription.md) zodat u het kunt verwijderen.

## <a name="best-practices-for-rest-development"></a>Best practices voor REST-ontwikkeling

- Gebruik een hulpprogramma voor netwerk traceer, zodat u uw aanvraag en het antwoord kunt zien en of er fouten zijn in de HTTP-statuscode in het antwoord. Zie REST-foutcodes voor [meer Partner Center over foutafhandeling.](error-codes.md)

- Gebruik een nieuwe correlatie-id voor elke aanroep naar de Partner Center REST API. Deze praktijk zorgt voor betere logboekregistratie en helpt bij het debuggen. Zie REST-headers [Partner Center meer informatie.](headers.md)

## <a name="troubleshooting-tips-for-common-rest-problems"></a>Tips voor probleemoplossing voor algemene problemen met REST

- Controleer alle headereigenschappen, inclusief de URL en API-versie.

- Zorg ervoor dat de eigenschappen indien nodig zijn opgenomen en correct zijn opgemaakt.

- Onjuiste matrixopmaak is een veelvoorkomende fout.

- **ETags** zijn tijdelijk en mogen dus niet worden opgeslagen. Wanneer een functie-aanroep een **ETags vereist,** gebruikt u de meest recente **ETags-waarde** door de resource opnieuw op te vragen. **ETags-waarden** moeten worden opgenomen tussen dubbele aanhalingstekens, zoals een tekenreeks:

   ```rest
   If-Match : "eyJpZCI6IjUwMWE4NjBjLTE2OTgtNDQyYi04MDhjLTRiNjEyY2NmMzVmMiIsInZlcnNpb24iOjF9"
   ```
