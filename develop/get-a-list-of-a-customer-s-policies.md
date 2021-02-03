---
title: Een lijst met beleidsregels van een klant ophalen
description: Een verzameling van het configuratie beleid van de opgegeven klant ophalen.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: dineshvu
ms.author: dineshvu
ms.openlocfilehash: 16886b1adca393ed2967f2a4fe74a379bef1c1c7
ms.sourcegitcommit: 58801b7a09c19ce57617ec4181a008a673b725f0
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 09/22/2020
ms.locfileid: "97767374"
---
# <a name="get-a-list-of-a-customers-policies"></a><span data-ttu-id="4a07d-103">Een lijst met beleidsregels van een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="4a07d-103">Get a list of a customer's policies</span></span>

<span data-ttu-id="4a07d-104">**Van toepassing op:**</span><span class="sxs-lookup"><span data-stu-id="4a07d-104">**Applies to:**</span></span>

- <span data-ttu-id="4a07d-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="4a07d-105">Partner Center</span></span>
- <span data-ttu-id="4a07d-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="4a07d-106">Partner Center for Microsoft Cloud Germany</span></span>

<span data-ttu-id="4a07d-107">In dit artikel wordt beschreven hoe u een verzameling van het configuratie beleid van de opgegeven klant ophaalt.</span><span class="sxs-lookup"><span data-stu-id="4a07d-107">This article describes how to retrieve a collection of the specified customer's configuration policies.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="4a07d-108">Vereisten</span><span class="sxs-lookup"><span data-stu-id="4a07d-108">Prerequisites</span></span>

- <span data-ttu-id="4a07d-109">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="4a07d-109">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="4a07d-110">Dit scenario ondersteunt verificatie met zowel zelfstandige app als app + gebruikers referenties.</span><span class="sxs-lookup"><span data-stu-id="4a07d-110">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="4a07d-111">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4a07d-111">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="4a07d-112">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="4a07d-112">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="4a07d-113">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="4a07d-113">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="4a07d-114">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="4a07d-114">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="4a07d-115">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="4a07d-115">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="4a07d-116">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="4a07d-116">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="4a07d-117">C\#</span><span class="sxs-lookup"><span data-stu-id="4a07d-117">C\#</span></span>

<span data-ttu-id="4a07d-118">Een lijst met alle beleids regels van een klant weer geven:</span><span class="sxs-lookup"><span data-stu-id="4a07d-118">To get a list of all of a customer's policies:</span></span>

