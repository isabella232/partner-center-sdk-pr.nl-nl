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
# <a name="net-sdk-release-notes"></a><span data-ttu-id="631b5-103">Releasenotities voor .NET SDK</span><span class="sxs-lookup"><span data-stu-id="631b5-103">.NET SDK release notes</span></span>

<span data-ttu-id="631b5-104">De volgende releasenotities zijn beschikbaar voor nieuwe versies van [Microsoft Partner Center .NET SDK.](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter)</span><span class="sxs-lookup"><span data-stu-id="631b5-104">The following release notes are available for new versions of [Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter).</span></span> <span data-ttu-id="631b5-105">U vindt [.NET SDK-voorbeelden](https://github.com/Microsoft/Partner-Center-DotNet-Samples) op GitHub.</span><span class="sxs-lookup"><span data-stu-id="631b5-105">You can find [.NET SDK samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) on GitHub.</span></span> <span data-ttu-id="631b5-106">U vindt de [naslaginformatie Partner Center .NET API](/dotnet/api/?view=partnercenter-dotnet-latest&preserve-view=true) in de .NET API-browser.</span><span class="sxs-lookup"><span data-stu-id="631b5-106">You can find the [Partner Center .NET API reference](/dotnet/api/?view=partnercenter-dotnet-latest&preserve-view=true) in the .NET API Browser.</span></span>

## <a name="version-201"></a><span data-ttu-id="631b5-107">Versie 2.0.1</span><span class="sxs-lookup"><span data-stu-id="631b5-107">Version 2.0.1</span></span>

<span data-ttu-id="631b5-108">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/2.0.1) v2.0.1 is nu algemeen beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-108">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/2.0.1) v2.0.1 is now general availability.</span></span> <span data-ttu-id="631b5-109">Bijgewerkte [GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-109">Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="631b5-110">De volgende wijzigingen zijn opgenomen in deze versie:</span><span class="sxs-lookup"><span data-stu-id="631b5-110">The following changes are included in this version:</span></span>

> [!NOTE]
> <span data-ttu-id="631b5-111">Sommige wijzigingen die zijn geïntroduceerd als onderdeel van New Commerce Experiences ('REVIEW'), die momenteel alleen beschikbaar zijn op basis van uitnodigingen voor partners die deel uitmaken van de technische preview van de nieuwe commerce-ervaring M365/D365.</span><span class="sxs-lookup"><span data-stu-id="631b5-111">Some of changes introduced as part of New Commerce Experiences (“NCE”) which are currently available based on invitation only to partners who are part of the M365/D365 new commerce experience technical preview.</span></span> <span data-ttu-id="631b5-112">Partners die geen deel uitmaken van de private preview van New Commerce mogen geen gevolgen merken en moeten achterwaarts compatibel zijn.</span><span class="sxs-lookup"><span data-stu-id="631b5-112">Partners who are not part of New commerce private preview should not notice impacts and should be backward compatible.</span></span>

