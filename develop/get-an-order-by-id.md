---
title: Een bestelling ophalen op basis van id
description: Haalt een Order-resource op die overeenkomt met de klant en de order-id.
ms.date: 09/17/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: cychua
ms.author: cychua
ms.openlocfilehash: 2cb2822935113fe1c5337b4ffc899fccff333d2f
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760178"
---
# <a name="get-an-order-by-id"></a><span data-ttu-id="59066-103">Een bestelling ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="59066-103">Get an order by ID</span></span>

<span data-ttu-id="59066-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="59066-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="59066-105">Haalt een [Order-resource](order-resources.md) op die overeenkomt met de klant en de order-id.</span><span class="sxs-lookup"><span data-stu-id="59066-105">Gets an [Order](order-resources.md) resource that matches the customer and order ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59066-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="59066-106">Prerequisites</span></span>

- <span data-ttu-id="59066-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="59066-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="59066-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="59066-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="59066-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="59066-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="59066-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="59066-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="59066-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="59066-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="59066-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="59066-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="59066-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="59066-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="59066-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="59066-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="59066-115">Een order-id.</span><span class="sxs-lookup"><span data-stu-id="59066-115">An order ID.</span></span>

## <a name="c"></a><span data-ttu-id="59066-116">C\#</span><span class="sxs-lookup"><span data-stu-id="59066-116">C\#</span></span>

<span data-ttu-id="59066-117">De order van een klant op id krijgen:</span><span class="sxs-lookup"><span data-stu-id="59066-117">To get a customer's order by ID:</span></span>

1. <span data-ttu-id="59066-118">Gebruik de **verzameling IAggregatePartner.Customers** en roep de **methode ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="59066-118">Use your **IAggregatePartner.Customers** collection and call the **ById()** method.</span></span>

2. <span data-ttu-id="59066-119">Roep de [**eigenschap Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) aan, gevolgd door de [**methode ByID().**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid)</span><span class="sxs-lookup"><span data-stu-id="59066-119">Call the [**Orders**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.orders) property, followed by the [**ByID()**](/dotnet/api/microsoft.store.partnercenter.orders.iordercollection.byid) method once more.</span></span>
3. <span data-ttu-id="59066-120">Roep [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.get) of [**GetAsync() aan.**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.getasync)</span><span class="sxs-lookup"><span data-stu-id="59066-120">Call [**Get()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.orders.iorder.getasync).</span></span>

```csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;
// string selectedOrderId;

var order = partnerOperations.Customers.ById(selectedCustomerId).Orders.ById(selectedOrderId).Get();
```

<span data-ttu-id="59066-121">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="59066-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="59066-122">**Project:** PartnerSDK.FeatureSample-klasse: GetOrder.cs </span><span class="sxs-lookup"><span data-stu-id="59066-122">**Project**: PartnerSDK.FeatureSample **Class**: GetOrder.cs</span></span>

## <a name="java"></a><span data-ttu-id="59066-123">Java</span><span class="sxs-lookup"><span data-stu-id="59066-123">Java</span></span>

[!INCLUDE [Partner Center Java SDK support details](../includes/java-sdk-support.md)]

<span data-ttu-id="59066-124">De order van een klant op id krijgen:</span><span class="sxs-lookup"><span data-stu-id="59066-124">To get a customer's order by ID:</span></span>

1. <span data-ttu-id="59066-125">Gebruik de **functie IAggregatePartner.getCustomers** en roep de **functie byId()** aan.</span><span class="sxs-lookup"><span data-stu-id="59066-125">Use your **IAggregatePartner.getCustomers** function and call the **byId()** function.</span></span>

2. <span data-ttu-id="59066-126">Roep de **functie getOrders** aan, gevolgd door de **functie byID().**</span><span class="sxs-lookup"><span data-stu-id="59066-126">Call the **getOrders** function, followed by the **byID()** function once more.</span></span>
3. <span data-ttu-id="59066-127">Roep de **functie get()** aan.</span><span class="sxs-lookup"><span data-stu-id="59066-127">Call the **get()** function.</span></span>

```java
// IAggregatePartner partnerOperations;
// String selectedCustomerId;
// String selectedOrderId;

Order order = partnerOperations.getCustomers().byId(selectedCustomerId).getOrders().byId(selectedOrderId).get();
```

## <a name="powershell"></a><span data-ttu-id="59066-128">PowerShell</span><span class="sxs-lookup"><span data-stu-id="59066-128">PowerShell</span></span>

[!INCLUDE [Partner Center PowerShell module support details](../includes/powershell-module-support.md)]

