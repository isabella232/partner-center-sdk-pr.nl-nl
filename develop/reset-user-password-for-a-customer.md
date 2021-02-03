---
title: Gebruikerswachtwoord voor een klant opnieuw instellen
description: Het opnieuw instellen van een wacht woord lijkt veel op het bijwerken van andere gegevens in een bestaand gebruikers account voor uw klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: e0df93c2db55ec0fe49fc0e3089b7e11928f32bb
ms.sourcegitcommit: cfedd76e573c5616cf006f826f4e27f08281f7b4
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 07/08/2020
ms.locfileid: "97767219"
---
# <a name="reset-user-password-for-a-customer"></a><span data-ttu-id="c5ee3-103">Gebruikerswachtwoord voor een klant opnieuw instellen</span><span class="sxs-lookup"><span data-stu-id="c5ee3-103">Reset user password for a customer</span></span>

<span data-ttu-id="c5ee3-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="c5ee3-104">**Applies To**</span></span>

- <span data-ttu-id="c5ee3-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="c5ee3-105">Partner Center</span></span>

<span data-ttu-id="c5ee3-106">Het opnieuw instellen van een wacht woord lijkt veel op het bijwerken van andere gegevens in een bestaand gebruikers account voor uw klant.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-106">Resetting a password is very similar to updating other details in an existing user account for your customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c5ee3-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="c5ee3-107">Prerequisites</span></span>

- <span data-ttu-id="c5ee3-108">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="c5ee3-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="c5ee3-109">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-109">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="c5ee3-110">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c5ee3-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="c5ee3-111">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="c5ee3-112">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="c5ee3-113">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="c5ee3-114">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="c5ee3-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="c5ee3-115">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="c5ee3-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="c5ee3-116">C\#</span><span class="sxs-lookup"><span data-stu-id="c5ee3-116">C\#</span></span>

<span data-ttu-id="c5ee3-117">Als u een wacht woord voor een opgegeven klant gebruiker opnieuw wilt instellen, moet u eerst de opgegeven klant-ID en de doel gebruiker ophalen.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-117">To reset a password for a specified customer user, first retrieve the specified customer ID and the targeted user.</span></span> <span data-ttu-id="c5ee3-118">Maak vervolgens een nieuw **CustomerUser** -object dat de informatie voor de bestaande klant bevat, maar met een nieuw **PasswordProfile** -object.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-118">Then, create a new **CustomerUser** object that contains the information for the existing customer, but with a new **PasswordProfile** object.</span></span> <span data-ttu-id="c5ee3-119">Vervolgens gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-119">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="c5ee3-120">Roep vervolgens de eigenschap **Users** , de methode **ById ()** , en vervolgens de **patch** -methode aan.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-120">Then call the **Users** property, the **ById()** method, and then the **Patch** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// CustomerUser specifiedUser;

var selectedCustomer = partnerOperations.Customers.ById(selectedCustomerId).Get();
var userToUpdate = new CustomerUser()
   {
      PasswordProfile = new PasswordProfile() { ForceChangePassword = true, Password = "newPassword" },
      DisplayName = "Roger Federer",
      FirstName = "Roger",
      LastName = "Federer",
      UsageLocation = "US",
      UserPrincipalName = Guid.NewGuid().ToString("N") + "@" + selectedCustomer.CompanyProfile.Domain.ToString()
   };

// update customer user information
User updatedCustomerUserInfo = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(specifiedUser.Id).Patch(userToUpdate);

