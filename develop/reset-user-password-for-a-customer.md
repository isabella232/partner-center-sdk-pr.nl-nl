---
title: Gebruikerswachtwoord voor een klant opnieuw instellen
description: Het opnieuw instellen van een wachtwoord is vergelijkbaar met het bijwerken van andere gegevens in een bestaand gebruikersaccount voor uw klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: f3661a588f566485cbd58035c63ae9f8e5d383af
ms.sourcegitcommit: 0b2a62af1765a447addd9c4340c28bc42fdc2747
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/04/2021
ms.locfileid: "111445677"
---
# <a name="reset-user-password-for-a-customer"></a><span data-ttu-id="d09df-103">Gebruikerswachtwoord voor een klant opnieuw instellen</span><span class="sxs-lookup"><span data-stu-id="d09df-103">Reset user password for a customer</span></span>

<span data-ttu-id="d09df-104">Het opnieuw instellen van een wachtwoord is vergelijkbaar met het bijwerken van andere gegevens in een bestaand gebruikersaccount voor uw klant.</span><span class="sxs-lookup"><span data-stu-id="d09df-104">Resetting a password is similar to updating other details in an existing user account for your customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d09df-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d09df-105">Prerequisites</span></span>

- <span data-ttu-id="d09df-106">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d09df-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d09df-107">Dit scenario ondersteunt alleen verificatie met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="d09df-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="d09df-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d09df-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d09df-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="d09df-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d09df-110">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="d09df-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d09df-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="d09df-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d09df-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="d09df-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d09df-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d09df-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="d09df-114">C\#</span><span class="sxs-lookup"><span data-stu-id="d09df-114">C\#</span></span>

<span data-ttu-id="d09df-115">Als u een wachtwoord voor een opgegeven klantgebruiker opnieuw wilt instellen, haalt u eerst de opgegeven klant-id en de beoogde gebruiker op.</span><span class="sxs-lookup"><span data-stu-id="d09df-115">To reset a password for a specified customer user, first retrieve the specified customer ID and the targeted user.</span></span> <span data-ttu-id="d09df-116">Maak vervolgens een nieuw **CustomerUser-object** dat de informatie voor de bestaande klant bevat, maar met een nieuw **PasswordProfile-object.**</span><span class="sxs-lookup"><span data-stu-id="d09df-116">Then, create a new **CustomerUser** object that contains the information for the existing customer, but with a new **PasswordProfile** object.</span></span> <span data-ttu-id="d09df-117">Gebruik vervolgens de verzameling **IAggregatePartner.Customers** en roep de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="d09df-117">Then, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="d09df-118">Roep vervolgens de **eigenschap Users,** de **methode ById()** en vervolgens de **patchmethode aan.**</span><span class="sxs-lookup"><span data-stu-id="d09df-118">Then call the **Users** property, the **ById()** method, and then the **Patch** method.</span></span>

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

<span data-ttu-id="d09df-119">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d09df-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d09df-120">**Project:** Klasse PartnerSDK.FeatureSamples: CustomerUserUpdate.cs </span><span class="sxs-lookup"><span data-stu-id="d09df-120">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserUpdate.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="d09df-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d09df-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d09df-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="d09df-122">Request syntax</span></span>

| <span data-ttu-id="d09df-123">Methode</span><span class="sxs-lookup"><span data-stu-id="d09df-123">Method</span></span>    | <span data-ttu-id="d09df-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d09df-124">Request URI</span></span>                                                                                  |
|-----------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="d09df-125">**Patch**</span><span class="sxs-lookup"><span data-stu-id="d09df-125">**PATCH**</span></span> | <span data-ttu-id="d09df-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="d09df-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="d09df-127">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="d09df-127">URI parameter</span></span>

<span data-ttu-id="d09df-128">Gebruik de volgende queryparameter om de juiste klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="d09df-128">Use the following query parameter to identify the correct customer.</span></span>

| <span data-ttu-id="d09df-129">Naam</span><span class="sxs-lookup"><span data-stu-id="d09df-129">Name</span></span>                   | <span data-ttu-id="d09df-130">Type</span><span class="sxs-lookup"><span data-stu-id="d09df-130">Type</span></span>     | <span data-ttu-id="d09df-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="d09df-131">Required</span></span> | <span data-ttu-id="d09df-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d09df-132">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d09df-133">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="d09df-133">**customer-tenant-id**</span></span> | <span data-ttu-id="d09df-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="d09df-134">**guid**</span></span> | <span data-ttu-id="d09df-135">J</span><span class="sxs-lookup"><span data-stu-id="d09df-135">Y</span></span>        | <span data-ttu-id="d09df-136">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="d09df-136">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="d09df-137">**user-id**</span><span class="sxs-lookup"><span data-stu-id="d09df-137">**user-id**</span></span>            | <span data-ttu-id="d09df-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="d09df-138">**guid**</span></span> | <span data-ttu-id="d09df-139">J</span><span class="sxs-lookup"><span data-stu-id="d09df-139">Y</span></span>        | <span data-ttu-id="d09df-140">De waarde is een **gebruikers-id** met GUID-indeling die bij één gebruikersaccount hoort.</span><span class="sxs-lookup"><span data-stu-id="d09df-140">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                       |

### <a name="request-headers"></a><span data-ttu-id="d09df-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d09df-141">Request headers</span></span>

<span data-ttu-id="d09df-142">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="d09df-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d09df-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="d09df-143">Request body</span></span>

### <a name="request-example"></a><span data-ttu-id="d09df-144">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d09df-144">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="d09df-145">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d09df-145">REST response</span></span>

<span data-ttu-id="d09df-146">Als dit lukt, retourneert deze methode de gebruikersgegevens, samen met de bijgewerkte wachtwoordgegevens.</span><span class="sxs-lookup"><span data-stu-id="d09df-146">If successful, this method returns the user information, along with the updated password information.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d09df-147">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="d09df-147">Response success and error codes</span></span>

<span data-ttu-id="d09df-148">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="d09df-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d09df-149">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d09df-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d09df-150">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="d09df-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d09df-151">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d09df-151">Response example</span></span>

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
