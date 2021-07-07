---
title: Een relatie als reseller met een klant verwijderen
description: Het verwijderen van een resellerrelatie met een klant met wie u geen transacties meer hebt.
ms.date: 01/12/2018
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 45eca3564c3b9078e04d1f8155d08849a589d52f
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446595"
---
# <a name="remove-a-reseller-relationship-with-a-customer"></a><span data-ttu-id="5ca32-103">Een relatie als reseller met een klant verwijderen</span><span class="sxs-lookup"><span data-stu-id="5ca32-103">Remove a reseller relationship with a customer</span></span>

<span data-ttu-id="5ca32-104">Verwijder een resellerrelatie met een klant met wie u geen transacties meer hebt.</span><span class="sxs-lookup"><span data-stu-id="5ca32-104">Remove a reseller relationship with a customer that you no longer have transactions with.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5ca32-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5ca32-105">Prerequisites</span></span>

- <span data-ttu-id="5ca32-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5ca32-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5ca32-107">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="5ca32-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="5ca32-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5ca32-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5ca32-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="5ca32-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5ca32-110">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="5ca32-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5ca32-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="5ca32-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5ca32-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="5ca32-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5ca32-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5ca32-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="5ca32-114">Alle orders voor gereserveerde VM-instanties van Azure moeten worden geannuleerd voordat een resellerrelatie wordt verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5ca32-114">All Azure Reserved VM Instance orders must be canceled before a reseller relationship is removed.</span></span> <span data-ttu-id="5ca32-115">Roep ondersteuning voor Azure voor het annuleren van openstaande orders voor gereserveerde Azure-VM-instanties.</span><span class="sxs-lookup"><span data-stu-id="5ca32-115">Call Azure support for canceling any open Azure Reserved VM Instance orders.</span></span>

## <a name="c"></a><span data-ttu-id="5ca32-116">C\#</span><span class="sxs-lookup"><span data-stu-id="5ca32-116">C\#</span></span>

<span data-ttu-id="5ca32-117">Als u de resellerrelatie voor een klant wilt verwijderen, moet u er eerst voor zorgen dat alle actieve Azure Reserved VM Instances voor die klant worden geannuleerd.</span><span class="sxs-lookup"><span data-stu-id="5ca32-117">To remove the reseller relationship for a customer, first ensure that any active Azure Reserved VM Instances for that customer are canceled.</span></span> <span data-ttu-id="5ca32-118">Controleer vervolgens of alle actieve abonnementen voor die klant zijn opgeschort.</span><span class="sxs-lookup"><span data-stu-id="5ca32-118">Next, ensure that all active subscriptions for that customer are suspended.</span></span> <span data-ttu-id="5ca32-119">Om dit te doen, bepaalt u de id van de klant voor wie u de resellerrelatie wilt verwijderen.</span><span class="sxs-lookup"><span data-stu-id="5ca32-119">To do so, determine the ID of the customer for whom you want to delete the reseller relationship.</span></span> <span data-ttu-id="5ca32-120">In het volgende codevoorbeeld wordt de gebruiker gevraagd de klant-id op te geven.</span><span class="sxs-lookup"><span data-stu-id="5ca32-120">In the following code example, the user is prompted to provide the customer identifier.</span></span>