### <a name="common"></a><span data-ttu-id="631b5-113">Algemeen</span><span class="sxs-lookup"><span data-stu-id="631b5-113">Common</span></span>
* <span data-ttu-id="631b5-114">Wijziging in de verwijzing naar de verificatiebibliotheek: de verwijzing is gewijzigd van Azure Active Directory Authentication Library[(ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)) in Microsoft Authentication Library[(MSAL)](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet)</span><span class="sxs-lookup"><span data-stu-id="631b5-114">Change on the reference to authentication library – The reference is changed from Azure Active Directory Authentication Library ([ADAL](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet)) to Microsoft Authentication Library ([MSAL](https://github.com/AzureAD/microsoft-authentication-library-for-dotnet))</span></span>

  <span data-ttu-id="631b5-115">De volgende wijzigingen moeten worden aangebracht om ervoor te zorgen dat MSAL correct wordt uitgevoerd in uw toepassing of .NET-voorbeeld:</span><span class="sxs-lookup"><span data-stu-id="631b5-115">Following changes should be made to ensure MSAL runs correctly on your application or .NET sample:</span></span>

  * <span data-ttu-id="631b5-116">Toevoegen `https://login.microsoftonline.com/common/oauth2/nativeclient` als RedirectUrl voor mobiele en bureaubladtoepassingen</span><span class="sxs-lookup"><span data-stu-id="631b5-116">Add `https://login.microsoftonline.com/common/oauth2/nativeclient` as RedirectUrl for Mobile and desktop applications</span></span>
  * <span data-ttu-id="631b5-117">Voeg **domein toe** aan de sectie UserAuthentication in het configuratiebestand van uw toepassing.</span><span class="sxs-lookup"><span data-stu-id="631b5-117">Add **Domain** into UserAuthentication section in your application configuration file.</span></span> 

    <span data-ttu-id="631b5-118">Domein is de Azure Active Directory of tenant-id waar de Azure AD-toepassing is gemaakt</span><span class="sxs-lookup"><span data-stu-id="631b5-118">Domain is the Azure Active Directory domain or tenant ID where the Azure AD application was created</span></span>

* <span data-ttu-id="631b5-119">[Foutcodes](error-codes.md) : er is een nieuwe foutcode toegevoegd</span><span class="sxs-lookup"><span data-stu-id="631b5-119">[Error codes](error-codes.md) – New error code added</span></span> 
  * <span data-ttu-id="631b5-120">408: Time-out van aanvraag</span><span class="sxs-lookup"><span data-stu-id="631b5-120">408: Request timeout</span></span>
  * <span data-ttu-id="631b5-121">504: Time-out van gateway</span><span class="sxs-lookup"><span data-stu-id="631b5-121">504: Gateway timeout</span></span> 

### <a name="manage-billing"></a><span data-ttu-id="631b5-122">De facturering beheren</span><span class="sxs-lookup"><span data-stu-id="631b5-122">Manage billing</span></span>

* <span data-ttu-id="631b5-123">[Factuurregelitems:](get-invoiceline-items.md) nieuwe kenmerken toegevoegd aan de volgende API's:</span><span class="sxs-lookup"><span data-stu-id="631b5-123">[Invoice line-items](get-invoiceline-items.md) - new attributes added to following APIs:</span></span>
  * `GET /invoices/{invoice-id}/lineitems?provider={provider}&invoicelineitemtype=billinglineitems`
  * `GET /invoices/unbilled/lineitems?provider=onetime&invoicelineitemtype=billinglineitems`

  <span data-ttu-id="631b5-124">Nieuwe kenmerken:</span><span class="sxs-lookup"><span data-stu-id="631b5-124">New attributes:</span></span> 
  * <span data-ttu-id="631b5-125">productQualifiers</span><span class="sxs-lookup"><span data-stu-id="631b5-125">productQualifiers</span></span>
  * <span data-ttu-id="631b5-126">subscriptionStartDate</span><span class="sxs-lookup"><span data-stu-id="631b5-126">subscriptionStartDate</span></span>
  * <span data-ttu-id="631b5-127">subscriptionEndDate</span><span class="sxs-lookup"><span data-stu-id="631b5-127">subscriptionEndDate</span></span>
  * <span data-ttu-id="631b5-128">referenceId</span><span class="sxs-lookup"><span data-stu-id="631b5-128">referenceId</span></span>
  * <span data-ttu-id="631b5-129">creditReasonCode (alleen van toepassing op REA)</span><span class="sxs-lookup"><span data-stu-id="631b5-129">creditReasonCode  (Only applicable to NCE)</span></span>
  * <span data-ttu-id="631b5-130">promotionId</span><span class="sxs-lookup"><span data-stu-id="631b5-130">promotionId</span></span> 


* <span data-ttu-id="631b5-131">[Regelitems voor dagelijks beoordeeld gebruik:](get-invoice-billed-consumption-lineitems.md) nieuwe kenmerken toegevoegd aan de volgende API:</span><span class="sxs-lookup"><span data-stu-id="631b5-131">[Daily rated usage Line-items](get-invoice-billed-consumption-lineitems.md) – new attributes added to following API:</span></span> 
  * `GET /invoices/{invoice-id}/lineitems?provider=onetime&invoicelineitemtype=usagelineitems`
  
  <span data-ttu-id="631b5-132">Nieuwe kenmerken:</span><span class="sxs-lookup"><span data-stu-id="631b5-132">New attributes:</span></span> 
  * <span data-ttu-id="631b5-133">hasPartnerEarnedCredit (alleen van toepassing op GEBRUIK)</span><span class="sxs-lookup"><span data-stu-id="631b5-133">hasPartnerEarnedCredit (Only applicable to NCE)</span></span>
  * <span data-ttu-id="631b5-134">creditType (alleen van toepassing op GEBRUIK)</span><span class="sxs-lookup"><span data-stu-id="631b5-134">creditType (Only applicable to NCE)</span></span>
  * <span data-ttu-id="631b5-135">rateOfCredit (alleen van toepassing op NCE)</span><span class="sxs-lookup"><span data-stu-id="631b5-135">rateOfCredit (Only applicable to NCE)</span></span>


### <a name="manage-orders"></a><span data-ttu-id="631b5-136">Bestellingen beheren</span><span class="sxs-lookup"><span data-stu-id="631b5-136">Manage orders</span></span>

* <span data-ttu-id="631b5-137">[Abonnementsbronnen:](subscription-resources.md) nieuwe eigenschap toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="631b5-137">[Subscription Resources](subscription-resources.md) – New property added.</span></span> 
  * <span data-ttu-id="631b5-138">CancellationAllowedUntilDate - (alleen van toepassing op ANNULATIE)</span><span class="sxs-lookup"><span data-stu-id="631b5-138">CancellationAllowedUntilDate  - (Only applicable to NCE)</span></span>

* <span data-ttu-id="631b5-139">Overgangsresources (alleen van toepassing op PROPERTY) – Nieuwe eigenschap toegevoegd</span><span class="sxs-lookup"><span data-stu-id="631b5-139">Transition Resources (Only applicable to NCE) – New property added</span></span> 
  * <span data-ttu-id="631b5-140">FromSubscriptionId</span><span class="sxs-lookup"><span data-stu-id="631b5-140">FromSubscriptionId</span></span>

### <a name="manage-customer-accounts"></a><span data-ttu-id="631b5-141">Klantaccounts beheren</span><span class="sxs-lookup"><span data-stu-id="631b5-141">Manage customer accounts</span></span>

* <span data-ttu-id="631b5-142">[Een adres valideren:](validate-an-address.md) het antwoord wordt gewijzigd van een Booleaanse in een nieuw model voor API:</span><span class="sxs-lookup"><span data-stu-id="631b5-142">[Validate an address](validate-an-address.md) – Response is changed from a Boolean to a new model for API:</span></span>
  * `POST /validations/address`
  
  <span data-ttu-id="631b5-143">Nieuw antwoordmodel:</span><span class="sxs-lookup"><span data-stu-id="631b5-143">New response model:</span></span> 
  * <span data-ttu-id="631b5-144">AddressValidationResponse</span><span class="sxs-lookup"><span data-stu-id="631b5-144">AddressValidationResponse</span></span>

* <span data-ttu-id="631b5-145">De synchronisatiesynchrone API van de klant is afgeschaft.</span><span class="sxs-lookup"><span data-stu-id="631b5-145">Customer’s qualification synchronous API is deprecated.</span></span>  


## <a name="version-1170"></a><span data-ttu-id="631b5-146">Versie 1.17.0</span><span class="sxs-lookup"><span data-stu-id="631b5-146">Version 1.17.0</span></span>

<span data-ttu-id="631b5-147">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.17.0) v1.17.0 is nu algemeen beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-147">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.17.0) v1.17.0 is now general availability.</span></span> <span data-ttu-id="631b5-148">Bijgewerkte [GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-148">Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="631b5-149">De volgende wijzigingen zijn opgenomen in deze versie:</span><span class="sxs-lookup"><span data-stu-id="631b5-149">The following changes are included in this version:</span></span>

* <span data-ttu-id="631b5-150">Controle bijgewerkt: nieuwe bewerkingstypen toegevoegd om te weten wanneer de klant DAP heeft goedgekeurd en beëindigd</span><span class="sxs-lookup"><span data-stu-id="631b5-150">Audit Updated - Added new operation types for knowing when the customer approved and terminated DAP</span></span>
  * [<span data-ttu-id="631b5-151">DapAdminRelationshipApproved</span><span class="sxs-lookup"><span data-stu-id="631b5-151">DapAdminRelationshipApproved</span></span>](auditing-resources.md)
  * [<span data-ttu-id="631b5-152">DapAdminRelationshipTerminated</span><span class="sxs-lookup"><span data-stu-id="631b5-152">DapAdminRelationshipTerminated</span></span>](auditing-resources.md)

* <span data-ttu-id="631b5-153">Controle bijgewerkt: nieuwe resource- en bewerkingstypen toegevoegd voor het ondersteunen van het scenario voor de directory-rol van de klant</span><span class="sxs-lookup"><span data-stu-id="631b5-153">Audit Updated – Added new resource and operation types for supporting the customer directory role scenario</span></span>
  * <span data-ttu-id="631b5-154">Resourcetype[CustomerDirectoryRole](auditing-resources.md)</span><span class="sxs-lookup"><span data-stu-id="631b5-154">Resource type "[CustomerDirectoryRole](auditing-resources.md)"</span></span>
  * <span data-ttu-id="631b5-155">Bewerkingstypen[AddUserMember](auditing-resources.md)en[RemoveUserMember](auditing-resources.md)</span><span class="sxs-lookup"><span data-stu-id="631b5-155">Operation types "[AddUserMember](auditing-resources.md)" and "[RemoveUserMember](auditing-resources.md)"</span></span>

* <span data-ttu-id="631b5-156">SDK-updates voor klantenaccount - ondersteuning voor volgende API's</span><span class="sxs-lookup"><span data-stu-id="631b5-156">SDK Updates to Customers Account - Support for following API's</span></span>
  * <span data-ttu-id="631b5-157">GET /customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus</span><span class="sxs-lookup"><span data-stu-id="631b5-157">GET /customers/{customer-tenant-id}/directSignedMicrosoftCustomerAgreementStatus</span></span>
  * <span data-ttu-id="631b5-158">GET /customers/{customer-tenant-id}/kwalificaties</span><span class="sxs-lookup"><span data-stu-id="631b5-158">GET /customers/{customer-tenant-id}/qualifications</span></span> 
  * <span data-ttu-id="631b5-159">POST /customers/{customer_id}/kwalificaties?code={validationCode}</span><span class="sxs-lookup"><span data-stu-id="631b5-159">POST /customers/{customer_id}/qualifications?code={validationCode}</span></span>

* <span data-ttu-id="631b5-160">**Na de wijzigingen die zijn geïntroduceerd als onderdeel van New Commerce, die momenteel alleen beschikbaar zijn op basis van uitnodiging aan partners die deel uitmaken van de technische preview van de nieuwe commerce-ervaring M365/D365.**</span><span class="sxs-lookup"><span data-stu-id="631b5-160">**Following changes introduced as part of New Commerce which are currently available based on invitation only to partners who are part of the M365/D365 new commerce experience technical preview.**</span></span> <span data-ttu-id="631b5-161">Partners die geen deel uitmaken van de private preview van New Commerce mogen geen gevolgen merken en moeten achterwaarts compatibel zijn.</span><span class="sxs-lookup"><span data-stu-id="631b5-161">Partners who are not part of New commerce private preview should not notice impacts and should be backward compatible.</span></span>
  * <span data-ttu-id="631b5-162">Cataloguswijzigingen:</span><span class="sxs-lookup"><span data-stu-id="631b5-162">Catalog Changes:</span></span>
    * <span data-ttu-id="631b5-163">GET /products/{product-id}/skus/{sku-id}</span><span class="sxs-lookup"><span data-stu-id="631b5-163">GET /products/{product-id}/skus/{sku-id}</span></span>
  * <span data-ttu-id="631b5-164">Kopen en beheren:</span><span class="sxs-lookup"><span data-stu-id="631b5-164">Purchase and Manage:</span></span>
    * <span data-ttu-id="631b5-165">GET /customers/{customerId}/subscriptions</span><span class="sxs-lookup"><span data-stu-id="631b5-165">GET /customers/{customerId}/subscriptions</span></span>
    * <span data-ttu-id="631b5-166">GET /customers/{customerId}/subscriptions/{subscriptionId}</span><span class="sxs-lookup"><span data-stu-id="631b5-166">GET /customers/{customerId}/subscriptions/{subscriptionId}</span></span>
    * <span data-ttu-id="631b5-167">PATCH /customers/{customerId}/subscriptions/{subscriptionId}</span><span class="sxs-lookup"><span data-stu-id="631b5-167">PATCH /customers/{customerId}/subscriptions/{subscriptionId}</span></span>
    * <span data-ttu-id="631b5-168">GET /customers/{customerId}/subscriptions/{subscriptionId}/transitioneligibilities</span><span class="sxs-lookup"><span data-stu-id="631b5-168">GET /customers/{customerId}/subscriptions/{subscriptionId}/transitioneligibilities</span></span>
    * <span data-ttu-id="631b5-169">GET /customers/{customerId}/subscriptions/{subscriptionId}/transitions</span><span class="sxs-lookup"><span data-stu-id="631b5-169">GET /customers/{customerId}/subscriptions/{subscriptionId}/transitions</span></span>
    * <span data-ttu-id="631b5-170">POST /customers/{customerId}/subscriptions/{subscriptionId}/transitions</span><span class="sxs-lookup"><span data-stu-id="631b5-170">POST /customers/{customerId}/subscriptions/{subscriptionId}/transitions</span></span>


## <a name="version-1163"></a><span data-ttu-id="631b5-171">Versie 1.16.3</span><span class="sxs-lookup"><span data-stu-id="631b5-171">Version 1.16.3</span></span>

<span data-ttu-id="631b5-172">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.3) v1.16.3 is nu algemeen beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-172">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.3) v1.16.3 is now general availability.</span></span> <span data-ttu-id="631b5-173">Bijgewerkte [GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-173">Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="631b5-174">De volgende wijzigingen zijn opgenomen in deze versie:</span><span class="sxs-lookup"><span data-stu-id="631b5-174">The following changes are included in this version:</span></span>

