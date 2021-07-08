---
title: Een lijst met bestellingen op basis van het type klant en factureringscyclus ophalen
description: Hiermee haalt u een verzameling orderbronnen op voor het opgegeven type klant en factureringscyclus.
ms.date: 06/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: c52a556887dba065c4ccd1a82d6223624d0ad1f2
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874224"
---
# <a name="get-a-list-of-orders-by-customer-and-billing-cycle-type"></a><span data-ttu-id="6871b-103">Een lijst met bestellingen op basis van het type klant en factureringscyclus ophalen</span><span class="sxs-lookup"><span data-stu-id="6871b-103">Get a list of orders by customer and billing cycle type</span></span>

<span data-ttu-id="6871b-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6871b-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6871b-105">Haalt een verzameling orderbronnen op die overeenkomen met een bepaald type klant en factureringscyclus.</span><span class="sxs-lookup"><span data-stu-id="6871b-105">Gets a collection of Order resources that correspond to a given customer and billing cycle type.</span></span> <span data-ttu-id="6871b-106">Er is een vertraging van maximaal 15 minuten tussen het moment waarop een order wordt verzonden en het moment waarop deze wordt weergegeven in een verzameling orders van een klant.</span><span class="sxs-lookup"><span data-stu-id="6871b-106">There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a collection of a customer's orders.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6871b-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6871b-107">Prerequisites</span></span>

- <span data-ttu-id="6871b-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6871b-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6871b-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="6871b-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="6871b-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6871b-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6871b-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="6871b-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6871b-112">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="6871b-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6871b-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="6871b-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6871b-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="6871b-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6871b-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6871b-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="6871b-116">C\#</span><span class="sxs-lookup"><span data-stu-id="6871b-116">C\#</span></span>

<span data-ttu-id="6871b-117">Een verzameling orders van een klant ophalen:</span><span class="sxs-lookup"><span data-stu-id="6871b-117">To get a collection of a customer's orders:</span></span>

