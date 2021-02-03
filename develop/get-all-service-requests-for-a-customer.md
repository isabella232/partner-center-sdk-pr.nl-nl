---
title: Alle serviceaanvragen voor een klant ophalen
description: Hiermee worden alle service aanvragen van een klant opgehaald.
ms.date: 12/15/2017
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: 6f473c7a7d43b1a3929d983fb23dae92fdafbc0f
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767560"
---
# <a name="get-all-service-requests-for-a-customer"></a><span data-ttu-id="d1045-103">Alle serviceaanvragen voor een klant ophalen</span><span class="sxs-lookup"><span data-stu-id="d1045-103">Get all service requests for a customer</span></span>

<span data-ttu-id="d1045-104">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="d1045-104">**Applies To**</span></span>

- <span data-ttu-id="d1045-105">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="d1045-105">Partner Center</span></span>
- <span data-ttu-id="d1045-106">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="d1045-106">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="d1045-107">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="d1045-107">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="d1045-108">Hiermee worden alle service aanvragen van een klant opgehaald.</span><span class="sxs-lookup"><span data-stu-id="d1045-108">Gets all of a customer's service requests.</span></span>

<span data-ttu-id="d1045-109">In het dash board van de partner centrum kan deze bewerking worden uitgevoerd door eerst [een klant te selecteren](get-a-customer-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="d1045-109">In the Partner Center dashboard, this operation can be performed by first [selecting a customer](get-a-customer-by-name.md).</span></span> <span data-ttu-id="d1045-110">Selecteer vervolgens **Service beheer** op de zijbalk links.</span><span class="sxs-lookup"><span data-stu-id="d1045-110">Then, select **Service management** on the left sidebar.</span></span> <span data-ttu-id="d1045-111">De service aanvragen van de klant worden weer gegeven onder **ondersteunings tickets**.</span><span class="sxs-lookup"><span data-stu-id="d1045-111">The customer's service requests are displayed under **Support tickets**.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="d1045-112">Vereisten</span><span class="sxs-lookup"><span data-stu-id="d1045-112">Prerequisites</span></span>

- <span data-ttu-id="d1045-113">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="d1045-113">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="d1045-114">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="d1045-114">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="d1045-115">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d1045-115">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="d1045-116">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="d1045-116">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="d1045-117">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="d1045-117">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="d1045-118">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="d1045-118">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="d1045-119">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="d1045-119">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="d1045-120">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="d1045-120">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="d1045-121">C\#</span><span class="sxs-lookup"><span data-stu-id="d1045-121">C\#</span></span>

<span data-ttu-id="d1045-122">Als u een lijst met alle service aanvragen van een klant wilt weer geven, gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="d1045-122">To display a list of all of a customer's service requests, use your **IAggregatePartner.Customers** collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="d1045-123">Roep vervolgens de eigenschap [**ServiceRequests**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicerequests) aan, gevolgd door de methoden [**Get ()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.getasync) .</span><span class="sxs-lookup"><span data-stu-id="d1045-123">Then call the [**ServiceRequests**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.servicerequests) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.servicerequests.iservicerequestcollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// string customerId as string;

ResourceCollection<ServiceRequest> serviceRequests = partnerOperations.Customers.ById(customerId).ServiceRequests.Get();
```

<span data-ttu-id="d1045-124">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="d1045-124">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="d1045-125">**Project**: PartnerCenterSDK. FeaturesSamples- **klasse**: CustomerManagedServices.cs</span><span class="sxs-lookup"><span data-stu-id="d1045-125">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="d1045-126">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="d1045-126">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="d1045-127">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d1045-127">Request syntax</span></span>

| <span data-ttu-id="d1045-128">Methode</span><span class="sxs-lookup"><span data-stu-id="d1045-128">Method</span></span>  | <span data-ttu-id="d1045-129">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="d1045-129">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="d1045-130">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="d1045-130">**GET**</span></span> | <span data-ttu-id="d1045-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/servicerequests http/1.1</span><span class="sxs-lookup"><span data-stu-id="d1045-131">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/servicerequests HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="d1045-132">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="d1045-132">URI parameter</span></span>

<span data-ttu-id="d1045-133">Gebruik de volgende query parameter om alle service aanvragen voor de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="d1045-133">Use the following query parameter to get all service requests for the customer.</span></span>

| <span data-ttu-id="d1045-134">Naam</span><span class="sxs-lookup"><span data-stu-id="d1045-134">Name</span></span>                   | <span data-ttu-id="d1045-135">Type</span><span class="sxs-lookup"><span data-stu-id="d1045-135">Type</span></span>     | <span data-ttu-id="d1045-136">Vereist</span><span class="sxs-lookup"><span data-stu-id="d1045-136">Required</span></span> | <span data-ttu-id="d1045-137">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="d1045-137">Description</span></span>                            |
|------------------------|----------|----------|----------------------------------------|
| <span data-ttu-id="d1045-138">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="d1045-138">**customer-tenant-id**</span></span> | <span data-ttu-id="d1045-139">**guid**</span><span class="sxs-lookup"><span data-stu-id="d1045-139">**guid**</span></span> | <span data-ttu-id="d1045-140">J</span><span class="sxs-lookup"><span data-stu-id="d1045-140">Y</span></span>        | <span data-ttu-id="d1045-141">Een GUID die overeenkomt met de klant..</span><span class="sxs-lookup"><span data-stu-id="d1045-141">A GUID corresponding to the customer..</span></span> |

### <a name="request-headers"></a><span data-ttu-id="d1045-142">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="d1045-142">Request headers</span></span>

<span data-ttu-id="d1045-143">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="d1045-143">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="d1045-144">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="d1045-144">Request body</span></span>

<span data-ttu-id="d1045-145">Geen.</span><span class="sxs-lookup"><span data-stu-id="d1045-145">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="d1045-146">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="d1045-146">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/servicerequests HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 53d5d48c-9693-46b6-8071-2eed07797d6c
MS-CorrelationId: 998e31a1-3f17-4471-a9ee-7678dd72e033
```

## <a name="rest-response"></a><span data-ttu-id="d1045-147">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="d1045-147">REST response</span></span>

<span data-ttu-id="d1045-148">Als dit lukt, retourneert deze methode een verzameling **service aanvraag** resources in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="d1045-148">If successful, this method returns a collection of **Service Request** resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="d1045-149">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="d1045-149">Response success and error codes</span></span>

<span data-ttu-id="d1045-150">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="d1045-150">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="d1045-151">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="d1045-151">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="d1045-152">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="d1045-152">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="d1045-153">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="d1045-153">Response example</span></span>

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
