---
title: Alle serviceaanvragen voor een klant ophalen
description: Haalt alle serviceaanvragen van een klant op.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: ffcbbb9cf14b1b2a5b3becab541d3042c3cad508
ms.sourcegitcommit: d4b0c80d81f1d5bdf3c4c03344ad639646ae6ab9
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111760671"
---
# <a name="get-all-service-requests-for-a-customer"></a><span data-ttu-id="bd713-103">Alle serviceaanvragen voor een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="bd713-103">Get all service requests for a customer</span></span>

<span data-ttu-id="bd713-104">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="bd713-104">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="bd713-105">Haalt alle serviceaanvragen van een klant op.</span><span class="sxs-lookup"><span data-stu-id="bd713-105">Gets all of a customer's service requests.</span></span>

<span data-ttu-id="bd713-106">In het Partner Center dashboard kunt u deze bewerking uitvoeren door eerst [een klant te selecteren.](get-a-customer-by-name.md)</span><span class="sxs-lookup"><span data-stu-id="bd713-106">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="bd713-107">Selecteer vervolgens **Servicebeheer in** de linkerzijbalk.</span><span class="sxs-lookup"><span data-stu-id="bd713-107">Then, select **Service management** on the left sidebar.</span></span> <span data-ttu-id="bd713-108">De serviceaanvragen van de klant worden weergegeven onder **Ondersteuningstickets.**</span><span class="sxs-lookup"><span data-stu-id="bd713-108">The customer's service requests are displayed under **Support tickets**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bd713-109">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bd713-109">Prerequisites</span></span>

- <span data-ttu-id="bd713-110">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bd713-110">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bd713-111">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="bd713-111">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="bd713-112">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="bd713-112">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="bd713-113">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="bd713-113">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="bd713-114">Selecteer **CSP** in Partner Center menu, gevolgd door **Klanten.**</span><span class="sxs-lookup"><span data-stu-id="bd713-114">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="bd713-115">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="bd713-115">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="bd713-116">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="bd713-116">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="bd713-117">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="bd713-117">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="bd713-118">C\#</span><span class="sxs-lookup"><span data-stu-id="bd713-118">C\#</span></span>

<span data-ttu-id="bd713-119">Als u een lijst met alle serviceaanvragen van een klant wilt weergeven, gebruikt u de verzameling **IAggregatePartner.Customers** en roept u de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="bd713-119">To display a list of all of a customer's service requests, use your **IAggregatePartner.Customers** collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="bd713-120">Roep vervolgens de [**eigenschap ServiceRequests**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicerequests) aan, gevolgd door de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.get) of [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="bd713-120">Then call the [**ServiceRequests**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicerequests) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId as string;

ResourceCollection<ServiceRequest> serviceRequests = partnerOperations.Customers.ById(customerId).ServiceRequests.Get();
```

<span data-ttu-id="bd713-121">**Voorbeeld:** [consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="bd713-121">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="bd713-122">**Project:** PartnerCenterSDK.FeaturesSamples-klasse: CustomerManagedServices.cs </span><span class="sxs-lookup"><span data-stu-id="bd713-122">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="bd713-123">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="bd713-123">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bd713-124">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="bd713-124">Request syntax</span></span>

| <span data-ttu-id="bd713-125">Methode</span><span class="sxs-lookup"><span data-stu-id="bd713-125">Method</span></span>  | <span data-ttu-id="bd713-126">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="bd713-126">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bd713-127">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="bd713-127">**GET**</span></span> | <span data-ttu-id="bd713-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/servicerequests HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="bd713-128">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/servicerequests HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="bd713-129">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="bd713-129">URI parameter</span></span>

<span data-ttu-id="bd713-130">Gebruik de volgende queryparameter om alle serviceaanvragen voor de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="bd713-130">Use the following query parameter to get all service requests for the customer.</span></span>

| <span data-ttu-id="bd713-131">Naam</span><span class="sxs-lookup"><span data-stu-id="bd713-131">Name</span></span>                   | <span data-ttu-id="bd713-132">Type</span><span class="sxs-lookup"><span data-stu-id="bd713-132">Type</span></span>     | <span data-ttu-id="bd713-133">Vereist</span><span class="sxs-lookup"><span data-stu-id="bd713-133">Required</span></span> | <span data-ttu-id="bd713-134">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bd713-134">Description</span></span>                            |
|------------------------|----------|----------|----------------------------------------|
| <span data-ttu-id="bd713-135">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="bd713-135">**customer-tenant-id**</span></span> | <span data-ttu-id="bd713-136">**guid**</span><span class="sxs-lookup"><span data-stu-id="bd713-136">**guid**</span></span> | <span data-ttu-id="bd713-137">J</span><span class="sxs-lookup"><span data-stu-id="bd713-137">Y</span></span>        | <span data-ttu-id="bd713-138">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="bd713-138">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="bd713-139">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="bd713-139">Request headers</span></span>

<span data-ttu-id="bd713-140">Zie REST-headers Partner Center [meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="bd713-140">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="bd713-141">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="bd713-141">Request body</span></span>

<span data-ttu-id="bd713-142">Geen.</span><span class="sxs-lookup"><span data-stu-id="bd713-142">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="bd713-143">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bd713-143">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/servicerequests HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 53d5d48c-9693-46b6-8071-2eed07797d6c
MS-CorrelationId: 998e31a1-3f17-4471-a9ee-7678dd72e033
```

## <a name="rest-response"></a><span data-ttu-id="bd713-144">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="bd713-144">REST response</span></span>

<span data-ttu-id="bd713-145">Als dit lukt, retourneert deze methode een verzameling **serviceaanvraagresources** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="bd713-145">If successful, this method returns a collection of **Service Request** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bd713-146">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="bd713-146">Response success and error codes</span></span>

<span data-ttu-id="bd713-147">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of het is gelukt of mislukt en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="bd713-147">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bd713-148">Gebruik een hulpprogramma voor netwerk traceer om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="bd713-148">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bd713-149">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="bd713-149">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="bd713-150">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="bd713-150">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 742
Content-Type: application/json
MS-CorrelationId: 998e31a1-3f17-4471-a9ee-7678dd72e033
MS-RequestId: 53d5d48c-9693-46b6-8071-2eed07797d6c
Date: Tue, 24 Nov 2015 07:19:21 GMT

{
    "totalCount": 1,
    "items": [{
        "title": "Test",
        "severity": 0,
        "id": "615112491169010",
        "status": 1,
        "primaryContact": {
            "lastName": "LastName",
            "firstName": "FirstName"
        },
        "createdDate": "2015-11-24T01:07:00.863",
        "lastModifiedDate": "2015-11-24T01:17:10.61",
        "lastClosedDate": "0001-01-01T00:00:00",
        "attributes": {
            "objectType": "ServiceRequest"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
