---
title: Gebruikersrollen voor een klant instellen
description: Binnen een klant account is er een set Directory rollen. U kunt gebruikers accounts toewijzen aan deze rollen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: f42120e40e54ff8bd6242634d97268091abf8e1c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767458"
---
# <a name="set-user-roles-for-a-customer"></a><span data-ttu-id="29dfa-104">Gebruikersrollen voor een klant instellen</span><span class="sxs-lookup"><span data-stu-id="29dfa-104">Set user roles for a customer</span></span>

<span data-ttu-id="29dfa-105">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="29dfa-105">**Applies To**</span></span>

- <span data-ttu-id="29dfa-106">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="29dfa-106">Partner Center</span></span>

<span data-ttu-id="29dfa-107">Binnen een klant account is er een set Directory rollen.</span><span class="sxs-lookup"><span data-stu-id="29dfa-107">Within a customer account, there's a set of directory roles.</span></span> <span data-ttu-id="29dfa-108">U kunt gebruikers accounts toewijzen aan deze rollen.</span><span class="sxs-lookup"><span data-stu-id="29dfa-108">You can assign user accounts to those roles.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="29dfa-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="29dfa-109">Prerequisites</span></span>

- <span data-ttu-id="29dfa-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="29dfa-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="29dfa-111">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="29dfa-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="29dfa-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="29dfa-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="29dfa-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="29dfa-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="29dfa-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="29dfa-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="29dfa-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="29dfa-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="29dfa-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="29dfa-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="29dfa-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="29dfa-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="29dfa-118">C\#</span><span class="sxs-lookup"><span data-stu-id="29dfa-118">C\#</span></span>

<span data-ttu-id="29dfa-119">Als u een directory-rol aan een klant gebruiker wilt toewijzen, maakt u een nieuwe [**UserMember**](/dotnet/api/microsoft.store.partnercenter.models.roles.usermember) met de relevante gebruikers details.</span><span class="sxs-lookup"><span data-stu-id="29dfa-119">To assign a directory role to a customer user, create a new [**UserMember**](/dotnet/api/microsoft.store.partnercenter.models.roles.usermember) with the relevant user details.</span></span> <span data-ttu-id="29dfa-120">Vervolgens roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de opgegeven klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="29dfa-120">Then, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer ID to identify the customer.</span></span> <span data-ttu-id="29dfa-121">Gebruik vervolgens de methode [**DirectoryRoles. ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) met de Directory-rol-id om de rol op te geven.</span><span class="sxs-lookup"><span data-stu-id="29dfa-121">From there, use the [**DirectoryRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) method with the directory role ID to specify the role.</span></span> <span data-ttu-id="29dfa-122">Vervolgens opent u de **UserMembers** -verzameling en gebruikt u de methode [**Create**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.create) om het nieuwe lid van de gebruiker toe te voegen aan de verzameling gebruikers leden die aan die rol zijn toegewezen.</span><span class="sxs-lookup"><span data-stu-id="29dfa-122">Then, access the **UserMembers** collection, and use the [**Create**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.create) method to add the new user member to the collection of user members assigned to that role.</span></span>

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

<span data-ttu-id="29dfa-123">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="29dfa-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="29dfa-124">**Project**: Partner Center SDK-voor beelden **klasse**: AddUserMemberToDirectoryRole.cs</span><span class="sxs-lookup"><span data-stu-id="29dfa-124">**Project**: Partner Center SDK Samples **Class**: AddUserMemberToDirectoryRole.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="29dfa-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="29dfa-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="29dfa-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="29dfa-126">Request syntax</span></span>

| <span data-ttu-id="29dfa-127">Methode</span><span class="sxs-lookup"><span data-stu-id="29dfa-127">Method</span></span>   | <span data-ttu-id="29dfa-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="29dfa-128">Request URI</span></span>                                                                                                                 |
|----------|-----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="29dfa-129">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="29dfa-129">**POST**</span></span> | <span data-ttu-id="29dfa-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/directoryroles/{Role-id}/usermembers http/1.1</span><span class="sxs-lookup"><span data-stu-id="29dfa-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="29dfa-131">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="29dfa-131">URI parameter</span></span>

<span data-ttu-id="29dfa-132">Gebruik de volgende URI-para meters om de juiste klant en rol te identificeren.</span><span class="sxs-lookup"><span data-stu-id="29dfa-132">Use the following URI parameters to identify the correct customer and role.</span></span> <span data-ttu-id="29dfa-133">Geef de identiteits informatie op in de aanvraag tekst om de gebruiker te identificeren aan wie de rol moet worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="29dfa-133">To identify the user to whom to assign the role, supply the identifying information in the request body.</span></span>

