---
title: Resources best Ellen
description: Een partner plaatst een bestelling wanneer een klant een abonnement wil kopen vanuit een lijst met aanbiedingen.
ms.date: 07/12/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9db07337a98214b4aaa93e2c8b43b84702249b77
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767338"
---
# <a name="order-resources"></a>Resources best Ellen

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Een partner plaatst een bestelling wanneer een klant een abonnement wil kopen vanuit een lijst met aanbiedingen.

>[!NOTE]
>De order resource heeft een frequentie limiet van 500 aanvragen per minuut per Tenant-id.

## <a name="order"></a>Volgorde

Beschrijft de volg orde van de partner.

| Eigenschap           | Type                                               | Beschrijving                                                 |
|--------------------|----------------------------------------------------|-------------------------------------------------------------|
| id                 | tekenreeks                                             | Een order-id die wordt geleverd bij het maken van de order.                                   |
| alternateId        | tekenreeks                                             | Een beschrijvende id voor de order.                                                                          |
|referenceCustomerId | tekenreeks                                             | De klant-id. |
| billingCycle       | tekenreeks                                             | Hiermee wordt de frequentie aangegeven waarmee de partner voor deze order wordt gefactureerd. Ondersteunde waarden zijn de lidnamen in [BillingCycleType](product-resources.md#billingcycletype). De standaard waarde is ' maandelijks ' of ' eenmalige ' bij het maken van de order. Dit veld wordt toegepast bij het maken van de order. |
| transactionType    | tekenreeks                                             | Alleen-lezen. Het transactie type van de order. Ondersteunde waarden zijn ' UserPurchase ', ' SystemPurchase ' of ' SystemBilling ' |
| Regel items          | matrix van [OrderLineItem](#orderlineitem) -resources | Een gespecificeerde lijst met de aanbiedingen die de klant koopt, met inbegrip van de hoeveelheid.        |
| currencyCode       | tekenreeks                                             | Alleen-lezen. De valuta die wordt gebruikt bij het plaatsen van de order. Wordt toegepast bij het maken van de order.           |
| currencySymbol     | tekenreeks                                             | Alleen-lezen. Het valuta symbool dat is gekoppeld aan de valuta code. |
| creationDate       | datum/tijd                                           | Alleen-lezen. De datum waarop de order is gemaakt, in datum-tijd notatie. Wordt toegepast bij het maken van de order.                                   |
| status             | tekenreeks                                             | Alleen-lezen. De status van de order.  Ondersteunde waarden zijn de lidnamen in [**OrderStatus**](#orderstatus).        |
| koppelen              | [OrderLinks](utility-resources.md#resourcelinks)           | De resource koppelingen die overeenkomen met de volg orde.            |
| kenmerken         | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met de volg orde.       |

## <a name="orderlineitem"></a>OrderLineItem

Een order bevat een gespecificeerde lijst met aanbiedingen en elk item wordt weer gegeven als een OrderLineItem.

| Eigenschap             | Type                                      | Description                                                                                                                                                                                                                                |
|----------------------|-------------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| lineItemNumber       | int                                       | Elk regel item in de verzameling krijgt een uniek regel nummer, geteld van 0 tot aantal-1.                                                                                                                                                 |
| offerId              | tekenreeks                                    | De ID van de aanbieding.                                                                                                                                                                                                                       |
| subscriptionId       | tekenreeks                                    | De ID van het abonnement.                                                                                                                                                                                                                |
| parentSubscriptionId | tekenreeks                                    | Optioneel. De ID van het bovenliggende abonnement in een invoeg toepassing. Is alleen van toepassing op PATCH.                                                                                                                                                     |
| friendlyName         | tekenreeks                                    | Optioneel. De beschrijvende naam voor het abonnement dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.                                                                                                                                              |
| quantity             | int                                       | Het aantal licenties of exemplaren.                                                                                                                                                                                |
| termDuration         | tekenreeks                                    | Een ISO 8601-representatie van de duur van de term. De huidige ondersteunde waarden zijn **P1M** (1 maand), **P1Y** (1 jaar) en **P3Y** (3 jaar).                               |
| transactionType      | tekenreeks                                    | Alleen-lezen. Het transactie type van het regel item. Ondersteunde waarden zijn ' New ', ' renew ', ' addQuantity ', ' removeQuantity ', ' Cancel ', ' Convert ' of ' customerCredit '. |
| partnerIdOnRecord    | tekenreeks                                    | Wanneer een indirecte provider een bestelling namens een indirecte wederverkoper plaatst, vult u dit veld alleen met de MPN-ID van de **indirecte wederverkoper** (nooit de id van de indirecte provider). Dit zorgt voor een goede administratieve verwerking van prikkels. |
| provisioningContext  | Dictionary<teken reeks, teken reeks>            | Informatie die is vereist voor het inrichten van sommige items in de catalogus. De eigenschap provisioningVariables in een SKU geeft aan welke eigenschappen vereist zijn voor specifieke items in de catalogus.                                                                                                                                               |
| koppelen                | [OrderLineItemLinks](#orderlineitemlinks) | Alleen-lezen. De resource koppelingen die overeenkomen met het order regel item.                                                                                                                                                                                |
| renewsTo             | [RenewsTo](#renewsto)                         |Duur Details van de verlengings termijn.                                                                           |

## <a name="renewsto"></a>RenewsTo

Vertegenwoordigt de duur Details van de verlengings periode.

| Eigenschap              | Type             | Vereist        | Beschrijving |
|-----------------------|------------------|-----------------|-------------------------------------------------------------------------------------------------------------------------|
| termDuration          | tekenreeks           | No              | Een ISO 8601-representatie van de duur van de verlengings termijn. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar). |

## <a name="orderlinks"></a>OrderLinks

Hiermee worden de resource koppelingen aangeduid die overeenkomen met de volg orde.

| Eigenschap           | Type                                         | Description                                                                   |
|--------------------|----------------------------------------------|-------------------------------------------------------------------------------|
| provisioningStatus | [Koppeling](utility-resources.md#link)            | Bij het invullen wordt de koppeling voor het ophalen van de inrichtings status voor de order opgehaald.       |
| Online               | [Koppeling](utility-resources.md#link)            | De koppeling om de order resource op te halen.                                      |

## <a name="orderlineitemlinks"></a>OrderLineItemLinks

Hiermee geeft u het volledige abonnement dat is gekoppeld aan de order.

| Eigenschap           | Type                                         | Description                                                                          |
|--------------------|----------------------------------------------|--------------------------------------------------------------------------------------|
| provisioningStatus | [Koppeling](utility-resources.md#link)            | Bij het invullen van de koppeling om de [inrichtings status](#orderlineitemprovisioningstatus) van het regel item op te halen.       |
| sku                | [Koppeling](utility-resources.md#link)            | De koppeling om de SKU-informatie voor het gekochte catalogus item op te halen.                    |
| abonnement       | [Koppeling](utility-resources.md#link)            | De koppeling naar de volledige abonnements gegevens wanneer deze is ingevuld.                       |
| activationLinks    | [Koppeling](utility-resources.md#link)            | De GET-resource voor koppelingen om het abonnement te activeren wanneer deze is ingevuld.             |

## <a name="orderstatus"></a>OrderStatus

Een [Enum/DotNet/API/System. enum) met waarden die de status van de order aangeven.

| Waarde              | Positie     | Description                                     |
|--------------------|--------------|-------------------------------------------------|
| unknown            | 0            | Enum-initialisatie functie.                               |
| gevuld          | 1            | Geeft aan dat de order is voltooid.          |
| in behandeling            | 2            | Geeft aan dat de order nog in behandeling is.      |
| gevraagd          | 3            | Geeft aan dat de order is geannuleerd.    |

## <a name="orderlineitemprovisioningstatus"></a>OrderLineItemProvisioningStatus

Hiermee wordt de inrichtings status van een [OrderLineItem](#orderlineitem)aangeduid.

| Eigenschap                        | Type                                | Description                                                                                |
|------------------------------------|-------------------------------------|--------------------------------------------------------------------------------------------|
| lineItemNumber                  | int                                 | Het unieke regel nummer van het order regel item. De waarden variëren van 0 tot het aantal-1.             |
| status                          | tekenreeks                              | De inrichtings status van het order regel item. De waarden zijn:</br>' Vervuld ': de volg orde van de bestelling is voltooid en de gebruiker kan de reserve ringen gebruiken</br>Niet voldaan: niet voldaan door annulering</br>"PrefulfillmentPending": uw aanvraag wordt verwerkt, de uitvoering is nog niet voltooid |
| quantityProvisioningInformation | <[QuantityProvisioningStatus](#quantityprovisioningstatus) weer geven> | Een lijst met de informatie over het inrichten van de hoeveelheid voor het order regel item. |

## <a name="quantityprovisioningstatus"></a>QuantityProvisioningStatus

Hiermee wordt de inrichtings status op hoeveelheid aangegeven.

| Eigenschap                           | Type                                         | Description                                          |
|------------------------------------|----------------------------------------------|------------------------------------------------------|
| quantity                           | int                                          | Het aantal items.                                 |
| status                             | tekenreeks                                       | De status van het aantal items.                   |
