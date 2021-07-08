---
title: Een lijst met abonnementen op basis van bestelling ophalen
description: Haalt een verzameling abonnementsbronnen op die overeenkomen met een bepaalde bestelling.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 011a92500d0c7ed44f86030febd1ea83be2c6474
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111873952"
---
# <a name="get-a-list-of-subscriptions-by-order"></a><span data-ttu-id="b4b9e-103">Een lijst met abonnementen op basis van bestelling ophalen</span><span class="sxs-lookup"><span data-stu-id="b4b9e-103">Get a list of subscriptions by order</span></span>

<span data-ttu-id="b4b9e-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="b4b9e-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="b4b9e-105">Haalt een verzameling [abonnementsbronnen](subscription-resources.md) op die overeenkomen met een bepaalde bestelling.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-105">Gets a collection of [Subscription](subscription-resources.md) resources that correspond to a given order.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="b4b9e-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="b4b9e-106">Prerequisites</span></span>

- <span data-ttu-id="b4b9e-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="b4b9e-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="b4b9e-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="b4b9e-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b4b9e-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="b4b9e-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="b4b9e-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="b4b9e-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="b4b9e-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="b4b9e-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="b4b9e-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="b4b9e-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="b4b9e-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="b4b9e-115">Een order-id.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-115">An order ID.</span></span>

## <a name="c"></a><span data-ttu-id="b4b9e-116">C\#</span><span class="sxs-lookup"><span data-stu-id="b4b9e-116">C\#</span></span>

<span data-ttu-id="b4b9e-117">Als u een lijst met abonnementen op volgorde wilt ophalen, gebruikt u de verzameling **IAggregatePartner.Customers** en roept u de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-117">To get a list of subscriptions by order, use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span> <span data-ttu-id="b4b9e-118">Roep vervolgens de [**eigenschap Abonnementen aan,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) gevolgd door de **methode ByOrder().**</span><span class="sxs-lookup"><span data-stu-id="b4b9e-118">Then call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the **ByOrder()** method.</span></span> <span data-ttu-id="b4b9e-119">Als laatste roept u [**Get()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) of [**GetAsync() aan.**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync)</span><span class="sxs-lookup"><span data-stu-id="b4b9e-119">Finish by calling [**Get()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.genericoperations.ientireentitycollectionretrievaloperations-2.getasync).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// string orderID;

ResourceCollection<Subscription> customerSubscriptions = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ByOrder(orderID).Get();
```

<span data-ttu-id="b4b9e-120">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="b4b9e-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="b4b9e-121">**Project:** PartnerSDK.FeatureSample-klasse: SubscriptionsByOrder.cs </span><span class="sxs-lookup"><span data-stu-id="b4b9e-121">**Project**: PartnerSDK.FeatureSample **Class**: SubscriptionsByOrder.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="b4b9e-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="b4b9e-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="b4b9e-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="b4b9e-123">Request syntax</span></span>

| <span data-ttu-id="b4b9e-124">Methode</span><span class="sxs-lookup"><span data-stu-id="b4b9e-124">Method</span></span>  | <span data-ttu-id="b4b9e-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="b4b9e-125">Request URI</span></span>                                                                                                                   |
|---------|-------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="b4b9e-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="b4b9e-126">**GET**</span></span> | <span data-ttu-id="b4b9e-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions?order \_ id={id-for-order} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="b4b9e-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions?order\_id={id-for-order} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="b4b9e-128">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="b4b9e-128">URI parameter</span></span>

<span data-ttu-id="b4b9e-129">Deze tabel bevat de vereiste queryparameter om alle abonnementen op te halen.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-129">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="b4b9e-130">Naam</span><span class="sxs-lookup"><span data-stu-id="b4b9e-130">Name</span></span>                   | <span data-ttu-id="b4b9e-131">Type</span><span class="sxs-lookup"><span data-stu-id="b4b9e-131">Type</span></span>     | <span data-ttu-id="b4b9e-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="b4b9e-132">Required</span></span> | <span data-ttu-id="b4b9e-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="b4b9e-133">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="b4b9e-134">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="b4b9e-134">**customer-tenant-id**</span></span> | <span data-ttu-id="b4b9e-135">**guid**</span><span class="sxs-lookup"><span data-stu-id="b4b9e-135">**guid**</span></span> | <span data-ttu-id="b4b9e-136">J</span><span class="sxs-lookup"><span data-stu-id="b4b9e-136">Y</span></span>        | <span data-ttu-id="b4b9e-137">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-137">A GUID corresponding to the customer.</span></span> |
| <span data-ttu-id="b4b9e-138">**id-for-order**</span><span class="sxs-lookup"><span data-stu-id="b4b9e-138">**id-for-order**</span></span>       | <span data-ttu-id="b4b9e-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="b4b9e-139">**guid**</span></span> | <span data-ttu-id="b4b9e-140">J</span><span class="sxs-lookup"><span data-stu-id="b4b9e-140">Y</span></span>        | <span data-ttu-id="b4b9e-141">Een GUID die overeenkomt met de bestelling.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-141">A GUID corresponding to the order.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="b4b9e-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="b4b9e-142">Request headers</span></span>

<span data-ttu-id="b4b9e-143">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="b4b9e-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="b4b9e-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="b4b9e-144">Request body</span></span>

<span data-ttu-id="b4b9e-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="b4b9e-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="b4b9e-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/{customer-tenant-id}/subscriptions?order_id={id-for-order} HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="b4b9e-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="b4b9e-147">REST response</span></span>

<span data-ttu-id="b4b9e-148">Als dit lukt, retourneert deze methode een verzameling [abonnementsresources](subscription-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-148">If successful, this method returns a collection of [Subscription](subscription-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="b4b9e-149">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="b4b9e-149">Response success and error codes</span></span>

<span data-ttu-id="b4b9e-150">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="b4b9e-151">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="b4b9e-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="b4b9e-152">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="b4b9e-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="b4b9e-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="b4b9e-153">Response example</span></span>

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