* <span data-ttu-id="631b5-175">SelfServePolicies: nieuwe functionaliteit toegevoegd</span><span class="sxs-lookup"><span data-stu-id="631b5-175">SelfServePolicies - new functionality added</span></span>
  * [<span data-ttu-id="631b5-176">GetSelfServePolicies</span><span class="sxs-lookup"><span data-stu-id="631b5-176">GetSelfServePolicies</span></span>](get-a-self-serve-policy-by-id.md)
  * [<span data-ttu-id="631b5-177">GetListOfSelfServicePolicies</span><span class="sxs-lookup"><span data-stu-id="631b5-177">GetListOfSelfServicePolicies</span></span>](get-a-list-of-self-serve-policies.md)
  * [<span data-ttu-id="631b5-178">CreateSelfServePolicies</span><span class="sxs-lookup"><span data-stu-id="631b5-178">CreateSelfServePolicies</span></span>](create-a-self-serve-policy.md)
  * [<span data-ttu-id="631b5-179">UpdateSelfServePolicies</span><span class="sxs-lookup"><span data-stu-id="631b5-179">UpdateSelfServePolicies</span></span>](update-a-self-serve-policy.md)
  * [<span data-ttu-id="631b5-180">DeleteSelfServePolicies</span><span class="sxs-lookup"><span data-stu-id="631b5-180">DeleteSelfServePolicies</span></span>](delete-a-self-serve-policy.md)

