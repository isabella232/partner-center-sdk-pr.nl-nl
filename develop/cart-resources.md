---
title: Winkelwagen resources
description: Een partner plaatst een bestelling in een mandje wanneer een klant een abonnement wil kopen vanuit een lijst met aanbiedingen.
ms.date: 08/26/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 3aea428064654077ae67974132ec05918edfee65
ms.sourcegitcommit: a8fe6268fed2162843e7c92dca41c3919b25647d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/26/2020
ms.locfileid: "97767332"
---
# <a name="cart-resources"></a>Winkelwagen resources

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Een partner plaatst een bestelling wanneer een klant een abonnement wil kopen vanuit een lijst met aanbiedingen.

## <a name="cart"></a>Winkelwagen

Hierin wordt een winkel wagen beschreven.

| Eigenschap              | Type             | Beschrijving                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | Een winkel wagen-id die is opgegeven bij het maken van de winkel wagen.                               |
| creationTimeStamp     | DateTime         | De datum waarop de winkel wagen is gemaakt, in datum-tijd notatie. Wordt toegepast bij het maken van de winkel wagen.      |
| lastModifiedTimeStamp | DateTime         | De datum waarop de winkel wagen voor het laatst is bijgewerkt, in datum-tijd notatie. Wordt toegepast bij het maken van de winkel wagen. |
| expirationTimeStamp   | DateTime         | De datum waarop de winkel wagen verloopt, in datum-tijd notatie. Wordt toegepast bij het maken van de winkel wagen.          |
| lastModifiedUser      | tekenreeks           | De gebruiker die de winkel wagen het laatst heeft bijgewerkt. Wordt toegepast bij het maken van de winkel wagen.                          |
| Regel items             | Matrix van objecten | Een matrix met [CartLineItem](#cartlineitem) -resources.                                                   |
| status                | tekenreeks           | De status van de winkel wagen. Mogelijke waarden zijn ' Active ' (kunnen worden bijgewerkt/verzonden) en ' geordend ' (is al verzonden). |

## <a name="cartlineitem"></a>CartLineItem

Vertegenwoordigt één item dat in een mandje is opgenomen.

| Eigenschap             | Type                             | Beschrijving                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                           | Een unieke id voor een winkelwagen regel item. Wordt toegepast bij het maken van de winkel wagen.                                                                   |
| catalogItemId        | tekenreeks                           | De id van het catalogus item.                                                                                                                          |
| friendlyName         | tekenreeks                           | Optioneel. De beschrijvende naam voor het item dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.                                                                 |
| quantity             | int                              | Het aantal licenties of exemplaren.                                                                                                                  |
| currencyCode         | tekenreeks                           | De valuta code.                                                                                                                                    |
| billingCycle         | Object                           | Het type facturerings cyclus dat voor de huidige periode is ingesteld.                                                                                                 |
| termDuration         | tekenreeks                           | Een ISO 8601-representatie van de duur van de term. De huidige ondersteunde waarden zijn P1M (1 maand), P1Y (1 jaar) en P3Y (3 jaar).                                |
| deelnemers         | Lijst met object teken reeks paren      | Een verzameling partner on record (MPNID) voor de aankoop.                                                                                          |
| provisioningContext  | Dictionary<teken reeks, teken reeks>       | Aanvullende context die wordt gebruikt bij het inrichten van het aangeschafte item. Als u wilt weten welke waarden voor een bepaald item nodig zijn, raadpleegt u de eigenschap provisioningVariables van de SKU. |
| orderGroup           | tekenreeks                           | Een groep om aan te geven welke items samen in dezelfde volg orde kunnen worden ingediend.                                                                          |
| addonItems           | Lijst met **CartLineItem** -objecten | Een verzameling winkelwagen regel items voor addons. Deze items worden bij het basis abonnement aangeschaft dat het resultaat is van de aankoop van de hoofd mand regel van het artikel. |
| fout                | Object                           | Wordt toegepast nadat het wagentje is gemaakt als er een fout is opgetreden.                                                                                                    |
| renewsTo             | Matrix van objecten                 | Een matrix met [RenewsTo](#renewsto) -resources.                                                                            |

## <a name="renewsto"></a>RenewsTo

Hiermee wordt één item aangeduid dat zich in een winkelwagen regel item bevindt.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | tekenreeks           | No              | Een ISO 8601-representatie van de duur van de verlengings termijn. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar). |

### <a name="response-success-and-error-codes"></a>Geslaagde en fout codes

Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing. Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen. Zie [fout codes voor Partner Center](error-codes.md)voor de volledige lijst.

## <a name="carterror"></a>CartError

Hiermee wordt een fout aangeduid die zich voordoet nadat een mandje is gemaakt.

| Eigenschap         | Type                                   | Description                                                                                   |
|------------------|----------------------------------------|-----------------------------------------------------------------------------------------------|
| errorCode        | [Fout codes van partner centrum](error-codes.md) | Het type fout bij de wagen.                                                                       |
| errorDescription | tekenreeks                                 | De fout beschrijving, inclusief opmerkingen over ondersteunde waarden, standaard waarden of limieten. |

## <a name="cartcheckoutresult"></a>CartCheckoutResult

Hiermee wordt het resultaat van een mandje afhandelen.

| Eigenschap    | Type                                              | Description                     |
|-------------|---------------------------------------------------|---------------------------------|
| orders      | Lijst met [order](order-resources.md#order) objecten.         | De verzameling orders.       |
| orderErrors | Lijst met [OrderError](#ordererror) -objecten. | Het verzamelen van order fouten. |

## <a name="ordererror"></a>OrderError

Hiermee wordt een fout aangeduid die optreedt tijdens het afhandelen van een mandje wanneer een order wordt gemaakt.

| Eigenschap     | Type   | Description                                     |
|--------------|--------|-------------------------------------------------|
| orderGroupId | tekenreeks | De order groep-ID van de order met de fout. |
| code         | int    | De fout code.                                 |
| beschrijving  | tekenreeks | De beschrijving van de fout.                   |
