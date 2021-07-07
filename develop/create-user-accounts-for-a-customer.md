---
title: Gebruikersaccounts maken voor een klant
description: Maak een nieuw gebruikersaccount voor uw klant.
ms.date: 05/28/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: d086d7ba72c9d9e42dc88684ddeafc9a597bfd7c
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111973380"
---
# <a name="create-user-accounts-for-a-customer"></a><span data-ttu-id="68683-103">Gebruikersaccounts maken voor een klant</span><span class="sxs-lookup"><span data-stu-id="68683-103">Create user accounts for a customer</span></span>

<span data-ttu-id="68683-104">Maak een nieuw gebruikersaccount voor uw klant.</span><span class="sxs-lookup"><span data-stu-id="68683-104">Create a new user account for your customer.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="68683-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="68683-105">Prerequisites</span></span>

- <span data-ttu-id="68683-106">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="68683-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="68683-107">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="68683-107">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="68683-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="68683-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="68683-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="68683-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="68683-110">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="68683-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="68683-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="68683-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="68683-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="68683-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="68683-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="68683-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="68683-114">C\#</span><span class="sxs-lookup"><span data-stu-id="68683-114">C\#</span></span>

<span data-ttu-id="68683-115">Een nieuw gebruikersaccount voor een klant verkrijgen:</span><span class="sxs-lookup"><span data-stu-id="68683-115">To obtain a new user account for a customer:</span></span>

1. <span data-ttu-id="68683-116">Maak een nieuw **CustomerUser-object** met de relevante gebruikersgegevens.</span><span class="sxs-lookup"><span data-stu-id="68683-116">Create a new **CustomerUser** object with the relevant user information.</span></span>

2. <span data-ttu-id="68683-117">Gebruik de **verzameling IAggregatePartner.Customers** en roep de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="68683-117">Use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span>

3. <span data-ttu-id="68683-118">Roep de **eigenschap Users** aan, gevolgd door de **methode Create.**</span><span class="sxs-lookup"><span data-stu-id="68683-118">Call the **Users** property, followed by the **Create** method.</span></span>

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

<span data-ttu-id="68683-119">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="68683-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="68683-120">**Project:** Klasse PartnerSDK.FeatureSamples: CustomerUserCreate.cs </span><span class="sxs-lookup"><span data-stu-id="68683-120">**Project**: PartnerSDK.FeatureSamples **Class**: CustomerUserCreate.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="68683-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="68683-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="68683-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="68683-122">Request syntax</span></span>

| <span data-ttu-id="68683-123">Methode</span><span class="sxs-lookup"><span data-stu-id="68683-123">Method</span></span>   | <span data-ttu-id="68683-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="68683-124">Request URI</span></span>                                                                                  |
|----------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="68683-125">**Verzenden**</span><span class="sxs-lookup"><span data-stu-id="68683-125">**POST**</span></span> | <span data-ttu-id="68683-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="68683-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

#### <a name="uri-parameters"></a><span data-ttu-id="68683-127">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="68683-127">URI parameters</span></span>

<span data-ttu-id="68683-128">Gebruik de volgende queryparameters om de juiste klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="68683-128">Use the following query parameters to identify the correct customer.</span></span>

| <span data-ttu-id="68683-129">Naam</span><span class="sxs-lookup"><span data-stu-id="68683-129">Name</span></span> | <span data-ttu-id="68683-130">Type</span><span class="sxs-lookup"><span data-stu-id="68683-130">Type</span></span> | <span data-ttu-id="68683-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="68683-131">Required</span></span> | <span data-ttu-id="68683-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="68683-132">Description</span></span> |
|----- |----- | -------- |------------ |
| <span data-ttu-id="68683-133">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="68683-133">**customer-tenant-id**</span></span> | <span data-ttu-id="68683-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="68683-134">**guid**</span></span> | <span data-ttu-id="68683-135">J</span><span class="sxs-lookup"><span data-stu-id="68683-135">Y</span></span> | <span data-ttu-id="68683-136">De waarde is een in GUID **opgemaakte customer-tenant-id.** Hiermee kan de reseller de resultaten filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="68683-136">The value is a GUID formatted **customer-tenant-id**. It allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="68683-137">**user-id**</span><span class="sxs-lookup"><span data-stu-id="68683-137">**user-id**</span></span> | <span data-ttu-id="68683-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="68683-138">**guid**</span></span> | <span data-ttu-id="68683-139">N</span><span class="sxs-lookup"><span data-stu-id="68683-139">N</span></span> | <span data-ttu-id="68683-140">De waarde is een guid-opgemaakte **gebruikers-id** die bij één gebruikersaccount hoort.</span><span class="sxs-lookup"><span data-stu-id="68683-140">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="68683-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="68683-141">Request headers</span></span>

<span data-ttu-id="68683-142">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="68683-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="68683-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="68683-143">Request body</span></span>

<span data-ttu-id="68683-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="68683-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="68683-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="68683-145">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="68683-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="68683-146">REST response</span></span>

<span data-ttu-id="68683-147">Als dit lukt, retourneert deze methode een gebruikersaccount, inclusief de GUID.</span><span class="sxs-lookup"><span data-stu-id="68683-147">If successful, this method returns a user account, including the GUID.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="68683-148">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="68683-148">Response success and error codes</span></span>

<span data-ttu-id="68683-149">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="68683-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="68683-150">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="68683-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="68683-151">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="68683-151">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="68683-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="68683-152">Response example</span></span>

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