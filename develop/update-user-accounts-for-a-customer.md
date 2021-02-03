---
title: Gebruikersaccounts voor een klant bijwerken
description: Details bijwerken in een bestaand gebruikers account voor uw klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 52a43341bf2c3ba64d8c232af01f3fbae6765d82
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767322"
---
# <a name="update-user-accounts-for-a-customer"></a><span data-ttu-id="eae08-103">Gebruikersaccounts voor een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="eae08-103">Update user accounts for a customer</span></span>

<span data-ttu-id="eae08-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="eae08-104">**Applies To**</span></span>

- <span data-ttu-id="eae08-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="eae08-105">Partner Center</span></span>

<span data-ttu-id="eae08-106">Details bijwerken in een bestaand gebruikers account voor uw klant.</span><span class="sxs-lookup"><span data-stu-id="eae08-106">Update details in an existing user account for your customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="eae08-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="eae08-107">Prerequisites</span></span>

- <span data-ttu-id="eae08-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="eae08-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="eae08-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="eae08-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="eae08-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eae08-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="eae08-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="eae08-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="eae08-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="eae08-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="eae08-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="eae08-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="eae08-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="eae08-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="eae08-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="eae08-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="eae08-116">C\#</span><span class="sxs-lookup"><span data-stu-id="eae08-116">C\#</span></span>

<span data-ttu-id="eae08-117">Als u de details van een opgegeven klant gebruiker wilt bijwerken, moet u eerst de opgegeven klant-ID en gebruiker ophalen om bij te werken.</span><span class="sxs-lookup"><span data-stu-id="eae08-117">To update the details for a specified customer user, first retrieve the specified customer ID and user to update.</span></span> <span data-ttu-id="eae08-118">Maak vervolgens een bijgewerkte versie van de gebruiker in een nieuw **CustomerUser** -object.</span><span class="sxs-lookup"><span data-stu-id="eae08-118">Then, create an updated version of the user in a new **CustomerUser** object.</span></span> <span data-ttu-id="eae08-119">Vervolgens gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="eae08-119">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="eae08-120">Roep vervolgens de eigenschap **Users** aan, de methode **ById ()** , gevolgd door de methode **patch ()** .</span><span class="sxs-lookup"><span data-stu-id="eae08-120">Then call the **Users** property, the **ById()** method, followed by the **Patch()** method.</span></span>

``` csharp
// string selectedCustomerId;
// customerUser specifiedUser;
// IAggregatePartner partnerOperations;

// Updated information
var userToUpdate = new CustomerUser()
{
    PasswordProfile = new PasswordProfile() { ForceChangePassword = true, Password = "testPw@!122B" },
    DisplayName = "DisplayNameChange",
    FirstName = "FirstNameChange",
    LastName = "LastNameChange",
    UsageLocation = "US",
    UserPrincipalName = Guid.NewGuid().ToString("N") + "@" + selectedCustomer.CompanyProfile.Domain.ToString()
};

// Update customer user information
User updatedCustomerUserInfo = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(specifiedUser.Id).Patch(userToUpdate);

```

<span data-ttu-id="eae08-121">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="eae08-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="eae08-122">**Project**: PartnerSDK. FeatureSamples- **klasse**: CustomerUserUpdate.cs</span><span class="sxs-lookup"><span data-stu-id="eae08-122">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserUpdate.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="eae08-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="eae08-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="eae08-124">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="eae08-124">Request syntax</span></span>

| <span data-ttu-id="eae08-125">Methode</span><span class="sxs-lookup"><span data-stu-id="eae08-125">Method</span></span>    | <span data-ttu-id="eae08-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="eae08-126">Request URI</span></span>                                                                                  |
|-----------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="eae08-127">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="eae08-127">**PATCH**</span></span> | <span data-ttu-id="eae08-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users http/1.1</span><span class="sxs-lookup"><span data-stu-id="eae08-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="eae08-129">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="eae08-129">URI parameter</span></span>

<span data-ttu-id="eae08-130">Gebruik de volgende query parameter om de juiste klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="eae08-130">Use the following query parameter to identify the correct customer.</span></span>

| <span data-ttu-id="eae08-131">Naam</span><span class="sxs-lookup"><span data-stu-id="eae08-131">Name</span></span>                   | <span data-ttu-id="eae08-132">Type</span><span class="sxs-lookup"><span data-stu-id="eae08-132">Type</span></span>     | <span data-ttu-id="eae08-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="eae08-133">Required</span></span> | <span data-ttu-id="eae08-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="eae08-134">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="eae08-135">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="eae08-135">**customer-tenant-id**</span></span> | <span data-ttu-id="eae08-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="eae08-136">**guid**</span></span> | <span data-ttu-id="eae08-137">J</span><span class="sxs-lookup"><span data-stu-id="eae08-137">Y</span></span>        | <span data-ttu-id="eae08-138">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="eae08-138">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="eae08-139">**gebruikers-id**</span><span class="sxs-lookup"><span data-stu-id="eae08-139">**user-id**</span></span>            | <span data-ttu-id="eae08-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="eae08-140">**guid**</span></span> | <span data-ttu-id="eae08-141">J</span><span class="sxs-lookup"><span data-stu-id="eae08-141">Y</span></span>        | <span data-ttu-id="eae08-142">De waarde is een **gebruikers-id** met een GUID-indeling die tot één gebruikers account behoort.</span><span class="sxs-lookup"><span data-stu-id="eae08-142">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                       |

### <a name="request-headers"></a><span data-ttu-id="eae08-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="eae08-143">Request headers</span></span>

<span data-ttu-id="eae08-144">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="eae08-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="eae08-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="eae08-145">Request body</span></span>

### <a name="request-example"></a><span data-ttu-id="eae08-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="eae08-146">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
{
      "usageLocation": "new country/region code",

      "attributes": {
        "objectType": "CustomerUser"
      }
}
```

## <a name="rest-response"></a><span data-ttu-id="eae08-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="eae08-147">REST response</span></span>

<span data-ttu-id="eae08-148">Als dit lukt, retourneert deze methode een gebruikers account met de bijgewerkte gegevens.</span><span class="sxs-lookup"><span data-stu-id="eae08-148">If successful, this method returns a user account with the updated information.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="eae08-149">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="eae08-149">Response success and error codes</span></span>

<span data-ttu-id="eae08-150">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="eae08-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="eae08-151">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="eae08-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="eae08-152">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="eae08-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="eae08-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="eae08-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST
{
  "usageLocation": "new country/region code",
  "id": "4b10bf41-ab11-40e3-8c53-cd67849b50de",
  "userPrincipalName": "emailidchange@abcdefgh1234.ccsctp.net",
  "firstName": "FirstNameChange",
  "lastName": "LastNameChange",
  "displayName": "DisplayNameChange",
  "userDomainType": "none",
  "state": "active",
  "links": {
    "self": {
      "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014/users/4b10bf41-ab11-40e3-8c53-cd67849b50de",
      "method": "GET",
      "headers": [

      ]
    }
  },
  "attributes": {
    "objectType": "CustomerUser"
  }
}
```