<span data-ttu-id="59066-129">Als u de order van een klant op id wilt krijgen, voert u de [**opdracht Get-PartnerCustomerOrder**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerOrder.md) uit en geeft u de parameters **CustomerId** en **OrderId** op.</span><span class="sxs-lookup"><span data-stu-id="59066-129">To get a customer's order by ID, execute the [**Get-PartnerCustomerOrder**](https://github.com/Microsoft/Partner-Center-PowerShell/blob/master/docs/help/Get-PartnerCustomerOrder.md) command, and specify the **CustomerId** and **OrderId** parameters.</span></span>

```powershell
# $selectedCustomerId
# $selectedOrderId

Get-PartnerCustomerOrder -CustomerId $selectedCustomerId -OrderId $selectedOrderId
```

## <a name="rest-request"></a><span data-ttu-id="59066-130">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="59066-130">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="59066-131">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="59066-131">Request syntax</span></span>

| <span data-ttu-id="59066-132">Methode</span><span class="sxs-lookup"><span data-stu-id="59066-132">Method</span></span>  | <span data-ttu-id="59066-133">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="59066-133">Request URI</span></span>                                                                                                  |
|---------|--------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="59066-134">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="59066-134">**GET**</span></span> | <span data-ttu-id="59066-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{id-for-order} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="59066-135">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/orders/{id-for-order} HTTP/1.1</span></span>  |

#### <a name="uri-parameters"></a><span data-ttu-id="59066-136">URI-parameters</span><span class="sxs-lookup"><span data-stu-id="59066-136">URI parameters</span></span>

<span data-ttu-id="59066-137">Deze tabel bevat de vereiste queryparameters om een order op id op te halen.</span><span class="sxs-lookup"><span data-stu-id="59066-137">This table lists the required query parameters to get an order by ID.</span></span>

| <span data-ttu-id="59066-138">Naam</span><span class="sxs-lookup"><span data-stu-id="59066-138">Name</span></span>                   | <span data-ttu-id="59066-139">Type</span><span class="sxs-lookup"><span data-stu-id="59066-139">Type</span></span>     | <span data-ttu-id="59066-140">Vereist</span><span class="sxs-lookup"><span data-stu-id="59066-140">Required</span></span> | <span data-ttu-id="59066-141">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="59066-141">Description</span></span>                                            |
|------------------------|----------|----------|--------------------------------------------------------|
| <span data-ttu-id="59066-142">customer-tenant-id</span><span class="sxs-lookup"><span data-stu-id="59066-142">customer-tenant-id</span></span>     | <span data-ttu-id="59066-143">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="59066-143">string</span></span>   | <span data-ttu-id="59066-144">Ja</span><span class="sxs-lookup"><span data-stu-id="59066-144">Yes</span></span>      | <span data-ttu-id="59066-145">Een tekenreeks met GUID-indeling die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="59066-145">A GUID formatted string corresponding to the customer.</span></span> |
| <span data-ttu-id="59066-146">id-for-order</span><span class="sxs-lookup"><span data-stu-id="59066-146">id-for-order</span></span>           | <span data-ttu-id="59066-147">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="59066-147">string</span></span>   | <span data-ttu-id="59066-148">Ja</span><span class="sxs-lookup"><span data-stu-id="59066-148">Yes</span></span>      | <span data-ttu-id="59066-149">Een tekenreeks die overeenkomt met de order-id.</span><span class="sxs-lookup"><span data-stu-id="59066-149">A string corresponding to the order ID.</span></span>                |

### <a name="request-headers"></a><span data-ttu-id="59066-150">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="59066-150">Request headers</span></span>

<span data-ttu-id="59066-151">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="59066-151">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="59066-152">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="59066-152">Request body</span></span>

<span data-ttu-id="59066-153">Geen.</span><span class="sxs-lookup"><span data-stu-id="59066-153">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="59066-154">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="59066-154">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/orders/<id-for-order> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 0e5fc923-8e3c-4560-9100-ce7283c3e081
MS-CorrelationId: 8a53b025-d5be-4d98-ab20-229d1813de76
Connection: Keep-Alive
```

## <a name="rest-response"></a><span data-ttu-id="59066-155">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="59066-155">REST response</span></span>

<span data-ttu-id="59066-156">Als dit lukt, retourneert deze methode een [Order-resource](order-resources.md) in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="59066-156">If successful, this method returns an [Order](order-resources.md) resource in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="59066-157">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="59066-157">Response success and error codes</span></span>

<span data-ttu-id="59066-158">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="59066-158">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="59066-159">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="59066-159">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="59066-160">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="59066-160">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="59066-161">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="59066-161">Response example</span></span>

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
