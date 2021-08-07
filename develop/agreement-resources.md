---
title: Overeenkomstbronnen
description: De overeenkomstresource vertegenwoordigt een Microsoft Cloud-klantovereenkomst met details van de certificering die door de partner wordt geleverd.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: dc67d93a40cdced977412ff8151a661f6655c0fa1d079c8f1bc468f0f8b1eea2
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115992468"
---
# <a name="agreement-resources-representing-a-microsoft-cloud-customer-agreement"></a>Overeenkomstbronnen die een Microsoft Cloud-klantovereenkomst vertegenwoordigen

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De **overeenkomstresource** wordt momenteel alleen ondersteund door Partner Center in de openbare Cloud van Microsoft.

De **overeenkomstresource** vertegenwoordigt een Microsoft Cloud-klantovereenkomst.

## <a name="agreement"></a>Overeenkomst

De **overeenkomstresource** vertegenwoordigt de details van de certificering die door de partner wordt geleverd.

| Eigenschap       | Type   | Description                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| userId         | tekenreeks                         | Object-id van de aangemelde gebruiker in de partner-tenant die namens de partnerorganisatie een bevestiging geeft. Wanneer u app+gebruikersverificatie gebruikt om een overeenkomstresource te maken, wordt Partner Center kenmerkwaarde **userId** automatisch afgeleid van het token App+Gebruiker.                                                                             |
| primaryContact | [Contact](./utility-resources.md#contact) | Informatie over de gebruiker van de klantorganisatie die de overeenkomst heeft geaccepteerd, waaronder:  **firstName,** **lastName,** **email** en **phoneNumber** (optioneel). |
| dateAgreed     | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de klant de overeenkomst heeft geaccepteerd.                                 |
| templateId     |tekenreeks                          | De unieke id van de overeenkomst die de klant heeft geaccepteerd. |
| type           |tekenreeks                          | Overeenkomsttype. Momenteel zijn de ondersteunde **waarden MicrosoftCloudAgreement** **en MicrosoftCustomerAgreement**.|
| agreementLink  | tekenreeks                         | URL voor de overeenkomstsjabloon.                                                    |
