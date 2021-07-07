---
title: Verwijderde gebruikers voor een klant weergeven
description: Haalt een lijst met verwijderde CustomerUser-resources voor een klant op op klant-id. U kunt desgewenst een paginaformaat instellen. U moet een filter leveren.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f4fec958a9a6bb580d35de1cf3007e1db3b2b650
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445303"
---
# <a name="view-deleted-users-for-a-customer"></a><span data-ttu-id="4fa89-105">Verwijderde gebruikers voor een klant weergeven</span><span class="sxs-lookup"><span data-stu-id="4fa89-105">View deleted users for a customer</span></span>

<span data-ttu-id="4fa89-106">Haalt een lijst met verwijderde CustomerUser-resources voor een klant op op klant-id.</span><span class="sxs-lookup"><span data-stu-id="4fa89-106">Gets a list of deleted CustomerUser resources for a customer by customer ID.</span></span> <span data-ttu-id="4fa89-107">U kunt desgewenst een paginaformaat instellen.</span><span class="sxs-lookup"><span data-stu-id="4fa89-107">You can optionally set a page size.</span></span> <span data-ttu-id="4fa89-108">U moet een filter leveren.</span><span class="sxs-lookup"><span data-stu-id="4fa89-108">You must supply a filter.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4fa89-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4fa89-109">Prerequisites</span></span>

- <span data-ttu-id="4fa89-110">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4fa89-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4fa89-111">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="4fa89-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="4fa89-112">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4fa89-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4fa89-113">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="4fa89-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4fa89-114">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="4fa89-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4fa89-115">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="4fa89-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4fa89-116">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="4fa89-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4fa89-117">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4fa89-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="what-happens-when-you-delete-a-user-account"></a><span data-ttu-id="4fa89-118">Wat gebeurt er wanneer u een gebruikersaccount verwijdert?</span><span class="sxs-lookup"><span data-stu-id="4fa89-118">What happens when you delete a user account?</span></span>

