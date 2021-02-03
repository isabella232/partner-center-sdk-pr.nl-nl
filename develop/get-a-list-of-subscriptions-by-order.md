---
title: Een lijst met abonnementen op basis van bestelling ophalen
description: Hiermee wordt een verzameling abonnements resources opgehaald die overeenkomen met een bepaalde volg orde.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 56b9c80021cace03976d410b2a6cd4c0eee18398
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767445"
---
# <a name="get-a-list-of-subscriptions-by-order"></a><span data-ttu-id="7f46c-103">Een lijst met abonnementen op basis van bestelling ophalen</span><span class="sxs-lookup"><span data-stu-id="7f46c-103">Get a list of subscriptions by order</span></span>

<span data-ttu-id="7f46c-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="7f46c-104">**Applies To**</span></span>

- <span data-ttu-id="7f46c-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="7f46c-105">Partner Center</span></span>
- <span data-ttu-id="7f46c-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="7f46c-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="7f46c-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="7f46c-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="7f46c-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="7f46c-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="7f46c-109">Hiermee wordt een verzameling [abonnements](subscription-resources.md) resources opgehaald die overeenkomen met een bepaalde volg orde.</span><span class="sxs-lookup"><span data-stu-id="7f46c-109">Gets a collection of [Subscription](subscription-resources.md) resources that correspond to a given order.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7f46c-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="7f46c-110">Prerequisites</span></span>

- <span data-ttu-id="7f46c-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="7f46c-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="7f46c-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="7f46c-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="7f46c-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7f46c-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="7f46c-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="7f46c-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="7f46c-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="7f46c-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="7f46c-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="7f46c-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="7f46c-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="7f46c-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="7f46c-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="7f46c-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="7f46c-119">Een order-ID.</span><span class="sxs-lookup"><span data-stu-id="7f46c-119">An order ID.</span></span>

## <a name="c"></a><span data-ttu-id="7f46c-120">C\#</span><span class="sxs-lookup"><span data-stu-id="7f46c-120">C\#</span></span>

<span data-ttu-id="7f46c-121">Als u een lijst met abonnementen op volg orde wilt ontvangen, gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="7f46c-121">To get a list of subscriptions by order, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="7f46c-122">Roep vervolgens de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) aan, gevolgd door de methode **ByOrder ()** .</span><span class="sxs-lookup"><span data-stu-id="7f46c-122">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the **ByOrder()** method.</span></span> <span data-ttu-id="7f46c-123">Volt ooien door [**Get ()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync)aan te roepen.</span><span class="sxs-lookup"><span data-stu-id="7f46c-123">Finish by calling [**Get()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// string orderID;

ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ByOrder(orderID).Get();
```

<span data-ttu-id="7f46c-124">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="7f46c-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="7f46c-125">**Project**: PartnerSDK. FeatureSample- **klasse**: SubscriptionsByOrder.cs</span><span class="sxs-lookup"><span data-stu-id="7f46c-125">**Project**: PartnerSDK.FeatureSample **Class**: SubscriptionsByOrder.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="7f46c-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f46c-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="7f46c-127">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f46c-127">Request syntax</span></span>

| <span data-ttu-id="7f46c-128">Methode</span><span class="sxs-lookup"><span data-stu-id="7f46c-128">Method</span></span>  | <span data-ttu-id="7f46c-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="7f46c-129">Request URI</span></span>                                                                                                                   |
|---------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="7f46c-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="7f46c-130">**GET**</span></span> | <span data-ttu-id="7f46c-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions? order \_ -id = {id-for-order} http/1.1</span><span class="sxs-lookup"><span data-stu-id="7f46c-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions?order\_id={id-for-order} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="7f46c-132">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="7f46c-132">URI parameter</span></span>

<span data-ttu-id="7f46c-133">Deze tabel bevat de vereiste query parameter om alle abonnementen op te halen.</span><span class="sxs-lookup"><span data-stu-id="7f46c-133">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="7f46c-134">Naam</span><span class="sxs-lookup"><span data-stu-id="7f46c-134">Name</span></span>                   | <span data-ttu-id="7f46c-135">Type</span><span class="sxs-lookup"><span data-stu-id="7f46c-135">Type</span></span>     | <span data-ttu-id="7f46c-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="7f46c-136">Required</span></span> | <span data-ttu-id="7f46c-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="7f46c-137">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="7f46c-138">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="7f46c-138">**customer-tenant-id**</span></span> | <span data-ttu-id="7f46c-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="7f46c-139">**guid**</span></span> | <span data-ttu-id="7f46c-140">J</span><span class="sxs-lookup"><span data-stu-id="7f46c-140">Y</span></span>        | <span data-ttu-id="7f46c-141">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="7f46c-141">A GUID corresponding to the customer.</span></span> |
| <span data-ttu-id="7f46c-142">**id voor order**</span><span class="sxs-lookup"><span data-stu-id="7f46c-142">**id-for-order**</span></span>       | <span data-ttu-id="7f46c-143">**guid**</span><span class="sxs-lookup"><span data-stu-id="7f46c-143">**guid**</span></span> | <span data-ttu-id="7f46c-144">J</span><span class="sxs-lookup"><span data-stu-id="7f46c-144">Y</span></span>        | <span data-ttu-id="7f46c-145">Een GUID die overeenkomt met de volg orde.</span><span class="sxs-lookup"><span data-stu-id="7f46c-145">A GUID corresponding to the order.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="7f46c-146">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="7f46c-146">Request headers</span></span>

<span data-ttu-id="7f46c-147">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="7f46c-147">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="7f46c-148">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="7f46c-148">Request body</span></span>

<span data-ttu-id="7f46c-149">Geen.</span><span class="sxs-lookup"><span data-stu-id="7f46c-149">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="7f46c-150">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="7f46c-150">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions?order_id={id-for-order} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="7f46c-151">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="7f46c-151">REST response</span></span>

<span data-ttu-id="7f46c-152">Als dit lukt, retourneert deze methode een verzameling [abonnements](subscription-resources.md) resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="7f46c-152">If successful, this method returns a collection of [Subscription](subscription-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="7f46c-153">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="7f46c-153">Response success and error codes</span></span>

<span data-ttu-id="7f46c-154">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="7f46c-154">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="7f46c-155">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="7f46c-155">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="7f46c-156">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="7f46c-156">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="7f46c-157">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="7f46c-157">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
Date: Wed, 25 Nov 2015 05:50:45 GMT

{
    "totalCount": 37,
    "items": [{
        "id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
        "entitlementId": "a356ac8c-e310-44f4-bf85-C7f29044af99",
        "friendlyName": "Myofferpurchase",
        "quantity": 1,
        "unitType": "none",
        "creationDate": "2015-11-25T06: 41: 12Z",
        "effectiveStartDate": "2015-11-24T08: 00: 00Z",
        "commitmentEndDate": "2016-12-12T08: 00: 00Z",
        "status": "active",
        "autoRenewEnabled": false,
        "billingType": "none",
        "contractType": "subscription",
        "links": {
            "offer": {
                "uri": "/v1/offers/0CCA44D6-68E9-4762-94EE-31ECE98783B9",
                "method": "GET",
                "headers": []
            },
            "self": {
                "uri": "/subscriptions?key=<key>",
                "method": "GET",
                "headers": []
            }
        },
        "orderId": "{id-for-order}",
        "attributes": {
            "etag": "<etag>",
            "objectType": "Subscription"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