```

<span data-ttu-id="c5ee3-121">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="c5ee3-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="c5ee3-122">**Project**: PartnerSDK. FeatureSamples- **klasse**: CustomerUserUpdate.cs</span><span class="sxs-lookup"><span data-stu-id="c5ee3-122">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserUpdate.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="c5ee3-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="c5ee3-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="c5ee3-124">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c5ee3-124">Request syntax</span></span>

| <span data-ttu-id="c5ee3-125">Methode</span><span class="sxs-lookup"><span data-stu-id="c5ee3-125">Method</span></span>    | <span data-ttu-id="c5ee3-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="c5ee3-126">Request URI</span></span>                                                                                  |
|-----------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="c5ee3-127">**VERZENDEN**</span><span class="sxs-lookup"><span data-stu-id="c5ee3-127">**PATCH**</span></span> | <span data-ttu-id="c5ee3-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users http/1.1</span><span class="sxs-lookup"><span data-stu-id="c5ee3-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="c5ee3-129">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="c5ee3-129">URI parameter</span></span>

<span data-ttu-id="c5ee3-130">Gebruik de volgende query parameter om de juiste klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-130">Use the following query parameter to identify the correct customer.</span></span>

| <span data-ttu-id="c5ee3-131">Naam</span><span class="sxs-lookup"><span data-stu-id="c5ee3-131">Name</span></span>                   | <span data-ttu-id="c5ee3-132">Type</span><span class="sxs-lookup"><span data-stu-id="c5ee3-132">Type</span></span>     | <span data-ttu-id="c5ee3-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="c5ee3-133">Required</span></span> | <span data-ttu-id="c5ee3-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="c5ee3-134">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="c5ee3-135">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="c5ee3-135">**customer-tenant-id**</span></span> | <span data-ttu-id="c5ee3-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="c5ee3-136">**guid**</span></span> | <span data-ttu-id="c5ee3-137">J</span><span class="sxs-lookup"><span data-stu-id="c5ee3-137">Y</span></span>        | <span data-ttu-id="c5ee3-138">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-138">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="c5ee3-139">**gebruikers-id**</span><span class="sxs-lookup"><span data-stu-id="c5ee3-139">**user-id**</span></span>            | <span data-ttu-id="c5ee3-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="c5ee3-140">**guid**</span></span> | <span data-ttu-id="c5ee3-141">J</span><span class="sxs-lookup"><span data-stu-id="c5ee3-141">Y</span></span>        | <span data-ttu-id="c5ee3-142">De waarde is een **gebruikers-id** met een GUID-indeling die tot één gebruikers account behoort.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-142">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                       |

### <a name="request-headers"></a><span data-ttu-id="c5ee3-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="c5ee3-143">Request headers</span></span>

<span data-ttu-id="c5ee3-144">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="c5ee3-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="c5ee3-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="c5ee3-145">Request body</span></span>

### <a name="request-example"></a><span data-ttu-id="c5ee3-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="c5ee3-146">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/users/<user-id> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
{
     "passwordProfile":{
        password: "Renew456*",
        forceChangePassword: true
      },

      "attributes": {
        "objectType": "CustomerUser"
      }
}
```

## <a name="rest-response"></a><span data-ttu-id="c5ee3-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="c5ee3-147">REST response</span></span>

<span data-ttu-id="c5ee3-148">Als dit lukt, retourneert deze methode de gebruikers gegevens, samen met de bijgewerkte wachtwoord gegevens.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-148">If successful, this method returns the user information, along with the updated password information.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="c5ee3-149">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="c5ee3-149">Response success and error codes</span></span>

<span data-ttu-id="c5ee3-150">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="c5ee3-151">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="c5ee3-152">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="c5ee3-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="c5ee3-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="c5ee3-153">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 31942
Content-Type: application/json
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
MS-RequestId: b1317092-f087-471e-a637-f66523b2b94c
Date: June 24 2016 22:00:25 PST
{
  "usageLocation": "AX",
  "id": "95794928-9abe-4548-8b43-50ffc20b9404",
  "userPrincipalName": "aaaa4@abcdefgh1234.ccsctp.net",
  "firstName": "aaaa4",
  "lastName": "aaaa4",
  "displayName": "aaaa4",
  "passwordProfile": {
    "forceChangePassword": false,
    "password": "Renew456*"
  },
  "lastDirectorySyncTime": null,
  "userDomainType": "none",
  "state": "active",
  "softDeletionTime": null,
  "links": {
    "self": {
      "uri": "/customers/eebd1b55-5360-4438-a11d-5c06918c3014/users/95794928-9abe-4548-8b43-50ffc20b9404",
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
