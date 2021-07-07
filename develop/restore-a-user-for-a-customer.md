---
title: Een verwijderde gebruiker voor een klant herstellen
description: Een verwijderde gebruiker herstellen op klant-id en gebruikers-id.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 23caf91c6b29b292c2638b4a1ad208c606c47492
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445711"
---
# <a name="restore-a-deleted-user-for-a-customer"></a><span data-ttu-id="72f5e-103">Een verwijderde gebruiker voor een klant herstellen</span><span class="sxs-lookup"><span data-stu-id="72f5e-103">Restore a deleted user for a customer</span></span>

<span data-ttu-id="72f5e-104">Een verwijderde gebruiker herstellen op **klant-id** en gebruikers-id.</span><span class="sxs-lookup"><span data-stu-id="72f5e-104">How to restore a deleted **User** by customer ID and user ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="72f5e-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="72f5e-105">Prerequisites</span></span>

- <span data-ttu-id="72f5e-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="72f5e-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="72f5e-107">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="72f5e-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="72f5e-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="72f5e-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="72f5e-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="72f5e-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="72f5e-110">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="72f5e-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="72f5e-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="72f5e-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="72f5e-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="72f5e-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="72f5e-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="72f5e-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="72f5e-114">De gebruikers-id.</span><span class="sxs-lookup"><span data-stu-id="72f5e-114">The user ID.</span></span> <span data-ttu-id="72f5e-115">Zie Verwijderde gebruikers weergeven voor een klant als u niet over de gebruikers-id [hebt.](view-a-deleted-user.md)</span><span class="sxs-lookup"><span data-stu-id="72f5e-115">If you do not have the user ID, see [View deleted users for a customer](view-a-deleted-user.md).</span></span>

## <a name="when-can-you-restore-a-deleted-user-account"></a><span data-ttu-id="72f5e-116">Wanneer kunt u een verwijderd gebruikersaccount herstellen?</span><span class="sxs-lookup"><span data-stu-id="72f5e-116">When can you restore a deleted user account?</span></span>

