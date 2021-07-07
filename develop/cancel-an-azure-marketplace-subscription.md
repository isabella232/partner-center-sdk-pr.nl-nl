---
title: Een abonnement op de commerciële marketplace annuleren
description: Meer informatie over het gebruik Partner Center API's voor het annuleren van een commerciële marketplace-abonnementsresource die overeenkomt met een klant en abonnements-id.
ms.date: 08/16/2019
ms.service: partner-dashboard
ms.subservice: partnercenter-sdk
ms.openlocfilehash: 95fa265a3c103d1ec55066f12a3ede7fdb2d0170
ms.sourcegitcommit: ad8082bee01fb1f57da423b417ca1ca9c0df8e45
ms.translationtype: MT
ms.contentlocale: nl-NL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111974281"
---
# <a name="cancel-a-commercial-marketplace-subscription-using-partner-center-apis"></a><span data-ttu-id="56359-103">Een abonnement op de commerciële marketplace annuleren met behulp Partner Center API's</span><span class="sxs-lookup"><span data-stu-id="56359-103">Cancel a commercial marketplace subscription using Partner Center APIs</span></span>

<span data-ttu-id="56359-104">In dit artikel wordt beschreven hoe u Partner Center API [](subscription-resources.md) kunt gebruiken om een commerciële marketplace-abonnementsresource te annuleren die overeenkomt met de klant- en abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="56359-104">This article describes how you can use Partner Center API to cancel a commercial marketplace [subscription](subscription-resources.md) resource that matches the customer and subscription ID.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="56359-105">Vereisten</span><span class="sxs-lookup"><span data-stu-id="56359-105">Prerequisites</span></span>