<span data-ttu-id="4fa89-119">De gebruikerstoestand wordt ingesteld op 'inactief' wanneer u een gebruikersaccount verwijdert.</span><span class="sxs-lookup"><span data-stu-id="4fa89-119">The user state is set to "inactive" when you delete a user account.</span></span> <span data-ttu-id="4fa89-120">Dit blijft 30 dagen zo, waarna het gebruikersaccount en de bijbehorende gegevens worden verwijderd en onherkenbaar worden gemaakt.</span><span class="sxs-lookup"><span data-stu-id="4fa89-120">It remains that way for 30 days, after which the user account and its associated data are purged and made unrecoverable.</span></span> <span data-ttu-id="4fa89-121">Zie Een verwijderde gebruiker herstellen voor een klant als u een verwijderd gebruikersaccount binnen het venster van 30 dagen [wilt herstellen.](restore-a-user-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="4fa89-121">If you want to restore a deleted user account within the 30-day window, see [Restore a deleted user for a customer](restore-a-user-for-a-customer.md).</span></span> <span data-ttu-id="4fa89-122">Zodra het gebruikersaccount is verwijderd en als 'inactief' is gemarkeerd, wordt het niet meer geretourneerd als lid van de gebruikersverzameling (bijvoorbeeld met Een lijst met alle gebruikersaccounts voor een klant [ophalen).](get-a-list-of-all-user-accounts-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="4fa89-122">Once deleted and marked "inactive", the user account is no longer returned as a member of the user collection (for example, using [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span> <span data-ttu-id="4fa89-123">Als u een lijst met verwijderde gebruikers wilt opvragen die nog niet zijn verwijderd, moet u een query uitvoeren voor gebruikersaccounts die zijn ingesteld op inactief.</span><span class="sxs-lookup"><span data-stu-id="4fa89-123">To get a list of deleted users that have not yet been purged, you must query for user accounts that have been set to inactive.</span></span>

## <a name="c"></a><span data-ttu-id="4fa89-124">C\#</span><span class="sxs-lookup"><span data-stu-id="4fa89-124">C\#</span></span>

<span data-ttu-id="4fa89-125">Als u een lijst met verwijderde gebruikers wilt ophalen, maakt u een query die filtert op gebruikers van klanten waarvan de status is ingesteld op inactief.</span><span class="sxs-lookup"><span data-stu-id="4fa89-125">To retrieve a list of deleted users, construct a query that filters for customer users whose status is set to inactive.</span></span> <span data-ttu-id="4fa89-126">Maak eerst het filter door een [**SimpleFieldFilter-object**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) te instantiëren met de parameters, zoals wordt weergegeven in het volgende codefragment.</span><span class="sxs-lookup"><span data-stu-id="4fa89-126">First, create the filter by instantiating a [**SimpleFieldFilter**](/dotnet/api/microsoft.store.partnercenter.models.query.simplefieldfilter) object with the parameters as shown in the following code snippet.</span></span> <span data-ttu-id="4fa89-127">Maak vervolgens de query met behulp van [**de methode BuildIndexedQuery.**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery)</span><span class="sxs-lookup"><span data-stu-id="4fa89-127">Then create the query using the [**BuildIndexedQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildindexedquery) method.</span></span> <span data-ttu-id="4fa89-128">Als u geen paginaresultaten wilt, kunt u in plaats daarvan de [**methode BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) gebruiken.</span><span class="sxs-lookup"><span data-stu-id="4fa89-128">If you do not want paged results, you can use the [**BuildSimpleQuery**](/dotnet/api/microsoft.store.partnercenter.models.query.queryfactory.buildsimplequery) method instead.</span></span> <span data-ttu-id="4fa89-129">Gebruik vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="4fa89-129">Next, use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="4fa89-130">Roep ten slotte de [**querymethode aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.query) om de aanvraag te verzenden.</span><span class="sxs-lookup"><span data-stu-id="4fa89-130">Finally, call the [**Query**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.query) method to send the request.</span></span>

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

<span data-ttu-id="4fa89-131">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="4fa89-131">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="4fa89-132">**Project**: Partnercentrum-SDK Samples **Class**: GetCustomerInactiveUsers.cs</span><span class="sxs-lookup"><span data-stu-id="4fa89-132">**Project**: Partner Center SDK Samples **Class**: GetCustomerInactiveUsers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="4fa89-133">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4fa89-133">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4fa89-134">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="4fa89-134">Request syntax</span></span>

| <span data-ttu-id="4fa89-135">Methode</span><span class="sxs-lookup"><span data-stu-id="4fa89-135">Method</span></span>  | <span data-ttu-id="4fa89-136">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4fa89-136">Request URI</span></span>                                                                                                       |
|---------|-------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4fa89-137">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="4fa89-137">**GET**</span></span> | <span data-ttu-id="4fa89-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users?size={size}&filter={filter} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="4fa89-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/users?size={size}&filter={filter} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="4fa89-139">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="4fa89-139">URI parameter</span></span>

<span data-ttu-id="4fa89-140">Gebruik het volgende pad en de queryparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="4fa89-140">Use the following path and query parameters when creating the request.</span></span>

| <span data-ttu-id="4fa89-141">Naam</span><span class="sxs-lookup"><span data-stu-id="4fa89-141">Name</span></span>        | <span data-ttu-id="4fa89-142">Type</span><span class="sxs-lookup"><span data-stu-id="4fa89-142">Type</span></span>   | <span data-ttu-id="4fa89-143">Vereist</span><span class="sxs-lookup"><span data-stu-id="4fa89-143">Required</span></span> | <span data-ttu-id="4fa89-144">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4fa89-144">Description</span></span>                                                                                                                                                                        |
|-------------|--------|----------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="4fa89-145">customer-id</span><span class="sxs-lookup"><span data-stu-id="4fa89-145">customer-id</span></span> | <span data-ttu-id="4fa89-146">guid</span><span class="sxs-lookup"><span data-stu-id="4fa89-146">guid</span></span>   | <span data-ttu-id="4fa89-147">Ja</span><span class="sxs-lookup"><span data-stu-id="4fa89-147">Yes</span></span>      | <span data-ttu-id="4fa89-148">De waarde is een in GUID opgemaakte klant-id die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="4fa89-148">The value is a GUID formatted customer-id that identifies the customer.</span></span>                                                                                                            |
| <span data-ttu-id="4fa89-149">grootte</span><span class="sxs-lookup"><span data-stu-id="4fa89-149">size</span></span>        | <span data-ttu-id="4fa89-150">int</span><span class="sxs-lookup"><span data-stu-id="4fa89-150">int</span></span>    | <span data-ttu-id="4fa89-151">Nee</span><span class="sxs-lookup"><span data-stu-id="4fa89-151">No</span></span>       | <span data-ttu-id="4fa89-152">Het aantal resultaten dat in één keer moet worden weergegeven.</span><span class="sxs-lookup"><span data-stu-id="4fa89-152">The number of results to be displayed at one time.</span></span> <span data-ttu-id="4fa89-153">Deze parameter is optioneel.</span><span class="sxs-lookup"><span data-stu-id="4fa89-153">This parameter is optional.</span></span>                                                                                                     |
| <span data-ttu-id="4fa89-154">filter</span><span class="sxs-lookup"><span data-stu-id="4fa89-154">filter</span></span>      | <span data-ttu-id="4fa89-155">filter</span><span class="sxs-lookup"><span data-stu-id="4fa89-155">filter</span></span> | <span data-ttu-id="4fa89-156">Ja</span><span class="sxs-lookup"><span data-stu-id="4fa89-156">Yes</span></span>      | <span data-ttu-id="4fa89-157">De query die de zoekopdracht van de gebruiker filtert.</span><span class="sxs-lookup"><span data-stu-id="4fa89-157">The query that filters the user search.</span></span> <span data-ttu-id="4fa89-158">Als u verwijderde gebruikers wilt ophalen, moet u de volgende tekenreeks opnemen en coderen: {"Field":"UserState","Value":"Inactive","Operator":"equals"}.</span><span class="sxs-lookup"><span data-stu-id="4fa89-158">To retrieve deleted users, you must include and encode the following string: {"Field":"UserState","Value":"Inactive","Operator":"equals"}.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4fa89-159">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4fa89-159">Request headers</span></span>

<span data-ttu-id="4fa89-160">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="4fa89-160">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4fa89-161">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4fa89-161">Request body</span></span>

<span data-ttu-id="4fa89-162">Geen.</span><span class="sxs-lookup"><span data-stu-id="4fa89-162">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="4fa89-163">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4fa89-163">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users?size=500&filter=%7B%22Field%22%3A%22UserState%22%2C%22Value%22%3A%22Inactive%22%2C%22Operator%22%3A%22equals%22%7D HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c11feb95-55d2-45b6-9d1b-74b55d2221fb
MS-CorrelationId: 2b4ab588-f48c-4874-b479-a61895e107b2
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="4fa89-164">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4fa89-164">REST response</span></span>

<span data-ttu-id="4fa89-165">Als dit lukt, retourneert deze methode een verzameling [CustomerUser-resources](user-resources.md#customeruser) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="4fa89-165">If successful, this method returns a collection of [CustomerUser](user-resources.md#customeruser) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4fa89-166">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="4fa89-166">Response success and error codes</span></span>

<span data-ttu-id="4fa89-167">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="4fa89-167">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4fa89-168">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4fa89-168">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4fa89-169">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="4fa89-169">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4fa89-170">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="4fa89-170">Response example</span></span>

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
