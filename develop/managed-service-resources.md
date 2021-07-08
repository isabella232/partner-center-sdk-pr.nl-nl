---
title: Beheerde servicebronnen
description: Beheerde services zijn services waaraan een partner beheerdersbevoegdheden heeft gedelegeerd. Partners kunnen ondersteuning bieden voor en serviceaanvragen indienen namens hun beheerde services.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 582efe75fd18a9174dd5dc173c290bee25443ee9
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548121"
---
# <a name="managed-service-resources"></a>Beheerde servicebronnen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Beheerde services zijn services waaraan een partner beheerdersbevoegdheden heeft gedelegeerd. Partners kunnen ondersteuning bieden voor en serviceaanvragen indienen namens hun beheerde services.

## <a name="managedservice"></a>ManagedService

Beschrijft een beheerde service.

| Eigenschap   | Type                | Beschrijving                                              |
|------------|---------------------|----------------------------------------------------------|
| Id         | tekenreeks              | De id van de beheerde service.                                  |
| Name       | tekenreeks              | De naam van de beheerde service.                         |
| Groupname  | tekenreeks              | De naam van de groep waar de service bij hoort.      |
| Koppelingen      | ManagedServiceLinks | De resourcekoppelingen die overeenkomen met de beheerde service. |
| Kenmerken | ResourceAttributes  | De metagegevenskenmerken die overeenkomen met de overeenkomst.  |

## <a name="managedservicelinks"></a>ManagedServiceLinks

Bevat de koppelingen waarmee de partner met gedelegeerde beheerdersmachtigingen ondersteuning kan bieden voor de service.

| Eigenschap      | Type | Beschrijving                 |
|---------------|------|-----------------------------|
| AdminService  | Koppeling | De URI van de beheerservice.      |
| ServiceHealth | Koppeling | De URI voor service health.     |
| ServiceTicket | Koppeling | De serviceticket-URI.     |
| Zelf          | Koppeling | De zelf-URI.               |
| Volgende          | Koppeling | De volgende pagina met items.     |
| Vorige      | Koppeling | De vorige pagina met items. |

