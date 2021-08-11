---
title: Beheerde servicebronnen
description: Beheerde services zijn services waaraan een partner beheerdersbevoegdheden heeft gedelegeerd. Partners kunnen ondersteuning bieden voor aanvragen van en bestandsservices namens hun beheerde services.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 066c9f2a0d5ca8d03553508c2b471ca49735406a5a0566bf48b0773385c129f7
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115994384"
---
# <a name="managed-service-resources"></a>Beheerde servicebronnen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Beheerde services zijn services waaraan een partner beheerdersbevoegdheden heeft gedelegeerd. Partners kunnen ondersteuning bieden voor aanvragen van en bestandsservices namens hun beheerde services.

## <a name="managedservice"></a>ManagedService

Beschrijft een beheerde service.

| Eigenschap   | Type                | Description                                              |
|------------|---------------------|----------------------------------------------------------|
| Id         | tekenreeks              | De id van de beheerde service.                                  |
| Name       | tekenreeks              | De naam van de beheerde service.                         |
| Groupname  | tekenreeks              | De naam van de groep waar de service bij hoort.      |
| Koppelingen      | ManagedServiceLinks | De resourcekoppelingen die overeenkomen met de beheerde service. |
| Kenmerken | ResourceAttributes  | De metagegevenskenmerken die overeenkomen met de overeenkomst.  |

## <a name="managedservicelinks"></a>ManagedServiceLinks

Bevat de koppelingen waarmee de partner met gedelegeerde beheerdersmachtigingen ondersteuning kan bieden voor de service.

| Eigenschap      | Type | Description                 |
|---------------|------|-----------------------------|
| AdminService  | Koppeling | De URI van de beheerservice.      |
| ServiceHealth | Koppeling | De status-URI van de service.     |
| ServiceTicket | Koppeling | De serviceticket-URI.     |
| Zelf          | Koppeling | De zelf-URI.               |
| Volgende          | Koppeling | De volgende pagina met items.     |
| Vorige      | Koppeling | De vorige pagina met items. |

