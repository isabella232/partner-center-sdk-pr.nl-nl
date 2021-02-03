---
title: Een relatie als reseller met een klant verwijderen
description: Een reseller-relatie verwijderen met een klant waarbij u geen trans acties meer hebt.
ms.date: 01/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 084797997e57c63b5c447379bb08ecb88ebd0cc4
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767462"
---
# <a name="remove-a-reseller-relationship-with-a-customer"></a><span data-ttu-id="382ec-103">Een relatie als reseller met een klant verwijderen</span><span class="sxs-lookup"><span data-stu-id="382ec-103">Remove a reseller relationship with a customer</span></span>

<span data-ttu-id="382ec-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="382ec-104">**Applies To**</span></span>

- <span data-ttu-id="382ec-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="382ec-105">Partner Center</span></span>

<span data-ttu-id="382ec-106">Een wederverkoper-relatie verwijderen met een klant waarbij u geen trans acties meer hebt.</span><span class="sxs-lookup"><span data-stu-id="382ec-106">Remove a reseller relationship with a customer that you no longer have transactions with.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="382ec-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="382ec-107">Prerequisites</span></span>

- <span data-ttu-id="382ec-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="382ec-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="382ec-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="382ec-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="382ec-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="382ec-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="382ec-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="382ec-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="382ec-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="382ec-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="382ec-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="382ec-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="382ec-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="382ec-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="382ec-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="382ec-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="382ec-116">Alle door Azure gereserveerde VM-exemplaar orders moeten worden geannuleerd voordat een reseller-relatie wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="382ec-116">All Azure Reserved VM Instance orders must be canceled before a reseller relationship is removed.</span></span> <span data-ttu-id="382ec-117">Neem contact op met Azure-ondersteuning voor het annuleren van openstaande Azure gereserveerde VM-instantie orders.</span><span class="sxs-lookup"><span data-stu-id="382ec-117">Call Azure support for canceling any open Azure Reserved VM Instance orders.</span></span>

## <a name="c"></a><span data-ttu-id="382ec-118">C\#</span><span class="sxs-lookup"><span data-stu-id="382ec-118">C\#</span></span>

<span data-ttu-id="382ec-119">Als u de reseller-relatie voor een klant wilt verwijderen, moet u er eerst voor zorgen dat alle actieve Azure Reserved VM Instances voor die klant worden geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="382ec-119">To remove the reseller relationship for a customer, first ensure that any active Azure Reserved VM Instances for that customer are canceled.</span></span> <span data-ttu-id="382ec-120">Zorg er vervolgens voor dat alle actieve abonnementen voor die klant worden opgeschort.</span><span class="sxs-lookup"><span data-stu-id="382ec-120">Next, ensure that all active subscriptions for that customer are suspended.</span></span> <span data-ttu-id="382ec-121">Om dit te doen, bepaalt u de ID van de klant voor wie u de reseller-relatie wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="382ec-121">To do so, determine the ID of the customer for whom you want to delete the reseller relationship.</span></span> <span data-ttu-id="382ec-122">In het volgende code voorbeeld wordt de gebruiker gevraagd de klant-id op te geven.</span><span class="sxs-lookup"><span data-stu-id="382ec-122">In the following code example, the user is prompted to provide the customer identifier.</span></span>

