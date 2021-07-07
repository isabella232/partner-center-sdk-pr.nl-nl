---
title: Gebruikersaccounts voor een klant bijwerken
description: Werk details bij in een bestaand gebruikersaccount voor uw klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 6ebfdbb5df1d56416835af771fd6b70190776012
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445269"
---
# <a name="update-user-accounts-for-a-customer"></a><span data-ttu-id="28887-103">Gebruikersaccounts voor een klant bijwerken</span><span class="sxs-lookup"><span data-stu-id="28887-103">Update user accounts for a customer</span></span>

<span data-ttu-id="28887-104">Werk details bij in een bestaand gebruikersaccount voor uw klant.</span><span class="sxs-lookup"><span data-stu-id="28887-104">Update details in an existing user account for your customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="28887-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="28887-105">Prerequisites</span></span>

- <span data-ttu-id="28887-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="28887-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="28887-107">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="28887-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="28887-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="28887-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="28887-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="28887-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="28887-110">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="28887-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="28887-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="28887-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="28887-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="28887-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="28887-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="28887-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="28887-114">C\#</span><span class="sxs-lookup"><span data-stu-id="28887-114">C\#</span></span>

<span data-ttu-id="28887-115">Als u de details voor een opgegeven klantgebruiker wilt bijwerken, haalt u eerst de opgegeven klant-id en de gebruiker op die u wilt bijwerken.</span><span class="sxs-lookup"><span data-stu-id="28887-115">To update the details for a specified customer user, first retrieve the specified customer ID and user to update.</span></span> <span data-ttu-id="28887-116">Maak vervolgens een bijgewerkte versie van de gebruiker in een nieuw **CustomerUser-object.**</span><span class="sxs-lookup"><span data-stu-id="28887-116">Then, create an updated version of the user in a new **CustomerUser** object.</span></span> <span data-ttu-id="28887-117">Gebruik vervolgens de verzameling **IAggregatePartner.Customers** en roep de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="28887-117">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="28887-118">Roep vervolgens de **eigenschap Users** aan, de **methode ById(),** gevolgd door de **methode Patch().**</span><span class="sxs-lookup"><span data-stu-id="28887-118">Then call the **Users** property, the **ById()** method, followed by the **Patch()** method.</span></span>

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

<span data-ttu-id="28887-119">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="28887-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="28887-120">**Project:** Klasse PartnerSDK.FeatureSamples: CustomerUserUpdate.cs </span><span class="sxs-lookup"><span data-stu-id="28887-120">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserUpdate.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="28887-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="28887-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="28887-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="28887-122">Request syntax</span></span>

| <span data-ttu-id="28887-123">Methode</span><span class="sxs-lookup"><span data-stu-id="28887-123">Method</span></span>    | <span data-ttu-id="28887-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="28887-124">Request URI</span></span>                                                                                  |
|-----------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="28887-125">**Patch**</span><span class="sxs-lookup"><span data-stu-id="28887-125">**PATCH**</span></span> | <span data-ttu-id="28887-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="28887-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="28887-127">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="28887-127">URI parameter</span></span>

<span data-ttu-id="28887-128">Gebruik de volgende queryparameter om de juiste klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="28887-128">Use the following query parameter to identify the correct customer.</span></span>

| <span data-ttu-id="28887-129">Naam</span><span class="sxs-lookup"><span data-stu-id="28887-129">Name</span></span>                   | <span data-ttu-id="28887-130">Type</span><span class="sxs-lookup"><span data-stu-id="28887-130">Type</span></span>     | <span data-ttu-id="28887-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="28887-131">Required</span></span> | <span data-ttu-id="28887-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="28887-132">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="28887-133">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="28887-133">**customer-tenant-id**</span></span> | <span data-ttu-id="28887-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="28887-134">**guid**</span></span> | <span data-ttu-id="28887-135">J</span><span class="sxs-lookup"><span data-stu-id="28887-135">Y</span></span>        | <span data-ttu-id="28887-136">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="28887-136">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="28887-137">**user-id**</span><span class="sxs-lookup"><span data-stu-id="28887-137">**user-id**</span></span>            | <span data-ttu-id="28887-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="28887-138">**guid**</span></span> | <span data-ttu-id="28887-139">J</span><span class="sxs-lookup"><span data-stu-id="28887-139">Y</span></span>        | <span data-ttu-id="28887-140">De waarde is een guid-opgemaakte **gebruikers-id** die bij één gebruikersaccount hoort.</span><span class="sxs-lookup"><span data-stu-id="28887-140">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                       |

### <a name="request-headers"></a><span data-ttu-id="28887-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="28887-141">Request headers</span></span>

<span data-ttu-id="28887-142">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="28887-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="28887-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="28887-143">Request body</span></span>

### <a name="request-example"></a><span data-ttu-id="28887-144">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="28887-144">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="28887-145">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="28887-145">REST response</span></span>

<span data-ttu-id="28887-146">Als dit lukt, retourneert deze methode een gebruikersaccount met de bijgewerkte informatie.</span><span class="sxs-lookup"><span data-stu-id="28887-146">If successful, this method returns a user account with the updated information.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="28887-147">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="28887-147">Response success and error codes</span></span>

<span data-ttu-id="28887-148">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="28887-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="28887-149">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="28887-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="28887-150">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="28887-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="28887-151">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="28887-151">Response example</span></span>

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
