---
title: Een verwijderde gebruiker voor een klant herstellen
description: Een verwijderde gebruiker herstellen op basis van klant-ID en gebruikers-ID.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9fd86a268c804a2fdd5efd67a8982afc043c95a6
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767527"
---
# <a name="restore-a-deleted-user-for-a-customer"></a><span data-ttu-id="1e9c2-103">Een verwijderde gebruiker voor een klant herstellen</span><span class="sxs-lookup"><span data-stu-id="1e9c2-103">Restore a deleted user for a customer</span></span>

<span data-ttu-id="1e9c2-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="1e9c2-104">**Applies To**</span></span>

- <span data-ttu-id="1e9c2-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="1e9c2-105">Partner Center</span></span>

<span data-ttu-id="1e9c2-106">Een verwijderde **gebruiker** herstellen op basis van klant-id en gebruikers-id.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-106">How to restore a deleted **User** by customer ID and user ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1e9c2-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="1e9c2-107">Prerequisites</span></span>

- <span data-ttu-id="1e9c2-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="1e9c2-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="1e9c2-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="1e9c2-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1e9c2-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="1e9c2-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="1e9c2-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="1e9c2-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="1e9c2-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="1e9c2-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="1e9c2-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="1e9c2-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="1e9c2-116">De gebruikers-ID.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-116">The user ID.</span></span> <span data-ttu-id="1e9c2-117">Als u de gebruikers-ID niet hebt, raadpleegt u [Verwijderde gebruikers voor een klant weer geven](view-a-deleted-user.md).</span><span class="sxs-lookup"><span data-stu-id="1e9c2-117">If you do not have the user ID, see [View deleted users for a customer](view-a-deleted-user.md).</span></span>

## <a name="when-can-you-restore-a-deleted-user-account"></a><span data-ttu-id="1e9c2-118">Wanneer kunt u een verwijderd gebruikers account herstellen?</span><span class="sxs-lookup"><span data-stu-id="1e9c2-118">When can you restore a deleted user account?</span></span>

<span data-ttu-id="1e9c2-119">De gebruikers status wordt ingesteld op ' inactief ' wanneer u een gebruikers account verwijdert.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-119">The user state is set to "inactive" when you delete a user account.</span></span> <span data-ttu-id="1e9c2-120">Gedurende dertig dagen blijft het de gebruikers account en de bijbehorende gegevens verwijderd en worden ze onherstelbaar gemaakt.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-120">It remains that way for thirty days, after which the user account and its associated data are purged and made unrecoverable.</span></span> <span data-ttu-id="1e9c2-121">U kunt een verwijderd gebruikers account alleen herstellen tijdens deze periode van dertig dagen.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-121">You can only restore a deleted user account during this thirty-day window.</span></span> <span data-ttu-id="1e9c2-122">Nadat het gebruikers account is verwijderd en gemarkeerd als ' inactief ', wordt het niet meer weer gegeven als lid van de gebruikers verzameling (bijvoorbeeld met behulp [van een lijst met alle gebruikers accounts voor een klant](get-a-list-of-all-user-accounts-for-a-customer.md)).</span><span class="sxs-lookup"><span data-stu-id="1e9c2-122">Once deleted and marked "inactive" the user account is no longer returned as a member of the user collection (for example, using [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span>

## <a name="c"></a><span data-ttu-id="1e9c2-123">C\#</span><span class="sxs-lookup"><span data-stu-id="1e9c2-123">C\#</span></span>

<span data-ttu-id="1e9c2-124">Als u een gebruiker wilt herstellen, maakt u een nieuw exemplaar van de klasse [**CustomerUser**](/dotnet/api/microsoft.store.partnercenter.models.users.customeruser) en stelt u de waarde van de eigenschap [**User. State**](/dotnet/api/microsoft.store.partnercenter.models.users.user.state) in op [**UserState. Active**](/dotnet/api/microsoft.store.partnercenter.models.users.userstate).</span><span class="sxs-lookup"><span data-stu-id="1e9c2-124">To restore a user, create a new instance of the [**CustomerUser**](/dotnet/api/microsoft.store.partnercenter.models.users.customeruser) class, and set the value of the [**User.State**](/dotnet/api/microsoft.store.partnercenter.models.users.user.state) property to [**UserState.Active**](/dotnet/api/microsoft.store.partnercenter.models.users.userstate).</span></span>

