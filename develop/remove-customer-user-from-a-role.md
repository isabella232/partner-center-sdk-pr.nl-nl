---
title: Een klantgebruiker uit een rol verwijderen
description: Een gebruiker verwijderen uit een directory-rol binnen een klant account.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6253e86f3733bbf2b9c593c5ca3f3e2fccce7c2c
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767477"
---
# <a name="remove-a-customer-user-from-a-role"></a><span data-ttu-id="798a0-103">Een klantgebruiker uit een rol verwijderen</span><span class="sxs-lookup"><span data-stu-id="798a0-103">Remove a customer user from a role</span></span>

<span data-ttu-id="798a0-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="798a0-104">**Applies To**</span></span>

- <span data-ttu-id="798a0-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="798a0-105">Partner Center</span></span>

<span data-ttu-id="798a0-106">Een gebruiker verwijderen uit een directory-rol binnen een klant account.</span><span class="sxs-lookup"><span data-stu-id="798a0-106">How to remove a user from a directory role within a customer account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="798a0-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="798a0-107">Prerequisites</span></span>

- <span data-ttu-id="798a0-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="798a0-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="798a0-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="798a0-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="798a0-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="798a0-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="798a0-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="798a0-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="798a0-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="798a0-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="798a0-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="798a0-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="798a0-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="798a0-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="798a0-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="798a0-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="798a0-116">C\#</span><span class="sxs-lookup"><span data-stu-id="798a0-116">C\#</span></span>

<span data-ttu-id="798a0-117">Als u een gebruiker uit een directory-rol wilt verwijderen, selecteert u de klant met de gebruiker die u wilt wijzigen met een aanroep van de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) , geeft u de functie op met behulp van de methode [**DirectoryRoles. ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) met de rol-id van de Directory.</span><span class="sxs-lookup"><span data-stu-id="798a0-117">To remove a user from a directory role, select the customer with the user to modify with a call to the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method, From there, specify the role using the [**DirectoryRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) method with the directory role ID.</span></span> <span data-ttu-id="798a0-118">Vervolgens opent u de methode [**UserMembers. ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.byid) om de gebruiker te identificeren die moet worden verwijderd en de [**Verwijder**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermember.delete) methode om de gebruiker te verwijderen uit de rol.</span><span class="sxs-lookup"><span data-stu-id="798a0-118">Then, access the [**UserMembers.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.byid) method to identify the user to remove, and the [**Delete**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermember.delete) method to remove the user from the role.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedRoleId;
// string selectedUserMemberId;

partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedRoleId).UserMembers.ById(selectedUserMemberId).Delete();
```

<span data-ttu-id="798a0-119">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="798a0-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="798a0-120">**Project**: Partner Center SDK-voor beelden **klasse**: RemoveCustomerUserMemberFromDirectoryRole.cs</span><span class="sxs-lookup"><span data-stu-id="798a0-120">**Project**: Partner Center SDK Samples **Class**: RemoveCustomerUserMemberFromDirectoryRole.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="798a0-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="798a0-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="798a0-122">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="798a0-122">Request syntax</span></span>

| <span data-ttu-id="798a0-123">Methode</span><span class="sxs-lookup"><span data-stu-id="798a0-123">Method</span></span>     | <span data-ttu-id="798a0-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="798a0-124">Request URI</span></span>                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="798a0-125">**VERWIJDERD**</span><span class="sxs-lookup"><span data-stu-id="798a0-125">**DELETE**</span></span> | <span data-ttu-id="798a0-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/directoryroles/{Role-id}/usermembers/{User-ID} http/1.1</span><span class="sxs-lookup"><span data-stu-id="798a0-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers/{user-ID} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="798a0-127">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="798a0-127">URI parameter</span></span>

<span data-ttu-id="798a0-128">Gebruik de volgende URI-para meters om de juiste klant, rol en gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="798a0-128">Use the following URI parameters to identify the correct customer, role and user.</span></span>

| <span data-ttu-id="798a0-129">Naam</span><span class="sxs-lookup"><span data-stu-id="798a0-129">Name</span></span>                   | <span data-ttu-id="798a0-130">Type</span><span class="sxs-lookup"><span data-stu-id="798a0-130">Type</span></span>     | <span data-ttu-id="798a0-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="798a0-131">Required</span></span> | <span data-ttu-id="798a0-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="798a0-132">Description</span></span>                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="798a0-133">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="798a0-133">**customer-tenant-id**</span></span> | <span data-ttu-id="798a0-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="798a0-134">**guid**</span></span> | <span data-ttu-id="798a0-135">J</span><span class="sxs-lookup"><span data-stu-id="798a0-135">Y</span></span>        | <span data-ttu-id="798a0-136">De waarde is een **klant-Tenant-id** die de klant aanduidt.</span><span class="sxs-lookup"><span data-stu-id="798a0-136">The value is a GUID formatted **customer-tenant-id** that identifies the customer.</span></span> |
| <span data-ttu-id="798a0-137">**rol-id**</span><span class="sxs-lookup"><span data-stu-id="798a0-137">**role-id**</span></span>            | <span data-ttu-id="798a0-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="798a0-138">**guid**</span></span> | <span data-ttu-id="798a0-139">J</span><span class="sxs-lookup"><span data-stu-id="798a0-139">Y</span></span>        | <span data-ttu-id="798a0-140">De waarde is een GUID-indeling met een **rol-id** waarmee de rol wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="798a0-140">The value is a GUID formatted **role-id** that identifies the role.</span></span>                |
| <span data-ttu-id="798a0-141">**gebruikers-id**</span><span class="sxs-lookup"><span data-stu-id="798a0-141">**user-id**</span></span>            | <span data-ttu-id="798a0-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="798a0-142">**guid**</span></span> | <span data-ttu-id="798a0-143">J</span><span class="sxs-lookup"><span data-stu-id="798a0-143">Y</span></span>        | <span data-ttu-id="798a0-144">De waarde is een **gebruikers-id** met een GUID-indeling waarmee één gebruikers account wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="798a0-144">The value is a GUID formatted **user-id** that identifies a single user account.</span></span>   |

### <a name="request-headers"></a><span data-ttu-id="798a0-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="798a0-145">Request headers</span></span>

<span data-ttu-id="798a0-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="798a0-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="798a0-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="798a0-147">Request body</span></span>

<span data-ttu-id="798a0-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="798a0-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="798a0-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="798a0-149">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04%20/directoryroles/729827e3-9c14-49f7-bb1b-9608f156bbb8/usermembers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04%20 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0a00ec08-6273-46bb-ab6f-14a13959b381
MS-CorrelationId: 87d18a45-81fc-40cf-921a-b91cb82d67fe
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 0
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="798a0-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="798a0-150">REST response</span></span>

<span data-ttu-id="798a0-151">Als de gebruiker is verwijderd uit de rol, is de antwoord tekst leeg.</span><span class="sxs-lookup"><span data-stu-id="798a0-151">If the user is removed from the role successfully, the response body is empty.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="798a0-152">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="798a0-152">Response success and error codes</span></span>

<span data-ttu-id="798a0-153">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="798a0-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="798a0-154">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="798a0-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="798a0-155">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="798a0-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="798a0-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="798a0-156">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
MS-RequestId: e784d7aa-8c8d-45ee-8f97-9e09823d7338
MS-CV: es01VX8do0u2aTXw.0
MS-ServerId: 101112616
Date: Tue, 20 Dec 2016 23:16:35 GMT
```
