---
title: Een lijst met invoegtoepassingen voor een abonnement ophalen
description: Een verzameling invoegtoepassingen ophalen die een klant heeft gekozen om toe te voegen aan het abonnement.
ms.date: 07/25/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
author: amitravat
ms.author: amrava
ms.openlocfilehash: c627f595333a295048b02ec4326dcdc279d07b51
ms.sourcegitcommit: b1d6fd0ca93d8a3e30e970844d3164454415f553
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/09/2021
ms.locfileid: "111874632"
---
# <a name="get-a-list-of-add-ons-for-a-subscription"></a><span data-ttu-id="bc6e4-103">Een lijst met invoegtoepassingen voor een abonnement ophalen</span><span class="sxs-lookup"><span data-stu-id="bc6e4-103">Get a list of add-ons for a subscription</span></span>

<span data-ttu-id="bc6e4-104">**Van toepassing op**: Partner Center | Partner Center beheerd door 21Vianet | Partner Center voor Microsoft Cloud Duitsland | Partner Center voor Microsoft Cloud for US Government</span><span class="sxs-lookup"><span data-stu-id="bc6e4-104">**Applies to**: Partner Center | Partner Center operated by 21Vianet | Partner Center for Microsoft Cloud Germany | Partner Center for Microsoft Cloud for US Government</span></span>

<span data-ttu-id="bc6e4-105">In dit artikel wordt beschreven hoe u een verzameling invoegtoepassingen ophaalt die een klant heeft gekozen om toe te voegen aan **[de abonnementsresource.](subscription-resources.md)**</span><span class="sxs-lookup"><span data-stu-id="bc6e4-105">This article describes how to get a collection of add-ons that a customer has chosen to add to their **[Subscription](subscription-resources.md)** resource.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="bc6e4-106">Vereisten</span><span class="sxs-lookup"><span data-stu-id="bc6e4-106">Prerequisites</span></span>

- <span data-ttu-id="bc6e4-107">Referenties zoals beschreven in [Partner Center verificatie](partner-center-authentication.md).</span><span class="sxs-lookup"><span data-stu-id="bc6e4-107">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="bc6e4-108">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-108">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="bc6e4-109">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="bc6e4-109">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="bc6e4-110">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="bc6e4-110">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="bc6e4-111">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-111">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="bc6e4-112">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-112">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="bc6e4-113">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="bc6e4-113">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="bc6e4-114">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="bc6e4-114">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="bc6e4-115">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-115">A subscription ID.</span></span>

## <a name="c"></a><span data-ttu-id="bc6e4-116">C\#</span><span class="sxs-lookup"><span data-stu-id="bc6e4-116">C\#</span></span>

<span data-ttu-id="bc6e4-117">De lijst met invoegtoepassingen voor het abonnement van een klant op te halen:</span><span class="sxs-lookup"><span data-stu-id="bc6e4-117">To get the list of add-ons for a customer's subscription:</span></span>

1. <span data-ttu-id="bc6e4-118">Gebruik de **verzameling IAggregatePartner.Customers om** de **methode ById() aan te** roepen.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-118">Use your **IAggregatePartner.Customers** collection to call the **ById()** method.</span></span>

2. <span data-ttu-id="bc6e4-119">Roep de [**eigenschap Abonnementen aan,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) gevolgd door de [**methode ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="bc6e4-119">Call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span>

3. <span data-ttu-id="bc6e4-120">Roep de [**eigenschap Addons**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.addons) aan, gevolgd door [**Get()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.get) of [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.getasync).</span><span class="sxs-lookup"><span data-stu-id="bc6e4-120">Call the [**Addons**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscription.addons) property, followed by [**Get()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.get) or [**GetAsync()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptionaddoncollection.getasync).</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// var selectedSubscription Subscription;

var subscriptionDetails = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).AddOns.Get();

