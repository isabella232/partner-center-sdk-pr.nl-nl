---
title: Gebruikersaccounts maken voor een klant
description: Maak een nieuw gebruikers account voor uw klant.
ms.date: 05/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 9131a1c4c37d07b1994b67379ec8361fda13a371
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767197"
---
# <a name="create-user-accounts-for-a-customer"></a><span data-ttu-id="aabfe-103">Gebruikersaccounts maken voor een klant</span><span class="sxs-lookup"><span data-stu-id="aabfe-103">Create user accounts for a customer</span></span>

<span data-ttu-id="aabfe-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="aabfe-104">**Applies to:**</span></span>

- <span data-ttu-id="aabfe-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="aabfe-105">Partner Center</span></span>

<span data-ttu-id="aabfe-106">Maak een nieuw gebruikers account voor uw klant.</span><span class="sxs-lookup"><span data-stu-id="aabfe-106">Create a new user account for your customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="aabfe-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="aabfe-107">Prerequisites</span></span>

- <span data-ttu-id="aabfe-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="aabfe-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="aabfe-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="aabfe-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="aabfe-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="aabfe-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="aabfe-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="aabfe-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="aabfe-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="aabfe-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="aabfe-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="aabfe-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="aabfe-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="aabfe-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="aabfe-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="aabfe-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="aabfe-116">C\#</span><span class="sxs-lookup"><span data-stu-id="aabfe-116">C\#</span></span>

<span data-ttu-id="aabfe-117">Een nieuw gebruikers account voor een klant verkrijgen:</span><span class="sxs-lookup"><span data-stu-id="aabfe-117">To obtain a new user account for a customer:</span></span>

1. <span data-ttu-id="aabfe-118">Maak een nieuw **CustomerUser** -object met de relevante gebruikers informatie.</span><span class="sxs-lookup"><span data-stu-id="aabfe-118">Create a new **CustomerUser** object with the relevant user information.</span></span>

2. <span data-ttu-id="aabfe-119">Gebruik uw verzameling **IAggregatePartner. Customers** en roep de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="aabfe-119">Use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span>

3. <span data-ttu-id="aabfe-120">Roep de eigenschap **Users** aan, gevolgd door de methode **Create** .</span><span class="sxs-lookup"><span data-stu-id="aabfe-120">Call the **Users** property, followed by the **Create** method.</span></span>

``` csharp
// string selectedCustomerId;
// IAggregatePartner partnerOperations;
// var SelectedCustomer;

var userToCreate = new CustomerUser()
{
    PasswordProfile = new PasswordProfile() { ForceChangePassword = true, Password = "Password!1" },
    DisplayName = "TestDisplayName",
    FirstName = "TestFirstName",
    LastName = "TestLastName",
    UsageLocation = "US",
    UserPrincipalName = Guid.NewGuid().ToString("N") + "@" + selectedCustomer.CompanyProfile.Domain.ToString()
};

User createdUser = partnerOperations.Customers.ById(selectedCustomerId).Users.Create(userToCreate);
```

<span data-ttu-id="aabfe-121">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="aabfe-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="aabfe-122">**Project**: PartnerSDK. FeatureSamples- **klasse**: CustomerUserCreate.cs</span><span class="sxs-lookup"><span data-stu-id="aabfe-122">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserCreate.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="aabfe-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="aabfe-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="aabfe-124">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="aabfe-124">Request syntax</span></span>

| <span data-ttu-id="aabfe-125">Methode</span><span class="sxs-lookup"><span data-stu-id="aabfe-125">Method</span></span>   | <span data-ttu-id="aabfe-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="aabfe-126">Request URI</span></span>                                                                                  |
|----------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="aabfe-127">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="aabfe-127">**POST**</span></span> | <span data-ttu-id="aabfe-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users http/1.1</span><span class="sxs-lookup"><span data-stu-id="aabfe-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="aabfe-129">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="aabfe-129">URI parameters</span></span>

