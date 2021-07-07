---
title: Gebruikersrollen voor een klant ophalen
description: Haal een lijst op met alle rollen/machtigingen die zijn gekoppeld aan een gebruikersaccount. Variaties zijn onder andere het verkrijgen van een lijst met alle machtigingen voor alle gebruikersaccounts voor een klant en het verkrijgen van een lijst met gebruikers met een bepaalde rol.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 8f58e8b7eae5bb47265bb1ac83fcdcd160f735d2
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445915"
---
# <a name="get-user-roles-for-a-customer"></a><span data-ttu-id="27734-104">Gebruikersrollen voor een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="27734-104">Get user roles for a customer</span></span>

<span data-ttu-id="27734-105">Haal een lijst op met alle rollen/machtigingen die zijn gekoppeld aan een gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="27734-105">Get a list of all the roles/permissions attached to a user account.</span></span> <span data-ttu-id="27734-106">Variaties zijn onder andere het verkrijgen van een lijst met alle machtigingen voor alle gebruikersaccounts voor een klant en het verkrijgen van een lijst met gebruikers met een bepaalde rol.</span><span class="sxs-lookup"><span data-stu-id="27734-106">Variations include getting a list of all permissions across all user accounts for a customer, and getting a list of users that have a given role.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="27734-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="27734-107">Prerequisites</span></span>

- <span data-ttu-id="27734-108">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="27734-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="27734-109">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="27734-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="27734-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="27734-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="27734-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="27734-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="27734-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="27734-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="27734-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="27734-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="27734-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="27734-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="27734-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="27734-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="27734-116">C\#</span><span class="sxs-lookup"><span data-stu-id="27734-116">C\#</span></span>

<span data-ttu-id="27734-117">Als u alle directoryrollen voor een opgegeven klant wilt ophalen, haalt u eerst de opgegeven klant-id op.</span><span class="sxs-lookup"><span data-stu-id="27734-117">To retrieve all the directory roles for a specified customer, first retrieve the specified customer ID.</span></span> <span data-ttu-id="27734-118">Gebruik vervolgens de verzameling **IAggregatePartner.Customers** en roep de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="27734-118">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="27734-119">Roep vervolgens de **eigenschap DirectoryRoles** aan, gevolgd door de **methode Get()** of **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="27734-119">Then call the **DirectoryRoles** property, followed by the **Get()** or **GetAsync()** method.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;

var directoryRoles = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.Get();
```

<span data-ttu-id="27734-120">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="27734-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="27734-121">**Project**: Partnercentrum-SDK Samples **Class:** GetCustomerDirectoryRoles.cs</span><span class="sxs-lookup"><span data-stu-id="27734-121">**Project**: Partner Center SDK Samples **Class**: GetCustomerDirectoryRoles.cs</span></span>

<span data-ttu-id="27734-122">Als u een lijst met klantgebruikers met een bepaalde rol wilt ophalen, haalt u eerst de opgegeven klant-id en de maprol-id op.</span><span class="sxs-lookup"><span data-stu-id="27734-122">To retrieve a list of customer users that have a given role, first retrieve the specified customer ID and the directory role ID.</span></span> <span data-ttu-id="27734-123">Gebruik vervolgens de verzameling **IAggregatePartner.Customers** en roep de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="27734-123">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="27734-124">Roep vervolgens de **eigenschap DirectoryRoles** aan, vervolgens de methode **ById()** en vervolgens de eigenschap **UserMembers,** gevolgd door de methode **Get()** of **GetAsync().**</span><span class="sxs-lookup"><span data-stu-id="27734-124">Then call the **DirectoryRoles** property, then **ById()** method, then the **UserMembers** property, the followed by the **Get()** or **GetAsync()** method.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;
// string selectedDirectoryRoleId;

var userMembers = partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedDirectoryRoleId).UserMembers.Get();
```

<span data-ttu-id="27734-125">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="27734-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="27734-126">**Project:** Klasse PartnerSDK.FeatureSamples: GetCustomerDirectoryRoleUserMembers.cs </span><span class="sxs-lookup"><span data-stu-id="27734-126">**Project**: PartnerSDK.FeatureSamples **Class**: GetCustomerDirectoryRoleUserMembers.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="27734-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="27734-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="27734-128">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="27734-128">Request syntax</span></span>

