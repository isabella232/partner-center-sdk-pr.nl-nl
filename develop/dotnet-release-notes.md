---
title: Release opmerkingen voor de .NET SDK voor Partner Center
description: Release opmerkingen voor de nieuwste versie van de .NET SDK van partner Center.
ms.date: 09/18/2020
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 2fe309500cc80e962c101ad97f0712bef7e11eb3
ms.sourcegitcommit: f7fce0b35ab1579e59136abc357b71cf768b81b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 03/23/2021
ms.locfileid: "104895530"
---
# <a name="net-sdk-release-notes"></a>Opmerkingen bij de release van .NET SDK

De volgende release opmerkingen zijn beschikbaar voor nieuwe versies van [micro soft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter). U kunt [.NET SDK](https://github.com/Microsoft/Partner-Center-DotNet-Samples) -voor beelden vinden op github. U vindt de [Naslag informatie voor het partner centrum .net API](/dotnet/api/?view=partnercenter-dotnet-latest&preserve-view=true) in de .net API-browser.

## <a name="version-1170"></a>Versie 1.17.0

[Micro soft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.17.0) v 1.17.0 is nu algemene Beschik baarheid. Er zijn ook bijgewerkte github-voor [beelden](https://github.com/Microsoft/Partner-Center-DotNet-Samples) beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

* Controle bijgewerkt: nieuwe bewerkings typen toegevoegd om te weten wanneer de door de klant goedgekeurde en beëindigde DAP is
  * [DapAdminRelationshipApproved](auditing-resources.md)
  * [DapAdminRelationshipTerminated](auditing-resources.md)

* Controle bijgewerkt: nieuwe resource en bewerkings typen toegevoegd voor het ondersteunen van het scenario voor de Directory functie van de klant
  * Resource type "[CustomerDirectoryRole](auditing-resources.md)"
  * Bewerkings typen '[AddUserMember](auditing-resources.md)' en '[RemoveUserMember](auditing-resources.md)'

* SDK-updates voor klanten account-ondersteuning voor de volgende API'S
  * /Customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus ophalen
  * /Customers/{Customer-Tenant-id}/Qualifications ophalen 
  * POST/Customers/{customer_id}/Qualifications? code = {validationCode}

* **De volgende wijzigingen zijn geïntroduceerd als onderdeel van de nieuwe Commerce, die momenteel alleen beschikbaar zijn op basis van de uitnodiging voor partners die deel uitmaken van de M365/D365 nieuwe technische preview van Commerce-ervaring.** Partners die geen deel uitmaken van de nieuwe preview-versie van Commerce private, mogen geen gevolgen ondervinden en moeten neerwaarts compatibel zijn.
  * Wijzigingen in catalogus:
    * /Products/{product-id}/SKUs/{SKU-id} ophalen
  * Kopen en beheren:
    * /Customers/{customerId}/subscriptions ophalen
    * /Customers/{customerId}/subscriptions/{subscriptionId} ophalen
    * PATCH/customers/{customerId}/subscriptions/{subscriptionId}
    * /Customers/{customerId}/subscriptions/{subscriptionId}/transitioneligibilities ophalen
    * /Customers/{customerId}/subscriptions/{subscriptionId}/transitions ophalen
    * /Customers/{customerId}/subscriptions/{subscriptionId}/transitions plaatsen


## <a name="version-1163"></a>Versie 1.16.3

[Micro soft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.3) v 1.16.3 is nu algemene Beschik baarheid. Er zijn ook bijgewerkte github-voor [beelden](https://github.com/Microsoft/Partner-Center-DotNet-Samples) beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

* SelfServePolicies-nieuwe functionaliteit toegevoegd
  * [GetSelfServePolicies](get-a-self-serve-policy-by-id.md)
  * [GetListOfSelfServicePolicies](get-a-list-of-self-serve-policies.md)
  * [CreateSelfServePolicies](create-a-self-serve-policy.md)
  * [UpdateSelfServePolicies](update-a-self-serve-policy.md)
  * [DeleteSelfServePolicies](delete-a-self-serve-policy.md)

* Bedrijfs profiel van klanten
  * [OrganizationRegistrationNumber](create-a-customer.md) toegevoegd

* CustomerBillingProfile.DefaultAddress
  * Middelste naam toegevoegd

## <a name="version-1162"></a>Versie 1.16.2

[Micro soft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.2) v 1.16.2 is nu algemene Beschik baarheid. Er zijn ook bijgewerkte github-voor [beelden](https://github.com/Microsoft/Partner-Center-DotNet-Samples) beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

* Ondersteunde bewerkings typen voor controle record bijwerken. De nieuwe toegevoegde items zijn:
  * CreateSelfServePolicy
  * UpdateSelfServePolicy
  * DeleteSelfServePolicy
  * RemovePartnerRelationship
  * DeleteTipCustomer
  * CreateRelatedReferral
  * UpdateRelatedReferral

* Het maken van de service aanvraag is nu afgeschaft
* Ondersteunings onderwerpen zijn nu afgeschaft


## <a name="version-1161"></a>Versie 1.16.1

[Micro soft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.1) v 1.16.1 is nu algemene Beschik baarheid. Er zijn ook bijgewerkte github-voor [beelden](https://github.com/Microsoft/Partner-Center-DotNet-Samples) beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

We hebben de bestaande micro soft Partner Center SDK gemigreerd van .NET Framework naar .NET Standard 2,0-platform. Hiermee maakt u de SDK compatibel met bestaande toepassingen met .NET Framework 4.6.1 en hoger. De SDK biedt ondersteuning voor .NET Core 2,0 en hoger. Controleer de [.net-implementatie ondersteuning](/dotnet/standard/net-standard) voordat u deze naar bestaande toepassingen overdraagt.   


## <a name="version-1153"></a>Versie 1.15.3
[Micro soft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.15.3) v 1.15.3 is nu algemene Beschik baarheid. Er zijn ook bijgewerkte REST Api's en github-voor [beelden](https://github.com/Microsoft/Partner-Center-DotNet-Samples) beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

* Partner overeenkomst
  * De mogelijkheid voor indirecte providers is toegevoegd om de [status van de micro soft Partner Agreement van indirecte wederverkopers te verifiëren](verify-indirect-reseller-mpa-status.md).
* Producten
  * De volgende twee interfaces zijn onjuist geplaatst onder de naam ruimte micro soft. Store. PartnerCenter. Products. Ze bevinden zich nu in de naam ruimte micro soft. Store. PartnerCenter. klanten. Products.
    * ICustomerProductByReservationScope
    * ICustomerSkuByReservationScope
