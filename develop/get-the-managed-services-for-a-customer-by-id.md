---
title: De beheerde services voor een klant ophalen op basis van id
description: Haalt de beheerde services voor een klant op. Met andere woorden, haal koppelingen op naar alle abonnementen van de klant waarvoor u beheerdersbevoegdheden hebt gedelegeerd. U kunt deze koppelingen gebruiken om ondersteunings- en bestandsserviceaanvragen bij Microsoft te bieden.
ms.date: 07/22/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 1cf7e7b62113bd96b00fdc2301e4e7ac4f5d4243
ms.sourcegitcommit: b307fd75e305e0a88cfd1182cc01d2c9a108ce45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/06/2021
ms.locfileid: "111548444"
---
# <a name="get-the-managed-services-for-a-customer-by-id"></a><span data-ttu-id="10476-105">De beheerde services voor een klant ophalen op basis van id</span><span class="sxs-lookup"><span data-stu-id="10476-105">Get the managed services for a customer by ID</span></span>

<span data-ttu-id="10476-106">**Van toepassing op**: Partner Center | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="10476-106">**Applies to**: Partner Center | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="10476-107">Haalt de beheerde services voor een klant op.</span><span class="sxs-lookup"><span data-stu-id="10476-107">Gets the managed services for a customer.</span></span> <span data-ttu-id="10476-108">Met andere woorden, haal koppelingen op naar alle abonnementen van de klant waarvoor u beheerdersbevoegdheden hebt gedelegeerd.</span><span class="sxs-lookup"><span data-stu-id="10476-108">In other words, get links to all of the customer's subscriptions for which you have delegated admin privileges.</span></span> <span data-ttu-id="10476-109">U kunt deze koppelingen gebruiken om ondersteunings- en bestandsserviceaanvragen bij Microsoft te bieden.</span><span class="sxs-lookup"><span data-stu-id="10476-109">You can use these links to provide support and file service requests with Microsoft.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="10476-110">Vereisten</span><span class="sxs-lookup"><span data-stu-id="10476-110">Prerequisites</span></span>

- <span data-ttu-id="10476-111">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="10476-111">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="10476-112">In dit scenario wordt verificatie alleen ondersteund met app- en gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="10476-112">This scenario supports authentication with App+User credentials only.</span></span>

- <span data-ttu-id="10476-113">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="10476-113">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="10476-114">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="10476-114">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="10476-115">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="10476-115">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="10476-116">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="10476-116">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="10476-117">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="10476-117">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="10476-118">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="10476-118">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

## <a name="c"></a><span data-ttu-id="10476-119">C\#</span><span class="sxs-lookup"><span data-stu-id="10476-119">C\#</span></span>

<span data-ttu-id="10476-120">Als u een lijst met alle beheerde services voor een klant wilt weergeven, gebruikt u de verzameling **IAggregatePartner.Customers** en roept u de [**methode ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) aan.</span><span class="sxs-lookup"><span data-stu-id="10476-120">To display a list of all the managed services for a customer, use your **IAggregatePartner.Customers** collection and call the [**ById()**](/dotnet/api/microsoft.store.partnercenter.customers.icustomercollection.byid) method.</span></span> <span data-ttu-id="10476-121">Roep vervolgens de [**eigenschap ManagedServices**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.managedservices) aan, gevolgd door de [**methoden Get()**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.get) of [**GetAsync().**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.getasync)</span><span class="sxs-lookup"><span data-stu-id="10476-121">Then call the [**ManagedServices**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.managedservices) property, followed by the [**Get()**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.managedservices.imanagedservicecollection.getasync) methods.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerID as Customer;

ResourceCollection<ManagedService> managedServices = partnerOperations.Customers.ById(selectedCustomerId).ManagedServices.Get();
```

<span data-ttu-id="10476-122">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="10476-122">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="10476-123">**Project:** PartnerCenterSDK.FeaturesSamples-klasse: CustomerManagedServices.cs </span><span class="sxs-lookup"><span data-stu-id="10476-123">**Project**: PartnerCenterSDK.FeaturesSamples **Class**: CustomerManagedServices.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="10476-124">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="10476-124">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="10476-125">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="10476-125">Request syntax</span></span>

| <span data-ttu-id="10476-126">Methode</span><span class="sxs-lookup"><span data-stu-id="10476-126">Method</span></span>  | <span data-ttu-id="10476-127">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="10476-127">Request URI</span></span>                                                                                            |
|---------|--------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="10476-128">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="10476-128">**GET**</span></span> | <span data-ttu-id="10476-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/managedservices HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="10476-129">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/managedservices HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="10476-130">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="10476-130">URI parameter</span></span>

<span data-ttu-id="10476-131">Gebruik de volgende queryparameter om de beheerde services van de klant op te halen.</span><span class="sxs-lookup"><span data-stu-id="10476-131">Use the following query parameter to get the customer's managed services.</span></span>

| <span data-ttu-id="10476-132">Naam</span><span class="sxs-lookup"><span data-stu-id="10476-132">Name</span></span>                   | <span data-ttu-id="10476-133">Type</span><span class="sxs-lookup"><span data-stu-id="10476-133">Type</span></span>     | <span data-ttu-id="10476-134">Vereist</span><span class="sxs-lookup"><span data-stu-id="10476-134">Required</span></span> | <span data-ttu-id="10476-135">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="10476-135">Description</span></span>                           |
|------------------------|----------|----------|---------------------------------------|
| <span data-ttu-id="10476-136">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="10476-136">**customer-tenant-id**</span></span> | <span data-ttu-id="10476-137">**guid**</span><span class="sxs-lookup"><span data-stu-id="10476-137">**guid**</span></span> | <span data-ttu-id="10476-138">J</span><span class="sxs-lookup"><span data-stu-id="10476-138">Y</span></span>        | <span data-ttu-id="10476-139">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="10476-139">A GUID corresponding to the customer.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="10476-140">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="10476-140">Request headers</span></span>

<span data-ttu-id="10476-141">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="10476-141">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="10476-142">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="10476-142">Request body</span></span>

<span data-ttu-id="10476-143">Geen.</span><span class="sxs-lookup"><span data-stu-id="10476-143">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="10476-144">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="10476-144">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/managedservices HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 4ff57220-f17b-4d8f-8e09-78334c57ba00
MS-CorrelationId: 03d6064a-f048-4aee-8892-ed46dc5c8bee
```

## <a name="rest-response"></a><span data-ttu-id="10476-145">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="10476-145">REST response</span></span>

<span data-ttu-id="10476-146">Als dit lukt, retourneert deze methode een verzameling **Managed Service-objecten** in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="10476-146">If successful, this method returns a collection of **Managed Service** objects in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="10476-147">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="10476-147">Response success and error codes</span></span>

<span data-ttu-id="10476-148">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="10476-148">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="10476-149">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="10476-149">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="10476-150">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="10476-150">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="10476-151">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="10476-151">Response example</span></span>

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