<span data-ttu-id="1e9c2-125">U herstelt een verwijderde gebruiker door de status van de gebruiker in te stellen op actief.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-125">You restore a deleted user by setting the user's state to active.</span></span> <span data-ttu-id="1e9c2-126">U hoeft de resterende velden niet opnieuw in te vullen in de gebruikers resource.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-126">You do not have to repopulate the remaining fields in the user resource.</span></span> <span data-ttu-id="1e9c2-127">Deze waarden worden automatisch hersteld op basis van de verwijderde, niet-actieve gebruikers resource.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-127">Those values will automatically be restored from the deleted, inactive user resource.</span></span> <span data-ttu-id="1e9c2-128">Gebruik vervolgens de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren en de [**gebruikers. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) -methode om de gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-128">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the user.</span></span>

<span data-ttu-id="1e9c2-129">Ten slotte roept u de [**patch**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.patch) -methode aan en geeft u het **CustomerUser** -exemplaar door om de aanvraag te verzenden om de gebruiker te herstellen.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-129">Finally, call the [**Patch**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.patch) method and pass the **CustomerUser** instance to send the request to restore the user.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedCustomerUserId;

var updatedCustomerUser = new CustomerUser()
{
    State = UserState.Active
};

// Restore customer user information.
var restoredCustomerUserInfo = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Patch(updatedCustomerUser);
```

<span data-ttu-id="1e9c2-130">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="1e9c2-130">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="1e9c2-131">**Project**: Partner Center SDK-voor beelden **klasse**: CustomerUserRestore.cs</span><span class="sxs-lookup"><span data-stu-id="1e9c2-131">**Project**: Partner Center SDK Samples **Class**: CustomerUserRestore.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="1e9c2-132">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="1e9c2-132">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="1e9c2-133">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1e9c2-133">Request syntax</span></span>

| <span data-ttu-id="1e9c2-134">Methode</span><span class="sxs-lookup"><span data-stu-id="1e9c2-134">Method</span></span>    | <span data-ttu-id="1e9c2-135">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="1e9c2-135">Request URI</span></span>                                                                                            |
|-----------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1e9c2-136">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="1e9c2-136">**PATCH**</span></span> | <span data-ttu-id="1e9c2-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users/{user-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="1e9c2-137">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="1e9c2-138">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="1e9c2-138">URI parameter</span></span>

<span data-ttu-id="1e9c2-139">Gebruik de volgende query parameters om de klant-id en gebruikers-id op te geven.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-139">Use the following query parameters to specify the customer id and user id.</span></span>

| <span data-ttu-id="1e9c2-140">Naam</span><span class="sxs-lookup"><span data-stu-id="1e9c2-140">Name</span></span>                   | <span data-ttu-id="1e9c2-141">Type</span><span class="sxs-lookup"><span data-stu-id="1e9c2-141">Type</span></span>     | <span data-ttu-id="1e9c2-142">Vereist</span><span class="sxs-lookup"><span data-stu-id="1e9c2-142">Required</span></span> | <span data-ttu-id="1e9c2-143">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1e9c2-143">Description</span></span>                                                                                                              |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="1e9c2-144">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="1e9c2-144">**customer-tenant-id**</span></span> | <span data-ttu-id="1e9c2-145">**guid**</span><span class="sxs-lookup"><span data-stu-id="1e9c2-145">**guid**</span></span> | <span data-ttu-id="1e9c2-146">J</span><span class="sxs-lookup"><span data-stu-id="1e9c2-146">Y</span></span>        | <span data-ttu-id="1e9c2-147">De waarde is een **klant-Tenant-id** die de wederverkoper toestaat de resultaten te filteren op een bepaalde klant.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-147">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results to a given customer.</span></span> |
| <span data-ttu-id="1e9c2-148">**gebruikers-id**</span><span class="sxs-lookup"><span data-stu-id="1e9c2-148">**user-id**</span></span>            | <span data-ttu-id="1e9c2-149">**guid**</span><span class="sxs-lookup"><span data-stu-id="1e9c2-149">**guid**</span></span> | <span data-ttu-id="1e9c2-150">J</span><span class="sxs-lookup"><span data-stu-id="1e9c2-150">Y</span></span>        | <span data-ttu-id="1e9c2-151">De waarde is een **gebruikers-id** met een GUID-indeling die tot één gebruikers account behoort.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-151">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                         |

### <a name="request-headers"></a><span data-ttu-id="1e9c2-152">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="1e9c2-152">Request headers</span></span>

<span data-ttu-id="1e9c2-153">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="1e9c2-153">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="1e9c2-154">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="1e9c2-154">Request body</span></span>

<span data-ttu-id="1e9c2-155">In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-155">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="1e9c2-156">Naam</span><span class="sxs-lookup"><span data-stu-id="1e9c2-156">Name</span></span>       | <span data-ttu-id="1e9c2-157">Type</span><span class="sxs-lookup"><span data-stu-id="1e9c2-157">Type</span></span>   | <span data-ttu-id="1e9c2-158">Vereist</span><span class="sxs-lookup"><span data-stu-id="1e9c2-158">Required</span></span> | <span data-ttu-id="1e9c2-159">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="1e9c2-159">Description</span></span>                                                            |
|------------|--------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="1e9c2-160">Staat</span><span class="sxs-lookup"><span data-stu-id="1e9c2-160">State</span></span>      | <span data-ttu-id="1e9c2-161">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="1e9c2-161">string</span></span> | <span data-ttu-id="1e9c2-162">J</span><span class="sxs-lookup"><span data-stu-id="1e9c2-162">Y</span></span>        | <span data-ttu-id="1e9c2-163">De gebruikers status.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-163">The user state.</span></span> <span data-ttu-id="1e9c2-164">Deze teken reeks moet ' Active ' bevatten om een verwijderde gebruiker te herstellen.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-164">To restore a deleted user, this string must contain "active".</span></span> |
| <span data-ttu-id="1e9c2-165">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="1e9c2-165">Attributes</span></span> | <span data-ttu-id="1e9c2-166">object</span><span class="sxs-lookup"><span data-stu-id="1e9c2-166">object</span></span> | <span data-ttu-id="1e9c2-167">N</span><span class="sxs-lookup"><span data-stu-id="1e9c2-167">N</span></span>        | <span data-ttu-id="1e9c2-168">Bevat "object type": "CustomerUser".</span><span class="sxs-lookup"><span data-stu-id="1e9c2-168">Contains "ObjectType": "CustomerUser".</span></span>                                 |

### <a name="request-example"></a><span data-ttu-id="1e9c2-169">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="1e9c2-169">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 6e668bc0-5bd7-44d6-b6fa-529d41ce9659
MS-CorrelationId: 32be760f-8282-4e01-a37b-829c8a700e8a
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 269
Expect: 100-continue

{
    "State": "active",
    "Attributes": {
        "ObjectType": "CustomerUser"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="1e9c2-170">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="1e9c2-170">REST response</span></span>

<span data-ttu-id="1e9c2-171">Als dit lukt, retourneert het antwoord de herstelde gebruikers gegevens in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-171">If successful, the response returns the restored user information in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="1e9c2-172">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="1e9c2-172">Response success and error codes</span></span>

<span data-ttu-id="1e9c2-173">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-173">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="1e9c2-174">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-174">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="1e9c2-175">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="1e9c2-175">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="1e9c2-176">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="1e9c2-176">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 465
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 32be760f-8282-4e01-a37b-829c8a700e8a
MS-RequestId: 6e668bc0-5bd7-44d6-b6fa-529d41ce9659
MS-CV: ZTeBriO7mEaiM13+.0
MS-ServerId: 101112616
Date: Fri, 20 Jan 2017 22:24:55 GMT

{
    "usageLocation": "US",
    "id": "a45f1416-3300-4f65-9e8d-f123b397a4ea",
    "userPrincipalName": "e83763f7f2204ac384cfcd49f79f2749@dtdemocspcustomer005.onmicrosoft.com",
    "firstName": "Ferdinand",
    "lastName": "Filibuster",
    "displayName": "Ferdinand",
    "userDomainType": "none",
    "state": "active",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "CustomerUser"
    }
}
```