* <span data-ttu-id="631b5-181">Bedrijfsprofiel van klanten</span><span class="sxs-lookup"><span data-stu-id="631b5-181">Customers Company Profile</span></span>
  * <span data-ttu-id="631b5-182">[OrganizationRegistrationNumber toegevoegd](create-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="631b5-182">Added [OrganizationRegistrationNumber](create-a-customer.md)</span></span>

* <span data-ttu-id="631b5-183">CustomerBillingProfile.DefaultAddress</span><span class="sxs-lookup"><span data-stu-id="631b5-183">CustomerBillingProfile.DefaultAddress</span></span>
  * <span data-ttu-id="631b5-184">MiddleName toegevoegd</span><span class="sxs-lookup"><span data-stu-id="631b5-184">Added MiddleName</span></span>

## <a name="version-1162"></a><span data-ttu-id="631b5-185">Versie 1.16.2</span><span class="sxs-lookup"><span data-stu-id="631b5-185">Version 1.16.2</span></span>

<span data-ttu-id="631b5-186">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.2) v1.16.2 is nu algemeen beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-186">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.2) v1.16.2 is now general availability.</span></span> <span data-ttu-id="631b5-187">Bijgewerkte [GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-187">Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="631b5-188">De volgende wijzigingen zijn opgenomen in deze versie:</span><span class="sxs-lookup"><span data-stu-id="631b5-188">The following changes are included in this version:</span></span>