<span data-ttu-id="5ca32-121">Om te bepalen of een Azure Reserved VM Instances voor de klant moet worden geannuleerd, haalt u de verzameling rechten op door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met behulp van de klant-id om de klant op te geven en de eigenschap [**Entitlements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) om een interface voor rechtenverzamelingsbewerkingen op te halen.</span><span class="sxs-lookup"><span data-stu-id="5ca32-121">To determine if any Azure Reserved VM Instances for the customer must be canceled, retrieve the collection of entitlements by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and the [**Entitlements**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to entitlement collection operations.</span></span> <span data-ttu-id="5ca32-122">Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) om de rechtenverzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="5ca32-122">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) method to retrieve the entitlement collection.</span></span> <span data-ttu-id="5ca32-123">Filter de verzameling op rechten met de waarde [**EntitlementType.VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) en annuleer deze door ondersteuning aan te roepen voordat u doorgaat. [](entitlement-resources.md#entitlementtype)</span><span class="sxs-lookup"><span data-stu-id="5ca32-123">Filter the collection for any entitlements with an [**EntitlementType**](entitlement-resources.md#entitlementtype) value of [**EntitlementType.VirtualMachineReservedInstance**](entitlement-resources.md#entitlementtype) and if there are any, cancel them by calling support before proceeding.</span></span>

<span data-ttu-id="5ca32-124">Haal vervolgens een verzameling van de abonnementen van de klant op door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met behulp van de klant-id om de klant op te geven en de eigenschap Abonnementen om een interface op te halen voor bewerkingen voor het verzamelen van abonnementen. [](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions)</span><span class="sxs-lookup"><span data-stu-id="5ca32-124">Then, retrieve a collection of the customer's subscriptions by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to subscription collection operations.</span></span> <span data-ttu-id="5ca32-125">Roep ten slotte de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) om de verzameling abonnementen van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="5ca32-125">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) method to retrieve the customer's subscriptions collection.</span></span> <span data-ttu-id="5ca32-126">Doorkruis de abonnementsverzameling en zorg ervoor dat geen van de abonnementen de [**eigenschapswaarde Subscriptions.Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) van [**SubscriptionStatus.Active heeft.**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus)</span><span class="sxs-lookup"><span data-stu-id="5ca32-126">Traverse the subscription collection and ensure that none of the subscriptions have a [**Subscriptions.Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property value of [**SubscriptionStatus.Active**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span> <span data-ttu-id="5ca32-127">Als een abonnement nog steeds actief is, zie [Abonnement opschorten voor](suspend-a-subscription.md) informatie over het opschorten van het abonnement.</span><span class="sxs-lookup"><span data-stu-id="5ca32-127">If a subscription is still active, see [Suspend a subscription](suspend-a-subscription.md) for information on how to suspend it.</span></span>

<span data-ttu-id="5ca32-128">Nadat u hebt bevestigd dat alle actieve Azure Reserved VM Instances voor die klant zijn geannuleerd en alle actieve abonnementen zijn opgeschort, kunt u de resellerrelatie voor de klant verwijderen.</span><span class="sxs-lookup"><span data-stu-id="5ca32-128">After confirming that all active Azure Reserved VM Instances for that customer are canceled and all active subscriptions are suspended, you can remove the reseller relationship for the customer.</span></span> <span data-ttu-id="5ca32-129">Maak eerst een nieuw object [Customer/dotnet/api/microsoft.store.partnercenter.models.customers.customer) met de eigenschap [Customer.RelationshipToPartner/dotnet/api/microsoft.store.partnercenter.models.customers.customer.relationshiptopartner) ingesteld op [**CustomerPartnerRelationship.None.**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship)</span><span class="sxs-lookup"><span data-stu-id="5ca32-129">First, create a new [Customer/dotnet/api/microsoft.store.partnercenter.models.customers.customer) object with the [Customer.RelationshipToPartner/dotnet/api/microsoft.store.partnercenter.models.customers.customer.relationshiptopartner) property set to [**CustomerPartnerRelationship.None**](/dotnet/api/microsoft.store.partnercenter.models.customers.customerpartnerrelationship).</span></span> <span data-ttu-id="5ca32-130">Roep vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met behulp van de klant-id om de klant op te geven en roep de **patchmethode** aan, waarbij het nieuwe klantobject wordt doorgeven.</span><span class="sxs-lookup"><span data-stu-id="5ca32-130">Then call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method using the customer identifier to specify the customer, and call the **Patch** method, passing in the new customer object.</span></span>

<span data-ttu-id="5ca32-131">Als u de relatie opnieuw tot stand wilt brengen, herhaalt u het proces van [een resellerrelatie aanvragen/partnercentrum/develop/request-reseller-relationship).</span><span class="sxs-lookup"><span data-stu-id="5ca32-131">To re-establish the relationship, repeat the process of [requesting a reseller relationship/partner-center/develop/request-reseller-relationship).</span></span>

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

<span data-ttu-id="5ca32-132">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="5ca32-132">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="5ca32-133">**Project:** PartnerSDK.FeatureSample-klasse: DeletePartnerCustomerRelationship.cs </span><span class="sxs-lookup"><span data-stu-id="5ca32-133">**Project**: PartnerSDK.FeatureSample **Class**: DeletePartnerCustomerRelationship.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="5ca32-134">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="5ca32-134">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5ca32-135">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="5ca32-135">Request syntax</span></span>

| <span data-ttu-id="5ca32-136">Methode</span><span class="sxs-lookup"><span data-stu-id="5ca32-136">Method</span></span>     | <span data-ttu-id="5ca32-137">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="5ca32-137">Request URI</span></span>                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5ca32-138">**Patch**</span><span class="sxs-lookup"><span data-stu-id="5ca32-138">**PATCH**</span></span>  | <span data-ttu-id="5ca32-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/ HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="5ca32-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/ HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="5ca32-140">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="5ca32-140">URI parameter</span></span>

<span data-ttu-id="5ca32-141">Deze tabel bevat de vereiste queryparameters voor het verwijderen van een resellerrelatie.</span><span class="sxs-lookup"><span data-stu-id="5ca32-141">This table lists the required query parameters to remove a reseller relationship.</span></span>

| <span data-ttu-id="5ca32-142">Naam</span><span class="sxs-lookup"><span data-stu-id="5ca32-142">Name</span></span>                   | <span data-ttu-id="5ca32-143">Type</span><span class="sxs-lookup"><span data-stu-id="5ca32-143">Type</span></span>     | <span data-ttu-id="5ca32-144">Vereist</span><span class="sxs-lookup"><span data-stu-id="5ca32-144">Required</span></span> | <span data-ttu-id="5ca32-145">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5ca32-145">Description</span></span>                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="5ca32-146">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="5ca32-146">**customer-tenant-id**</span></span> | <span data-ttu-id="5ca32-147">**guid**</span><span class="sxs-lookup"><span data-stu-id="5ca32-147">**guid**</span></span> | <span data-ttu-id="5ca32-148">J</span><span class="sxs-lookup"><span data-stu-id="5ca32-148">Y</span></span>        | <span data-ttu-id="5ca32-149">De waarde is een in GUID **opgemaakte klant-tenant-id** die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="5ca32-149">The value is a GUID formatted **customer-tenant-id** that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5ca32-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="5ca32-150">Request headers</span></span>

<span data-ttu-id="5ca32-151">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="5ca32-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5ca32-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="5ca32-152">Request body</span></span>

<span data-ttu-id="5ca32-153">Een **klantresource** is vereist in de aanvraag body.</span><span class="sxs-lookup"><span data-stu-id="5ca32-153">A **Customer** resource is required in the request body.</span></span> <span data-ttu-id="5ca32-154">Zorg ervoor **dat de eigenschap RelationshipToPartner** is ingesteld op geen.</span><span class="sxs-lookup"><span data-stu-id="5ca32-154">Ensure the **RelationshipToPartner** property has been set to none.</span></span>

### <a name="request-example"></a><span data-ttu-id="5ca32-155">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5ca32-155">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="5ca32-156">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="5ca32-156">REST response</span></span>

<span data-ttu-id="5ca32-157">Als dit lukt, wordt met deze methode een resellerrelatie voor de opgegeven klant verwijderd.</span><span class="sxs-lookup"><span data-stu-id="5ca32-157">If successful, this method removes a reseller relationship for the specified customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5ca32-158">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="5ca32-158">Response success and error codes</span></span>

<span data-ttu-id="5ca32-159">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="5ca32-159">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5ca32-160">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="5ca32-160">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5ca32-161">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="5ca32-161">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5ca32-162">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="5ca32-162">Response example</span></span>

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
