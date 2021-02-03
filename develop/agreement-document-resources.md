---
title: Document bronnen van de overeenkomst
description: De AgreementDocument-resource is een micro soft-overeenkomst document voor preview en down load. Het wordt ondersteund door het partner centrum in de open bare cloud van micro soft.
ms.date: 08/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 4805d25b0838bf922b81bebd998810c3f6a809c3
ms.sourcegitcommit: d1104d5c27f8fb3908a87532f80c432f0147ef5d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 11/13/2020
ms.locfileid: "97767604"
---
# <a name="agreement-document-resources-supported-by-partner-center-in-the-microsoft-public-cloud"></a>Document bronnen van de overeenkomst die worden ondersteund door het partner centrum in de open bare cloud van micro soft

**Van toepassing op:**

- Partnercentrum

De **AgreementDocument** -resource wordt momenteel alleen ondersteund door het partner centrum in de *open bare cloud van micro soft*. Deze resource is niet van toepassing op:

- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De resource **AgreementDocument** vertegenwoordigt een micro soft-overeenkomst document dat beschikbaar is voor preview en down load.

## <a name="agreementdocument"></a>AgreementDocument

Een **AgreementDocument** -resource bevat de volgende eigenschappen:

| Eigenschap       | Type   | Description                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| country | tekenreeks | Het land of de markt waarop dit document van toepassing is. |
| language | tekenreeks | De taal waarin dit document is gelokaliseerd. |
| displayUri | tekenreeks | Een koppeling om een voor beeld van het overeenkomst document in een browser te bekijken.  |
| downloadUri |tekenreeks | Een koppeling voor het downloaden van het overeenkomst document (in micro soft Word-indeling). |