* <span data-ttu-id="631b5-189">Ondersteunde bewerkingstypen voor Controlerecord bijwerken.</span><span class="sxs-lookup"><span data-stu-id="631b5-189">Update supported operation types for Audit Record.</span></span> <span data-ttu-id="631b5-190">De zojuist toegevoegde zijn:</span><span class="sxs-lookup"><span data-stu-id="631b5-190">The newly added ones are:</span></span>
  * <span data-ttu-id="631b5-191">CreateSelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="631b5-191">CreateSelfServePolicy</span></span>
  * <span data-ttu-id="631b5-192">UpdateSelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="631b5-192">UpdateSelfServePolicy</span></span>
  * <span data-ttu-id="631b5-193">DeleteSelfServePolicy</span><span class="sxs-lookup"><span data-stu-id="631b5-193">DeleteSelfServePolicy</span></span>
  * <span data-ttu-id="631b5-194">RemovePartnerRelationship</span><span class="sxs-lookup"><span data-stu-id="631b5-194">RemovePartnerRelationship</span></span>
  * <span data-ttu-id="631b5-195">DeleteTipCustomer</span><span class="sxs-lookup"><span data-stu-id="631b5-195">DeleteTipCustomer</span></span>
  * <span data-ttu-id="631b5-196">CreateRelatedReferral</span><span class="sxs-lookup"><span data-stu-id="631b5-196">CreateRelatedReferral</span></span>
  * <span data-ttu-id="631b5-197">UpdateRelatedReferral</span><span class="sxs-lookup"><span data-stu-id="631b5-197">UpdateRelatedReferral</span></span>

