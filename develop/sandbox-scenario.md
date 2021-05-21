---
title: Sandbox-mogelijkheden voor reseller-relatie
description: Partner-sandbox biedt de mogelijkheid om relaties tussen de partner en de klant te ondersteunen
ms.date: 05/01/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9bef4a15685ebbdc2212988f5ac5724b946cfd54
ms.sourcegitcommit: 1aeaa12705a5945b8aab6bca254fedebd9c8bc4e
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 05/21/2021
ms.locfileid: "110243381"
---
# <a name="sandbox-capabilities-for-reseller-relationship"></a>Sandbox-mogelijkheden voor reseller-relatie

**Van toepassing op:**

- Partnercentrum
- Partnercentrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt uitgelegd wat er wordt ondersteund in de Sandbox voor resellerrelaties tussen de partner en de klant. 

## <a name="prerequisites"></a>Vereisten

- Partner Center accountreferenties. Het sandboxscenario ondersteunt verificatie met zowel de zelfstandige app- als app+gebruikersreferenties.
- Een klant-id (klant-tenant-id). Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard/home). Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**. Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**. Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.** De Microsoft-id is hetzelfde als de klant-id (klant-tenant-id).
- Alle Azure Reserved Virtual Machine Instances en software-aankooporders moeten worden geannuleerd voordat u een klant uit de Sandbox voor tipintegratie kunt verwijderen.

## <a name="scenarios-supporting-reseller-relationship"></a>Scenario's die een resellerrelatie ondersteunen

1.  Sandbox-partners voor directe factuur en indirecte providers kunnen relaties met de Sandbox-klant maken. 
2.  Sandbox Directe factuurpartners en indirecte providers kunnen sandbox-klanten niet uitnodigen.

3. Sandbox Direct Bill Partner en indirecte providers kunnen de resellerrelatie verwijderen uit Partner Center gebruikersinterface en API.

4. Met de Sandbox Remove Reseller-relatie wordt klant-AP verwijderen aanroepen. Hiermee verwijdert u de relatie en verwijdert u de tenant van de klant. {baseURL}/v1/Customers/{customer-Tenant-id}


    ### <a name="in-the-sandbox"></a>In de sandbox

    **Partners voor directe factuur:**

    - Kan bestaande klanten toevoegen

    - Kan geen relaties met nieuwe klanten aanvragen

    **Indirecte providers:**

    - Kan bestaande klanten toevoegen

    - Kan geen relaties met nieuwe klanten aanvragen

    - Kan geen relatie hebben met een indirecte reseller

    **Indirecte reseller:** 

    -   Kan relaties hebben met bestaande klanten

    -   Kan geen nieuwe relaties aanvragen of nieuwe klanten toevoegen

    ### <a name="in-partner-center"></a>In Partner Center

    **Partners voor directe factuur:**

    -   Kan nieuwe klanten toevoegen

    -   Kan relaties met nieuwe klanten aanvragen

    **Indirecte providers:**

    -   Kan nieuwe klanten toevoegen

    -   Kan relaties met nieuwe klanten aanvragen

    -   Kan relaties hebben met indirecte resellers

    **Indirecte resellers:**

    -   Kan geen nieuwe klanten toevoegen

    -   Kan relaties met nieuwe klanten aanvragen


Volg de [instructies in Resellerrelatie verwijderen](remove-a-reseller-relationship-with-a-customer.md) voor de klant voor meer informatie. Er zijn echter enkele verschillen tussen de product- en sandbox-mogelijkheden.

### <a name="request-syntax"></a>AANVRAAGSYNTAXIS

|**Methode**|**Verwijderen**|
|-------------|------------|
|Verwijderen|{baseURL}/v1/Customers/{customer-Tenant-id} |

Aanvraag body None

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen. Zie REST-foutcodes voor [Partner Center lijst.](./error-codes.md)

## <a name="next-steps"></a>Volgende stappen

- [Sandbox-abonnementen activeren voor Azure Marketplace producten](activate-sandbox-subscription-azure-marketplace-products.md)

- [Een bestelling van sandbox annuleren](cancel-an-order-from-the-integration-sandbox.md)

- [Testen en fouten opsporen](test-and-debug.md)