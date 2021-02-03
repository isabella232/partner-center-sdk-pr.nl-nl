---
title: Een lijst met alle gebruikersaccounts voor een klant ophalen
description: Een lijst met alle gebruikers accounts ophalen die deel uitmaken van een van uw klanten.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 6f2b1bcf9926e02232b6e2cc68b71e992b015324
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767372"
---
# <a name="get-a-list-of-all-user-accounts-for-a-customer"></a><span data-ttu-id="8618a-103">Een lijst met alle gebruikersaccounts voor een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="8618a-103">Get a list of all user accounts for a customer</span></span>

<span data-ttu-id="8618a-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="8618a-104">**Applies to:**</span></span>

- <span data-ttu-id="8618a-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="8618a-105">Partner Center</span></span>

<span data-ttu-id="8618a-106">In dit artikel wordt beschreven hoe u een lijst krijgt van alle gebruikers accounts die deel uitmaken van een van uw klanten.</span><span class="sxs-lookup"><span data-stu-id="8618a-106">This article describes how to get a list of all user accounts that belong to one of your customers.</span></span>

<span data-ttu-id="8618a-107">Als u één gebruikers account wilt opzoeken op basis van ID, raadpleegt u [een gebruikers account ophalen op basis van de id](get-a-user-account-by-id.md).</span><span class="sxs-lookup"><span data-stu-id="8618a-107">To look up a single user account by ID, see [Get a user account by ID](get-a-user-account-by-id.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8618a-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="8618a-108">Prerequisites</span></span>

- <span data-ttu-id="8618a-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="8618a-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="8618a-110">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="8618a-110">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="8618a-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8618a-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="8618a-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="8618a-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="8618a-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="8618a-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="8618a-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="8618a-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="8618a-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="8618a-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="8618a-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="8618a-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="8618a-117">C\#</span><span class="sxs-lookup"><span data-stu-id="8618a-117">C\#</span></span>

<span data-ttu-id="8618a-118">De verzameling van alle gebruikers accounts voor een opgegeven klant ophalen:</span><span class="sxs-lookup"><span data-stu-id="8618a-118">To retrieve the collection of all user accounts for a specified customer:</span></span>

1. <span data-ttu-id="8618a-119">Roep de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de opgegeven klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="8618a-119">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the specified customer ID to identify the customer.</span></span>

2. <span data-ttu-id="8618a-120">Roep de methode [**Users. Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) aan om de verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="8618a-120">Call the [**Users.Get**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.getasync) method to retrieve the collection.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

// Get customer users collection.
var customerUsers = partnerOperations.Customers.ById(selectedCustomerId).Users.Get();
```

<span data-ttu-id="8618a-121">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="8618a-121">For an example, see the following:</span></span>

- <span data-ttu-id="8618a-122">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="8618a-122">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="8618a-123">Project: **Partner Center SDK** -voor beelden</span><span class="sxs-lookup"><span data-stu-id="8618a-123">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="8618a-124">Klasse: **GetCustomerUserCollection.cs**</span><span class="sxs-lookup"><span data-stu-id="8618a-124">Class: **GetCustomerUserCollection.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="8618a-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="8618a-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="8618a-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="8618a-126">Request syntax</span></span>

| <span data-ttu-id="8618a-127">Methode</span><span class="sxs-lookup"><span data-stu-id="8618a-127">Method</span></span>  | <span data-ttu-id="8618a-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="8618a-128">Request URI</span></span>                                                                                  |
|---------|----------------------------------------------------------------------------------------------|
| <span data-ttu-id="8618a-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="8618a-129">**GET**</span></span> | <span data-ttu-id="8618a-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-ID}/users http/1.1</span><span class="sxs-lookup"><span data-stu-id="8618a-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/users HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="8618a-131">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="8618a-131">URI parameter</span></span>

<span data-ttu-id="8618a-132">Gebruik de volgende URI-para meter om de juiste klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="8618a-132">Use the following URI parameter to identify the correct customer.</span></span>

| <span data-ttu-id="8618a-133">Naam</span><span class="sxs-lookup"><span data-stu-id="8618a-133">Name</span></span>                   | <span data-ttu-id="8618a-134">Type</span><span class="sxs-lookup"><span data-stu-id="8618a-134">Type</span></span>     | <span data-ttu-id="8618a-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="8618a-135">Required</span></span> | <span data-ttu-id="8618a-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="8618a-136">Description</span></span>                                                                                                                                            |
|------------------------|----------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="8618a-137">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="8618a-137">**customer-tenant-id**</span></span> | <span data-ttu-id="8618a-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="8618a-138">**guid**</span></span> | <span data-ttu-id="8618a-139">J</span><span class="sxs-lookup"><span data-stu-id="8618a-139">Y</span></span>        | <span data-ttu-id="8618a-140">De waarde is een door de **klant-Tenant-id** opgemaakte naam waarmee de wederverkoper de resultaten kan filteren voor een bepaalde klant die bij de wederverkoper hoort.</span><span class="sxs-lookup"><span data-stu-id="8618a-140">The value is a GUID formatted **customer-tenant-id** that allows the reseller to filter the results for a given customer that belongs to the reseller.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="8618a-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="8618a-141">Request headers</span></span>

<span data-ttu-id="8618a-142">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="8618a-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="8618a-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="8618a-143">Request body</span></span>

<span data-ttu-id="8618a-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="8618a-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="8618a-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="8618a-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/users HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 5d845377-5b7d-4cd4-98f6-19e5ae3faa81
MS-CorrelationId: 5a3d64d4-4490-4932-bf5e-0dc9a58f27ca
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="8618a-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="8618a-146">REST response</span></span>

<span data-ttu-id="8618a-147">Als dit lukt, retourneert deze methode een verzameling gebruikers accounts voor een klant.</span><span class="sxs-lookup"><span data-stu-id="8618a-147">If successful, this method returns a collection of user accounts for a customer.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="8618a-148">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="8618a-148">Response success and error codes</span></span>

<span data-ttu-id="8618a-149">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="8618a-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="8618a-150">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="8618a-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="8618a-151">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="8618a-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="8618a-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="8618a-152">Response example</span></span>

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
