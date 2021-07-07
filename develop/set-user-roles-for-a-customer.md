---
title: Gebruikersrollen voor een klant instellen
description: Binnen een klantaccount is er een set adreslijstrollen. U kunt gebruikersaccounts toewijzen aan deze rollen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a035d711ffa91200fa7b479ed5ec53929aa4feaf
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111446697"
---
# <a name="set-user-roles-for-a-customer"></a><span data-ttu-id="78b14-104">Gebruikersrollen voor een klant instellen</span><span class="sxs-lookup"><span data-stu-id="78b14-104">Set user roles for a customer</span></span>

<span data-ttu-id="78b14-105">Binnen een klantaccount is er een set adreslijstrollen.</span><span class="sxs-lookup"><span data-stu-id="78b14-105">Within a customer account, there's a set of directory roles.</span></span> <span data-ttu-id="78b14-106">U kunt gebruikersaccounts toewijzen aan deze rollen.</span><span class="sxs-lookup"><span data-stu-id="78b14-106">You can assign user accounts to those roles.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="78b14-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="78b14-107">Prerequisites</span></span>

- <span data-ttu-id="78b14-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="78b14-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="78b14-109">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="78b14-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="78b14-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="78b14-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="78b14-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="78b14-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="78b14-112">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="78b14-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="78b14-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="78b14-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="78b14-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="78b14-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="78b14-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="78b14-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="78b14-116">C\#</span><span class="sxs-lookup"><span data-stu-id="78b14-116">C\#</span></span>

<span data-ttu-id="78b14-117">Als u een directoryrol wilt toewijzen aan een klantgebruiker, maakt u een nieuw [**UserMember**](/dotnet/api/microsoft.store.partnercenter.models.roles.usermember) met de relevante gebruikersgegevens.</span><span class="sxs-lookup"><span data-stu-id="78b14-117">To assign a directory role to a customer user, create a new [**UserMember**](/dotnet/api/microsoft.store.partnercenter.models.roles.usermember) with the relevant user details.</span></span> <span data-ttu-id="78b14-118">Roep vervolgens de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de opgegeven klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="78b14-118">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer ID to identify the customer.</span></span> <span data-ttu-id="78b14-119">Van hieruit gebruikt u de [**methode DirectoryRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) met de id van de directoryrol om de rol op te geven.</span><span class="sxs-lookup"><span data-stu-id="78b14-119">From there, use the [**DirectoryRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) method with the directory role ID to specify the role.</span></span> <span data-ttu-id="78b14-120">Ga vervolgens naar de **verzameling UserMembers** en gebruik de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.create) om het nieuwe gebruikerslid toe te voegen aan de verzameling gebruikersleden die aan die rol zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="78b14-120">Then, access the **UserMembers** collection, and use the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.create) method to add the new user member to the collection of user members assigned to that role.</span></span>

``` csharp
// UserMember createdUser;
// IAggregatePartner partnerOperations;
// Customer selectedCustomer;
// IDirectoryRole selectedRole;

// Create the new user member.
UserMember userMemberToAdd = new UserMember()
{
    UserPrincipalName = createdUser.UserPrincipalName,
    DisplayName = createdUser.DisplayName,
    Id = createdUser.Id
};

// Add the new user member to the role.
var userMemberAdded = partnerOperations.Customers.ById(selectedCustomer.Id).DirectoryRoles.ById(selectedRole.Id).UserMembers.Create(userMemberToAdd);
```

<span data-ttu-id="78b14-121">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="78b14-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="78b14-122">**Project:** Partnercentrum-SDK Klasse **Samples:** AddUserMemberToDirectoryRole.cs</span><span class="sxs-lookup"><span data-stu-id="78b14-122">**Project**: Partner Center SDK Samples **Class**: AddUserMemberToDirectoryRole.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="78b14-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="78b14-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="78b14-124">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="78b14-124">Request syntax</span></span>

