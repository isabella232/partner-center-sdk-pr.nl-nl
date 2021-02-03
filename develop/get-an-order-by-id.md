---
title: Een bestelling ophalen op basis van id
description: Hiermee wordt een order resource opgehaald die overeenkomt met de klant-en Order-ID.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 0a39d7142e5bf97f9fb345416964d4ed6bb935ad
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767551"
---
# <a name="get-an-order-by-id"></a><span data-ttu-id="6d5ed-103">Een bestelling ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="6d5ed-103">Get an order by ID</span></span>

<span data-ttu-id="6d5ed-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="6d5ed-104">**Applies to:**</span></span>

- <span data-ttu-id="6d5ed-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="6d5ed-105">Partner Center</span></span>
- <span data-ttu-id="6d5ed-106">Partner centrum beheerd door 21Vianet</span><span class="sxs-lookup"><span data-stu-id="6d5ed-106">Partner Center operated by 21Vianet</span></span>
- <span data-ttu-id="6d5ed-107">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="6d5ed-107">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="6d5ed-108">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="6d5ed-108">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="6d5ed-109">Hiermee wordt een [order](order-resources.md) resource opgehaald die overeenkomt met de klant-en order-id.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-109">Gets an [Order](order-resources.md) resource that matches the customer and order ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6d5ed-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="6d5ed-110">Prerequisites</span></span>

- <span data-ttu-id="6d5ed-111">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="6d5ed-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="6d5ed-112">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-112">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="6d5ed-113">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6d5ed-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="6d5ed-114">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="6d5ed-115">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="6d5ed-116">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="6d5ed-117">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="6d5ed-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="6d5ed-118">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="6d5ed-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="6d5ed-119">Een order-ID.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-119">An order ID.</span></span>

## <a name="c"></a><span data-ttu-id="6d5ed-120">C\#</span><span class="sxs-lookup"><span data-stu-id="6d5ed-120">C\#</span></span>

<span data-ttu-id="6d5ed-121">De order van een klant ophalen op basis van de ID:</span><span class="sxs-lookup"><span data-stu-id="6d5ed-121">To get a customer's order by ID:</span></span>

1. <span data-ttu-id="6d5ed-122">Gebruik uw verzameling **IAggregatePartner. Customers** en roep de methode **ById ()** aan.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-122">Use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span>

2. <span data-ttu-id="6d5ed-123">Roep de eigenschap [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) aan, gevolgd door de methode [**ByID ()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) .</span><span class="sxs-lookup"><span data-stu-id="6d5ed-123">Call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property, followed by the [**ByID()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) method once more.</span></span>
3. <span data-ttu-id="6d5ed-124">Roep [**Get ()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.getasync)aan.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-124">Call [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.getasync).</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedOrderId;

var order = partnerOperations.Customers.ById(selectedCustomerId).Orders.ById(selectedOrderId).Get();
```

<span data-ttu-id="6d5ed-125">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="6d5ed-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="6d5ed-126">**Project**: PartnerSDK. FeatureSample- **klasse**: GetOrder.cs</span><span class="sxs-lookup"><span data-stu-id="6d5ed-126">**Project**: PartnerSDK.FeatureSample **Class**: GetOrder.cs</span></span>

## <a name="java"></a><span data-ttu-id="6d5ed-127">Java</span><span class="sxs-lookup"><span data-stu-id="6d5ed-127">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="6d5ed-128">De order van een klant ophalen op basis van de ID:</span><span class="sxs-lookup"><span data-stu-id="6d5ed-128">To get a customer's order by ID:</span></span>

1. <span data-ttu-id="6d5ed-129">Gebruik de functie **IAggregatePartner. getCustomers** en roep de functie **byId ()** aan.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-129">Use your **IAggregatePartner.getCustomers** function and call the **byId()** function.</span></span>

2. <span data-ttu-id="6d5ed-130">Roep de functie **getOrders** aan, gevolgd door de functie **byID ()** nog een keer.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-130">Call the **getOrders** function, followed by the **byID()** function once more.</span></span>
3. <span data-ttu-id="6d5ed-131">Roep de functie **Get () aan** .</span><span class="sxs-lookup"><span data-stu-id="6d5ed-131">Call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String selectedCustomerId;
// String selectedOrderId;

Order order = partnerOperations.getCustomers().byId(selectedCustomerId).getOrders().byId(selectedOrderId).get();
```

## <a name="powershell"></a><span data-ttu-id="6d5ed-132">PowerShell</span><span class="sxs-lookup"><span data-stu-id="6d5ed-132">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="6d5ed-133">Als u de order op ID van een klant wilt ophalen, voert u de opdracht [**Get-PartnerCustomerOrder**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerOrder.md) uit en geeft u de para meters **CustomerId** en **OrderID** op.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-133">To get a customer's order by ID, execute the [**Get-PartnerCustomerOrder**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerOrder.md) command, and specify the **CustomerId** and **OrderId** parameters.</span></span>

```powershell
# $selectedCustomerId
# $selectedOrderId

Get-PartnerCustomerOrder -CustomerId $selectedCustomerId -OrderId $selectedOrderId
```

