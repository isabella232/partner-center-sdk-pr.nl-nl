---
title: TransferEligibility-resources
description: Een partner kan een overdracht maken wanneer een klant een abonnement bij de partner aanvraagt om te worden overgedragen naar een andere partner.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8f121d499abffb4c4dda688c2a91c25f83d2e863
ms.sourcegitcommit: 4275f9f67f9479ce27af6a9fda96fe86d0bc0b44
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/05/2021
ms.locfileid: "111530205"
---
# <a name="transfereligibility-resources"></a>TransferEligibility-resources

Een partner kan een overdracht maken wanneer een klant een abonnement bij de partner aanvraagt om te worden overgedragen naar een andere partner. Gebruik TransferEligibility om te controleren of een abonnement in aanmerking komt voor overdracht.

## <a name="transfereligibility"></a>TransferEligibility

Beschrijft een transferEligibility.

| Eigenschap              | Type             | Beschrijving                                                                              |
|-----------------------|------------------|------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | De abonnements-id van de klant.                                                  |
| isEligible            | booleaans             | Geeft aan of het abonnement in aanmerking komt voor de overdracht.                         |
| Reden                | tekenreeks           | De eigenschap reason verklaart waarom het abonnement niet in aanmerking komt voor overdracht. |