| <span data-ttu-id="29dfa-134">Naam</span><span class="sxs-lookup"><span data-stu-id="29dfa-134">Name</span></span>                   | <span data-ttu-id="29dfa-135">Type</span><span class="sxs-lookup"><span data-stu-id="29dfa-135">Type</span></span>     | <span data-ttu-id="29dfa-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="29dfa-136">Required</span></span> | <span data-ttu-id="29dfa-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="29dfa-137">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="29dfa-138">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="29dfa-138">**customer-tenant-id**</span></span> | <span data-ttu-id="29dfa-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="29dfa-139">**guid**</span></span> | <span data-ttu-id="29dfa-140">J</span><span class="sxs-lookup"><span data-stu-id="29dfa-140">Y</span></span>        | <span data-ttu-id="29dfa-141">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="29dfa-141">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="29dfa-142">**rol-id**</span><span class="sxs-lookup"><span data-stu-id="29dfa-142">**role-id**</span></span>            | <span data-ttu-id="29dfa-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="29dfa-143">**guid**</span></span> | <span data-ttu-id="29dfa-144">J</span><span class="sxs-lookup"><span data-stu-id="29dfa-144">Y</span></span>        | <span data-ttu-id="29dfa-145">De waarde is een GUID-indeling met een **rol-id** waarmee de rol wordt geïdentificeerd die aan de gebruiker moet worden toegewezen.</span><span class="sxs-lookup"><span data-stu-id="29dfa-145">The value is a GUID formatted **role-id** that identifies the role to assign to the user.</span></span>                                                              |

### <a name="request-headers"></a><span data-ttu-id="29dfa-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="29dfa-146">Request headers</span></span>

<span data-ttu-id="29dfa-147">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="29dfa-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="29dfa-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="29dfa-148">Request body</span></span>

<span data-ttu-id="29dfa-149">In deze tabel worden de vereiste eigenschappen in de hoofd tekst van de aanvraag beschreven.</span><span class="sxs-lookup"><span data-stu-id="29dfa-149">This table describes the required properties in the request body.</span></span>

| <span data-ttu-id="29dfa-150">Naam</span><span class="sxs-lookup"><span data-stu-id="29dfa-150">Name</span></span>                  | <span data-ttu-id="29dfa-151">Type</span><span class="sxs-lookup"><span data-stu-id="29dfa-151">Type</span></span>       | <span data-ttu-id="29dfa-152">Vereist</span><span class="sxs-lookup"><span data-stu-id="29dfa-152">Required</span></span> | <span data-ttu-id="29dfa-153">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="29dfa-153">Description</span></span>                            |
|-----------------------|------------|----------|----------------------------------------|
| <span data-ttu-id="29dfa-154">**Id**</span><span class="sxs-lookup"><span data-stu-id="29dfa-154">**Id**</span></span>                | <span data-ttu-id="29dfa-155">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="29dfa-155">**string**</span></span> | <span data-ttu-id="29dfa-156">J</span><span class="sxs-lookup"><span data-stu-id="29dfa-156">Y</span></span>        | <span data-ttu-id="29dfa-157">De id van de gebruiker die aan de rol moet worden toegevoegd.</span><span class="sxs-lookup"><span data-stu-id="29dfa-157">The Id of the user to add to the role.</span></span> |
| <span data-ttu-id="29dfa-158">**DisplayName**</span><span class="sxs-lookup"><span data-stu-id="29dfa-158">**DisplayName**</span></span>       | <span data-ttu-id="29dfa-159">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="29dfa-159">**string**</span></span> | <span data-ttu-id="29dfa-160">J</span><span class="sxs-lookup"><span data-stu-id="29dfa-160">Y</span></span>        | <span data-ttu-id="29dfa-161">De beschrijvende weergave naam van de gebruiker.</span><span class="sxs-lookup"><span data-stu-id="29dfa-161">The friendly display name of the user.</span></span> |
| <span data-ttu-id="29dfa-162">**UserPrincipalName**</span><span class="sxs-lookup"><span data-stu-id="29dfa-162">**UserPrincipalName**</span></span> | <span data-ttu-id="29dfa-163">**tekenreeksexpressie**</span><span class="sxs-lookup"><span data-stu-id="29dfa-163">**string**</span></span> | <span data-ttu-id="29dfa-164">J</span><span class="sxs-lookup"><span data-stu-id="29dfa-164">Y</span></span>        | <span data-ttu-id="29dfa-165">De naam van de gebruikers-principal.</span><span class="sxs-lookup"><span data-stu-id="29dfa-165">The name of the user principal.</span></span>        |
| <span data-ttu-id="29dfa-166">**Kenmerken**</span><span class="sxs-lookup"><span data-stu-id="29dfa-166">**Attributes**</span></span>        | <span data-ttu-id="29dfa-167">**object**</span><span class="sxs-lookup"><span data-stu-id="29dfa-167">**object**</span></span> | <span data-ttu-id="29dfa-168">J</span><span class="sxs-lookup"><span data-stu-id="29dfa-168">Y</span></span>        | <span data-ttu-id="29dfa-169">Bevat "object type": "UserMember"</span><span class="sxs-lookup"><span data-stu-id="29dfa-169">Contains "ObjectType":"UserMember"</span></span>     |

### <a name="request-example"></a><span data-ttu-id="29dfa-170">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="29dfa-170">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="29dfa-171">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="29dfa-171">REST response</span></span>

<span data-ttu-id="29dfa-172">Deze methode retourneert het gebruikers account met de rol-id die is gekoppeld wanneer de gebruiker is toegewezen aan de rol.</span><span class="sxs-lookup"><span data-stu-id="29dfa-172">This method returns the user account with the role id attached when the user is successfully assigned the role.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="29dfa-173">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="29dfa-173">Response success and error codes</span></span>

<span data-ttu-id="29dfa-174">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="29dfa-174">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="29dfa-175">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="29dfa-175">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="29dfa-176">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="29dfa-176">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="29dfa-177">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="29dfa-177">Response example</span></span>

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