```

<span data-ttu-id="bc6e4-121">Zie voor een voorbeeld het volgende:</span><span class="sxs-lookup"><span data-stu-id="bc6e4-121">For an example, see the following:</span></span>

- <span data-ttu-id="bc6e4-122">Voorbeeld: [Consoletest-app](console-test-app.md)</span><span class="sxs-lookup"><span data-stu-id="bc6e4-122">Sample: [Console test app](console-test-app.md)</span></span>
- <span data-ttu-id="bc6e4-123">Project: **PartnerSDK.FeatureSample**</span><span class="sxs-lookup"><span data-stu-id="bc6e4-123">Project: **PartnerSDK.FeatureSample**</span></span>
- <span data-ttu-id="bc6e4-124">Klasse: **SubscriptionAddons.cs**</span><span class="sxs-lookup"><span data-stu-id="bc6e4-124">Class: **SubscriptionAddons.cs**</span></span>

## <a name="rest-request"></a><span data-ttu-id="bc6e4-125">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="bc6e4-125">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="bc6e4-126">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="bc6e4-126">Request syntax</span></span>

| <span data-ttu-id="bc6e4-127">Methode</span><span class="sxs-lookup"><span data-stu-id="bc6e4-127">Method</span></span>  | <span data-ttu-id="bc6e4-128">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="bc6e4-128">Request URI</span></span>                                                                                                                       |
|---------|-----------------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="bc6e4-129">**Toevoegen**</span><span class="sxs-lookup"><span data-stu-id="bc6e4-129">**GET**</span></span> | <span data-ttu-id="bc6e4-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/addons HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="bc6e4-130">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription}/addons HTTP/1.1</span></span> |

#### <a name="uri-parameter"></a><span data-ttu-id="bc6e4-131">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="bc6e4-131">URI parameter</span></span>

<span data-ttu-id="bc6e4-132">Deze tabel bevat de vereiste queryparameters om de lijst met invoegtoepassingen voor het abonnement op te halen.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-132">This table lists the required query parameters to get the list of add-ons for the subscription.</span></span>

| <span data-ttu-id="bc6e4-133">Naam</span><span class="sxs-lookup"><span data-stu-id="bc6e4-133">Name</span></span>                    | <span data-ttu-id="bc6e4-134">Type</span><span class="sxs-lookup"><span data-stu-id="bc6e4-134">Type</span></span>     | <span data-ttu-id="bc6e4-135">Vereist</span><span class="sxs-lookup"><span data-stu-id="bc6e4-135">Required</span></span> | <span data-ttu-id="bc6e4-136">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="bc6e4-136">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="bc6e4-137">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="bc6e4-137">**customer-tenant-id**</span></span>  | <span data-ttu-id="bc6e4-138">**guid**</span><span class="sxs-lookup"><span data-stu-id="bc6e4-138">**guid**</span></span> | <span data-ttu-id="bc6e4-139">J</span><span class="sxs-lookup"><span data-stu-id="bc6e4-139">Y</span></span>        | <span data-ttu-id="bc6e4-140">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-140">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="bc6e4-141">**id-for-subscription**</span><span class="sxs-lookup"><span data-stu-id="bc6e4-141">**id-for-subscription**</span></span> | <span data-ttu-id="bc6e4-142">**guid**</span><span class="sxs-lookup"><span data-stu-id="bc6e4-142">**guid**</span></span> | <span data-ttu-id="bc6e4-143">J</span><span class="sxs-lookup"><span data-stu-id="bc6e4-143">Y</span></span>        | <span data-ttu-id="bc6e4-144">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-144">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="bc6e4-145">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="bc6e4-145">Request headers</span></span>

<span data-ttu-id="bc6e4-146">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="bc6e4-146">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="bc6e4-147">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="bc6e4-147">Request body</span></span>

<span data-ttu-id="bc6e4-148">Geen.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-148">None.</span></span>

### <a name="request-example"></a><span data-ttu-id="bc6e4-149">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="bc6e4-149">Request example</span></span>

```http
GET https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription>/addons HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: 429902e2-ea2f-4704-b8a0-27fc53c539ba
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
```

## <a name="rest-response"></a><span data-ttu-id="bc6e4-150">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="bc6e4-150">REST response</span></span>

<span data-ttu-id="bc6e4-151">Als dit lukt, retourneert deze methode een verzameling resources in de antwoord-body.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-151">If successful, this method returns a collection of resources in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="bc6e4-152">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="bc6e4-152">Response success and error codes</span></span>

<span data-ttu-id="bc6e4-153">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-153">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="bc6e4-154">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="bc6e4-154">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="bc6e4-155">Zie Foutcodes voor een [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="bc6e4-155">For a full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="bc6e4-156">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="bc6e4-156">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 73754
Content-Type: application/json
MS-CorrelationId: c49004b1-224f-4d86-a607-6c8bcc52cfdd
MS-RequestId: 16fee928-dc2c-412f-adbb-871f68babf16
Date: Wed, 25 Nov 2015 05:50:45 GMT

{
    "totalCount": 37,
    "items": [{
        "id": "83ef9d05-4169-4ef9-9657-0e86b1eab1de",
        "entitlementId": "42226ed6-070a-4e0f-b80c-4cdfB3e97aa7",
        "friendlyName": "Myofferpurchase",
        "quantity": 1,
        "unitType": "none",
        "creationDate": "2015-11-25T06: 41: 12Z",
        "effectiveStartDate": "2015-11-24T08: 00: 00Z",
        "commitmentEndDate": "2016-12-12T08: 00: 00Z",
        "status": "active",
        "autoRenewEnabled": false,
        "billingType": "none",
        "contractType": "subscription",
        "links": {
            "offer": {
                "uri": "/v1/offers/0CCA44D6-68E9-4762-94EE-31ECE98783B9",
                "method": "GET",
                "headers": []
            },
            "self": {
                "uri": "/subscriptions?key=<key>",
                "method": "GET",
                "headers": []
            }
        },
        "orderId": "6183db3d-6318-4e52-877e-25806e4971be",
        "attributes": {
            "etag": "<etag>",
            "objectType": "Subscription"
        }
    }],
    "attributes": {
        "objectType": "Collection"
    }
}
```
