---
title: De beheerde services voor een klant ophalen op basis van id
description: Hiermee haalt u de beheerde services voor een klant op. Met andere woorden, koppelingen naar alle abonnementen van de klant ophalen waarvoor u beheerders bevoegdheden hebt gedelegeerd. U kunt deze koppelingen gebruiken om ondersteuning en aanvragen voor bestands Services bij micro soft aan te bieden.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 4764fce6a80035ea4b9dcc6677a3da28fc863eb7
ms.sourcegitcommit: 30d1b9d48453c7697a2f42ee09138e507dcf9f2d
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 10/19/2020
ms.locfileid: "97767528"
---
# <a name="get-the-managed-services-for-a-customer-by-id"></a><span data-ttu-id="9bfe0-105">De beheerde services voor een klant ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="9bfe0-105">Get the managed services for a customer by ID</span></span>

<span data-ttu-id="9bfe0-106">**Van toepassing op**</span><span class="sxs-lookup"><span data-stu-id="9bfe0-106">**Applies To**</span></span>

- <span data-ttu-id="9bfe0-107">Partnercentrum</span><span class="sxs-lookup"><span data-stu-id="9bfe0-107">Partner Center</span></span>
- <span data-ttu-id="9bfe0-108">Partnercentrum voor Microsoft Cloud Duitsland</span><span class="sxs-lookup"><span data-stu-id="9bfe0-108">Partner Center for Microsoft Cloud Germany</span></span>
- <span data-ttu-id="9bfe0-109">Partnercentrum voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="9bfe0-109">Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="9bfe0-110">Hiermee haalt u de beheerde services voor een klant op.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-110">Gets the managed services for a customer.</span></span> <span data-ttu-id="9bfe0-111">Met andere woorden, koppelingen naar alle abonnementen van de klant ophalen waarvoor u beheerders bevoegdheden hebt gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-111">In other words, get links to all of the customer's subscriptions for which you have delegated admin privileges.</span></span> <span data-ttu-id="9bfe0-112">U kunt deze koppelingen gebruiken om ondersteuning en aanvragen voor bestands Services bij micro soft aan te bieden.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-112">You can use these links to provide support and file service requests with Microsoft.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="9bfe0-113">Vereisten</span><span class="sxs-lookup"><span data-stu-id="9bfe0-113">Prerequisites</span></span>

