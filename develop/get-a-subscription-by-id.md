---
title: Een abonnement ophalen op basis van id
description: Haalt een abonnementsresource op die overeenkomt met de klant-id en de abonnements-id.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 75f21a3f76e5502ba40b89995aa26bd0e668b3fa
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873816"
---
# <a name="get-a-subscription-by-id"></a><span data-ttu-id="0dffe-103">Een abonnement ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="0dffe-103">Get a subscription by ID</span></span>

<span data-ttu-id="0dffe-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0dffe-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0dffe-105">Haalt een [abonnementsresource](subscription-resources.md) op die overeenkomt met de klant-id en de abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="0dffe-105">Gets a [Subscription](subscription-resources.md) resource that matches the customer ID and the subscription ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0dffe-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0dffe-106">Prerequisites</span></span>

- <span data-ttu-id="0dffe-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0dffe-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0dffe-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="0dffe-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="0dffe-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0dffe-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="0dffe-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="0dffe-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="0dffe-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="0dffe-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="0dffe-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="0dffe-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="0dffe-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="0dffe-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="0dffe-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0dffe-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="0dffe-115">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="0dffe-115">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="0dffe-116">C\#</span><span class="sxs-lookup"><span data-stu-id="0dffe-116">C\#</span></span>

<span data-ttu-id="0dffe-117">Als u een abonnement op id wilt verkrijgen, begint u met het verkrijgen van een interface voor de abonnementsbewerkingen door de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan te roepen met de klant-id om de klant te identificeren en de methode [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="0dffe-117">To get a subscription by ID, begin by obtaining an interface to the subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the subscription.</span></span> <span data-ttu-id="0dffe-118">Gebruik deze [**interface om de**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) abonnementsgegevens op te halen door Ophalen aan te [**roepen.**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get)</span><span class="sxs-lookup"><span data-stu-id="0dffe-118">Use that [**interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) to retrieve the subscription details by calling [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string subscriptionID;

var subscriptionDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(subscriptionID).Get();
```

<span data-ttu-id="0dffe-119">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="0dffe-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="0dffe-120">**Project:** Partnercentrum-SDK Klasse **Samples:** GetSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="0dffe-120">**Project**: Partner Center SDK Samples **Class**: GetSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="0dffe-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="0dffe-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0dffe-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="0dffe-122">Request syntax</span></span>

| <span data-ttu-id="0dffe-123">Methode</span><span class="sxs-lookup"><span data-stu-id="0dffe-123">Method</span></span>  | <span data-ttu-id="0dffe-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="0dffe-124">Request URI</span></span>                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0dffe-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="0dffe-125">**GET**</span></span> | <span data-ttu-id="0dffe-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0dffe-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="0dffe-127">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="0dffe-127">URI parameter</span></span>

<span data-ttu-id="0dffe-128">Deze tabel bevat de vereiste queryparameters om het abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="0dffe-128">This table lists the required query parameters to get the subscription.</span></span>

| <span data-ttu-id="0dffe-129">Naam</span><span class="sxs-lookup"><span data-stu-id="0dffe-129">Name</span></span>                    | <span data-ttu-id="0dffe-130">Type</span><span class="sxs-lookup"><span data-stu-id="0dffe-130">Type</span></span>     | <span data-ttu-id="0dffe-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="0dffe-131">Required</span></span> | <span data-ttu-id="0dffe-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0dffe-132">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="0dffe-133">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="0dffe-133">**customer-tenant-id**</span></span>  | <span data-ttu-id="0dffe-134">**guid**</span><span class="sxs-lookup"><span data-stu-id="0dffe-134">**guid**</span></span> | <span data-ttu-id="0dffe-135">J</span><span class="sxs-lookup"><span data-stu-id="0dffe-135">Y</span></span>        | <span data-ttu-id="0dffe-136">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="0dffe-136">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="0dffe-137">**id-for-subscription**</span><span class="sxs-lookup"><span data-stu-id="0dffe-137">**id-for-subscription**</span></span> | <span data-ttu-id="0dffe-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="0dffe-138">**guid**</span></span> | <span data-ttu-id="0dffe-139">J</span><span class="sxs-lookup"><span data-stu-id="0dffe-139">Y</span></span>        | <span data-ttu-id="0dffe-140">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="0dffe-140">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="0dffe-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="0dffe-141">Request headers</span></span>

<span data-ttu-id="0dffe-142">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="0dffe-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0dffe-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="0dffe-143">Request body</span></span>

<span data-ttu-id="0dffe-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="0dffe-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0dffe-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="0dffe-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/A356AC8C-E310-44F4-BF85-C7F29044AF99 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8f489776-a3f3-47cb-91c3-538e1f70f560
MS-CorrelationId: e72e1dc3-4abd-4ce0-908b-d23fdaedcb28
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="0dffe-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="0dffe-146">REST response</span></span>

<span data-ttu-id="0dffe-147">Als dit lukt, retourneert deze methode een [abonnementsresource](subscription-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="0dffe-147">If successful, this method returns a [Subscription](subscription-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0dffe-148">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="0dffe-148">Response success and error codes</span></span>

<span data-ttu-id="0dffe-149">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="0dffe-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0dffe-150">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="0dffe-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0dffe-151">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="0dffe-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-for-a-standard-subscription"></a><span data-ttu-id="0dffe-152">Voorbeeld van een antwoord voor een standaardabonnement</span><span class="sxs-lookup"><span data-stu-id="0dffe-152">Response example for a standard subscription</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 833
Content-Type: application/json; charset=utf-8
MS-CorrelationId: e72e1dc3-4abd-4ce0-908b-d23fdaedcb28
MS-RequestId: 8f489776-a3f3-47cb-91c3-538e1f70f560
MS-CV: 7v11Wa//5EuGEo+A.0
MS-ServerId: 202010406
Date: Fri, 27 Jan 2017 21:51:40 GMT

{
    "id": "A356AC8C-E310-44F4-BF85-C7F29044AF99",
    "entitlementId": "42226ED6-070A-4E0F-B80C-4CDFB3E97AA7",
    "offerId": "MS-AZR-0145P",
    "offerName": "Microsoft Azure",
    "friendlyName": "Microsoft Azure",
    "quantity": 1,
    "unitType": "Usage-based",
    "creationDate": "2016-05-10T07:30:05.427Z",
    "effectiveStartDate": "2016-05-10T00:00:00Z",
    "commitmentEndDate": "9999-12-10T00:00:00Z",
    "status": "active",
    "autoRenewEnabled": false,
    "billingType": "usage",
    "contractType": "subscription",
    "links": {
        "offer": {
            "uri": "/offers/MS-AZR-0145P?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/A356AC8C-E310-44F4-BF85-C7F29044AF99",
            "method": "GET",
            "headers": []
        }
    },
    "orderId": "B23FDEDD-D6BD-415A-8B71-3624C81C9644",
    "attributes": {
        "etag": "eyJpZCI6ImEzNTZhYzhjLWUzMTAtNDRmNC1iZjg1LWM3ZjI5MDQ0YWY5OSIsInZlcnNpb24iOjJ9",
        "objectType": "Subscription"
    }
}
```

### <a name="response-example-for-an-add-on-subscription"></a><span data-ttu-id="0dffe-153">Voorbeeld van een reactie voor een invoegabonnement</span><span class="sxs-lookup"><span data-stu-id="0dffe-153">Response example for an add-on subscription</span></span>

<span data-ttu-id="0dffe-154">Het antwoord voor een invoegabonnement bevat de bovenliggende abonnements-id in de hoofdliggende en in de koppelingen.</span><span class="sxs-lookup"><span data-stu-id="0dffe-154">The response for an add-on subscription includes the parent subscription ID in the body and in the links.</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1132
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 6eacec93-852d-4167-9d96-c57809bea7ed
MS-RequestId: 22bfd0fb-d1e6-4a8f-aa1a-124b7c820d80
MS-CV: cmde2DtbuUWi8JLq.0
MS-ServerId: 201022015
Date: Fri, 27 Jan 2017 00:12:53 GMT

{
    "id": "968BA1CF-C146-4ADF-A300-308DCF718EEE",
    "offerId": "2828BE95-46BA-4F91-B2FD-0BEF192ECF60",
    "offerName": "Exchange Online Archiving for Exchange Online",
    "friendlyName": "Some friendly name",
    "quantity": 2,
    "unitType": "Licenses",
    "parentSubscriptionId": "1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
    "creationDate": "2017-01-25T23:01:08.693Z",
    "effectiveStartDate": "2017-01-25T00:00:00Z",
    "commitmentEndDate": "2018-02-10T00:00:00Z",
    "status": "active",
    "autoRenewEnabled": true,
    "billingType": "license",
    "contractType": "subscription",
    "links": {
        "offer": {
            "uri": "/offers/2828BE95-46BA-4F91-B2FD-0BEF192ECF60?country=US",
            "method": "GET",
            "headers": []
        },
        "parentSubscription": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/1C2B75C1-74A5-472A-A729-7F8CEFC477F9",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/968BA1CF-C146-4ADF-A300-308DCF718EEE",
            "method": "GET",
            "headers": []
        }
    },
    "orderId": "CF3B0E37-BE0B-4CDD-B584-D1A97D98A922",
    "attributes": {
        "etag": "eyJpZCI6Ijk2OGJhMWNmLWMxNDYtNGFkZi1hMzAwLTMwOGRjZjcxOGVlZSIsInZlcnNpb24iOjF9",
        "objectType": "Subscription"
    }
}
```
