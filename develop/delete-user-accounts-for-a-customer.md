---
title: Een gebruikersaccount voor een klant verwijderen
description: Een bestaand gebruikers account voor een klant verwijderen.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 77fc1a1c7264779ca549be8d52798e90c91138bb
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767388"
---
# <a name="delete-a-user-account-for-a-customer"></a><span data-ttu-id="96879-103">Een gebruikersaccount voor een klant verwijderen</span><span class="sxs-lookup"><span data-stu-id="96879-103">Delete a user account for a customer</span></span>

<span data-ttu-id="96879-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="96879-104">**Applies to:**</span></span>

- <span data-ttu-id="96879-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="96879-105">Partner Center</span></span>

<span data-ttu-id="96879-106">In dit artikel wordt uitgelegd hoe u een bestaand gebruikers account voor een klant verwijdert.</span><span class="sxs-lookup"><span data-stu-id="96879-106">This article explains how to delete an existing user account for a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="96879-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="96879-107">Prerequisites</span></span>

- <span data-ttu-id="96879-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="96879-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="96879-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="96879-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="96879-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="96879-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="96879-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="96879-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="96879-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="96879-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="96879-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="96879-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="96879-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="96879-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="96879-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="96879-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="96879-116">Een gebruikers-ID.</span><span class="sxs-lookup"><span data-stu-id="96879-116">A user ID.</span></span> <span data-ttu-id="96879-117">Als u de gebruikers-ID niet hebt, raadpleegt u [een lijst met alle gebruikers accounts voor een klant ophalen](get-a-list-of-all-user-accounts-for-a-customer.md).</span><span class="sxs-lookup"><span data-stu-id="96879-117">If you do not have the user ID, see [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md).</span></span>

## <a name="deleting-a-user-account"></a><span data-ttu-id="96879-118">Een gebruikers account verwijderen</span><span class="sxs-lookup"><span data-stu-id="96879-118">Deleting a user account</span></span>

<span data-ttu-id="96879-119">Wanneer u een gebruikers account verwijdert, wordt de gebruikers status op dertig dagen ingesteld op **inactief** .</span><span class="sxs-lookup"><span data-stu-id="96879-119">When you delete a user account, the user state is set to **inactive** for thirty days.</span></span> <span data-ttu-id="96879-120">Na dertig dagen worden het gebruikers account en de bijbehorende gegevens verwijderd en onherstelbaar gemaakt.</span><span class="sxs-lookup"><span data-stu-id="96879-120">After thirty days, the user account and its associated data are purged and made unrecoverable.</span></span>