| <span data-ttu-id="78b14-125">Methode</span><span class="sxs-lookup"><span data-stu-id="78b14-125">Method</span></span>   | <span data-ttu-id="78b14-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="78b14-126">Request URI</span></span>                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="78b14-127">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="78b14-127">**POST**</span></span> | <span data-ttu-id="78b14-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="78b14-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="78b14-129">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="78b14-129">URI parameter</span></span>

<span data-ttu-id="78b14-130">Gebruik de volgende URI-parameters om de juiste klant en rol te identificeren.</span><span class="sxs-lookup"><span data-stu-id="78b14-130">Use the following URI parameters to identify the correct customer and role.</span></span> <span data-ttu-id="78b14-131">Als u de gebruiker wilt identificeren aan wie de rol moet worden toegewezen, geeft u de identificatiegegevens op in de aanvraag body.</span><span class="sxs-lookup"><span data-stu-id="78b14-131">To identify the user to whom to assign the role, supply the identifying information in the request body.</span></span>

| <span data-ttu-id="78b14-132">Naam</span><span class="sxs-lookup"><span data-stu-id="78b14-132">Name</span></span>                   | <span data-ttu-id="78b14-133">Type</span><span class="sxs-lookup"><span data-stu-id="78b14-133">Type</span></span>     | <span data-ttu-id="78b14-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="78b14-134">Required</span></span> | <span data-ttu-id="78b14-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="78b14-135">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="78b14-136">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="78b14-136">**customer-tenant-id**</span></span> | <span data-ttu-id="78b14-137">**guid**</span><span class="sxs-lookup"><span data-stu-id="78b14-137">**guid**</span></span> | <span data-ttu-id="78b14-138">J</span><span class="sxs-lookup"><span data-stu-id="78b14-138">Y</span></span>        | <span data-ttu-id="78b14-139">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="78b14-139">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="78b14-140">**role-id**</span><span class="sxs-lookup"><span data-stu-id="78b14-140">**role-id**</span></span>            | <span data-ttu-id="78b14-141">**guid**</span><span class="sxs-lookup"><span data-stu-id="78b14-141">**guid**</span></span> | <span data-ttu-id="78b14-142">J</span><span class="sxs-lookup"><span data-stu-id="78b14-142">Y</span></span>        | <span data-ttu-id="78b14-143">De waarde is een **rol-id** met GUID-indeling die de rol identificeert die aan de gebruiker moet worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="78b14-143">The value is a GUID formatted **role-id** that identifies the role to assign to the user.</span></span>                                                              |

### <a name="request-headers"></a><span data-ttu-id="78b14-144">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="78b14-144">Request headers</span></span>

<span data-ttu-id="78b14-145">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="78b14-145">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="78b14-146">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="78b14-146">Request body</span></span>

