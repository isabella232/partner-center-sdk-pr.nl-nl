---
title: Een gebruikersaccount ophalen op basis van id
description: Een specifiek gebruikers account voor een klant ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: a2f42001365324a65376318cb1f2d57dc123df0c
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767351"
---
# <a name="get-a-user-account-by-id"></a><span data-ttu-id="07d61-103">Een gebruikersaccount ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="07d61-103">Get a user account by ID</span></span>

<span data-ttu-id="07d61-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="07d61-104">**Applies To**</span></span>

- <span data-ttu-id="07d61-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="07d61-105">Partner Center</span></span>

<span data-ttu-id="07d61-106">Een specifiek gebruikers account voor een klant ophalen.</span><span class="sxs-lookup"><span data-stu-id="07d61-106">Get a specific user account for a customer.</span></span>

- <span data-ttu-id="07d61-107">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="07d61-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="07d61-108">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="07d61-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="07d61-109">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="07d61-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="07d61-110">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="07d61-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="07d61-111">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="07d61-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="07d61-112">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="07d61-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="07d61-113">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="07d61-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="07d61-114">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="07d61-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="07d61-115">C\#</span><span class="sxs-lookup"><span data-stu-id="07d61-115">C\#</span></span>

<span data-ttu-id="07d61-116">Als u een gebruikers account voor een klant wilt ophalen, roept u de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="07d61-116">To retrieve a user account for a customer, call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer.</span></span> <span data-ttu-id="07d61-117">Vervolgens roept u de methode [**Users. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) aan om de specifieke gebruiker op te halen.</span><span class="sxs-lookup"><span data-stu-id="07d61-117">Next, call the [**Users.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to retrieve the specific user.</span></span> <span data-ttu-id="07d61-118">Roep ten slotte de methode [**Users. Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) aan om het gebruikers account op te halen.</span><span class="sxs-lookup"><span data-stu-id="07d61-118">Finally, call the [**Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) method to retrieve the user account.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedCustomerUserId;

// Get customer user detail.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.ById(selectedCustomerUserId).Get();
```

<span data-ttu-id="07d61-119">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="07d61-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="07d61-120">**Project**: Partner Center SDK-voor beelden **klasse**: GetCustomerUserDetails.cs</span><span class="sxs-lookup"><span data-stu-id="07d61-120">**Project**: Partner Center SDK Samples **Class**: GetCustomerUserDetails.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="07d61-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="07d61-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="07d61-122">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="07d61-122">Request syntax</span></span>

| <span data-ttu-id="07d61-123">Methode</span><span class="sxs-lookup"><span data-stu-id="07d61-123">Method</span></span>  | <span data-ttu-id="07d61-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="07d61-124">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="07d61-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="07d61-125">**GET**</span></span> | <span data-ttu-id="07d61-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users/{user-id} http/1.1</span><span class="sxs-lookup"><span data-stu-id="07d61-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users/{user-id} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="07d61-127">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="07d61-127">URI parameter</span></span>

<span data-ttu-id="07d61-128">Gebruik de volgende URI-para meters om de juiste klant en gebruiker te identificeren.</span><span class="sxs-lookup"><span data-stu-id="07d61-128">Use the following URI parameters to identify the correct customer and user.</span></span>

| <span data-ttu-id="07d61-129">Naam</span><span class="sxs-lookup"><span data-stu-id="07d61-129">Name</span></span>                   | <span data-ttu-id="07d61-130">Type</span><span class="sxs-lookup"><span data-stu-id="07d61-130">Type</span></span>     | <span data-ttu-id="07d61-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="07d61-131">Required</span></span> | <span data-ttu-id="07d61-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="07d61-132">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="07d61-133">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="07d61-133">**customer-tenant-id**</span></span> | <span data-ttu-id="07d61-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="07d61-134">**guid**</span></span> | <span data-ttu-id="07d61-135">J</span><span class="sxs-lookup"><span data-stu-id="07d61-135">Y</span></span>        | <span data-ttu-id="07d61-136">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="07d61-136">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |
| <span data-ttu-id="07d61-137">**gebruikers-id**</span><span class="sxs-lookup"><span data-stu-id="07d61-137">**user-id**</span></span>            | <span data-ttu-id="07d61-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="07d61-138">**guid**</span></span> | <span data-ttu-id="07d61-139">J</span><span class="sxs-lookup"><span data-stu-id="07d61-139">Y</span></span>        | <span data-ttu-id="07d61-140">De waarde is een **gebruikers-id** met een GUID-indeling die tot één gebruikers account behoort.</span><span class="sxs-lookup"><span data-stu-id="07d61-140">The value is a GUID formatted **user-id** that belongs to a single user account.</span></span>                                                                       |

### <a name="request-headers"></a><span data-ttu-id="07d61-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="07d61-141">Request headers</span></span>

<span data-ttu-id="07d61-142">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="07d61-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="07d61-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="07d61-143">Request body</span></span>

<span data-ttu-id="07d61-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="07d61-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="07d61-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="07d61-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/a9ef48bb-8758-4590-a312-d4a47bfaded4 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: c1f673cb-655c-45a7-8a6b-257a0a006f4b
MS-CorrelationId: 24a631eb-a110-49dc-8325-99d4b196774c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="07d61-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="07d61-146">REST response</span></span>

<span data-ttu-id="07d61-147">Als dit lukt, retourneert deze methode het gebruikers account voor de klant.</span><span class="sxs-lookup"><span data-stu-id="07d61-147">If successful, this method returns the user account for the customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="07d61-148">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="07d61-148">Response success and error codes</span></span>

<span data-ttu-id="07d61-149">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="07d61-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="07d61-150">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="07d61-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="07d61-151">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="07d61-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="07d61-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="07d61-152">Response example</span></span>

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
