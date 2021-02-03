---
title: Beheerde service resources
description: Beheerde services zijn services waaraan een partner beheerders bevoegdheden heeft gedelegeerd. Partners kunnen ondersteuning bieden voor en bestands service aanvragen namens hun beheerde services.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ef644ac4d8ae9660cffc9558af33cc27832556c7
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767215"
---
# <a name="managed-service-resources"></a>Beheerde service resources

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Beheerde services zijn services waaraan een partner beheerders bevoegdheden heeft gedelegeerd. Partners kunnen ondersteuning bieden voor en bestands service aanvragen namens hun beheerde services.

## <a name="managedservice"></a>ManagedService

Hierin wordt een beheerde service beschreven.

| Eigenschap   | Type                | Description                                              |
|------------|---------------------|----------------------------------------------------------|
| Id         | tekenreeks              | De beheerde service-id.                                  |
| Name       | tekenreeks              | De naam van de beheerde service.                         |
| GroupName  | tekenreeks              | De naam van de groep waartoe de service behoort.      |
| Koppelingen      | ManagedServiceLinks | De resource koppelingen die overeenkomen met de beheerde service. |
| Kenmerken | ResourceAttributes  | De meta gegevens kenmerken die overeenkomen met de overeenkomst.  |

## <a name="managedservicelinks"></a>ManagedServiceLinks

Bevat de koppelingen waarmee de partner met gedelegeerde beheerders machtigingen toegang biedt voor de service.

| Eigenschap      | Type | Description                 |
|---------------|------|-----------------------------|
| AdminService  | Koppeling | De URI van de beheer service.      |
| ServiceHealth | Koppeling | De URI van de service status.     |
| ServiceTicket | Koppeling | De URI van het service ticket.     |
| Zelf          | Koppeling | De zelf-URI.               |
| Volgende          | Koppeling | De volgende pagina met items.     |
| Vorige      | Koppeling | De vorige pagina met items. |

