---
title: Alle bestellingen van een klant ophalen
description: Hiermee haalt u een verzameling van alle orders voor een opgegeven klant op.
ms.date: 06/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: e8f23e90cbb5afb45e519e2c58fd0d3b9ea2de6a
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760297"
---
# <a name="get-all-of-a-customers-orders"></a><span data-ttu-id="ff1f9-103">Alle bestellingen van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="ff1f9-103">Get all of a customer's orders</span></span>

<span data-ttu-id="ff1f9-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="ff1f9-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="ff1f9-105">Hiermee haalt u een verzameling van alle orders voor een opgegeven klant op.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-105">Gets a collection of all the orders for a specified customer.</span></span> <span data-ttu-id="ff1f9-106">Er is een vertraging van maximaal 15 minuten tussen het moment waarop een order wordt verzonden en het moment waarop deze wordt weergegeven in een verzameling orders van een klant.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-106">There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a collection of a customer's orders.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ff1f9-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="ff1f9-107">Prerequisites</span></span>

- <span data-ttu-id="ff1f9-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="ff1f9-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="ff1f9-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="ff1f9-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ff1f9-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="ff1f9-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="ff1f9-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="ff1f9-112">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="ff1f9-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="ff1f9-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="ff1f9-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="ff1f9-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="ff1f9-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="ff1f9-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="ff1f9-116">C\#</span><span class="sxs-lookup"><span data-stu-id="ff1f9-116">C\#</span></span>

<span data-ttu-id="ff1f9-117">Een verzameling van alle orders van een klant verkrijgen:</span><span class="sxs-lookup"><span data-stu-id="ff1f9-117">To obtain a collection of all of a customer's orders:</span></span>

1. <span data-ttu-id="ff1f9-118">Gebruik de [**verzameling IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roep de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-118">Use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span>

2. <span data-ttu-id="ff1f9-119">Roep de [**eigenschap Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) aan, gevolgd door de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) of [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="ff1f9-119">Call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var orders = partnerOperations.Customers.ById(selectedCustomerId).Orders.Get();
```

<span data-ttu-id="ff1f9-120">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="ff1f9-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="ff1f9-121">**Project:** Klasse PartnerSDK.FeatureSamples: GetOrders.cs </span><span class="sxs-lookup"><span data-stu-id="ff1f9-121">**Project**: PartnerSDK.FeatureSamples **Class**: GetOrders.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="ff1f9-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="ff1f9-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="ff1f9-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="ff1f9-123">Request syntax</span></span>

| <span data-ttu-id="ff1f9-124">Methode</span><span class="sxs-lookup"><span data-stu-id="ff1f9-124">Method</span></span>  | <span data-ttu-id="ff1f9-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="ff1f9-125">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="ff1f9-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="ff1f9-126">**GET**</span></span> | <span data-ttu-id="ff1f9-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="ff1f9-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders HTTP/1.1</span></span>  |

#### <a name="uri-parameter"></a><span data-ttu-id="ff1f9-128">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="ff1f9-128">URI parameter</span></span>

<span data-ttu-id="ff1f9-129">Gebruik de volgende queryparameter om alle orders op te halen.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-129">Use the following query parameter to get all orders.</span></span>

| <span data-ttu-id="ff1f9-130">Naam</span><span class="sxs-lookup"><span data-stu-id="ff1f9-130">Name</span></span>                   | <span data-ttu-id="ff1f9-131">Type</span><span class="sxs-lookup"><span data-stu-id="ff1f9-131">Type</span></span>     | <span data-ttu-id="ff1f9-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="ff1f9-132">Required</span></span> | <span data-ttu-id="ff1f9-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="ff1f9-133">Description</span></span>                                               |
|------------------------|----------|----------|-----------------------------------------------------------|
| <span data-ttu-id="ff1f9-134">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="ff1f9-134">customer-tenant-id</span></span>     | <span data-ttu-id="ff1f9-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="ff1f9-135">string</span></span>   | <span data-ttu-id="ff1f9-136">Ja</span><span class="sxs-lookup"><span data-stu-id="ff1f9-136">Yes</span></span>      | <span data-ttu-id="ff1f9-137">Een tekenreeks met GUID-indeling die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-137">A GUID formatted string corresponding to the customer.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="ff1f9-138">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="ff1f9-138">Request headers</span></span>

<span data-ttu-id="ff1f9-139">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="ff1f9-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="ff1f9-140">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="ff1f9-140">Request body</span></span>

<span data-ttu-id="ff1f9-141">Geen.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-141">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="ff1f9-142">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="ff1f9-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="ff1f9-143">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="ff1f9-143">REST response</span></span>

<span data-ttu-id="ff1f9-144">Als dit lukt, retourneert deze methode een verzameling [orderresources](order-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-144">If successful, this method returns a collection of [Order](order-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="ff1f9-145">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="ff1f9-145">Response success and error codes</span></span>

<span data-ttu-id="ff1f9-146">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="ff1f9-147">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="ff1f9-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="ff1f9-148">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="ff1f9-148">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="ff1f9-149">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="ff1f9-149">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 22463
Content-Type: application/json; charset=utf-8
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
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
            "id": "eeba9d00-7b46-443a-917e-22887a8fc993",
            "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
            "billingCycle": "monthly",
            "currencyCode": "USD",
            "lineItems": [
                {
                    "lineItemNumber": 0,
                    "offerId": "E59159FC-6F67-4599-B3CB-17FF4020F643",
                    "subscriptionId": "DB8C695B-1C3C-4C55-B697-771503DD46BF",
                    "friendlyName": "Azure Active Directory Premium P2",
                    "quantity": 1,
                    "links": {
                        "subscription": {
                            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/subscriptions/DB8C695B-1C3C-4C55-B697-771503DD46BF",
                            "method": "GET",
                            "headers": []
                        },
                        "sku": {
                            "uri": "/products/84A661C4-E949-4BD2-A560-ED7766FCAF2B/skus/E59159FC-6F67-4599-B3CB-17FF4020F643",
                            "method": "GET",
                            "headers": []
                        },
                        "provisioningStatus": {
                            "uri": "/subscriptions/DB8C695B-1C3C-4C55-B697-771503DD46BF/provisioningstatus",
                            "method": "GET",
                            "headers": []
                        }
                    }
            ],
            "creationDate": "2018-03-06T17:37:05.253-08:00",
            "status": "completed",
            "links": {
                "self": {
                    "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/eeba9d00-7b46-443a-917e-22887a8fc993",
                    "method": "GET",
                    "headers": []
                }
            },
            "attributes": {
                "etag": "eyJpZCI6ImVlYmE5ZDAwLTdiNDYtNDQzYS05MTdlLTIyODg3YThmYzk5MyIsInZlcnNpb24iOjF9",
                "objectType": "Order"
            }
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
         "objectType": "Collection"
    }
}
```
