---
title: Een gebruikersaccount ophalen op basis van id
description: Haal een specifiek gebruikersaccount voor een klant op.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 3a7cac98a8081a8557dcadfb0724f5497be7d14c
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760263"
---
# <a name="get-a-user-account-by-id"></a><span data-ttu-id="7473b-103">Een gebruikersaccount ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="7473b-103">Get a user account by ID</span></span>

<span data-ttu-id="7473b-104">Haal een specifiek gebruikersaccount voor een klant op.</span><span class="sxs-lookup"><span data-stu-id="7473b-104">Get a specific user account for a customer.</span></span>

- <span data-ttu-id="7473b-105">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7473b-105">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7473b-106">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="7473b-106">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="7473b-107">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7473b-107">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7473b-108">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="7473b-108">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7473b-109">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="7473b-109">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7473b-110">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="7473b-110">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7473b-111">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="7473b-111">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7473b-112">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7473b-112">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="7473b-113">C\#</span><span class="sxs-lookup"><span data-stu-id="7473b-113">C\#</span></span>

<span data-ttu-id="7473b-114">Als u een gebruikersaccount voor een klant wilt ophalen, roept u de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="7473b-114">To retrieve a user account for a customer, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="7473b-115">Roep vervolgens de methode [**Users.ById aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om de specifieke gebruiker op te halen.</span><span class="sxs-lookup"><span data-stu-id="7473b-115">Next, call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to retrieve the specific user.</span></span> <span data-ttu-id="7473b-116">Roep ten slotte de [**methode Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) om het gebruikersaccount op te halen.</span><span class="sxs-lookup"><span data-stu-id="7473b-116">Finally, call the [**Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) method to retrieve the user account.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedCustomerUserId;

// Get customer user detail.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Get();
```

<span data-ttu-id="7473b-117">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="7473b-117">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="7473b-118">**Project**: Partnercentrum-SDK Samples **Class:** GetCustomerUserDetails.cs</span><span class="sxs-lookup"><span data-stu-id="7473b-118">**Project**: Partner Center SDK Samples **Class**: GetCustomerUserDetails.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="7473b-119">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7473b-119">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7473b-120">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="7473b-120">Request syntax</span></span>

| <span data-ttu-id="7473b-121">Methode</span><span class="sxs-lookup"><span data-stu-id="7473b-121">Method</span></span>  | <span data-ttu-id="7473b-122">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7473b-122">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7473b-123">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7473b-123">**GET**</span></span> | <span data-ttu-id="7473b-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="7473b-124">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="7473b-125">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="7473b-125">URI parameter</span></span>

<span data-ttu-id="7473b-126">Gebruik de volgende URI-parameters om de juiste klant en gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="7473b-126">Use the following URI parameters to identify the correct customer and user.</span></span>

| <span data-ttu-id="7473b-127">Naam</span><span class="sxs-lookup"><span data-stu-id="7473b-127">Name</span></span>                   | <span data-ttu-id="7473b-128">Type</span><span class="sxs-lookup"><span data-stu-id="7473b-128">Type</span></span>     | <span data-ttu-id="7473b-129">Vereist</span><span class="sxs-lookup"><span data-stu-id="7473b-129">Required</span></span> | <span data-ttu-id="7473b-130">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7473b-130">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7473b-131">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="7473b-131">**customer-tenant-id**</span></span> | <span data-ttu-id="7473b-132">**guid**</span><span class="sxs-lookup"><span data-stu-id="7473b-132">**guid**</span></span> | <span data-ttu-id="7473b-133">J</span><span class="sxs-lookup"><span data-stu-id="7473b-133">Y</span></span>        | <span data-ttu-id="7473b-134">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="7473b-134">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="7473b-135">**user-id**</span><span class="sxs-lookup"><span data-stu-id="7473b-135">**user-id**</span></span>            | <span data-ttu-id="7473b-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="7473b-136">**guid**</span></span> | <span data-ttu-id="7473b-137">J</span><span class="sxs-lookup"><span data-stu-id="7473b-137">Y</span></span>        | <span data-ttu-id="7473b-138">De waarde is een guid-opgemaakte **gebruikers-id** die bij één gebruikersaccount hoort.</span><span class="sxs-lookup"><span data-stu-id="7473b-138">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                       |

### <a name="request-headers"></a><span data-ttu-id="7473b-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7473b-139">Request headers</span></span>

<span data-ttu-id="7473b-140">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="7473b-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7473b-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7473b-141">Request body</span></span>

<span data-ttu-id="7473b-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="7473b-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7473b-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7473b-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a9ef48bb-8758-4590-a312-d4a47bfaded4 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c1f673cb-655c-45a7-8a6b-257a0a006f4b
MS-CorrelationId: 24a631eb-a110-49dc-8325-99d4b196774c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="7473b-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7473b-144">REST response</span></span>

<span data-ttu-id="7473b-145">Als dit lukt, retourneert deze methode het gebruikersaccount voor de klant.</span><span class="sxs-lookup"><span data-stu-id="7473b-145">If successful, this method returns the user account for the customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7473b-146">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="7473b-146">Response success and error codes</span></span>

<span data-ttu-id="7473b-147">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="7473b-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7473b-148">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7473b-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7473b-149">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="7473b-149">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7473b-150">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="7473b-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 432
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 24a631eb-a110-49dc-8325-99d4b196774c
MS-RequestId: c1f673cb-655c-45a7-8a6b-257a0a006f4b
MS-CV: uWM1EGU7+0aI2MvV.0
MS-ServerId: 020021921
Date: Wed, 21 Dec 2016 22:59:10 GMT

{
    "usageLocation": "US",
    "id": "a9ef48bb-8758-4590-a312-d4a47bfaded4",
    "userPrincipalName": "Daniel@dtdemocspcustomer005.onmicrosoft.com",
    "firstName": "Daniel",
    "lastName": "Tsai",
    "displayName": "Daniel Tsai",
    "userDomainType": "none",
    "state": "active",
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a9ef48bb-8758-4590-a312-d4a47bfaded4",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "CustomerUser"
    }
}
```
