---
title: Partner Center opmerkingen bij de release van .NET SDK
description: Releasenotities voor de nieuwste versie van de Partner Center .NET SDK.
ms.date: 07/07/2021
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c1532d48c00550f5eb437ed0164d6a1f7bb340dd
ms.sourcegitcommit: 53c94db33b09c30e762b842c4275b2b531dba932
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/09/2021
ms.locfileid: "113522631"
---
# <a name="net-sdk-release-notes"></a>Releasenotities voor .NET SDK

De volgende releasenotities zijn beschikbaar voor nieuwe versies van [Microsoft Partner Center .NET SDK.](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter) U vindt [.NET SDK-voorbeelden](https://github.com/Microsoft/Partner-Center-DotNet-Samples) op GitHub. U vindt de [naslaginformatie Partner Center .NET API](/dotnet/api/?view=partnercenter-dotnet-latest&preserve-view=true) in de .NET API-browser.

## <a name="version-201"></a>Versie 2.0.1

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/2.0.1) v2.0.1 is nu algemeen beschikbaar. Bijgewerkte [GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

> [!NOTE]
> Sommige wijzigingen die zijn geïntroduceerd als onderdeel van New Commerce Experiences ('REVIEW'), die momenteel alleen beschikbaar zijn op basis van uitnodigingen voor partners die deel uitmaken van de technische preview van de nieuwe commerce-ervaring M365/D365. Partners die geen deel uitmaken van de private preview van New Commerce mogen geen gevolgen merken en moeten achterwaarts compatibel zijn.

### <a name="common"></a>Algemeen
* Wijziging in de verwijzing naar de verificatiebibliotheek: de verwijzing is gewijzigd van Azure Active Directory Authentication Library[(ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)) in Microsoft Authentication Library[(MSAL)](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet)

  De volgende wijzigingen moeten worden aangebracht om ervoor te zorgen dat MSAL correct wordt uitgevoerd in uw toepassing of .NET-voorbeeld:

  * Toevoegen `https://login.microsoftonline.com/common/oauth2/nativeclient` als RedirectUrl voor mobiele en bureaubladtoepassingen
  * Voeg **domein toe** aan de sectie UserAuthentication in het configuratiebestand van uw toepassing. 

    Domein is de Azure Active Directory of tenant-id waar de Azure AD-toepassing is gemaakt

* [Foutcodes](error-codes.md) : er is een nieuwe foutcode toegevoegd 
  * 408: Time-out van aanvraag
  * 504: Time-out van gateway 

### <a name="manage-billing"></a>De facturering beheren

* [Factuurregelitems:](get-invoiceline-items.md) nieuwe kenmerken toegevoegd aan de volgende API's:
  * `GET /invoices/{invoice-id}/lineitems?provider={provider}&invoicelineitemtype=billinglineitems`
  * `GET /invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems`

  Nieuwe kenmerken: 
  * productQualifiers
  * subscriptionStartDate
  * subscriptionEndDate
  * referenceId
  * creditReasonCode (alleen van toepassing op REA)
  * promotionId 


* [Regelitems voor dagelijks beoordeeld gebruik:](get-invoice-billed-consumption-lineitems.md) nieuwe kenmerken toegevoegd aan de volgende API: 
  * `GET /invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems`
  
  Nieuwe kenmerken: 
  * hasPartnerEarnedCredit (alleen van toepassing op GEBRUIK)
  * creditType (alleen van toepassing op GEBRUIK)
  * rateOfCredit (alleen van toepassing op NCE)


### <a name="manage-orders"></a>Bestellingen beheren

* [Abonnementsbronnen:](subscription-resources.md) nieuwe eigenschap toegevoegd. 
  * CancellationAllowedUntilDate - (alleen van toepassing op ANNULATIE)

* Overgangsresources (alleen van toepassing op PROPERTY) – Nieuwe eigenschap toegevoegd 
  * FromSubscriptionId

### <a name="manage-customer-accounts"></a>Klantaccounts beheren

* [Een adres valideren:](validate-an-address.md) het antwoord wordt gewijzigd van een Booleaanse in een nieuw model voor API:
  * `POST /validations/address`
  
  Nieuw antwoordmodel: 
  * AddressValidationResponse

* De synchronisatiesynchrone API van de klant is afgeschaft.  


## <a name="version-1170"></a>Versie 1.17.0

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.17.0) v1.17.0 is nu algemeen beschikbaar. Bijgewerkte [GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

* Controle bijgewerkt: nieuwe bewerkingstypen toegevoegd om te weten wanneer de klant DAP heeft goedgekeurd en beëindigd
  * [DapAdminRelationshipApproved](auditing-resources.md)
  * [DapAdminRelationshipTerminated](auditing-resources.md)

* Controle bijgewerkt: nieuwe resource- en bewerkingstypen toegevoegd voor het ondersteunen van het scenario voor de directory-rol van de klant
  * Resourcetype[CustomerDirectoryRole](auditing-resources.md)
  * Bewerkingstypen[AddUserMember](auditing-resources.md)en[RemoveUserMember](auditing-resources.md)

* SDK-updates voor klantenaccount - ondersteuning voor volgende API's
  * GET /customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus
  * GET /customers/{customer-tenant-id}/kwalificaties 
  * POST /customers/{customer_id}/kwalificaties?code={validationCode}

* **Na de wijzigingen die zijn geïntroduceerd als onderdeel van New Commerce, die momenteel alleen beschikbaar zijn op basis van uitnodiging aan partners die deel uitmaken van de technische preview van de nieuwe commerce-ervaring M365/D365.** Partners die geen deel uitmaken van de private preview van New Commerce mogen geen gevolgen merken en moeten achterwaarts compatibel zijn.
  * Cataloguswijzigingen:
    * GET /products/{product-id}/skus/{sku-id}
  * Kopen en beheren:
    * GET /customers/{customerId}/subscriptions
    * GET /customers/{customerId}/subscriptions/{subscriptionId}
    * PATCH /customers/{customerId}/subscriptions/{subscriptionId}
    * GET /customers/{customerId}/subscriptions/{subscriptionId}/transitioneligibilities
    * GET /customers/{customerId}/subscriptions/{subscriptionId}/transitions
    * POST /customers/{customerId}/subscriptions/{subscriptionId}/transitions


## <a name="version-1163"></a>Versie 1.16.3

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.3) v1.16.3 is nu algemeen beschikbaar. Bijgewerkte [GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

* SelfServePolicies: nieuwe functionaliteit toegevoegd
  * [GetSelfServePolicies](get-a-self-serve-policy-by-id.md)
  * [GetListOfSelfServicePolicies](get-a-list-of-self-serve-policies.md)
  * [CreateSelfServePolicies](create-a-self-serve-policy.md)
  * [UpdateSelfServePolicies](update-a-self-serve-policy.md)
  * [DeleteSelfServePolicies](delete-a-self-serve-policy.md)

* Bedrijfsprofiel van klanten
  * [OrganizationRegistrationNumber toegevoegd](create-a-customer.md)

* CustomerBillingProfile.DefaultAddress
  * MiddleName toegevoegd

## <a name="version-1162"></a>Versie 1.16.2

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.2) v1.16.2 is nu algemeen beschikbaar. Bijgewerkte [GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

* Ondersteunde bewerkingstypen voor Controlerecord bijwerken. De zojuist toegevoegde zijn:
  * CreateSelfServePolicy
  * UpdateSelfServePolicy
  * DeleteSelfServePolicy
  * RemovePartnerRelationship
  * DeleteTipCustomer
  * CreateRelatedReferral
  * UpdateRelatedReferral

* Het maken van een serviceaanvraag is nu afgeschaft
* Ondersteuningsonderwerpen zijn nu afgeschaft


## <a name="version-1161"></a>Versie 1.16.1

[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.1) v1.16.1 is nu algemeen beschikbaar. Bijgewerkte [GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

We hebben de bestaande Microsoft-Partnercentrum-SDK gemigreerd van .NET Framework naar het .NET Standard 2.0-platform. Hierdoor wordt de SDK compatibel met bestaande toepassingen met .NET Framework 4.6.1 en hoger. De SDK biedt ondersteuning voor .NET Core 2.0 en hoger. Controleer [de ondersteuning voor .NET-implementatie](/dotnet/standard/net-standard) voordat u deze overplaatst naar bestaande toepassingen.   


## <a name="version-1153"></a>Versie 1.15.3
[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.15.3) v1.15.3 is nu algemeen beschikbaar. Bijgewerkte REST [API's en GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar. De volgende wijzigingen zijn opgenomen in deze versie:

* Partnerovereenkomst
  * Indirecte providers hebben de mogelijkheid toegevoegd om de [status Microsoft Partner-overeenkomst indirecte resellers te verifiëren.](verify-indirect-reseller-mpa-status.md)
* Producten
  * De volgende twee interfaces zijn onjuist geplaatst onder de naamruimte Microsoft.Store.PartnerCenter.Products. Ze bevinden zich nu onder de naamruimte Microsoft.Store.PartnerCenter.Customers.Products.
    * ICustomerProductByReservationScope
    * ICustomerSkuByReservationScope
