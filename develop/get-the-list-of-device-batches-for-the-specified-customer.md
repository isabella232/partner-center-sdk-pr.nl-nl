---
title: Een lijst met de batches van een apparaat voor de opgegeven klant ophalen
description: Een verzameling apparaatbatchs ophalen voor de opgegeven klant.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 9d020bbfa1faef0be423d2fef2d8982465dfa21f
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548411"
---
# <a name="get-a-list-of-device-batches-for-the-specified-customer"></a><span data-ttu-id="9b95e-103">Een lijst met de batches van een apparaat voor de opgegeven klant ophalen</span><span class="sxs-lookup"><span data-stu-id="9b95e-103">Get a list of device batches for the specified customer</span></span>

<span data-ttu-id="9b95e-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="9b95e-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="9b95e-105">Een verzameling apparaatbatchs ophalen voor de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="9b95e-105">How to retrieve a collection of device batches for the specified customer.</span></span>

<span data-ttu-id="9b95e-106">Elke apparaatbatch bevat overzichtsstatusinformatie over apparaten die zijn ingeschreven in zero-touch-implementatie.</span><span class="sxs-lookup"><span data-stu-id="9b95e-106">Each device batch contains summary status information about devices that have been enrolled in zero-touch deployment.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9b95e-107">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9b95e-107">Prerequisites</span></span>

- <span data-ttu-id="9b95e-108">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9b95e-108">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9b95e-109">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="9b95e-109">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="9b95e-110">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9b95e-110">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="9b95e-111">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="9b95e-111">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="9b95e-112">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="9b95e-112">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="9b95e-113">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="9b95e-113">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="9b95e-114">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="9b95e-114">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="9b95e-115">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9b95e-115">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="9b95e-116">C\#</span><span class="sxs-lookup"><span data-stu-id="9b95e-116">C\#</span></span>

<span data-ttu-id="9b95e-117">Als u de verzameling apparaatbatchs voor de opgegeven klant wilt ophalen, roept u eerst de methode [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="9b95e-117">To get the collection of device batches for the specified customer, first call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span> <span data-ttu-id="9b95e-118">Haal vervolgens de waarde van de eigenschap [**DeviceBatches**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicebatches) op om een interface op te halen voor batchverzamelingsbewerkingen van apparaten.</span><span class="sxs-lookup"><span data-stu-id="9b95e-118">Then, retrieve the value of the [**DeviceBatches**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.devicebatches) property to get an interface to device batch collection operations.</span></span> <span data-ttu-id="9b95e-119">Roep ten slotte de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.getasync) om de verzameling op te halen.</span><span class="sxs-lookup"><span data-stu-id="9b95e-119">Finally, call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.idevicesbatchcollection.getasync) method to retrieve the collection.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string selectedCustomerId;

var devicesBatches =
    partnerOperations.Customers.ById(selectedCustomerId).DeviceBatches.Get();
```

<span data-ttu-id="9b95e-120">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="9b95e-120">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="9b95e-121">**Project:** Partnercentrum-SDK Klasse **Samples:** GetDevicesBatches.cs</span><span class="sxs-lookup"><span data-stu-id="9b95e-121">**Project**: Partner Center SDK Samples **Class**: GetDevicesBatches.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="9b95e-122">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9b95e-122">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9b95e-123">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="9b95e-123">Request syntax</span></span>

| <span data-ttu-id="9b95e-124">Methode</span><span class="sxs-lookup"><span data-stu-id="9b95e-124">Method</span></span>  | <span data-ttu-id="9b95e-125">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="9b95e-125">Request URI</span></span>                                                                                   |
|---------|-----------------------------------------------------------------------------------------------|
| <span data-ttu-id="9b95e-126">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="9b95e-126">**GET**</span></span> | <span data-ttu-id="9b95e-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="9b95e-127">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/deviceBatches HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="9b95e-128">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="9b95e-128">URI parameter</span></span>

<span data-ttu-id="9b95e-129">Gebruik de volgende padparameters bij het maken van de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="9b95e-129">Use the following path parameters when creating the request.</span></span>

| <span data-ttu-id="9b95e-130">Naam</span><span class="sxs-lookup"><span data-stu-id="9b95e-130">Name</span></span>        | <span data-ttu-id="9b95e-131">Type</span><span class="sxs-lookup"><span data-stu-id="9b95e-131">Type</span></span>   | <span data-ttu-id="9b95e-132">Vereist</span><span class="sxs-lookup"><span data-stu-id="9b95e-132">Required</span></span> | <span data-ttu-id="9b95e-133">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9b95e-133">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="9b95e-134">customer-id</span><span class="sxs-lookup"><span data-stu-id="9b95e-134">customer-id</span></span> | <span data-ttu-id="9b95e-135">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="9b95e-135">string</span></span> | <span data-ttu-id="9b95e-136">Ja</span><span class="sxs-lookup"><span data-stu-id="9b95e-136">Yes</span></span>      | <span data-ttu-id="9b95e-137">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="9b95e-137">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9b95e-138">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9b95e-138">Request headers</span></span>

<span data-ttu-id="9b95e-139">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="9b95e-139">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9b95e-140">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9b95e-140">Request body</span></span>

<span data-ttu-id="9b95e-141">Geen</span><span class="sxs-lookup"><span data-stu-id="9b95e-141">None</span></span>

### <a name="request-example"></a><span data-ttu-id="9b95e-142">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9b95e-142">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/deviceBatches HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="9b95e-143">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9b95e-143">REST response</span></span>

<span data-ttu-id="9b95e-144">Als dit lukt, bevat de antwoord-body de verzameling [DeviceBatch-resources.](device-deployment-resources.md#devicebatch)</span><span class="sxs-lookup"><span data-stu-id="9b95e-144">If successful, the response body contains the collection of [DeviceBatch](device-deployment-resources.md#devicebatch) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9b95e-145">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="9b95e-145">Response success and error codes</span></span>

<span data-ttu-id="9b95e-146">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="9b95e-146">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9b95e-147">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9b95e-147">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9b95e-148">Zie REST-foutcodes voor [Partner Center lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="9b95e-148">For the full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9b95e-149">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9b95e-149">Response example</span></span>

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