* <span data-ttu-id="631b5-198">Het maken van een serviceaanvraag is nu afgeschaft</span><span class="sxs-lookup"><span data-stu-id="631b5-198">Service request creation is now deprecated</span></span>
* <span data-ttu-id="631b5-199">Ondersteuningsonderwerpen zijn nu afgeschaft</span><span class="sxs-lookup"><span data-stu-id="631b5-199">Support topics are now deprecated</span></span>


## <a name="version-1161"></a><span data-ttu-id="631b5-200">Versie 1.16.1</span><span class="sxs-lookup"><span data-stu-id="631b5-200">Version 1.16.1</span></span>

<span data-ttu-id="631b5-201">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.1) v1.16.1 is nu algemeen beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-201">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.16.1) v1.16.1 is now general availability.</span></span> <span data-ttu-id="631b5-202">Bijgewerkte [GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-202">Updated [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="631b5-203">De volgende wijzigingen zijn opgenomen in deze versie:</span><span class="sxs-lookup"><span data-stu-id="631b5-203">The following changes are included in this version:</span></span>

<span data-ttu-id="631b5-204">We hebben de bestaande Microsoft-Partnercentrum-SDK gemigreerd van .NET Framework naar het .NET Standard 2.0-platform.</span><span class="sxs-lookup"><span data-stu-id="631b5-204">We have migrated the existing Microsoft Partner Center SDK from .NET Framework to .NET Standard 2.0 platform.</span></span> <span data-ttu-id="631b5-205">Hierdoor wordt de SDK compatibel met bestaande toepassingen met .NET Framework 4.6.1 en hoger.</span><span class="sxs-lookup"><span data-stu-id="631b5-205">This will make the SDK compatible with existing applications using .NET Framework 4.6.1 and above.</span></span> <span data-ttu-id="631b5-206">De SDK biedt ondersteuning voor .NET Core 2.0 en hoger.</span><span class="sxs-lookup"><span data-stu-id="631b5-206">The SDK will support .NET Core 2.0 and above.</span></span> <span data-ttu-id="631b5-207">Controleer [de ondersteuning voor .NET-implementatie](/dotnet/standard/net-standard) voordat u deze overplaatst naar bestaande toepassingen.</span><span class="sxs-lookup"><span data-stu-id="631b5-207">Check [.NET implementation support](/dotnet/standard/net-standard) before porting it to existing applications.</span></span>   


## <a name="version-1153"></a><span data-ttu-id="631b5-208">Versie 1.15.3</span><span class="sxs-lookup"><span data-stu-id="631b5-208">Version 1.15.3</span></span>
<span data-ttu-id="631b5-209">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.15.3) v1.15.3 is nu algemeen beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-209">[Microsoft Partner Center .NET SDK](https://www.nuget.org/packages/Microsoft.Store.PartnerCenter/1.15.3) v1.15.3 is now general availability.</span></span> <span data-ttu-id="631b5-210">Bijgewerkte REST [API's en GitHub zijn](https://github.com/Microsoft/Partner-Center-DotNet-Samples) ook beschikbaar.</span><span class="sxs-lookup"><span data-stu-id="631b5-210">Updated REST APIs and [GitHub samples](https://github.com/Microsoft/Partner-Center-DotNet-Samples) are also available.</span></span> <span data-ttu-id="631b5-211">De volgende wijzigingen zijn opgenomen in deze versie:</span><span class="sxs-lookup"><span data-stu-id="631b5-211">The following changes are included in this version:</span></span>

