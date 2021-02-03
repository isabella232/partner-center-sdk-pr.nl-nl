---
title: Overeenkomst bronnen
description: De overeenkomst resource vertegenwoordigt een micro soft Cloud-klant overeenkomst met details van certificering van de partner.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: d964b1c7c6d70814ef68e48f05611ecbb113c8fe
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767601"
---
# <a name="agreement-resources-representing-a-microsoft-cloud-customer-agreement"></a>Overeenkomst bronnen die een micro soft-Cloud klant overeenkomst vertegenwoordigen

**Van toepassing op:**

- Partnercentrum

De bron van de **overeenkomst** wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft. Het is niet van toepassing op:

- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De **overeenkomst** resource vertegenwoordigt een micro soft-Cloud-klant overeenkomst.

## <a name="agreement"></a>Overeenkomst

De **overeenkomst** resource bevat de details van de certificering die is verschaft door de partner.

| Eigenschap       | Type   | Description                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| userId         | tekenreeks                         | De object-id van de aangemelde gebruiker in de partner-Tenant die een bevestiging verstrekt namens de partner organisatie. Wanneer u app + gebruikers authenticatie gebruikt voor het maken van een overeenkomst resource, wordt in het partner centrum automatisch de kenmerk- **id** van het gebruikers token van de app + gebruiker afgeleid.                                                                             |
| primaryContact | [Contact](./utility-resources.md#contact) | Informatie over de gebruiker van de organisatie van de klant die de overeenkomst heeft geaccepteerd, waaronder:  **FirstName**, **LastName**, **email** en **phonenumber** (optioneel). |
| dateAgreed     | teken reeks in UTC-datum tijd notatie | De datum waarop de klant de overeenkomst heeft geaccepteerd.                                 |
| Ontbrekende templateid     |tekenreeks                          | De unieke id van de overeenkomst die de klant heeft geaccepteerd. |
| type           |tekenreeks                          | Type overeenkomst. Op dit moment worden de volgende waarden ondersteund: **MicrosoftCloudAgreement** en **MicrosoftCustomerAgreement**.|
| agreementLink  | tekenreeks                         | URL voor de overeenkomst sjabloon.                                                    |
