---
title: Resources van de overeenkomst met meta gegevens
description: De resource verzameling AgreementMetadata beschrijft overeenkomst typen die partners kunnen gebruiken om de acceptatie van klanten te bevestigen.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 36ba2aa2f78552dc9a835168b5bbd5b6a3ce47f3
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767207"
---
# <a name="agreement-metadata-resources"></a>Resources van de overeenkomst met meta gegevens

**Van toepassing op:**

- Partnercentrum

De **AgreementMetaData** -resource wordt momenteel alleen ondersteund door het partner centrum in de *open bare cloud van micro soft*. Deze resource is niet van toepassing op:

- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De **AgreementMetaData** -verzameling bevat meta gegevens over alle typen overeenkomsten. Partners kunnen deze verzameling gebruiken om een bevestiging van de acceptatie van de klant op te geven. De **AgreementMetaData** -verzameling retourneert meta gegevens voor beide overeenkomst typen (**Microsoft Cloud overeenkomst** en **micro soft Customer Agreement**).

## <a name="agreementmetadata"></a>AgreementMetaData

De geretourneerde meta gegevens van de overeenkomst bevatten de volgende eigenschappen:

| Eigenschap      | Type               | Description                                                                       |
|---------------|--------------------|-----------------------------------------------------------------------------------|
| Ontbrekende templateid    | tekenreeks             | De unieke id van een overeenkomst sjabloon.                                       |
| type          | tekenreeks             | Type overeenkomst. Op dit moment worden de volgende waarden ondersteund: **MicrosoftCloudAgreement** en **MicrosoftCustomerAgreement** (preview). |
| agreementLink | tekenreeks             | URL voor de overeenkomst sjabloon.                                                    |
