---
title: De status van direct ondertekenen (direct accepteren) van een klant overeenkomst.
description: De resource DirectSignedCustomerAgreementStatus vertegenwoordigt de status van de directe ondertekening (directe acceptatie) van een klant overeenkomst.
ms.date: 02/11/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: aarzh-AaronZhang
ms.author: v-aarzh
ms.openlocfilehash: 9c4fd12ac3319057f3c4034aa0c8d93dcda726c6
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767193"
---
# <a name="direct-signing-direct-acceptance-status-of-a-customer-agreement"></a>Status van direct ondertekenen (direct geaccepteerd) van een klant overeenkomst

**Van toepassing op:**

- Partnercentrum

De **DirectSignedCustomerAgreementStatus** -resource wordt momenteel alleen ondersteund door het partner centrum in de open bare cloud van micro soft.

Deze resource is *niet van toepassing* op:

- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

De **DirectSignedCustomerAgreementStatus** -resource vertegenwoordigt de status van de directe acceptatie van een klant overeenkomst.

## <a name="directsignedcustomeragreementstatus"></a>DirectSignedCustomerAgreementStatus

Een **DirectSignedCustomerAgreementStatus** -resource bevat de volgende eigenschappen:

| Eigenschap       | Type   | Description                                                                                               |
|----------------|--------|-----------------------------------------------------------------------------------------------------------|
| isSigned | booleaans | Hiermee wordt aangegeven of de klant overeenkomst rechtstreeks is ondertekend (geaccepteerd) door de klant. |