1. <span data-ttu-id="4a07d-119">Roep de methode [**IAggregatePartner. Customs. ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan met de klant-id om een interface op te halen voor bewerkingen op de opgegeven klant.</span><span class="sxs-lookup"><span data-stu-id="4a07d-119">Call the [**IAggregatePartner.Customers.ById**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method with the customer ID to retrieve an interface to operations on the specified customer.</span></span>

2. <span data-ttu-id="4a07d-120">Haal de eigenschap [**ConfigurationPolicies**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) op om een interface voor het verzamelen van configuratie beleidsregels op te halen.</span><span class="sxs-lookup"><span data-stu-id="4a07d-120">Retrieve the [**ConfigurationPolicies**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.configurationpolicies) property to get an interface to configuration policy collection operations.</span></span>
3. <span data-ttu-id="4a07d-121">Roep de methode [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.get) of [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.getasync) aan om de verzameling beleids regels op te halen.</span><span class="sxs-lookup"><span data-stu-id="4a07d-121">Call the [**Get**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.get) or [**GetAsync**](/dotnet/api/microsoft.store.partnercenter.devicesdeployment.iconfigurationpolicycollection.getasync) method to retrieve the collection of policies.</span></span>

``` csharp
IAggregatePartner partnerOperations;
string selectedCustomerId;

var configPolicies = partnerOperations.Customers.ById(selectedCustomerId).ConfigurationPolicies.Get();
```

<span data-ttu-id="4a07d-122">Voor een voor beeld ziet u het volgende:</span><span class="sxs-lookup"><span data-stu-id="4a07d-122">For an example, see the following:</span></span>

- <span data-ttu-id="4a07d-123">Voor beeld: [console test-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="4a07d-123">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="4a07d-124">Project: **Partner Center SDK** -voor beelden</span><span class="sxs-lookup"><span data-stu-id="4a07d-124">Project: **Partner Center SDK Samples**</span></span>
- <span data-ttu-id="4a07d-125">Klasse: **GetAllConfigurationPolicies.cs**</span><span class="sxs-lookup"><span data-stu-id="4a07d-125">Class: **GetAllConfigurationPolicies.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="4a07d-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="4a07d-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="4a07d-127">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4a07d-127">Request syntax</span></span>

| <span data-ttu-id="4a07d-128">Methode</span><span class="sxs-lookup"><span data-stu-id="4a07d-128">Method</span></span>  | <span data-ttu-id="4a07d-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="4a07d-129">Request URI</span></span>                                                                              |
|---------|------------------------------------------------------------------------------------------|
| <span data-ttu-id="4a07d-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="4a07d-130">**GET**</span></span> | <span data-ttu-id="4a07d-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-ID}/policies http/1.1</span><span class="sxs-lookup"><span data-stu-id="4a07d-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-id}/policies HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="4a07d-132">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="4a07d-132">URI parameter</span></span>

<span data-ttu-id="4a07d-133">Gebruik de volgende para meter Path bij het maken van de aanvraag:</span><span class="sxs-lookup"><span data-stu-id="4a07d-133">Use the following path parameter when creating the request:</span></span>

| <span data-ttu-id="4a07d-134">Naam</span><span class="sxs-lookup"><span data-stu-id="4a07d-134">Name</span></span>        | <span data-ttu-id="4a07d-135">Type</span><span class="sxs-lookup"><span data-stu-id="4a07d-135">Type</span></span>   | <span data-ttu-id="4a07d-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="4a07d-136">Required</span></span> | <span data-ttu-id="4a07d-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="4a07d-137">Description</span></span>                                           |
|-------------|--------|----------|-------------------------------------------------------|
| <span data-ttu-id="4a07d-138">klant-id</span><span class="sxs-lookup"><span data-stu-id="4a07d-138">customer-id</span></span> | <span data-ttu-id="4a07d-139">tekenreeks</span><span class="sxs-lookup"><span data-stu-id="4a07d-139">string</span></span> | <span data-ttu-id="4a07d-140">Yes</span><span class="sxs-lookup"><span data-stu-id="4a07d-140">Yes</span></span>      | <span data-ttu-id="4a07d-141">Een teken reeks met een GUID-indeling waarmee de klant wordt geïdentificeerd.</span><span class="sxs-lookup"><span data-stu-id="4a07d-141">A GUID-formatted string that identifies the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="4a07d-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="4a07d-142">Request headers</span></span>

<span data-ttu-id="4a07d-143">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="4a07d-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="4a07d-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="4a07d-144">Request body</span></span>

<span data-ttu-id="4a07d-145">Geen</span><span class="sxs-lookup"><span data-stu-id="4a07d-145">None</span></span>

### <a name="request-example"></a><span data-ttu-id="4a07d-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="4a07d-146">Request example</span></span>

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

## <a name="rest-response"></a><span data-ttu-id="4a07d-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="4a07d-147">REST response</span></span>

<span data-ttu-id="4a07d-148">Als dit lukt, bevat de antwoord tekst de verzameling [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) -resources.</span><span class="sxs-lookup"><span data-stu-id="4a07d-148">If successful, the response body contains the collection of [ConfigurationPolicy](device-deployment-resources.md#configurationpolicy) resources.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="4a07d-149">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="4a07d-149">Response success and error codes</span></span>

<span data-ttu-id="4a07d-150">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="4a07d-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="4a07d-151">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="4a07d-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="4a07d-152">Zie voor een volledige lijst de [rest-fout codes van het partner centrum](error-codes.md).</span><span class="sxs-lookup"><span data-stu-id="4a07d-152">For a full list, see [Partner Center REST error codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="4a07d-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="4a07d-153">Response example</span></span>

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