## <a name="rest-request"></a><span data-ttu-id="6d5ed-134">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="6d5ed-134">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="6d5ed-135">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6d5ed-135">Request syntax</span></span>

| <span data-ttu-id="6d5ed-136">Methode</span><span class="sxs-lookup"><span data-stu-id="6d5ed-136">Method</span></span>  | <span data-ttu-id="6d5ed-137">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="6d5ed-137">Request URI</span></span>                                                                                                  |
|---------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="6d5ed-138">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="6d5ed-138">**GET**</span></span> | <span data-ttu-id="6d5ed-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/orders/{id-for-order} http/1.1</span><span class="sxs-lookup"><span data-stu-id="6d5ed-139">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{id-for-order} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="6d5ed-140">URI-para meters</span><span class="sxs-lookup"><span data-stu-id="6d5ed-140">URI parameters</span></span>

<span data-ttu-id="6d5ed-141">Deze tabel bevat de vereiste query parameters om een order by-ID op te halen.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-141">This table lists the required query parameters to get an order by ID.</span></span>

| <span data-ttu-id="6d5ed-142">Naam</span><span class="sxs-lookup"><span data-stu-id="6d5ed-142">Name</span></span>                   | <span data-ttu-id="6d5ed-143">Type</span><span class="sxs-lookup"><span data-stu-id="6d5ed-143">Type</span></span>     | <span data-ttu-id="6d5ed-144">Vereist</span><span class="sxs-lookup"><span data-stu-id="6d5ed-144">Required</span></span> | <span data-ttu-id="6d5ed-145">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="6d5ed-145">Description</span></span>                                            |
|------------------------|----------|----------|--------------------------------------------------------|
| <span data-ttu-id="6d5ed-146">klant-Tenant-id</span><span class="sxs-lookup"><span data-stu-id="6d5ed-146">customer-tenant-id</span></span>     | <span data-ttu-id="6d5ed-147">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6d5ed-147">string</span></span>   | <span data-ttu-id="6d5ed-148">Yes</span><span class="sxs-lookup"><span data-stu-id="6d5ed-148">Yes</span></span>      | <span data-ttu-id="6d5ed-149">Een GUID-indelings teken reeks die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-149">A GUID formatted string corresponding to the customer.</span></span> |
| <span data-ttu-id="6d5ed-150">id voor order</span><span class="sxs-lookup"><span data-stu-id="6d5ed-150">id-for-order</span></span>           | <span data-ttu-id="6d5ed-151">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="6d5ed-151">string</span></span>   | <span data-ttu-id="6d5ed-152">Yes</span><span class="sxs-lookup"><span data-stu-id="6d5ed-152">Yes</span></span>      | <span data-ttu-id="6d5ed-153">Een teken reeks die overeenkomt met de order-ID.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-153">A string corresponding to the order ID.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="6d5ed-154">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="6d5ed-154">Request headers</span></span>

<span data-ttu-id="6d5ed-155">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="6d5ed-155">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="6d5ed-156">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="6d5ed-156">Request body</span></span>

<span data-ttu-id="6d5ed-157">Geen.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-157">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="6d5ed-158">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="6d5ed-158">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/orders/<id-for-order> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="6d5ed-159">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="6d5ed-159">REST response</span></span>

<span data-ttu-id="6d5ed-160">Als dit lukt, retourneert deze methode een [order](order-resources.md) resource in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-160">If successful, this method returns an [Order](order-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="6d5ed-161">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="6d5ed-161">Response success and error codes</span></span>

<span data-ttu-id="6d5ed-162">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-162">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="6d5ed-163">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-163">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="6d5ed-164">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="6d5ed-164">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="6d5ed-165">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="6d5ed-165">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 823
Content-Type: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Date: Thu, 15 Mar 2018 22:05:30 GMT

{
    "id": "YxH1q4KScfvfkJQjgRI8QY1DznnUWZTH1",
    "referenceCustomerId": "b0d70a69-4c42-4b27-b17b-91a835d8686a",
    "billingCycle": "one_time",
    "currencyCode": "USD",
    "currencySymbol" : "$",
    "lineItems": [
    {
        "lineItemNumber": 0,
        "offerId": "DZH318Z0BQ4Z:002L:DZH318Z0CMNP",
        "friendlyName": "Reserved_VM_Instance_Standard_NC12_AU_East_1_Year",
        "quantity": 1,
        "links": {
            "sku": {
                "uri": "/products/DZH318Z0BQ4Z/skus/002L?country=US",
                "method": "GET",
                "headers": []
            }
        }
    }
    ],
    "creationDate": "2018-03-13T22:49:54.3396949Z",
    "status": "completed",
    "links": {
        "provisioningStatus": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/YxH1q4KScfvfkJQjgRI8QY1DznnUWZTH1/provisioningstatus",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/b0d70a69-4c42-4b27-b17b-91a835d8686a/orders/YxH1q4KScfvfkJQjgRI8QY1DznnUWZTH1",
            "method": "GET",
            "headers": []
        }
    },
    "attributes": {
        "objectType": "Order"
    }
}
```
