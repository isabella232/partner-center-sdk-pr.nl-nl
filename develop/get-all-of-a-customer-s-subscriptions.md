---
title: De abonnementen van een klant ophalen
description: Een verzameling van de abonnementen van een klant ophalen.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: a037e4a81fccbff0a02b0bdf6d93478ee15fd50f
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767500"
---
# <a name="get-a-customers-subscriptions"></a><span data-ttu-id="9c4ff-103">De abonnementen van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="9c4ff-103">Get a customer's subscriptions</span></span>

<span data-ttu-id="9c4ff-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="9c4ff-104">**Applies To**</span></span>

- <span data-ttu-id="9c4ff-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="9c4ff-105">Partner Center</span></span>
- <span data-ttu-id="9c4ff-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="9c4ff-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="9c4ff-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="9c4ff-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="9c4ff-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9c4ff-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="9c4ff-109">Een verzameling van de abonnementen van een klant ophalen.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-109">How to get a collection of a customer's subscriptions.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9c4ff-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9c4ff-110">Prerequisites</span></span>

- <span data-ttu-id="9c4ff-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9c4ff-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9c4ff-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="9c4ff-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9c4ff-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="9c4ff-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="9c4ff-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="9c4ff-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="9c4ff-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="9c4ff-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="9c4ff-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9c4ff-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="9c4ff-119">C\#</span><span class="sxs-lookup"><span data-stu-id="9c4ff-119">C\#</span></span>

<span data-ttu-id="9c4ff-120">Als u een lijst met alle abonnementen van een klant wilt weer geven, gebruikt u eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) met de klant-id om de klant te identificeren.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-120">To get a list of all of a customer's subscriptions, first use the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer identifier to identify the customer.</span></span> <span data-ttu-id="9c4ff-121">Gebruik vervolgens de eigenschap [**abonnementen**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) om een interface op te halen voor het verzamelen van abonnementen.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-121">Then use the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property to retrieve an interface to subscription collection operations.</span></span> <span data-ttu-id="9c4ff-122">Roep ten slotte de methoden [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) aan om de abonnementen verzameling van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-122">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.getasync) methods to retrieve the customer's subscriptions collection.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId;

var customerSubscriptions = partnerOperations.Customers.ById(customerId).Subscriptions.Get();
```

<span data-ttu-id="9c4ff-123">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="9c4ff-123">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="9c4ff-124">**Project**: Partner Center SDK-voor beelden **klasse**: GetSubscriptions.cs</span><span class="sxs-lookup"><span data-stu-id="9c4ff-124">**Project**: Partner Center SDK Samples **Class**: GetSubscriptions.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="9c4ff-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9c4ff-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9c4ff-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9c4ff-126">Request syntax</span></span>

| <span data-ttu-id="9c4ff-127">Methode</span><span class="sxs-lookup"><span data-stu-id="9c4ff-127">Method</span></span>  | <span data-ttu-id="9c4ff-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="9c4ff-128">Request URI</span></span>                                                                                          |
|---------|------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9c4ff-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="9c4ff-129">**GET**</span></span> | <span data-ttu-id="9c4ff-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/Subscriptions http/1.1</span><span class="sxs-lookup"><span data-stu-id="9c4ff-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="9c4ff-131">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="9c4ff-131">URI parameter</span></span>

<span data-ttu-id="9c4ff-132">Deze tabel bevat de vereiste query parameter om alle abonnementen op te halen.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-132">This table lists the required query parameter to get all the subscriptions.</span></span>

| <span data-ttu-id="9c4ff-133">Naam</span><span class="sxs-lookup"><span data-stu-id="9c4ff-133">Name</span></span>               | <span data-ttu-id="9c4ff-134">Type</span><span class="sxs-lookup"><span data-stu-id="9c4ff-134">Type</span></span>   | <span data-ttu-id="9c4ff-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="9c4ff-135">Required</span></span> | <span data-ttu-id="9c4ff-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9c4ff-136">Description</span></span>                                           |
|--------------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="9c4ff-137">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="9c4ff-137">customer-tenant-id</span></span> | <span data-ttu-id="9c4ff-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9c4ff-138">string</span></span> | <span data-ttu-id="9c4ff-139">Yes</span><span class="sxs-lookup"><span data-stu-id="9c4ff-139">Yes</span></span>      | <span data-ttu-id="9c4ff-140">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-140">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9c4ff-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9c4ff-141">Request headers</span></span>

<span data-ttu-id="9c4ff-142">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9c4ff-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9c4ff-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9c4ff-143">Request body</span></span>

<span data-ttu-id="9c4ff-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="9c4ff-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9c4ff-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: b2d13828-2ca5-41d4-94fb-9946214f4244
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="9c4ff-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9c4ff-146">REST response</span></span>

<span data-ttu-id="9c4ff-147">Als dit lukt, retourneert deze methode een verzameling [abonnements](subscription-resources.md) resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-147">If successful, this method returns a collection of [Subscription](subscription-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9c4ff-148">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="9c4ff-148">Response success and error codes</span></span>

<span data-ttu-id="9c4ff-149">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9c4ff-150">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9c4ff-151">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="9c4ff-151">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9c4ff-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9c4ff-152">Response example</span></span>

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