1. <span data-ttu-id="6871b-118">Gebruik de [**verzameling IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roep de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de geselecteerde klant-id.</span><span class="sxs-lookup"><span data-stu-id="6871b-118">Use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the selected customer ID.</span></span>

2. <span data-ttu-id="6871b-119">Roep de [**eigenschap Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) en de **methode ByBillingCycleType()** aan met uw opgegeven  [**BillingCycleType**](product-resources.md#billingcycletype).</span><span class="sxs-lookup"><span data-stu-id="6871b-119">Call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property and the **ByBillingCycleType()** method with your specified  [**BillingCycleType**](product-resources.md#billingcycletype).</span></span>
3. <span data-ttu-id="6871b-120">Roep de [**methode Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="6871b-120">Call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// BillingCycleType selectedBillingCycleType;

var orders = partnerOperations.Customers.ById(selectedCustomerId).Orders.ByBillingCycleType(selectedBillingCycleType).Get();
```

## <a name="rest-request"></a><span data-ttu-id="6871b-121">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="6871b-121">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6871b-122">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="6871b-122">Request syntax</span></span>

| <span data-ttu-id="6871b-123">Methode</span><span class="sxs-lookup"><span data-stu-id="6871b-123">Method</span></span>  | <span data-ttu-id="6871b-124">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="6871b-124">Request URI</span></span>                                                                                                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6871b-125">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="6871b-125">**GET**</span></span> | <span data-ttu-id="6871b-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders?billingType={billing-cycle-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6871b-126">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders?billingType={billing-cycle-type} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="6871b-127">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="6871b-127">URI parameters</span></span>

<span data-ttu-id="6871b-128">Deze tabel bevat de vereiste queryparameters voor het ophalen van een verzameling orders op klant-id en type factureringscyclus.</span><span class="sxs-lookup"><span data-stu-id="6871b-128">This table lists the required query parameters to get a collection of orders by customer ID and billing cycle type.</span></span>

| <span data-ttu-id="6871b-129">Naam</span><span class="sxs-lookup"><span data-stu-id="6871b-129">Name</span></span>                   | <span data-ttu-id="6871b-130">Type</span><span class="sxs-lookup"><span data-stu-id="6871b-130">Type</span></span>     | <span data-ttu-id="6871b-131">Vereist</span><span class="sxs-lookup"><span data-stu-id="6871b-131">Required</span></span> | <span data-ttu-id="6871b-132">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6871b-132">Description</span></span>                                               |
|------------------------|----------|----------|-----------------------------------------------------------|
| <span data-ttu-id="6871b-133">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="6871b-133">customer-tenant-id</span></span>     | <span data-ttu-id="6871b-134">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6871b-134">string</span></span>   | <span data-ttu-id="6871b-135">Ja</span><span class="sxs-lookup"><span data-stu-id="6871b-135">Yes</span></span>      | <span data-ttu-id="6871b-136">Een tekenreeks met GUID-indeling die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="6871b-136">A GUID formatted string corresponding to the customer.</span></span>    |
| <span data-ttu-id="6871b-137">factureringscyclus-type</span><span class="sxs-lookup"><span data-stu-id="6871b-137">billing-cycle-type</span></span>     | <span data-ttu-id="6871b-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6871b-138">string</span></span>   | <span data-ttu-id="6871b-139">No</span><span class="sxs-lookup"><span data-stu-id="6871b-139">No</span></span>       | <span data-ttu-id="6871b-140">Een tekenreeks die overeenkomt met het type factureringscyclus.</span><span class="sxs-lookup"><span data-stu-id="6871b-140">A string corresponding to the billing cycle type.</span></span>         |

### <a name="request-headers"></a><span data-ttu-id="6871b-141">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="6871b-141">Request headers</span></span>

<span data-ttu-id="6871b-142">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="6871b-142">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6871b-143">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="6871b-143">Request body</span></span>

<span data-ttu-id="6871b-144">Geen.</span><span class="sxs-lookup"><span data-stu-id="6871b-144">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6871b-145">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6871b-145">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders?billingType=onetime HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="6871b-146">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="6871b-146">REST response</span></span>

<span data-ttu-id="6871b-147">Als dit lukt, retourneert deze methode een verzameling [orderresources](order-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="6871b-147">If successful, this method returns a collection of [Order](order-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6871b-148">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="6871b-148">Response success and error codes</span></span>

<span data-ttu-id="6871b-149">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="6871b-149">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6871b-150">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="6871b-150">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6871b-151">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="6871b-151">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6871b-152">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="6871b-152">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 22463
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 97fa8b4f-6576-4cd9-dd19-ac7c97a023a7
MS-RequestId: 3c6a034c-82ee-4095-d50f-9b530a415f1f
MS-CV: nb4/b3Yl2keY0eYR.0
MS-ServerId: 202010607
Date: Thu, 15 Mar 2018 20:44:40 GMT

{
    "totalCount": 2,
    "items": [
        {
            "id": "9qg-ErcO-4MPbPqq_3MIQaS7bn8W6HfG1",
            "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
            "billingCycle": "one_time",
            "currencyCode": "USD",
            "lineItems": [
                {
                    "lineItemNumber": 0,
                    "offerId": "DZH318Z0BQ4B:000Z:DZH318Z0DSPL",
                    "friendlyName": "Reserved_VM_Instance_Standard_D1_AP_East_1_Year",
                    "quantity": 1,
                    "links": {
                        "sku": {
                            "uri": "/products/DZH318Z0BQ4B/skus/000Z?country=US",
                            "method": "GET",
                            "headers": []
                        }
                    }
                }
            ],
            "creationDate": "2018-03-15T02:17:15.6455674Z",
            "status": "pending",
            "links": {
                "provisioningStatus": {
                    "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/9qg-ErcO-4MPbPqq_3MIQaS7bn8W6HfG1/provisioningstatus",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/9qg-ErcO-4MPbPqq_3MIQaS7bn8W6HfG1",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "objectType": "Order"
            }
        },
        {
            "id": "s-BZlr_TeGksPNT61SsWRL-sqMaKbyVa1",
            "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
            "billingCycle": "one_time",
            "currencyCode": "USD",
            "lineItems": [
                {
                    "lineItemNumber": 0,
                    "offerId": "DZH318Z0BQ4Z:002P:DZH318Z0CL2D",
                    "friendlyName": "Reserved_VM_Instance_Standard_NC12_AU_East_3_Years",
                    "quantity": 1,
                    "links": {
                        "sku": {
                            "uri": "/products/DZH318Z0BQ4Z/skus/002P?country=US",
                            "method": "GET",
                            "headers": []
                        }
                    }
                }
            ],
            "creationDate": "2018-03-15T01:42:36.8440279Z",
            "status": "pending",
            "links": {
                "provisioningStatus": {
                    "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/s-BZlr_TeGksPNT61SsWRL-sqMaKbyVa1/provisioningstatus",
                    "method": "GET",
                    "headers": []
                },
                "self": {
                    "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/s-BZlr_TeGksPNT61SsWRL-sqMaKbyVa1",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": { "objectType": "Order" }
        }
    ],
    "links": {
        "self": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType":
        "Collection"
    }
}
```