<span data-ttu-id="96879-121">U kunt [een verwijderd gebruikers account voor een klant herstellen](restore-a-user-for-a-customer.md) als het inactieve account zich in het venster van dertig dagen bevindt.</span><span class="sxs-lookup"><span data-stu-id="96879-121">You can [restore a deleted user account for a customer](restore-a-user-for-a-customer.md) if the inactive account is within the thirty day window.</span></span> <span data-ttu-id="96879-122">Wanneer u echter een account herstelt dat is verwijderd en als inactief is gemarkeerd, wordt het account niet langer geretourneerd als lid van de gebruikers verzameling (bijvoorbeeld wanneer u [een lijst met alle gebruikers accounts voor een klant krijgt](get-a-list-of-all-user-accounts-for-a-customer.md)).</span><span class="sxs-lookup"><span data-stu-id="96879-122">However, when you restore an account that was deleted and marked as inactive, the account is no longer returned as a member of the user collection (for example, when you [get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span>

## <a name="c"></a><span data-ttu-id="96879-123">C\#</span><span class="sxs-lookup"><span data-stu-id="96879-123">C\#</span></span>

<span data-ttu-id="96879-124">Een bestaand gebruikers account van de klant verwijderen:</span><span class="sxs-lookup"><span data-stu-id="96879-124">To delete an existing customer user account:</span></span>

1. <span data-ttu-id="96879-125">Gebruik de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="96879-125">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="96879-126">Roep de [**gebruikers. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) -methode aan om de gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="96879-126">Call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the user.</span></span>

3. <span data-ttu-id="96879-127">Roep de [**verwijderings**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) methode aan om de gebruiker te verwijderen en stel de gebruikers status in op inactief.</span><span class="sxs-lookup"><span data-stu-id="96879-127">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) method to delete the user and set the user state to inactive.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string customerUserIdToDelete;

partnerOperations.Customers.ById(selectedCustomerId).Users.ById(customerUserIdToDelete).Delete();
```

<span data-ttu-id="96879-128">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="96879-128">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="96879-129">**Project**: Partner Center SDK-voor beelden **klasse**: DeleteCustomerUser.cs</span><span class="sxs-lookup"><span data-stu-id="96879-129">**Project**: Partner Center SDK Samples **Class**: DeleteCustomerUser.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="96879-130">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="96879-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="96879-131">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="96879-131">Request syntax</span></span>

| <span data-ttu-id="96879-132">Methode</span><span class="sxs-lookup"><span data-stu-id="96879-132">Method</span></span>     | <span data-ttu-id="96879-133">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="96879-133">Request URI</span></span>                                                                                            |
|------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="96879-134">DELETE</span><span class="sxs-lookup"><span data-stu-id="96879-134">DELETE</span></span>     | <span data-ttu-id="96879-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users/{user-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="96879-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="96879-136">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="96879-136">URI parameters</span></span>

<span data-ttu-id="96879-137">Gebruik de volgende query parameters om de klant en gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="96879-137">Use the following query parameters to identify the customer and user.</span></span>

| <span data-ttu-id="96879-138">Naam</span><span class="sxs-lookup"><span data-stu-id="96879-138">Name</span></span>                   | <span data-ttu-id="96879-139">Type</span><span class="sxs-lookup"><span data-stu-id="96879-139">Type</span></span>     | <span data-ttu-id="96879-140">Vereist</span><span class="sxs-lookup"><span data-stu-id="96879-140">Required</span></span> | <span data-ttu-id="96879-141">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="96879-141">Description</span></span>                                                                                                               |
|------------------------|----------|----------|---------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="96879-142">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="96879-142">customer-tenant-id</span></span>     | <span data-ttu-id="96879-143">GUID</span><span class="sxs-lookup"><span data-stu-id="96879-143">GUID</span></span>     | <span data-ttu-id="96879-144">J</span><span class="sxs-lookup"><span data-stu-id="96879-144">Y</span></span>        | <span data-ttu-id="96879-145">De waarde is een **klant-Tenant-id** van de GUID-indeling waarmee de wederverkoper de resultaten voor een bepaalde klant kan filteren.</span><span class="sxs-lookup"><span data-stu-id="96879-145">The value is a GUID-formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer.</span></span> |
| <span data-ttu-id="96879-146">user-id</span><span class="sxs-lookup"><span data-stu-id="96879-146">user-id</span></span>                | <span data-ttu-id="96879-147">GUID</span><span class="sxs-lookup"><span data-stu-id="96879-147">GUID</span></span>     | <span data-ttu-id="96879-148">J</span><span class="sxs-lookup"><span data-stu-id="96879-148">Y</span></span>        | <span data-ttu-id="96879-149">De waarde is een **gebruikers-id** met een GUID-indeling die tot één gebruikers account behoort.</span><span class="sxs-lookup"><span data-stu-id="96879-149">The value is a GUID-formatted **user-id** that belongs to a single user account.</span></span>                                          |

### <a name="request-headers"></a><span data-ttu-id="96879-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="96879-150">Request headers</span></span>

<span data-ttu-id="96879-151">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="96879-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="96879-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="96879-152">Request body</span></span>

<span data-ttu-id="96879-153">Geen.</span><span class="sxs-lookup"><span data-stu-id="96879-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="96879-154">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="96879-154">Request example</span></span>

```http
DELETE https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a45f1416-3300-4f65-9e8d-f123b397a4ea HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
X-Locale: en-US
Host: api.partnercenter.microsoft.com
Content-Length: 0
```

## <a name="rest-response"></a><span data-ttu-id="96879-155">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="96879-155">REST response</span></span>

<span data-ttu-id="96879-156">Als deze methode is geslaagd, wordt de status code van **204 geen inhoud** geretourneerd.</span><span class="sxs-lookup"><span data-stu-id="96879-156">If successful, this method returns a **204 No Content** status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="96879-157">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="96879-157">Response success and error codes</span></span>

<span data-ttu-id="96879-158">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="96879-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="96879-159">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="96879-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="96879-160">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="96879-160">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="96879-161">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="96879-161">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CV: 90KUJA7HKEaG8wHu.0
MS-ServerId: 101112616
Date: Tue, 24 Jan 2017 23:27:18 GMT
```
