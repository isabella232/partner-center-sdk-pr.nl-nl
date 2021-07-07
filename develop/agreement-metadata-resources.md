---
title: Resources voor overeenkomstmetagegevens
description: In de resourceverzameling AgreementMetadata worden overeenkomsttypen beschreven die partners kunnen gebruiken om de acceptatie van klanten te bevestigen.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: b930e3691b9d269ddb8d76ae18b6b26a217123c0
ms.sourcegitcommit: c7dd3f92cade7f127f88cf6d4d6df5e9a05eca41
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/11/2021
ms.locfileid: "112025622"
---
# <a name="agreement-metadata-resources"></a>Resources voor overeenkomstmetagegevens

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De **AgreementMetaData-resource** wordt momenteel alleen Partner Center in de openbare Cloud van Microsoft. 

De **verzameling AgreementMetaData** bevat metagegevens over alle typen overeenkomst. Partners kunnen deze verzameling gebruiken om de acceptatie van overeenkomsten door de klant te bevestigen. De **verzameling AgreementMetaData** retourneert metagegevens voor beide typen overeenkomst (**Microsoft Cloud-overeenkomst** en **Microsoft-klantovereenkomst**).

## <a name="agreementmetadata"></a>AgreementMetaData

Geretourneerde overeenkomstmetagegevens bevatten de volgende eigenschappen:

| Eigenschap      | Type               | Beschrijving                                                                       |
|---------------|--------------------|-----------------------------------------------------------------------------------|
| templateId    | tekenreeks             | Unieke id van een overeenkomstsjabloon.                                       |
| type          | tekenreeks             | Overeenkomsttype. Momenteel zijn de ondersteunde **waarden MicrosoftCloudAgreement** **en MicrosoftCustomerAgreement** (preview). |
| agreementLink | tekenreeks             | URL voor de overeenkomstsjabloon.                                                    |
