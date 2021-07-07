---
title: De abonnementen van een klant ophalen
description: Een verzameling van de abonnementen van een klant ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 01ac9e5169258d0ac263d5bbe8cff567c76f98ed
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760620"
---
# <a name="get-a-customers-subscriptions"></a><span data-ttu-id="0bd64-103">De abonnementen van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="0bd64-103">Get a customer's subscriptions</span></span>

<span data-ttu-id="0bd64-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="0bd64-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="0bd64-105">Een verzameling van de abonnementen van een klant ophalen.</span><span class="sxs-lookup"><span data-stu-id="0bd64-105">How to get a collection of a customer's subscriptions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="0bd64-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="0bd64-106">Prerequisites</span></span>

- <span data-ttu-id="0bd64-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="0bd64-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="0bd64-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="0bd64-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="0bd64-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0bd64-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="0bd64-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="0bd64-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="0bd64-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="0bd64-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="0bd64-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="0bd64-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="0bd64-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="0bd64-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="0bd64-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="0bd64-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="0bd64-115">C\#</span><span class="sxs-lookup"><span data-stu-id="0bd64-115">C\#</span></span>

<span data-ttu-id="0bd64-116">Als u een lijst met alle abonnementen van een klant wilt, gebruikt u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="0bd64-116">To get a list of all of a customer's subscriptions, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to identify the customer.</span></span> <span data-ttu-id="0bd64-117">Gebruik vervolgens de eigenschap [**Abonnementen om**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) een interface op te halen voor bewerkingen voor het verzamelen van abonnementen.</span><span class="sxs-lookup"><span data-stu-id="0bd64-117">Then use the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to subscription collection operations.</span></span> <span data-ttu-id="0bd64-118">Roep ten slotte de [**methoden Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) om de verzameling abonnementen van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="0bd64-118">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) methods to retrieve the customer's subscriptions collection.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var customerSubscriptions = partnerOperations.Customers.ById(customerId).Subscriptions.Get();
```

<span data-ttu-id="0bd64-119">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="0bd64-119">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="0bd64-120">**Project:** Partnercentrum-SDK Samples **Class**: GetSubscriptions.cs</span><span class="sxs-lookup"><span data-stu-id="0bd64-120">**Project**: Partner Center SDK Samples **Class**: GetSubscriptions.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="0bd64-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="0bd64-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="0bd64-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="0bd64-122">Request syntax</span></span>

| <span data-ttu-id="0bd64-123">Methode</span><span class="sxs-lookup"><span data-stu-id="0bd64-123">Method</span></span>  | <span data-ttu-id="0bd64-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="0bd64-124">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="0bd64-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="0bd64-125">**GET**</span></span> | <span data-ttu-id="0bd64-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="0bd64-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="0bd64-127">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="0bd64-127">URI parameter</span></span>

<span data-ttu-id="0bd64-128">Deze tabel bevat de vereiste queryparameter om alle abonnementen op te halen.</span><span class="sxs-lookup"><span data-stu-id="0bd64-128">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="0bd64-129">Naam</span><span class="sxs-lookup"><span data-stu-id="0bd64-129">Name</span></span>               | <span data-ttu-id="0bd64-130">Type</span><span class="sxs-lookup"><span data-stu-id="0bd64-130">Type</span></span>   | <span data-ttu-id="0bd64-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="0bd64-131">Required</span></span> | <span data-ttu-id="0bd64-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="0bd64-132">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="0bd64-133">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="0bd64-133">customer-tenant-id</span></span> | <span data-ttu-id="0bd64-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="0bd64-134">string</span></span> | <span data-ttu-id="0bd64-135">Ja</span><span class="sxs-lookup"><span data-stu-id="0bd64-135">Yes</span></span>      | <span data-ttu-id="0bd64-136">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="0bd64-136">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="0bd64-137">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="0bd64-137">Request headers</span></span>

<span data-ttu-id="0bd64-138">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="0bd64-138">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="0bd64-139">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="0bd64-139">Request body</span></span>

<span data-ttu-id="0bd64-140">Geen.</span><span class="sxs-lookup"><span data-stu-id="0bd64-140">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="0bd64-141">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="0bd64-141">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b2d13828-2ca5-41d4-94fb-9946214f4244
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="0bd64-142">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="0bd64-142">REST response</span></span>

<span data-ttu-id="0bd64-143">Als dit lukt, retourneert deze methode een verzameling [abonnementsresources](subscription-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="0bd64-143">If successful, this method returns a collection of [Subscription](subscription-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="0bd64-144">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="0bd64-144">Response success and error codes</span></span>

<span data-ttu-id="0bd64-145">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="0bd64-145">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="0bd64-146">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="0bd64-146">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="0bd64-147">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="0bd64-147">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="0bd64-148">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="0bd64-148">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
MS-RequestId: b2d13828-2ca5-41d4-94fb-9946214f4244
Date: Wed, 25 Nov 2015 05:43:06 GMT

{
    "totalCount": 37,
    "items": [{
        "id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
        "entitlementId": "a356ac8c-e310-44f4-bf85-C7f29044af99",
        "friendlyName": "nickname",
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
        "orderId": "6183db3d-6318-4e52-877e-25806e4971be",
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