- <span data-ttu-id="56359-106">Referenties zoals beschreven in [Partner Center verificatie.](partner-center-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="56359-106">Credentials as described in [Partner Center authentication](partner-center-authentication.md).</span></span> <span data-ttu-id="56359-107">Dit scenario ondersteunt verificatie met zowel zelfstandige app- als app+gebruikersreferenties.</span><span class="sxs-lookup"><span data-stu-id="56359-107">This scenario supports authentication with both standalone App and App+User credentials.</span></span>

- <span data-ttu-id="56359-108">Een klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="56359-108">A customer ID (`customer-tenant-id`).</span></span> <span data-ttu-id="56359-109">Als u de id van de klant niet weet, kunt u deze op zoeken in het Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span><span class="sxs-lookup"><span data-stu-id="56359-109">If you don't know the customer's ID, you can look it up in the Partner Center [dashboard](https://partner.microsoft.com/dashboard).</span></span> <span data-ttu-id="56359-110">Selecteer **CSP** in het Partner Center menu, gevolgd door **Klanten**.</span><span class="sxs-lookup"><span data-stu-id="56359-110">Select **CSP** from the Partner Center menu, followed by **Customers**.</span></span> <span data-ttu-id="56359-111">Selecteer de klant in de lijst met klanten en selecteer vervolgens **Account**.</span><span class="sxs-lookup"><span data-stu-id="56359-111">Select the customer from the customer list, then select **Account**.</span></span> <span data-ttu-id="56359-112">Zoek op de pagina Account van de klant naar de **Microsoft-id** in de **sectie Klantaccountgegevens.**</span><span class="sxs-lookup"><span data-stu-id="56359-112">On the customer’s Account page, look for the **Microsoft ID** in the **Customer Account Info** section.</span></span> <span data-ttu-id="56359-113">De Microsoft-id is hetzelfde als de klant-id ( `customer-tenant-id` ).</span><span class="sxs-lookup"><span data-stu-id="56359-113">The Microsoft ID is the same as the customer ID  (`customer-tenant-id`).</span></span>

- <span data-ttu-id="56359-114">Een abonnements-id.</span><span class="sxs-lookup"><span data-stu-id="56359-114">A subscription ID.</span></span>

## <a name="partner-center-dashboard-method"></a><span data-ttu-id="56359-115">Partner Center-dashboardmethode</span><span class="sxs-lookup"><span data-stu-id="56359-115">Partner Center dashboard method</span></span>

<span data-ttu-id="56359-116">Een abonnement op de commerciële marketplace opzeggen in het Partner Center dashboard:</span><span class="sxs-lookup"><span data-stu-id="56359-116">To cancel a commercial marketplace subscription in the Partner Center dashboard:</span></span>

1. <span data-ttu-id="56359-117">[Selecteer een klant](get-a-customer-by-name.md).</span><span class="sxs-lookup"><span data-stu-id="56359-117">[Select a customer](get-a-customer-by-name.md).</span></span>

2. <span data-ttu-id="56359-118">Selecteer het abonnement dat u wilt annuleren.</span><span class="sxs-lookup"><span data-stu-id="56359-118">Select the subscription that you wish to cancel.</span></span>

3. <span data-ttu-id="56359-119">Kies de **optie Abonnement annuleren** en selecteer vervolgens **Verzenden.**</span><span class="sxs-lookup"><span data-stu-id="56359-119">Choose the **Cancel subscription** option, then select **Submit**.</span></span>

## <a name="c"></a><span data-ttu-id="56359-120">C\#</span><span class="sxs-lookup"><span data-stu-id="56359-120">C\#</span></span>

<span data-ttu-id="56359-121">Het abonnement van een klant annuleren:</span><span class="sxs-lookup"><span data-stu-id="56359-121">To cancel a customer's subscription:</span></span>

1. <span data-ttu-id="56359-122">[Haal het abonnement op id op.](get-a-subscription-by-id.md)</span><span class="sxs-lookup"><span data-stu-id="56359-122">[Get the subscription by ID](get-a-subscription-by-id.md).</span></span>

2. <span data-ttu-id="56359-123">Wijzig de eigenschap Status van [**het**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) abonnement.</span><span class="sxs-lookup"><span data-stu-id="56359-123">Change the subscription's [**Status**](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscription.status) property.</span></span> <span data-ttu-id="56359-124">Zie [SubscriptionStatus enumeration voor meer informatie over statuscodes.](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus) </span><span class="sxs-lookup"><span data-stu-id="56359-124">For information on **Status** codes, see [SubscriptionStatus enumeration](/dotnet/api/microsoft.store.partnercenter.models.subscriptions.subscriptionstatus).</span></span>

3. <span data-ttu-id="56359-125">Nadat de wijziging is aangebracht, gebruikt u uw **`IAggregatePartner.Customers`** verzameling en roept u de methode **ById()** aan.</span><span class="sxs-lookup"><span data-stu-id="56359-125">After the change is made, use your **`IAggregatePartner.Customers`** collection and call the **ById()** method.</span></span>

4. <span data-ttu-id="56359-126">Roep de [**eigenschap Abonnementen aan,**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) gevolgd door de [**methode ById().**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid)</span><span class="sxs-lookup"><span data-stu-id="56359-126">Call the [**Subscriptions**](/dotnet/api/microsoft.store.partnercenter.customers.icustomer.subscriptions) property, followed by the [**ById()**](/dotnet/api/microsoft.store.partnercenter.subscriptions.isubscriptioncollection.byid) method.</span></span>

5. <span data-ttu-id="56359-127">Roep de **methode Patch()** aan.</span><span class="sxs-lookup"><span data-stu-id="56359-127">Call the **Patch()** method.</span></span>

``` csharp
// IAggregatePartner partnerOperations;
// var selectedCustomerId as string;
// Subscription selectedSubscription;

selectedSubscription.Status = SubscriptionStatus.Deleted;
var updatedSubscription = partnerOperations.Customers.ById(selectedCustomerId).Subscriptions.ById(selectedSubscription.Id).Patch(selectedSubscription);
```

### <a name="sample-console-test-app"></a><span data-ttu-id="56359-128">Voorbeeldconsoletest-app</span><span class="sxs-lookup"><span data-stu-id="56359-128">Sample console test app</span></span>

<span data-ttu-id="56359-129">**Voorbeeld:** [Consoletest-app](console-test-app.md).</span><span class="sxs-lookup"><span data-stu-id="56359-129">**Sample**: [Console test app](console-test-app.md).</span></span> <span data-ttu-id="56359-130">**Project:** PartnerSDK.FeatureSample-klasse: UpdateSubscription.cs </span><span class="sxs-lookup"><span data-stu-id="56359-130">**Project**: PartnerSDK.FeatureSample **Class**: UpdateSubscription.cs</span></span>

## <a name="rest-request"></a><span data-ttu-id="56359-131">REST-aanvraag</span><span class="sxs-lookup"><span data-stu-id="56359-131">REST request</span></span>

### <a name="request-syntax"></a><span data-ttu-id="56359-132">Aanvraagsyntaxis</span><span class="sxs-lookup"><span data-stu-id="56359-132">Request syntax</span></span>

| <span data-ttu-id="56359-133">Methode</span><span class="sxs-lookup"><span data-stu-id="56359-133">Method</span></span>    | <span data-ttu-id="56359-134">Aanvraag-URI</span><span class="sxs-lookup"><span data-stu-id="56359-134">Request URI</span></span>                                                                                                                |
|-----------|----------------------------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="56359-135">**Patch**</span><span class="sxs-lookup"><span data-stu-id="56359-135">**PATCH**</span></span> | <span data-ttu-id="56359-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span><span class="sxs-lookup"><span data-stu-id="56359-136">[*{baseURL}*](partner-center-rest-urls.md)/v1/customers/{customer-tenant-id}/subscriptions/{id-for-subscription} HTTP/1.1</span></span> |

### <a name="uri-parameter"></a><span data-ttu-id="56359-137">URI-parameter</span><span class="sxs-lookup"><span data-stu-id="56359-137">URI parameter</span></span>

<span data-ttu-id="56359-138">Deze tabel bevat de vereiste queryparameter om het abonnement op te schorten.</span><span class="sxs-lookup"><span data-stu-id="56359-138">This table lists the required query parameter to suspend the subscription.</span></span>

| <span data-ttu-id="56359-139">Naam</span><span class="sxs-lookup"><span data-stu-id="56359-139">Name</span></span>                    | <span data-ttu-id="56359-140">Type</span><span class="sxs-lookup"><span data-stu-id="56359-140">Type</span></span>     | <span data-ttu-id="56359-141">Vereist</span><span class="sxs-lookup"><span data-stu-id="56359-141">Required</span></span> | <span data-ttu-id="56359-142">Beschrijving</span><span class="sxs-lookup"><span data-stu-id="56359-142">Description</span></span>                               |
|-------------------------|----------|----------|-------------------------------------------|
| <span data-ttu-id="56359-143">**customer-tenant-id**</span><span class="sxs-lookup"><span data-stu-id="56359-143">**customer-tenant-id**</span></span>  | <span data-ttu-id="56359-144">**guid**</span><span class="sxs-lookup"><span data-stu-id="56359-144">**guid**</span></span> | <span data-ttu-id="56359-145">J</span><span class="sxs-lookup"><span data-stu-id="56359-145">Y</span></span>        | <span data-ttu-id="56359-146">Een GUID die overeenkomt met de klant.</span><span class="sxs-lookup"><span data-stu-id="56359-146">A GUID corresponding to the customer.</span></span>     |
| <span data-ttu-id="56359-147">**id-for-subscription**</span><span class="sxs-lookup"><span data-stu-id="56359-147">**id-for-subscription**</span></span> | <span data-ttu-id="56359-148">**guid**</span><span class="sxs-lookup"><span data-stu-id="56359-148">**guid**</span></span> | <span data-ttu-id="56359-149">J</span><span class="sxs-lookup"><span data-stu-id="56359-149">Y</span></span>        | <span data-ttu-id="56359-150">Een GUID die overeenkomt met het abonnement.</span><span class="sxs-lookup"><span data-stu-id="56359-150">A GUID corresponding to the subscription.</span></span> |

### <a name="request-headers"></a><span data-ttu-id="56359-151">Aanvraagheaders</span><span class="sxs-lookup"><span data-stu-id="56359-151">Request headers</span></span>

<span data-ttu-id="56359-152">Zie REST-headers [Partner Center meer informatie.](headers.md)</span><span class="sxs-lookup"><span data-stu-id="56359-152">For more information, see [Partner Center REST headers](headers.md).</span></span>

### <a name="request-body"></a><span data-ttu-id="56359-153">Aanvraagbody</span><span class="sxs-lookup"><span data-stu-id="56359-153">Request body</span></span>

<span data-ttu-id="56359-154">Een volledige **abonnementsresource** is vereist in de aanvraag.</span><span class="sxs-lookup"><span data-stu-id="56359-154">A full **Subscription** resource is required in the request body.</span></span> <span data-ttu-id="56359-155">Zorg ervoor dat **de eigenschap Status** is bijgewerkt.</span><span class="sxs-lookup"><span data-stu-id="56359-155">Ensure that the **Status** property has been updated.</span></span>

### <a name="request-example"></a><span data-ttu-id="56359-156">Voorbeeld van aanvraag</span><span class="sxs-lookup"><span data-stu-id="56359-156">Request example</span></span>

```http
PATCH https://api.partnercenter.microsoft.com/v1/customers/<customer-tenant-id>/subscriptions/<id-for-subscription> HTTP/1.1
Authorization: Bearer <token>
Accept: application/json
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
If-Match: <etag>
Content-Type: application/json
Content-Length: 1029
Expect: 100-continue
Connection: Keep-Alive

{
    "id": "6e7aa601-629e-461b-8933-0898c3cc3c7c",
    "offerId": "DZH318Z0BXWC:0001:DZH318Z0BMJX",
    "offerName": "offer Name",
    "friendlyName": "friendly Name",
    "quantity": 1,
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "deleted",
    "autoRenewEnabled": false,
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [{
        "type": "Full",
        "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
    }],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "publisherName": "publisher Name",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {"objectType": "Subscription"},
}
```

## <a name="rest-response"></a><span data-ttu-id="56359-157">REST-antwoord</span><span class="sxs-lookup"><span data-stu-id="56359-157">REST response</span></span>

<span data-ttu-id="56359-158">Als dit lukt, retourneert deze methode verwijderde eigenschappen van abonnementsresources in de antwoord-body. [](subscription-resources.md)</span><span class="sxs-lookup"><span data-stu-id="56359-158">If successful, this method returns deleted [Subscription](subscription-resources.md) resource properties in the response body.</span></span>

### <a name="response-success-and-error-codes"></a><span data-ttu-id="56359-159">Antwoord geslaagd en foutcodes</span><span class="sxs-lookup"><span data-stu-id="56359-159">Response success and error codes</span></span>

<span data-ttu-id="56359-160">Elk antwoord wordt geleverd met een HTTP-statuscode die aangeeft of de fout is geslaagd en aanvullende informatie over foutopsporing.</span><span class="sxs-lookup"><span data-stu-id="56359-160">Each response comes with an HTTP status code that indicates success or failure and additional debugging information.</span></span> <span data-ttu-id="56359-161">Gebruik een hulpprogramma voor netwerk traceren om deze code, het fouttype en aanvullende parameters te lezen.</span><span class="sxs-lookup"><span data-stu-id="56359-161">Use a network trace tool to read this code, error type, and additional parameters.</span></span> <span data-ttu-id="56359-162">Zie Foutcodes voor de [volledige lijst.](error-codes.md)</span><span class="sxs-lookup"><span data-stu-id="56359-162">For the full list, see [Error Codes](error-codes.md).</span></span>

### <a name="response-example"></a><span data-ttu-id="56359-163">Voorbeeld van antwoord</span><span class="sxs-lookup"><span data-stu-id="56359-163">Response example</span></span>

```http
HTTP/1.1 200 OK
Content-Length: 1322
Content-Type: application/json; charset=utf-8
MS-RequestId: ca7c39f7-1a80-43bc-90d8-ee7d1cad3831
MS-CorrelationId: ec8f62e5-1d92-47e9-8d5d-1924af105f2c
X-Locale: en-US

{
    "id": "6e7aa601-629e-461b-8933-0898c3cc3c7c",
    "offerId": "DZH318Z0BXWC:0001:DZH318Z0BMJX",
    "offerName": "offer Name",
    "friendlyName": "friendly Name",
    "quantity": 1,
    "unitType": "License(s)",
    "hasPurchasableAddons": false,
    "creationDate": "2019-01-04T01:00:12.6647304Z",
    "effectiveStartDate": "2019-01-09T00:21:45.9263727+00:00",
    "commitmentEndDate": "2019-02-08T00:21:45.9263727+00:00",
    "status": "deleted",
    "autoRenewEnabled": false,
    "isTrial": false,
    "billingType": "license",
    "billingCycle": "monthly",
    "termDuration": "P1M",
    "refundOptions": [
        {
            "type": "Full",
            "expiresAt": "2019-01-10T00:21:45.9263727+00:00"
        }
    ],
    "isMicrosoftProduct": false,
    "partnerId": "",
    "contractType": "subscription",
    "links": {
        "product": {
            "uri": "/products/DZH318Z0BXWC?country=US",
            "method": "GET",
            "headers": []
        },
        "sku": {
            "uri": "/products/DZH318Z0BXWC/skus/0001?country=US",
            "method": "GET",
            "headers": []
        },
        "availability": {
            "uri": "/products/DZH318Z0BXWC/skus/0001/availabilities/DZH318Z0BMJX?country=US",
            "method": "GET",
            "headers": []
        },
        "self": {
            "uri": "/customers/5921f00a-32c0-4457-aaa1-e8018c650895/subscriptions/6e7aa601-629e-461b-8933-0898c3cc3c7c",
            "method": "GET",
            "headers": []
        }
    },
    "publisherName": "publishe rName",
    "orderId": "ImxjLNL4_fOc-2KoyOxGTZcrlIquzls11",
    "attributes": {
        "etag": "",
        "objectType": "Subscription"
    }
}
```
