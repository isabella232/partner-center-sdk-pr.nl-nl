---
title: Een gebruikersaccount voor een klant verwijderen
description: Een bestaand gebruikersaccount voor een klant verwijderen.
ms.date: 06/20/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: c45646da43b8926f911942374de5da07f318c526
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973057"
---
# <a name="delete-a-user-account-for-a-customer"></a><span data-ttu-id="05429-103">Een gebruikersaccount voor een klant verwijderen</span><span class="sxs-lookup"><span data-stu-id="05429-103">Delete a user account for a customer</span></span>

<span data-ttu-id="05429-104">In dit artikel wordt uitgelegd hoe u een bestaand gebruikersaccount voor een klant verwijdert.</span><span class="sxs-lookup"><span data-stu-id="05429-104">This article explains how to delete an existing user account for a customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="05429-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="05429-105">Prerequisites</span></span>

- <span data-ttu-id="05429-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="05429-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="05429-107">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="05429-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="05429-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="05429-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="05429-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="05429-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="05429-110">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="05429-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="05429-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="05429-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="05429-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="05429-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="05429-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="05429-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="05429-114">Een gebruikers-id.</span><span class="sxs-lookup"><span data-stu-id="05429-114">A user ID.</span></span> <span data-ttu-id="05429-115">Zie Get a list of all user accounts for a customer (Een lijst met alle gebruikersaccounts voor een klant opmaken) als u niet over de [gebruikers-id hebt.](get-a-list-of-all-user-accounts-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="05429-115">If you do not have the user ID, see [Get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md).</span></span>

## <a name="deleting-a-user-account"></a><span data-ttu-id="05429-116">Een gebruikersaccount verwijderen</span><span class="sxs-lookup"><span data-stu-id="05429-116">Deleting a user account</span></span>

<span data-ttu-id="05429-117">Wanneer u een gebruikersaccount verwijdert, wordt de gebruikerstoestand ingesteld op **inactief** voor 30 dagen.</span><span class="sxs-lookup"><span data-stu-id="05429-117">When you delete a user account, the user state is set to **inactive** for 30 days.</span></span> <span data-ttu-id="05429-118">Na dertig dagen worden het gebruikersaccount en de bijbehorende gegevens verwijderd en onherkenbaar gemaakt.</span><span class="sxs-lookup"><span data-stu-id="05429-118">After thirty 30 days, the user account and its associated data are purged and made unrecoverable.</span></span>

<span data-ttu-id="05429-119">U kunt [een verwijderd gebruikersaccount voor een](restore-a-user-for-a-customer.md) klant herstellen als het inactieve account binnen het venster van 30 dagen valt.</span><span class="sxs-lookup"><span data-stu-id="05429-119">You can [restore a deleted user account for a customer](restore-a-user-for-a-customer.md) if the inactive account is within the 30-day window.</span></span> <span data-ttu-id="05429-120">Wanneer u echter een account herstelt dat is verwijderd en gemarkeerd als inactief, wordt het account niet meer geretourneerd als lid van de gebruikersverzameling (bijvoorbeeld wanneer u een lijst met alle gebruikersaccounts voor een klant [krijgt).](get-a-list-of-all-user-accounts-for-a-customer.md)</span><span class="sxs-lookup"><span data-stu-id="05429-120">However, when you restore an account that was deleted and marked as inactive, the account is no longer returned as a member of the user collection (for example, when you [get a list of all user accounts for a customer](get-a-list-of-all-user-accounts-for-a-customer.md)).</span></span>

## <a name="c"></a><span data-ttu-id="05429-121">C\#</span><span class="sxs-lookup"><span data-stu-id="05429-121">C\#</span></span>

<span data-ttu-id="05429-122">Een bestaand klantgebruikersaccount verwijderen:</span><span class="sxs-lookup"><span data-stu-id="05429-122">To delete an existing customer user account:</span></span>

1. <span data-ttu-id="05429-123">Gebruik de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="05429-123">Use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span>

2. <span data-ttu-id="05429-124">Roep de [**methode Users.ById aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om de gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="05429-124">Call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the user.</span></span>

3. <span data-ttu-id="05429-125">Roep de [**methode Delete**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) aan om de gebruiker te verwijderen en de gebruikerstoestand in te stellen op inactief.</span><span class="sxs-lookup"><span data-stu-id="05429-125">Call the [**Delete**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomeruser.delete) method to delete the user and set the user state to inactive.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string customerUserIdToDelete;

partnerOperations.Customers.ById(selectedCustomerId).Users.ById(customerUserIdToDelete).Delete();
```

<span data-ttu-id="05429-126">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="05429-126">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="05429-127">**Project**: Partnercentrum-SDK **Voorbeeldklasse:** DeleteCustomerUser.cs</span><span class="sxs-lookup"><span data-stu-id="05429-127">**Project**: Partner Center SDK Samples **Class**: DeleteCustomerUser.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="05429-128">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="05429-128">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="05429-129">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="05429-129">Request syntax</span></span>

| <span data-ttu-id="05429-130">Methode</span><span class="sxs-lookup"><span data-stu-id="05429-130">Method</span></span>     | <span data-ttu-id="05429-131">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="05429-131">Request URI</span></span>                                                                                            |
|------------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="05429-132">DELETE</span><span class="sxs-lookup"><span data-stu-id="05429-132">DELETE</span></span>     | <span data-ttu-id="05429-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="05429-133">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="05429-134">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="05429-134">URI parameters</span></span>

<span data-ttu-id="05429-135">Gebruik de volgende queryparameters om de klant en gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="05429-135">Use the following query parameters to identify the customer and user.</span></span>

| <span data-ttu-id="05429-136">Naam</span><span class="sxs-lookup"><span data-stu-id="05429-136">Name</span></span>                   | <span data-ttu-id="05429-137">Type</span><span class="sxs-lookup"><span data-stu-id="05429-137">Type</span></span>     | <span data-ttu-id="05429-138">Vereist</span><span class="sxs-lookup"><span data-stu-id="05429-138">Required</span></span> | <span data-ttu-id="05429-139">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="05429-139">Description</span></span>                                                                                                               |
|------------------------|----------|----------|---------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="05429-140">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="05429-140">customer-tenant-id</span></span>     | <span data-ttu-id="05429-141">GUID</span><span class="sxs-lookup"><span data-stu-id="05429-141">GUID</span></span>     | <span data-ttu-id="05429-142">J</span><span class="sxs-lookup"><span data-stu-id="05429-142">Y</span></span>        | <span data-ttu-id="05429-143">De waarde is een **klant-tenant-id** in GUID-indeling waarmee de reseller de resultaten voor een bepaalde klant kan filteren.</span><span class="sxs-lookup"><span data-stu-id="05429-143">The value is a GUID-formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer.</span></span> |
| <span data-ttu-id="05429-144">user-id</span><span class="sxs-lookup"><span data-stu-id="05429-144">user-id</span></span>                | <span data-ttu-id="05429-145">GUID</span><span class="sxs-lookup"><span data-stu-id="05429-145">GUID</span></span>     | <span data-ttu-id="05429-146">J</span><span class="sxs-lookup"><span data-stu-id="05429-146">Y</span></span>        | <span data-ttu-id="05429-147">De waarde is een gebruikers-id in **GUID-indeling** die bij één gebruikersaccount hoort.</span><span class="sxs-lookup"><span data-stu-id="05429-147">The value is a GUID-formatted **user-id** that belongs to a single user account.</span></span>                                          |

### <a name="request-headers"></a><span data-ttu-id="05429-148">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="05429-148">Request headers</span></span>

<span data-ttu-id="05429-149">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="05429-149">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="05429-150">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="05429-150">Request body</span></span>

<span data-ttu-id="05429-151">Geen.</span><span class="sxs-lookup"><span data-stu-id="05429-151">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="05429-152">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="05429-152">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="05429-153">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="05429-153">REST response</span></span>

<span data-ttu-id="05429-154">Als dit lukt, retourneert deze methode de statuscode **204 Geen** inhoud.</span><span class="sxs-lookup"><span data-stu-id="05429-154">If successful, this method returns a **204 No Content** status code.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="05429-155">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="05429-155">Response success and error codes</span></span>

<span data-ttu-id="05429-156">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="05429-156">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="05429-157">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="05429-157">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="05429-158">Zie REST-foutcodes voor [Partner Center de volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="05429-158">For the full list, see [Partner Center REST Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="05429-159">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="05429-159">Response example</span></span>

```http
HTTP/1.1 204 No Content
Content-Length: 0
MS-CorrelationId: 709c0b80-016c-4662-b29f-697fdf03e87a
MS-RequestId: f113b126-ec13-4baa-ab4d-67c245244971
MS-CV: 90KUJA7HKEaG8wHu.0
MS-ServerId: 101112616
Date: Tue, 24 Jan 2017 23:27:18 GMT
```
