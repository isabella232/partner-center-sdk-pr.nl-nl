---
title: Winkelwagenresources
description: Een partner plaatst een bestelling in een winkelwagen wanneer een klant een abonnement wil kopen uit een lijst met aanbiedingen.
ms.date: 08/26/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 08085dde1b43f20b6f6bf707120dd87c48816aba
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974145"
---
# <a name="cart-resources"></a>Winkelwagenresources

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Een partner plaatst een bestelling wanneer een klant een abonnement wil kopen uit een lijst met aanbiedingen.

## <a name="cart"></a>Winkelwagen

Beschrijft een winkelwagen.

| Eigenschap              | Type             | Beschrijving                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | Een winkelwagen-id die wordt opgegeven wanneer de winkelwagen is gemaakt.                               |
| creationTimeStamp     | DateTime         | De datum waarop de winkelwagen is gemaakt, in datum/tijd-indeling. Toegepast wanneer de winkelwagen is gemaakt.      |
| lastModifiedTimeStamp | DateTime         | De datum waarop de winkelwagen het laatst is bijgewerkt, in datum/tijd-indeling. Toegepast wanneer de winkelwagen is gemaakt. |
| expirationTimeStamp   | DateTime         | De datum waarop de winkelwagen verloopt, in datum/tijd-indeling. Toegepast bij het maken van de winkelwagen.          |
| lastModifiedUser      | tekenreeks           | De gebruiker die de winkelwagen voor het laatst heeft bijgewerkt. Toegepast bij het maken van de winkelwagen.                          |
| lineItems             | Matrix van objecten | Een matrix van [CartLineItem-resources.](#cartlineitem)                                                   |
| status                | tekenreeks           | De status van de winkelwagen. Mogelijke waarden zijn 'Actief' (kan worden bijgewerkt/verzonden) en 'Besteld' (is al verzonden). |

## <a name="cartlineitem"></a>CartLineItem

Vertegenwoordigt één item in een winkelwagen.

| Eigenschap             | Type                             | Beschrijving                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                           | Een unieke id voor een winkelwagenregelitem. Toegepast bij het maken van de winkelwagen.                                                                   |
| catalogItemId        | tekenreeks                           | De id van het catalogusitem.                                                                                                                          |
| Friendlyname         | tekenreeks                           | Optioneel. De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het opsysen van ambiguïteit.                                                                 |
| quantity             | int                              | Het aantal licenties of instanties.                                                                                                                  |
| currencyCode         | tekenreeks                           | De valutacode.                                                                                                                                    |
| billingCycle         | Object                           | Het type factureringscyclus dat is ingesteld voor de huidige periode.                                                                                                 |
| termDuration         | tekenreeks                           | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn P1M (1 maand), P1Y (1 jaar) en P3Y (3 jaar).                                |
| deelnemers         | Lijst met objectreeksparen      | Een verzameling PartnerId on Record (MPN-id) voor de aankoop.                                                                                          |
| provisioningContext  | Woordenlijst<tekenreeks, tekenreeks>       | Aanvullende context die wordt gebruikt bij het inrichten van het gekochte item. Als u wilt bepalen welke waarden nodig zijn voor een bepaald item, raadpleegt u de eigenschap provisioningVariables van de SKU. |
| orderGroup           | tekenreeks                           | Een groep om aan te geven welke items samen in dezelfde volgorde kunnen worden verzonden.                                                                          |
| addonItems           | Lijst met **CartLineItem-objecten** | Een verzameling winkelwagenregelitems voor addons. Deze items worden aangeschaft voor het basisabonnement dat het resultaat is van de aankoop van het regelitem van de hoofdwagen. |
| fout                | Object                           | Toegepast nadat de winkelwagen is gemaakt als er een fout is opgetreden.                                                                                                    |
| renewsTo             | Matrix van objecten                 | Een matrix van [RenewsTo-resources.](#renewsto)                                                                            |

## <a name="renewsto"></a>RenewsTo

Vertegenwoordigt één item in een winkelwagenregelitem.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | tekenreeks           | No              | Een ISO 8601-weergave van de duur van de verlengingsperiode. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar). |

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes](error-codes.md).

## <a name="carterror"></a>CartError

Vertegenwoordigt een fout die optreedt nadat een winkelwagen is gemaakt.

| Eigenschap         | Type                                   | Beschrijving                                                                                   |
|------------------|----------------------------------------|-----------------------------------------------------------------------------------------------|
| errorCode        | [Partner Center-foutcodes](error-codes.md) | Het type winkelwagenfout.                                                                       |
| errorDescription | tekenreeks                                 | De foutbeschrijving, inclusief eventuele opmerkingen over ondersteunde waarden, standaardwaarden of limieten. |

## <a name="cartcheckoutresult"></a>CartCheckoutResult

Vertegenwoordigt het resultaat van het uitchecken van een winkelwagen.

| Eigenschap    | Type                                              | Beschrijving                     |
|-------------|---------------------------------------------------|---------------------------------|
| orders      | Lijst met [orderobjecten.](order-resources.md#order)         | De verzameling orders.       |
| orderErrors | Lijst met [OrderError-objecten.](#ordererror) | De verzameling orderfouten. |

## <a name="ordererror"></a>OrderError

Vertegenwoordigt een fout die optreedt tijdens het uitchecken van een winkelwagen wanneer een order wordt gemaakt.

| Eigenschap     | Type   | Beschrijving                                     |
|--------------|--------|-------------------------------------------------|
| orderGroupId | tekenreeks | De ordergroep-id van de bestelling met de fout. |
| code         | int    | De foutcode.                                 |
| beschrijving  | tekenreeks | De beschrijving van de fout.                   |
