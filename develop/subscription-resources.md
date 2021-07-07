---
title: Abonnementsbronnen
description: Abonnementsresources kunnen gedurende de hele levenscyclus meer informatie bieden over abonnementen, zoals ondersteuning, restituties en Azure-rechten.
ms.date: 11/01/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 35d8c86ab061797109b3c152eff02f354b7ea23a
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547447"
---
# <a name="subscription-resources"></a>Abonnementsbronnen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Met een abonnement kan een klant een service voor een bepaalde periode gebruiken. Niet alle velden zijn van toepassing op alle abonnementen. Veel velden zijn alleen van toepassing op bepaalde punten in de levenscyclus, bijvoorbeeld wanneer een abonnement wordt opgeschort of geannuleerd.

## <a name="subscription"></a>Abonnement

>[!NOTE]
>De **abonnementsresource** heeft een snelheidslimiet van 500 aanvragen per minuut per tenant-id.

De **abonnementsresource** vertegenwoordigt de levenscyclus van een abonnement en bevat eigenschappen die de staten gedurende de levenscyclus van het abonnement definiëren.

| Eigenschap             | Type                                                          | Beschrijving                                                                                                                                                                   |
|----------------------|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| id                   | tekenreeks                                                        | De abonnements-id.                                                                                                                                                  |
| offerId              | tekenreeks                                                        | De aanbiedings-id.                                                                                                                                                         |
| entitlementId        | tekenreeks                                                        | De rechten-id (een Azure-abonnements-id).                                                                                                                        |
| offerName            | tekenreeks                                                        | De naam van de aanbieding.                                                                                                                                                               |
| Friendlyname         | tekenreeks                                                        | De gebruiksvriendelijke naam voor het abonnement dat is gedefinieerd door de partner om te helpen bij het op ondubbelzinnig maken.                                                                                           |
| quantity             | getal                                                        | De hoeveelheid. In het geval van facturering op basis van licenties is deze eigenschap bijvoorbeeld ingesteld op het aantal licenties.                                                            |
| unitType             | tekenreeks                                                        | De eenheden die de hoeveelheid voor het abonnement definiëren.                                                                                                                             |
| parentSubscriptionId | tekenreeks                                                        | Hiermee haalt u de bovenliggende abonnements-id op of stelt u deze in.                                                                                                                              |
| creationDate         | tekenreeks                                                        | Hiermee haalt u de aanmaakdatum op of stelt u deze in datum-/tijdnotatie in.                                                                                                                          |
| effectiveStartDate   | tekenreeks in UTC-datum/tijd-indeling                                | Hiermee wordt de effectieve begindatum voor dit abonnement, in datum/tijd-indeling, op halen of in stellen. Het wordt gebruikt om een gemigreerd abonnement van een back-up te maken of om het uit te lijnen met een ander abonnement.                |
| commitmentEndDate    | tekenreeks in UTC-datum/tijd-indeling                                | De einddatum van de toezegging voor dit abonnement, in datum/tijd-indeling. Voor abonnementen die niet automatisch kunnen worden verlengd, vertegenwoordigt dit een datum die in de toekomst ver weg is.       |
| status               | tekenreeks                                                        | De status van het abonnement: 'none', 'active', 'pending', 'suspended' of 'deleted'.                                                                                                         |
| autoRenewEnabled     | booleaans                                                       | Haalt een waarde op die aangeeft of het abonnement automatisch wordt verlengd.                                                                                                    |
| billingType          | tekenreeks                                                        | Hiermee geeft u op hoe het abonnement wordt gefactureerd: 'none', 'usage' of 'license'.                                                                                                      |
| billingCycle         | tekenreeks                                                        | Geeft de frequentie aan waarmee de partner wordt gefactureerd voor deze bestelling. Ondersteunde waarden zijn de ledennamen in [**BillingCycleType.**](product-resources.md#billingcycletype) |
| hasPurchasableAddons | booleaans                                                       | Hiermee haalt u een waarde op of stelt u in of geeft u aan of het abonnement opschatbare invoegtoepassingen heeft.                                                                                             |
| isTrial              | booleaans                                                       | Een waarde die aangeeft of dit een proefabonnement is.                                                                                                                      |
| isMicrosoftProduct   | booleaans                                                       | Een waarde die aangeeft of dit een Microsoft-product is.                                                                                                                       |
| publisherName        | tekenreeks                                                        | De naam van de uitgever.                                                                                                                                                           |
| acties              | tekenreeksmatrix                                              | Hiermee haalt u de acties op die zijn toegestaan of stelt u deze in. Mogelijke waarden: 'edit', 'cancel'                                                                                                  |
| partnerId            | tekenreeks                                                        | De MPN-id van de wederverkoper van de record, die wordt gebruikt in het model van de indirecte partner.                                                                                                     |
| suspensionReasons    | tekenreeksmatrix                                              | Alleen-lezen. Als het abonnement is opgeschort, wordt aangegeven waarom.                                                                                                                  |
| contractType         | tekenreeks                                                        | Alleen-lezen. Het type contract: 'abonnement', 'productKey' of 'redemptionCode'.                                                                                           |
| refundOptions        | matrix van [RefundOption-resources](#refundoption)   | Alleen-lezen. De set restitutieopties die beschikbaar zijn voor dit abonnement.                                                                                              |
| Verwijzigingen                | [SubscriptionLinks](#subscriptionlinks)                       | Hiermee haalt u de abonnementskoppelingen op of stelt u deze in.                                                                                                                                          |
| Orderid              | tekenreeks                                                        | De id van de bestelling die is geplaatst om het abonnement te starten.                                                                                                                |
| termDuration         | tekenreeks                                                        | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn **P1M** (1 maand), **P1Y** (1 jaar) en **P3Y** (3 jaar).                                                        |
| kenmerken           | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met het abonnement.                                                                                                                    |
| renewalTermDuration  | tekenreeks                                                        | Een ISO 8601-weergave van de duur van de term. De huidige ondersteunde waarden zijn **P1M** (1 maand) en **P1Y** (1 jaar).                                                        |

## <a name="subscriptionlinks"></a>SubscriptionLinks

De **SubscriptionLinks-resource** beschrijft de verzameling koppelingen die zijn gekoppeld aan een abonnementsresource.

| Eigenschap           | Type                               | Beschrijving                           |
|--------------------|------------------------------------|---------------------------------------|
| offer              | [Koppeling](utility-resources.md#link) | Hiermee haalt u de aanbieding op of stelt u deze in.               |
| parentSubscription | [Koppeling](utility-resources.md#link) | Haalt het bovenliggende abonnement op of stelt het in. |
| product            | [Koppeling](utility-resources.md#link) | Hiermee haalt u het product op dat is gekoppeld aan het abonnement. |
| sku                | [Koppeling](utility-resources.md#link) | Hiermee haalt u de product-SKU op die is gekoppeld aan het abonnement. |
| availability       | [Koppeling](utility-resources.md#link) | Hiermee haalt u de beschikbaarheid op van de product-SKU die is gekoppeld aan het abonnement. |
| activationLinks    | [Koppeling](utility-resources.md#link) | Hiermee haalt u de lijst met activeringskoppelingen op die zijn gekoppeld aan het abonnement. |
| Zelf               | [Koppeling](utility-resources.md#link) | De zelf-URI.                         |
| volgende               | [Koppeling](utility-resources.md#link) | De volgende pagina met items.               |
| Vorige           | [Koppeling](utility-resources.md#link) | De vorige pagina met items.           |

## <a name="subscriptionprovisioningstatus"></a>SubscriptionProvisioningStatus

De **resource SubscriptionProvisioningStatus** biedt informatie over de inrichtingsstatus van een abonnement.

| Eigenschap   | Type                                                           | Beschrijving                                                          |
|------------|----------------------------------------------------------------|----------------------------------------------------------------------|
| skuId      | tekenreeks                                                         | Een tekenreeks met GUID-indeling die de product-SKU identificeert.             |
| status     | tekenreeks                                                         | Geeft de inrichtingsstatus aan: 'geslaagd', 'in behandeling' of 'mislukt'. |
| quantity   | getal                                                         | Geeft de hoeveelheid van het abonnement weer na het inrichten.               |
| Enddate    | tekenreeks in UTC-datum/tijd-indeling                                 | De einddatum van het abonnement.                                    |
| kenmerken | [ResourceAttributes](utility-resources.md#resourceattributes)  | De metagegevenskenmerken.                                             |

## <a name="subscriptionregistrationstatus"></a>SubscriptionRegistrationStatus

De **resource SubscriptionRegistrationStatus** beschrijft de verzameling koppelingen die zijn gekoppeld aan een abonnementsresource.

| Eigenschap           | Type                               | Beschrijving                                                                           |
|--------------------|------------------------------------|---------------------------------------------------------------------------------------|
| subscriptionId     | tekenreeks                             | De abonnements-id.                                                          |
| status             | tekenreeks                             | Geeft de registratiestatus aan: 'geregistreerd', 'registreren' of 'niet geregistreerd'.    |

## <a name="supportcontact"></a>OndersteuningContact

De **resource SupportContact** vertegenwoordigt een contactpersoon voor ondersteuning voor het abonnement van een klant.

| Eigenschap        | Type                                                           | Beschrijving                                                                     |
|-----------------|----------------------------------------------------------------|---------------------------------------------------------------------------------|
| supportTenantId | tekenreeks                                                         | Een tekenreeks met GUID-indeling die de tenant-id van de contactpersoon van de ondersteuning aangeeft. |
| supportMpnId    | tekenreeks                                                         | De MPN-id (Microsoft Partner Network) van de contactpersoon.                       |
| naam            | tekenreeks                                                         | De naam van de contactpersoon voor ondersteuning.                                                |
| Verwijzigingen           | [ResourceLinks](utility-resources.md#resourcelinks)            | De koppelingen naar de contactpersoon voor ondersteuning.                                              |
| kenmerken      | [ResourceAttributes](utility-resources.md#resourceattributes)  | De metagegevenskenmerken. Bevat "objectType": " SupportContact".              |

## <a name="registersubscription"></a>RegisterAbonnement

De **RegisterSubscription-resource** retourneert een koppeling die kan worden gebruikt om de registratiestatus van een abonnement op te vragen. De registratiestatus wordt geretourneerd in de antwoord-body van een geaccepteerde aanvraag om een Azure-abonnement te registreren.

| Eigenschap                | Type                               | Beschrijving                                                                           |
|-------------------------|------------------------------------|---------------------------------------------------------------------------------------|
| httpResponseMessage     | object                             | Retourneert HTTP-statuscode 202 'Geaccepteerd', met een Location-header met een koppeling om de registratiestatus op te vragen. Bijvoorbeeld: `"/customers/{customer-id}/subscriptions/{subscription-id}/registrationstatus"` |

## <a name="refundoption"></a>RestitutieOption

De **resource RefundOption** vertegenwoordigt een mogelijke restitutieoptie voor het abonnement.

| Eigenschap          | Type | Beschrijving                                                                         |
|-------------------|--------|-------------------------------------------------------------------------------------|
| type | tekenreeks | Het type restitutie. De ondersteunde waarden zijn Gedeeltelijk en Volledig |
| expiresAfter      | tekenreeks in UTC-datum/tijd-indeling | Het tijdstempel wanneer deze optie verloopt. Als null is, betekent dit dat er geen vervaldatum is. |

## <a name="azureentitlement"></a>AzureEntitlement

De **resource AzureEntitlement** vertegenwoordigt de Azure-rechten voor het abonnement.

| Eigenschap          | Type | Beschrijving                                                                         |
|-------------------|--------|-------------------------------------------------------------------------------------|
| id | tekenreeks | De rechten-id |
| Friendlyname      | tekenreeks | De gebruiksvriendelijke naam van het recht. |
| status | tekenreeks | De status van rechten. |
| subscriptionId | tekenreeks | De abonnements-id waar het recht bij hoort. |
