---
title: Winkelwagenresources
description: Een partner plaatst een bestelling in een winkelwagen wanneer een klant een abonnement wil kopen uit een lijst met aanbiedingen.
ms.date: 08/26/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c9372bb982528127f8870094e26465d004b1f05c75140f0ac729375f5d5f3302
ms.sourcegitcommit: 63ef5995314ef22f29768132dff2acf45914ea84
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 08/06/2021
ms.locfileid: "115992174"
---
# <a name="cart-resources"></a>Winkelwagenresources

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Een partner plaatst een bestelling wanneer een klant een abonnement wil kopen in een lijst met aanbiedingen.

## <a name="cart"></a>Winkelwagen

Beschrijft een winkelwagen.

| Eigenschap              | Type             | Beschrijving                                                                                            |
|-----------------------|------------------|--------------------------------------------------------------------------------------------------------|
| id                    | tekenreeks           | Een winkelwagen-id die wordt opgegeven wanneer de winkelwagen is gemaakt.                               |
| creationTimeStamp     | DateTime         | De datum waarop de winkelwagen is gemaakt, in datum/tijd-indeling. Toegepast wanneer de winkelwagen is gemaakt.      |
| lastModifiedTimeStamp | DateTime         | De datum waarop de winkelwagen het laatst is bijgewerkt, in datum/tijd-indeling. Toegepast wanneer de winkelwagen is gemaakt. |
| expirationTimeStamp   | DateTime         | De datum waarop de winkelwagen verloopt, in datum/tijd-indeling. Toegepast nadat de winkelwagen is gemaakt.          |
| lastModifiedUser      | tekenreeks           | De gebruiker die de winkelwagen voor het laatst heeft bijgewerkt. Toegepast nadat de winkelwagen is gemaakt.                          |
| lineItems             | Matrix met objecten | Een matrix van [CartLineItem-resources.](#cartlineitem)                                                   |
| status                | tekenreeks           | De status van de winkelwagen. Mogelijke waarden zijn 'Actief' (kan worden bijgewerkt/verzonden) en 'Besteld' (is al verzonden). |

## <a name="cartlineitem"></a>CartLineItem

Vertegenwoordigt één item in een winkelwagen.

| Eigenschap             | Type                             | Beschrijving                                                                                                                                           |
|----------------------|----------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                           | Een unieke id voor een winkelwagenregelitem. Toegepast nadat de winkelwagen is gemaakt.                                                                   |
| catalogItemId        | tekenreeks                           | De id van het catalogusitem.                                                                                                                          |
| Friendlyname         | tekenreeks                           | Optioneel. De gebruiksvriendelijke naam voor het item dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.                                                                 |
| quantity             | int                              | Het aantal licenties of exemplaren.                                                                                                                  |
| currencyCode         | tekenreeks                           | De valutacode.                                                                                                                                    |
| billingCycle         | Object                           | Het type factureringscyclus dat is ingesteld voor de huidige periode.                                                                                                 |
| termDuration         | tekenreeks                           | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn P1M (1 maand), P1Y (1 jaar) en P3Y (3 jaar).                                |
| deelnemers         | Lijst met objectreeksparen      | Een verzameling PartnerId on Record (MPN-id) voor de aankoop.                                                                                          |
| provisioningContext  | Woordenlijst<tekenreeks, tekenreeks>       | Aanvullende context die wordt gebruikt bij het inrichten van het gekochte item. Als u wilt bepalen welke waarden nodig zijn voor een bepaald item, raadpleegt u de eigenschap provisioningVariables van de SKU. |
| orderGroup           | tekenreeks                           | Een groep om aan te geven welke items samen in dezelfde volgorde kunnen worden verzonden.                                                                          |
| addonItems           | Lijst met **CartLineItem-objecten** | Een verzameling winkelwagenregelitems voor addons. Deze items worden aangeschaft voor het basisabonnement dat het resultaat is van de aankoop van het regelitem van de hoofdwagen. |
| fout                | Object                           | Toegepast nadat de winkelwagen is gemaakt als er een fout is opgetreden.                                                                                                    |
| renewsTo             | Matrix met objecten                 | Een matrix van [RenewsTo-resources.](#renewsto)                                                                            |
| AttestationAccepted             | booleaans                 | Geeft aan dat u akkoord gaat met de aanbieding of SKU-voorwaarden. Alleen vereist voor aanbiedingen of SKU's waarbij SkuAttestationProperties of OfferAttestationProperties afdwingenAttestation true is.                                                                            |

## <a name="renewsto"></a>RenewsTo

Vertegenwoordigt één item in een winkelwagenregelitem.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | tekenreeks           | No              | Een ISO 8601-weergave van de duur van de verlengingstermijn. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar). |

### <a name="response-success-and-error-codes"></a>Antwoord geslaagd en foutcodes

Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing. Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen. Zie voor de volledige lijst Partner Center [foutcodes.](error-codes.md)

## <a name="carterror"></a>CartError

Vertegenwoordigt een fout die optreedt nadat een winkelwagen is gemaakt.

| Eigenschap         | Type                                   | Description                                                                                   |
|------------------|----------------------------------------|-----------------------------------------------------------------------------------------------|
| errorCode        | [CareErrorCode](#carterrorcode) | Het type winkelwagenfout.                                                                       |
| errorDescription | tekenreeks                                 | De foutbeschrijving, inclusief eventuele opmerkingen over ondersteunde waarden, standaardwaarden of limieten. |


## <a name="carterrorcode"></a>CartErrorCode

Typen winkelwagenfouten.

| Name                             | ErrorCode   | Description
|----------------------------------|-------------|-----------------------------------------------------------------------------------------------|
| CurrencyIsNotSupported           | 10.000   | Valuta wordt niet ondersteund voor de opgegeven markt  |
| CatalogItemIdIsNotValid          | 10001   | Catalogusitem-id is ongeldig  |
| QuotaNiet beschikbaar                | 10002   | Onvoldoende quotum beschikbaar  |
| InventoryNotAvailable            | 10003   | Inventaris is niet beschikbaar voor geselecteerde aanbieding  |
| ParticipantsIsNotSupportedForPartner  | 10004   | Het instellen van deelnemers wordt niet ondersteund voor Partner  |
| UnableToProcessCartLineItem      | 10006   | Kan winkelwagenregelitem niet verwerken.  |
| SubscriptionIsNotValid           | 10007   | Het abonnement is ongeldig.  |
| SubscriptionIsNotEnabledForRI    | 10008   | Abonnement is niet ingeschakeld voor ri-aankoop.  |
| SandboxLimitExceeded             | 10009   | De sandboxlimiet is overschreden.  |
| InvalidInput                     | 10010   | Algemene invoer is ongeldig.  |
| SubscriptionNotRegistered        | 10011   | Het abonnement is ongeldig.  |
| AttestationNotAccepted           | 10012   | Attestation is niet geaccepteerd.  |
| Onbekend                          | 0   | Standaardwaarde   |

## <a name="cartcheckoutresult"></a>CartCheckoutResult

Vertegenwoordigt het resultaat van het uitchecken van een winkelwagen.

| Eigenschap    | Type                                              | Description                     |
|-------------|---------------------------------------------------|---------------------------------|
| orders      | Lijst met [orderobjecten.](order-resources.md#order)         | De verzameling orders.       |
| orderErrors | Lijst met [OrderError-objecten.](#ordererror) | De verzameling orderfouten. |

## <a name="ordererror"></a>OrderError

Vertegenwoordigt een fout die optreedt tijdens het uitchecken van een winkelwagen wanneer een order wordt gemaakt.

| Eigenschap     | Type   | Description                                     |
|--------------|--------|-------------------------------------------------|
| orderGroupId | tekenreeks | De ordergroep-id van de order met de fout . |
| code         | int    | De foutcode.                                 |
| beschrijving  | tekenreeks | De beschrijving van de fout.                   |