| <span data-ttu-id="27734-129">Methode</span><span class="sxs-lookup"><span data-stu-id="27734-129">Method</span></span>  | <span data-ttu-id="27734-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="27734-130">Request URI</span></span>                                                                                                           |
|---------|-----------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="27734-131">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="27734-131">**GET**</span></span> | <span data-ttu-id="27734-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id}/directoryroles HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="27734-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id}/directoryroles HTTP/1.1</span></span> |
| <span data-ttu-id="27734-133">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="27734-133">**GET**</span></span> | <span data-ttu-id="27734-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="27734-134">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles HTTP/1.1</span></span>                 |
| <span data-ttu-id="27734-135">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="27734-135">**GET**</span></span> | <span data-ttu-id="27734-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers</span><span class="sxs-lookup"><span data-stu-id="27734-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers</span></span>    |

### <a name="uri-parameter"></a><span data-ttu-id="27734-137">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="27734-137">URI parameter</span></span>

<span data-ttu-id="27734-138">Gebruik de volgende queryparameter om de juiste klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="27734-138">Use the following query parameter to identify the correct customer.</span></span>

| <span data-ttu-id="27734-139">Naam</span><span class="sxs-lookup"><span data-stu-id="27734-139">Name</span></span>                   | <span data-ttu-id="27734-140">Type</span><span class="sxs-lookup"><span data-stu-id="27734-140">Type</span></span>     | <span data-ttu-id="27734-141">Vereist</span><span class="sxs-lookup"><span data-stu-id="27734-141">Required</span></span> | <span data-ttu-id="27734-142">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="27734-142">Description</span></span>                                                                                                                                                                                                 |
|------------------------|----------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="27734-143">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="27734-143">**customer-tenant-id**</span></span> | <span data-ttu-id="27734-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="27734-144">**guid**</span></span> | <span data-ttu-id="27734-145">J</span><span class="sxs-lookup"><span data-stu-id="27734-145">Y</span></span>        | <span data-ttu-id="27734-146">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="27734-146">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span>                                                      |
| <span data-ttu-id="27734-147">**user-id**</span><span class="sxs-lookup"><span data-stu-id="27734-147">**user-id**</span></span>            | <span data-ttu-id="27734-148">**guid**</span><span class="sxs-lookup"><span data-stu-id="27734-148">**guid**</span></span> | <span data-ttu-id="27734-149">N</span><span class="sxs-lookup"><span data-stu-id="27734-149">N</span></span>        | <span data-ttu-id="27734-150">De waarde is een guid-opgemaakte **gebruikers-id** die bij één gebruikersaccount hoort.</span><span class="sxs-lookup"><span data-stu-id="27734-150">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                                                                            |
| <span data-ttu-id="27734-151">**role-id**</span><span class="sxs-lookup"><span data-stu-id="27734-151">**role-id**</span></span>            | <span data-ttu-id="27734-152">**guid**</span><span class="sxs-lookup"><span data-stu-id="27734-152">**guid**</span></span> | <span data-ttu-id="27734-153">N</span><span class="sxs-lookup"><span data-stu-id="27734-153">N</span></span>        | <span data-ttu-id="27734-154">De waarde is een **rol-id** met GUID-indeling die bij een type rol hoort.</span><span class="sxs-lookup"><span data-stu-id="27734-154">The value is a GUID formatted **role-id** that belongs to a type of role.</span></span> <span data-ttu-id="27734-155">U kunt deze ID's krijgen door een query uit te voeren op alle directoryrollen voor een klant, voor alle gebruikersaccounts.</span><span class="sxs-lookup"><span data-stu-id="27734-155">You can get these IDs by querying all the directory roles for a customer, across all user accounts.</span></span> <span data-ttu-id="27734-156">(Het tweede scenario hierboven).</span><span class="sxs-lookup"><span data-stu-id="27734-156">(The second scenario, above).</span></span> |

### <a name="request-headers"></a><span data-ttu-id="27734-157">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="27734-157">Request headers</span></span>

<span data-ttu-id="27734-158">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="27734-158">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="27734-159">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="27734-159">Request body</span></span>

### <a name="request-example"></a><span data-ttu-id="27734-160">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="27734-160">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id>/directoryroles HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
```

## <a name="rest-response"></a><span data-ttu-id="27734-161">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="27734-161">REST response</span></span>

<span data-ttu-id="27734-162">Als dit lukt, retourneert deze methode een lijst met de rollen die zijn gekoppeld aan het opgegeven gebruikersaccount.</span><span class="sxs-lookup"><span data-stu-id="27734-162">If successful, this method returns a list of the roles associated with the given user account.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="27734-163">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="27734-163">Response success and error codes</span></span>

<span data-ttu-id="27734-164">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="27734-164">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="27734-165">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="27734-165">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="27734-166">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="27734-166">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="27734-167">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="27734-167">Response example</span></span>

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
