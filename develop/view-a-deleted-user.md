---
title: Verwijderde gebruikers voor een klant weergeven
description: Hiermee wordt een lijst met verwijderde CustomerUser-resources voor een klant opgehaald op basis van de klant-ID. U kunt desgewenst een pagina grootte instellen. U moet een filter opgeven.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9b1a9b85e3eba7ae7ec1dab8e951134d03371604
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767439"
---
# <a name="view-deleted-users-for-a-customer"></a><span data-ttu-id="5506f-105">Verwijderde gebruikers voor een klant weergeven</span><span class="sxs-lookup"><span data-stu-id="5506f-105">View deleted users for a customer</span></span>

<span data-ttu-id="5506f-106">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="5506f-106">**Applies To**</span></span>

- <span data-ttu-id="5506f-107">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="5506f-107">Partner Center</span></span>

<span data-ttu-id="5506f-108">Hiermee wordt een lijst met verwijderde CustomerUser-resources voor een klant opgehaald op basis van de klant-ID.</span><span class="sxs-lookup"><span data-stu-id="5506f-108">Gets a list of deleted CustomerUser resources for a customer by customer ID.</span></span> <span data-ttu-id="5506f-109">U kunt desgewenst een pagina grootte instellen.</span><span class="sxs-lookup"><span data-stu-id="5506f-109">You can optionally set a page size.</span></span> <span data-ttu-id="5506f-110">U moet een filter opgeven.</span><span class="sxs-lookup"><span data-stu-id="5506f-110">You must supply a filter.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5506f-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="5506f-111">Prerequisites</span></span>

- <span data-ttu-id="5506f-112">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="5506f-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="5506f-113">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="5506f-113">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="5506f-114">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5506f-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="5506f-115">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="5506f-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="5506f-116">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="5506f-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="5506f-117">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="5506f-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="5506f-118">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="5506f-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="5506f-119">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="5506f-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="what-happens-when-you-delete-a-user-account"></a><span data-ttu-id="5506f-120">Wat gebeurt er wanneer u een gebruikers account verwijdert?</span><span class="sxs-lookup"><span data-stu-id="5506f-120">What happens when you delete a user account?</span></span>

