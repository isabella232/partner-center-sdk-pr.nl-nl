---
title: Profiel resources
description: Hierin wordt het gedrag van de profielen van een Cloud Solution Provider beschreven.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: e0561278995f4f9747320866b51de57efea8f712
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767482"
---
# <a name="profile-resources"></a>Profiel resources

**Van toepassing op**

- Partnercentrum
- Partner centrum beheerd door 21Vianet
- Partnercentrum voor Microsoft Cloud Duitsland
- Partnercentrum voor Microsoft Cloud for US Government

Hierin wordt het gedrag van de profielen van een Cloud Solution Provider beschreven.

## <a name="billingprofile"></a>BillingProfile

Hiermee wordt het facturerings Profiel van een partner beschreven.

| Eigenschap            | Type                                                           | Description                                                 |
|---------------------|----------------------------------------------------------------|-------------------------------------------------------------|
| companyName         | tekenreeks                                                         | De naam van het facturerings bedrijf.                                   |
| adres             | [Adres](utility-resources.md#address)                       | Het adres van het factuur adres van het bedrijf of de organisatie. |
| primaryContact      | [Contact](utility-resources.md#contact)                       | De primaire contact persoon voor het bedrijf of de organisatie.        |
| purchaseOrderNumber | tekenreeks                                                         | Het inkooporder nummer van het bedrijf of de organisatie.        |
| in taxI               | tekenreeks                                                         | De BTW-ID van het bedrijf of de organisatie.                       |
| billingCurrency     | tekenreeks                                                         | De valuta die wordt gebruikt door het bedrijf of de organisatie.           |
| Bestands type         | tekenreeks                                                         | Het Partner Profiel type.                                   |
| koppelen               | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen die overeenkomen met het profiel.            |
| kenmerken          | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met het profiel.       |

## <a name="legalbusinessprofile"></a>LegalBusinessProfile

Hierin wordt het juridische zakelijke profiel van een partner beschreven.

| Eigenschap               | Type                                                           | Description                                                                                                                                                          |
|------------------------|----------------------------------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| companyName            | tekenreeks                                                         | De naam van het rechts bedrijf.                                                                                                                                              |
| adres                | [Adres](utility-resources.md#address)                       | Het adres van het bedrijf of de organisatie.                                                                                                                          |
| primaryContact         | [Contact](utility-resources.md#contact)                       | De primaire contact persoon voor het bedrijf of de organisatie.                                                                                                                 |
| companyApproverAddress | [Adres](utility-resources.md#address)                       | Het adres van de bedrijfs goed keurder.                                                                                                                                        |
| companyApproverEmail   | tekenreeks                                                         | Het e-mail adres van de bedrijf goed keurder.                                                                                                                                          |
| vettingStatus          | tekenreeks                                                         | De status hebben. Deze waarde is de teken reeks representatie van de naam van een van de leden die zijn gevonden in [**VettingStatus**](/dotnet/api/microsoft.store.partnercenter.models.partners.vettingstatus).           |
| vettingSubStatus       | tekenreeks                                                         | De hebben-substatus. Deze waarde is de teken reeks representatie van de naam van een van de leden die zijn gevonden in [**VettingSubStatus**](/dotnet/api/microsoft.store.partnercenter.models.partners.vettingsubstatus). |
| Bestands type            | tekenreeks                                                         | Het Partner Profiel type.                                                                                                                                            |
| koppelen                  | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen die overeenkomen met het profiel.                                                                                                                     |
| kenmerken             | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met het profiel.                                                                                                                |

## <a name="mpnprofile"></a>MpnProfile

Beschrijft het Microsoft Partner Network Profiel van een partner.

| Eigenschap    | Type                                                           | Description                                           |
|-------------|----------------------------------------------------------------|-------------------------------------------------------|
| partnerName | tekenreeks                                                         | De naam van het bedrijf of de organisatie.                     |
| mpnId       | tekenreeks                                                         | De Microsoft Partner Network-ID.                     |
| Bestands type | tekenreeks                                                         | Het Partner Profiel type.                             |
| koppelen       | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen die overeenkomen met het profiel.      |
| kenmerken  | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met het profiel. |

## <a name="organizationprofile"></a>OrganizationProfile

Hierin wordt het organisatie profiel van een partner beschreven.

| Eigenschap       | Type                                                           | Beschrijving                                                            |
|----------------|----------------------------------------------------------------|------------------------------------------------------------------------|
| id             | tekenreeks                                                         | De id van de organisatie.                                                 |
| companyName    | tekenreeks                                                         | De naam van het bedrijf of de organisatie.                               |
| defaultAddress | [Adres](utility-resources.md#address)                       | Het standaard adres van het bedrijf of de organisatie.                    |
| tenantId       | tekenreeks                                                         | De Tenant-id.                                                 |
| domein         | tekenreeks                                                         | Het bedrijfs domein of de organisatie.                                  |
| e-mail          | tekenreeks                                                         | Hiermee wordt het bovenliggende abonnement opgehaald of ingesteld.                                  |
| language       | tekenreeks                                                         | De voorkeurs taal voor communicatie.                              |
| culturele        | tekenreeks                                                         | De voorkeurs cultuur voor communicatie en valuta, zoals ' en-us '. |
| Bestands type    | tekenreeks                                                         | Het Partner Profiel type.                                              |
| koppelen          | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen die overeenkomen met het profiel.                       |
| kenmerken     | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met het profiel.                  |

## <a name="supportprofile"></a>SupportProfile

Hierin wordt het ondersteunings Profiel van een partner beschreven.

| Eigenschap    | Type                                                           | Description                                           |
|-------------|----------------------------------------------------------------|-------------------------------------------------------|
| e-mail       | tekenreeks                                                         | Het e-mail adres dat is gekoppeld aan het profiel.        |
| telefoon   | tekenreeks                                                         | Het telefoon nummer dat aan het profiel is gekoppeld.         |
| website     | tekenreeks                                                         | De ondersteunings website.                                  |
| Bestands type | tekenreeks                                                         | Het Partner Profiel type.                             |
| koppelen       | [ResourceLinks](utility-resources.md#resourcelinks)           | De resource koppelingen die overeenkomen met het profiel.      |
| kenmerken  | [ResourceAttributes](utility-resources.md#resourceattributes) | De meta gegevens kenmerken die overeenkomen met het profiel. |

