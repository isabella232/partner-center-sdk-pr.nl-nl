---
title: Resources voor overeenkomstmetagegevens
description: In de agreementMetadata-resourceverzameling worden overeenkomsttypen beschreven die partners kunnen gebruiken om de acceptatie van klanten te bevestigen.
ms.date: 02/12/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 7c09dc2a8dd88e3d3a6a7925f6f61737cbbd410eabda6ecb4c3ead13d889de04
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115991256"
---
# <a name="agreement-metadata-resources"></a>Resources voor overeenkomstmetagegevens

**Van toepassing op**: Partner Center

**Is niet van toepassing op**: Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

De **AgreementMetaData-resource** wordt momenteel ondersteund door Partner Center alleen in de openbare Cloud van Microsoft. 

De **verzameling AgreementMetaData** bevat metagegevens over alle typen overeenkomst. Partners kunnen deze verzameling gebruiken om de acceptatie van overeenkomsten door de klant te bevestigen. De **verzameling AgreementMetaData** retourneert metagegevens voor beide typen overeenkomst (**Microsoft Cloud-overeenkomst** en **Microsoft-klantovereenkomst**).

## <a name="agreementmetadata"></a>AgreementMetaData

Geretourneerde metagegevens van overeenkomst bevatten de volgende eigenschappen:

| Eigenschap      | Type               | Description                                                                       |
|---------------|--------------------|-----------------------------------------------------------------------------------|
| templateId    | tekenreeks             | De unieke id van een overeenkomstsjabloon.                                       |
| type          | tekenreeks             | Overeenkomsttype. Momenteel worden onder andere **MicrosoftCloudAgreement** en **MicrosoftCustomerAgreement (preview) ondersteund.** |
| agreementLink | tekenreeks             | URL voor de overeenkomstsjabloon.                                                    |