<span data-ttu-id="5506f-121">De gebruikers status wordt ingesteld op ' inactief ' wanneer u een gebruikers account verwijdert.</span><span class="sxs-lookup"><span data-stu-id="5506f-121">The user state is set to "inactive" when you delete a user account.</span></span> <span data-ttu-id="5506f-122">Gedurende dertig dagen blijft het de gebruikers account en de bijbehorende gegevens verwijderd en worden ze onherstelbaar gemaakt.</span><span class="sxs-lookup"><span data-stu-id="5506f-122">It remains that way for thirty days, after which the user account and its associated data are purged and made unrecoverable.</span></span> <span data-ttu-id="5506f-123">Als u een verwijderd gebruikers account in het venster van de dertig dag wilt herstellen, raadpleegt u [een verwijderde gebruiker herstellen voor een klant](restore-a-user-for-a-customer.md).</span><span class="sxs-lookup"><span data-stu-id="5506f-123">If you want to restore a deleted user account within the thirty day window, see [Restore a deleted user for a customer](restore-a-user-for-a-customer.md).</span></span> <span data-ttu-id="5506f-124">Eenmaal verwijderd en gemarkeerd als ' inactief ', wordt het gebruikers account niet langer geretourneerd als lid van de gebruikers verzameling (bijvoorbeeld met behulp [van een lijst met alle gebruikers accounts voor een klant ophalen](get-a-list-of-all-user-accounts-for-a-customer.md)).</span><span class="sxs-lookup"><span data-stu-id="5506f-124">Once deleted and marked "inactive", the user account is no longer returned as a member of the user collection (for example, using [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span> <span data-ttu-id="5506f-125">Als u een lijst wilt weer geven met verwijderde gebruikers die nog niet zijn opgeschoond, moet u een query uitvoeren voor gebruikers accounts die zijn ingesteld op inactief.</span><span class="sxs-lookup"><span data-stu-id="5506f-125">To get a list of deleted users that have not yet been purged, you must query for user accounts that have been set to inactive.</span></span>

## <a name="c"></a><span data-ttu-id="5506f-126">C\#</span><span class="sxs-lookup"><span data-stu-id="5506f-126">C\#</span></span>

<span data-ttu-id="5506f-127">Als u een lijst met verwijderde gebruikers wilt ophalen, moet u een query maken die filtert op klant gebruikers waarvan de status is ingesteld op inactief.</span><span class="sxs-lookup"><span data-stu-id="5506f-127">To retrieve a list of deleted users, construct a query that filters for customer users whose status is set to inactive.</span></span> <span data-ttu-id="5506f-128">Maak eerst het filter door een [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) -object te instantiëren met de para meters, zoals wordt weer gegeven in het volgende code fragment.</span><span class="sxs-lookup"><span data-stu-id="5506f-128">First, create the filter by instantiating a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object with the parameters as shown in the following code snippet.</span></span> <span data-ttu-id="5506f-129">Maak vervolgens de query met behulp van de methode [**BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) .</span><span class="sxs-lookup"><span data-stu-id="5506f-129">Then create the query using the [**BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) method.</span></span> <span data-ttu-id="5506f-130">Als u geen pagina-resultaten wilt, kunt u in plaats daarvan de [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) -methode gebruiken.</span><span class="sxs-lookup"><span data-stu-id="5506f-130">If you do not want paged results, you can use the [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method instead.</span></span> <span data-ttu-id="5506f-131">Gebruik vervolgens de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="5506f-131">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="5506f-132">Roep ten slotte de [**query**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.query) methode aan om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="5506f-132">Finally, call the [**Query**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.query) method to send the request.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// int customerUserPageSize;

// Create a filter for users whose status is inactive (i.e. deleted).
var filter = new SimpleFieldFilter("UserState", FieldFilterOperation.Equals, "Inactive");

// Build a paged query.
var simpleQueryWithFilter = QueryFactory.Instance.BuildIndexedQuery(customerUserPageSize, 0, filter);

// Send the request.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.Query(simpleQueryWithFilter);
```

<span data-ttu-id="5506f-133">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="5506f-133">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="5506f-134">**Project**: Partner Center SDK-voor beelden **klasse**: GetCustomerInactiveUsers.cs</span><span class="sxs-lookup"><span data-stu-id="5506f-134">**Project**: Partner Center SDK Samples **Class**: GetCustomerInactiveUsers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="5506f-135">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="5506f-135">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="5506f-136">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5506f-136">Request syntax</span></span>

| <span data-ttu-id="5506f-137">Methode</span><span class="sxs-lookup"><span data-stu-id="5506f-137">Method</span></span>  | <span data-ttu-id="5506f-138">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="5506f-138">Request URI</span></span>                                                                                                       |
|---------|-------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5506f-139">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="5506f-139">**GET**</span></span> | <span data-ttu-id="5506f-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/users? grootte = {size} &filter = {filter} http/1.1</span><span class="sxs-lookup"><span data-stu-id="5506f-140">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users?size={size}&filter={filter} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="5506f-141">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="5506f-141">URI parameter</span></span>

<span data-ttu-id="5506f-142">Gebruik de volgende pad-en query parameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="5506f-142">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="5506f-143">Naam</span><span class="sxs-lookup"><span data-stu-id="5506f-143">Name</span></span>        | <span data-ttu-id="5506f-144">Type</span><span class="sxs-lookup"><span data-stu-id="5506f-144">Type</span></span>   | <span data-ttu-id="5506f-145">Vereist</span><span class="sxs-lookup"><span data-stu-id="5506f-145">Required</span></span> | <span data-ttu-id="5506f-146">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="5506f-146">Description</span></span>                                                                                                                                                                        |
|-------------|--------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="5506f-147">klant-id</span><span class="sxs-lookup"><span data-stu-id="5506f-147">customer-id</span></span> | <span data-ttu-id="5506f-148">guid</span><span class="sxs-lookup"><span data-stu-id="5506f-148">guid</span></span>   | <span data-ttu-id="5506f-149">Yes</span><span class="sxs-lookup"><span data-stu-id="5506f-149">Yes</span></span>      | <span data-ttu-id="5506f-150">De waarde is een klant-id met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="5506f-150">The value is a GUID formatted customer-id that identifies the customer.</span></span>                                                                                                            |
| <span data-ttu-id="5506f-151">grootte</span><span class="sxs-lookup"><span data-stu-id="5506f-151">size</span></span>        | <span data-ttu-id="5506f-152">int</span><span class="sxs-lookup"><span data-stu-id="5506f-152">int</span></span>    | <span data-ttu-id="5506f-153">No</span><span class="sxs-lookup"><span data-stu-id="5506f-153">No</span></span>       | <span data-ttu-id="5506f-154">Het aantal resultaten dat tegelijk moet worden weer gegeven.</span><span class="sxs-lookup"><span data-stu-id="5506f-154">The number of results to be displayed at one time.</span></span> <span data-ttu-id="5506f-155">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="5506f-155">This parameter is optional.</span></span>                                                                                                     |
| <span data-ttu-id="5506f-156">filter</span><span class="sxs-lookup"><span data-stu-id="5506f-156">filter</span></span>      | <span data-ttu-id="5506f-157">filter</span><span class="sxs-lookup"><span data-stu-id="5506f-157">filter</span></span> | <span data-ttu-id="5506f-158">Yes</span><span class="sxs-lookup"><span data-stu-id="5506f-158">Yes</span></span>      | <span data-ttu-id="5506f-159">De query die de zoek opdracht van de gebruiker filtert.</span><span class="sxs-lookup"><span data-stu-id="5506f-159">The query that filters the user search.</span></span> <span data-ttu-id="5506f-160">Als u verwijderde gebruikers wilt ophalen, moet u de volgende teken reeks insluiten en coderen: {"veld": "UserState", "waarde": "inactieve", "operator": "is gelijk aan"}.</span><span class="sxs-lookup"><span data-stu-id="5506f-160">To retrieve deleted users, you must include and encode the following string: {"Field":"UserState","Value":"Inactive","Operator":"equals"}.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="5506f-161">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="5506f-161">Request headers</span></span>

<span data-ttu-id="5506f-162">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="5506f-162">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="5506f-163">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="5506f-163">Request body</span></span>

<span data-ttu-id="5506f-164">Geen.</span><span class="sxs-lookup"><span data-stu-id="5506f-164">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="5506f-165">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="5506f-165">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users?size=500&filter=%7B%22Field%22%3A%22UserState%22%2C%22Value%22%3A%22Inactive%22%2C%22Operator%22%3A%22equals%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c11feb95-55d2-45b6-9d1b-74b55d2221fb
MS-CorrelationId: 2b4ab588-f48c-4874-b479-a61895e107b2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="5506f-166">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="5506f-166">REST response</span></span>

<span data-ttu-id="5506f-167">Als dit lukt, retourneert deze methode een verzameling [CustomerUser](user-resources.md#customeruser) -resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="5506f-167">If successful, this method returns a collection of [CustomerUser](user-resources.md#customeruser) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="5506f-168">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="5506f-168">Response success and error codes</span></span>

<span data-ttu-id="5506f-169">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="5506f-169">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="5506f-170">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="5506f-170">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="5506f-171">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="5506f-171">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="5506f-172">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="5506f-172">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 802
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 690b34ca-07c8-4f8a-ab13-f22a50594a43
MS-RequestId: 1187f9ad-02b4-4d96-b668-7cf3d289467b
MS-CV: 3TLmR9gz6EaCVCjR.0
MS-ServerId: 101112616
Date: Fri, 20 Jan 2017 19:13:14 GMT

{
    "totalCount": 1,
    "items": [{
            "usageLocation": "US",
            "id": "a45f1416-3300-4f65-9e8d-f123b397a4ea",
            "userPrincipalName": "e83763f7f2204ac384cfcd49f79f2749@dtdemocspcustomer005.onmicrosoft.com",
            "firstName": "Ferdinand",
            "lastName": "Filibuster",
            "displayName": "Ferdinand",
            "userDomainType": "none",
            "state": "inactive",
            "softDeletionTime": "2017-01-20T00:33:34Z",
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
    ],
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users?size=500&filter=%7B%22Field%22%3A%22UserStatus%22%2C%22Value%22%3A%22Inactive%22%2C%22Operator%22%3A%22equals%22%7D",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
