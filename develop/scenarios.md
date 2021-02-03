---
title: API-scenario's voor partner centrum
description: Meer informatie over hoe de partners van het Cloud Solution Provider-programma de partner centrum-API kunnen gebruiken om klant accounts, bestellingen, ondersteuning en facturering programmatisch te beheren.
ms.date: 10/13/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 14dbd501e3d075c3880fae6f362feef797cba133
ms.sourcegitcommit: 8a5c37376a29e29fe0002a980082d4acc6b91131
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/11/2020
ms.locfileid: "97767580"
---
# <a name="partner-center-api-scenarios-that-let-you-programmatically-manage-customer-accounts"></a>API-scenario's voor partner centrum waarmee u op een programmatische manier klant accounts kunt beheren

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel worden een aantal manieren beschreven waarop partners in het Cloud Solution Provider-programma de partner centrum-API kunnen gebruiken om op een programmatische manier gebieden te beheren:

- Klant accounts
- Bestellingen
- Abonnementen
- Ondersteuning
- Billing

Er zijn verschillende versies van het partner centrum beschikbaar die verschillende mogelijkheden hebben. Niet alle scenario's worden ondersteund in alle versies van partner Center. Zie [ontwikkelen voor Partner Center voor micro soft National Cloud](developing-for-partner-center-for-microsoft-national-cloud.md)voor meer informatie.

## <a name="scenarios-supported-by-the-partner-center-sdk"></a>Scenario's die worden ondersteund door de Partner Center SDK

Alle volgende scenario's kunnen op drie verschillende manieren worden uitgevoerd:

- Hand matig in het dash board van de [partner centrum](https://partner.microsoft.com/dashboard) .

- Programmatisch met behulp van de beheerde API van het partner centrum.

- Programmatisch met behulp van het REST API van de Partner Center.

| Voor meer informatie over deze ondersteunde scenario's:  | Zie deze resource:     |
|----------------------------------|--------------------------|
| **Analytics:** Meer informatie over het ophalen van analyse gegevens over Azure-gebruik, abonnementen, licenties of verwijzingen.         | [Analyse](usage-analytics.md)  |
| **Controle bewerkingen:** Meer informatie over het ophalen van historische controle records van de activiteiten en bewerkingen van het partner centrum. | [Auditbewerkingen](audit.md)                     |
| **Implementaties van apparaten:** Meer informatie over het configureren van beleids regels voor apparaten, het werken met batches voor apparaten en meta gegevens van apparaten. Deze scenario's omvatten het toevoegen, verwijderen, bijwerken en ophalen van het configuratie beleid voor apparaten.    | [Implementatie van apparaat](device-deployment.md)  |
| **Accounts en profielen:** Meer informatie over het ophalen of bijwerken van facturerings profielen voor partners, juridische profielen, MPN profiel, zakelijke profielen of ondersteunings profielen. U kunt ook een lijst met klanten of indirecte wederverkopers ophalen. | [Accounts en profielen beheren](manage-profiles-and-information.md)                                                                        |
| **Facturering:** Meer informatie over gebieden zoals het wijzigen van de facturerings cyclus, het ophalen van Azure-tarieven en Azure-gebruiks gegevens, het ophalen van facturen, het verkrijgen van het huidige account saldo van de partner of het verkrijgen van kosten voor de klanten service.  | [De facturering beheren](manage-billing.md)   |
| **Azure-uitgaven:** Krijg informatie over het gebruik van Azure-uitgaven en-partners, het gebruik van klant abonnementen, gebruik van de data limiet en budget gebruik. Daarnaast wordt beschreven hoe u een klant gebruiks budget bijwerkt. | [Uitgaven voor Azure](azure-spending.md)  |
| **Klant accounts beheren:** Leer hoe u veel aspecten van het account beheer van klanten kunt doen, zoals het maken en verwijderen van klant accounts of de gebruikers accounts van een klant, het beheren en valideren van klant account gegevens, het beheren van gebruikers accounts en het toewijzen van licenties.  | [Klanten beheren](manage-customers.md)  |
| **Beheren van orders:** Meer informatie over de manieren waarop u klant orders en abonnementen kunt beheren via een programma. Dit gebied omvat het aanschaffen van Azure-reserve ringen, het maken van orders, het ophalen van aanbiedingen uit de catalogus en het beheren van aanbiedingen voor proef versies.   | [Bestellingen beheren](manage-orders.md)  |
| **Ondersteuning bieden:** Meer informatie over het beheren van services voor een klant, het verkrijgen of bijwerken van ondersteunings contacten voor een abonnement en het beheren van service aanvragen.  | [Ondersteuning bieden](provide-support.md)   |
| **Verwijzingen:** Meer informatie over het maken van een verwijzing, het ophalen van een lijst met verwijzingen of het bijwerken van een verwijzing.  | [Verwijzingen](/partner/develop/referrals)  |
| **Hulpprogram ma's:** Meer informatie over het valideren van een adres, het ophalen van adres regels per markt, het controleren van de beschik baarheid van domeinen, het verwijderen van een klant account uit de integratie sandbox of het verkrijgen van een record van de Partner Center-activiteit. | [Hulpprogramma's](utilities.md)  |
| **Beveiliging:** Meer informatie over de REST-Api's met betrekking tot multi-factor Authentication (MFA) in partner centrum. Met deze Api's kunt u MFA afdwingen voor elk gebruikers account in uw partner Tenant.  | [Status van partner beveiligings vereisten](partner-security-requirements.md)  |

## <a name="next-steps"></a>Volgende stappen

- [Zie voor beelden van partner Center](partner-center-samples.md)
- [Meer informatie over hoe u aan de slag gaat](get-started.md)