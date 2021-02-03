---
title: Gebruikersrollen voor een klant ophalen
description: Een lijst ophalen met alle rollen/machtigingen die zijn gekoppeld aan een gebruikers account. Variaties zijn onder andere het ophalen van een lijst met alle machtigingen voor alle gebruikers accounts voor een klant en het ophalen van een lijst met gebruikers die een bepaalde rol hebben.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8dad5c035c08905c3d39052de07ebb912452a16b
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767230"
---
# <a name="get-user-roles-for-a-customer"></a><span data-ttu-id="49559-104">Gebruikersrollen voor een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="49559-104">Get user roles for a customer</span></span>

<span data-ttu-id="49559-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="49559-105">**Applies To**</span></span>

- <span data-ttu-id="49559-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="49559-106">Partner Center</span></span>

<span data-ttu-id="49559-107">Een lijst ophalen met alle rollen/machtigingen die zijn gekoppeld aan een gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="49559-107">Get a list of all the roles/permissions attached to a user account.</span></span> <span data-ttu-id="49559-108">Variaties zijn onder andere het ophalen van een lijst met alle machtigingen voor alle gebruikers accounts voor een klant en het ophalen van een lijst met gebruikers die een bepaalde rol hebben.</span><span class="sxs-lookup"><span data-stu-id="49559-108">Variations include getting a list of all permissions across all user accounts for a customer, and getting a list of users that have a given role.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="49559-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="49559-109">Prerequisites</span></span>

- <span data-ttu-id="49559-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="49559-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="49559-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="49559-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="49559-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="49559-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="49559-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="49559-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="49559-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="49559-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="49559-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="49559-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="49559-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="49559-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="49559-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="49559-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="49559-118">C\#</span><span class="sxs-lookup"><span data-stu-id="49559-118">C\#</span></span>

<span data-ttu-id="49559-119">Als u alle Directory rollen voor een opgegeven klant wilt ophalen, moet u eerst de opgegeven klant-ID ophalen.</span><span class="sxs-lookup"><span data-stu-id="49559-119">To retrieve all the directory roles for a specified customer, first retrieve the specified customer ID.</span></span> <span data-ttu-id="49559-120">Vervolgens gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="49559-120">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="49559-121">Roep vervolgens de eigenschap **DirectoryRoles** aan, gevolgd door de methode **Get ()** of **GetAsync ()**.</span><span class="sxs-lookup"><span data-stu-id="49559-121">Then call the **DirectoryRoles** property, followed by the **Get()** or **GetAsync()** method.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var directoryRoles = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.Get();
```

<span data-ttu-id="49559-122">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="49559-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="49559-123">**Project**: Partner Center SDK-voor beelden **klasse**: GetCustomerDirectoryRoles.cs</span><span class="sxs-lookup"><span data-stu-id="49559-123">**Project**: Partner Center SDK Samples **Class**: GetCustomerDirectoryRoles.cs</span></span>

<span data-ttu-id="49559-124">Als u een lijst met klant gebruikers met een bepaalde rol wilt ophalen, moet u eerst de opgegeven klant-ID en de ID van de Directory-rol ophalen.</span><span class="sxs-lookup"><span data-stu-id="49559-124">To retrieve a list of customer users that have a given role, first retrieve the specified customer ID and the directory role ID.</span></span> <span data-ttu-id="49559-125">Vervolgens gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="49559-125">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="49559-126">Roep vervolgens de eigenschap **DirectoryRoles** en vervolgens de methode **ById ()** aan, vervolgens de eigenschap **UserMembers** , gevolgd door de methode **Get ()** of **GetAsync ()** .</span><span class="sxs-lookup"><span data-stu-id="49559-126">Then call the **DirectoryRoles** property, then **ById()** method, then the **UserMembers** property, the followed by the **Get()** or **GetAsync()** method.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;
// string selectedDirectoryRoleId;

var userMembers = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedDirectoryRoleId).UserMembers.Get();
```

<span data-ttu-id="49559-127">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="49559-127">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="49559-128">**Project**: PartnerSDK. FeatureSamples- **klasse**: GetCustomerDirectoryRoleUserMembers.cs</span><span class="sxs-lookup"><span data-stu-id="49559-128">**Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerDirectoryRoleUserMembers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="49559-129">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="49559-129">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="49559-130">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="49559-130">Request syntax</span></span>

| <span data-ttu-id="49559-131">Methode</span><span class="sxs-lookup"><span data-stu-id="49559-131">Method</span></span>  | <span data-ttu-id="49559-132">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="49559-132">Request URI</span></span>                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="49559-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="49559-133">**GET**</span></span> | <span data-ttu-id="49559-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users/{user-id}/directoryroles http/1.1</span><span class="sxs-lookup"><span data-stu-id="49559-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id}/directoryroles HTTP/1.1</span></span> |
| <span data-ttu-id="49559-135">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="49559-135">**GET**</span></span> | <span data-ttu-id="49559-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/directoryroles http/1.1</span><span class="sxs-lookup"><span data-stu-id="49559-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles HTTP/1.1</span></span>                 |
| <span data-ttu-id="49559-137">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="49559-137">**GET**</span></span> | <span data-ttu-id="49559-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/directoryroles/{Role-id}/usermembers</span><span class="sxs-lookup"><span data-stu-id="49559-138">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers</span></span>    |

