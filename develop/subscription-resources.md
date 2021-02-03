---
title: Abonnements resources
description: Abonnements bronnen kunnen gedurende de hele levens cyclus meer informatie geven over abonnementen, zoals ondersteuning, restituties en Azure-rechten.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: fd835e46e99b1fcb1e0b0e694ad73b1dca1240c9
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767249"
---
# <a name="subscription-resources"></a>Abonnements resources

**Van toepassing op:**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Met een abonnement kan een klant een service voor een bepaalde periode gebruiken. Niet alle velden zijn van toepassing op alle abonnementen. Veel velden zijn alleen van toepassing op bepaalde punten in de levens cyclus, bijvoorbeeld als een abonnement wordt geschorst of geannuleerd.

## <a name="subscription"></a>Abonnement

>[!NOTE]
>De resource van het **abonnement** heeft een frequentie limiet van 500 aanvragen per minuut per Tenant-id.

De resource van het **abonnement** vertegenwoordigt de levens cyclus van een abonnement en bevat eigenschappen die de statussen tijdens de levens cyclus van het abonnement definiëren.

| Eigenschap             | Type                                                          | Beschrijving                                                                                                                                                                   |
|----------------------|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                                                        | De abonnements-id.                                                                                                                                                  |
| offerId              | tekenreeks                                                        | De aanbiedings-id.                                                                                                                                                         |
| entitlementId        | tekenreeks                                                        | De rechten-id (een Azure-abonnement-ID).                                                                                                                        |
| offerName            | tekenreeks                                                        | De naam van de aanbieding.                                                                                                                                                               |
| friendlyName         | tekenreeks                                                        | De beschrijvende naam voor het abonnement dat is gedefinieerd door de partner om dubbel zinnigheid te helpen.                                                                                           |
| quantity             | getal                                                        | De hoeveelheid. In het geval van facturering op basis van een licentie wordt deze eigenschap bijvoorbeeld ingesteld op het aantal licenties.                                                            |
| Unit type             | tekenreeks                                                        | De eenheden voor het definiëren van de hoeveelheid voor het abonnement.                                                                                                                             |
| parentSubscriptionId | tekenreeks                                                        | Hiermee wordt de id van het bovenliggende abonnement opgehaald of ingesteld.                                                                                                                              |
| creationDate         | tekenreeks                                                        | Hiermee wordt de aanmaak datum in datum-tijd notatie opgehaald of ingesteld.                                                                                                                          |
| effectiveStartDate   | teken reeks in UTC-datum tijd notatie                                | Hiermee wordt de ingangs datum voor dit abonnement opgehaald of ingesteld, in datum-tijd notatie. De back-up wordt gebruikt om een gemigreerd abonnement te maken of om het te uitlijnen met een andere.                |
| commitmentEndDate    | teken reeks in UTC-datum tijd notatie                                | De eind datum van de toezeg ging voor dit abonnement, in datum-tijd notatie. Voor abonnementen die niet automatisch worden verlengd, is dit een datum die ver in de toekomst ligt.       |
| status               | tekenreeks                                                        | De abonnements status: ' none ', ' Active ', ' pending ', ' Suspended ' of ' deleted '.                                                                                                         |
| autoRenewEnabled     | booleaans                                                       | Haalt een waarde op die aangeeft of het abonnement automatisch wordt vernieuwd.                                                                                                    |
| billingType          | tekenreeks                                                        | Hiermee geeft u op hoe het abonnement wordt gefactureerd: ' none ', ' usage ' of ' License '.                                                                                                      |
| billingCycle         | tekenreeks                                                        | Hiermee wordt de frequentie aangegeven waarmee de partner voor deze order wordt gefactureerd. Ondersteunde waarden zijn de lidnamen in [**BillingCycleType**](product-resources.md#billingcycletype). |
| hasPurchasableAddons | booleaans                                                       | Hiermee wordt een waarde opgehaald of ingesteld waarmee wordt aangegeven of het abonnement tevens-invoeg toepassingen bevat.                                                                                             |
| isTrial              | booleaans                                                       | Een waarde die aangeeft of dit een proef abonnement is.                                                                                                                      |
| isMicrosoftProduct   | booleaans                                                       | Een waarde die aangeeft of dit een micro soft-product is.                                                                                                                       |
| publisherName        | tekenreeks                                                        | De naam van de uitgever.                                                                                                                                                           |
| acties              | tekenreeksmatrix                                              | Hiermee worden de toegestane acties opgehaald of ingesteld. Mogelijke waarden: ' bewerken ', ' annuleren '                                                                                                  |
| Partner            | tekenreeks                                                        | De MPN-ID van de wederverkoper van de record die wordt gebruikt in het indirecte partner model.                                                                                                     |
| suspensionReasons    | tekenreeksmatrix                                              | Alleen-lezen. Als het abonnement is onderbroken, geeft dit aan waarom.                                                                                                                  |
| contractType         | tekenreeks                                                        | Alleen-lezen. Het type contract: ' abonnement ', ' productKey ' of ' redemptionCode '.                                                                                           |
| refundOptions        | matrix van [RefundOption](#refundoption) -resources   | Alleen-lezen. De set met opties voor restitutie die beschikbaar zijn voor dit abonnement.                                                                                              |
| koppelen                | [SubscriptionLinks](#subscriptionlinks)                       | Hiermee worden de abonnements koppelingen opgehaald of ingesteld.                                                                                                                                          |
| Velden              | tekenreeks                                                        | De ID van de order die is geplaatst om het abonnement te starten.                                                                                                                |
| termDuration         | tekenreeks                                                        | Een ISO 8601-representatie van de duur van de term. De huidige ondersteunde waarden zijn **P1M** (1 maand), **P1Y** (1 jaar) en **P3Y** (3 jaar).                                                        |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met het abonnement.                                                                                                                    |
| renewalTermDuration  | tekenreeks                                                        | Een ISO 8601-representatie van de duur van de term. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar).                                                        |

## <a name="subscriptionlinks"></a>SubscriptionLinks

De **SubscriptionLinks** -resource beschrijft de verzameling koppelingen die aan een abonnements resource is gekoppeld.

| Eigenschap           | Type                               | Description                           |
|--------------------|------------------------------------|---------------------------------------|
| offer              | [Koppeling](utility-resources.md#link) | Hiermee wordt de aanbieding opgehaald of ingesteld.               |
| parentSubscription | [Koppeling](utility-resources.md#link) | Hiermee wordt het bovenliggende abonnement opgehaald of ingesteld. |
| product            | [Koppeling](utility-resources.md#link) | Hiermee wordt het product opgehaald dat is gekoppeld aan het abonnement. |
| sku                | [Koppeling](utility-resources.md#link) | Hiermee wordt de product-SKU opgehaald die aan het abonnement is gekoppeld. |
| availability       | [Koppeling](utility-resources.md#link) | Hiermee haalt u de product-SKU Beschik baarheid die aan het abonnement is gekoppeld. |
| activationLinks    | [Koppeling](utility-resources.md#link) | Hiermee haalt u de lijst met activerings koppelingen op die zijn gekoppeld aan het abonnement. |
| Online               | [Koppeling](utility-resources.md#link) | De zelf-URI.                         |
| volgende               | [Koppeling](utility-resources.md#link) | De volgende pagina met items.               |
| bestaande           | [Koppeling](utility-resources.md#link) | De vorige pagina met items.           |

## <a name="subscriptionprovisioningstatus"></a>SubscriptionProvisioningStatus

De **SubscriptionProvisioningStatus** -resource bevat informatie over de inrichtings status van een abonnement.

| Eigenschap   | Type                                                           | Description                                                          |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------|
| skuId      | tekenreeks                                                         | Een teken reeks met een GUID-indeling waarmee de product-SKU wordt geïdentificeerd.             |
| status     | tekenreeks                                                         | Hiermee wordt de inrichtings status aangegeven: "geslaagd", "in behandeling" of "mislukt". |
| quantity   | getal                                                         | Geeft het aantal abonnementen na inrichting.               |
| endDate    | teken reeks in UTC-datum tijd notatie                                 | De eind datum van het abonnement.                                    |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes)  | De meta gegevens kenmerken.                                             |

## <a name="subscriptionregistrationstatus"></a>SubscriptionRegistrationStatus

De **SubscriptionRegistrationStatus** -resource beschrijft de verzameling koppelingen die aan een abonnements resource is gekoppeld.

| Eigenschap           | Type                               | Description                                                                           |
|--------------------|------------------------------------|---------------------------------------------------------------------------------------|
| subscriptionId     | tekenreeks                             | De abonnements-id.                                                          |
| status             | tekenreeks                             | Hiermee wordt de registratie status aangegeven: ' geregistreerd ', ' registratie ' of ' notregistered '.    |

## <a name="supportcontact"></a>SupportContact

De **SupportContact** -resource vertegenwoordigt een ondersteunings contact voor het abonnement van een klant.

| Eigenschap        | Type                                                           | Description                                                                     |
|-----------------|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| supportTenantId | tekenreeks                                                         | Een teken reeks met een GUID-indeling die de Tenant-id van de ondersteunings contact persoon aangeeft. |
| supportMpnId    | tekenreeks                                                         | De id van de Microsoft Partner Network van de contact persoon (MPN).                       |
| naam            | tekenreeks                                                         | De naam van de contact persoon voor ondersteuning.                                                |
| koppelen           | [ResourceLinks](utility-resources.md#resourcelinks)            | Het ondersteunings contact met verwante koppelingen.                                              |
| kenmerken      | [ResourceAttributes](utility-resources.md#resourceattributes)  | De meta gegevens kenmerken. Bevat "object type": "SupportContact".              |

## <a name="registersubscription"></a>RegisterSubscription

De **RegisterSubscription** -resource retourneert een koppeling die kan worden gebruikt om de registratie status van een abonnement op te vragen. De registratie status wordt geretourneerd in de antwoord tekst van een geslaagde aanvraag om een Azure-abonnement te registreren.

| Eigenschap                | Type                               | Description                                                                           |
|-------------------------|------------------------------------|---------------------------------------------------------------------------------------|
| httpResponseMessage     | object                             | Retourneert HTTP-status code 202 ' accepted ', met een locatie header met een koppeling om de registratie status op te vragen. Bijvoorbeeld: `"/customers/{customer-id}/subscriptions/{subscription-id}/registrationstatus"` |

## <a name="refundoption"></a>RefundOption

De **RefundOption** -resource vertegenwoordigt een mogelijke terugbetalings optie voor het abonnement.

| Eigenschap          | Type | Beschrijving                                                                         |
|-------------------|--------|-------------------------------------------------------------------------------------|
| type | tekenreeks | Het type restitutie. De ondersteunde waarden zijn ' gedeeltelijk ' en ' volledig ' |
| expiresAfter      | teken reeks in UTC-datum tijd notatie | De tijds tempel wanneer deze optie verloopt. Als deze null is, betekent dit dat er geen verval datum is. |

## <a name="azureentitlement"></a>AzureEntitlement

De resource **AzureEntitlement** vertegenwoordigt de Azure-rechten voor het abonnement.

| Eigenschap          | Type | Beschrijving                                                                         |
|-------------------|--------|-------------------------------------------------------------------------------------|
| id | tekenreeks | De rechtse-id |
| friendlyName      | tekenreeks | De beschrijvende naam van het recht. |
| status | tekenreeks | De status van recht. |
| subscriptionId | tekenreeks | De abonnements-id waarvan het recht deel uitmaakt. |
