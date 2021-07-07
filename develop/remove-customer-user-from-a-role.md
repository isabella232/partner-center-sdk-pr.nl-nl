---
title: Een klantgebruiker uit een rol verwijderen
description: Een gebruiker verwijderen uit een directoryrol binnen een klantaccount.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 36dc742c4f713131b4996d7dc945b6dd008a3ef5
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445643"
---
# <a name="remove-a-customer-user-from-a-role"></a><span data-ttu-id="eb4b0-103">Een klantgebruiker uit een rol verwijderen</span><span class="sxs-lookup"><span data-stu-id="eb4b0-103">Remove a customer user from a role</span></span>

<span data-ttu-id="eb4b0-104">Een gebruiker verwijderen uit een directoryrol binnen een klantaccount.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-104">How to remove a user from a directory role within a customer account.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eb4b0-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="eb4b0-105">Prerequisites</span></span>

- <span data-ttu-id="eb4b0-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="eb4b0-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="eb4b0-107">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="eb4b0-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eb4b0-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="eb4b0-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="eb4b0-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="eb4b0-110">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="eb4b0-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="eb4b0-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="eb4b0-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="eb4b0-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="eb4b0-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eb4b0-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="eb4b0-114">C\#</span><span class="sxs-lookup"><span data-stu-id="eb4b0-114">C\#</span></span>

<span data-ttu-id="eb4b0-115">Als u een gebruiker uit een directoryrol wilt verwijderen, selecteert u de klant met de gebruiker die u wilt wijzigen met een aanroep naar de methode [**IAggregatePartner.Customers.ById.**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) Geef hier de rol op met behulp van de [**methode DirectoryRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) met de directoryrol-id.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-115">To remove a user from a directory role, select the customer with the user to modify with a call to the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method, From there, specify the role using the [**DirectoryRoles.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.idirectoryrolecollection.byid) method with the directory role ID.</span></span> <span data-ttu-id="eb4b0-116">Ga vervolgens naar de [**methode UserMembers.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.byid) om de gebruiker te identificeren die u wilt verwijderen en de methode [**Delete**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermember.delete) om de gebruiker uit de rol te verwijderen.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-116">Then, access the [**UserMembers.ById**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermembercollection.byid) method to identify the user to remove, and the [**Delete**](/dotnet/api/microsoft.store.partnercenter.customerdirectoryroles.iusermember.delete) method to remove the user from the role.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedRoleId;
// string selectedUserMemberId;

partnerOperations.Customers.ById(selectedCustomerId).DirectoryRoles.ById(selectedRoleId).UserMembers.ById(selectedUserMemberId).Delete();
```

<span data-ttu-id="eb4b0-117">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="eb4b0-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="eb4b0-118">**Project**: Partnercentrum-SDK Klasse **Samples:** RemoveCustomerUserMemberFromDirectoryRole.cs</span><span class="sxs-lookup"><span data-stu-id="eb4b0-118">**Project**: Partner Center SDK Samples **Class**: RemoveCustomerUserMemberFromDirectoryRole.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="eb4b0-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="eb4b0-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="eb4b0-120">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="eb4b0-120">Request syntax</span></span>

| <span data-ttu-id="eb4b0-121">Methode</span><span class="sxs-lookup"><span data-stu-id="eb4b0-121">Method</span></span>     | <span data-ttu-id="eb4b0-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="eb4b0-122">Request URI</span></span>                                                                                                                           |
|------------|---------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eb4b0-123">**Verwijderen**</span><span class="sxs-lookup"><span data-stu-id="eb4b0-123">**DELETE**</span></span> | <span data-ttu-id="eb4b0-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers/{user-ID} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="eb4b0-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/directoryroles/{role-ID}/usermembers/{user-ID} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="eb4b0-125">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="eb4b0-125">URI parameter</span></span>

<span data-ttu-id="eb4b0-126">Gebruik de volgende URI-parameters om de juiste klant, rol en gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-126">Use the following URI parameters to identify the correct customer, role, and user.</span></span>

| <span data-ttu-id="eb4b0-127">Naam</span><span class="sxs-lookup"><span data-stu-id="eb4b0-127">Name</span></span>                   | <span data-ttu-id="eb4b0-128">Type</span><span class="sxs-lookup"><span data-stu-id="eb4b0-128">Type</span></span>     | <span data-ttu-id="eb4b0-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="eb4b0-129">Required</span></span> | <span data-ttu-id="eb4b0-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="eb4b0-130">Description</span></span>                                                                        |
|------------------------|----------|----------|------------------------------------------------------------------------------------|
| <span data-ttu-id="eb4b0-131">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="eb4b0-131">**customer-tenant-id**</span></span> | <span data-ttu-id="eb4b0-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="eb4b0-132">**guid**</span></span> | <span data-ttu-id="eb4b0-133">J</span><span class="sxs-lookup"><span data-stu-id="eb4b0-133">Y</span></span>        | <span data-ttu-id="eb4b0-134">De waarde is een in GUID **opgemaakte klant-tenant-id** die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-134">The value is a GUID formatted **customer-tenant-id** that identifies the customer.</span></span> |
| <span data-ttu-id="eb4b0-135">**role-id**</span><span class="sxs-lookup"><span data-stu-id="eb4b0-135">**role-id**</span></span>            | <span data-ttu-id="eb4b0-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="eb4b0-136">**guid**</span></span> | <span data-ttu-id="eb4b0-137">J</span><span class="sxs-lookup"><span data-stu-id="eb4b0-137">Y</span></span>        | <span data-ttu-id="eb4b0-138">De waarde is een **rol-id** met GUID-indeling die de rol identificeert.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-138">The value is a GUID formatted **role-id** that identifies the role.</span></span>                |
| <span data-ttu-id="eb4b0-139">**user-id**</span><span class="sxs-lookup"><span data-stu-id="eb4b0-139">**user-id**</span></span>            | <span data-ttu-id="eb4b0-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="eb4b0-140">**guid**</span></span> | <span data-ttu-id="eb4b0-141">J</span><span class="sxs-lookup"><span data-stu-id="eb4b0-141">Y</span></span>        | <span data-ttu-id="eb4b0-142">De waarde is een **gebruikers-id** met GUID-indeling die één gebruikersaccount identificeert.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-142">The value is a GUID formatted **user-id** that identifies a single user account.</span></span>   |

### <a name="request-headers"></a><span data-ttu-id="eb4b0-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="eb4b0-143">Request headers</span></span>

<span data-ttu-id="eb4b0-144">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="eb4b0-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="eb4b0-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="eb4b0-145">Request body</span></span>

<span data-ttu-id="eb4b0-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="eb4b0-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="eb4b0-147">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="eb4b0-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="eb4b0-148">REST response</span></span>

<span data-ttu-id="eb4b0-149">Als de gebruiker is verwijderd uit de rol, is de antwoord-body leeg.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-149">If the user is removed from the role successfully, the response body is empty.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="eb4b0-150">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="eb4b0-150">Response success and error codes</span></span>

<span data-ttu-id="eb4b0-151">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="eb4b0-152">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="eb4b0-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="eb4b0-153">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="eb4b0-153">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="eb4b0-154">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="eb4b0-154">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 90bda268-7929-4ad6-be01-89c5af5fc504
MS-RequestId: e784d7aa-8c8d-45ee-8f97-9e09823d7338
MS-CV: es01VX8do0u2aTXw.0
MS-ServerId: 101112616
Date: Tue, 20 Dec 2016 23:16:35 GMT
```
