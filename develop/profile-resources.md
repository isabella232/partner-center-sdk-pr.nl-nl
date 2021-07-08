---
title: Profielbronnen
description: Beschrijft het gedrag van Cloud Solution Provider profielen van een klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 945cfa141d1e6bde1709da882a177daaa32fba1f
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111547781"
---
# <a name="profile-resources"></a>Profielbronnen

**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government

Beschrijft het gedrag van Cloud Solution Provider profielen van een klant.

## <a name="billingprofile"></a>BillingProfile

Beschrijft het factureringsprofiel van een partner.

| Eigenschap            | Type                                                           | Beschrijving                                                 |
|---------------------|----------------------------------------------------------------|-------------------------------------------------------------|
| companyName         | tekenreeks                                                         | De naam van het factureringsbedrijf.                                   |
| adres             | [Adres](utility-resources.md#address)                       | Het factureringsadres van het bedrijf of de organisatie. |
| primaryContact      | [Contact](utility-resources.md#contact)                       | De primaire contactpersoon voor het bedrijf of de organisatie.        |
| purchaseOrderNumber | tekenreeks                                                         | Het inkoopordernummer van het bedrijf of de organisatie.        |
| taxId               | tekenreeks                                                         | Het btw-nummer van het bedrijf of de organisatie.                       |
| billingCurrency     | tekenreeks                                                         | De valuta die wordt gebruikt door het bedrijf of de organisatie.           |
| profileType         | tekenreeks                                                         | Het partnerprofieltype.                                   |
| Verwijzigingen               | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen die overeenkomen met het profiel.            |
| kenmerken          | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met het profiel.       |

## <a name="legalbusinessprofile"></a>LegalBusinessProfile

Beschrijft het juridische bedrijfsprofiel van een partner.

| Eigenschap               | Type                                                           | Beschrijving                                                                                                                                                          |
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| companyName            | tekenreeks                                                         | De naam van het juridische bedrijf.                                                                                                                                              |
| adres                | [Adres](utility-resources.md#address)                       | Het adres van het bedrijf of de organisatie.                                                                                                                          |
| primaryContact         | [Contact](utility-resources.md#contact)                       | De primaire contactpersoon voor het bedrijf of de organisatie.                                                                                                                 |
| companyApproverAddress | [Adres](utility-resources.md#address)                       | Het adres van de fiattelaar van het bedrijf.                                                                                                                                        |
| companyApproverEmail   | tekenreeks                                                         | Het e-mailadres van de fiattelaar van het bedrijf.                                                                                                                                          |
| vettingStatus          | tekenreeks                                                         | De status van de doorlichting. Deze waarde is de tekenreeksweergave van een van de lidnamen in [**VettingStatus**](/dotnet/api/microsoft.store.partnercenter.models.partners.vettingstatus).           |
| vettingSubStatus       | tekenreeks                                                         | De substatus van de doorlichting. Deze waarde is de tekenreeksweergave van een van de lidnamen in [**VettingSubStatus.**](/dotnet/api/microsoft.store.partnercenter.models.partners.vettingsubstatus) |
| profileType            | tekenreeks                                                         | Het partnerprofieltype.                                                                                                                                            |
| Verwijzigingen                  | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen die overeenkomen met het profiel.                                                                                                                     |
| kenmerken             | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met het profiel.                                                                                                                |

## <a name="mpnprofile"></a>MpnProfile

Beschrijft het Microsoft Partner Network van een partner.

| Eigenschap    | Type                                                           | Beschrijving                                           |
|-------------|----------------------------------------------------------------|-------------------------------------------------------|
| partnerName | tekenreeks                                                         | De naam van het bedrijf of de organisatie.                     |
| mpnId       | tekenreeks                                                         | De Microsoft Partner Network(MPN)-id.                     |
| profileType | tekenreeks                                                         | Het partnerprofieltype.                             |
| Verwijzigingen       | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen die overeenkomen met het profiel.      |
| kenmerken  | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met het profiel. |

## <a name="organizationprofile"></a>OrganizationProfile

Beschrijft het organisatieprofiel van een partner.

| Eigenschap       | Type                                                           | Beschrijving                                                            |
|----------------|----------------------------------------------------------------|------------------------------------------------------------------------|
| id             | tekenreeks                                                         | De id van de organisatie.                                                 |
| companyName    | tekenreeks                                                         | De naam van het bedrijf of de organisatie.                               |
| defaultAddress | [Adres](utility-resources.md#address)                       | Het standaardadres van het bedrijf of de organisatie.                    |
| tenantId       | tekenreeks                                                         | De tenant-id.                                                 |
| domein         | tekenreeks                                                         | Het domein van het bedrijf of de organisatie.                                  |
| e-mail          | tekenreeks                                                         | Haalt het bovenliggende abonnement op of stelt het in.                                  |
| language       | tekenreeks                                                         | De voorkeurstaal voor communicatie.                              |
| Cultuur        | tekenreeks                                                         | De voorkeurscultuur voor communicatie en valuta, zoals 'en-us'. |
| profileType    | tekenreeks                                                         | Het partnerprofieltype.                                              |
| Verwijzigingen          | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen die overeenkomen met het profiel.                       |
| kenmerken     | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met het profiel.                  |

## <a name="supportprofile"></a>SupportProfile

Beschrijft het ondersteuningsprofiel van een partner.

| Eigenschap    | Type                                                           | Beschrijving                                           |
|-------------|----------------------------------------------------------------|-------------------------------------------------------|
| e-mail       | tekenreeks                                                         | Het e-mailadres dat is gekoppeld aan het profiel.        |
| telefoon   | tekenreeks                                                         | Het telefoonnummer dat is gekoppeld aan het profiel.         |
| website     | tekenreeks                                                         | De ondersteuningswebsite.                                  |
| profileType | tekenreeks                                                         | Het partnerprofieltype.                             |
| Verwijzigingen       | [ResourceLinks](utility-resources.md#resourcelinks)           | De resourcekoppelingen die overeenkomen met het profiel.      |
| kenmerken  | [ResourceAttributes](utility-resources.md#resourceattributes) | De metagegevenskenmerken die overeenkomen met het profiel. |

