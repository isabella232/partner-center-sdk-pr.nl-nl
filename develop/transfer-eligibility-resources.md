---
title: TransferEligibility-resources
description: Een partner kan een overdracht maken wanneer een klant een abonnement bij de partner aanvraagt om te worden overgedragen naar een andere partner.
ms.date: 04/10/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ffe72aa04de17cf6e45e49e9fdbec8ba08da2deed89f5d54425a17825c91a53a
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115996645"
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