- <span data-ttu-id="9bfe0-114">Referenties zoals beschreven in [Partner Center-verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="9bfe0-114">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="9bfe0-115">In dit scenario wordt alleen verificatie met app + gebruikers referenties ondersteund.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-115">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="9bfe0-116">Een klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9bfe0-116">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="9bfe0-117">Als u de klant-ID niet weet, kunt u deze bekijken in het [dash board](https://partner.microsoft.com/dashboard)van de partner centrum.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-117">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="9bfe0-118">Selecteer **CSP** in het menu partner centrum, gevolgd door **klanten**.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-118">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="9bfe0-119">Selecteer de klant in de lijst klant en selecteer vervolgens **account**.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-119">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="9bfe0-120">Zoek op de pagina account van de klant naar de **micro soft-id** in het gedeelte **klant account info** .</span><span class="sxs-lookup"><span data-stu-id="9bfe0-120">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="9bfe0-121">De micro soft-ID is gelijk aan de klant-ID ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="9bfe0-121">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="9bfe0-122">C\#</span><span class="sxs-lookup"><span data-stu-id="9bfe0-122">C\#</span></span>

<span data-ttu-id="9bfe0-123">Als u een lijst met alle beheerde services voor een klant wilt weer geven, gebruikt u de verzameling **IAggregatePartner. Customers** en roept u de methode [**ById ()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-123">To display a list of all the managed services for a customer, use your **IAggregatePartner.Customers** collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="9bfe0-124">Roep vervolgens de eigenschap [**ManagedServices**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.managedservices) aan, gevolgd door de methoden [**Get ()**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.get) of [**GetAsync ()**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.getasync) .</span><span class="sxs-lookup"><span data-stu-id="9bfe0-124">Then call the [**ManagedServices**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.managedservices) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerID as Customer;

ResourceCollection<ManagedService> managedServices = partnerOperations.Customers.ById(selectedCustomerId).ManagedServices.Get();
```

<span data-ttu-id="9bfe0-125">Voor **beeld**: [console test-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="9bfe0-125">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="9bfe0-126">**Project**: PartnerCenterSDK. FeaturesSamples- **klasse**: CustomerManagedServices.cs</span><span class="sxs-lookup"><span data-stu-id="9bfe0-126">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="9bfe0-127">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="9bfe0-127">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="9bfe0-128">Syntaxis van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9bfe0-128">Request syntax</span></span>

| <span data-ttu-id="9bfe0-129">Methode</span><span class="sxs-lookup"><span data-stu-id="9bfe0-129">Method</span></span>  | <span data-ttu-id="9bfe0-130">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="9bfe0-130">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="9bfe0-131">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="9bfe0-131">**GET**</span></span> | <span data-ttu-id="9bfe0-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/Customers/{Customer-Tenant-id}/managedservices http/1.1</span><span class="sxs-lookup"><span data-stu-id="9bfe0-132">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/managedservices HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="9bfe0-133">URI-para meter</span><span class="sxs-lookup"><span data-stu-id="9bfe0-133">URI parameter</span></span>

<span data-ttu-id="9bfe0-134">Gebruik de volgende query parameter om de beheerde services van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-134">Use the following query parameter to get the customer's managed services.</span></span>

| <span data-ttu-id="9bfe0-135">Naam</span><span class="sxs-lookup"><span data-stu-id="9bfe0-135">Name</span></span>                   | <span data-ttu-id="9bfe0-136">Type</span><span class="sxs-lookup"><span data-stu-id="9bfe0-136">Type</span></span>     | <span data-ttu-id="9bfe0-137">Vereist</span><span class="sxs-lookup"><span data-stu-id="9bfe0-137">Required</span></span> | <span data-ttu-id="9bfe0-138">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="9bfe0-138">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="9bfe0-139">**klant-Tenant-id**</span><span class="sxs-lookup"><span data-stu-id="9bfe0-139">**customer-tenant-id**</span></span> | <span data-ttu-id="9bfe0-140">**guid**</span><span class="sxs-lookup"><span data-stu-id="9bfe0-140">**guid**</span></span> | <span data-ttu-id="9bfe0-141">J</span><span class="sxs-lookup"><span data-stu-id="9bfe0-141">Y</span></span>        | <span data-ttu-id="9bfe0-142">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-142">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="9bfe0-143">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="9bfe0-143">Request headers</span></span>

<span data-ttu-id="9bfe0-144">Zie voor meer informatie [Partner Center rest headers](headers.md).</span><span class="sxs-lookup"><span data-stu-id="9bfe0-144">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="9bfe0-145">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="9bfe0-145">Request body</span></span>

<span data-ttu-id="9bfe0-146">Geen.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-146">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="9bfe0-147">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="9bfe0-147">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/managedservices HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4ff57220-f17b-4d8f-8e09-78334c57ba00
MS-CorrelationId: 03d6064a-f048-4aee-8892-ed46dc5c8bee
```

## <a name="rest-response"></a><span data-ttu-id="9bfe0-148">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="9bfe0-148">REST response</span></span>

<span data-ttu-id="9bfe0-149">Als dit lukt, retourneert deze methode een verzameling **beheerde service** objecten in de hoofd tekst van het antwoord.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-149">If successful, this method returns a collection of **Managed Service** objects in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="9bfe0-150">Geslaagde en fout codes</span><span class="sxs-lookup"><span data-stu-id="9bfe0-150">Response success and error codes</span></span>

<span data-ttu-id="9bfe0-151">Elk antwoord wordt geleverd met een HTTP-status code die aangeeft of de fout is opgetreden of mislukt en aanvullende informatie over fout opsporing.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-151">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="9bfe0-152">Gebruik een hulp programma voor netwerk tracering om deze code, het fout type en aanvullende para meters te lezen.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-152">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="9bfe0-153">Zie [fout codes](error-codes.md)voor de volledige lijst.</span><span class="sxs-lookup"><span data-stu-id="9bfe0-153">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="9bfe0-154">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="9bfe0-154">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 10588
Content-Type: application/json
MS-CorrelationId: 03d6064a-f048-4aee-8892-ed46dc5c8bee
MS-RequestId: 4ff57220-f17b-4d8f-8e09-78334c57ba00
Date: Mon, 23 Nov 2015 18:02:12 GMT

{
    "totalCount": 2,
    "items": [{
        "id": "Exchange",
        "name": "Exchange",
        "groupName": "Office",
        "links": {
            "adminService": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=Exchange&InitialDomain=<domain>&PrimaryDomain=<domain>",
                "method": "GET",
                "headers": []
            },
            "serviceHealth": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=ServiceStatus",
                "method": "GET",
                "headers": []
            },
            "serviceTicket": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=Support",
                "method": "GET",
                "headers": []
            }
        },
        "attributes": {
            "objectType": "ManagedService"
        }
    },
    {
        "id": "MicrosoftCommunicationsOnline",
        "name": "SkypeforBusiness",
        "groupName": "Office",
        "links": {
            "adminService": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=MicrosoftCommunicationsOnline",
                "method": "GET",
                "headers": []
            },
            "serviceHealth": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=ServiceStatus",
                "method": "GET",
                "headers": []
            },
            "serviceTicket": {
                "uri": "https://portal.office.com/Partner/BeginClientSession.aspx?CTID=<ctid>&CSDEST=Support",
                "method": "GET",
                "headers": []
            }
        },
        "attributes": {
            "objectType": "ManagedService"
        }
    }
```