* <span data-ttu-id="631b5-212">Partnerovereenkomst</span><span class="sxs-lookup"><span data-stu-id="631b5-212">Partner Agreement</span></span>
  * <span data-ttu-id="631b5-213">Indirecte providers hebben de mogelijkheid toegevoegd om de [status Microsoft Partner-overeenkomst indirecte resellers te verifiëren.](verify-indirect-reseller-mpa-status.md)</span><span class="sxs-lookup"><span data-stu-id="631b5-213">Added the ability for indirect providers to [verify Microsoft Partner Agreement status of indirect resellers](verify-indirect-reseller-mpa-status.md).</span></span>
* <span data-ttu-id="631b5-214">Producten</span><span class="sxs-lookup"><span data-stu-id="631b5-214">Products</span></span>
  * <span data-ttu-id="631b5-215">De volgende twee interfaces zijn onjuist geplaatst onder de naamruimte Microsoft.Store.PartnerCenter.Products.</span><span class="sxs-lookup"><span data-stu-id="631b5-215">The following two interfaces were incorrectly placed under the Microsoft.Store.PartnerCenter.Products namespace.</span></span> <span data-ttu-id="631b5-216">Ze bevinden zich nu onder de naamruimte Microsoft.Store.PartnerCenter.Customers.Products.</span><span class="sxs-lookup"><span data-stu-id="631b5-216">Now, they are located under the Microsoft.Store.PartnerCenter.Customers.Products namespace.</span></span>
    * <span data-ttu-id="631b5-217">ICustomerProductByReservationScope</span><span class="sxs-lookup"><span data-stu-id="631b5-217">ICustomerProductByReservationScope</span></span>
    * <span data-ttu-id="631b5-218">ICustomerSkuByReservationScope</span><span class="sxs-lookup"><span data-stu-id="631b5-218">ICustomerSkuByReservationScope</span></span>
