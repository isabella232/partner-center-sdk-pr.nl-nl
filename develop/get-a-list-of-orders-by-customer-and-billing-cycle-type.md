---
title: Een lijst met bestellingen op basis van het type klant en factureringscyclus ophalen
description: Hiermee wordt een verzameling order resources opgehaald voor het opgegeven type klant en facturerings cyclus.
ms.date: 06/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: rbars
ms.author: rbars
ms.openlocfilehash: 43fe08b0791851f915e2b39a25394db5ffd022ca
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767440"
---
# <a name="get-a-list-of-orders-by-customer-and-billing-cycle-type"></a><span data-ttu-id="6c9fc-103">Een lijst met bestellingen op basis van het type klant en factureringscyclus ophalen</span><span class="sxs-lookup"><span data-stu-id="6c9fc-103">Get a list of orders by customer and billing cycle type</span></span>

<span data-ttu-id="6c9fc-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="6c9fc-104">**Applies to:**</span></span>

- <span data-ttu-id="6c9fc-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="6c9fc-105">Partner Center</span></span>
- <span data-ttu-id="6c9fc-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="6c9fc-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="6c9fc-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="6c9fc-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="6c9fc-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6c9fc-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6c9fc-109">Hiermee wordt een verzameling order resources opgehaald die overeenkomen met een bepaald type klant en facturerings cyclus.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-109">Gets a collection of Order resources that correspond to a given customer and billing cycle type.</span></span> <span data-ttu-id="6c9fc-110">Er is een vertraging van Maxi maal 15 minuten tussen de tijd dat een bestelling wordt verzonden en wanneer deze wordt weer gegeven in een verzameling van de orders van een klant.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-110">There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a collection of a customer's orders.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6c9fc-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6c9fc-111">Prerequisites</span></span>

- <span data-ttu-id="6c9fc-112">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6c9fc-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6c9fc-113">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-113">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="6c9fc-114">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6c9fc-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6c9fc-115">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6c9fc-116">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6c9fc-117">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6c9fc-118">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="6c9fc-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6c9fc-119">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6c9fc-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="6c9fc-120">C\#</span><span class="sxs-lookup"><span data-stu-id="6c9fc-120">C\#</span></span>

<span data-ttu-id="6c9fc-121">Een verzameling van de orders van een klant ophalen:</span><span class="sxs-lookup"><span data-stu-id="6c9fc-121">To get a collection of a customer's orders:</span></span>

1. <span data-ttu-id="6c9fc-122">Gebruik uw verzameling [**IAggregatePartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roep de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de geselecteerde klant-id.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-122">Use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the selected customer ID.</span></span>

2. <span data-ttu-id="6c9fc-123">Roep de eigenschap [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) en de methode **ByBillingCycleType ()** aan met de opgegeven  [**BillingCycleType**](product-resources.md#billingcycletype).</span><span class="sxs-lookup"><span data-stu-id="6c9fc-123">Call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property and the **ByBillingCycleType()** method with your specified  [**BillingCycleType**](product-resources.md#billingcycletype).</span></span>
3. <span data-ttu-id="6c9fc-124">Roep de methode [**Get ()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync) aan.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-124">Call the [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync) method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// BillingCycleType selectedBillingCycleType;

var orders = partnerOperations.Customers.ById(selectedCustomerId).Orders.ByBillingCycleType(selectedBillingCycleType).Get();
```

## <a name="rest-request"></a><span data-ttu-id="6c9fc-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="6c9fc-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6c9fc-126">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6c9fc-126">Request syntax</span></span>

| <span data-ttu-id="6c9fc-127">Methode</span><span class="sxs-lookup"><span data-stu-id="6c9fc-127">Method</span></span>  | <span data-ttu-id="6c9fc-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="6c9fc-128">Request URI</span></span>                                                                                                                    |
|---------|--------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6c9fc-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="6c9fc-129">**GET**</span></span> | <span data-ttu-id="6c9fc-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/orders? billingType = {Bill-Cycle-type} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="6c9fc-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders?billingType={billing-cycle-type} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="6c9fc-131">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="6c9fc-131">URI parameters</span></span>

<span data-ttu-id="6c9fc-132">Deze tabel bevat de vereiste query parameters voor het ophalen van een verzameling orders per klant-ID en type facturerings cyclus.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-132">This table lists the required query parameters to get a collection of orders by customer ID and billing cycle type.</span></span>

| <span data-ttu-id="6c9fc-133">Naam</span><span class="sxs-lookup"><span data-stu-id="6c9fc-133">Name</span></span>                   | <span data-ttu-id="6c9fc-134">Type</span><span class="sxs-lookup"><span data-stu-id="6c9fc-134">Type</span></span>     | <span data-ttu-id="6c9fc-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="6c9fc-135">Required</span></span> | <span data-ttu-id="6c9fc-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6c9fc-136">Description</span></span>                                               |
|------------------------|----------|----------|-----------------------------------------------------------|
| <span data-ttu-id="6c9fc-137">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="6c9fc-137">customer-tenant-id</span></span>     | <span data-ttu-id="6c9fc-138">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6c9fc-138">string</span></span>   | <span data-ttu-id="6c9fc-139">Yes</span><span class="sxs-lookup"><span data-stu-id="6c9fc-139">Yes</span></span>      | <span data-ttu-id="6c9fc-140">Een GUID-indelings teken reeks die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-140">A GUID formatted string corresponding to the customer.</span></span>    |
| <span data-ttu-id="6c9fc-141">facturering-cyclus-type</span><span class="sxs-lookup"><span data-stu-id="6c9fc-141">billing-cycle-type</span></span>     | <span data-ttu-id="6c9fc-142">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6c9fc-142">string</span></span>   | <span data-ttu-id="6c9fc-143">No</span><span class="sxs-lookup"><span data-stu-id="6c9fc-143">No</span></span>       | <span data-ttu-id="6c9fc-144">Een teken reeks die overeenkomt met het type facturerings cyclus.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-144">A string corresponding to the billing cycle type.</span></span>         |

### <a name="request-headers"></a><span data-ttu-id="6c9fc-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="6c9fc-145">Request headers</span></span>

<span data-ttu-id="6c9fc-146">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6c9fc-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6c9fc-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="6c9fc-147">Request body</span></span>

<span data-ttu-id="6c9fc-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6c9fc-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6c9fc-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders?billingType=onetime HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="6c9fc-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="6c9fc-150">REST response</span></span>

<span data-ttu-id="6c9fc-151">Als dit lukt, retourneert deze methode een verzameling [bestel](order-resources.md) resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-151">If successful, this method returns a collection of [Order](order-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6c9fc-152">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="6c9fc-152">Response success and error codes</span></span>

<span data-ttu-id="6c9fc-153">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6c9fc-154">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6c9fc-155">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="6c9fc-155">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6c9fc-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="6c9fc-156">Response example</span></span>

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