### <a name="uri-parameter"></a><span data-ttu-id="49559-139">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="49559-139">URI parameter</span></span>

<span data-ttu-id="49559-140">Gebruik de volgende query parameter om de juiste klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="49559-140">Use the following query parameter to identify the correct customer.</span></span>

| <span data-ttu-id="49559-141">Naam</span><span class="sxs-lookup"><span data-stu-id="49559-141">Name</span></span>                   | <span data-ttu-id="49559-142">Type</span><span class="sxs-lookup"><span data-stu-id="49559-142">Type</span></span>     | <span data-ttu-id="49559-143">Vereist</span><span class="sxs-lookup"><span data-stu-id="49559-143">Required</span></span> | <span data-ttu-id="49559-144">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="49559-144">Description</span></span>                                                                                                                                                                                                 |
|------------------------|----------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="49559-145">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="49559-145">**customer-tenant-id**</span></span> | <span data-ttu-id="49559-146">**guid**</span><span class="sxs-lookup"><span data-stu-id="49559-146">**guid**</span></span> | <span data-ttu-id="49559-147">J</span><span class="sxs-lookup"><span data-stu-id="49559-147">Y</span></span>        | <span data-ttu-id="49559-148">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="49559-148">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span>                                                      |
| <span data-ttu-id="49559-149">**gebruikers-id**</span><span class="sxs-lookup"><span data-stu-id="49559-149">**user-id**</span></span>            | <span data-ttu-id="49559-150">**guid**</span><span class="sxs-lookup"><span data-stu-id="49559-150">**guid**</span></span> | <span data-ttu-id="49559-151">N</span><span class="sxs-lookup"><span data-stu-id="49559-151">N</span></span>        | <span data-ttu-id="49559-152">De waarde is een **gebruikers-id** met een GUID-indeling die tot één gebruikers account behoort.</span><span class="sxs-lookup"><span data-stu-id="49559-152">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                                                                            |
| <span data-ttu-id="49559-153">**rol-id**</span><span class="sxs-lookup"><span data-stu-id="49559-153">**role-id**</span></span>            | <span data-ttu-id="49559-154">**guid**</span><span class="sxs-lookup"><span data-stu-id="49559-154">**guid**</span></span> | <span data-ttu-id="49559-155">N</span><span class="sxs-lookup"><span data-stu-id="49559-155">N</span></span>        | <span data-ttu-id="49559-156">De waarde is een GUID-indeling met een **rol-id** die tot een type rol behoort.</span><span class="sxs-lookup"><span data-stu-id="49559-156">The value is a GUID formatted **role-id** that belongs to a type of role.</span></span> <span data-ttu-id="49559-157">U kunt deze Id's ophalen door de Directory rollen voor een klant te doorzoeken op alle gebruikers accounts.</span><span class="sxs-lookup"><span data-stu-id="49559-157">You can get these IDs by querying all the directory roles for a customer, across all user accounts.</span></span> <span data-ttu-id="49559-158">(Het tweede scenario hierboven).</span><span class="sxs-lookup"><span data-stu-id="49559-158">(The second scenario, above).</span></span> |

### <a name="request-headers"></a><span data-ttu-id="49559-159">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="49559-159">Request headers</span></span>

<span data-ttu-id="49559-160">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="49559-160">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="49559-161">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="49559-161">Request body</span></span>

### <a name="request-example"></a><span data-ttu-id="49559-162">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="49559-162">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id>/directoryroles HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
```

## <a name="rest-response"></a><span data-ttu-id="49559-163">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="49559-163">REST response</span></span>

<span data-ttu-id="49559-164">Als deze methode is geslaagd, wordt een lijst geretourneerd met de rollen die zijn gekoppeld aan het opgegeven gebruikers account.</span><span class="sxs-lookup"><span data-stu-id="49559-164">If successful, this method returns a list of the roles associated with the given user account.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="49559-165">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="49559-165">Response success and error codes</span></span>

<span data-ttu-id="49559-166">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="49559-166">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="49559-167">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="49559-167">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="49559-168">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="49559-168">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="49559-169">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="49559-169">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST

{
      "totalCount": 2,
      "items": [
        {
          "name": "Helpdesk Administrator",
          "id": "729827e3-9c14-49f7-bb1b-9608f156bbb8",
          "attributes": { "objectType": "DirectoryRole" }
        },
        {
          "name": "User Account Administrator",
          "id": "fe930be7-5e62-47db-91af-98c3a49a38b1",
          "attributes": { "objectType": "DirectoryRole" }
        }
      ],
      "attributes": { "objectType": "Collection" }
}
```
