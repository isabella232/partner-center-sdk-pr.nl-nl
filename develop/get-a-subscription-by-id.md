---
title: Een abonnement ophalen op basis van id
description: Hiermee wordt een abonnements resource opgehaald die overeenkomt met de klant-ID en de abonnements-ID.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 6690a6886eeb31a78cdb556280d4bdc2b4beb124
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767470"
---
# <a name="get-a-subscription-by-id"></a><span data-ttu-id="92115-103">Een abonnement ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="92115-103">Get a subscription by ID</span></span>

<span data-ttu-id="92115-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="92115-104">**Applies To**</span></span>

- <span data-ttu-id="92115-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="92115-105">Partner Center</span></span>
- <span data-ttu-id="92115-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="92115-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="92115-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="92115-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="92115-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="92115-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="92115-109">Hiermee wordt een [abonnements](subscription-resources.md) resource opgehaald die overeenkomt met de klant-id en de abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="92115-109">Gets a [Subscription](subscription-resources.md) resource that matches the customer ID and the subscription ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="92115-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="92115-110">Prerequisites</span></span>

- <span data-ttu-id="92115-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="92115-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="92115-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="92115-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="92115-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="92115-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="92115-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="92115-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="92115-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="92115-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="92115-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="92115-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="92115-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="92115-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="92115-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="92115-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="92115-119">Een abonnements-ID.</span><span class="sxs-lookup"><span data-stu-id="92115-119">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="92115-120">C\#</span><span class="sxs-lookup"><span data-stu-id="92115-120">C\#</span></span>

<span data-ttu-id="92115-121">Als u een abonnement op ID wilt ophalen, moet u eerst een interface voor de abonnements bewerkingen verkrijgen door de [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) -methode aan te roepen met de klant-id om de klant te identificeren en de methode [**abonnementen. ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) om het abonnement te identificeren.</span><span class="sxs-lookup"><span data-stu-id="92115-121">To get a subscription by ID, begin by obtaining an interface to the subscription operations by calling the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to identify the customer, and the [**Subscriptions.ById**](/dotnet/api/microsoft.store.partnercenter.customerusers.icustomerusercollection.byid) method to identify the subscription.</span></span> <span data-ttu-id="92115-122">Gebruik die [**Interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) om de abonnements gegevens op te halen door [**Get aan**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get)te roepen.</span><span class="sxs-lookup"><span data-stu-id="92115-122">Use that [**interface**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription) to retrieve the subscription details by calling [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.get).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string subscriptionID;

var subscriptionDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(subscriptionID).Get();
```

<span data-ttu-id="92115-123">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="92115-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="92115-124">**Project**: Partner Center SDK-voor beelden **klasse**: GetSubscription.cs</span><span class="sxs-lookup"><span data-stu-id="92115-124">**Project**: Partner Center SDK Samples **Class**: GetSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="92115-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="92115-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="92115-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="92115-126">Request syntax</span></span>

| <span data-ttu-id="92115-127">Methode</span><span class="sxs-lookup"><span data-stu-id="92115-127">Method</span></span>  | <span data-ttu-id="92115-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="92115-128">Request URI</span></span>                                                                                                                |
|---------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="92115-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="92115-129">**GET**</span></span> | <span data-ttu-id="92115-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions/{id-for-Subscription} http/1.1</span><span class="sxs-lookup"><span data-stu-id="92115-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="92115-131">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="92115-131">URI parameter</span></span>

<span data-ttu-id="92115-132">Deze tabel bevat de vereiste query parameters om het abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="92115-132">This table lists the required query parameters to get the subscription.</span></span>

| <span data-ttu-id="92115-133">Naam</span><span class="sxs-lookup"><span data-stu-id="92115-133">Name</span></span>                    | <span data-ttu-id="92115-134">Type</span><span class="sxs-lookup"><span data-stu-id="92115-134">Type</span></span>     | <span data-ttu-id="92115-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="92115-135">Required</span></span> | <span data-ttu-id="92115-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="92115-136">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="92115-137">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="92115-137">**customer-tenant-id**</span></span>  | <span data-ttu-id="92115-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="92115-138">**guid**</span></span> | <span data-ttu-id="92115-139">J</span><span class="sxs-lookup"><span data-stu-id="92115-139">Y</span></span>        | <span data-ttu-id="92115-140">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="92115-140">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="92115-141">**id voor abonnement**</span><span class="sxs-lookup"><span data-stu-id="92115-141">**id-for-subscription**</span></span> | <span data-ttu-id="92115-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="92115-142">**guid**</span></span> | <span data-ttu-id="92115-143">J</span><span class="sxs-lookup"><span data-stu-id="92115-143">Y</span></span>        | <span data-ttu-id="92115-144">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="92115-144">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="92115-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="92115-145">Request headers</span></span>

<span data-ttu-id="92115-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="92115-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="92115-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="92115-147">Request body</span></span>

<span data-ttu-id="92115-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="92115-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="92115-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="92115-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/4d3cf487-70f4-4e1e-9ff1-b2bfce8d9f04/subscriptions/A356AC8C-E310-44F4-BF85-C7F29044AF99 HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 8f489776-a3f3-47cb-91c3-538e1f70f560
MS-CorrelationId: e72e1dc3-4abd-4ce0-908b-d23fdaedcb28
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="92115-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="92115-150">REST response</span></span>

<span data-ttu-id="92115-151">Als dit lukt, retourneert deze methode een resource van een [abonnement](subscription-resources.md) in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="92115-151">If successful, this method returns a [Subscription](subscription-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="92115-152">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="92115-152">Response success and error codes</span></span>

<span data-ttu-id="92115-153">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="92115-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="92115-154">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="92115-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="92115-155">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="92115-155">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example-for-a-standard-subscription"></a><span data-ttu-id="92115-156">Antwoord voorbeeld voor een Standard-abonnement</span><span class="sxs-lookup"><span data-stu-id="92115-156">Response example for a standard subscription</span></span>

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

### <a name="response-example-for-an-add-on-subscription"></a><span data-ttu-id="92115-157">Antwoord voorbeeld voor een invoeg toepassings abonnement</span><span class="sxs-lookup"><span data-stu-id="92115-157">Response example for an add-on subscription</span></span>

<span data-ttu-id="92115-158">Het antwoord voor een invoeg toepassings abonnement bevat de ID van het bovenliggende abonnement in de hoofd tekst en de koppelingen.</span><span class="sxs-lookup"><span data-stu-id="92115-158">The response for an add-on subscription includes the parent subscription ID in the body and in the links.</span></span>

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
