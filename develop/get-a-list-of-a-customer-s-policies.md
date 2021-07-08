---
title: Een lijst met beleidsregels van een klant ophalen
description: Een verzameling van de opgegeven configuratiebeleidsregels van de klant ophalen.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: bf6ace0d2425e28d80c4f2310878c2d2a9e2a876
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874581"
---
# <a name="get-a-list-of-a-customers-policies"></a><span data-ttu-id="fdb55-103">Een lijst met beleidsregels van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="fdb55-103">Get a list of a customer's policies</span></span>

<span data-ttu-id="fdb55-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="fdb55-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="fdb55-105">In dit artikel wordt beschreven hoe u een verzameling van de opgegeven configuratiebeleidsregels van de klant ophaalt.</span><span class="sxs-lookup"><span data-stu-id="fdb55-105">This article describes how to retrieve a collection of the specified customer's configuration policies.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="fdb55-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="fdb55-106">Prerequisites</span></span>

- <span data-ttu-id="fdb55-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="fdb55-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="fdb55-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="fdb55-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="fdb55-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fdb55-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="fdb55-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="fdb55-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="fdb55-111">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="fdb55-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="fdb55-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="fdb55-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="fdb55-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="fdb55-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="fdb55-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="fdb55-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="fdb55-115">C\#</span><span class="sxs-lookup"><span data-stu-id="fdb55-115">C\#</span></span>

<span data-ttu-id="fdb55-116">Een lijst met alle beleidsregels van een klant op te halen:</span><span class="sxs-lookup"><span data-stu-id="fdb55-116">To get a list of all of a customer's policies:</span></span>

1. <span data-ttu-id="fdb55-117">Roep de [**methode IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="fdb55-117">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="fdb55-118">Haal de [**eigenschap ConfigurationPolicies op**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) om een interface op te halen voor bewerkingen voor het verzamelen van configuratiebeleid.</span><span class="sxs-lookup"><span data-stu-id="fdb55-118">Retrieve the [**ConfigurationPolicies**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) property to get an interface to configuration policy collection operations.</span></span>
3. <span data-ttu-id="fdb55-119">Roep de [**methode Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.get) of [**GetAsync aan**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.getasync) om de verzameling beleidsregels op te halen.</span><span class="sxs-lookup"><span data-stu-id="fdb55-119">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.getasync) method to retrieve the collection of policies.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;

var configPolicies = partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.Get();
```

<span data-ttu-id="fdb55-120">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="fdb55-120">For an example, see the following:</span></span>

- <span data-ttu-id="fdb55-121">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="fdb55-121">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="fdb55-122">Project: **Partnercentrum-SDK Voorbeelden**</span><span class="sxs-lookup"><span data-stu-id="fdb55-122">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="fdb55-123">Klasse: **GetAllConfigurationPolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="fdb55-123">Class: **GetAllConfigurationPolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="fdb55-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="fdb55-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="fdb55-125">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="fdb55-125">Request syntax</span></span>

| <span data-ttu-id="fdb55-126">Methode</span><span class="sxs-lookup"><span data-stu-id="fdb55-126">Method</span></span>  | <span data-ttu-id="fdb55-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="fdb55-127">Request URI</span></span>                                                                              |
|---------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="fdb55-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="fdb55-128">**GET**</span></span> | <span data-ttu-id="fdb55-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="fdb55-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="fdb55-130">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="fdb55-130">URI parameter</span></span>

<span data-ttu-id="fdb55-131">Gebruik de volgende padparameter bij het maken van de aanvraag:</span><span class="sxs-lookup"><span data-stu-id="fdb55-131">Use the following path parameter when creating the request:</span></span>

| <span data-ttu-id="fdb55-132">Naam</span><span class="sxs-lookup"><span data-stu-id="fdb55-132">Name</span></span>        | <span data-ttu-id="fdb55-133">Type</span><span class="sxs-lookup"><span data-stu-id="fdb55-133">Type</span></span>   | <span data-ttu-id="fdb55-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="fdb55-134">Required</span></span> | <span data-ttu-id="fdb55-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="fdb55-135">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="fdb55-136">customer-id</span><span class="sxs-lookup"><span data-stu-id="fdb55-136">customer-id</span></span> | <span data-ttu-id="fdb55-137">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="fdb55-137">string</span></span> | <span data-ttu-id="fdb55-138">Ja</span><span class="sxs-lookup"><span data-stu-id="fdb55-138">Yes</span></span>      | <span data-ttu-id="fdb55-139">Een tekenreeks in GUID-indeling die de klant identificeert.</span><span class="sxs-lookup"><span data-stu-id="fdb55-139">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="fdb55-140">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="fdb55-140">Request headers</span></span>

<span data-ttu-id="fdb55-141">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="fdb55-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="fdb55-142">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="fdb55-142">Request body</span></span>

<span data-ttu-id="fdb55-143">Geen</span><span class="sxs-lookup"><span data-stu-id="fdb55-143">None</span></span>

### <a name="request-example"></a><span data-ttu-id="fdb55-144">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="fdb55-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/47021739-3426-40bf-9601-61b4b6d7c793/policies HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: e88d014d-ab70-41de-90a0-f7fd1797267d
MS-CorrelationId: de894e18-f027-4ac0-8b5a-34f0c222af0c
Content-Length:0
X-Locale: en-US
Host: api.partnercenter.microsoft.com
```

