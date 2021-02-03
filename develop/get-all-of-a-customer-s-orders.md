---
title: Alle bestellingen van een klant ophalen
description: Hiermee wordt een verzameling opgehaald van alle orders voor een opgegeven klant.
ms.date: 06/19/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 4d71cd138421704d94a55a9fe21e074d92638815
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767503"
---
# <a name="get-all-of-a-customers-orders"></a><span data-ttu-id="631ac-103">Alle bestellingen van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="631ac-103">Get all of a customer's orders</span></span>

<span data-ttu-id="631ac-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="631ac-104">**Applies to:**</span></span>

- <span data-ttu-id="631ac-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="631ac-105">Partner Center</span></span>
- <span data-ttu-id="631ac-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="631ac-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="631ac-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="631ac-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="631ac-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="631ac-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="631ac-109">Hiermee wordt een verzameling opgehaald van alle orders voor een opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="631ac-109">Gets a collection of all the orders for a specified customer.</span></span> <span data-ttu-id="631ac-110">Er is een vertraging van Maxi maal 15 minuten tussen de tijd dat een bestelling wordt verzonden en wanneer deze wordt weer gegeven in een verzameling van de orders van een klant.</span><span class="sxs-lookup"><span data-stu-id="631ac-110">There is a delay of up to 15 minutes between the time an order is submitted and when it will appear in a collection of a customer's orders.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="631ac-111">Vereisten</span><span class="sxs-lookup"><span data-stu-id="631ac-111">Prerequisites</span></span>

- <span data-ttu-id="631ac-112">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="631ac-112">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="631ac-113">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="631ac-113">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="631ac-114">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="631ac-114">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="631ac-115">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="631ac-115">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="631ac-116">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="631ac-116">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="631ac-117">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="631ac-117">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="631ac-118">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="631ac-118">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="631ac-119">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="631ac-119">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="631ac-120">C\#</span><span class="sxs-lookup"><span data-stu-id="631ac-120">C\#</span></span>

<span data-ttu-id="631ac-121">Voor het verkrijgen van een verzameling van alle orders van een klant:</span><span class="sxs-lookup"><span data-stu-id="631ac-121">To obtain a collection of all of a customer's orders:</span></span>

1. <span data-ttu-id="631ac-122">Gebruik uw verzameling [**IAggregatePartner. Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) en roep de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="631ac-122">Use your [**IAggregatePartner.Customers**](/dotnet/api/microsoft.store.partnercenter.ipartner.customers) collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span>

2. <span data-ttu-id="631ac-123">Roep de eigenschap [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) aan, gevolgd door de methoden [**Get ()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync) .</span><span class="sxs-lookup"><span data-stu-id="631ac-123">Call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var orders = partnerOperations.Customers.ById(selectedCustomerId).Orders.Get();
```

<span data-ttu-id="631ac-124">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="631ac-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="631ac-125">**Project**: PartnerSDK. FeatureSamples- **klasse**: GetOrders.cs</span><span class="sxs-lookup"><span data-stu-id="631ac-125">**Project**: PartnerSDK.FeatureSamples **Class**: GetOrders.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="631ac-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="631ac-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="631ac-127">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="631ac-127">Request syntax</span></span>

| <span data-ttu-id="631ac-128">Methode</span><span class="sxs-lookup"><span data-stu-id="631ac-128">Method</span></span>  | <span data-ttu-id="631ac-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="631ac-129">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="631ac-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="631ac-130">**GET**</span></span> | <span data-ttu-id="631ac-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/orders http/1.1</span><span class="sxs-lookup"><span data-stu-id="631ac-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders HTTP/1.1</span></span>  |

#### <a name="uri-parameter"></a><span data-ttu-id="631ac-132">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="631ac-132">URI parameter</span></span>

<span data-ttu-id="631ac-133">Gebruik de volgende query parameter om alle orders op te halen.</span><span class="sxs-lookup"><span data-stu-id="631ac-133">Use the following query parameter to get all orders.</span></span>

| <span data-ttu-id="631ac-134">Naam</span><span class="sxs-lookup"><span data-stu-id="631ac-134">Name</span></span>                   | <span data-ttu-id="631ac-135">Type</span><span class="sxs-lookup"><span data-stu-id="631ac-135">Type</span></span>     | <span data-ttu-id="631ac-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="631ac-136">Required</span></span> | <span data-ttu-id="631ac-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="631ac-137">Description</span></span>                                               |
|------------------------|----------|----------|-----------------------------------------------------------|
| <span data-ttu-id="631ac-138">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="631ac-138">customer-tenant-id</span></span>     | <span data-ttu-id="631ac-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="631ac-139">string</span></span>   | <span data-ttu-id="631ac-140">Yes</span><span class="sxs-lookup"><span data-stu-id="631ac-140">Yes</span></span>      | <span data-ttu-id="631ac-141">Een GUID-indelings teken reeks die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="631ac-141">A GUID formatted string corresponding to the customer.</span></span>    |

### <a name="request-headers"></a><span data-ttu-id="631ac-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="631ac-142">Request headers</span></span>

<span data-ttu-id="631ac-143">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="631ac-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="631ac-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="631ac-144">Request body</span></span>

<span data-ttu-id="631ac-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="631ac-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="631ac-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="631ac-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="631ac-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="631ac-147">REST response</span></span>

<span data-ttu-id="631ac-148">Als dit lukt, retourneert deze methode een verzameling [bestel](order-resources.md) resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="631ac-148">If successful, this method returns a collection of [Order](order-resources.md) resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="631ac-149">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="631ac-149">Response success and error codes</span></span>

<span data-ttu-id="631ac-150">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="631ac-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="631ac-151">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="631ac-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="631ac-152">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="631ac-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="631ac-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="631ac-153">Response example</span></span>

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