<span data-ttu-id="aabfe-130">Gebruik de volgende query parameters om de juiste klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="aabfe-130">Use the following query parameters to identify the correct customer.</span></span>

| <span data-ttu-id="aabfe-131">Naam</span><span class="sxs-lookup"><span data-stu-id="aabfe-131">Name</span></span> | <span data-ttu-id="aabfe-132">Type</span><span class="sxs-lookup"><span data-stu-id="aabfe-132">Type</span></span> | <span data-ttu-id="aabfe-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="aabfe-133">Required</span></span> | <span data-ttu-id="aabfe-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="aabfe-134">Description</span></span> |
|----- |----- | -------- |------------ |
| <span data-ttu-id="aabfe-135">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="aabfe-135">**customer-tenant-id**</span></span> | <span data-ttu-id="aabfe-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="aabfe-136">**guid**</span></span> | <span data-ttu-id="aabfe-137">J</span><span class="sxs-lookup"><span data-stu-id="aabfe-137">Y</span></span> | <span data-ttu-id="aabfe-138">De waarde is een **klant-Tenant-id** die als GUID is opgemaakt. Hiermee kan de wederverkoper de resultaten filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="aabfe-138">The value is a GUID formatted **customer-tenant-id**. It allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="aabfe-139">**gebruikers-id**</span><span class="sxs-lookup"><span data-stu-id="aabfe-139">**user-id**</span></span> | <span data-ttu-id="aabfe-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="aabfe-140">**guid**</span></span> | <span data-ttu-id="aabfe-141">N</span><span class="sxs-lookup"><span data-stu-id="aabfe-141">N</span></span> | <span data-ttu-id="aabfe-142">De waarde is een **gebruikers-id** met een GUID-indeling die tot één gebruikers account behoort.</span><span class="sxs-lookup"><span data-stu-id="aabfe-142">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="aabfe-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="aabfe-143">Request headers</span></span>

<span data-ttu-id="aabfe-144">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="aabfe-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="aabfe-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="aabfe-145">Request body</span></span>

<span data-ttu-id="aabfe-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="aabfe-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="aabfe-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="aabfe-147">Request example</span></span>

```http
POST https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
{
      "usageLocation": "country/region code",
      "userPrincipalName": "userid@domain.onmicrosoft.com",
      "firstName": "First",
      "lastName": "Last",
      "displayName": "User name",
      "immutableId": "Some unique ID",
      "passwordProfile":{
                 password: "abCD123*",
                 forceChangePassword: true
      },
      "attributes": {
        "objectType": "CustomerUser"
      }
}
```

## <a name="rest-response"></a><span data-ttu-id="aabfe-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="aabfe-148">REST response</span></span>

<span data-ttu-id="aabfe-149">Als dit lukt, retourneert deze methode een gebruikers account, met inbegrip van de GUID.</span><span class="sxs-lookup"><span data-stu-id="aabfe-149">If successful, this method returns a user account, including the GUID.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="aabfe-150">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="aabfe-150">Response success and error codes</span></span>

<span data-ttu-id="aabfe-151">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="aabfe-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="aabfe-152">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="aabfe-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="aabfe-153">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="aabfe-153">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="aabfe-154">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="aabfe-154">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST

{
  "usageLocation": "country/region code",
  "id": "4b10bf41-ab11-40e3-8c53-cd67849b50de",
  "userPrincipalName": "userid@domain.onmicrosoft.com",
  "firstName": "First",
  "lastName": "Last",
  "displayName": "User name",
  "immutableId": "Some unique ID",
  "passwordProfile": {
    "forceChangePassword": true,
    "password": "abCD123*"
  },
  "lastDirectorySyncTime": null,
  "userDomainType": "none",
  "state": "active",
  "softDeletionTime": null,
  "attributes": {
    "objectType": "CustomerUser"
  }
}
```