## <a name="rest-response"></a><span data-ttu-id="fdb55-145">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="fdb55-145">REST response</span></span>

<span data-ttu-id="fdb55-146">Als dit lukt, bevat de antwoord-body de verzameling [ConfigurationPolicy-resources.](device-deployment-resources.md#configurationpolicy)</span><span class="sxs-lookup"><span data-stu-id="fdb55-146">If successful, the response body contains the collection of [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="fdb55-147">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="fdb55-147">Response success and error codes</span></span>

<span data-ttu-id="fdb55-148">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="fdb55-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="fdb55-149">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="fdb55-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="fdb55-150">Zie REST-foutcodes voor [Partner Center een volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="fdb55-150">For a full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="fdb55-151">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="fdb55-151">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1221
Content-Type: application/json; charset=utf-8
MS-CorrelationId: d5ff2573-3ef8-4553-aac4-4b73d97dce1b
MS-RequestId: 6eb7383d-eeb5-44d7-8570-e0ed12c0547a
MS-CV: YrLe3w6BbUSMt1fi.0
MS-ServerId: 030020344
Date: Tue, 25 Jul 2017 18:07:49 GMT

{
    "totalCount": 3,
    "items": [{
            "id": "8c7d25aa-2dbb-409c-a1f0-f55bd9108fa9",
            "name": "Windows 10 Enterprise E3",
            "category": "o_o_b_e",
            "description": "P462017 description",
            "devicesAssigned": 0,
            "policySettings": ["oobe_user_not_local_admin", "skip_express_settings"],
            "createdDate": "2017-04-27T11:30:34.1944704-07:00",
            "lastModifiedDate": "2017-04-27T11:30:34.1944704-07:00",
            "attributes": {
                "objectType": "ConfigurationPolicy"
            }
        }, {
            "id": "56edf752-ee77-4fd8-b7f5-df1f74a3a9ac",
            "name": "Test policy",
            "category": "o_o_b_e",
            "description": "Test policy creation from API 1",
            "devicesAssigned": 0,
            "policySettings": ["skip_express_settings"],
            "createdDate": "2017-07-25T11:03:03.8457088-07:00",
            "lastModifiedDate": "2017-07-25T11:04:00.8150016-07:00",
            "attributes": {
                "objectType": "ConfigurationPolicy"
            }
        }, {
            "id": "a96b5fd9-0f3a-419a-b55c-a8aecd6b1f00",
            "name": "Windows 10 Enterprise E5",
            "category": "o_o_b_e",
            "description": "test policy creation from API",
            "devicesAssigned": 0,
            "policySettings": ["oobe_user_not_local_admin", "skip_express_settings"],
            "createdDate": "2017-07-25T11:07:36.1501184-07:00",
            "lastModifiedDate": "2017-07-25T11:07:36.1501184-07:00",
            "attributes": {
                "objectType": "ConfigurationPolicy"
            }
        }
    ],
    "attributes": {
        "objectType": "Collection"
    }
}
```
