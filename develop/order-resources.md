---
title: Resources bestellen
description: Een partner plaatst een bestelling wanneer een klant een abonnement wil kopen in een lijst met aanbiedingen.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 128c9e041cacc1c15f6187c4d99690d5c5fa4183
ms.sourcegitcommit: 59950cf131440786779c8926be518c2dc4bc4030
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/31/2021
ms.locfileid: "115009166"
---
# <a name="order-resources"></a>Resources bestellen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Een partner plaatst een bestelling wanneer een klant een abonnement wil kopen in een lijst met aanbiedingen.

>[!NOTE]
>De resource Order heeft een snelheidslimiet van 500 aanvragen per minuut per tenant-id.

## <a name="order"></a>Volgorde

Beschrijft de volgorde van een partner.

| Eigenschap           | Type                                               | Beschrijving                                                 |
|--------------------|----------------------------------------------------|-------------------------------------------------------------|
| id                 | tekenreeks                                             | Een order-id die wordt opgegeven wanneer de order is gemaakt.                                   |
| alternateId        | tekenreeks                                             | Een gebruiksvriendelijke id voor de bestelling.                                                                          |
|referenceCustomerId | tekenreeks                                             | De klant-id. |
| billingCycle       | tekenreeks                                             | Geeft de frequentie aan waarmee de partner wordt gefactureerd voor deze bestelling. Ondersteunde waarden zijn de ledennamen in [BillingCycleType.](product-resources.md#billingcycletype) De standaardwaarde is 'Maandelijks' of 'OneTime' bij het maken van de order. Dit veld wordt toegepast wanneer de order is gemaakt. |
| transactionType    | tekenreeks                                             | Alleen-lezen. Het transactietype van de order. Ondersteunde waarden zijn 'UserPurchase', 'SystemPurchase' of 'SystemBilling' |
| lineItems          | matrix van [OrderLineItem-resources](#orderlineitem) | Een gespecificeerde lijst van de aanbiedingen die de klant aanschaft, inclusief de hoeveelheid.        |
| currencyCode       | tekenreeks                                             | Alleen-lezen. De valuta die wordt gebruikt bij het plaatsen van de order. Toegepast wanneer de order is gemaakt.           |
| currencySymbol     | tekenreeks                                             | Alleen-lezen. Het valutasymbool dat is gekoppeld aan de valutacode. |
| creationDate       | datum/tijd                                           | Alleen-lezen. De datum waarop de order is gemaakt, in datum/tijd-indeling. Toegepast wanneer de order is gemaakt.                                   |
| status             | tekenreeks                                             | Alleen-lezen. De status van de bestelling.  Ondersteunde waarden zijn de ledennamen in [**OrderStatus**](#orderstatus).        |
| Verwijzigingen              | [OrderLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen die overeenkomen met de Order.            |
| kenmerken         | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met de Order.       |

## <a name="orderlineitem"></a>OrderLineItem

Een order bevat een gespecificeerde lijst met aanbiedingen en elk item wordt weergegeven als een OrderLineItem.

| Eigenschap             | Type                                      | Beschrijving                                                                                                                                                                                                                                |
|----------------------|-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| lineItemNumber       | int                                       | Elk regelitem in de verzameling krijgt een uniek regelnummer, dat wordt geteld van 0 tot count-1.                                                                                                                                                 |
| offerId              | tekenreeks                                    | De id van de aanbieding.                                                                                                                                                                                                                       |
| subscriptionId       | tekenreeks                                    | De id van het abonnement.                                                                                                                                                                                                                |
| parentSubscriptionId | tekenreeks                                    | Optioneel. De id van het bovenliggende abonnement in een invoegaanbieding. Alleen van toepassing op PATCH.                                                                                                                                                     |
| Friendlyname         | tekenreeks                                    | Optioneel. De gebruiksvriendelijke naam voor het abonnement dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.                                                                                                                                              |
| quantity             | int                                       | Het aantal licenties of exemplaren.                                                                                                                                                                                |
| termDuration         | tekenreeks                                    | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn **P1M** (1 maand), **P1Y** (1 jaar) en **P3Y** (3 jaar).                               |
| transactionType      | tekenreeks                                    | Alleen-lezen. Het transactietype van het regelitem. Ondersteunde waarden zijn 'new', 'renew', 'addQuantity', 'removeQuantity', 'cancel', 'convert' of 'customerCredit'. |
| partnerIdOnRecord    | tekenreeks                                    | Wanneer een indirecte provider een order plaatst namens een indirecte reseller, vult u dit veld in met de MPN-id van alleen de **indirecte reseller** (nooit de id van de indirecte provider). Dit zorgt voor een juiste boekhouding voor incentives. |
| provisioningContext  | Woordenlijst<tekenreeks, tekenreeks>            | Informatie die vereist is voor het inrichten van sommige items in de catalogus. De eigenschap provisioningVariables in een SKU geeft aan welke eigenschappen vereist zijn voor specifieke items in de catalogus.                                                                                                                                               |
| Verwijzigingen                | [OrderLineItemLinks](#orderlineitemlinks) | Alleen-lezen. De resourcekoppelingen die overeenkomen met het orderregelitem.                                                                                                                                                                                |
| renewsTo             | [RenewsTo](#renewsto)                         |Details van de duur van de verlengingsperiode.                                                                           |
| AttestationAccepted             | booleaans                 | Geeft aan dat u akkoord gaat met de aanbieding of SKU-voorwaarden. Alleen vereist voor aanbiedingen of SKU's waarbij SkuAttestationProperties of OfferAttestationProperties afdwingenAttestation true is.                                                                            |

## <a name="renewsto"></a>RenewsTo

Vertegenwoordigt de details van de duur van de verlengingstermijn.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | tekenreeks           | No              | Een ISO 8601-weergave van de duur van de verlengingstermijn. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar). |

## <a name="orderlinks"></a>OrderLinks

Vertegenwoordigt de resourcekoppelingen die overeenkomen met de bestelling.

| Eigenschap           | Type                                         | Beschrijving                                                                   |
|--------------------|----------------------------------------------|-------------------------------------------------------------------------------|
| provisioningStatus | [Koppeling](utility-resources.md#link)            | Wanneer deze is ingevuld, wordt de koppeling voor het ophalen van de inrichtingsstatus voor de order opgehaald.       |
| Zelf               | [Koppeling](utility-resources.md#link)            | De koppeling om de orderresource op te halen.                                      |

## <a name="orderlineitemlinks"></a>OrderLineItemLinks

Vertegenwoordigt het volledige abonnement dat is gekoppeld aan de order.

| Eigenschap           | Type                                         | Beschrijving                                                                          |
|--------------------|----------------------------------------------|--------------------------------------------------------------------------------------|
| provisioningStatus | [Koppeling](utility-resources.md#link)            | Wanneer deze is ingevuld, wordt de koppeling voor het ophalen [van de inrichtingsstatus van](#orderlineitemprovisioningstatus) het regelitem opgehaald.       |
| sku                | [Koppeling](utility-resources.md#link)            | De koppeling voor het ophalen van SKU-gegevens voor het gekochte catalogusitem.                    |
| abonnement       | [Koppeling](utility-resources.md#link)            | Wanneer deze is ingevuld, wordt de koppeling naar de volledige abonnementsgegevens ingevuld.                       |
| activationLinks    | [Koppeling](utility-resources.md#link)            | Wanneer deze is ingevuld, wordt de GET-resource gebruikt voor koppelingen om het abonnement te activeren.             |

## <a name="orderstatus"></a>OrderStatus

Een [Enum/dotnet/api/system.enum) met waarden die de status van de bestelling aangeven.

| Waarde              | Positie     | Beschrijving                                     |
|--------------------|--------------|-------------------------------------------------|
| unknown            | 0            | Enum initializer.                               |
| Voltooid          | 1            | Geeft aan dat de order is voltooid.          |
| in behandeling            | 2            | Geeft aan dat de order nog steeds in behandeling is.      |
| Geannuleerd          | 3            | Geeft aan dat de order is geannuleerd.    |

## <a name="orderlineitemprovisioningstatus"></a>OrderLineItemProvisioningStatus

Vertegenwoordigt de inrichtingsstatus van een [OrderLineItem.](#orderlineitem)

| Eigenschap                        | Type                                | Beschrijving                                                                                |
|------------------------------------|-------------------------------------|--------------------------------------------------------------------------------------------|
| lineItemNumber                  | int                                 | Het unieke regelnummer van het orderregelitem. Waarden variëren van 0 tot count-1.             |
| status                          | tekenreeks                              | De inrichtingsstatus van het orderregelitem. De waarden zijn:</br>**Voltooid:** de order is voltooid en de gebruiker kan de reserveringen gebruiken</br>**Niet-voltooid:** niet voltooid vanwege annulering</br>**PrefulfillmentPending:** Uw aanvraag wordt nog verwerkt, de uitvoering is nog niet voltooid |
| quantityProvisioningInformation | Lijst<[QuantityProvisioningStatus](#quantityprovisioningstatus)> | Een lijst met informatie over de inrichtingsstatus van de hoeveelheid voor het orderregelitem. |

## <a name="quantityprovisioningstatus"></a>QuantityProvisioningStatus

Vertegenwoordigt de inrichtingsstatus per hoeveelheid.

| Eigenschap                           | Type                                         | Beschrijving                                          |
|------------------------------------|----------------------------------------------|------------------------------------------------------|
| quantity                           | int                                          | Het aantal items.                                 |
| status                             | tekenreeks                                       | De status van het aantal items.                   |