<span data-ttu-id="382ec-123">Om te bepalen of een Azure Reserved VM Instances voor de klant moet worden geannuleerd, haalt u de verzameling rechten op door de [**IAggregatePartner. Customers. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met behulp van de klant-id om de klant op te geven, en de eigenschap [**rechten**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) om een interface op te halen voor de verzamelings bewerkingen van rechten.</span><span class="sxs-lookup"><span data-stu-id="382ec-123">To determine if any Azure Reserved VM Instances for the customer must be canceled, retrieve the collection of entitlements by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and the [**Entitlements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to entitlement collection operations.</span></span> <span data-ttu-id="382ec-124">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) aan om de rechtings verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="382ec-124">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) method to retrieve the entitlement collection.</span></span> <span data-ttu-id="382ec-125">De verzameling filteren op rechten met een [**EntitlementType**](entitlement-resources.md#entitlementtype) -waarde van [**EntitlementType. VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) en, indien aanwezig, annuleren door ondersteuning aan te roepen voordat u doorgaat.</span><span class="sxs-lookup"><span data-stu-id="382ec-125">Filter the collection for any entitlements with an [**EntitlementType**](entitlement-resources.md#entitlementtype) value of [**EntitlementType.VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) and if there are any, cancel them by calling support before proceeding.</span></span>

<span data-ttu-id="382ec-126">Vervolgens haalt u een verzameling van de abonnementen van de klant op door de [**IAggregatePartner. Customers. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met behulp van de klant-id om de klant op te geven, en de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) om een interface op te halen voor het verzamelen van abonnementen.</span><span class="sxs-lookup"><span data-stu-id="382ec-126">Then, retrieve a collection of the customer's subscriptions by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to subscription collection operations.</span></span> <span data-ttu-id="382ec-127">Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) aan om de abonnementen verzameling van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="382ec-127">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) method to retrieve the customer's subscriptions collection.</span></span> <span data-ttu-id="382ec-128">Blader door de abonnements verzameling en zorg ervoor dat geen van de abonnementen een abonnement heeft. eigenschaps waarde voor [**status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) van [**SubscriptionStatus. Active**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span><span class="sxs-lookup"><span data-stu-id="382ec-128">Traverse the subscription collection and ensure that none of the subscriptions have a [**Subscriptions.Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property value of [**SubscriptionStatus.Active**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span> <span data-ttu-id="382ec-129">Als een abonnement nog steeds actief is, raadpleegt u [een abonnement opschorten](https://review.docs.microsoft.com/partner-center/develop/suspend-a-subscription) voor informatie over hoe u dit kunt onderbreken.</span><span class="sxs-lookup"><span data-stu-id="382ec-129">If a subscription is still active, see [Suspend a subscription](https://review.docs.microsoft.com/partner-center/develop/suspend-a-subscription) for information on how to suspend it.</span></span>

<span data-ttu-id="382ec-130">Nadat u hebt gecontroleerd of alle actieve Azure Reserved VM Instances voor die klant zijn geannuleerd en alle actieve abonnementen zijn onderbroken, kunt u de reseller-relatie voor de klant verwijderen.</span><span class="sxs-lookup"><span data-stu-id="382ec-130">After confirming that all active Azure Reserved VM Instances for that customer are canceled and all active subscriptions are suspended, you can remove the reseller relationship for the customer.</span></span> <span data-ttu-id="382ec-131">Maak eerst een nieuw object [klant/DotNet/API/Microsoft. Store. partnercenter. Models. klanten. Customer) met de eigenschap [Customer. RelationshipToPartner/DotNet/API/micro soft. Store. partnercenter. Models. custom. Customer. RelationshipToPartner) ingesteld op [**CustomerPartnerRelationship. none**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship).</span><span class="sxs-lookup"><span data-stu-id="382ec-131">First, create a new [Customer/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object with the [Customer.RelationshipToPartner/dotnet/api/microsoft.store.partnercenter.models.customers.customer.relationshiptopartner) property set to [**CustomerPartnerRelationship.None**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship).</span></span> <span data-ttu-id="382ec-132">Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant op te geven en de **patch** -methode aan te roepen, in het nieuwe klant object door te geven.</span><span class="sxs-lookup"><span data-stu-id="382ec-132">Then call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and call the **Patch** method, passing in the new customer object.</span></span>

<span data-ttu-id="382ec-133">Als u de relatie opnieuw tot stand wilt brengen, herhaalt u het proces van [een reseller Relationship/Partner Center/partnership/Request-reseller-Relationship).</span><span class="sxs-lookup"><span data-stu-id="382ec-133">To re-establish the relationship, repeat the process of [requesting a reseller relationship/partner-center/develop/request-reseller-relationship).</span></span>

``` csharp
// IAggregatePartner partnerOperations;

// Prompt the user the enter the customer ID.
var customerIdToDeleteRelationshipOf = this.Context.ConsoleHelper.ReadNonEmptyString("Please enter the ID of the customer you want to delete the relationship with", "The customer ID can't be empty");

// Determine if there are any active Azure Reserved VM Instances for this customer.
ResourceCollection<Entitlement> entitlements = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Entitlements.Get();

If (entitlements.Items.Where(x => x.EntitlementType == EntitlementType.VirtualMachineReservedInstance).Any())
{
    this.Context.ConsoleHelper.Warning("Please cancel Azure Reserved Virtual Machine Instance orders through support and try again. Aborting the delete customer relationship operation");
               return;
}

// Verify that there are no active subscriptions.
ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Subscriptions.Get();
IList<Subscription> subscriptions = new List<Subscription>(customerSubscriptions.Items);

foreach (Subscription customerSubscription in subscriptions)
{
    if (customerSubscription.Status == SubscriptionStatus.Active)
    {
        this.Context.ConsoleHelper.Warning(String.Format("Subscription with ID :{0}  OfferName: {1} cannot be in active state, ", customerSubscription.Id, customerSubscription.OfferName));
        this.Context.ConsoleHelper.Warning("Please Suspend all the Subscriptions and try again. Aborting the delete customer relationship operation");
               return;
    }
}

// Delete the customer's relationship to the partner.
Customer customer = new Customer();
customer.RelationshipToPartner = CustomerPartnerRelationship.None;
customer = partnerOperations.Customers.ById(customerIdToDeleteRelationshipOf).Patch(customer);

if (customer.RelationshipToPartner == CustomerPartnerRelationship.None)
{
    this.Context.ConsoleHelper.Success("Customer Partner Relationship successfully deleted");
}
```

<span data-ttu-id="382ec-134">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="382ec-134">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="382ec-135">**Project**: PartnerSDK. FeatureSample- **klasse**: DeletePartnerCustomerRelationship.cs</span><span class="sxs-lookup"><span data-stu-id="382ec-135">**Project**: PartnerSDK.FeatureSample **Class**: DeletePartnerCustomerRelationship.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="382ec-136">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="382ec-136">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="382ec-137">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="382ec-137">Request syntax</span></span>

| <span data-ttu-id="382ec-138">Methode</span><span class="sxs-lookup"><span data-stu-id="382ec-138">Method</span></span>     | <span data-ttu-id="382ec-139">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="382ec-139">Request URI</span></span>                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="382ec-140">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="382ec-140">**PATCH**</span></span>  | <span data-ttu-id="382ec-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/http/1.1</span><span class="sxs-lookup"><span data-stu-id="382ec-141">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/ HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="382ec-142">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="382ec-142">URI parameter</span></span>

<span data-ttu-id="382ec-143">Deze tabel bevat de vereiste query parameters voor het verwijderen van een reseller-relatie.</span><span class="sxs-lookup"><span data-stu-id="382ec-143">This table lists the required query parameters to remove a reseller relationship.</span></span>

| <span data-ttu-id="382ec-144">Naam</span><span class="sxs-lookup"><span data-stu-id="382ec-144">Name</span></span>                   | <span data-ttu-id="382ec-145">Type</span><span class="sxs-lookup"><span data-stu-id="382ec-145">Type</span></span>     | <span data-ttu-id="382ec-146">Vereist</span><span class="sxs-lookup"><span data-stu-id="382ec-146">Required</span></span> | <span data-ttu-id="382ec-147">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="382ec-147">Description</span></span>                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="382ec-148">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="382ec-148">**customer-tenant-id**</span></span> | <span data-ttu-id="382ec-149">**guid**</span><span class="sxs-lookup"><span data-stu-id="382ec-149">**guid**</span></span> | <span data-ttu-id="382ec-150">J</span><span class="sxs-lookup"><span data-stu-id="382ec-150">Y</span></span>        | <span data-ttu-id="382ec-151">De waarde is een **klant-Tenant-id** die de klant aanduidt.</span><span class="sxs-lookup"><span data-stu-id="382ec-151">The value is a GUID formatted **customer-tenant-id** that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="382ec-152">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="382ec-152">Request headers</span></span>

<span data-ttu-id="382ec-153">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="382ec-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="382ec-154">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="382ec-154">Request body</span></span>

<span data-ttu-id="382ec-155">Een **klant** resource is vereist in de aanvraag tekst.</span><span class="sxs-lookup"><span data-stu-id="382ec-155">A **Customer** resource is required in the request body.</span></span> <span data-ttu-id="382ec-156">Zorg ervoor dat de eigenschap **RelationshipToPartner** is ingesteld op geen.</span><span class="sxs-lookup"><span data-stu-id="382ec-156">Ensure the **RelationshipToPartner** property has been set to none.</span></span>

### <a name="request-example"></a><span data-ttu-id="382ec-157">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="382ec-157">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id> HTTP/1.1
Authorization: Bearer <token>
Content-Length: 74
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 9b4bf2ca-f374-4d51-9113-781ca87b8380
MS-RequestId: 9fef8b23-6e3e-45d2-8678-e9fe89c35af5
Date: Fri, 12 Jan 2018 00:31:55 GMT

{
    "relationshipToPartner":"none",
    "attributes":{
        "objectType":"Customer"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="382ec-158">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="382ec-158">REST response</span></span>

<span data-ttu-id="382ec-159">Als deze methode is geslaagd, wordt een reseller-relatie voor de opgegeven klant verwijderd.</span><span class="sxs-lookup"><span data-stu-id="382ec-159">If successful, this method removes a reseller relationship for the specified customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="382ec-160">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="382ec-160">Response success and error codes</span></span>

<span data-ttu-id="382ec-161">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="382ec-161">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="382ec-162">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="382ec-162">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="382ec-163">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="382ec-163">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="382ec-164">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="382ec-164">Response example</span></span>

```http
HTTP/1.1 200 OK
MS-RequestId: 7988dde4-b516-472c-b226-6d53fb18f04e
MS-CorrelationId: 9b4bf2ca-f374-4d51-9113-781ca87b8380
X-Locale: en-US
Content-Type: application/json
Content-Length: 242
Expect: 100-continue

{
    "Id":null,
    "CommerceId":null,
    "CompanyProfile":null,
    "BillingProfile":null,
    "RelationshipToPartner":"none",
    "AllowDelegatedAccess":null,
    "UserCredentials":null,
    "CustomDomains":null,
    "AssociatedPartnerId":null,
    "Attributes":{
        "ObjectType":"Customer"
    }
}
```
