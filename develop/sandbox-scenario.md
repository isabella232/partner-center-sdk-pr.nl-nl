---
title: Sandbox-mogelijkheden voor partners die reseller-relatie ondersteunen
description: Partner sandbox biedt de mogelijkheid om relaties tussen de partner en de klant te ondersteunen
ms.date: 11/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: af46811b3615e1f904a9619de85b0aca7622490b
ms.sourcegitcommit: 717e483a6eec23607b4e31ddfaa3e2691f3043e6
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/20/2021
ms.locfileid: "104711862"
---
# <a name="partner-sandbox-capabilities-that-support-reseller-relationship"></a>Sandbox-mogelijkheden voor partners die reseller-relatie ondersteunen

**Van toepassing op:**

- Partnercentrum
- Partnercentrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

In dit artikel wordt uitgelegd wat wordt ondersteund in de sandbox voor wederverkoper relaties tussen de partner en de klant. 

## <a name="prerequisites"></a>Vereisten

- Referenties van het partner centrum-account. Het sandbox-scenario ondersteunt verificatie met zowel de zelfstandige app als de app + gebruikers referenties.
- Een klant-ID (klant-Tenant-id). Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard/home)van de partner centrum. Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**. Selecteer de klant in de lijst klant en selecteer vervolgens **account**. Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** . De micro soft-ID is gelijk aan de klant-ID (klant-Tenant-id).
- Alle Azure Reserved Virtual Machine Instances-en software-aankoop orders moeten worden geannuleerd voordat een klant uit de tip Integration sandbox kan worden verwijderd.

## <a name="scenarios-supporting-reseller-relationship"></a>Scenario's die reseller Relationship ondersteunen

1.  Sandbox direct-factuur partners en indirecte providers kunnen relatie maken met de klant in de sandbox. 
2.  Sandbox direct-factuur partners en indirecte providers kunnen sandbox-klanten niet uitnodigen.



### <a name="in-the-sandbox"></a>In de sandbox

**Directe factuur partners**:

• Kan bestaande klanten toevoegen

• Kan geen relaties aanvragen met nieuwe klanten

**Indirecte providers**:

• Kan bestaande klanten toevoegen

• Kan geen relaties aanvragen met nieuwe klanten

• Kan geen relatie hebben met een indirecte wederverkoper

**Indirecte wederverkoper**: (binnenkort beschikbaar)

• Kan een relatie met bestaande klanten hebben

• Kan geen nieuwe relaties aanvragen of nieuwe klanten toevoegen

### <a name="in-partner-center"></a>In partner centrum

**Directe factuur partners**:

• Kan nieuwe klanten toevoegen

• Kan relaties aanvragen met nieuwe klanten

**Indirecte providers**:

• Kan nieuwe klanten toevoegen

• Kan relaties aanvragen met nieuwe klanten

• Kan relaties hebben met indirecte wederverkopers

**Indirecte wederverkopers**:

• Kan geen nieuwe klanten toevoegen

• Kan relaties aanvragen met nieuwe klanten

3. Sandbox direct Bill-partner en indirecte providers kunnen wederverkoper-relaties verwijderen uit de gebruikers interface en API van partner Center.

4. Met de sandbox-relatie verwijderen wordt het verwijderen van de klant-AP aangeroepen. Hiermee wordt de relatie verwijderd en wordt de Tenant van de klant verwijderd. {baseURL}/v1/Customers/{customer-Tenant-id}

Volg de [wederverkoper-relatie verwijderen](remove-a-reseller-relationship-with-a-customer.md) voor de klant voor meer informatie. Er zijn echter enkele verschillen tussen de mogelijkheden van het product en de sandbox.

### <a name="request-syntax"></a>SYNTAXIS VAN AANVRAAG

|**Methode**|**Verwijderen**|
|-------------|------------|
|Verwijderen|{baseURL}/v1/Customers/{customer-Tenant-id} |

Hoofd tekst van aanvraag geen

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [rest-fout codes van het partner centrum](./error-codes.md)voor de volledige lijst.

## <a name="next-steps"></a>Volgende stappen

- [Sandbox-abonnementen voor Azure Marketplace-producten activeren](activate-sandbox-subscription-azure-marketplace-products.md)

- [Een order annuleren vanuit sandbox](cancel-an-order-from-the-integration-sandbox.md)

- [Testen en fouten opsporen](test-and-debug.md)