<span data-ttu-id="72f5e-117">De gebruikerstoestand wordt ingesteld op 'inactief' wanneer u een gebruikersaccount verwijdert.</span><span class="sxs-lookup"><span data-stu-id="72f5e-117">The user state is set to "inactive" when you delete a user account.</span></span> <span data-ttu-id="72f5e-118">Dit blijft 30 dagen zo, waarna het gebruikersaccount en de bijbehorende gegevens worden verwijderd en onherkenbaar worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="72f5e-118">It remains that way for 30 days, after which the user account and its associated data are purged and made unrecoverable.</span></span> <span data-ttu-id="72f5e-119">U kunt een verwijderd gebruikersaccount alleen herstellen tijdens dit venster van 30 dagen.</span><span class="sxs-lookup"><span data-stu-id="72f5e-119">You can only restore a deleted user account during this 30-day window.</span></span> <span data-ttu-id="72f5e-120">Zodra het gebruikersaccount is verwijderd en als 'inactief' is gemarkeerd, wordt het niet meer geretourneerd als lid van de gebruikersverzameling (bijvoorbeeld met Een lijst met alle gebruikersaccounts voor een [klant ophalen).](get-a-list-of-all-user-accounts-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="72f5e-120">Once deleted and marked "inactive" the user account is no longer returned as a member of the user collection (for example, using [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span>

## <a name="c"></a><span data-ttu-id="72f5e-121">C\#</span><span class="sxs-lookup"><span data-stu-id="72f5e-121">C\#</span></span>

<span data-ttu-id="72f5e-122">Als u een gebruiker wilt herstellen, maakt u een nieuw exemplaar van de klasse [**CustomerUser**](/dotnet/api/microsoft.store.partnercenter.models.users.customeruser) en stelt u de waarde van de eigenschap [**User.State**](/dotnet/api/microsoft.store.partnercenter.models.users.user.state) in [**op UserState.Active.**](/dotnet/api/microsoft.store.partnercenter.models.users.userstate)</span><span class="sxs-lookup"><span data-stu-id="72f5e-122">To restore a user, create a new instance of the [**CustomerUser**](/dotnet/api/microsoft.store.partnercenter.models.users.customeruser) class, and set the value of the [**User.State**](/dotnet/api/microsoft.store.partnercenter.models.users.user.state) property to [**UserState.Active**](/dotnet/api/microsoft.store.partnercenter.models.users.userstate).</span></span>

<span data-ttu-id="72f5e-123">U herstelt een verwijderde gebruiker door de status van de gebruiker in te stellen op actief.</span><span class="sxs-lookup"><span data-stu-id="72f5e-123">You restore a deleted user by setting the user's state to active.</span></span> <span data-ttu-id="72f5e-124">U hoeft de resterende velden in de gebruikersresource niet opnieuw in tepopuleren.</span><span class="sxs-lookup"><span data-stu-id="72f5e-124">You do not have to repopulate the remaining fields in the user resource.</span></span> <span data-ttu-id="72f5e-125">Deze waarden worden automatisch hersteld vanuit de verwijderde, inactieve gebruikersresource.</span><span class="sxs-lookup"><span data-stu-id="72f5e-125">Those values will automatically be restored from the deleted, inactive user resource.</span></span> <span data-ttu-id="72f5e-126">Gebruik vervolgens de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren en de [**methode Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om de gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="72f5e-126">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the user.</span></span>

<span data-ttu-id="72f5e-127">Roep ten slotte de [**patchmethode aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.patch) en geef het **CustomerUser-exemplaar** door om de aanvraag voor het herstellen van de gebruiker te verzenden.</span><span class="sxs-lookup"><span data-stu-id="72f5e-127">Finally, call the [**Patch**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.patch) method and pass the **CustomerUser** instance to send the request to restore the user.</span></span>

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

<span data-ttu-id="72f5e-128">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="72f5e-128">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="72f5e-129">**Project**: Partnercentrum-SDK Samples **Class**: CustomerUserRestore.cs</span><span class="sxs-lookup"><span data-stu-id="72f5e-129">**Project**: Partner Center SDK Samples **Class**: CustomerUserRestore.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="72f5e-130">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="72f5e-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="72f5e-131">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="72f5e-131">Request syntax</span></span>

| <span data-ttu-id="72f5e-132">Methode</span><span class="sxs-lookup"><span data-stu-id="72f5e-132">Method</span></span>    | <span data-ttu-id="72f5e-133">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="72f5e-133">Request URI</span></span>                                                                                            |
|-----------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="72f5e-134">**Patch**</span><span class="sxs-lookup"><span data-stu-id="72f5e-134">**PATCH**</span></span> | <span data-ttu-id="72f5e-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="72f5e-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="72f5e-136">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="72f5e-136">URI parameter</span></span>

<span data-ttu-id="72f5e-137">Gebruik de volgende queryparameters om de klant-id en gebruikers-id op te geven.</span><span class="sxs-lookup"><span data-stu-id="72f5e-137">Use the following query parameters to specify the customer ID and user ID.</span></span>

| <span data-ttu-id="72f5e-138">Naam</span><span class="sxs-lookup"><span data-stu-id="72f5e-138">Name</span></span>                   | <span data-ttu-id="72f5e-139">Type</span><span class="sxs-lookup"><span data-stu-id="72f5e-139">Type</span></span>     | <span data-ttu-id="72f5e-140">Vereist</span><span class="sxs-lookup"><span data-stu-id="72f5e-140">Required</span></span> | <span data-ttu-id="72f5e-141">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="72f5e-141">Description</span></span>                                                                                                              |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="72f5e-142">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="72f5e-142">**customer-tenant-id**</span></span> | <span data-ttu-id="72f5e-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="72f5e-143">**guid**</span></span> | <span data-ttu-id="72f5e-144">J</span><span class="sxs-lookup"><span data-stu-id="72f5e-144">Y</span></span>        | <span data-ttu-id="72f5e-145">De waarde is een in GUID **opgemaakte klant-tenant-id** waarmee de reseller de resultaten kan filteren op een bepaalde klant.</span><span class="sxs-lookup"><span data-stu-id="72f5e-145">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results to a given customer.</span></span> |
| <span data-ttu-id="72f5e-146">**user-id**</span><span class="sxs-lookup"><span data-stu-id="72f5e-146">**user-id**</span></span>            | <span data-ttu-id="72f5e-147">**guid**</span><span class="sxs-lookup"><span data-stu-id="72f5e-147">**guid**</span></span> | <span data-ttu-id="72f5e-148">J</span><span class="sxs-lookup"><span data-stu-id="72f5e-148">Y</span></span>        | <span data-ttu-id="72f5e-149">De waarde is een guid-opgemaakte **gebruikers-id** die bij één gebruikersaccount hoort.</span><span class="sxs-lookup"><span data-stu-id="72f5e-149">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                         |

### <a name="request-headers"></a><span data-ttu-id="72f5e-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="72f5e-150">Request headers</span></span>

<span data-ttu-id="72f5e-151">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="72f5e-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="72f5e-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="72f5e-152">Request body</span></span>

<span data-ttu-id="72f5e-153">In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="72f5e-153">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="72f5e-154">Naam</span><span class="sxs-lookup"><span data-stu-id="72f5e-154">Name</span></span>       | <span data-ttu-id="72f5e-155">Type</span><span class="sxs-lookup"><span data-stu-id="72f5e-155">Type</span></span>   | <span data-ttu-id="72f5e-156">Vereist</span><span class="sxs-lookup"><span data-stu-id="72f5e-156">Required</span></span> | <span data-ttu-id="72f5e-157">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="72f5e-157">Description</span></span>                                                            |
|------------|--------|----------|------------------------------------------------------------------------|
| <span data-ttu-id="72f5e-158">Staat</span><span class="sxs-lookup"><span data-stu-id="72f5e-158">State</span></span>      | <span data-ttu-id="72f5e-159">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="72f5e-159">string</span></span> | <span data-ttu-id="72f5e-160">J</span><span class="sxs-lookup"><span data-stu-id="72f5e-160">Y</span></span>        | <span data-ttu-id="72f5e-161">De gebruikerstoestand.</span><span class="sxs-lookup"><span data-stu-id="72f5e-161">The user state.</span></span> <span data-ttu-id="72f5e-162">Als u een verwijderde gebruiker wilt herstellen, moet deze tekenreeks 'actief' bevatten.</span><span class="sxs-lookup"><span data-stu-id="72f5e-162">To restore a deleted user, this string must contain "active".</span></span> |
| <span data-ttu-id="72f5e-163">Kenmerken</span><span class="sxs-lookup"><span data-stu-id="72f5e-163">Attributes</span></span> | <span data-ttu-id="72f5e-164">object</span><span class="sxs-lookup"><span data-stu-id="72f5e-164">object</span></span> | <span data-ttu-id="72f5e-165">N</span><span class="sxs-lookup"><span data-stu-id="72f5e-165">N</span></span>        | <span data-ttu-id="72f5e-166">Bevat 'ObjectType': 'CustomerUser'.</span><span class="sxs-lookup"><span data-stu-id="72f5e-166">Contains "ObjectType": "CustomerUser".</span></span>                                 |

### <a name="request-example"></a><span data-ttu-id="72f5e-167">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="72f5e-167">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="72f5e-168">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="72f5e-168">REST response</span></span>

<span data-ttu-id="72f5e-169">Als dit lukt, retourneert het antwoord de herstelde gebruikersgegevens in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="72f5e-169">If successful, the response returns the restored user information in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="72f5e-170">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="72f5e-170">Response success and error codes</span></span>

<span data-ttu-id="72f5e-171">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="72f5e-171">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="72f5e-172">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="72f5e-172">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="72f5e-173">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="72f5e-173">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="72f5e-174">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="72f5e-174">Response example</span></span>

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
