---
title: Overeenkomstbronnen
description: De overeenkomstresource vertegenwoordigt een Microsoft Cloud-klantovereenkomst met details van de certificering die door de partner wordt geleverd.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 5fa196e711d9ff899b61ba20e75edd92749165e5
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025613"
---
# <a name="agreement-resources-representing-a-microsoft-cloud-customer-agreement"></a>Overeenkomstbronnen die een Microsoft Cloud-klantovereenkomst vertegenwoordigen

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De **overeenkomstresource** wordt momenteel alleen ondersteund door Partner Center in de openbare Cloud van Microsoft.

De **overeenkomstresource** vertegenwoordigt een Microsoft Cloud-klantovereenkomst.

## <a name="agreement"></a>Overeenkomst

De **overeenkomstresource** vertegenwoordigt de details van de certificering die door de partner wordt geleverd.

| Eigenschap       | Type   | Beschrijving                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| userId         | tekenreeks                         | Object-id van de aangemelde gebruiker in de partner-tenant die namens de partnerorganisatie een bevestiging geeft. Wanneer u app+gebruikersverificatie gebruikt om een overeenkomstresource te maken, wordt Partner Center kenmerkwaarde **userId** automatisch afgeleid van het token App+Gebruiker.                                                                             |
| primaryContact | [Contact](./utility-resources.md#contact) | Informatie over de gebruiker van de klantorganisatie die de overeenkomst heeft geaccepteerd, waaronder:  **firstName,** **lastName,** **email** en **phoneNumber** (optioneel). |
| dateAgreed     | tekenreeks in UTC-datum/tijd-indeling | De datum waarop de klant de overeenkomst heeft geaccepteerd.                                 |
| templateId     |tekenreeks                          | De unieke id van de overeenkomst die de klant heeft geaccepteerd. |
| type           |tekenreeks                          | Overeenkomsttype. Momenteel zijn de ondersteunde **waarden MicrosoftCloudAgreement** **en MicrosoftCustomerAgreement**.|
| agreementLink  | tekenreeks                         | URL voor de overeenkomstsjabloon.                                                    |
