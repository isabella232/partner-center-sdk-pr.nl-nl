---
title: Een lijst met de batches van een apparaat voor de opgegeven klant ophalen
description: Een verzameling batches ophalen voor de opgegeven klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: ea5797bbaff4d4eafd1e63428556ab784bcb0ee2
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767531"
---
# <a name="get-a-list-of-device-batches-for-the-specified-customer"></a><span data-ttu-id="d268c-103">Een lijst met de batches van een apparaat voor de opgegeven klant ophalen</span><span class="sxs-lookup"><span data-stu-id="d268c-103">Get a list of device batches for the specified customer</span></span>

<span data-ttu-id="d268c-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="d268c-104">**Applies To**</span></span>

- <span data-ttu-id="d268c-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d268c-105">Partner Center</span></span>
- <span data-ttu-id="d268c-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="d268c-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="d268c-107">Een verzameling batches ophalen voor de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="d268c-107">How to retrieve a collection of device batches for the specified customer.</span></span>

<span data-ttu-id="d268c-108">Elke apparaat batch bevat samenvattings status informatie over apparaten die zijn Inge schreven bij een Zero-touch-implementatie.</span><span class="sxs-lookup"><span data-stu-id="d268c-108">Each device batch contains summary status information about devices that have been enrolled in zero-touch deployment.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d268c-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d268c-109">Prerequisites</span></span>

- <span data-ttu-id="d268c-110">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d268c-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d268c-111">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="d268c-111">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="d268c-112">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d268c-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d268c-113">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="d268c-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d268c-114">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="d268c-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d268c-115">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="d268c-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d268c-116">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="d268c-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d268c-117">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d268c-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="d268c-118">C\#</span><span class="sxs-lookup"><span data-stu-id="d268c-118">C\#</span></span>

<span data-ttu-id="d268c-119">Als u de verzameling batches wilt ophalen voor de opgegeven klant, roept u eerst de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="d268c-119">To get the collection of device batches for the specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="d268c-120">Haal vervolgens de waarde van de eigenschap [**DeviceBatches**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicebatches) op om een interface te verkrijgen voor het verzamelen van batch-bewerkingen voor het apparaat.</span><span class="sxs-lookup"><span data-stu-id="d268c-120">Then, retrieve the value of the [**DeviceBatches**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicebatches) property to get an interface to device batch collection operations.</span></span> <span data-ttu-id="d268c-121">Roep ten slotte de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.getasync) aan om de verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="d268c-121">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.getasync) method to retrieve the collection.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var devicesBatches =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.Get();
```

<span data-ttu-id="d268c-122">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d268c-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d268c-123">**Project**: Partner Center SDK-voor beelden **klasse**: GetDevicesBatches.cs</span><span class="sxs-lookup"><span data-stu-id="d268c-123">**Project**: Partner Center SDK Samples **Class**: GetDevicesBatches.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="d268c-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d268c-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d268c-125">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d268c-125">Request syntax</span></span>

| <span data-ttu-id="d268c-126">Methode</span><span class="sxs-lookup"><span data-stu-id="d268c-126">Method</span></span>  | <span data-ttu-id="d268c-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d268c-127">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="d268c-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="d268c-128">**GET**</span></span> | <span data-ttu-id="d268c-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/deviceBatches http/1.1</span><span class="sxs-lookup"><span data-stu-id="d268c-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="d268c-130">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="d268c-130">URI parameter</span></span>

<span data-ttu-id="d268c-131">Gebruik de volgende Path-para meters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="d268c-131">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="d268c-132">Naam</span><span class="sxs-lookup"><span data-stu-id="d268c-132">Name</span></span>        | <span data-ttu-id="d268c-133">Type</span><span class="sxs-lookup"><span data-stu-id="d268c-133">Type</span></span>   | <span data-ttu-id="d268c-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="d268c-134">Required</span></span> | <span data-ttu-id="d268c-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d268c-135">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="d268c-136">klant-id</span><span class="sxs-lookup"><span data-stu-id="d268c-136">customer-id</span></span> | <span data-ttu-id="d268c-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="d268c-137">string</span></span> | <span data-ttu-id="d268c-138">Yes</span><span class="sxs-lookup"><span data-stu-id="d268c-138">Yes</span></span>      | <span data-ttu-id="d268c-139">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="d268c-139">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d268c-140">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d268c-140">Request headers</span></span>

<span data-ttu-id="d268c-141">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d268c-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d268c-142">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="d268c-142">Request body</span></span>

<span data-ttu-id="d268c-143">Geen</span><span class="sxs-lookup"><span data-stu-id="d268c-143">None</span></span>

### <a name="request-example"></a><span data-ttu-id="d268c-144">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d268c-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="d268c-145">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d268c-145">REST response</span></span>

<span data-ttu-id="d268c-146">Als dit lukt, bevat de antwoord tekst de verzameling [DeviceBatch](device-deployment-resources.md#devicebatch) -resources.</span><span class="sxs-lookup"><span data-stu-id="d268c-146">If successful, the response body contains the collection of [DeviceBatch](device-deployment-resources.md#devicebatch) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d268c-147">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="d268c-147">Response success and error codes</span></span>

<span data-ttu-id="d268c-148">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="d268c-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d268c-149">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d268c-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d268c-150">Zie [rest-fout codes van het partner centrum](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="d268c-150">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d268c-151">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d268c-151">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 339
Content-Type: application/json; charset=utf-8
MS-CorrelationId: 4a5002a2-0c1b-4e57-b491-dbcf19c0e7b8
MS-RequestId: 7b3e2e00-b330-4480-9d84-59ace713427f
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 17:52:41 GMT

{
    "totalCount": 1,
    "items": [{
            "id": "Test batch",
            "status": "finished",
            "creationDate": "2017-07-25T01:51:00",
            "devicesCount": 5,
            "devicesLink": {
                "uri": "/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches/Test batch/devices",
                "method": "GET",
                "headers": []
            },
            "attributes": {
                "objectType": "DeviceBatch"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