<span data-ttu-id="78b14-147">In deze tabel worden de vereiste eigenschappen in de aanvraag body beschreven.</span><span class="sxs-lookup"><span data-stu-id="78b14-147">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="78b14-148">Naam</span><span class="sxs-lookup"><span data-stu-id="78b14-148">Name</span></span>                  | <span data-ttu-id="78b14-149">Type</span><span class="sxs-lookup"><span data-stu-id="78b14-149">Type</span></span>       | <span data-ttu-id="78b14-150">Vereist</span><span class="sxs-lookup"><span data-stu-id="78b14-150">Required</span></span> | <span data-ttu-id="78b14-151">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="78b14-151">Description</span></span>                            |
|-----------------------|------------|----------|----------------------------------------|
| <span data-ttu-id="78b14-152">**Id**</span><span class="sxs-lookup"><span data-stu-id="78b14-152">**Id**</span></span>                | <span data-ttu-id="78b14-153">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="78b14-153">**string**</span></span> | <span data-ttu-id="78b14-154">J</span><span class="sxs-lookup"><span data-stu-id="78b14-154">Y</span></span>        | <span data-ttu-id="78b14-155">De id van de gebruiker die aan de rol moet worden toevoegen.</span><span class="sxs-lookup"><span data-stu-id="78b14-155">The ID of the user to add to the role.</span></span> |
| <span data-ttu-id="78b14-156">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="78b14-156">**DisplayName**</span></span>       | <span data-ttu-id="78b14-157">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="78b14-157">**string**</span></span> | <span data-ttu-id="78b14-158">J</span><span class="sxs-lookup"><span data-stu-id="78b14-158">Y</span></span>        | <span data-ttu-id="78b14-159">De gebruiksvriendelijke weergavenaam van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="78b14-159">The friendly display name of the user.</span></span> |
| <span data-ttu-id="78b14-160">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="78b14-160">**UserPrincipalName**</span></span> | <span data-ttu-id="78b14-161">**tekenreeks**</span><span class="sxs-lookup"><span data-stu-id="78b14-161">**string**</span></span> | <span data-ttu-id="78b14-162">J</span><span class="sxs-lookup"><span data-stu-id="78b14-162">Y</span></span>        | <span data-ttu-id="78b14-163">De naam van de user principal.</span><span class="sxs-lookup"><span data-stu-id="78b14-163">The name of the user principal.</span></span>        |
| <span data-ttu-id="78b14-164">**Kenmerken**</span><span class="sxs-lookup"><span data-stu-id="78b14-164">**Attributes**</span></span>        | <span data-ttu-id="78b14-165">**Object**</span><span class="sxs-lookup"><span data-stu-id="78b14-165">**object**</span></span> | <span data-ttu-id="78b14-166">J</span><span class="sxs-lookup"><span data-stu-id="78b14-166">Y</span></span>        | <span data-ttu-id="78b14-167">Bevat "ObjectType":"UserMember"</span><span class="sxs-lookup"><span data-stu-id="78b14-167">Contains "ObjectType":"UserMember"</span></span>     |

### <a name="request-example"></a><span data-ttu-id="78b14-168">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="78b14-168">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/directoryroles/f023fd81-a637-4b56-95fd-791ac0226033/usermembers HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: a56cb2e5-a156-4f68-9155-57ffe2b93d18
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
X-Locale: en-US
Content-Type: application/json
Host: api.partnercenter.microsoft.com
Content-Length: 180
Expect: 100-continue

{
    "Id": "a9ef48bb-8758-4590-a312-d4a47bfaded4",
    "DisplayName": "Daniel Tsai",
    "UserPrincipalName": "Daniel@dtdemocspcustomer005.onmicrosoft.com",
    "Attributes": {
        "ObjectType": "UserMember"
    }
}
```

## <a name="rest-response"></a><span data-ttu-id="78b14-169">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="78b14-169">REST response</span></span>

<span data-ttu-id="78b14-170">Deze methode retourneert het gebruikersaccount met de rol-id die is gekoppeld wanneer de gebruiker de rol heeft toegewezen.</span><span class="sxs-lookup"><span data-stu-id="78b14-170">This method returns the user account with the role ID attached when the user is successfully assigned the role.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="78b14-171">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="78b14-171">Response success and error codes</span></span>

<span data-ttu-id="78b14-172">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="78b14-172">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="78b14-173">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="78b14-173">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="78b14-174">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="78b14-174">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="78b14-175">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="78b14-175">Response example</span></span>

```http
HTTP/1.1 201 Created
Content-Length: 231
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
MS-RequestId: a56cb2e5-a156-4f68-9155-57ffe2b93d18
MS-CV: aia94+gnrEeQqkGr.0
MS-ServerId: 101112202
Date: Tue, 20 Dec 2016 23:36:55 GMT

{
    "displayName": "Daniel Tsai",
    "userPrincipalName": "Daniel@dtdemocspcustomer005.onmicrosoft.com",
    "roleId": "f023fd81-a637-4b56-95fd-791ac0226033",
    "id": "a9ef48bb-8758-4590-a312-d4a47bfaded4",
    "attributes": {
        "objectType": "UserMember"
    }
}
```
