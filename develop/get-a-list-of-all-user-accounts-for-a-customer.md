---
title: Een lijst met alle gebruikersaccounts voor een klant ophalen
description: Een lijst met alle gebruikersaccounts van een van uw klanten op te halen.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: f3d5fcc610eae8c1bff056c1e4a9e7a74093c87d
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874564"
---
# <a name="get-a-list-of-all-user-accounts-for-a-customer"></a><span data-ttu-id="53181-103">Een lijst met alle gebruikersaccounts voor een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="53181-103">Get a list of all user accounts for a customer</span></span>

<span data-ttu-id="53181-104">In dit artikel wordt beschreven hoe u een lijst op kunt halen met alle gebruikersaccounts die deel uitmaken van een van uw klanten.</span><span class="sxs-lookup"><span data-stu-id="53181-104">This article describes how to get a list of all user accounts that belong to one of your customers.</span></span>

<span data-ttu-id="53181-105">Zie Get a user account by ID (Een gebruikersaccount op id opmaken) als u één gebruikersaccount op id [wilt op zoeken.](get-a-user-account-by-id.md)</span><span class="sxs-lookup"><span data-stu-id="53181-105">To look up a single user account by ID, see [Get a user account by ID](get-a-user-account-by-id.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="53181-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="53181-106">Prerequisites</span></span>

- <span data-ttu-id="53181-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="53181-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="53181-108">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="53181-108">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="53181-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="53181-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="53181-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="53181-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="53181-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="53181-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="53181-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="53181-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="53181-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="53181-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="53181-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="53181-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="53181-115">C\#</span><span class="sxs-lookup"><span data-stu-id="53181-115">C\#</span></span>

<span data-ttu-id="53181-116">De verzameling van alle gebruikersaccounts voor een opgegeven klant ophalen:</span><span class="sxs-lookup"><span data-stu-id="53181-116">To retrieve the collection of all user accounts for a specified customer:</span></span>

1. <span data-ttu-id="53181-117">Roep de [**methode IAggregatePartner.Customers.ById aan**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de opgegeven klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="53181-117">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer ID to identify the customer.</span></span>

2. <span data-ttu-id="53181-118">Roep de [**methode Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) om de verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="53181-118">Call the [**Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) method to retrieve the collection.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

// Get customer users collection.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.Get();
```

<span data-ttu-id="53181-119">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="53181-119">For an example, see the following:</span></span>

- <span data-ttu-id="53181-120">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="53181-120">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="53181-121">Project: **Partnercentrum-SDK Voorbeelden**</span><span class="sxs-lookup"><span data-stu-id="53181-121">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="53181-122">Klasse: **GetCustomerUserCollection.cs**</span><span class="sxs-lookup"><span data-stu-id="53181-122">Class: **GetCustomerUserCollection.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="53181-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="53181-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="53181-124">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="53181-124">Request syntax</span></span>

| <span data-ttu-id="53181-125">Methode</span><span class="sxs-lookup"><span data-stu-id="53181-125">Method</span></span>  | <span data-ttu-id="53181-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="53181-126">Request URI</span></span>                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="53181-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="53181-127">**GET**</span></span> | <span data-ttu-id="53181-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="53181-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="53181-129">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="53181-129">URI parameter</span></span>

<span data-ttu-id="53181-130">Gebruik de volgende URI-parameter om de juiste klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="53181-130">Use the following URI parameter to identify the correct customer.</span></span>

| <span data-ttu-id="53181-131">Naam</span><span class="sxs-lookup"><span data-stu-id="53181-131">Name</span></span>                   | <span data-ttu-id="53181-132">Type</span><span class="sxs-lookup"><span data-stu-id="53181-132">Type</span></span>     | <span data-ttu-id="53181-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="53181-133">Required</span></span> | <span data-ttu-id="53181-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="53181-134">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="53181-135">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="53181-135">**customer-tenant-id**</span></span> | <span data-ttu-id="53181-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="53181-136">**guid**</span></span> | <span data-ttu-id="53181-137">J</span><span class="sxs-lookup"><span data-stu-id="53181-137">Y</span></span>        | <span data-ttu-id="53181-138">De waarde is een in GUID opgemaakte **klant-tenant-id** waarmee de reseller de resultaten kan filteren voor een bepaalde klant die bij de reseller hoort.</span><span class="sxs-lookup"><span data-stu-id="53181-138">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="53181-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="53181-139">Request headers</span></span>

<span data-ttu-id="53181-140">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="53181-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="53181-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="53181-141">Request body</span></span>

<span data-ttu-id="53181-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="53181-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="53181-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="53181-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 5d845377-5b7d-4cd4-98f6-19e5ae3faa81
MS-CorrelationId: 5a3d64d4-4490-4932-bf5e-0dc9a58f27ca
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="53181-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="53181-144">REST response</span></span>

<span data-ttu-id="53181-145">Als dit lukt, retourneert deze methode een verzameling gebruikersaccounts voor een klant.</span><span class="sxs-lookup"><span data-stu-id="53181-145">If successful, this method returns a collection of user accounts for a customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="53181-146">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="53181-146">Response success and error codes</span></span>

<span data-ttu-id="53181-147">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="53181-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="53181-148">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="53181-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="53181-149">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="53181-149">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="53181-150">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="53181-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1030
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 5a3d64d4-4490-4932-bf5e-0dc9a58f27ca
MS-RequestId: 5d845377-5b7d-4cd4-98f6-19e5ae3faa81
MS-CV: 6zmKqrSFB0+t7m3y.0
MS-ServerId: 101112616
Date: Wed, 21 Dec 2016 21:13:24 GMT

 {
    "totalCount": 2,
    "items": [{
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
        }, {
            "id": "6e668259-1f09-479d-bcb8-d9b03e826b8d",
            "userPrincipalName": "admin@dtdemocspcustomer005.onmicrosoft.com",
            "firstName": "Daniel",
            "lastName": "Tsai",
            "displayName": "DT Demo CSP Customer 005",
            "userDomainType": "none",
            "state": "active",
            "links": {
                "self": {
                    "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users/6e668259-1f09-479d-bcb8-d9b03e826b8d",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "CustomerUser"
            }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Collection"
    }
}
```
